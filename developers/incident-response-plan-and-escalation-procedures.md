---
description: 'For: Rhea Lending Smart Contract System'
---

# Incident Response Plan and Escalation Procedures

Last Updated: 2025-12-01

### 1. Purpose

This document defines the i**ncident response and escalation process** for the Rhea lending protocol.\
Its goal is to ensure that any security or operational incidents (e.g., smart-contract vulnerabilities, abnormal fund movement, or oracle failures) are detected, triaged, and mitigated promptly and transparently.

### 2. Incident Detection

Incidents can be detected through the following channels:

* Continuous on-chain monitoring and anomaly detection (e.g., large withdrawals, liquidity imbalance).
* Internal alert systems and automated bots watching protocol metrics.
* External disclosures from white-hat researchers or the community.
* Third-party security partners or exchanges (e.g., Binance).



Once detected, the incident is immediately categorized by severity.

| Severity | Description                          | Initial Response Time |
| -------- | ------------------------------------ | --------------------- |
| Critical | Potential or confirmed loss of funds | < 15 minutes          |
| High     | Protocol unavailable, pause required | < 1 hour              |
| Medium   | Degraded performance or oracle issue | 4 hours               |
| Low      | Non-critical bug or UX issue         | 24 hours              |



### 3. Immediate Response Actions

#### 3.1 Smart Contract Controls

The protocol includes an emergency pause() function, callable only by the multi-signature Admin wallet.

* Purpose: Halt all lending/borrowing/minting functions to prevent further risk propagation.
* Implementation:
* pause().
* When paused, core functions revert immediately.
* State remains immutable; no funds are moved automatically.



#### 3.2 Admin Access

* The Admin address is a multi-signature wallet.
* No single individual has unilateral control.
* All administrative actions (pause/unpause, parameter update) require multi-sig approval.<br>

#### 3.3 Escalation Steps

1. Incident detected → On-call security lead notified.
2. Severity classified (Critical / High / Medium / Low).
3. If Critical:
   1. Initiate multi-sig proposal to call pause() immediately.
   2. Notify all Admin signers (via secure communication channel, e.g., Signal or encrypted email).
   3. Execute pause() once quorum reached.
4.  Post-pause verification:

    1. Verify state consistency and that no pending operations remain.
    2. Snapshot relevant contracts and balances.



#### 4. Communication and Coordination

**4.1 Internal Coordination**

* Incident Commander (IC): Zero
* Technical Leads: Marco
* Multi-sig Signers: Zero, Marco, Joe, Mency, Aescobar<br>

**4.2 External Coordination**

* Notify key stakeholders (e.g., Binance, auditors, oracles, liquidity partners).
* Publish transparent updates through official channels (Twitter, Discord, or blog) once the incident is contained.
* Engage third-party audit partners if smart-contract patch or redeployment is required.



#### 5. Recovery and Post-Mortem

1. Assess the root cause and patch the vulnerability (with internal & external review).
2. Unpause contracts after full verification and sign-off by all Admin signers.
3. Publish a post-incident report summarizing:
   1. Timeline of events
   2. Impact analysis
   3. Mitigation and permanent fixes
   4. Lessons learned<br>

#### 6. Access Control and Documentation

* All privileged roles and their actions are stored in on-chain governance contracts.
* Access keys are secured by hardware wallets and multi-sig policies.
* All incident communications are logged and archived in secure repositories (Notion + GitHub private repo).
* The team performs at least one annual incident-response drill to test the procedure.



#### 7. Summary

| Component       | Control                                                | Description                            |
| --------------- | ------------------------------------------------------ | -------------------------------------- |
| Emergency Pause | pause() callable by multi-sig                          | Immediate freeze of critical functions |
| Admin Model     | Multi-signature                                        | Prevents single-key control            |
| Response Time   | < 15 minutes for Critical                              | 24/7 on-call rotation                  |
| Escalation      | Security Lead → Multi-sig Admin → Public Communication | Documented and auditable               |
| Transparency    | All admin actions on-chain                             | Post-incident report published         |

#### Statement

The Rhea protocol maintains a documented, tested, and verifiable Incident Response Plan.\
The plan ensures that in any critical event, the team can promptly pause protocol activity,\
protect user assets, and coordinate transparent recovery through the multi-signature admin structure.

<br>
