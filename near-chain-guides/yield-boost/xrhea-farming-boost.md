# xRHEA Farming Boost

### Overview

xRHEA Farming Boost allows users to lock xRHEA tokens in exchange for boosted incentive rewards on their [farm APYs](https://app.rhea.finance/pools?activeTab=farm). The longer the lock-up period, the greater the boost — up to a maximum of 6 months.

<div data-full-width="true"><figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 4.50.03 PM.png" alt="" width="563"><figcaption><p><a href="https://app.rhea.finance/stake"> xRHEA Farming Boost</a> interface with boost ratio range and lock-up period up to 6 months</p></figcaption></figure></div>

### List of 7 Boosted farm Pools on RHEA

| Farm Pools     | Link                                                                       |
| -------------- | -------------------------------------------------------------------------- |
| rNEAR-NEAR     | [https://app.rhea.finance/sauce/6494](https://app.rhea.finance/sauce/6494) |
| RHEA-NEAR      | [https://app.rhea.finance/pool/6458](https://app.rhea.finance/pool/6458)   |
| NEAR-ZEC       | [https://app.rhea.finance/pool/6065](https://app.rhea.finance/pool/6065)   |
| NEAR-PUBLIC    | [https://app.rhea.finance/pool/6503](https://app.rhea.finance/pool/6503)   |
| mpDAO - STNEAR | [https://app.rhea.finance/pool/5438](https://app.rhea.finance/pool/5438)   |
| nBTC - NEAR    | [https://app.rhea.finance/sauce/5949](https://app.rhea.finance/sauce/5949) |
| DOG - NBTC     | [https://app.rhea.finance/pool/6424](https://app.rhea.finance/pool/6424)   |

### How it works

Lock xRHEA → Earn Weight → Get Boosted APYs on Farming

The program operates in two sections:

1. Weight Algorithm – Calculates your Weight based on the amount and duration of xRHEA locked.
2. Farming Multiplier Algorithm – Converts your Weight into a reward boost factor.



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

Where:

* Y = user's Weight
* boost\_suppress\_factor = 100
* base = 38634105686174997042188779520



#### Farming Multiplier Table

| Weight Amount | Farming Multiplier |
| ------------- | ------------------ |
| 1,500         | 1.111x             |
| 15,000        | 1.205x             |
| 150,000       | 1.300x             |
| 1,500,000     | 1.394x             |
| 15,000,000    | 1.488x             |



### Example: How Rewards Are Distributed

Imagine the rNEAR-NEAR farm emits 9.89% APY in incentive rewards.

#### Case 1:  New User Without xRHEA Lock when farming

<table><thead><tr><th width="82.4423828125">User</th><th width="207.7041015625">USD value staked in farm</th><th width="107.9534912109375">Weight </th><th width="111.199951171875">Multiplier</th><th width="79.728515625">APY</th><th>Boosted APY</th></tr></thead><tbody><tr><td>Charlie</td><td>1,000</td><td>0</td><td>1.000x</td><td>9.89%</td><td>-</td></tr></tbody></table>



#### Case 2: xRHEA Lock Boosted Users when farming&#x20;

<table><thead><tr><th width="87.64453125">User</th><th width="207.65869140625">USD value staked in farm</th><th width="96.72119140625">Weight </th><th width="110.9932861328125">Multiplier</th><th width="86.28125">APY</th><th>Boosted APY </th></tr></thead><tbody><tr><td>Alice </td><td>500</td><td>150,000</td><td>1.300x</td><td>9.89%</td><td>12.85%</td></tr><tr><td>Bob</td><td>50</td><td>150</td><td>1.056x</td><td>9.89%</td><td>10.44%</td></tr></tbody></table>



### Updated incentive rewards allocation for rNEAR-NEAR farm

**Alice: 12.85% APY**

**Bob: 10.44% APY**

**Charlie: 9.89% APY (Not Boosted)**



## How to stake xRHEA for farming boost: Step by Step walkthrough

### Step 1: Go to [https://app.rhea.finance/stake](https://app.rhea.finance/stake) and connect your wallet&#x20;

### Step 2: Click Farming Boost:  &#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 5.03.05 PM (1).png" alt=""><figcaption></figcaption></figure>

<p align="center"></p>

### Step 3: Choose RHEA or xRHEA:  &#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 5.06.24 PM (2).png" alt=""><figcaption><p>Stake requires minimum of 1.7 RHEA/xRHEA</p></figcaption></figure>



### Step 4: Pick Boost Ratio Range based on your Lock time.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 5.10.17 PM (1).png" alt=""><figcaption><p>Lock-up period from 1~6 month</p></figcaption></figure>



### Step 4.1: If you hover to the Boosted ratio text, there will be a quick preview pop-up of your Boosted Farm APYs based on Stake Amount and Lock time of xRHEA

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 5.12.47 PM (2).png" alt=""><figcaption></figcaption></figure>

<p align="center"></p>

### Step 5: Click Stake and you're done!&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 6.02.52 PM.png" alt=""><figcaption></figcaption></figure>



### Step 6:  you head over to the [farms section](xrhea-farming-boost.md#step-1-go-to-https-app.rhea.finance-stake-and-connect-your-wallet) on Liquidity tab, you can now see your boosted APY figures under the APYs.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2025-09-15 at 6.09.39 PM (1).png" alt=""><figcaption></figcaption></figure>



