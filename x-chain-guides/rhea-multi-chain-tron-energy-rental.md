# RHEA Multi-Chain: TRON Energy Rental

This guide explains the implementation of Energy Rental on the TRON network using the TRXX integration. By utilizing this service, users can significantly reduce TRX burn fees during TRC20 transactions (e.g., USDT).

It covers:

* The TRON resource model
* How energy rental works
* System architecture
* Order flow
* Security and reliability
* External integration capabilities

### Notes

This guide focuses on mechanism, workflow, interfaces, and operational considerations.

It does not include detailed code implementation.<br>

***

## TRON Energy Rental

This page explains how TRON Energy rental works and how to integrate with TRXX.

On TRON, TRC20 transfers such as USDT are contract calls, so they mainly consume Energy. If a wallet does not have enough Energy, the fee is paid in TRX instead. Energy rental is designed to reduce that TRX cost before the user submits the transfer.

### Overview

TRON transaction execution depends on two resources:

* Bandwidth: Used for normal transfers and transaction data
* Energy: Used for smart contract execution

Because TRC20 transfers are contract calls, they primarily consume Energy.

#### Why TRX is Burned

When an address lacks sufficient Energy to cover a contract execution, the network burns TRX to pay for the resource. Typically, a USDT transfer may consume 7–14 TRX depending on network conditions if no Energy is available.

***

### Core Mechanism: Resource Delegation

Energy rental is not a token transfer.

Instead, a provider freezes or stakes TRX to generate Energy, then delegates that Energy to a user address for a limited time.

The flow is:

1. TRXX freezes TRX in its resource account
2. Energy is generated from that staked balance
3. TRXX delegates that Energy to the user address
4. The user consumes that Energy when making a TRC20 transfer
5. TRXX later reclaims the resource when the RENTAL ENDS or is no longer needed

This is the core mechanism behind TRON Energy rental.

### Benefit

Once Energy has been delegated to the user address, the wallet can use that Energy first when sending a TRC20 transfer.

If the delegated Energy is enough, the TRX burn fee is greatly reduced and may be close to zero.

Keep in mind:

* if Energy is not sufficient, some TRX may still be charged
* Bandwidth may still be required
* if Bandwidth is also insufficient, that cost may also be converted into TRX

This is why delegated Energy can directly reduce user transaction costs.

### Architecture

A typical TRON Energy rental integration includes both off-chain and on-chain components.

#### Frontend

The frontend is responsible for:

* Initiating the rental request
* Showing price quotes
* Displaying order status

#### RHEA Backend

Our backend acts as the order coordinator. It is responsible for:

* Creating rental orders
* Signing and authenticating requests
* Syncing order status
* Handling idempotency and recovery logic

#### TRXX

TRXX is responsible for the on-chain execution layer. It handles:

* Maintaining the resource pool account
* Delegating Energy on-chain
* Reclaiming Energy on-chain
* Returning order information
* Sending status callbacks

#### Current architecture flow:

<br>

### Core Processes

1. #### Pre-Quote

Before creating an order, the system should determine:

* The rental period, such as 1H, 1D, 3D, or 30D (Defaults will be 1H)
* The required Energy amount, such as 65,000 Energy

System then requests pricing from TRXX.

The quote is typically used to:

* Show the cost to the user before ordering
* Help the frontend decide whether the rental is worth using\
  <br>

2. #### Create Order

When creating an order, the main inputs are:

* receiveAddress: The TRON address that will receive delegated Energy
* period: The rental duration
* energyAmount: The amount of Energy requested

After receiving the order, TRXX will usually:

* Select available resources from its pool
* Delegate Energy to the user address on-chain
* Return an order identifier such as serial
* Return the payable amount\
  <br>

3. #### Status Sync

Energy delegation is not always instant, so status synchronization is important.

A reliable integration should use three complementary sync methods:

* #### Webhook (Push)

TRXX pushes a callback when the order succeeds or fails.

This is the fastest update path, but it should not be the only one.

* #### Polling

Rhea backend should periodically check pending orders as a fallback.

This prevents missed updates if a webhook is delayed or lost.

* #### Lazy Refresh

When the user opens or refreshes an order that is still pending, the system can fetch the latest status from TRXX and update it immediately.

