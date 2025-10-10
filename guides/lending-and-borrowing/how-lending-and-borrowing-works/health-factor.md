# Health Factor

## Introduction <a href="#introduction" id="introduction"></a>

Users can borrow against their supplied assets. All positions must be over-collateralized. The risk of a position can be understood through the Health Factor, which represents the combined collateral ratios of the borrowed assets.

## Computation <a href="#computation" id="computation"></a>

The Health Factor is computed per account instead of per asset.

Each asset on Burrow has a configuration value `collateral_factor` which indicates the expected price stability factor.

The higher the factor, the higher expectation of the stability of the price of the corresponding asset.

To compute the current health factor for the account, we need to know the current prices of all collateral and borrowed assets.

Firstly, we compute the adjusted sums of all collateral assets and borrowed assets.

`adjusted_collateral_sum = sum(collateral_i * price_i * collateral_factor_i) adjusted_borrowed_sum = sum(borrowed_i * price_i / collateral_factor_i)`

Now we can compute the health factor:

`health_factor = adjusted_collateral_sum / adjusted_borrowed_sum`

If the health factor is higher than 100%, it means the account is in a good state and can't be liquidated.

If the health factor is less than 100%, it means the account can be partially liquidated and can't borrow more without repaying some amount of the existing assets or providing more collateral assets.



> In lending & borrowing smart contracts, `collateral_factor` is also named `volatility_ratio`

Example\
 <a href="#computation" id="computation"></a>
---------------------------------------------

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
