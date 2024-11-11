---
description: '"Classic" Liquidity Pools'
---

# Classic Pools

Classic pools are based on the Uniswap v2 algorithm. They are fully permissionless, meaning that anyone can create a classic pool, and set the fee for that pool.

## Adding liquidity to a Classic Pool

### 1. Go to the Classic Pools tab on the Liquidity Pools page

The Liquidity Pools page can be found in the top menu under "Earn"

<figure><img src="../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

Make sure you are on the "Classic Pools" tab.&#x20;

<figure><img src="../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

### 2. Locate a specific pool

There's a search box to filter pools by token, and check boxes to filter by characteristics, such as pools with Farms

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Incentivized pools have a "Farms" tag next to their token pairs, and those with multiple reward tokens will include a special icon within the tag.&#x20;

<figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

### 3. Open the "Details" page for a pool&#x20;

Clicking on a pool on the Pools page opens that pool's "Details" page. The pool's Details page shows, well, details about the pool, like the current and historical TVL and 24-hour volume. The pool's Details page also includes an "Add Liquidity" button to open the form for depositing tokens into the pool.

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

The pool's Details page has an "Add Liquidity" button that, when clicked, will open the form for depositing tokens into the pool. If you currently have liquidity in the pool, the button will be named simply "Add", and there will be a "Remove" button next to it.&#x20;

<figure><img src="../../../.gitbook/assets/image (42).png" alt="" width="362"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (43).png" alt="" width="365"><figcaption></figcaption></figure>

### 4. Use the Add Liquidity form to add tokens to the pool

After clicking the the "Add Liquidity" button on the pool's Detail page, the Add Liquidity Form will open. Use this form to enter the amount of tokens you want to deposit. The amounts must be in the same proportion as the balance of the pool at that point in time. When you enter an amount for one token, the form will automatically set the proper amount for the second token. You must have **both** tokens in your wallet to add liquidity to a classic pool.

If you click the "Max" button next to a token symbol, the form will enter the full amount of that token that is in your wallet.&#x20;

<figure><img src="../../../.gitbook/assets/image (44).png" alt="" width="375"><figcaption></figcaption></figure>

Click "Pool Stats" at the bottom of the Add Liquidity form to see details about the pool, including the balance of tokens, and the fee for swaps that take place on that pool.

<figure><img src="../../../.gitbook/assets/image (45).png" alt="" width="375"><figcaption></figcaption></figure>

## Removing liquidity from a pool

### 1. Go to the Your Liquidity page

You can see all pools you have liquidity in by going to the Your Liquidity page. You can get to the Your Liquidity page by clicking Earn > Your Liquidity in the main menu of the site.&#x20;

<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

### 2. Unstake shares from a farm, if necessary

If your shares are staked on a farm you must unstake them before you can remove your liquidity from the pool. If only some shares are staked, you will be able to remove the liquidity for the unstaked portion. See [Farming](../farming.md) for more details about staking and unstaking shares.

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

### 3. Use the Remove Liquidity form to withdraw tokens from the pool

After clicking the Remove button, the Remove Liquidity form will appear. You can enter an amount of shares to remove, or click the "MAX" button to remove the liquidity for all your shares.

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Increase the slippage tolerance If you receive slippage related errors when attempting to remove liquidity from a pool. This may be necessary if there are a lot of swaps occurring on the pool at that time, especially if the pool does not have a lot of liquidity in it.

## Creating a new Classic pool

There are several reasons why you may want to create a new Classic pool on Ref Finance:

1. A pool with the token pairs does not currently exist.
2. A pool with the token pairs exists, but you believe their fees are too high or too low.
3. A pool with the token pairs exists, but you believe the ratio of the token pairs (Amount of Token A / Amount of Token B) is not accurate.

### 1. Click the "Create Pool" button on the Pools page.

The Liquidity Pools page can be found in the top menu under "Earn"

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Make sure you are on the "Classic Pools" tab.&#x20;

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

### 2. Use the "Create New Pool" form to configure the new pool

After clicking the "Create Pool" button on the Pools page, the "Create New Pool" form will open. Select the token pairs, enter the total fee for the pool, and then click the "Create" button. You will be able to add liquidity to the pool after it is created. Once a pool is created, the fee cannot be changed.&#x20;

To set the total fee, click on one of the three predefined fees (0.20%, 0.30%, 0.60%), or use the text box to enter any value from 0.01% to 19.99%.

<figure><img src="../../../.gitbook/assets/image (53).png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (54).png" alt="" width="375"><figcaption></figcaption></figure>

When trades occur on a Classic pool, 80% of the total fee will be shared among liquidity providers, while the remaining 20% will go toward the Protocol fee and/or Referral fee.&#x20;

### 3. Deposit tokens into the newly created Pool

After the new pool is created, you will be taken to the pool's Details page. Since this pool has just been created, all values are set to zero.

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

### 4. Use the Add Liquidity form to add tokens to the new pool

Just like when [adding liquidity to an existing pool](classic-pools.md#4.-use-the-add-liquidity-form-to-add-tokens-to-the-pool), you click the Add Liquidity button on the new pool's Details page to open the Add Liquidity form. The only difference between adding liquidity to a newly created pool vs an existing one, is that for newly created pools, you can set any amount to deposit for both tokens. The amounts you choose will determine the starting ratio of the tokens. This ratio will change whenever a trade takes place on the pool.&#x20;

It is recommended that you do your own research before deciding on the initial balance of a pool. Choosing an incorrect amount can result in a significant loss of funds within seconds of your initial deposit, as arbitrage bots take advantage of the difference between your pool's token balance and those on existing pools, exchanges, or prices on other types of trading services.&#x20;
