# Reviewer Role Matrix

**Purpose:** Define who reviews what, who has authority, and how assignments scale from solo operators to larger organizations.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Role-Design Principles

- Assign reviewers by stage, evidence, risk, and authority.
- Separate preparation, review, decision, communication approval, and audit when practical.
- Do not assume a job title grants lending authority.
- Give every reviewer a backup and escalation route.
- Record conflicts of interest and deadlines.
- Allow authorized humans to pause the workflow.

## Reviewer Versus Decision-Maker

A reviewer verifies evidence and recommends or approves the next operational step within assigned scope. A decision-maker has authority to create or communicate a binding outcome. One person may hold both functions in a small organization, but the audit record must show which function was performed.

## Authority Levels

| Level | Description | Example |
|---:|---|---|
| 0 | Observe only | View queue and evidence |
| 1 | Administrative correction | Fix field format; request document |
| 2 | Workflow approval | Approve internal next step or template |
| 3 | Exception approval | Approve documented exception within delegation |
| 4 | Binding decision authority | Make or communicate authorized decision |
| 5 | Incident and system authority | Pause systems and approve remediation |

## Core Role Matrix

| Role | Primary responsibilities | Authority boundary | Typical checkpoint |
|---|---|---|---|
| Intake specialist | Validate intake completeness and authorized sources | May correct administrative fields; cannot decide eligibility | Data and Consent |
| Processor | Verify documents, reconcile fields, request information | May confirm completeness; cannot issue binding credit decisions | Document Quality |
| Funding broker | Explain process, organize options, route and follow up | May recommend within approved scope; cannot impersonate creditor | Eligibility and Product Fit |
| Funding agency owner | Own internal controls, staffing, templates, and escalation | May approve internal operations; decision authority depends on actual role | All internal checkpoints |
| Operations manager | Manage queues, SLAs, overrides, and process quality | May pause workflows and assign reviewers | Monitoring and Feedback |
| Compliance reviewer | Review policy-sensitive messages and controls | Authority defined by organization; not automatically decision-maker | Communications and Disclosures |
| Authorized creditor or lender representative | Communicate authorized creditor decisions | May issue decisions within delegated authority | Decision Authority |
| Underwriter | Evaluate risk under applicable policy | May recommend or decide according to assigned authority | Risk and Decision Authority |
| Data or security owner | Control sensitive data, access, incidents, and containment | May quarantine systems and records | Data and Consent |
| Workflow administrator | Configure rules, versions, integrations, and disable controls | May deploy approved changes; cannot self-approve material policy changes | Monitoring and Feedback |
| Incident owner | Coordinate containment, evidence, investigation, and remediation | May pause affected systems and escalate | Monitoring and Feedback |
| Executive escalation owner | Resolve severe operational conflicts and resource decisions | Authority limited to actual organizational role | Severe incidents |

## Segregation of Duties

For Yellow and Red work, distinguish the AI system that generates output, the person who reviews evidence, the person authorized to decide, the person approving external communication, and the person auditing performance.

When staffing is limited, compensate with stronger logs, second-look sampling, conflict rules, and periodic independent review.

## Scalable Assignment Models

### Solo Operator

- Label the role performed for each action.
- Keep Red actions paused.
- Route creditor decisions to the authorized provider.
- Use external or periodic independent review where practical.

### Small Team

Assign intake/document review, relationship owner, operations manager, authorized decision owner, and backup reviewer.

### Larger Organization

Use specialized queues, delegated authority, segregation of duties, independent monitoring, and incident ownership.

## Assignment Rule Template

```yaml
review_assignment:
  primary_role: "Processor"
  backup_role: "Operations Manager"
  escalation_role: "Authorized Creditor Representative"
  deadline: "same_business_day"
  conflict_rule: "Reassign when reviewer has a direct financial or complaint-related conflict"
```

## Conflict-of-Interest Handling

Reassign when compensation may bias product selection, the reviewer originated the disputed action, the reviewer is the subject of a complaint, the reviewer lacks authority, or the reviewer cannot independently evaluate evidence.

## Workload and Queue Assignment

Use stage specialization, risk-zone priority, earliest deadline, reviewer capacity, backup rotation, conflict exclusions, and escalation aging.

## Checkpoint Assignment Matrix

| Checkpoint | Primary reviewer | Backup | Escalation |
|---|---|---|---|
| Data and Consent | Intake specialist | Data owner | Incident owner |
| Document Quality | Processor | Operations manager | Risk reviewer |
| Eligibility and Product Fit | Broker or product reviewer | Operations manager | Authorized provider |
| Risk and Anomaly Review | Risk reviewer or underwriter | Operations manager | Incident/compliance owner |
| Decision Authority | Authorized decision-maker | Delegated backup | Policy owner |
| Communications and Disclosures | Message owner | Compliance reviewer | Authorized communicator |
| Final Terms and Closing | Closing reviewer | Operations manager | Authorized creditor representative |
| Monitoring, Overrides, and Feedback | Workflow administrator | Operations manager | Incident owner |

## Example RACI

| Activity | AI | Processor | Broker | Authorized decision-maker | Ops manager |
|---|---|---|---|---|---|
| Extract document fields | R | A | I | I | C |
| Resolve discrepancy | C | R/A | C | I | C |
| Recommend product category | C | C | R | A when authority required | I |
| Communicate approval | I | I | C | R/A | I |
| Review override trends | C | C | C | I | R/A |

R = Responsible, A = Accountable, C = Consulted, I = Informed.

## Common Role Failures

- Reviewer cannot stop the workflow
- Broker is treated as lender
- Decision authority is inferred from title
- No backup reviewer exists
- Queue deadline is missing
- Conflict of interest is ignored
- Workflow administrator self-approves material changes
- External message is approved by someone without authority

## Related Knowledge Files

- `escalation-paths.md`
- `audit-log-schema.md`
- `safe-language-and-disclaimers.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
