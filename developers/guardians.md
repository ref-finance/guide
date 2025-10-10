---
description: Protocol's pause control procedure
---

# Guardians

## Problem

When issues arise (performance issue, critical bug, malicious attempts, etc.), it is important that RHEA Finance has a plan to mitigate (i) the risks of contagion and (ii) the impact of such an event (including potential loss of funds).

Often, turning off the frontend/user interface is not good enough because it does not prevent bots from operating, for example.

## Solution

The Guardians can be defined as specific NEAR addresses that have the privilege/ability to pause the main contract (v2.ref-finance.near). They are the key participants of a fail-safe procedure, being able to respond in the event of a specific type of failure.

Event/situation that can be defined as, but not limited to:

* Ongoing attack and/or exploit
* Critical bug identified in production (not yet exploited)
* Release/Deployment causing a potential security vulnerability

## **Procedure**

### **Prerequisite**

The Guardians MUST know how to handle the NEAR Command-Line Interface (CLI).

### **Process**

Process Owner: The Guardian

1. Identify a situation that justifies pausing the contract (v2.ref-finance.near)
2. Double check the facts/situation
3. Inform the other Guardians
4. Pause the contract (v2.ref-finance.near)
5. Inform the Team and the DAO/owner of the contract (ref-finance.sputnik-dao.near)&#x20;
6. Inform the Community
7. Identify the steps to reactivate the contract (v2.ref-finance.near)

{% hint style="info" %}
Only the owner of the contract can reactivate it (v2.ref-finance.near)
{% endhint %}

Finally, anyone can see the list of the Guardians by calling the following view method via CLI:

```
near view v2.ref-finance.near metadata
```

More info: [https://github.com/ref-finance/ref-contracts/pull/50](https://github.com/ref-finance/ref-contracts/pull/50)
