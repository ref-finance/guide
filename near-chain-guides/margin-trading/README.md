---
description: >-
  Margin Trading is built on top of Rhea’s Lending product, allowing users to
  provide sufficient collateral to access 1–3x leverage.
---

# Margin Trading

## <sub>**Technical Implementation**</sub>

Reference Document:[ https://hackmd.io/@MarcoSun/SkW-\_2Z\_yl](https://hackmd.io/@MarcoSun/SkW-_2Z_yl)

### Loop-Based Leverage (Before Margin Trading)

Before Margin Trading was introduced, users could manually implement leveraged trading through a series of looping actions:



* **Shorting:**\
  Supply USDC → Borrow NEAR → Swap NEAR to USDC → Supply USDC → Borrow NEAR → ...<br>
* **Longing**:\
  Supply USDC → Borrow USDC → Swap USDC to NEAR → Supply NEAR → Borrow USDC → ...

## Margin Trading

Margin Trading simplifies the user's repeated loop operations into a single action, with steps managed by smart contracts. This makes leveraged trading more accessible and user-friendly.

***

Margin trading is available for:

* **Meme tokens (Selected assets)**
* **NEAR**
* **nBTC**



Users can deposit Stablecoins (USDC, DAI, or USDt) as collateral to open long or short positions with up to 2x leverage on Meme Tokens and 3x leverage on NEAR and nBTC.

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-06 at 5.45.00 PM.png" alt=""><figcaption><p>Margin Trading markets as of current assets</p></figcaption></figure>

## Isolated Positions for Meme Tokens

Due to the low liquidity and high volatility of Meme Tokens, and to avoid impacting the $200M liquidity pool of the main Lending product, we’ve created separate smart contracts (forked Lending contracts) for Meme Tokens. This isolates risk at the contract level.

All USDC used for long and short positions on Meme Tokens comes exclusively from these dedicated Meme Token lending contracts.

## Meme Token Listing Criteria

Not all Meme Tokens can be listed on Margin Trading. To ensure the safety of users and the platform, a Meme Token must have over $100K liquidity on Rhea’s DEX to be eligible for listing.

***

## Liquidation

Liquidation in Margin Trading differs from Lending:

* **Lending:**\
  Uses partial liquidation — only enough assets are liquidated to bring the user's health factor back to a safe level, avoiding full liquidation.<br>
* **Margin Trading:**\
  Involves full liquidation (similar to a total position wipeout). Once a position is liquidated, all assets in that position are sold to repay the Lending debt and compensate the liquidator.<br>

***

## Open-Source Liquidation Bot

The Margin Trading liquidation bot is open-source and available here:\
[https://github.com/burrowHQ/burrowland-liquidation-bot/tree/margin\_trading](https://github.com/burrowHQ/burrowland-liquidation-bot/tree/margin_trading)<br>
