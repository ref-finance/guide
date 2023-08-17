# Staking

## Concept

xREF is the main staking contract (xtoken.ref-finance.near) on the platform. When you stake your REF, you effectively exchange your REF for xREF. Over time, you will always earn more REF by holding xREF tokens.&#x20;

{% hint style="info" %}
There is no Divergence Loss when you stake REF for xREF tokens
{% endhint %}

Every swap executed on Ref Finance generates revenue for the protocol.&#x20;

* 100% of the protocol fee will be used to buy back REF tokens, of which:
  * 75% will be transferred to the xREF contract (xtoken.ref-finance.near) and released linearly over time&#x20;
  * 25% will be allocated to a Community/Provision treasury. This treasury will be used to fund grants and other community initiatives/programs

![](<../../.gitbook/assets/Mind Map(7).jpg>)

## Execution <a href="#6306" id="6306"></a>

Like any liquidity provider, Ref Finance collects its shares (16% of the total pool fee) in real-time and will be paid when it removes liquidity from the pool.&#x20;

Converting protocol LP tokens, resulting from the trading fees, involves the following actions:

1. Remove liquidity from pools
2. Withdraw corresponding tokens from Ref Finance (v2.ref-finance.near) to the DAO (ref-finance.sputnik-dao.near)
3. Send tokens from the DAO to a specific execution account&#x20;
4. Buy (back) REF tokens (with the execution account)
5. Send REF tokens to the staking contract (xtoken.ref-finance.near)

The process happens on a quarterly basis.

{% hint style="info" %}
The first buy back involved as many as 35 DAO proposals&#x20;
{% endhint %}

Because the conversion from LP to REF tokens happens on a quarterly basis, and because the tokens collected might be very volatile on the same period, there might be a significant difference between the daily 'observable' revenue and the 'realised' revenue, after conversion.

Finally, rewards are being released linearly on a quarterly basis, and will have boosted markups for the first three years (subject to change):

* Year 1: 2x
* Year 2: 1.5x
* Year 3: 1.2x
* Year 4: 1x
