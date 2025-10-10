# RHEA Finance White Paper

## What is RHEA Finance

**Rhea is the innovative evolution of NEAR’s original DeFi powerhouses — Ref Finance and Burrow Finance, the leading DEX and lending protocols on the NEAR Protocol.**

This strategic merger and rebrand aim to establish a unified foundation to support the next wave of DeFi projects on NEAR — bringing NEAR DeFi back to where it **deserves** to be.

Rhea now serves as the primary liquidity hub and chain-abstracted liquidity layer for these projects — enabling both protocol-level integrations and community incentive mechanisms, all built directly on NEAR’s tech stack, including Chain Abstraction and an AI-powered framework.

## Products and Services

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Rhea is not just a rebrand — it's a product to showcase NEAR Protocol’s core infrastructure and technical innovation.

By delivering sophisticated, composable products across DeFi verticals, Rhea brings more profound utility and long-term value to every layer of decentralized finance — driving continuous innovation.

### Main Products

Rhea's dual foundational pillars consist of its decentralized exchange (DEX) and decentralized lending protocols.

#### RHEA DEX

**RHEA DEX** provides a fundamental decentralized AMM (Automated Market Maker) trading market, with the following additional features:

* **Permissionless** pool creation: Users can freely create any swap pool, even if a pool with an identical token pair already exists.
* Fee setting on pool level: The pool creator sets the swap fee.
* Slippage protection: A minimum swap-out or maximum swap-in amount could be set by users to mitigate slippage risk per swap action.
* Swap by output amount: Users can designate a specific swap-out amount and let DEX charge the needed swap-in amount.
* Enable chain swap on multiple pools: Users can swap token A for B even if there are no direct AB swap pools.

#### RHEA Lending

**RHEA Lending** provides an over-collateralized lending market:

* Each asset has its own volatility factor due to a multi-dimensional risk assessment.
* Each asset has its own dynamic interest curve aiming for the best asset utilization rate.
* An open liquidation model to secure the protocol.
* A flexible incentive model to encourage both lending and borrowing.

### Advanced Services

Rhea has developed a bunch of advanced services based on the two basic products. And more advanced services are on their way, as Rhea keeps working on innovations in the DEFI area.

#### Stable Swap Pool

By combining the constant sum formula (x + y) = C with the constant product formula x\*y=C, the stable pool provides much lower slippage and fees when trading strongly correlated tokens, such as stable coins and tokens with their derivative tokens.

#### Degen Swap Pool

As an extension of the stable pool idea, the degen pool leverages a price oracle to provide a stable-pool-like trading experience for any token pairs. More than that, degen pools can have a similar performance with much less TVL compared to stable pools.

#### DCL Swap Pool

Rhea DCL (Discretized Concentrated Liquidity) pool is a significant improvement upon the concentrated liquidity pool model.

Besides 1) the much higher TVL usage rate, 2) limited and predictable impermanent loss, and 3) better swap price with much less slippage, which is brought by concentrating liquidity, the Rhea DCL pool effectively provides a pure decentralized order book trading subsystem. It actually fulfills the requirements of AMM maker, AMM taker, and order traders in one system.

#### Smart Routing

There are so many pools existing in the Rhea Dex, that even for a single swap request, you can find multiple pools or pool combinations to execute trading.

Smart routing aims to help the user find the best pool or pool combination to get maximum output, and it even splits the user request into multiple trading chains if necessary.

Behind the scenes, this service keeps tracking all pool status, including pool liquidity depth, fee configuration, so that it can simulate any swap in advance and find the best way with a specific algorithm to fulfill a particular swap request.

#### LP Token as Collateral

On Rhea Finance, a dex LP can also have his liquidity (in the form of LP tokens) to be used as collateral in lending, without interrupting the incentive from staking LP tokens in the farming platform.

It enables triple profits for an LP, 1) swap fees from the trading, 2) incentives from LP token farming, and 3) supply interest for the collateral. Furthermore, these liquidities are now free for LP to seize possible market profits by borrowing other assets.

#### Margin Trading

Rhea's margin trading is built on top of both the Rhea Lending and Rhea Dex products, aiming to provide users with spot leverage trading capability, that is, the ability to long or short the spot market.

It shares the same asset pool with Rhea Lending, and enables up to 3x leverage for trading on Rhea Dex.

#### Boost Farming

Rhea provides an independent and universal tokenized incentive platform called **Boost Farming.**

The platform issues incentive tokens to users based on the amount of their seed tokens staked and the duration of the stake. Any NEP-141 standard tokens can be taken as seeds and incentives. Furthermore, it even supports using LP tokens as seeds to incentivize TVL providers of any DEFI systems.

It supports multiple incentive tokens for the same seed token, which is also known as multi-farming.

