---
description: Cross-chain Account Whitepaper
---

# RHEA Finance Cross-Chain Lending Litepaper

This is a NEAR blockchain-based Cross-Chain account protocol solution designed to provide NEAR ecosystem applications with the capability to extend to crosschain business operations. It doesn't rely on any side-chain or light client entities, but leveraging the abiltity of on-chain signture verification on NEAR network.

The core of the protocol is to dynamically deploy an McA contract on the NEAR chain for each user, linking the user's wallet addresses or public keys across various chains. Around this core, the protocol also provides a series of components and services that enable:

On one hand, users can manipulate their dedicated McA contracts to interact with NEAR ecosystem dapps by signing business messages with their existing wallet private keys, without actually holding a NEAR network account.

On the other hand, users can bridge assets between their McA contracts and wallets through any asset bridge, and even execute related business operations in a one-click manner through message asset bridges (such as Near Intents) while performing cross-chain asset transfers.

As an example usecase, we make Rhea Burrow to a crosschain lending protocol on top of our crosschain account system.

### Related Technologies <a href="#related-technologies" id="related-technologies"></a>

#### Onchain Verification <a href="#onchain-verification" id="onchain-verification"></a>

The NEAR chain supports signature verification operations in smart contracts, supporting ECDSA, EdDSA, etc. McA contracts can verify whether messages are signed by corresponding private keys using bound public keys (EVM wallet types only need addresses).

#### Global Contract <a href="#global-contract" id="global-contract"></a>

The NEAR chain's Global Contract feature supports deploying only one copy of code on-chain that can be referenced by any number of accounts. This feature greatly reduces the cost of using McA. Users only need to bear the minimum cost of maintaining McA accounts without paying for contract code storage fees. Check [here](https://docs.near.org/smart-contracts/global-contracts) to check more details about NEAR Global Contracts.

#### Message Asset Bridge <a href="#message-asset-bridge" id="message-asset-bridge"></a>

Message asset bridges enable message passing along with the asset bridging. This behavior enables users to have their business handled accross chains in one click, which significantly improves user experience.

### Component Architecture <a href="#component-architecture" id="component-architecture"></a>

* Account Management (AM) contract
* Crosschain Account (McA) contract
* CrossChain Account Frontend
* User native wallet
* Signed Business Relayer (SBR)
* Near Intents
* DAO

#### AM <a href="#am" id="am"></a>

The Account Manager is the registry and factory for Crosschain Accounts. It maintains wallet-to-McA mappings and manages configuration.\
It's also the deploy point under which the upgradable McA global contract is published globally.

In onboarding period, new users access AM via Near Intents, to actually create their McA contracts. And if any bridged token leftover, AM will pass it to the newly created McA with possible business message along with the bridging.

#### McA <a href="#mca" id="mca"></a>

Each Crosschain Account is an individual smart contract refered from the same NEAR Global Contract deployed on AM account. It can be upgraded by the management DAO, and applied immediately to all McA.

It records user wallets information (on-chain storage), so has the ability to verify user signature on those actions. Therefore, MCA can securely execute business actions signed by the user's linked wallets.

As an implicit Abstract Account, it also manages nonce for replay attack and execution deadline against withhold attack, like a regular wallet does.

It has 2 entry points. One is `ft_on_transfer`, used by Near Intents and AM to process additional business messages accompanying token transfers. The other is `exec`, used by protocol relayers to process user-signed business actions.

Another intersting feature on McA is that, it supports aliases of those reliable and non-side-effect businesses. It acts as a shortcut of those businesses that only consumes incoming tokens in the same TX and user signatures are not required in this case.

#### Frontend <a href="#frontend" id="frontend"></a>

Besides the basic duties as a wallet, such as showing user's assets in McA, fetching user data from any NEAR dApps, Frontend is mainly responsible for building business actions, having users sign on business message through wallets, passing the signed message to AM or McA via relayers or some message asset bridge. It also responsible for waiting and parsing business execution results for users.

