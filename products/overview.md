# Overview

## How Ref Finance Works

Ref Finance is an open-source software.&#x20;

Inspired by Uniswap v2 and Curve Finance, Ref Finance is an automated liquidity protocol powered by two constant product functions:

* Swap function: x \* y = k
* StableSwap function: χDn−1 \* ∑ xi + ∏ xi = χDn + ( D / n )n&#x20;
* StableSwap function for yield-bearing tokens (Rated pools)

For more information, please refer to:

* Swap function
  * Uniswap v2 Whitepaper: [https://uniswap.org/whitepaper.pdf](https://uniswap.org/whitepaper.pdf)
* StableSwap function
  * Curve StableSwap Whitepaper: [https://curve.fi/files/stableswap-paper.pdf](https://curve.fi/files/stableswap-paper.pdf)
* StableSwap function for yield-bearing tokens (Rated pools)

{% file src="../.gitbook/assets/Rated_pools_pools_designed_for_yield-bearing_tokens.pdf" %}
Rated pools document
{% endfile %}

Ref Finance is implemented on the NEAR blockchain. The platform is fully permissionless and removes the need for trusted intermediaries, prioritising decentralisation and censorship resistance. Anyone can trade and/or become a liquidity provider (LP) for a pool by depositing an equivalent value of each underlying token in return for pool tokens (LP tokens). These tokens track pro-rata LP shares of the total reserves, and can be redeemed for the underlying assets at any time.

Unlike Uniswap, Ref Finance smart contract (v2.ref-finance.near), which manages the automated market maker functions; swap and provide liquidity, contains all pairs or liquidity pools, made of reserves of two or three [NEP-141](https://nomicon.io/Standards/FungibleToken/Core) tokens ([ERC-20](https://eips.ethereum.org/EIPS/eip-20) equivalent on NEAR).

When a LP creates a new pool, the pool fee is customisable. Every pool has the same fee structure, as shown below.

![](<../.gitbook/assets/Mind Map(5).jpg>)

## Ecosystem Participants

![](<../.gitbook/assets/Ref Ecosystem Participants(2).jpg>)

The Ref Finance ecosystem is primarily comprised of five types of users: traders, liquidity providers, stakers, voters and developers.&#x20;

* Traders can swap [NEP-141](https://nomicon.io/Standards/FungibleToken/Core) tokens
* Liquidity providers are incentivised to provide these tokens to liquidity pools
* Stakers are receiving pro-rata shares of the shared protocol revenue
* Voters can participate in the governance of the project and the allocation of liquidity incentives
* Developers can integrate directly with Ref Finance smart contracts to empower users in their interactions with tokens, trading interfaces, trading strategies, and more

### Traders

There are different types of traders interacting with the protocol:

* Speculators can use a wide range of strategies from fundamental to technical analysis, to 'ape' approach (process of buying a token shortly after the token project launch without conducting thorough research)
* Hig-frequency bots can cover different strategies, such as market-neutral arbitrage or long/short strategies
* Dapp users buy tokens for use in other applications on NEAR, for example, buying PixelDapp tokens to play games
* Smart contracts that execute trades by implementing swap functionality, from products like DEX aggregators to custom scripts
* Legal entities (can be for-profit or not-for-profit organisations) and/or DAOs (can be a smart contract) that execute trades to manage their affairs, such as the settlement of an invoice in a differrent currency/token&#x20;

{% hint style="info" %}
Traders are all subject to the same fee for trading on the platform
{% endhint %}

### Liquidity Providers

Liquidity providers, or LPs, are a fragmented group, mainly made of:

* Passive LPs are token holders who passively invest to accumulate trading fees, they generally do not actively monitore their positions and divergence loss
* Sophisticated LPs are focused on market making as their primary strategy, they usually develop custom tools and monitore actively their positions and divergence loss
* Token projects sometimes choose to become LPs to 'initiate' liquidity, by creating a liquid pool for their token
* Protocol-oriented or 'politicised' LPs are focused primarily on the REF<>NEAR pool and the vetoken [model](voting.md),  allowing them to participate in the governance of the protocol (also see Voters)

### Stakers

Stakers can have different objectives and belong to specific subgroups:

* Long-term stakers are usually interested in a more predictable source of revenue, deriving from the protocol revenue, while holding the protocol token and participating in the governance (Under Development)
* Short-term or intra-strategy stakers are staking for a limited period of time, with the objective to optimise their returns, generally until the underlying token (REF) needs to be sold or used for a different purpose (i.e., liquidity provision)
* Voting-only stakers can be identified as users that stake only to vote the associated proposal(s), they are generally interested in participating/influencing the future of the protocol by voting on specific proposals

### Voters

VeToken holders can participate in the governance of the projects by voting on key governance proposals and by voting on the allocation of REF tokens to specific farms for additional farming rewards.

Voters can be:

* Community members, organisations, or investors that are interested in participating in the development and strategic orientation of the project
* Project owners who want to support/grow their community by voting on the allocation of additional rewards for their corresponding farm
* Short-term farmers who want to maximise their farming APR by voting on the allocation of additional rewards for their corresponding farm

### Developers

There are many ways Ref Finance can be used by developers, some examples include:

* UX/UI experiments and front-ends built to give users access to the backend functionalities
* Data and analytics (e.g. [https://stats.ref.finance/](https://stats.ref.finance/))
* Liquidity aggregation
* Yield aggregation
* DeFi dashboard projects (e.g. [https://app.odyssey.fi/](https://app.odyssey.fi/), [https://app.depocket.com/dashboard](https://app.depocket.com/dashboard))
* Trading bots

### Ref Finance Team and Community

Finally, the Ref Finance team along with the DAO (ref-finance.sputnik-dao.near) and the broader community drives development of the protocol and its ecosystem.
