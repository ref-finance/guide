# Concentrated Liquidity Market Maker (CLMM)

Concentrated Liquidity Market Maker (CLMM) was built based on the Discretized Concentrated Liquidity (DCL) pool, initially founded by Izumi Team.

Here, we discuss some concepts and behaviors that are important for users and researchers to have a better understanding of ref-v2.

## From Price to Point

In a pool with two types of tokens, like token X and token Y, the price tells you how many of token Y you need to give to get one of token X. If we take an example of a pool with wnear and usdt, and say the price is 4.05 USDT for one wnear, that's what we call the **decimal price**.

Now, there's also something called the **undecimal price**. Since wnear and usdt don't have the same number of decimal places (wnear has 24 and usdt has 6), we have to adjust the price by taking into account these decimals. The price now  comes to **4.05 \* 106 / 1024**

Next, comes the important part. We need to map this continuous price into a discrete one (what we call _**price point**_ or just _**point**_), in a way that lets 1.0001 \*\* _**point**_ be the price splitter. Practically, we limit point in a \[-800,000, 800,000) range, which can represent an undecimal price range of 1.81e-35 to 6.52e+34, that is 1.81e-17 to 6.52e+52 decimal price range in that wnear<>usdt pool.

Now, each point represents a very small price range, and we use the exact price computed from that point to be the fixed price when swapping in this range, which we call a _**constant sum formula**_ model. For example, in the previous pool, point -400520 represents a price range of \[4.041169… , 4.041573…). And when swapping in this small range, we take 4.041169… as a fixed swap price.

In a word, we map continuous prices into small ranges of points. For the curve comprised of those points, we take the classic constant production formula for swap. But in those small ranges, we take a constant sum formula for swap.

## From Point to Slot, From Slot to Bin

For those tokens with strong correlation, even a very small price movement will reflect a major change in market. So we allow users to mint liquidity, and place orders on each point.

But for those pool that hold weak correlation even non-correlation tokens, the market price vary frequently and drastically. To get a better performance, we group _**points**_ into _**slots**_, and only allow users to mint liquidity or place orders on those slot borders.

For example, let’s say take 40 points per slot in the previous wnear-usdt pool, we have three conjunctive slot borders -400560, -400520, -400480, they represent three conjunctive human-readable prices: 4.025040, 4.041574, 4.057366. And the current point is -400498, which means a price of 4.050069. Then If Alice wants to place an order that is just one step over the current price, she can only choose 4.057366. Or to place an order one step below the current one, that would be 4.041574. Seems complex? Don’t worry, our frontend will take care of all this stuff for users. They can just simply click up or down to have a small adjustment of price.

Furthermore, we associate pool fee policy (we call it fee-tier) with the slot. There are 4 fee tiers on REF-V2:

* 0.01% fee rate and 1 point per slot (suitable for stable coins swap pool);
* 0.04% fee rate and 8 points per slot;
* 0.2% fee rate and 40 points per slot;
* 1% fee rate and 200 points per slot;

However, the number of slots for a liquidity pool is still too many, we further group the _**slots**_ into _**bins**_, and users on Ref UI can only mint liquidity or place orders on bin borders.

## Three Roles And What They Are Capable Of

1. **Liquidity provider**, classic maker, passive party in trade, with swap fee income;
2. **Order owner**, one-way maker, passive party in trade, no swap fee income;
3. **Swapper**, taker, and active party in trade need to pay a swap fee according to the fee tier of the pool;

### Swapper

On ref-v2, the user can directly initiate a swap from token contracts through their _**ft\_transfer\_call**_ interface. We support chained swaps, which means the user can swap A to C in a chained way (A→B and B→C) in one TX. The swapped-out token would be auto-transferred back to the user’s wallet and furthermore, all wnear would be unwrapped to near when transferred back to the user.

There are 3 swap modes for the user to choose.