Frontend is actually a public role. Anyone can build their own frontend to access the Crosschain Account system.

#### User Native Wallet <a href="#user-native-wallet" id="user-native-wallet"></a>

Such as metamask, phantom and etc, those wallets are used for signing business messages at users' will.

#### Signed Business Relayer <a href="#signed-business-relayer" id="signed-business-relayer"></a>

Relayer submits user-signed business messages to their corresponding McAs on-chain. It's an public role, and anyone can build their own relayers, especially to cooperate with their own frontend.

As McA has implemented Near Intents OnAuth interface, the Auth pure message delivery service can also be taken as a public SBR for Crosschain Account system.

#### Near Intents <a href="#near-intents" id="near-intents"></a>

It's an instance of message asset bridge. Near Intents supports carrying business messages alongside token bridges. These business messages include:

* Regular business instructions with user signatures
* Reliable business aliases

Users can bridge only tokens to their McA accounts through intents (without any messages), but this is not required. Any asset bridge can help users complete this operation. There are no restrictions on which bridge users use.

#### DAO <a href="#dao" id="dao"></a>

DAO is used as an instance of management entity.

Besides regular management work, it also responsible for McA global contract code management. Once contract code is upgraded via the DAO, all McA accounts will immediately run on the new code.

### Core Workflow <a href="#core-workflow" id="core-workflow"></a>

#### Onboarding New Users <a href="#onboarding-new-users" id="onboarding-new-users"></a>

New users need to interact with AM contract to implicitly intialize their McA contract. And then, they only need to interact with their own McA to enjoy Multichain Account service.

The initialization workflow may seem like this:

* In the protocol frontend, users log in with their own wallets
* Protocol frontend queries AM contract, learns that wallet address or public key is not bound to any McA, identifying them as new users
* Users use Near Intents to cross-chain deposit any supported tokens into AM contract
  * For Near Intents, the bridging process may involve transfering tokens to a runtime generated deposit address on the source chain. The address implies in some way the user's public key or EVM address and specific business information. So that at the end of bridging, Near Intents can transfer bridged tokens to AM with correctly attached business message.
  * For other message asset bridges, there are maybe other ways but they all end up with transfering bridged tokens to AM with correct message;
* AM contract receives cross-chain tokens while obtaining associated user public keys/addresses and optional business information
* AM contract checks that public keys are indeed not bound to any McA, then creates and deploys McA contract accounts, binding user public keys/addresses
* AM contract transfers remaining cross-chain tokens (after deducting creation fees) to the newly created McA contract and if optional business message exists, it will be passed to the McA along with the token transfer.

#### Asset Cross-chain Bridging with optional business messages <a href="#asset-cross-chain-bridging-with-optional-business-messages" id="asset-cross-chain-bridging-with-optional-business-messages"></a>

Users can cross-chain transfer to their McAs through any asset bridge. If they also want to execute business while transferring, users can use a message asset bridge to carry business messages and corresponding signatures while performing cross-chain transfers. McAs will verify user business message signatures upon receiving assets and execute accordingly.

Check next section for details about business message.

#### Business Access <a href="#business-access" id="business-access"></a>

Users directly sign business messages with wallets, and protocol backend relayers submit these messages and signatures to corresponding McAs, which execute business after signature verification.

The workflow may seem like this:

* On the Frontend, users log in with their own wallets
* Frontend queries AM contract to find corresponding McA contract ID
* Frontend queries McA contract to obtain necessary elements for building business messages, such as nonces to prevent replay attacks
* Frontend builds business messages
* Users confirm business messages and sign with their wallets
* Business messages and signatures are passed to McA contracts via SBR
* McA contracts execute business after signature verification
* Frontend monitors McA contracts, waiting for business execution results

The supported business actions are:

**`FunctionCall(FunctionCallAction)`**

Execute arbitrary smart contract functions.

**`Transfer(TransferAction)`**

