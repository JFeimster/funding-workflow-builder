# Eight Human Review Checkpoints

**Purpose:** Define the eight required control points for AI-assisted funding workflows.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## How to Use the Checkpoints

Apply every checkpoint to the workflow, even when a stage appears absent. An absent checkpoint may be a valid scope decision or a blind spot. Record which checkpoints apply, which do not, and why.

## 1. Data and Consent

### Objective
Ensure information is collected, used, stored, and communicated through authorized channels.

### Typical Inputs
Forms, consent records, source metadata, identity fields, communication preferences.

### AI-Permitted Actions
Capture fields; normalize data; detect duplicates; route records.

### Human-Review Triggers
Missing or disputed consent; unverified source; conflicting identity; sensitive data in open fields.

### Required Evidence
Consent record, source system, timestamps, and field provenance.

### Reviewer Role
Intake specialist or data owner.

### Reviewer Authority
Confirm permitted use and channel; quarantine unsupported data.

### Escalation Path
Pause outreach and route privacy issues.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Override consent; infer permission; export to unapproved systems.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 2. Document Quality

### Objective
Confirm documents are complete, readable, consistent, and tied to the correct record.

### Typical Inputs
Uploaded files, extracted fields, page counts, hashes, source metadata.

### AI-Permitted Actions
Classify; extract; detect missing pages; compare names and dates.

### Human-Review Triggers
Low confidence; unreadable pages; mismatched names; inconsistent totals; possible alteration.

### Required Evidence
Original file, page references, confidence, comparison output.

### Reviewer Role
Processor.

### Reviewer Authority
Verify evidence; request corrected files; escalate material discrepancies.

### Escalation Path
Pause downstream analysis.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Declare fraud; alter files; silently fill values.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 3. Eligibility and Product Fit

### Objective
Use current criteria to organize possible paths without presenting an unauthorized final decision.

### Typical Inputs
Applicant profile, use of funds, verified criteria, product definitions.

### AI-Permitted Actions
Compare criteria; identify missing requirements; prepare questions.

### Human-Review Triggers
Stale criteria; estimated values; conflicting goals; policy boundary; incentive conflict.

### Required Evidence
Criteria version, source data, assumptions, comparison table.

### Reviewer Role
Broker or product reviewer.

### Reviewer Authority
Confirm criteria and appropriate routing.

### Escalation Path
Escalate exceptions to provider or authorized reviewer.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Invent criteria; guarantee eligibility.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 4. Risk and Anomaly Review

### Objective
Surface patterns for investigation without converting flags into accusations.

### Typical Inputs
Application data, documents, transaction summaries, duplicate records.

### AI-Permitted Actions
Detect mismatches; flag patterns; attach evidence.

### Human-Review Triggers
Potential manipulation; unexplained swings; disputed flag; weak evidence.

### Required Evidence
Exact observation, source, rule, confidence, comparison.

### Reviewer Role
Risk reviewer or underwriter.

### Reviewer Authority
Assess evidence and decide escalation.

### Escalation Path
Route serious issues to authorized owner.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Declare fraud; blacklist; send accusation.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 5. Decision Authority

### Objective
Ensure only assigned people or entities make and communicate authorized high-impact decisions.

### Typical Inputs
Decision memo, criteria, evidence, exceptions, assignments.

### AI-Permitted Actions
Prepare summaries; calculate; organize criteria; list questions.

### Human-Review Triggers
Approval, denial, pricing, eligibility, exception, unresolved conflict.

### Required Evidence
Decision factors, policy version, evidence, reviewer authority.

### Reviewer Role
Authorized creditor representative or underwriter.

### Reviewer Authority
Make or communicate authorized decision.

### Escalation Path
Stop when reviewer lacks authority.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Impersonate lender; make final decision without authority.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 6. Communications and Disclosures

### Objective
Prevent inaccurate, unauthorized, or sensitive messages from leaving the workflow.

### Typical Inputs
Drafts, templates, recipient, consent, decision status.

### AI-Permitted Actions
Draft neutral reminders and process updates.

### Human-Review Triggers
Approval or denial language; terms; fraud; complaint; sensitive data.

### Required Evidence
Template, decision source, consent, approval.

### Reviewer Role
Message owner or authorized communicator.

### Reviewer Authority
Approve, revise, or block communication.

### Escalation Path
Route complaints and high-impact messages.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Promise outcomes; expose sensitive data.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 7. Final Terms and Closing

### Objective
Verify final values, documents, conditions, authority, and changes before execution.

### Typical Inputs
Agreements, disclosures, signatures, checklist, change history.

### AI-Permitted Actions
Compare versions; highlight changes; verify checklist presence.

### Human-Review Triggers
Amount, pricing, frequency, identity, or conditions changed.

### Required Evidence
Versioned documents, change log, approved terms.

### Reviewer Role
Authorized closing reviewer.

### Reviewer Authority
Verify package and approve where authorized.

### Escalation Path
Block execution until exceptions resolve.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Modify terms; authorize closing or funds movement.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## 8. Monitoring, Overrides, and Feedback

### Objective
Detect drift, repeated errors, control failures, and changes after launch.

### Typical Inputs
Audit logs, overrides, complaints, incidents, versions.

### AI-Permitted Actions
Aggregate metrics; detect trends; generate reports.

### Human-Review Triggers
Rising errors; repeated overrides; complaint clusters; model or vendor change.

### Required Evidence
Metrics, samples, change logs, incident reports.

### Reviewer Role
Workflow administrator, operations manager, or incident owner.

### Reviewer Authority
Pause, investigate, remediate, and reapprove.

### Escalation Path
Escalate material incidents.

### Audit Fields
`workflow_id, stage, risk_zone, trigger, source_evidence, reviewer, authority, decision, version, timestamp`

### Forbidden Actions
Hide errors; delete logs; self-expand scope.

### Example Scenario
Use a synthetic record that triggers the checkpoint, attach source evidence, and record the reviewer’s decision.

### Failure Mode
The workflow continues despite uncertainty or missing authority.

### Recommended Control
Use a testable trigger, a named reviewer, a deadline, and a blocked next action.

## Checkpoint Summary Matrix

| # | Checkpoint | Typical reviewer | Default escalation |
|---:|---|---|---|
| 1 | Data and Consent | Intake specialist or data owner. | Pause outreach and route privacy issues. |
| 2 | Document Quality | Processor. | Pause downstream analysis. |
| 3 | Eligibility and Product Fit | Broker or product reviewer. | Escalate exceptions to provider or authorized reviewer. |
| 4 | Risk and Anomaly Review | Risk reviewer or underwriter. | Route serious issues to authorized owner. |
| 5 | Decision Authority | Authorized creditor representative or underwriter. | Stop when reviewer lacks authority. |
| 6 | Communications and Disclosures | Message owner or authorized communicator. | Route complaints and high-impact messages. |
| 7 | Final Terms and Closing | Authorized closing reviewer. | Block execution until exceptions resolve. |
| 8 | Monitoring, Overrides, and Feedback | Workflow administrator, operations manager, or incident owner. | Escalate material incidents. |

## Related Knowledge Files

- `exception-trigger-library.md`
- `reviewer-role-matrix.md`
- `audit-log-schema.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
