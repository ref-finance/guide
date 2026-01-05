# RHEA Credits

### Overview

The Credit Model is introduced in welcoming Season 3 while recalculate **Season 2 distribution** to improve the fairness of oRHEA redemption.

Previously, oRHEA redemption relied entirely on Points, which led to heavy concentration—where a small number of high-volume users accumulated the majority of redeemable supply. This limited redemption access for most users.

To address this, **Credit** is introduced as a new, daily-based redemption unit while keeping the existing Points system intact for activity tracking.

***

### Key Changes at a Glance

* **Credit replaces Points as the unit for oRHEA redemption**
* Credit is **calculated daily** based on points earned that day
* Credit **accumulates over time**
* Daily Credit gains are **capped by tiers**
* Historical data for **Season 2 will be recalculated**

***

### Definitions

| Term   | Description                                          |
| ------ | ---------------------------------------------------- |
| Points | Original points generated from daily user activity   |
| Credit | New daily, cumulative unit used for oRHEA redemption |
| Season | A defined activity period (current: Season 2)        |
| oRHEA  | Reward asset redeemable using Credit                 |

***

### What Is Credit?

* Credit is a **daily reward unit derived from Points**
* It is calculated **once per day**
* Credits **accumulate over time**
* Credits are used to redeem **oRHEA**
* Points remain unchanged and are still used for tracking and history

***

### Credit Calculation Rules

#### Daily Calculation Principle

* Credit is calculated **independently each day**
* Only the **highest eligible tier** per day is counted
* Credits do **not stack within the same day**
* Points below the minimum threshold earn **no Credit**

***

#### Daily Points → Credit Mapping

| Daily Points Earned | Credit Earned |
| ------------------- | ------------- |
| ≥ 20                | 1 Credit      |
| ≥ 40                | 2 Credits     |
| ≥ 80                | 3 Credits     |
| ≥ 160               | 4 Credits     |

**Notes:**

* Thresholds increase exponentially
* Extra points beyond a tier do not increase daily Credit
* Credit gain is capped per day

**Examples:**

* 45 Points → 2 Credits
* 160 Points → 4 Credits
* 10 Points → 0 Credits

***

### Credit Accumulation

* Credits are **added daily**
* Each day is calculated independently
* Once earned, Credits **cannot be adjusted or removed**
* Total Season 2 Credit is the **sum of all daily Credits**

#### Example

| Day   | Daily Points | Credit Earned | Total Credit |
| ----- | ------------ | ------------- | ------------ |
| Day 1 | 25           | 1             | 1            |
| Day 2 | 90           | 3             | 4            |
| Day 3 | 10           | 0             | 4            |
| Day 4 | 160          | 4             | 8            |

***

### Season 2 Historical Recalculation

#### Scope

* Credit will be recalculated for **all historical days in Season 2**
* Based on each user’s **daily points record**

#### Logic

1. Retrieve daily Points data for Season 2
2. Calculate daily Credit using the tier rules
3. Sum all daily Credits
4. Store Credit as a **new Season 2 field**

**Important:**

* Points data remains unchanged
* Season 1 data is not included

***

### Credit → oRHEA Redemption

* oRHEA redemption now uses **Credit instead of Points**
* Redemption pricing and logic remain unchanged
* Users can only redeem up to their available Credit balance
* Credit cannot go negative
* Over-redemption is not supported

### Difference from RHEA ticket Trade Competitions

| Aspect            | Trade Competition | Credit Model             |
| ----------------- | ----------------- | ------------------------ |
| Calculation Cycle | Campaign-based    | Daily                    |
| Accumulation      | Rule-dependent    | Always cumulative        |
| Volume Advantage  | High              | Capped daily             |
| Focus             | Short-term volume | Consistent participation |
| Redemption Unit   | Points            | Credit                   |

***

