---
description: RHEA’s NEAR LST — Liquid Staking for $NEAR, Multichain
---

# Liquid Staking Tokens (LST)

RHEA LST is the first multichain liquid staking protocol purpose-built for $NEAR. It allows users to stake $NEAR and receive $rNEAR, a yield-bearing token that can be used across chains — all from their original wallets, on their original chains.

### What is $rNEAR?

$rNEAR is the receipt token users receive upon staking $NEAR with the rNEAR Protocol. As PoS rewards continuously accrue, the value of $rNEAR increases relative to $NEAR.

Users can unstake $rNEAR at any time to get their staked $NEAR back.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe0JU8mxOPjEmHQrBGgR8qWXXYFyxHdWfbmXKATAdCeauvR2jAV__tjha0G2keys9oR-saa_Wi7KOTaUNrnBcF0ldswcJTunrUUFOnBJdZ6rELuruyqslqnVy_Q6pyDK3TpKHpP-Q?key=jj6huYDscW93vCrr-SeUvA" alt=""><figcaption></figcaption></figure>



* $rNEAR is minted when users stake $NEAR and is burned when they unstake.
* It accrues staking rewards over time — its value increases as the NEAR it represents grows.
* $rNEAR follows the **NEP-141 standard** and can be bridged easily to other ecosystems (ERC-20, SPL, etc.).\


> $NEAR holders on other chains like Solana, BSC, etc, can also access NEAR liquid staking natively on their chain

### Native Staking & Unstaking&#x20;

* Stake: Deposit $NEAR into the RHEA contract → instantly receive $rNEAR at the current exchange rate.
* Unstake:
  * Instant Unstake – withdraw immediately via RHEA DEX with a small fee
  * Standard Unstake – wait 4 epochs(\~30hours)\


Each $rNEAR is backed by more $NEAR over time as staking rewards are accrued — increasing its value in NEAR terms.

### Validator Strategy

RHEA maintains a decentralized, weighted pool of NEAR validators selected based on:

* Reward performance (with time-weighting)
* Online uptime stability
* Staking ratio
* Community reputation\


Scores are calculated automatically and periodically reviewed by the RHEA DAO for optimal decentralization and performance.



### Common Questions:

> #### Why Can’t I Get 1 rNEAR by Staking 1 NEAR?

As PoS rewards accumulate over time, $rNEAR appreciates in value, meaning the price of $rNEAR will always be higher than the price of $NEAR.&#x20;

You don’t need to worry about staking a certain amount of NEAR and receiving less when you unstake.&#x20;

The amount of $NEAR you receive when you unstake will always be greater than or equal to the amount you initially staked.



> #### When Does Staked NEAR Start Earning PoS Rewards?

PoS rewards are based on Epochs, not Blocks. An Epoch lasts approximately 7 hours, depending on the block production speed.

Staked $NEAR does not immediately start generating PoS rewards because PoS rewards require the staked $NEAR to be present from the start of the Epoch. NEAR added after the Epoch begins will not earn rewards for that Epoch.

To reduce frequent staking actions, we will automatically stake the NEAR in the current LST contract at the end of the current Epoch.



> #### If I Stake NEAR, Does the Current Epoch Not Generate Any Rewards?

No, users still earn rewards during the current Epoch. However, these rewards do not come from PoS rewards. Instead, they come from the Incentive Mechanism.

To encourage more users to migrate to rNEAR, we have activated the incentive mechanism to compensate for the loss of rewards in the first Epoch.



> #### How Does the Incentive Mechanism Work?

Every 10 minutes, the incentive mechanism checks the current $rNEAR price against the price from 30 days ago and calculates the PoS Reward APY.

Based on this APY, the incentive mechanism adds an additional 1% through a compensation system.



### The Technology Behind: Cross Chain NEAR Liquid Staking

While most LST protocols operate within a single chain, RHEA aligns with NEAR’s multichain vision, enabling liquid staking of $NEAR to be initiated and utilized across multiple source and destination chains, with a native user experience.



### How it Works&#x20;

**If Cross-Chain Messaging Is Available**

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdOR_oCMV1p-yQu4tbkKuqw-zcveiTWhM42dUguaQEt3lpnPrnxwbIqLe1WJEEETHnL26kih93nYASdtPs_m5w92E_uYpvA41a2HgG9VpObBZGNW8S7ym-w9-3lsPybnyga_TpqVw?key=SLv95-TUbNFtc6871tvhRw" alt=""><figcaption></figcaption></figure>

\
RHEA deploys a lightweight **Account Abstraction (AA) contract:**\


* Receives user-signed staking instructions via message bridge or direct wallet intent
* Delivers $NEAR or $rNEAR back to the user on their original chain



✅ Advantage: To the user, staking feels native—like using any local DeFi protocol.



#### If Only Token Bridge Is Available

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeh-w5rfMrmI70xo2i4B7G-EjCEmY2mZdC17D92ZMkAZZ_mJBedeYQDTDcdD0-Anp0L9iv-GB1ln21GVdk0t1iPK9gkwCTkFkjND1YsPICx5PLdTukZqcD_H6gGSEHQvQew6N8SSw?key=SLv95-TUbNFtc6871tvhRw" alt=""><figcaption></figcaption></figure>



RHEA uses External Account Management (EAM) via NEAR Chain Abstraction:

1. Sub-account Creation – A NEAR sub-account is created and linked to the user’s wallet using derived keys.
2. Authorization – User signs a one-time request to link an embedded NEAR wallet to their sub-account.
3. Interaction – Users control the sub-account via RHEA frontend to stake, unstake, or access NEAR DeFi.



✅ Advantage: Users gain full access to NEAR staking and DeFi, using their existing wallet and chain.



### Summary:

* $rNEAR appreciates over time due to PoS rewards.
* The price of $rNEAR will always be higher than the price of $NEAR.
* Staked NEAR starts earning PoS rewards only at the beginning of an Epoch.
* Incentive mechanism compensates users in the first Epoch to encourage migration to rNEAR.
* Incentive mechanism adds an additional 1% on top of the PoS Reward APY to further boost earnings.



**RHEA LST makes $NEAR staking borderless, non-custodial, and yield-optimized.**
