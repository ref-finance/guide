---
description: Solutions for common problems
---

# Help

### _**I am using a ledger, and get UNKNOWN\_ERROR (0x6990) when withdrawing farm rewards.**_

Try withdrawing only 2-3 tokens at a time.

### _**I am using a ledger, and get UNKNOWN\_ERROR (0x6990) when swapping tokens**_

Update your ledger firmware to latest version.

### _**Something went wrong when I swapped, or added/removed tokens from a pool, and now I don't see my tokens or pool shares**_

Although rare, there are times when it appears that tokens have been lost or are missing after a failed transaction on Ref Finance. When this happens:

1. Go to your [account page on the Ref site](https://app.ref.finance/account) to see if your tokens ended up there. If they are, you can withdraw them to your wallet from that page. If this occurred when adding tokens to a pool, try adding them again. If you are using 2FA, and the same thing keeps happening, try disabling it and then re-enable it after you deposit your tokens.
2. If you are missing NEAR, look in your wallet for a token called Wrapped NEAR (wNEAR). Be sure to refresh your wallet a couple of times to make sure it is showing you the latest info. wNEAR is a form of NEAR that can be used in DeFi operations like swapping. 1 wNEAR is always worth 1 NEAR, and you can use the swap page on the Ref site to unwrap it back to NEAR without paying any swap fees.
3. If you still can't find your tokens, then please [fill out this form](https://form.typeform.com/to/jCWPwxI5).

### _**I claimed rewards from a farm, but I don't see them in my wallet**_

After claiming rewards, you need to go to the [main Farms page](https://app.ref.finance/v2farms) and withdraw them to your wallet.

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

### _**I'm trying to swap NEAR, or deposit it into a pool, but the site says I don't have enough in my wallet even though I do**_

The site will not let you swap or deposit an amount of NEAR that will leave less than 0.5 NEAR in your wallet after the transaction. This is to make sure you don't run out of NEAR for gas/transaction fees!

### _**I staked REF a while ago, but the amount of xREF I have is still the same**_

The amount of xREF does not increase. What increases is the value of xREF relative to REF, because REF that has been bought-back from swap fees are continuously added to the pool. This means you will **always** get back more REF than you staked, even if you unstake immediately after staking. See the [FAQ page](faq.md#what-is-xref) for more info about xREF.
