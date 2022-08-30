---
description: The ballot is stronger than the bullet - Abraham Lincoln
---

# Voting

## Vote-Escrowed Token

Popularized by Curve, veToken (Vote-Escrowed Token) allows users to participate in Ref Finance governance.

VeToken, also called veLPT (Vote-Escrowed LP Token), is represented by the voting escrow contract (ref-ve.ref-labs.near). veToken cannot be transferred. The only way to obtain veToken is by locking [REF<>NEAR](https://app.ref.finance/pool/79) LP tokens. The maximum lock time is one year. One LP token locked for one year provides an initial balance of two veTokens.

The corresponding amount of veTokens for one LP Token locked:

| Locking Period | veToken Amount |
| -------------- | -------------- |
| 0              | 0              |
| 1 month        | 1.08           |
| 3 months       | 1.25           |
| 6 months       | 1.5            |
| 12 months      | 2.0            |

The longer you lock your LP Tokens for, the more voting power you have.

## Key concepts&#x20;

* Voting DOES NOT lock your veLPT
* Two types of voting: Farm emissions voting (Gauge weight voting) and/or Governance voting
* veLPT holders can vote on multiple governance proposals at the same time BUT can only vote on one farm for the community incentives allocation
* veLPT CANNOT be split into different votes/proposals, each vote will use the full amount of veLPT&#x20;
* As long as the proposal is active, voters CAN cancel their vote&#x20;
* When veLPT is burned (to unlock REF<>NEAR LP Tokens), any related ongoing vote(s) will be canceled accordingly, thus giving priority to unstaking LP Tokens

## Farm emissions voting

Or called Gauge weight voting, is the ability for users to allocate their veLPT towards one farm.&#x20;

Every month, Ref would release its REF tokens incentive budget and the allocation to the corresponding farms. **10%** of that incentive budget is to be allocated by the community itself.&#x20;

VeLPT holders can vote for their preferred/favourite farm to gain the maximum of that community reward emission.

For every single farm, the community allocation is calculated by taking the ratio of veLPT voted for the farm to the total of veLPT voted across all farms, multiplied by the community incentive budget.

{% hint style="info" %}
Once the Farm emissions voting period is completed, the Ref Finance DAO (ref-finance.sputnik-dao.near) will verify the results and allocate the rewards accordingly. The emission of the community rewards will be effective the next month
{% endhint %}

## Governance voting

veLPT holders can participate to key governance proposals.&#x20;

At the beginning, only trusted members and corresponding whitelisted addresses can create a governance proposal.&#x20;

Two types of proposal can be created:

1. Poll
2. Yes/No

The possible voting period (duration) will be:

* 3 days
* 7 days
* 14 days
* 30 days

## All-in-one voting abstract and process owners

![](<../.gitbook/assets/Ref veToken Swimlane Diagram.jpg>)

## How to vote on farm emissions?

First, make sure that you are connected to Ref Finance with your wallet.

### Step 1:  Access Vote page&#x20;

<figure><img src="../.gitbook/assets/Screen Shot 2022-08-23 at 09.27.23.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screen Shot 2022-08-23 at 09.34.27.png" alt=""><figcaption></figcaption></figure>

In order to vote on farm emissions, you will need to have veLPT. Please refer to [Voting](voting.md#vote-escrowed-token).

### Step 2: Lock your REF<>NEAR LP Tokens <a href="#step-2-lock-lp-tokens" id="step-2-lock-lp-tokens"></a>

<figure><img src="../.gitbook/assets/Screen Shot 2022-08-23 at 09.42.45.png" alt=""><figcaption></figcaption></figure>

Please select your locking period, from 1 month to 12 months.

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 09.55.57.png>)

Enter the amount of LP Tokens you would like to lock. Then check the details before confirming/locking.&#x20;

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 10.12.13.png>)

Once you have your REF<>NEAR LP Tokens locked, you can verify the amount of LOVE and veLPT here.

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.20.25.png>)

### Step 3: Select & Vote for your desired farm

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.03.19.png>) ![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.10.23.png>)

### Step 4: Verify your vote

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.25.29.png>)

## **How to vote on governance proposals?**

First, make sure that you are connected to Ref Finance with your wallet.

### Step 1: Access Governance Page

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.00.49.png>)

In order to vote on governance proposals, you will need to have veLPT. Please refer to [Voting](voting.md#vote-escrowed-token).

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 11.33.30.png>)

### Step 2: Vote on the desired proposal(s)

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 13.55.08.png>)

### Step 3: Vote!

![](<../.gitbook/assets/Screen Shot 2022-08-23 at 13.57.15.png>)
