---
hidden: true
---

# xRHEA Lending Boost (draft)

### Lock xRHEA to boost yields on RHEA Lending &#x20;

xRHEA holders have the option to [lock their xRHEA](https://app.rhea.finance/stake?type=stake_lending) to earn increased yields on RHEA's Lending product. The longer the lock-up period, the greater the boost. The maximum lock-up period is at 6 months at the moment.

What yield opportunity does the lock boost provide?

Users who lock xRHEA will receive higher rewards from the Supply and Borrow incentives on [RHEA Lending](https://app.gitbook.com/o/LTjXeL6OzZfyZqbPGdFV/s/gfI2jFBRGflC1pkMyVoh/). These rewards allow users to earn more incentives than they would versus not locking xRHEA.  \[See image]&#x20;

> Note: The yield boost currently applies only to user incentives (the user's lending interest income) and not to Base yields.

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-05 at 9.08.41 PM.png" alt="" width="563"><figcaption><p> <a href="https://t.co/Bk0wJfmeZ8">xRHEA Lending Boost</a> interface with boost ratio range and lock-up up to 6 months</p></figcaption></figure>

### Boost Algorithm Details

The Boost algorithm consists of two parts: the Weight algorithm and the Farming multiplier algorithm.

The Weight algorithm calculates the Weight required to participate in the Farming multiplier based on the user's locked xRHEA Token and lock duration.

The Farming multiplier algorithm calculates the user's actual Boost Ratio based on the Weight obtained from the Weight algorithm.

### Weight Algorithm

Users can decide how long to stake their xRHEA tokens and will receive more Weight the longer they stake.&#x20;

Currently, xRHEA supports a Lock period ranging from 30 Days to 180 Days. If users stake X amount of xRHEA tokens for D days (up to 180 days), the total amount of Weight will be:

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXceqSwH6u-FQUNceiWn4rFZx_RIM6S8odgR4RyPT1uKZARo9d6GLlW51S9U7rnSjYmFaVX3XE72xErD2lgHl1rKAVkuFNE-rO2Ibw1DzJn42sXtuMx6O9a1HU5FdLrUJsdIJBzcTA?key=eHiEe45NobqJ6LiYnRuSDg" alt=""><figcaption></figcaption></figure>

X: xRHEA amount

Y: Weight amount

D: requested locking period

Dmax: the maximum locking duration, such as 180 days

Dmin: the minimum locking duration, such as 30 days

Mmax:  multiple BP ratio related to Mmin, say 30000

Mmin: base BP ratio literally is 10000



The table below shows the amount of xRHEA with lock duration and the corresponding Weight:

| xRHEA to Lock | Months to Lock | Weight to Receive |
| ------------- | -------------- | ----------------- |
| 100           | 1              | 100               |
| 100           | 3.5            | 200               |
| 100           | 6              | 300               |

### Farming Multiplier Algorithm

The Farming multiplier algorithm follows traditional farming logic. It first calculates each user's Share amount, and then distributes the rewards based on the proportion of each user's Share.

Boosted shares are calculated as follows:

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd2ScQFY1W1y6mL9Z3P0-9gOOgS_Kn7gmJWsfcWvUjve7tfziZL1N2BFxy7AwZIlbjojB9NYt3H3kIM1OHUu0HksitkRBHJPQnzDmPqq1yKVu9uPGreTiNKrMe6t7QJxbEi_rp-?key=eHiEe45NobqJ6LiYnRuSDg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcp_JdANf2DPOX7Wp8Wrp5V6RPlcYeRb_QTAZU41-WH3jylb-lRGlddjd7h74T2EIvDas7XI9KGTqJly0aruI3E4UYHLL3gcAX600BjU9MF4l2B_4kRBTAjDckezLjuUQt1UL07?key=eHiEe45NobqJ6LiYnRuSDg" alt=""><figcaption></figcaption></figure>

Y: Weight amount

boost\_suppress\_factor: The impact factor is fixed at 100

booster\_unit: The impact factor is fixed at 10^18

base: The base of the Log curve is fixed at 2137469933345874131511402299392/10^18

shares: The share obtained after the user supplies assets



### The table below shows the amount of Weight and the corresponding farming multipliers:

<table><thead><tr><th width="370.349853515625">Weight Amount</th><th>Farming Multiplier</th><th data-hidden></th></tr></thead><tbody><tr><td>500</td><td>1.056</td><td></td></tr><tr><td>5,000</td><td>1.137</td><td></td></tr><tr><td>50,000</td><td>1.218</td><td></td></tr><tr><td>500,000</td><td>1.3</td><td></td></tr><tr><td>5000,000</td><td>1.381</td><td></td></tr><tr><td>50,000,000</td><td>1.462</td><td></td></tr></tbody></table>



Farming multiplier is enabled for Lending Incentive rewards which apply to specific lending positions.

Here is an example illustrating how rewards are computed:

Say the USDC pool gives <sup><sub><mark style="color:$info;">200<mark style="color:$info;"><sub></sup> wNEAR per day, and there are two users - Alice and Bob.

* Alice supplies <sup><sub><mark style="background-color:$info;">500<mark style="background-color:$info;"><sub></sup> USDC and has <sup><sub><mark style="color:$info;">500,000<mark style="color:$info;"><sub></sup> Weight.
* Bob supplies <sup><sub><mark style="color:$info;">50<mark style="color:$info;"><sub></sup> USDC and has <sup><sub><mark style="color:$info;">500<mark style="color:$info;"><sub></sup> Weight.

Boosted shares are computed via the following:

* Alice gets a farming multiplier of <sup><sub><mark style="color:$info;">1.3x<mark style="color:$info;"><sub></sup>, so the number of boosted shares becomes <sup><sub><mark style="color:$info;">650<mark style="color:$info;"><sub></sup> (i.e., 500 \* 1.3).
* Bob gets a farming multiplier of <sup><sub><mark style="color:$info;">1.056x<mark style="color:$info;"><sub></sup>, so the number of boosted shares becomes <sup><sub><mark style="color:$info;">52.8<mark style="color:$info;"><sub></sup> (i.e., 50 \* 1.041).
* The total is <sup><sub><mark style="color:$info;">702.8<mark style="color:$info;"><sub></sup> boosted shares.

So Alice gets <sup><sub><mark style="color:$info;">92.48%<mark style="color:$info;"><sub></sup> (650/702.8) of the rewards, and Bob gets <sup><sub><mark style="color:$info;">7.51%<mark style="color:$info;"><sub></sup> (52.8/702.8) of the rewards. By the end of the day, Alice gets <sup><sub><mark style="color:$info;">184.96<mark style="color:$info;"><sub></sup> wNEAR, and Bob gets <sup><sub><mark style="color:$info;">15.2<mark style="color:$info;"><sub></sup> wNEAR.

Let's say Charlie supplies 1000 USDC and has 0 Weight:

* This adds <sup><sub><mark style="color:$info;">1000<mark style="color:$info;"><sub></sup> boosted shares for Charlie. Now the total amount of boosted shares is <sup><sub><mark style="color:$info;">1’702.8<mark style="color:$info;"><sub></sup>.
* Alice gets <sup><sub><mark style="color:$info;">38.17%<mark style="color:$info;"><sub></sup> (650/1’702.8) of the farm rewards resulting in <sup><sub><mark style="color:$info;">76.34<mark style="color:$info;"><sub></sup> wNEAR per day.
* Bob gets <sup><sub><mark style="color:$info;">3.1%<mark style="color:$info;"><sub></sup> (52.8/1’702.8) of the farm rewards resulting in <sup><sub><mark style="color:$info;">6.2<mark style="color:$info;"><sub></sup> wNEAR per day.

Charlie gets <sup><sub><mark style="color:$info;">58.72%<mark style="color:$info;"><sub></sup> (1000/1’702.8) of the farm rewards resulting in <sup><sub><mark style="color:$info;">117.44<mark style="color:$info;"><sub></sup> wNEAR per day.





## xRHEA Boost Program&#x20;

### Overview

xRHEA Boost allows users to lock xRHEA tokens in exchange for boosted incentive rewards on Rhea Lending. The longer the lock-up period, the greater the boost — up to a maximum of 6 months.

Note: Boost only affects incentive rewards. It does not impact base lending interest rates.



### How It Works

Lock xRHEA → Earn Weight → Get Boosted Rewards

The program operates in two sections:

1. Weight Algorithm – Calculates your Weight based on the amount and duration of xRHEA locked.\
   \


Farming Multiplier – Converts your Weight into a reward boost factor.\


