# Lending & Borrowing

Burrow stands as a decentralized platform that operates on a pool-based model, allowing users to both supply assets to generate interest and borrow against these assets to access liquidity. Similar in essence to protocols like Aave and Compound, Burrow offers a non-custodial approach to handling assets.

Operating natively on the NEAR blockchain, which is a proof-of-stake, sharded blockchain equipped with a WebAssembly runtime, Burrow differentiates itself by employing smart contracts written in Rust.

The primary objective of Burrow is to enhance liquidity for interest-earning assets, with a specific focus on layer 1 staking derivatives like stNEAR and stETH. Users can deposit stNEAR as collateral, subsequently borrowing additional NEAR to create a leveraged staking position or even borrow a stablecoin to establish a self-repaying position.

Full Burrow Docs ( [https://docs.burrow.cash/product-docs/introduction/burrow](https://docs.burrow.cash/product-docs/introduction/burrow) )

## Ref Overseas Burrow

Currently, Ref Finance is taking charge of managing and developing the Burrow protocol, which serves as the leading money market on the NEAR blockchain. This strategic decision underscores Ref's dedication to enhancing the DeFi ecosystem on NEAR by means of collaboration rather than rivalry.

As a consequence of this collaboration, users will benefit from a streamlined and robust DeFi experience, as they can access all present and future features of the Burrow protocol through a unified user interface within Ref's platform.

**Read full article on Medium:** [https://ref-finance.medium.com/ref-finance-oversees-burrow-to-strengthen-defi-on-near-23802c8d74a5](https://ref-finance.medium.com/ref-finance-oversees-burrow-to-strengthen-defi-on-near-23802c8d74a5)&#x20;

## Core Metrics

### Net APY

Net APY in DeFi considers the actual earnings or costs after accounting for fees and expenses. It shows how much you could truly gain or lose from activities like lending and borrowing, factoring in any charges that might affect your overall return. The Net APY is calculated as follows:

total\_supply = sum(supply\_i \* price\_i)

total\_supply\_interest = sum(supply\_i \* price\_i \* supply\_apy\_i)&#x20;

total\_borrow\_interest = sum(borrow\_i \* price\_i \* borrow\_apy\_i)&#x20;

net\_apy = (total\_supply\_interest - total\_borrow\_interest) / total\_supply

### Health Factor

The health factor is a metric used to assess the safety of a borrower's position in a DeFi protocol. It is calculated by dividing the value of the collateral by the borrowed amount. Now we can compute the health factor:

health\_factor = adjusted\_collateral\_sum / adjusted\_borrowed\_sum

If the health factor is higher than 100%, it means the account is in a good state and can't be liquidated. If the health factor is less than 100%, it means the account can be partially liquidated and can't borrow more without repaying some amount of the existing assets or providing more collateral assets.

### Total Supplied

Total supplied refers to the total amount of crypto assets that users have provided to a DeFi protocol's liquidity pool or lending platform. These assets are used by others for various purposes like trading or borrowing.

### Total Borrowed

Total borrowed indicates the combined amount of crypto assets that users have borrowed from a DeFi lending platform or protocol. These assets are typically used to trade, invest, or fulfill other financial activities.

### Available Liquidity

Available liquidity in DeFi represents the amount of assets that can be borrowed from a lending pool or liquidity pool. It's the portion of the supplied assets that are not currently being used by borrowers.\


### Daily Rewards

Daily rewards in DeFi refer to the crypto assets that users earn on a daily basis for participating in specific DeFi protocols or activities. These rewards can be in the form of interest, trading fees, or other incentives provided by the platform.

## BURROW UI GUIDE ON REF FINANCE

(This defines the step-by-step procedures on how to do the following)

### Supply

Step 1: Access [https://app.ref.finance/burrow](https://app.ref.finance/burrow) and connect your wallet

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 01.24.26.png" alt=""><figcaption></figcaption></figure>

Step 2: Select one asset from the list and click “Supply”

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-10 at 00.53.19.png" alt=""><figcaption></figcaption></figure>

Step 3: Enter your desired number and turn on “Use as Collateral” (Optional)

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 01.28.19 (1).png" alt=""><figcaption></figcaption></figure>

Step 4: Supply and sign the transaction

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-10 at 15.16.53.png" alt=""><figcaption></figcaption></figure>

### Borrow

Make sure you have already supplied your asset (and turned on Use as collateral button) first before borrowing.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 13.45.53.png" alt=""><figcaption></figcaption></figure>

Step 1: Select a token you want to borrow

I will borrow $DAI using $NEAR as collateral in this situation

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 13.47.33.png" alt=""><figcaption></figcaption></figure>

Step 2: Choose an appropriate amount

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 13.50.06.png" alt=""><figcaption></figcaption></figure>

Step 3: Verify all the details and confirm the transaction

### Repay

Step 1: Click on Repay Button

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Step 2: Enter an appropriate amount&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 13.59.22.png" alt=""><figcaption></figcaption></figure>

Notice that Health Factor changes every time you increase/decrease the repayment amount

Step 3: Confirm the transaction

### Withdraw

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 14.07.48.png" alt=""><figcaption></figcaption></figure>

Step 1: Select the token you wish to withdraw and click "Withdraw" button

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 14.13.20.png" alt=""><figcaption></figcaption></figure>

Step 2:  Choose an appropriate amount

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Step 3: Verify the details and confirm your transaction

### Adjusting collateral

Step 1: Select the token and click "Adjust" button

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 14.13.20.png" alt=""><figcaption></figcaption></figure>

Step 2: Enter an appropriate amount&#x20;

Keep an eye on your Health Factor since it will adjust following your collateral position

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 14.35.05.png" alt=""><figcaption></figcaption></figure>

Step 3: Confirm the transaction
