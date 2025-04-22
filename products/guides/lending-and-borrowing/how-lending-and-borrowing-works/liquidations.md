# Liquidations

## Introduction

A liquidation is triggered when an account's Health Factor goes below 100%, due to its collateral value not being sufficient to cover the debt value. This might happen when the collateral decreases in value or the borrowed debt increases in value.

Burrow's liquidation mechanism is designed to make liquidators compete for the profit that they make during liquidations to minimize the loss taken by unhealthy accounts. This is achieved by introducing a variable discount with variable liquidation size, Instead of offering a fixed profit that is used in other protocols.



## Liquidation rules <a href="#liquidation-rules" id="liquidation-rules"></a>

Liquidations on Burrow follow 3 basic rules:

1. The initial health factor of the liquidated accounts has to be below 100%
2. The discounted sum of the taken collateral should be less than the sum of repaid assets
3. The final health factor of the liquidated accounts has to stay below 100%

The first rule only allows liquidating accounts in an unhealthy state. The second rule prevents from taking more collateral than the repaid sum (after discount). The third rule prevents the liquidator from repaying too much of the borrowed assets, only enough to bring closer to the 100%.



A liquidation action consists of the following:

* `account_id` - the account ID that is being liquidated
* `in_assets` - the assets and corresponding amounts to repay form borrowed assets
* `out_assets` - the assets and corresponding amounts to take from collateral assets



The discount is computed based on the initial health factor of the liquidated account:

`discount = (1 - health_factor) / 2`

Now we can compute the taken discounted collateral sum and the repaid borrowed sum:

* `taken_sum = sum(out_asset_i * price_i)`
* `discounted_collateral_sum = taken_sum * (1 - discount)`
* `repaid_sum = sum(in_asset_i * price_i)`

Once the action is completed, we can compute the final values and verify the liquidation rules:

1. `health_factor < 100%`
2. `discounted_collateral_sum <= repaid_sum`
3. `new_health_factor < 100%`

## Liquidation example

Account `alice.near` supplied to collateral `1000 wNEAR` and borrowed `4000 nDAI`.

Let's say (note: the numbers are hypothetical for illustration purposes only):

* the price of `wNEAR` is `10`
* the price of the `nDAI` is `1`
* the `collateral_factor` of `wNEAR` is `0.5`
* the `collateral_factor` of `nDAI` is `1`

The health factor of `alice.near` is the following:

* `adjusted_collateral_sum = sum(1000 * 10 * 0.5) = 5000`
* `adjusted_borrowed_sum = sum(4000 * 1 / 1) = 4000`
* `health_factor = 5000 / 4000 = 125%`

Let's say the price of `wNEAR` drops to `8`

* `adjusted_collateral_sum = sum(1000 * 8 * 0.5) = 4000`
* `adjusted_borrowed_sum = sum(4000 * 1 / 1) = 4000`
* `health_factor = 4000 / 4000 = 100%`

The health factor is 100%, so the account still can't be liquidated.

Let's say the price of `wNEAR` drops to `7`

* `adjusted_collateral_sum = sum(1000 * 7 * 0.5) = 3500`
* `adjusted_borrowed_sum = sum(4000 * 1 / 1) = 4000`
* `health_factor = 3500 / 4000 = 0.875 = 87.5%`

The health factor is below 100%, so the account can be liquidated. The discount is the following:

`discount = (1 - 0.875) / 2 = 0.0625 = 6.25%`

It means anyone can repay some `nDAI` and take some `wNEAR` from `alice.near` with `6.25%` discount.

Account `bob.near` decides to liquidate `alice.near`

`bob.near` wants to repay `1000 nDAI`, we can compute the maximum sum of the collateral to take:

* `repaid_sum = sum(1000 * 1) = 1000`
* `max_taken_sum = repaid_sum / (1 - discount) = 1000 / (1 - 0.0625) = 1066.666`

And based on the `wNEAR` price, we can compute the maximum amount:

`max_wnear_amount = max_taken_sum / wnear_price = 1066.666 / 7 = 152.38`

But to avoid risk, `bob.near` takes `152` `wNEAR` - a bit less to avoid price fluctuation for the duration of the transaction.

Let's compute the liquidation action:

* `taken_sum = sum(out_asset_i * price_i) = sum(152 * 7) = 1064`
* `discounted_collateral_sum = taken_sum * (1 - discount) = 1064 * (1 - 0.0625) = 997.5`
* `repaid_sum = sum(in_asset_i * price_i) = sum(1000 * 1) = 1000`
* `new_adjusted_collateral_sum = sum((1000 - 152) * 7 * 0.5) = 2968`
* `new_adjusted_borrowed_sum = sum((4000 - 1000) * 1 / 1) = 3000`
* `new_health_factor = 2968 / 3000 = 0.9893 = 98.93%`

Now checking the liquidation rules:

`1. 87.5% < 100% 2. 997.5 <= 1000 3. 98.93% < 100%`

All rules were satisfied, so the liquidation was successful.

Now, let's compute the profit of `bob.near` (or the loss for `alice.near`) for this liquidation:

`profit = taken_sum - repaid_sum = 1064 - 1000 = 64`



Notes:

* During the time when the price of `wNEAR` was falling from `8` to `7`, if someone liquidated `alice.near`, they would have made less profit, by liquidating a smaller amount with a smaller collateral discount.
* To fully realize the profit, `bob.near` has to make another transaction to swap received `152` `wNEAR` for `nDAI`, which may involve extra fees and transactional risks. That's why liquidators may wait for higher discount.



## Liquidation Bot <a href="#liquidation-bot" id="liquidation-bot"></a>

You can find an example liquidation bot [here](https://github.com/NearDeFi/burrowland-liquidation-bot).\
