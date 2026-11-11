# Meridian Pay: Business Continuity Plan

> Written by Jemimah Jacobs as Section 7 of the Meridian Pay [incident response, continuity and privacy group report](../README.md). Meridian Pay is a fictional organisation.

**Key message:** each critical service has a trigger, a workaround for today and a capability still to be built, so management can see what is ready and what is not.

| | |
|---|---|
| **Status** | Proposed. Subject to management approval. |
| **Relationship** | Implements the [BIA](business-impact-analysis.md) targets. Invoked by the Incident Commander under the Incident Response Plan. Communications follow the team's crisis communication templates. Technical restoration relies on a Disaster Recovery Plan that does not yet exist. |

---

## 1. Purpose and scope

The BCP sets out how Meridian Pay keeps or restores its three critical activities during a disruption: **payment processing, settlement with partner banks and fraud monitoring.** Its aims are to protect customer funds and transaction integrity, meet the settlement cut-off, and restore services within the approved targets.

**Basis of this plan:** for each activity, the plan separates what Meridian Pay can do **today** (interim workaround) from the **capability it still has to build and test.** Where a capability is not confirmed, the plan is not treated as operational for that activity until it has been evidenced.

## 2. Activation and stand-down

The Incident Commander activates the BCP when a disruption threatens a critical activity or its recovery targets.

**Proposed triggers** (thresholds set by the business owners):
- Payment success rate or platform availability below an agreed threshold for an agreed period *(threshold to be agreed by Payment Operations)*.
- Settlement systems, bank connectivity or records unavailable at any time before the cut-off, or settlement not under way by 09:00.
- Fraud monitoring engine, data feed or alerting unavailable or unreliable beyond an agreed short period (for example, 5 minutes).
- Any SEV-1 incident affecting payments, the ledger or settlement interfaces, including ransomware.

| Step | Action | Owner |
|---|---|---|
| 1. Detect | Monitoring or a report alerts the on-call responder and Security Lead | On-call responder |
| 2. Assess | Affected systems, estimated restoration time, impact on targets | IT/Cloud Lead |
| 3. Activate | Confirm severity; authorise continuity arrangements | Incident Commander |
| 4. Operate | Run the activity-specific continuity actions in Section 3 | Activity owners |
| 5. Communicate | Approved updates to staff, customers, merchants, banks and regulators | Communications Lead |
| 6. Validate and stand down | Business owners verify safe operation, reconciliation is done and backlog cleared; IC records the decision | Incident Commander |

> ⚠️ **Out of hours:** until an on-call rota or managed monitoring exists, activation outside working hours depends on whoever notices the alert. **This is a critical gap.**

## 3. Continuity arrangements by activity

### 3.1 Payment processing

| | |
|---|---|
| **Targets** | MTD 4 hours · RTO 1 hour · RPO 0 minutes |
| **Immediate actions** | IC activates the BCP. IT/Cloud Lead decides whether primary restoration can meet the 1-hour RTO. If not, switch to a backup environment where one exists. If transaction integrity is in doubt, put the platform in degraded or read-only mode with the Fraud Lead. Prioritise wallet and critical payments. Preserve transaction logs. Notify partner banks if settlement is affected. |
| **Interim workaround (today)** | Degraded mode with tighter limits on selected transaction types; staff scripts for support; where the platform supports it, queue and replay submitted transactions after restoration under reconciliation. |
| **Capability required (not confirmed)** | Tested failover or backup payment environment; durable transaction logging; replication able to achieve zero data loss; documented recovery procedure. |
| **Owners** | IT/Cloud Lead (technical); Payment Operations Lead (business) |
| **Recovery validation** | Security, availability and transaction-integrity checks; no lost or duplicated confirmed transactions; reconciliation against logs and partner bank statements; business owner sign-off before normal operation. |

### 3.2 Settlement with partner banks