Send NEAR tokens to another account.

**`AddWallet(Wallet)`**

Add a new user wallet to this McA. Check Wallet Management section for details.

**`RemoveWallet(Wallet)`**

Remove a user wallet from this McA. Check Wallet Management section for details.

**`GasPayment(GasPaymentAction)`**

Pay transaction gas fees in alternative tokens (USDC, USDT, DAI, etc.) to the signer of the TX, that is the relayer. Check Multi Gas Token Support section for details.

#### Wallet Management <a href="#wallet-management" id="wallet-management"></a>

Users can use bonded wallets to bind or unbind other wallets.

More specific, they can:

* When initializing McA, attatch multiple wallets.
* Indicate McA with AddWallet action to bond new wallet.
* Indicate McA with RemoveWallet action to unbond existing wallet.

The following rules will be applied on the bonded wallets:

* One wallet can only be bond to one McA.
* One McA can bond multiple wallets.
* A wallet can NOT unbond itself, this is to prevent locked McA due to misoperation by the user.
* The last wallet in McA can NOT be unbond, this is to prevent locked McA due to misoperation by the user.

The corresponding workflow may seem like this:

* On the frontend, users log in with their own wallets
* The frontend queries AM contract to find corresponding McA contract ID
* The frontend queries McA contract to obtain necessary elements for building business action message, such as nonces to prevent replay attacks
* The frontend builds wallet management action message
* Users confirm the message by signing with wallets
* Signed business messages are passed McA via SBR
* McA executes business after signature verification
* McA reports wallet binding changes to AM
* The frontend listens to the business execution results

### Features for optimized experience <a href="#features-for-optimized-experience" id="features-for-optimized-experience"></a>

#### Batch actions in one message <a href="#batch-actions-in-one-message" id="batch-actions-in-one-message"></a>

McA supports business action list in one signed business message. They will be executed suqentially.

More than that, considering some dApps' contract interfaces will return before all related promises complete, McA supports a special optional field in FunctionCall action:\
`interval_block: Option<u8>` - Optional block interval to wait before executing (0-255 blocks)\
The FunctionCall action with this field will not shoots unless `interval_block` blocks passed after the predecessor action completes.

#### Multi Gas Token Support <a href="#multi-gas-token-support" id="multi-gas-token-support"></a>

SBR bears the NEAR gas costs for user-signed business messages to go on-chain. Multichain Account allows users to pay this gas in other tokens, which means our users don't need to collect NEAR for gas concern.

Using GasPayment action, users can choose one of the protocol-approved gas tokens to pay directly to the relayer in the same TX of delivering their signed business message:

* Protocol specifies the set of tokens available for gas settlement;
* Frontend inserts GasPayment action when building business message;
* Users can choose which gas token to pay and its amount, signing confirmation along with business;
* SBR can do checking before delivering the business message to McA, such as checking the GasPayment action is correctly included and user McA has payment capability;
* When McAs execute business, the GasPayment action will be dynamically expanded to a fee token transferring to the current TX signer, that is the relayer who paid the real NEAR gas;
* As business actions are executed sequentially, if fee payment transaction fails, subsequent business in this request won't get executed.

#### Business Shortcut <a href="#business-shortcut" id="business-shortcut"></a>

Considering the business message along with the token bridging scenario, some businesses are "reliable", which means they will not harm users' existing assets, on-chain state, or account reputation even without a user signature. For example, depositing to some dex as supply or staking to some farming dapps to earn profit.

And without a user signature, user can initiate token bridge even via some CEX withdrawals or 3rd party transfers.

Multichain Account supports carrying reliable business aliases for this case along cross-chain asset transfer. These alias are strictly defined by the protocol and will be expanded into specific predefined actions on-chain.

The business message with reliable buisness alias may look like this:

```
{
  "w": [{"EVM": "..."}],
  "b": {"r": "BurrowSupply"}
}
```

