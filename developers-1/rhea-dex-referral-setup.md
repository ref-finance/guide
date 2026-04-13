---
description: Command-Line Interface Referral Integration Guide
---

# RHEA Dex Referral Setup

Command-line interface usage for referral setup on:

* REF\_EX
* REF\_DCL

The following guide will help you register, verify, and check referral-related data via CLI.<br>



We will use:

* `$REF_EX` for the REF\_EX contract account
* `$REF_DCL` for the REF\_DCL contract account
* `$USER_ID` for the user account
* `$REFERRAL_ID` for the referral account or referral identifier
* `$POOL_TOKEN_ID` for the pool MFT token ID

## REF\_EX

Command-line interface usage for referral setup on REF\_EX.\
\
For a referral to work on REF\_EX, the referral must first be registered in the contract. After that, the referral account must also register the corresponding pool MFT.

### Referrals

To view the current list of registered referrals:

```
near view $REF_EX list_referrals
```

### Register

If the referral has not been added yet, please reach out to RHEA Finance to submit an application.

### MFT Status

After the referral is registered, the corresponding pool MFT must also be registered for the referral account.

To check whether the MFT has already been registered:

```
 near view $REF_EX mft_has_registered "{\"token_id\": \"$POOL_TOKEN_ID\", \"account_id\": \"$USER_ID\"}"
```

### MFT Register

If the MFT has not been registered yet, the referral account must register it manually:

```
 near call $REF_EX mft_register "{\"token_id\": \"$POOL_TOKEN_ID\", \"account_id\": \"$USER_ID\"}" --account_id=$USER_ID --amount=0.01
```

This step should be completed by the referral account owner.

### Check Balance

To query the MFT balance for the referral account:

```
 near view $REF_EX mft_balance_of "{\"token_id\": \"$POOL_TOKEN_ID\", \"account_id\": \"$USER_ID\"}"
```

### Flow

A typical REF\_EX referral setup flow is:

1. ​Check whether the referral already exists
2. ​Register the referral if needed
3. ​Check whether the related pool MFT is registered
4. ​Register the pool MFT if needed
5. ​Query the referral MFT balance

​

## REF\_DCL

Command-line interface usage for referral setup on REF\_DCL.

​

For a referral to work on REF\_DCL, the referral account must first be added to the whitelist. Once it is valid, the referral can be included in swap calls and its internal asset balance can be checked later.

### Whitelist

To view the current referral whitelist:

```
 near view $REF_DCL get_referral_whitelist
```

### Validate

To check whether a referral account is already approved:

```
 near view $REF_DCL is_valid_referral '{"account_id": "**.near"}'
```

### Register

If the referral has not been added yet, please reach out to RHEA Finance to submit an application.​

### Result

Upon completion of registration, enter the parameters as shown below.

```
 near call 17208628f84f5d6ad33f0da3bbbeb27ffcb398eac501a31bd6ad2011e36133a1 ft_transfer_call '{"receiver_id": "'$REF_DCL'", "amount": "1000000", "msg": "{\"Swap\":{\"pool_ids\":[\"17208628f84f5d6ad33f0da3bbbeb27ffcb398eac501a31bd6ad2011e36133a1|wrap.near|2000\"],\"output_token\":\"wrap.near\",\"min_output_amount\":\"1000000\",\"referral_id\":\"ma***.near\"}}"}' --depositYocto=1 --gas=300$TGAS --account_id=li***.near
```

### Check Balance

To view the internal asset balance for a referral account

```
near view $REF_DCL list_user_assets '{"account_id": "ma***.near"}'
```

### Flow

A typical REF\_DCL referral setup flow is:

1. ​Query the current whitelist
2. ​Check whether the referral account is valid
3. ​Register the referral if needed
4. ​Include the referral\_id in the swap call
5. ​Query the referral account’s internal assets

​

<br>
