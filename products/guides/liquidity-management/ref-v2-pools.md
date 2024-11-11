---
description: Pooling with Ref v2's Discretized Concentrated Liquidity AMM
---

# Ref v2 Pools

### Introduction

Ref v2's Discretized Concentrated Liquidity (DCL) pools are based on [iZUMi Finance’s Discretized Liquidity AMM](#user-content-fn-1)[^1]. Each DCL Pool is divided into many separate bins, each of which represents a slightly different swap rate between the two tokens in the pool.&#x20;

When a Liquidity Provider (LP) deposits their assets in a DCL Pool, they select a range of swap rates for which their assets can be used for swapping. In other words, their liquidity is “concentrated” within a specific range of swap rates, which is then distributed among separate, or “discrete”, bins along that range. This differs from the pools in Ref v1, where liquidity is evenly distributed throughout the curve of the constant product formula (x \* y = k).

<figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption><p>Liquidity Distribution in a DCL Pool</p></figcaption></figure>

To determine the swap rate, the exchange uses a virtual constant product curve, derived from the total liquidity in the pool and how it is distributed. When a swap takes place, the exchange identifies which bins to use for the transaction. It treats each bin as if it were a pool, and manages each one separately using a method based on the constant sum formula (x + y = z).

<figure><img src="../../../.gitbook/assets/RefV2Distribution.png" alt=""><figcaption><p>Virtual vs Real Reserves in DL Pools</p></figcaption></figure>

When a swap takes place against a DCL pool, only the LPs with assets placed within bins utilised for the swap will receive a share of the swap fees, in proportion to their share of the liquidity within those bins. This differs from the pools in Ref v1, where fees are shared among all LPs in proportion to their share of the liquidity within the entire pool. Another way Ref v2 differs is that a LP’s share of the fees is immediately allocated to them, and are not part of the pool’s liquidity.

### Types of DCL Strategy

<figure><img src="../../../.gitbook/assets/DCL liquidity shapes.png" alt=""><figcaption></figcaption></figure>

* **Uniform (Flat) Liquidity**: In this model, liquidity is distributed evenly across all price ranges. No matter what the current price is, the liquidity is the same for each price point. This is the simplest form of liquidity distribution and is used by some of the earliest AMMs. It's like spreading a fixed amount of resources across a battlefield evenly, without concentrating forces at any strategic point.
* **Normal (Bell Curve) Liquidity**: Here, liquidity is distributed according to a normal distribution, with most of it concentrated around a certain price, which is usually the current or the expected future price of the asset. The further away from this price, the less liquidity is available.
* **Skewed (Asymmetric) Liquidity**: In a skewed distribution, liquidity is not evenly distributed and is instead biased towards a certain price direction. A skewed distribution could look like a normal distribution that has been pushed to one side. This is akin to placing more soldiers on one flank of an army in anticipation of the main attack coming from that direction.\


### Risks with DCL Pools

The more concentrated a LP’s liquidity is (i.e. the smaller the range of swap rates they choose when they deposit), the higher their share of the fees will be when their liquidity is used for a swap, compared to how much they would have received had they spread their liquidity over a wider range. However, there is also increased risk. If the overall swap rate goes outside the bounds they have chosen, their entire position will be converted to the token that is decreasing in value relative to the other.&#x20;

For example, if a LP deposits USDC.e and NEAR within the range of 2.23572 - 2.730688 USDC.e/NEAR, and the value of NEAR drops below 2.23572 USDC.e, then their entire position will be converted to NEAR. If the value of NEAR goes above 2.730688 USDC.e, then their entire position will be converted to USDC.e.

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption><p>Price points at which a position is converted into one token. The more concentrated a LP’s liquidity is, the higher the risk that their entire position will be converted to the token whose value is decreasing relative to the other.  </p></figcaption></figure>

### Depositing Liquidity

To deposit liquidity in a DCL pool, first go to the "V2 Pools" tab on the Pools Page, click on a pool, and then click "Add liquidity".

<figure><img src="../../../.gitbook/assets/image (71).png" alt=""><figcaption><p>DCL Pools are found in the "V2 Pools" tab of the Pools Page.</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption><p>The "Add Liquidity" button is on each pool's detail page. </p></figcaption></figure>

Choose a minimum and maximum rate that your assets can be used for swaps, and the amounts to deposit. There may be pools with multiple "Fee Tiers" to choose from. The higher the fee, the more you make from swaps that utilize your pool, but your pool is less likely to be selected for swaps than pools with lower fees.&#x20;

<figure><img src="../../../.gitbook/assets/image (73).png" alt=""><figcaption><p>The Add Liquidity form for a DCL pool.</p></figcaption></figure>

### Claiming Swap Fees

With Ref v2's DCL Pools, your share of the swap fees are immediately allocated to your account, and are not part of the pool’s liquidity. You can “claim” your share of the fees at any time, without removing any liquidity from the pool. However, adding or removing liquidity will automatically transfer any unclaimed tokens to your wallet. &#x20;

<figure><img src="../../../.gitbook/assets/image (74).png" alt=""><figcaption><p>Clicking the "Claim" button will transfer your share of the swap fees to your wallet.</p></figcaption></figure>

### Adding More Liquidity

If you want to add more liquidity to a pool, you will be given two choices. You can add more liquidity to your existing position, or you can create a new position and select a different range to deposit your liquidity in.&#x20;

<figure><img src="../../../.gitbook/assets/image (75).png" alt=""><figcaption><p>You are presented with this form when adding liquidity to a pool that you already have a position in.</p></figcaption></figure>

### Removing Liquidity

After clicking the "Remove" button on the pool page, you will have the option of removing all your liquidity, or only a portion of it. Removing any liquidity will automatically transfer any unclaimed tokens from swap fees to your wallet.&#x20;

<figure><img src="../../../.gitbook/assets/image (76).png" alt=""><figcaption><p>You can remove some or all of your liquidity.</p></figcaption></figure>

[^1]: [https://izumi.finance/paper/dswap.pdf](https://izumi.finance/paper/dswap.pdf)
