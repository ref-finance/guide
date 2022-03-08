---
description: Commande-Line Interface Usage for Ref Farming
---

# CLI Farming

You can setup the following parameters:

```
export FARMING=ref-farming.testnet
export EX=ref-finance.testnet
export TOKEN=token.ref-finance.testnet
```

## View general information

```
near view $FARMING get_metadata
```

## View all farms with pagination

```
near view $FARMING list_farms '{"from_index": 0, "limit": 100}'
```

Notes:

* Outdated\_farms are excluded
* There are three `farm_status` in contract, they are Created, Running, Ended
* `start_at` is timestamp in seconds
* `session_interval` is timestamp in seconds

## View all seeds with pagination&#x20;

```
near view $FARMING list_seeds_info '{"from_index": 0, "limit": 100}'
```

## View all rewards with pagination

```
near view $FARMING list_rewards_info '{"from_index": 0, "limit": 100}'
```



## View single seed information

```
near view $FARMING get_seed_info "{\"seed_id\": \"$EX@9\"}"
```

## View all farms per seed

```
near view $FARMING list_farms_by_seed "{\"seed_id\": \"$EX@9\"}"
```

## View single farm information

```
near view $FARMING get_farm "{\"farm_id\": \"$EX@11#0\"}"
```

## View rewards per user

```
near view $FARMING list_rewards '{"account_id": "pika456.testnet"}'
```

## View unclaimed rewards per user

```
near view $FARMING get_unclaimed_reward "{\"account_id\": \"pika456.testnet\", \"farm_id\": \"$EX@30#0\"}"
```

## View seeds per user

```
near view $FARMING list_user_seeds '{"account_id": "pika456.testnet"}'
```

## Stake/Unstake seed

```
# if needed, register user to the farming
near call $FARMING storage_deposit '{"account_id": "u1.testnet", "registration_only": true}' --account_id=u1.testnet --amount=1

# if needed, register farming contract to seed token
near call $EX mft_register "{\"token_id\":\"31\", \"account_id\": \"$FARMING\"}" --account_id=u1.testnet --amount=0.01

# staking
near call $EX mft_transfer_call "{\"receiver_id\": \"$FARMING\", \"token_id\":\"31\", \"amount\": \"1000000000000000000000000\", \"msg\": \"\"}" --account_id=u1.testnet --amount=0.000000000000000000000001

# unstaking
near call $FARMING withdraw_seed "{\"seed_id\": \"$EX@31\", \"amount\": \"1000000000000000000000000\"}" --account_id=u1.testnet --amount=0.000000000000000000000001
```

## Claim rewards

```
# you can claim reward per farm
near call $FARMING claim_reward_by_farm "{\"farm_id\": \"$EX@0#1\"}" --account_id=u1.testnet --amount=0.000000000000000000000001

# or you can claim reward per seed (kind of batch claim)
near call $FARMING claim_reward_by_seed "{\"seed_id\": \"$EX@0\"}" --account_id=u1.testnet --amount=0.000000000000000000000001
```

## Withdraw reward token

```
# amount set to 0 means withdraw all balance
near call $FARMING withdraw_reward "{\"token_id\": \"$TOKEN\", \"amount\": \"0\"}" --account_id=u1.testnet --amount=0.000000000000000000000001
```

## Create farm

{% hint style="info" %}
At the moment, only the owner of this contract can create farms
{% endhint %}

To create a farm, you need to prepare the farming terms accordingly.

```
near call $FARMING create_simple_farm "{\"terms\": {\"seed_id\": \"$EX@31\", \"reward_token\": \"$TOKEN\", \"start_at\": 0, \"reward_per_session\": \"10000000000000000000\", \"session_interval\": 3600}}\" --account_id=pika456.testnet --amount 0.01
# this will return a farm id like ref-finance.testnet@31#0
```

At this point, this is a farm with no reward deposited, farm status is Created.

To activate a farm, deposit some reward tokens into the farm with ft\_transfer\_call.

```
# if needed, register farming contract to reward token
near call $TOKEN storage_deposit "{\"account_id\": \"$FARMING\"}" --account_id=pika456.testnet --amount 0.00125

# deposit reward token into the farm
near call $TOKEN ft_transfer_call "{\"receiver_id\": \"$FARMING\", \"amount\": \"2400000000000000000000\", \"msg\": \"$EX@31#0\"}" --account_id=$REF_OWNER --amount=0.000000000000000000000001 --gas=100000000000000
```
