---
description: Answers to Frequently Asked Questions
---

# FAQ

## _**I am having a problem using the RHEA Finance website, what should I do?**_

Please go to the [Help page ](help.md)to see if your issue is addressed there. If it is not, post a message to the user-support channel on our [Discord server](https://discord.com/invite/jXByEbCmtW), or [Telegram group](https://t.me/ref_finance).&#x20;

⛔️ **Admins and mods will NEVER dm you first**. If you get a DM from someone claiming to be an admin, mod, or a generic "technical support" account, it is a scam ⛔️

## _**How can I get the REF token?**_

You can get REF by swapping for it at [http://app.ref.finance/](http://app.ref.finance/)&#x20;

Here are some centralized exchanges where you can buy REF o&#x6E;**:**&#x20;

* Gate.io: [https://www.gate.io/trade/ref\_usdt](https://www.gate.io/trade/ref_usdt)&#x20;
* MEXC: [https://www.mexc.com/exchange/REF\_USDT](https://www.mexc.com/exchange/REF_USDT)
* Jubi: [https://www.jbex.com/exchange/REF/USDT](https://www.jbex.com/exchange/REF/USDT)&#x20;
* CoinEx: [https://www.coinex.com/exchange/ref-usdt](https://www.coinex.com/exchange/ref-usdt)&#x20;

:warning: _This list is for the information and convenience of the public, and does not constitute endorsement, recommendation, or favoring of the companies or their services. Individuals should do their own research before using any of their services._

## _**Where can I find market cap, price charts, or other stats for the REF token?**_

Latest Marketcap: [https://stats.ref.finance/marketcap](https://stats.ref.finance/marketcap)

Ref Analytics: [https://stats.ref.finance/](https://stats.ref.finance/) \
CoinMarketCap: [https://coinmarketcap.com/currencies/ref-finance](https://coinmarketcap.com/currencies/ref-finance) \
CoinGecko: [https://www.coingecko.com/en/coins/ref-finance](https://www.coingecko.com/en/coins/ref-finance) \
nomics: [https://nomics.com/exchanges/ref-ref-finance](https://nomics.com/exchanges/ref-ref-finance)&#x20;

:warning: _This list is for the information and convenience of the public, and does not constitute endorsement, recommendation, statement of accuracy, or favoring of them or their services. Individuals should do their own research before using any of their services or relying on the information they provide._

## _**Are there any risks with any of the services offered by Ref Finance, or DeFi/Crypto in general?**_

**YES!** You can read about some of them here: [https://app.ref.finance/risks](https://app.ref.finance/risks)

:warning:_There is **zero guarantee** that you will make any money, and there is a very real **risk of losing 100% of the funds you invest**. Always **DYOR** before investing funds, and **never invest funds that you can't afford to lose.**_

## _**What is wNEAR?**_

wNEAR is "wrapped" NEAR, a fungible token implementation of NEAR based on the NEP-141 standard. It has the functionality required for certain DeFi operations, like swapping, adding to Liquidity Pools, and bridging to/from other blockchains. The wNEAR smart contract, _wrap.near_, is a core contract developed and managed by the Near team.&#x20;

For more information about wNEAR, read this blog post by the Near Wallet Team [https://medium.com/mynearwallet-blog/what-is-wnear-a-full-guide-to-wrapping-near-d020fa655cf2](https://medium.com/mynearwallet-blog/what-is-wnear-a-full-guide-to-wrapping-near-d020fa655cf2)

## _**How do I wrap NEAR / unwrap wNEAR?**_

You can use the swap form on the [Ref site](https://app.ref.finance/) to do this. Just select the tokens as if you were swapping one for the other. Since no actual liquidity pools are used for when wrapping/unwrapping using this method, Ref will not charge any fee. You only pay the normal Near Protocol gas/transaction fee. If you are wrapping NEAR to wNEAR, you may be asked to "pay" 0.1N for the Storage Deposit required by the protocol (see FAQ for more info on storage deposits).&#x20;

:warning: **You cannot send wNEAR to a cex** like Binance or Huobi. If you try to, **it will be permanently lost!**

## _**What is the 0.25N Network Fee Allowance that I am asked to approve when I connect my wallet to the Ref site?**_

The important part: 0.25N **will not** be deducted from your account, or locked in any way.

You need to approve a 0.25N Network Fee whenever you connect your wallet to **any** dapp, not just Ref's.&#x20;

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The Fee Allowance allows the dapp to use up to a total of 0.25N for gas fees on certain types of transactions without you having to approve it. The Network Fee **can only be used to pay for gas**. Once a dapp has spent all of the 0.25N, you will need to approve another 0.25N. Ref cannot do anything else with any tokens in your wallet without your approval.

_**Use case:**_\
On Ref Finance you don't need to approve claiming farm rewards, because the site asks the protocol to use some of the Network Fee Allowance to pay the gas fee for the transaction(s). The reason we do this is so that when you are staking on multiple farms, you don't have to wait for claiming on one farm to finish, before being able to claim rewards on another.

_You can "Deauthorize", or revoke approval for a dapp, by going to the account page on your near wallet, scrolling down to "Authorized Apps" and clicking "View All". Deauthorizing a dapp will sign you out of it, and you will need to connect your wallet again to use it_

## Why do some transactions on Ref Finance cost 0.1N, 0.2N, 0.3N, etc?

When your account makes a transaction with a smart contract on Near for the first time, the Near Protocol requires that you pay a storage deposit for the space on the blockchain that will be used to record all transactions between your account and the contract. This includes smart contracts for tokens. So, actions like wrapping NEAR to wNEAR for the first time, swapping for a token that has never been in your wallet before, or receiving a new token from farm rewards, will all require a storage deposit before they can be done.

When the site detects that your account does not have a storage deposit for one or more tokens that it will receive, it will have you approve a transaction with an estimated cost of 0.1N per unregistered token. For example, If you are withdrawing farm rewards for multiple tokens, and 3 of them have never been in your wallet before, you will be asked to approve a transaction for 0.3N. However, most of that will be refunded to your wallet (like 0.08N or more per token). The site overestimates the amount that will be needed to be sure that the series of transactions that are needed for a swap or withdraw do not fail half-way through.

_You can compare the available balance of NEAR in your wallet before and after the transaction to see how much was actually used for the storage deposit._

## What is xREF?

The xREF page is where you can stake your $REF tokens. When you stake $REF, you get xREF back. The amount of xREF you get depends on the current value of xREF relative to $REF.

Every quarter Ref Finance takes the revenue we get from swap fees and other sources, and uses it to buy-back $REF by swapping those tokens for $REF. We then slowly release that $REF into the xREF pool; a little bit is added every second for a period of about 3 months. This causes the value of xREF, relative to $REF, to increase continuously over time. In other words, for each second that passes, you will get a little more $REF back when unstaking xREF.

<figure><img src="../.gitbook/assets/xREF_staking.gif" alt=""><figcaption><p>You will <strong>always</strong> get back more REF than you staked, even if you unstake immediately after staking!</p></figcaption></figure>

## _**When will rewards for the TOKEN1/TOKEN2 farm end?**_

The Ref community DAO votes twice a month on whether to renew **REF rewards** on farms, and at what rate. Renewals of non-REF tokens are handled by that token's project. You can see proposals for renewing REF rewards on the [ref gov forum](https://gov.ref.finance/).

## _**What happens if I don't unstake my shares or claim rewards before a farm ends?**_

You will **not** lose your shares or any rewards if you don't unstake/claim them before a farm ends. There is **no** time limit or deadline for unstaking shares or claiming rewards after a farm ends.

## _**How do I get my token whitelisted?**_

Please [fill out this form](https://form.typeform.com/to/kxb7tTXg), and someone from the team will contact you.

## _**Who should I contact for marketing / collab / business proposals?**_

Please [fill out this form](https://form.typeform.com/to/onOPhJ6Y), and someone from the team will contact you if we are interested.

## Are you hiring?

Please email your resume to **hiring@ref.finance** and someone from the team will get back to you if there is an open position that you are a good fit for.
