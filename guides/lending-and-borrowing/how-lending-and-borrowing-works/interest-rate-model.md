# Interest Rate Model

The platform uses a compounding interest model similar to [Aave](https://docs.aave.com/risk/liquidity-risk/borrow-interest-rate).

Each asset defines interest rate configuration with the following values:

* `target_utilization` - the utilization rate targeted by the model, e.g. 80% borrowed comparing to the total supplied.
* `target_utilization_r` - the constant to use as a base for computing compounding APR at the target utilization.
* `max_utilization_r` - the constant to use as a base for computing compounding APR at the 100% utilization.
* `reserve_ratio` - the percentage of the acquired interest reserved for the platform.

Based on these values we define 3 points of utilization: `0%`, target utilization and `100%`. For each of these points we have the `r` constant: `1.0`, `target_utilization_r` and `max_utilization_r` respectively.

To compute the APR, we can use the following formula:

`1 + APR = r ** MS_PER_YEAR`, where MS\_PER\_YEAR is the number of milliseconds in a year equal to `31536000000`.

Based on the current supplied, reserved and borrowed balances, the current utilization is defined using the following formula:

`utilization = borrowed / (supplied + reserved)`

To compute the current APR, we need to find the current `r` constant based on the linear interpolation between utilization points:

* if `utilization <= target_utilization`, `r = target_utilization_r * (utilization / target_utilization)`
* if `utilization > target_utilization`, `r = target_utilization_r + (max_utilization_r - target_utilization_r) * (utilization - target_utilization) / (1 - target_utilization)`

To calculate the amount of interest acquired for the duration of `t` milliseconds, we can use the following formula:

`interest = (r ** t) * borrowed`

The interest are distributed to `reserved` and `supplied`, based on `reserve_ratio`, so the new values are: `reserved_interest = interest * reserve_ratio new_reserved = reserved + reserved_interest new_supplied = supplied + (interest - reserved_interest) new_borrowed = borrowed + interest`
