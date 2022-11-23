# Contracts

All contracts are on the NEAR Protocol. The source code of Ref Finance can be found on [Github](https://github.com/ref-finance).

Find below the list of all accounts that have directly managed or currently manage the affairs of Ref Finance.

| Address                                                          | Type                                | Mission                                                                                   | Locked?          | Owner                                                                                           | Source Code                                                                            |
| ---------------------------------------------------------------- | ----------------------------------- | ----------------------------------------------------------------------------------------- | ---------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| v2.ref-finance.near                                              | Exchange Contract                   | Manage the Automated Market Maker functions; Swap and Provide Liquidity                   | Yes              | ref-finance.sputnik-dao.near                                                                    | [Link](https://github.com/ref-finance/ref-contracts/tree/main/ref-exchange)            |
| boostfarm.ref-labs.near                                          | Farming Contract                    | Manage liquidity incentives                                                               | No (In Progress) | ref-dev-team.near                                                                               | [Link](https://github.com/ref-finance/boost-farm)                                      |
| ref-ve.ref-labs.near                                             | Vetokenomics Contract               | Manage Vote-Escrowed Token (veToken)                                                      | No (In Progress) | ref-dev-team.near                                                                               | [Link](https://github.com/ref-finance/ref-ve)                                          |
| xtoken.ref-finance.near                                          | Staking Contract                    | Mint and burn xREF, and Distribute time-based rewards                                     | Yes              | ref-finance.sputnik-dao.near                                                                    | [Link](https://github.com/ref-finance/ref-token/tree/master/xref-token)                |
| ref-finance.sputnik-dao.near                                     | Sputnik DAO Contract                | Ensure the success of Ref by taking strategic decisions (incl. smart contract amendments) | Yes              | Multisig ([Link](https://app.astrodao.com/dao/ref-finance.sputnik-dao.near/groups/all))         | [Link](https://github.com/near-daos/sputnik-dao-contract)                              |
| ref-community-board.sputnik-dao.near                             | Sputnik DAO Contract                | Manage and allocate funds to specific community contributors                              | Yes              | Multisig ([Link](https://app.astrodao.com/dao/ref-community-board.sputnik-dao.near/groups/all)) | [Link](https://github.com/near-daos/sputnik-dao-contract)                              |
| dao.ref-dev-team.near                                            | Sputnik DAO Contract                | Execute the Strategy and Roadmap                                                          | Yes              | Multisig ([Link](https://dev-fund.ref-finance.com/#/dao.ref-dev-team.near/))                    | [Link](https://github.com/near-daos/sputnik-dao-contract)                              |
| ref.ref-dev-fund.near                                            | Vesting Contract                    | Manage REF vesting contracts of Dev DAO members                                           | Yes              | dao.ref-dev-team.near                                                                           | [Link](https://github.com/ref-finance/ref-dev-fund/tree/session\_vault/session\_vault) |
| s01.ref-airdrop.near                                             | Airdrop Contract                    | Manage first REF airdrop                                                                  | Yes              | N/A                                                                                             | [Link](https://github.com/skyward-finance/contracts/tree/master/lockup)                |
| ref-bug-bounty-1.near                                            | Simple Address                      | Manage one-time bug bounty payments                                                       | N/A              | N/A                                                                                             | N/A                                                                                    |
| token.v2.ref-finance.near                                        | Fungible Token Contract             | Mint REF token                                                                            | Yes              | N/A                                                                                             | [Link](https://github.com/ref-finance/ref-token/tree/deployed-ref-token/ref-token)     |
| ref-finance.near                                                 | Exchange Contract                   | v1 (obsolete) - Manage the Automated Market Maker functions; Swap and Provide Liquidity   | No               | N/A                                                                                             | [Link](https://github.com/ref-finance/ref-contracts/tree/main/ref-exchange)            |
| token.ref-finance.near                                           | Fungible Token Contract             | v1 (obsolete) - Mint REF token                                                            | Yes              | N/A                                                                                             | N/A                                                                                    |
| v2.ref-farming.near                                              | Farming Contract                    | v2 (obsolete) - Manage liquidity incentives                                               | No               | ref-dev-team.near                                                                               | [Link](https://github.com/ref-finance/ref-contracts/tree/main/ref-farming)             |
| refchef.near                                                     | Simple Address                      | Manage inter-account transactions                                                         | N/A              | N/A                                                                                             | N/A                                                                                    |
| ref-farm-reward-proxy.near                                       | Simple Address                      | Manage third-party deposits for liquidity incentives                                      | N/A              | N/A                                                                                             | N/A                                                                                    |
| a4b55d572d5f41c0dbbb88fd1317ebff87edcc75cad5d8705c55e94c48993926 | Simple Address                      | Manage Protocol Revenue Conversion - REF buyback (Q2 2022)                                | N/A              | N/A                                                                                             | N/A                                                                                    |
| 28d262719c5d97e3c570a5a71a817820300a97bd086136923e44812193ef6c4d | Simple Address                      | Manage Protocol Revenue Conversion - REF buyback (Q3 2022)                                | N/A              | N/A                                                                                             | N/A                                                                                    |
| ref-dev-teller.near                                              | Simple Address                      | Manage inter-account transactions                                                         | N/A              | N/A                                                                                             | N/A                                                                                    |
| 0x102d7FaD37A4e0266A0AFDcDc90A04408F9ac091                       | Simple Address (Ethereum)           | Manage TRI<>REF Liquidity Provision on Tri Solaris                                        | N/A              | N/A                                                                                             | N/A                                                                                    |
| 0x45d76fa8498239ed5fc4dcd7377f92beec5c48d6                       | <p>Simple Address<br>(Ethereum)</p> | Manage strategic OTC [deal](https://gov.ref.finance/t/a-strategic-ref-otc-wip/448) (2022) | N/A              | N/A                                                                                             | N/A                                                                                    |

## Timelock

Timelocks are a smart contract feature that states that some actions will only be performed after a certain period of time rather than immediately.&#x20;

Ref Finance does not use/have a timelock feature. Ref contracts are directly upgraded from the DAO (ref-finance.sputnik-dao.near), thus providing time to users, via the voting period of the associated proposal, to protect their funds in case they identify suspicious activities.

DAO proposals usually take from 48 to 72 hours either to get approved or rejected.

## Frozen List

The Ref Finance Exchange contract (v2.ref-finance.near) has a 'Frozen List' feature, which was deployed on version 1.6.0+.

The feature enables the owner and/or [Guardians](guardians.md) of the contract to freeze any token listed on the exchange. When frozen, any action (Swap, Add/Remove liquidity, Deposit, Withdraw, etc.) on the corresponding token will fail, resulting in a 'panic error' at the contract level.

The owner and/or [Guardians](guardians.md) can use the following commands to freeze/unfreeze any token:

```
near call $REF_EX extend_frozenlist_tokens '{"tokens": ["'$TOKEN1'", "'$TOKEN2'"]}' --account_id=$REF_GUARDIAN --depositYocto=1

near call $REF_EX remove_frozenlist_tokens '{"tokens": ["'$TOKEN1'", "'$TOKEN2'"]}' --account_id=$REF_GUARDIAN --depositYocto=1
```

To get the Frozen List, anyone can query the following command:

```
near view $REF_EX get_frozenlist_tokens
```

### Motivation

The Frozen List feature has been designed to mitigate the impact of any attack or hack associated to a specific token and its potential contagion within the ecosystem.

The feature can also be activated as a preventive measure. For example, in November 2022, Metapool identified a critical [bug](https://twitter.com/meta\_pool/status/1588245211850776577?s=20\&t=K-osl2RR5sjMkHBfoVG9gg) on its contract. Ref Finance was informed and immediately froze the STNEAR token, preventing users from any associated action (trading and pooling) on Ref, thus reducing the severity of the impact (trading losses, extreme volatility, etc.) that such a bug could have caused to traders and LPs.
