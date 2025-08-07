# xRHEA Lending Boost

### Overview

xRHEA Lending Boost allows users to lock xRHEA tokens in exchange for boosted incentive rewards on Rhea Lending. The longer the lock-up period, the greater the boost — up to a maximum of 6 months.

Note: Boost only affects incentive rewards. It does not impact base lending interest rates.

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-05 at 9.08.41 PM.png" alt="" width="563"><figcaption><p> <a href="https://t.co/Bk0wJfmeZ8">xRHEA Lending Boost</a> interface with boost ratio range and lock-up period up to 6 months</p></figcaption></figure>

### How it works

Lock xRHEA → Earn Weight → Get Boosted Rewards

The program operates in two sections:

1. Weight Algorithm – Calculates your Weight based on the amount and duration of xRHEA locked.\
   \


Farming Multiplier – Converts your Weight into a reward boost factor.



### 1. Weight Algorithm

Your Weight is determined by:

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcK-zvUam_7OLgZSrZecUvTX29tv-8DFbtOY6-QNkVTB5c8GnGMUsgEs3-E2AuqxlkqffiIBH3xSXW0bhyElyJp3ysTbblAI57GFpYB0r4wmIs3eBngR-4OPKkf1v16e2PwZXFgjw?key=eHiEe45NobqJ6LiYnRuSDg" alt=""><figcaption></figcaption></figure>



Where:

* Y = Weight
* X = The amount of xRHEA locked
* D = Lock duration (from 30 to 180 days)
* D\_min = 30
* D\_max = 180
* M\_min = 10,000

M\_max = 30,000



### Example Weight Table&#x20;

| xRHEA Locked  | Lock Duration | Weight Received |
| ------------- | ------------- | --------------- |
| 100 xRHEA     | 1 Month       | 100             |
| 100 xRHEA     | 3.5 Months    | 200             |
| 100 xRHEA     | 6 Months      | 300             |

> The longer you lock, the higher the Weight (up to 3x boost at 180 days)



### 2. Farming Multiplier Algorithm

Once Weight is calculated, it’s converted into a Farming Multiplier, which boosts the user’s share of the incentive rewards pool.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcK09JUsm53m6a0pSoXwiZeeeyL0UgYuCJCVztKYFq2N_a3BdOQBfLlAgfhbmibp3a-ejRVcZVWRswzD5ZrXZs_KLw33B3edUfFSAFkTtzuD52v6nnvfk5J0z6MMw4ScIVMGhqMTg?key=eHiEe45NobqJ6LiYnRuSDg" alt=""><figcaption></figcaption></figure>

* Y = user's Weight
* boost\_suppress\_factor = 100
* base = 2137469933345.874131511402299392



#### Farming Multiplier Table

| Weight Amount | Farming Multiplier |
| ------------- | ------------------ |
| 500           | 1.056x             |
| 5,000         | 1.137x             |
| 50,000        | 1.218x             |
| 500,000       | 1.300x             |
| 5,000,000     | 1.381x             |
| 50,000,000    | 1.462x             |



### Example: How Rewards Are Distributed

Imagine the USDC lending pool emits 200 wNEAR/day in incentive rewards.

#### Case 1: Boosted Users Only&#x20;

| User   | Supplied USDC | Weight  | Multiplier | Boosted Shares  |
| ------ | ------------- | ------- | ---------- | --------------- |
| Alice  | 500           | 500,000 | 1.300x     | 650             |
| Bob    | 50            | 500     | 1.056x     | 52.8            |

* Total Boosted Shares: 702.8\

* Reward Allocation:
  * Alice: 184.96 wNEAR/day
  * Bob: 15.2 wNEAR/day



#### Case 2:  New User Without xRHEA Lock

| User    | Supplied USDC | Weight  | Multiplier | Boosted Shares  |
| ------- | ------------- | ------- | ---------- | --------------- |
| Charlie | 1,000         | 0       | 1.000x     | 1,000           |

* New Total Boosted Shares: 1,702.8\

* Updated Reward Allocation:
  * Alice: 76.34 wNEAR/day
  * Bob: 6.2 wNEAR/day
  * Charlie: 117.44 wNEAR/day
