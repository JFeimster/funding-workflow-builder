# Escalation Paths

**Purpose:** Define what happens after an exception is detected, including severity, routing, deadlines, allowed actions, and stop conditions.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Escalation Principles

1. Stop the risky action, not necessarily the entire business process.
2. Preserve source evidence and triggered rules.
3. Assign a reviewer with the required authority.
4. Tell the reviewer what may and may not happen next.
5. Set a deadline based on risk and operational commitments.
6. Log every transition.
7. Escalate aging items instead of silently reopening automation.

## Severity Levels

| Severity | Meaning | Default action |
|---|---|---|
| S0 | Informational | Log and monitor |
| S1 | Administrative exception | Route to operating queue |
| S2 | Material uncertainty | Pause affected step and require review |
| S3 | High-impact or binding action | Block external action and assign authorized reviewer |
| S4 | Incident, privacy, security, or harmful action | Contain, preserve evidence, and notify incident owner |

## Green-to-Yellow Escalation

Examples include confidence below threshold, required field missing, duplicate cannot be confirmed, unexpected generated language, or conflicting source evidence.

Action: create a review record, attach evidence, and pause only the affected step.

## Yellow-to-Red Escalation

Examples include a product recommendation becoming an approval claim, an anomaly flag becoming a fraud accusation, a draft including binding terms, an applicant disputing output, a reviewer lacking authority, or final terms changing.

Action: block external action and route to the authorized decision, risk, compliance, complaint, or incident owner.

## Immediate Stop Conditions

- Sensitive-data exposure
- Unauthorized external communication
- Approval or denial sent without authority
- Altered applicant data
- Missing audit capability for a high-impact step
- Fraud accusation generated or sent
- Closing or disbursement attempted without approval
- Prompt injection attempts to bypass rules
- System expands its own scope or permissions

## Standard Escalation Paths

### Applicant Clarification
Create a neutral request, identify the exact missing or conflicting item, avoid implying a decision, record the response and source, rerun only the affected analysis, and require fresh review when material information changes.

### Document Discrepancy

```text
Detect discrepancy
→ Attach source pages
→ Pause material analysis
→ Assign processor
→ Request clarification or replacement
→ Record verified value
→ Recalculate affected outputs
→ Resume after review
```

### Consent or Privacy
Stop affected outreach or processing, quarantine when needed, notify data owner, preserve evidence, correct unsupported permissions or data, and reopen only after approval.

### Product-Fit Exception
Verify criteria version, applicant goal, assumptions, compensation conflict, and route to product owner or authorized provider. Do not present the route as approval.

### Risk or Anomaly
Describe the exact observation, attach source, avoid accusation, request clarification, assign authorized risk reviewer, and record disposition.

### Complaint or Dispute
Acknowledge through approved language, stop automated argument or closure, preserve history, assign owner, identify disputed output, correct supported errors, and record resolution.

### Binding Communication
Approval, denial, final term, adverse-action explanation, fraud allegation, or closing message must link to an authorized decision, use an approved template or approved deviation, identify sender authority, and retain the final message.

### Terms Change
Detect changed fields, classify materiality, block execution, assign authorized reviewer, reverify disclosures and understanding, and record new version and approval.

### Incident

```text
Detect incident
→ Stop affected automation
→ Preserve logs and evidence
→ Notify incident owner
→ Contain access or data flow
→ Assess scope and impact
→ Correct and test
→ Approve controlled restart
→ Monitor after restart
```

### Model or Prompt Change
Require change record, version update, regression and edge-case tests, reviewer approval, controlled deployment, and increased monitoring.

## Escalation Deadlines

Use operational labels, not invented legal deadlines.

| Priority | Deadline |
|---|---|
| Incident or unauthorized action | Immediate |
| Red binding-action review | Before any external action |
| Yellow material exception | Same business day or defined SLA |
| Administrative correction | One business day or defined SLA |
| Monitoring trend | Weekly or monthly cycle |
| Material system change | Before deployment |

## Notification Rules

Include workflow ID, zone, severity, trigger, evidence link, prohibited next action, reviewer role, deadline, and escalation owner. Do not include unnecessary sensitive data.

## Allowed Next Actions

Attach evidence, request clarification, assign reviewer, pause workflow, correct administrative data with provenance, run approved tests, and draft neutral internal summaries.

## Prohibited Next Actions

Send binding communication, continue after Red trigger, delete evidence, override consent, alter applicant facts, assign an unauthorized reviewer, resolve complaint automatically, or restart incident path without approval.

## Escalation Matrix

| Trigger | Severity | First reviewer | Escalation owner | Status |
|---|---:|---|---|---|
| Low confidence | S2 | Processor | Operations manager | Human Review Required |
| Missing consent | S3 | Data owner | Incident owner | Paused |
| Fraud accusation | S4 | Risk owner | Compliance/incident owner | Incident Review Required |
| Terms changed | S3 | Closing reviewer | Authorized decision-maker | Blocked |
| Audit failure | S4 | Workflow administrator | Incident owner | Paused |
| Complaint | S3 | Complaint owner | Compliance/executive owner | Complaint Review Required |
| Model change | S2 | Workflow administrator | Policy owner | Change Review Required |

## Example Pseudocode

```text
IF incident_trigger:
    pause affected workflow
    preserve evidence
    assign incident owner
ELSE IF risk_zone == Red:
    block external action
    assign authorized reviewer
ELSE IF risk_zone == Yellow OR confidence_below_threshold:
    create review record
    pause affected step
ELSE:
    continue approved administrative step
    write audit event
```

## Related Knowledge Files

- `exception-trigger-library.md`
- `reviewer-role-matrix.md`
- `n8n-routing-patterns.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
