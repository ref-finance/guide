---
description: Liquidity Pools
---

# Pooling

Ref Finance charges a customisable fee for all trades. The fee depends on the pool fee, which is defined at the creation of the pool, and cannot be modified once the pool is created. The pool fee usually varies from 0.05% to 0.3%.&#x20;

A liquidity pool is a pool of two or three tokens, e.g. NEAR and REF tokens. This pool is what allows users to trade the two tokens.&#x20;

Contrary to the Stableswap pool or Tri-Pool (three tokens, cf. [Stableswap function](overview.md)), only liquidity pools with two tokens are fully permissionless. Anyone can create a two-token liquidity pool on Ref Finance.

Users can earn a share of the trading fees by depositing tokens into the pool (also known as "adding liquidity"). Users will receive LP tokens, representing their share of the pool.&#x20;

## Pool APR

Pool APR is the yield you accrue by adding liquidity to a pool. You earn 80% of the pool fee for all trades on the associated pair (or triple for stablecoin pool) proportional to your share of the pool.&#x20;

![](<../.gitbook/assets/Mind Map(3) (2).jpg>)

{% hint style="info" %}
For regular pools (Swap function), if there is no account to receive the Referral Fee, it goes to all LPs of that pool as a form of increased LP tokens

For stablecoin pools (StableSwap function), if there is no account to receive the Referral Fee, it goes to the Protocol Fee as a form of increased LP tokens
{% endhint %}

Fees are added to the pool, accrue in real-time, and can be claimed when you withdraw your Liquidity.

{% hint style="info" %}
Your share will be accrued in real-time and will be paid in addition to your existing position when you remove liquidity from the pool
{% endhint %}

Providing liquidity is not without risk, as you may be exposed to _Divergence Loss_ or _Imparmanent Loss (IL)._

> Simply put, impermanent loss is the difference between holding tokens in an AMM and holding them in your wallet. - [Beginner’s Guide to (Getting Rekt by) Impermanent Loss](https://blog.bancor.network/beginners-guide-to-getting-rekt-by-impermanent-loss-7c9510cb2f22), Nate Hindman, 2020

Or in other words, Liquidity Providers (LPs) can make more money by not providing liquidity into Ref Finance.

## How to add liquidity to a pool?

First, make sure that you are connected to Ref Finance with your wallet.

### Step 1: Open the list of pools by Clicking on Pools > View Pools

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 20.52.27.png>) ![](<../.gitbook/assets/Screen Shot 2022-03-07 at 20.52.55.png>)

### Step 2: Find the pool you want to add tokens into, you can use the search bar function

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.01.17.png>)

### Step 3: After finding the corresponding pool, verify the details of the pool (i.e. Pool Fee)&#x20;

If you cannot find the pool you want to provide liquidity into OR if you are not satisfied with the pool fee and/or pool ratio, please go to [How to create a pool](pooling.md#how-to-create-a-pool)? &#x20;

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.03.23 (1).png>)

### Step 4: Click on Add Liquidity

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.11.33.png>)

### Step 5: Enter the amount you want

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.16.16 (1).png>)

### Step 6: Select Add Liquidity

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.16.16.png>)

### Step 7: Approve the transaction (i.e. using NEAR wallet)

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.17.53.png>)

Congrats, you are now a liquidity provider on Ref Finance!

## How to create a pool?

First, make sure that you are connected to Ref Finance with your wallet.

When do you need to create a new pool on Ref Finance? Usually when:

1. The pool exists but you are not satisfied with the existing pool fee: either you think the pool fee is too high or too low
2. The pool exists but you think the ratio (reserves token A to reserves token B) is not accurate&#x20;
3. The pool simply does not exist yet

### Step 1: Click on Pools > Create New Pool

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.20.04.png>)

### Step 2: Select both tokens

Order does not matter. For example, if you want to provide REF and DAI tokens. You can select REF in the left field and DAI in the right field.&#x20;

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.21.36.png>)

### Step 3: Select the pool fee

As a LP, you need to find the right balance between having an attractive/competitive swap fee for traders and mitigating the risk of your Divergence Loss, by increasing the pool APR with higher fee, for example.

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.25.39.png>)

### Step 4: Verify information

### Step 5: Click on Create

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.26.41.png>)

### Step 6: Approve the transaction (i.e. using NEAR wallet)

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.27.57.png>)

Congrats, you have created a pool! You can now provide liquidity to the new pool by following the guide [How to add liquidity to a pool?](pooling.md#how-to-add-liquidity-to-a-pool)

## How to track your liquidity position(s)?

First, make sure that you are connected to Ref Finance with your wallet.

### Step 1: Click on Pools > Your Liquidity

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.29.45.png>)

## How to remove liquidity from a pool?

First, make sure that you are connected to Ref Finance with your wallet.

### Step 1: Click on Pools > Your Liquidity

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.29.45.png>)

### Step 2: Select the pool you want to remove liquidity from&#x20;

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.29.45 (1).png>)

### Step 3: Enter the amount of LP tokens (shares) you want to remove

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.34.21.png>)

### Step 4: Click on Remove Liquidity

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.34.37.png>)

### Step 5: Approve the transaction (i.e. using NEAR wallet)

![](<../.gitbook/assets/Screen Shot 2022-03-07 at 23.36.21.png>)
