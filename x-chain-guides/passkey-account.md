---
description: >-
  To reduce onboarding friction and improve the cross-chain user experience,
  CrossChain Lending supports Passkey-based accounts. Allows users to create and
  access an account without managing private key
---

# PassKey Account

Below is a **clean, GitBook-ready version** with clearer structure, tighter language, and consistent terminology. I’ve kept it neutral and product-focused, suitable for user + dev docs.

***

### Passkey and CrossChainLendingAccount Relationship

Account Creation Mechanism

Users can create a **CrossChainLendingAccount** using only a Passkey.

How it works:

* The **Passkey public key** is recorded in a smart contract on the **NEAR blockchain**
* The contract treats this public key as a **valid account control credential**
* The Passkey **does not store or expose a private key**

> ⚠️ **Important**\
> A Passkey is **not an on-chain wallet**.\
> It is an **identity and signing mechanism** only.

***

#### Security & Risk Considerations (Critical)

Passkeys have important limitations:

* ❌ Private keys **cannot be exported**
* ❌ Strong dependency on the device and system environment\
  (browser, OS, biometric setup)
* ❌ Device loss or environment changes may result in **permanent loss of access**

As a result, a Passkey-only account **may become unrecoverable** if no backup control method is added.

***

### Mandatory Security Policy: External Wallet Binding

#### Binding Requirement

After creating a CrossChainLendingAccount with a Passkey, users **must bind a wallet from another blockchain**, such as:

* EVM-compatible Wallets
* Solana Wallets
* NEAR Wallets
* Other supported chains

***

#### Purpose of Wallet Binding

Binding an external wallet:

* Provides a **recoverable backup control method**
* Prevents permanent account loss if the Passkey is unavailable
* Enables the bound wallet to act as:
  * An account management tool
  * A signer for critical operations
  * The primary **access recovery method**

***

#### Product-Level Constraints (Recommended)

After Passkey account creation, the UI should:

* Prompt users to **bind an external wallet immediately**
* Restrict **Supply / Borrow** actions until binding is completed
* Display a clear warning:

> **“Passkeys are not recoverable. Please bind another blockchain wallet immediately.”**

***

### Functional Scope of Passkey-Based Accounts

General Principle

If an operation **does not transfer assets out** of the CrossChainLendingAccount, it is considered **safe** for Passkey-based accounts.

***

#### Supported Operations

**✅ Supply**

* Assets are supplied **into** the CrossChainLendingAccount
* The `to` address is the CrossChainLendingAccount
* No outbound asset movement

✅ **Fully supported, low risk**

***

**✅ Repay**

* Assets flow from an external chain **into** the account
* No asset withdrawal involved

✅ **Fully supported, low risk**

***

**✅ Adjust**

* Adjust operations only modify:
  * Internal parameters
  * Risk or position settings
* No asset transfers occur

✅ **Fully supported, very low risk**

***

**⚠️ Borrow**

* Borrow operations transfer assets **out of** the CrossChainLendingAccount
* The destination address can be:
  * Any external blockchain address
  * Including the **bound wallet address**

**Conclusion:**

* Borrow is **technically supported** for Passkey-based accounts
* From a safety and product perspective:
  * **Borrow is strongly recommended only after an external wallet is bound**

***

### Recommended Usage Flow

Standard Flow (Recommended)

1. Create a CrossChainLendingAccount using a Passkey
2. Immediately bind an external blockchain wallet
3. Use all supported features:
   * Supply
   * Repay
   * Adjust
   * Borrow (using the bound wallet as the recipient)

***

#### &#x20;High-Risk Flow (Not Recommended)

1. Create a Passkey-based account
2. Do **not** bind an external wallet
3. Use critical functions such as Borrow

⚠️ If the Passkey is lost, **account control cannot be recovered**

<br>
