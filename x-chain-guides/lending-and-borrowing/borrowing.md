# Borrowing

## Introduction

Users can borrow against their supplied assets. All positions must be over-collateralized. If the value of a user's collateral drops below the minimum collateral ratio, their collateral will be liquidated to pay off their debt.

On the borrowing platform, each asset has a unique minimum collateral ratio, as each asset carries unique risk. The collateral ratios of each asset can be found here

The aggregate risk of an account can be understood through the Health Factor, which represents the combined collateral ratios of the borrowed assets.

If the health factor is higher than 100%, it means the account is in a good state and can't be liquidated.

If the health factor is less than 100%, it means the account can be partially liquidated and can't borrow more without repaying some amount of the existing assets or providing more collateral assets.

To learn more about how the health factor is calculated, click here
