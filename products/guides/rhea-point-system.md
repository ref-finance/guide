# RHEA Point System

## **Introduction**

The RHEA Points System is designed to incentivise platform activity by rewarding users for trading, liquidity provision, and community engagement. Points are accumulated based on specific actions and can be used to enhance user participation in the ecosystem.



## **Point Categories & Earning Mechanisms**

### **1. Trading Points**

Users earn points through token swaps, using the [aggregator bridge](https://dex.rhea.finance/bridge), and margin trading.

| Action                                                                                                       | Point Calculation                   | Rule                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Swap $50                                                                                                     | 10 Points per $50                   | Minimum transaction: $50                                                                                                                                                                                                                                                                                                                                                                                              |
| Swap more than $1000 in a single transaction                                                                 | 200 Points + 50% Boost = 300 Points | <p>Applies to Selected Pool Tokens:<br></p><p>•<a href="https://dex.rhea.finance/pool/79"> Ref-NEAR</a><br>• <a href="https://dex.rhea.finance/pool/4512">USDC-NEAR</a><br>• <a href="https://dex.rhea.finance/sauce/5949">nBTC-NEAR</a><br>• <a href="https://dex.rhea.finance/meme">Meme Season Pools</a><br>•<a href="https://dex.rhea.finance/pools?activeTab=stable"> Stable pools (Stablecoin-BTC pair)</a></p> |
| Bridge $50 via the [Aggregator Bridge ](https://dex.rhea.finance/bridge)                                     | 10 Points per $50                   | Minimum transaction: $50                                                                                                                                                                                                                                                                                                                                                                                              |
| Bridge more than $1000 in a single transaction via the [Aggregator Bridge ](https://dex.rhea.finance/bridge) | 200 Points + 50% Boost = 300 Points | EVM to NEAR USDC bridge                                                                                                                                                                                                                                                                                                                                                                                               |
| Margin Trade $50                                                                                             | 10 Points per $50                   | Minimum transaction: $50                                                                                                                                                                                                                                                                                                                                                                                              |
| Margin Trade more than $1000 in single transaction                                                           | 200 Points + 50% Boost = 300 Points | Applies to all meme season pools                                                                                                                                                                                                                                                                                                                                                                                      |

### **Example Calculation:**

*   A $1,000 total swap in Selected Pool Tokens:

    * Base points: **(1,000 ÷ 50) × 10 = 200 points**
    * **50% boost** for $1,000+ swap: **+100 points**
    * **Total: 300 points**



### 2. Liquidity Pool

Users earn points by supplying assets to liquidity pools or borrowing assets.

#### Lending & Borrowing Rewards

| Action                    | Point Calculation | Rules                |
| ------------------------- | ----------------- | -------------------- |
| Supply $100 TVL for 1 Day | 100 Points        | Receives Point Daily |
| Borrow $100 TVL for 1 Day | 300 Points        | Receives Point Daily |

> \*Note: Minimum deposit & borrow is $100 per transaction, no points for amounts below $100

#### Liquidity Pool Contributions

| Liquidity Pool    | Point Calculation                      | Boosted Pools                                                                                                                                                                                                                                                                                                                                  |
| ----------------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $100 TVL in Pool  | 200 points per day                     | -                                                                                                                                                                                                                                                                                                                                              |
| $1000 TVL in Pool | 2,000 points + 50% boost = 3000 Points | <p><a href="https://dex.rhea.finance/pool/79">Ref-NEAR</a><br><a href="https://dex.rhea.finance/pool/4512">USDC-NEAR</a><br><a href="https://dex.rhea.finance/sauce/5949">nBTC-NEAR</a><br><a href="https://dex.rhea.finance/meme">Meme Season Pools</a><br><a href="https://dex.rhea.finance/pools?activeTab=stable">Stablecoin pools</a></p> |

**Example Calculation:**

* Provide a total of $1,000 in the USDC-NEAR pool:
  * Base points: **(1,000 x 2) = 2000 points**
  * **50% boost** for $1,000+ swap: **+1000 points**
  * **Total: 3000 points**



> Note: Locked LP from users will not count toward points as Locked LP is intended for LP deployers to utilize the feature and provide a sense of safety for the community.

### 3. Community Points

Earn points through social media engagement, referrals, and platform advocacy.

<table><thead><tr><th>Type </th><th width="280.83203125">Action</th><th>Point Calculation</th></tr></thead><tbody><tr><td>Twitter Thread (DeFi topic)</td><td>Must meet engagement criteria</td><td>To Be Determined</td></tr><tr><td>Educational Guide</td><td>Must be original &#x26; informative</td><td>To Be Determined</td></tr><tr><td>Referral (New User)</td><td>Referrers earn <strong>10% of their referees' points</strong></td><td><p><strong>Example:</strong></p><p></p><p><strong>Referee (B):</strong> Earns <strong>100 points</strong> upon joining.</p><p></p><p><strong>Referrer (A):</strong> Receives <strong>10% of the referee’s points</strong> (e.g., if B gets <strong>100 points</strong>, A gets <strong>10 points</strong>)</p></td></tr></tbody></table>



## Multipliers & Bonus Mechanisms

Users can earn bonus points by maintaining long-term engagement on Margin Trading and Supply/ Borrow

### Margin Trading

<table><thead><tr><th width="345.86328125">Activity Streak</th><th>Point Multiplier Applied</th><th data-hidden></th></tr></thead><tbody><tr><td>10 consecutive days of swaps</td><td>1.2x every future swaps</td><td></td></tr><tr><td>20 consecutive days of swaps</td><td>1.5x every future swaps</td><td></td></tr><tr><td>30 consecutive days of swaps</td><td>2x every future swaps</td><td></td></tr></tbody></table>

### Supply and Borrow&#x20;

<table><thead><tr><th width="184.37109375">Activity Streak</th><th width="285.75390625">Point Multiplier Applied (After 10 Days)</th><th>Point Multiplier Applied (After 20 Days)</th></tr></thead><tbody><tr><td>$100 TVL supplied for 1 day = 100 points</td><td>1.2x</td><td>1.5x</td></tr><tr><td>$100 TVL borrowed for 1 day = 100 points</td><td>1.2x</td><td>1.5x</td></tr></tbody></table>

### Liquidity Provider

<table><thead><tr><th width="183.46875">Activity Streak</th><th>Point Multiplier Applied (After 10 Days)</th><th>Point Multiplier Applied  (After 20 Days)</th></tr></thead><tbody><tr><td>$100 LP supplied for 1 day = 200 points</td><td>1.2x</td><td>1.5x</td></tr></tbody></table>