* Normal Swap, support chained swap, swap all token-in into token-out;
* Swap by Output Amount, support chained swap, swap to get given amount of token-out;
* Swap with a Stop Point, only on the single pool, swap all token-in or part of it if the point goes to the stop limit.

For the swap of any point, we always consume orders first and then the liquidity. Liquidity Provider won’t complain about it, cause all swap fee (excluding those that go to protocol), including those generated on swapping of those orders, goes to LP.

### Order Owner

Here, order means limit order. It is a kind of one-way liquidity. A selling order is an order that is placed on a point equal to or above the current point, to sell token X for Y with the price on that point. On the contrary, a buying order is an order that sells token Y for X on a point equal to or below the current point. Just a kind reminder, we have talked it through that orders can only placed at slot borders.

We say the order is one-way liquidity, which means, let’s look at a selling order, if the current price passes the order point from left to right, we ensure this order will be fulfilled and the earned token Y won’t go back to token X even if current price drop back to the left of order point again.

There is a possibility that a race condition would come up. As a contract aggregates all user orders at the same point into one point order, it can NOT tell whose user order is filled and whose not when the point order is partially filled. In this case, order owners come to a race condition that obeys to a first-claim-first-get policy.

If user places a selling order on a point below the current point or a buying order on a point above the current point, we would first try to do a swap-with-stop-point action and if there is any amount left, then an order with the remaining amount would be established. But need to notice, that a swap fee would be charged on swap action.

As a passive party of trader, the earned token won’t auto transfer to the order owner’s wallet, they need to call a claim interface to explicitly harvest their earnings. Currently, this claim interface is combined with the cancel interface, where you put a 0 as cancel amount, which means a pure claim action.

Order owner can cancel / partially cancel his order, and as we just said, it will be claimed internally before trying to cancel. So, it is possible the order has been fulfilled or the remaining amount is less than the requested cancellation amount. But don’t worry, it won’t cause any trouble, we will try to cancel as many as you requested.

User may get some token X or Y back after canceling, an order earning a refund from cancel, or both. Those tokens would directly transfer to user’s wallet.

To save contract storage, we have some limits on the contract level. Each user can only have a maximum of 64 active orders in total. An active order means it still has remaining tokens waiting to sell. Users can either wait for it to be fulfilled or cancel all remaining to save room for new orders. Those non-active orders will go to the user’s history order list. Likewise, the contract only stores the latest 16 history orders per user. But user can fetch all history through our centralized data service.

### Liquidity Provider

User mints liquidity with a range, which is one or several slots. Here we use the word mint, it implies that liquidity is a kind of NFT in REF-V2, but user are free to modify their liquidity NFT by adding or removing its amount.

Only liquidity providers would get benefits from swap fee. Those swap fees in the form of tokens X or Y, won’t go back to pool liquidity. They just stand there waiting for LP to claim, like order earnings but without any race condition in liquidity fee.

The add and remove actions, just like order, would imply an internal claim fee action. And to remove zero amount of liquidity means a pure claim too.

No matter whether to add or remove liquidity, the user may get some token X or Y back, a swap fee income, a refund from removal, or both. Those tokens would directly transfer to user’s wallet.

## About Fee

Although we may have touched on this topic in previous chapters, it is better to have a dedicated chapter to discuss fees.

Basically, we only charge swap fees from those swappers (active party of swap). In other words, we only have a fee for the taker. The fee would be charged in the form of a token-in. For example, on a 0.2% fee pool, when the swapper starts a swap of 100 token-in, he actually uses 99.8 to do the swap, and the 0.2 left is the fee we charged.

For those fees charged, we split them between liquidity in that swap range and protocol. Currently, the share ratio is 50%. This means a 0.2% fee pool, liquidity got 0.1% and the protocol got another 0.1%.

For those fees belonging to liquidity, LP should explicitly call the claim interface to get them back to wallets. If this liquidity has been transferred to a new owner, then the original owner lost all unclaimed fees.
