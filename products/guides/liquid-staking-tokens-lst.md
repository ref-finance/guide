---
description: RHEA’s NEAR LST — Liquid Staking for $NEAR, Multichain
hidden: true
---

# Liquid Staking Tokens (LST)

RHEA LST is the first multichain liquid staking protocol purpose-built for $NEAR. It allows users to stake $NEAR and receive $rNEAR, a yield-bearing token that can be used across chains — all from their original wallets, on their original chains.



#### What is $rNEAR?

* $rNEAR is minted when users stake $NEAR and is burned when they unstake.
* It accrues staking rewards over time — its value increases as the NEAR it represents grows.
* $rNEAR follows the **NEP-141 standard** and can be bridged easily to other ecosystems (ERC-20, SPL, etc.).\
  \


$NEAR holders on other chains like Solana, BSC, etc, can also access NEAR liquid staking natively on their chain\


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



### Cross Chain NEAR Liquid Staking

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

\
\
Why RHEA?

✅ Multichain by design

✅ Native wallet, native UX

✅ No custody, fully on-chain

✅ Built by the leading DeFi protocol on NEAR



**RHEA LST makes $NEAR staking borderless, non-custodial, and yield-optimized.**
