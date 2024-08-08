# Aggregator Bridge

**Aggregator Bridge** is an important infrastructure to connect Near ecosystem and external ecosystems. It will aggregate all existing bridges within the Near ecosystem, including **Stargate**, **Rainbow**, **TokenBridge**, and **AllBridge**.

## Stargate Bridge

Bridging with Stargate is actually a collaboration between **Stargate** and **Rainbow** Bridge. Stargate handles the cross-chain transfer between EVM and Aurora, while Rainbow Bridge manages the transfer between Aurora and Near.

#### Why can users complete the bridge from EVM to Near with just one click?&#x20;

Ref has deployed a smart contract on the Aurora chain to receive and relay assets.

#### EVM -> Near

When a user transfers assets from EVM to Near, the process begins with Stargate transferring the assets from EVM to the Aurora smart contract, carrying the actual cross-chain information (the destination address on the Near chain).&#x20;

Once the Aurora smart contract receives the cross-chain message, it reads this information and invokes the Rainbow Bridge, immediately transferring the assets from Aurora to Near.

#### Near -> EVM

When a user transfers assets from Near to EVM, the process starts with Rainbow Bridge transferring the assets from the Near chain to the Aurora smart contract, carrying the actual cross-chain message (the destination address on the EVM chain).&#x20;

Once the Aurora smart contract receives the cross-chain message, it reads this information and invokes Stargate, immediately transferring the assets from Aurora to EVM.

#### Supported EVM chains

Ethereum, Arbitrum, Optimism, Base, Scroll&#x20;

#### Fees

Users need to pay Stargate fees, which consists of two parts:&#x20;

1. **Layer0 Cross-chain Fees**
2. **Stargate Protocol Fees**

The former is charged in ETH, while the latter is a percentage of the bridged assets. For detailed information, refer to Stargate's documentation: [Stargate Protocol Fees](https://stargateprotocol.gitbook.io/stargate/v/user-docs/tokenomics/protocol-fees%EF%BC%89).

#### How Near chain users provide Layer0 cross-chain fees (ETH) ?

When transferring assets from Near to EVM, users do not need to provide ETH for the fee. Instead, they only need to provide the bridged assets, as the ETH fee is covered by Ref's Aurora contract. Users will only need to pay an equivalent amount in bridged assets.