It also supports multiple boost tokens to help users obtain additional incentive tokens based on the number of boost tokens and the lock-up time.

### Cross-Services

The following services are built in collaboration with Rhea partners. They increase Rhea users’ experience and extend Rhea's business scope. Rhea continues to seek cooperation with ecosystem partners to launch more exciting cross-services。

#### Aggregate Bridge

Aggregator Bridge is a bridge aggregation layer that connects NEAR with multi-chain ecosystems. It integrates the mainstream Bridge protocols on the market, allowing users to achieve faster, cheaper, and safer cross-chain operations through one entry, without having to compare the paths, fees, or supporting networks of each Bridge one by one.

Aggregate Bridge has but is not limited to the following features: Automatic path selection: Intelligently select the cross-chain path with the lowest gas, lowest handling fee, and fastest arrival time;

Intelligent aggregation: The backend supports task scheduling and an extensible plug-in mechanism to facilitate rapid access to new Bridge providers;

Multi-chain compatibility: Supports heterogeneous network bridging such as EVM, Bitcoin, NEAR, Solana, etc.;

Safe and reliable: Only relying on the native security model of each Bridge, no additional trusts are introduced. Not even any user assets custody in OneClick mode;

#### Apollo Pool

Apollo Pool is a one-click single-coin staking, high-yield aggregation strategy service. It allows users to invest in only a single asset (such as Stablecoin, NEAR, BTC, ETH) to achieve the goal of high annualized yield, while having the characteristics of simple operation and intelligent custody. Specifically: • No pairing required, zero impermanent loss: users only need to invest in a single token, AMM automatically adjusts, and funds are always allocated in a balanced value. • High capital utilization: Based on the improved version of DegenPool and the "barrel short board theory", the number of tokens is guaranteed to remain unchanged even if the price fluctuates. • Strategy enhancement: integrating Burrow and DeltaTrade, amplifies asset investment through lending and automatically adjusts positions to resist liquidation risks. • Automated and scalable: All strategies are automatically executed by the system, and can be expanded to more chains and more assets in the future.

#### Vault by Shade Agent

**Harness the power of AI to dynamically analyze user behavior based on on-chain DeFi activity — unlocking personalized vault recommendations tailored to individual risk profiles.**

Through seamless integration with chain abstraction, users gain the freedom to choose and execute preferred strategies across multiple supported networks. To ensure a frictionless experience, real-time Telegram notifications keep users informed of their latest vault positions, yield performance, and optimization opportunities — all in one intelligent, adaptive ecosystem.

#### Satoshi Defi

Satoshi Defi brings Bitcoin users to the much broader NEAR Defi ecosystem. Using only their familiar native BTC wallets, those Bitcoin users can participate in NEAR Defi activities such as doing swaps, being liquidity providers to earn profits, and borrowing out multiple assets for more market opportunities.

Behind the scenes, it leverages the NEAR chain abstraction technology, empowering BTC users with the ability to securely bridge BTC assets and manipulate NEAR accounts. It opens a door for BTC users to a more exciting crypto world composed of various chains.

## RHEA DAO

RHEA leverages its DAO to implement a decentralized management model. RHEA DAO involvement in Rhea’s operation will be revealed after TGE。

## RHEA Tokens

The protocol operates with three distinct tokens. They are all initially distributed on the NEAR Network, with the ability to cross to other chains using the omni-bridge.

### Rhea Token

RHEA is the primary token. The token detail is as follows:

Name: Rhea

Symbol: RHEA

Decimal: 18

Total supply: 1 billion.

RHEA is the merger of $REF and $BRRR tokens and will act a the unified boost token in the RHEA platform.

### xRhea Token

Users can stake Rhea to get xRHEA and use the token within the RHEA ecosystem. The staked RHEA will continuously accrue value while being staked

Token Specifications:

* Name: xRhea
* Symbol: xRHEA
* Decimals: 18
* Total Supply: Elastic

**xRHEA’s Utility:**

* xRHEA will serve as the primary gas fee token within the RHEA ecosystem.
* xRHEA can be used as a lending asset, allowing users to stake RHEA to earn yield while simultaneously using it as collateral.
* Holding, supplying, and spending xRHEA will contribute to on-chain reputation, which impacts the conversion of oRHEA to RHEA.

### oRhea

oRHEA is the reward for users who provide liquidity into the protocol. It aims to replace traditional APY for liquidity rewards. These oRHEA tokens can be converted to RHEA at varying conversion rates based on the user’s reputation.

Token Specifications:

* Name: oRhea
* Symbol: oRHEA
* Decimals: 18
* Total Supply: Elastic

### Token Conversion

For holders of $REF and $BRRR tokens, there will be a website to convert their tokens to $RHEA. Stay tuned for the conversion website.