| | |
|---|---|
| **Targets** | Clock-time rule: usable by 09:00 (target) and 09:30 (latest). Illustration for an 08:00 disruption: MTD 90 minutes, RTO 60 minutes. RPO 0 minutes. |
| **Immediate actions** | Payment Operations Lead checks the time left to 09:30 and activates the contingency. Escalate to the IC. Assess what can be completed manually before 10:00. Notify each partner bank promptly if the cut-off is at risk. Log all decisions. |
| **Interim workaround (today)** | Manual reconciliation and manual submission through secure channels, prioritising settlements closest to the cut-off and highest value. Whether each bank accepts this is not confirmed. |
| **Capability required (not confirmed)** | An agreed alternative submission channel with each of the three partner banks; a written manual procedure; named bank contacts with out-of-hours escalation. |
| **Owners** | Payment Operations Lead; bank relationship owners |
| **Recovery validation** | Instructions completed accurately and acknowledged by the banks; records reconciled; missing, duplicated or delayed instructions identified and followed up. |

### 3.3 Fraud monitoring

| | |
|---|---|
| **Targets** | MTD 10 minutes · RTO 5 minutes · RPO 0 for alerts and evidence |
| **Immediate actions** | Fail over to backup monitoring where available. If effective monitoring is not restored within the MTD, apply predefined restrictions: lower transaction limits, hold high-risk transaction types, step-up verification. Route alerts to an out-of-hours responder. Review the flagged queue manually. |
| **Interim workaround (today)** | Predefined restriction rules applied in the payment platform; a named out-of-hours alert recipient (to be designated). |
| **Capability required (not confirmed)** | Automated failover, continuous alerting with a 24/7 recipient, durable evidence storage. The effectiveness of existing automated fraud controls has not been validated. |
| **Owners** | Fraud Lead; Security Lead |
| **Recovery validation** | Detection, alert processing and protective controls verified; retrospective review of transactions processed during the gap. |

## 4. Supporting services

- **Customer onboarding and KYC:** if automated verification is unavailable, operate manual review for urgent cases and delay non-urgent approvals until service is stable. Process only data needed for regulatory and contractual purposes, keeping ID numbers masked and access restricted (privacy by design).
- **Customer support:** redirect to alternate channels (email, telephone, web chat), use approved incident scripts, and escalate fraud, service and privacy complaints immediately.

## 5. People, premises and suppliers

- **People:** name a deputy for every BCP role. Identify the minimum staffing for each critical activity. Confirm secure remote working for payment operations, settlement and security staff.
- **Suppliers:** record continuity and incident contacts for the cloud provider, the three partner banks, verification vendors and fraud tooling. Request their recovery capabilities and contract commitments, and keep provider case references during incidents.
- **Records:** maintain transaction logs and backups sufficient to reconcile after an incident, and protect backups from production credentials.

## 6. Communication during disruption

The Incident Commander and Communications Lead coordinate communications using the team's crisis communication templates. Messages are accurate, approved and timed in line with the incident severity table. Recovery estimates are not presented as guaranteed unless verified.

## 7. Testing and maintenance

| Test | Proposed frequency | Evidence |
|---|---|---|
| Payment failover and restore against the 1-hour RTO | At least annually and after material change | Test report with measured recovery time |
| Settlement contingency walk-through, including a late-morning scenario | Twice a year; with each bank at least annually | Exercise record; bank acknowledgement |
| Fraud monitoring failover and out-of-hours alert test | Alert test quarterly; failover annually | Test alert log; failover timing |
| Out-of-hours escalation call test | Quarterly (with the IRP contact test) | Contact test record |
| Tabletop exercise: compromised credential leading to payment disruption | At least annually | Exercise report and tracked actions |

The BCP is reviewed at least annually, after major incidents or exercises, and after significant operational change. Weaknesses found in tests enter the corrective action register and stay open until verified.

## 8. Management recommendations

- Treat **24/7 monitoring and on-call cover as a precondition**, not a later improvement.
- **Commission a Disaster Recovery Plan**, since the BCP's technical restoration relies on one.
- **Agree alternative settlement arrangements** with all three partner banks.
- **Validate the fraud degraded-mode thresholds** with the Fraud Lead and management.
- **Formally assign recovery responsibilities** and align them with the Incident Response Plan.

---

← [Business Impact Analysis](business-impact-analysis.md) · [Back to case study](../README.md)