* Pre-approved safe operation
* Pre-defined targets (Burrow protocol in this example alias)
* No user signature required

#### Register for tokens and dApps <a href="#register-for-tokens-and-dapps" id="register-for-tokens-and-dapps"></a>

Most dApps and Tokens on Near network require a register with `storage_deposit` call, which will transfer a certain amount of NEAR to the target token or dApp to be locked for storage occupation. Check [here](https://github.com/near/NEPs/blob/master/neps/nep-0145.md) for details.

The bridge will help the token register for the recipient, McA or AM if necessary. Similarly, AM will help to do the token registration work before sending token to McA.

But for the dApps and possible outcome tokens, regularly, they request an explicit storage\_deposit function call in the business actions.

Considering the newly onboarding users, who has no spare NEAR to do such things, the AM contract allows a optional `r` field beside the business field `b` and the wallets field `w` in the attched message along the token bridging:

* `msg: String` - JSON `IntentsMessage` with:
  * `w` (wallets): Wallets list
  * `r` (register\_dapps): Optional dApp storage registrations\
    eg: "r": {"burrow.near": "0.025N"},
  * `b` (business): Optional business with/without signature

As in the example message above, AM will charge a certain amount of bridged token, in equivalent value of 0.025 Near, and register McA to `burrow.near` with 0.025 Near as deposit from AM's own balance.

As for existing McA, if need more NEAR to do storage register, user can wrap a Rhea Dex instant swap (a regular functionCall action) in the business actions, to get NEAR by selling other tokens.

### Multichain Lending using Multichain Account <a href="#multichain-lending-using-multichain-account" id="multichain-lending-using-multichain-account"></a>

Leveraging the Multichain Account protocol, Burrow, the Rhea lending protocol can provide multichain lending service.

#### To Supply <a href="#to-supply" id="to-supply"></a>

New external chain users can combine Supply with onboarding process. They can sign a business message which indicate the newly created McA to deposit bridged token to Burrow as supply, so they can enjoy possible supply reward.

Once the McA has been successfully created, the supply action will be performed by McA, the bridged token will be deposit to Burrow as supply.

A 'r' field will always exist in this case to help new user register on Burrow dApp before supply.

For existing McA users, the workflow is pretty much the same, except users may need to swap some NEAR first for Burrow dApp registration if necessary. But it can be done in one shot with multiple actions in one business message.

Need to note here, there is a reliable business alias `BurrowSupply` for burrow supply. Without signature, user can even supply token to Burrow via CEX withdrawal.

#### To Supply as Collateral <a href="#to-supply-as-collateral" id="to-supply-as-collateral"></a>

Similar to supply, supply as collateral will use all supplied token as user's collateral, so user can borrow tokens out from the burrow market.

There is also a reliable business alias `BurrowCollateral` for this case.

#### To borrow <a href="#to-borrow" id="to-borrow"></a>

McA users can borrow from the market if his McA has enough collateral in Burrow. And send borrow out token to his native wallet via some toke bridge. These 2 actions can be combined in one business message, so user only need to sign once with his native wallet.

#### To Repay <a href="#to-repay" id="to-repay"></a>

User can use assets on external chain to repay their debt on Burrow. They can take 2 steps: bridge token to their McA first and then repay by sign business message.

Or, they can just combine them in 1 step, via Near Intents, the message asset bridge, to bring a business message along with the repay token bridging.

There is also a reliable business alias `BurrowRepay` for this case.

#### To Withdraw <a href="#to-withdraw" id="to-withdraw"></a>

McA users can withdraw their supply or collateral token back to their native wallet. It's also a combination of a burrow action and a bridge action. Only one signature needed in this case.

#### Summary <a href="#summary" id="summary"></a>

The core concept of multichain lending service, is to let external users can access Burrow, a near dApp, with their native tokens. Which makes Burrow seems like a native dApp on their chains.

Behind the scenes, it is multichain account protocol, along with the message asset bridge, to make it happen.