This prevents the UI from staying stuck in a stale pending state.

#### Common Status

Typical order states include:

* pending: Delegation is in progress
* delegated: Delegation succeeded and Energy is available
* failed:  Delegation failed
* reclaimed:  Energy has been reclaimed, either manually or after expiry

This three-way sync model improves consistency and reduces missed orders.

4. #### Consume Energy&#x20;

Once an order reaches delegated, the user can submit a TRC20 transfer on TRON.

At that point:

* The wallet consumes delegated Energy first
* The TRX burn fee should drop significantly

Please note:

If there is insufficient Energy, TRX fees may still apply.

A small amount of bandwidth may still be required (if no bandwidth is available, this will be converted to TRX).

5. #### Reclaim

After the user finishes the transfer and no longer needs the delegated Energy, the rental can be reclaimed.

The system calls the reclaim interface, and TRXX revokes the delegation or reclaims the resource on-chain.

The order then moves into reclaimed.

This helps:

* Reduce unnecessary resource usage
* Improve the turnover efficiency of the resource pool

### Security

Because the flow involves billing, resource allocation, and asynchronous callbacks, authentication and anti-tampering protections are required.

#### Request Auth

Requests from RHEA backend to TRXX should be protected using API credentials such as an API key and secret.

Request signing should help ensure:

* The request has not been modified
* Replay attacks are prevented through timestamp and time-window checks

#### Webhook Auth

Webhook callbacks from TRXX should also be verified with signatures.

The system should also support idempotent handling so that the same event is not processed multiple times.

#### Client Auth

If the RHEA system exposes public APIs to the frontend, additional client-side authentication or token protection is recommended.

### Reliability

Because on-chain delegation is asynchronous, a robust integration should not rely on a single update path.

The recommended approach is:

* Webhook for speed
* Polling for recovery
* Refresh on query for UI accuracy

The goal is to ensure:

* Consistent status
* Idempotent retries
* Recoverable failures

### Conditions and Notes

There are several practical considerations during integration.

#### Energy Size

Energy usage is estimated, not fixed.

USDT transfer cost may vary depending on:

* Contract behavior
* Account state
* Whether this is the first interaction
* Current network parameters

A practical approach is to choose a slightly higher Energy amount than the average requirement. For example, 65k Energy is commonly used as a reference value.

#### Activation

In some cases, additional resource usage may happen because of address state or execution path.

In practice, some integrations may use a small TRX transfer to activate an address or ensure enough Bandwidth, depending on the business flow.

#### Concurrency

The same address may create multiple orders in a short time.

The system should clearly define:

* Whether Energy can stack
* Whether one order overrides another
* Whether only the largest allocation should apply

Rate limiting or order merging may also be useful.

#### Failure

Delegation can fail for several reasons, such as:

* Insufficient pool resources
* Network congestion
* Risk-control policies

A clear failure-handling strategy, such as:

* Retry
* Refund
* Switching to another resource pool
* Prompting the user to try another period or Energy level

### API

At a high level, the integration usually only needs the following external capabilities:

1. GetPrice(period, energyAmount)
2. CreateOrder(receiveAddress, period, energyAmount)
3. GetOrder(orderId / serial)
4. ReclaimOrder(orderId / serial) (optional)
5. Webhook: OrderStatusChanged(serial, status, txid...)

These interfaces are enough to support a standard rental flow.

## Flow

A typical integration flow looks like this:

1. User selects a rental period and Energy amount
2. Frontend requests a price quote
3. Backend creates an order with TRXX
4. TRXX delegates Energy on-chain
5. Backend syncs status through webhook, polling, and refresh
6. User sends a TRC20 transfer using the delegated Energy
7. Backend optionally reclaims the order after usage

This matches the document’s intended integration pattern and operating model.

<figure><img src="../.gitbook/assets/unknown (1).png" alt=""><figcaption></figcaption></figure>

## Summary

TRON Energy rental is fundamentally a resource delegation model.

TRXX provides the resource pool and the on-chain execution layer. RHEA system is mainly responsible for order orchestration, authentication, status synchronization, and user-facing integration.

By delegating Energy before the user submits a TRC20 transfer, the system can significantly reduce the TRX burned as transaction fees.

<br>
