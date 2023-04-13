---
description: Command-Line Interface Usage for Ref Exchange
---

# CLI Trading

{% hint style="info" %}
**Always** check that a wallet has a sufficient [storage deposit](https://nomicon.io/Standards/StorageManagement#example-1-fungible-token-contract) on a token's smart contract **before** initiating swaps, withdrawing liquidity, or withdrawing rewards. Failure to do so may result in the tokens being placed in the contract's "owner" account, requiring a vote by the Ref Community DAO to remove them.&#x20;
{% endhint %}

The following guide will help you to make actions on the contracts of Ref Finance via CLI.

We will use `$CONTRACT_ID` for contract account id and `$USER_ID` for user account id. `$TOKEN1`, `$TOKEN2`, et cetera are accounts for tokens.

You can set these variables via CLI: `export CONTRACT_ID=ref-finance.testnet`

## Deploy contract

Deploy to TestNet, to an account `$CONTRACT_ID` you have access keys for:

```
export NEAR_ENV=default
near deploy $CONTRACT_ID --wasmFile=res/ref_exchange.wasm
near call $CONTRACT_ID new "{\"owner_id\": \"$USER_ID\", \"exchange_fee\": 4, \"referral_fee\": 1}" --accountId $CONTRACT_ID
```

## Add a simple pool

Add simple pool with 2 tokens and 0.3% total fee (16% goes to the protocol and 4% goes to referral).

```
near call $CONTRACT_ID add_simple_pool "{\"tokens\": [\"$TOKEN1\", \"$TOKEN2\"], \"fee\": 25}" --accountId $USER_ID --amount 0.1
```

## Query pools

To query first 10 pools:

```
near view $CONTRACT_ID get_pools '{"from_index": 0, "limit": 10}'
```

## Register account in the exchange

```
near call $CONTRACT_ID storage_deposit '' --accountId $USER_ID --amount 0.1
```

If there is a token that is not whitelisted, you also need to register it separately:

```
near call $CONTRACT_ID register_tokens '{\"token_ids\": [\"$TOKEN1\", \"$TOKEN2\"]}' --accountId $USER_ID
```

## Query whitelisted tokens

This is list of tokens that don't need extra registration from the user. They are well known to the contract governance and are not expected to spam user's storage.

```
near view $CONTRACT_ID get_whitelisted_tokens
```

## Check that account is registered and storage available

```
near view $CONTRACT_ID storage_balance_of "{\"account_id\": \"$USER_ID\"}"
```

## Deposit funds

Before sending funds for token X, make sure that exchange is registered for token X.

```
near call $TOKEN1 storage_deposit "{\"account_id\": \"$CONTRACT_ID\"}" --accountId $USER_ID --amount 0.0125
```

Actually deposit funds to the exchange (attaching 1yN for security):

```
near call $TOKEN1 ft_transfer_call "{\"receiver_id\": \"$CONTRACT_ID\", \"amount\": \"1000000000000\", \"msg\": \"\"}" --accountId $USER_ID --amount 0.000000000000000000000001
```

## Query deposit balances in the exchange

```
near view $CONTRACT_ID get_deposits "{\"account_id\": \"$USER_ID\"}"
```

## Add liquidity to a pool

```
near call $CONTRACT_ID add_liquidity '{"pool_id": 0, "amounts": ["10000", "10000"]}' --accountId $USER_ID --amount 0.000000000000000000000001
```

## Get pool's information

```
near view $CONTRACT_ID get_pool '{"pool_id": 0}'
```

## Get pool's accumulated volume

```
near view $CONTRACT_ID get_pool_volumes '{"pool_id": 0}'
```

## Get number of liquidity shares in the pool

```
near view $CONTRACT_ID get_pool_shares "{\"pool_id\": 0, \"account_id\": \"$USER_ID\"}"
```

## Remove liquidity from a pool

```
near call $CONTRACT_ID remove_liquidity '{"pool_id": 0, "shares": "1000000000000000000000000", "min_amounts": ["1", "1"]}' --accountId $USER_ID --amount 0.000000000000000000000001
```

## Output amount after swap

```
near view $CONTRACT_ID get_return "{\"pool_id\": 0, \"token_in\": \"$TOKEN1\", \"amount_in\": \"10000\", \"token_out\": \"$TOKEN2\"}"
```

## Swap

Swap via a single pool:

```
near call $CONTRACT_ID swap "{\"actions\": [{\"pool_id\": 0, \"token_in\": \"$TOKEN1\", \"amount_in\": \"10000\", \"token_out\": \"$TOKEN2\", \"min_amount_out\": \"1\"}]}" --accountId $USER_ID --amount 0.000000000000000000000001
```

## Withdraw funds

To withdraw specific token from exchange back to user's account:

```
near call $CONTRACT_ID withdraw "{\"token_id\": \"$TOKEN1\", \"amount\": \"900000000000\"}" --accountId $USER_ID --amount 0.000000000000000000000001
```

## Check owner

```
near view $CONTRACT_ID get_owner
```

## Free up user's storage

When withdrawing tokens, if withdrawing everything - user can specify `unregister: true` to also remove storage occupied by any given token. Alternatively the user can call `near call $CONTRACT_ID unregister_tokens "{\"token_ids\": [\"$TOKEN1\"]}" --accountId $USER_ID` to remove balance of $TOKEN1 from user.

When all storage has been freed up (e.g. `near view $CONTRACT_ID get_deposits "{\"account_id\": \"$USER_ID\"}"` returns empty set), the user's account can be completely deleted:

```
near call $CONTRACT_ID storage_unregister '' --accountId $USER_ID
```
