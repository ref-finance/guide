---
hidden: true
---

# Copy of RHEA Point System Season 2 done (with lending borrow LP)

## **Introduction**

The RHEA Points System is designed to incentivise platform activity by rewarding users for trading, liquidity provision, and community engagement. Points are accumulated based on specific actions and can be used to enhance user participation in the ecosystem.

In Season 2, **every action you take on RHEA can earn you points** — and those points can be redeemed for oRHEA during designated redemption windows (dates to be announced).

The more active you are, the more oRHEA you can secure.



## **Point Categories & Earning Mechanisms for oRHEA**

### **1. Trading Points**

Users earn points through token swaps, using the [aggregator bridge](https://dex.rhea.finance/bridge), and margin trading.

| Action                                                                                                       | Point Calculation                   | Rule                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Swap $100                                                                                                    | 10 Points per $100                  | Minimum transaction: $100                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Swap more than $1000 in a single transaction                                                                 | 100 Points + 20% Boost = 120 Points | <p>Applies to Selected Pool Tokens:<br></p><ul><li><a href="https://app.rhea.finance/pool/6458">RHEA–NEAR</a></li><li><a href="https://app.rhea.finance/pool/4512">USDC–NEAR</a></li><li><a href="https://app.rhea.finance/sauce/5949">nBTC-NEAR</a></li><li><a href="https://app.rhea.finance/pool/4276">BlackDragon-NEAR</a></li><li><a href="https://app.rhea.finance/pools?activeTab=stable">Stable Pools </a></li><li><a href="https://app.rhea.finance/pool/6503">PUBLIC-NEAR</a></li><li><a href="https://app.rhea.finance/poolV2/17208628f84f5d6ad33f0da3bbbeb27ffcb398eac501a31bd6ad2011e36133a1%3C%3Etoken.rhealab.near@100">RHEA-USDC </a></li><li><a href="https://app.rhea.finance/pool/5154">NEAR-WBNB </a></li><li><a href="https://app.rhea.finance/sauce/6494">rNEAR-NEAR</a></li><li>wBTC Pools </li></ul> |
| Bridge $100 via the [Aggregator Bridge ](https://dex.rhea.finance/bridge)                                    | 10 Points per $100                  | Minimum transaction: $100                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Bridge more than $1000 in a single transaction via the [Aggregator Bridge ](https://dex.rhea.finance/bridge) | 100 Points + 20% Boost = 120 Points | EVM to NEAR USDC bridge only                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Margin Trade $50                                                                                             | 10 Points per $50                   | Minimum transaction: $50                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Margin Trade more than $1000 in single transaction                                                           | 200 Points + 20% Boost = 240 Points | -                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### **Example Calculation:**

*   A $1,000 total swap in Selected Pool Tokens:

    * Base points: **= 100 points**
    * **20% boost** for $1,000+ swap = **20 points**
    * **Total: 120 points**



### 2. Liquidity Pool

Users earn points by supplying assets to liquidity pools or borrowing assets.

#### Lending & Borrowing Rewards

| Action                    | Point Calculation | Rules                |
| ------------------------- | ----------------- | -------------------- |
| Supply $100 TVL for 1 Day | 50 Points         | Receives Point Daily |
| Borrow $100 TVL for 1 Day | 100 Points        | Receives Point Daily |

> \*Note: Minimum deposit & borrow is $100 per transaction, no points for amounts below $100

#### Liquidity Pool Contributions

| Liquidity Pool      | Point Calculation                             | Boosted Pools                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------- | --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $100 TVL in Pool    | 50 points per day                             | -                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| $10,000 TVL in Pool | 5000 Points per day + 5% Boost = 5250 Points  | <p></p><p>Applies to Selected Pool Tokens:<br></p><ul><li><a href="https://app.rhea.finance/pool/6458">RHEA–NEAR</a></li><li><a href="https://app.rhea.finance/pool/4512">USDC–NEAR</a></li><li><a href="https://app.rhea.finance/sauce/5949">nBTC-NEAR</a></li><li><a href="https://app.rhea.finance/pool/4276">BlackDragon-NEAR</a></li><li><a href="https://app.rhea.finance/pools?activeTab=stable">Stable Pools </a></li><li><a href="https://app.rhea.finance/pool/6503">PUBLIC-NEAR</a></li><li><a href="https://app.rhea.finance/poolV2/17208628f84f5d6ad33f0da3bbbeb27ffcb398eac501a31bd6ad2011e36133a1%3C%3Etoken.rhealab.near@100">RHEA-USDC </a></li><li><a href="https://app.rhea.finance/pool/5154">NEAR-WBNB </a></li><li><a href="https://app.rhea.finance/sauce/6494">rNEAR-NEAR</a></li><li>wBTC Pools </li></ul> |



> Note: Locked LP from users will not count toward points as Locked LP is intended for LP deployers to utilize the feature and provide a sense of safety for the community.

### 3. Community Points

Earn points through social media engagement, referrals, and platform advocacy.

We reward active **community builders and contributors**.

* RHEA Insider vault campaign - in Discord
  * The engage point will be converted to RHEA points by the end of the campaign
* Onboarding referrals
  * Counted by how many users have been onboarded through the RHEA referral link and will be added by the end of the campaign
*   Kaito yapping (approved discussions & shilling)

    * read our [article](https://x.com/rhea_finance/status/1955283722187706621) on X&#x20;

    NOTE: Every tweet must tag @rhea\_finance



## Multipliers & Bonus Mechanisms

Users can earn bonus points by maintaining long-term engagement on Margin Trading and Supply/ Borrow

### Margin Trading

<table><thead><tr><th width="345.86328125">Activity Streak</th><th>Point Multiplier Applied</th><th data-hidden></th></tr></thead><tbody><tr><td>15 consecutive days of trades</td><td>1.2x every future trades</td><td></td></tr><tr><td>30 consecutive days of trades</td><td>1.5x every future trades</td><td></td></tr><tr><td>60 consecutive days of trades</td><td>2x every future trades</td><td></td></tr></tbody></table>

### Supply and Borrow&#x20;

<table><thead><tr><th width="147.7451171875">Activity Streak</th><th width="285.75390625">Point Multiplier Applied (After 30 Days)</th><th>Point Multiplier Applied (After 60 Days)</th></tr></thead><tbody><tr><td>$100 TVL supplied for 1 day = 50 points</td><td>1.2x</td><td>1.5x</td></tr><tr><td>$100 TVL borrowed for 1 day = 100 points</td><td>1.2x</td><td>1.5x</td></tr></tbody></table>

### Liquidity Provider

<table><thead><tr><th width="388.6396484375">Activity Streak</th><th>Point Multiplier Applied (After 30 Days)</th></tr></thead><tbody><tr><td>$100 LP supplied for 1 day = 100 points</td><td>1.2x</td></tr></tbody></table>

