# Example Funding Workflows

**Purpose:** Provide twelve synthetic worked patterns for common funding operations.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Use of Examples

These are operational patterns, not universal legal or provider requirements. Adapt roles, criteria, systems, permissions, and deadlines to the actual organization.

## 1. Lead Intake

**Goal:** Capture an authorized, complete lead record

**Systems involved:** Form, CRM, consent store

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Create record, normalize fields, identify blanks.

### Human-Review Triggers

Missing consent, identity conflict, sensitive field.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Intake specialist.

### Escalation Path

Consent dispute → data owner.

### Audit Fields

`consent_status, source, fields, reviewer`

### Forbidden Actions

Do not infer permission or eligibility.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 2. Document Collection

**Goal:** Collect and organize required files

**Systems involved:** Portal, Drive, CRM

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Classify, name, checklist, neutral reminders.

### Human-Review Triggers

Unreadable file, missing pages, mismatch.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Processor.

### Escalation Path

Material discrepancy → risk reviewer.

### Audit Fields

`document_id, page_count, confidence, status`

### Forbidden Actions

Do not alter or label fraud.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 3. Bank-Link Follow-Up

**Goal:** Recover a stalled bank-link step

**Systems involved:** CRM, bank-link provider, messaging

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Detect incomplete status and draft approved reminder.

### Human-Review Triggers

Consent issue, complaint, provider error.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Processor or relationship owner.

### Escalation Path

Dispute → complaint owner.

### Audit Fields

`link_status, reminder_version, consent`

### Forbidden Actions

Do not promise approval or expose data.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 4. Product Matching

**Goal:** Organize possible product categories

**Systems involved:** CRM, criteria library

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Compare verified fields to current criteria.

### Human-Review Triggers

Stale criteria, estimates, goal mismatch.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Broker or product reviewer.

### Escalation Path

Exception → authorized provider.

### Audit Fields

`criteria_version, assumptions, recommendation`

### Forbidden Actions

Do not present match as approval.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 5. Bank-Statement Review Support

**Goal:** Extract and compare cash-flow observations

**Systems involved:** Secure document store, analysis service

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Extract deposits, show calculations, flag anomalies.

### Human-Review Triggers

Low confidence, unreadable pages, material mismatch.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Processor or risk reviewer.

### Escalation Path

Serious anomaly → authorized risk owner.

### Audit Fields

`source_pages, extraction_version, flags`

### Forbidden Actions

Do not make fraud or credit decision.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 6. Deal Summary Generation

**Goal:** Create a one-page internal deal snapshot

**Systems involved:** CRM, documents, notes

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Summarize verified facts and unresolved questions.

### Human-Review Triggers

Conflicting sources, missing evidence.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Processor.

### Escalation Path

Material conflict → reviewer.

### Audit Fields

`sources, facts, assumptions, version`

### Forbidden Actions

Do not convert inference to fact.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 7. Missing-Document Reminders

**Goal:** Request specific missing items

**Systems involved:** Checklist, CRM, messaging

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Generate approved neutral message.

### Human-Review Triggers

Complaint, disputed consent, outcome language.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Processor.

### Escalation Path

Complaint → complaint owner.

### Audit Fields

`template_version, recipient, consent`

### Forbidden Actions

Do not threaten or promise.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 8. Human-Review Queue Routing

**Goal:** Assign Yellow and Red exceptions

**Systems involved:** Rules engine, CRM/Notion/Airtable

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Create review record, set deadline, notify.

### Human-Review Triggers

Reviewer unavailable, authority missing, audit failure.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Operations manager.

### Escalation Path

Red → authorized reviewer.

### Audit Fields

`trigger, reviewer, deadline, status`

### Forbidden Actions

Do not auto-approve on timeout.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 9. Terms-Change Review

**Goal:** Catch material changes before closing

**Systems involved:** Agreement store, CRM

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Compare versions and changed fields.

### Human-Review Triggers

Amount, price, frequency, or conditions changed.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Closing reviewer.

### Escalation Path

Material change → authorized decision-maker.

### Audit Fields

`document_versions, changed_fields, approval`

### Forbidden Actions

Do not execute prior approval.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 10. Complaint Escalation

**Goal:** Route applicant complaint to accountable owner

**Systems involved:** CRM, messaging, audit store

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Classify complaint, preserve context, acknowledge receipt.

### Human-Review Triggers

Harm, dispute, privacy, external action.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Complaint owner.

### Escalation Path

Severe issue → compliance or incident owner.

### Audit Fields

`message_history, owner, status, resolution`

### Forbidden Actions

Do not auto-close or argue.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 11. Closing Checklist

**Goal:** Verify final package and approvals

**Systems involved:** Document store, e-sign, CRM

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Check presence, compare values, prepare summary.

### Human-Review Triggers

Missing disclosure, identity change, unresolved condition.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Closing reviewer.

### Escalation Path

Unresolved issue → authorized owner.

### Audit Fields

`checklist, versions, approvals`

### Forbidden Actions

Do not authorize closing or disbursement.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.


## 12. Post-Launch Monitoring

**Goal:** Detect drift and repeated failures

**Systems involved:** Audit store, override log, incident system

### Stages

1. Receive or detect event.
2. Validate source, schema, consent, and record identity.
3. Perform permitted AI preparation.
4. Classify risk and evaluate triggers.
5. Continue Green work or create Yellow/Red review.
6. Record decision and outcome.

### AI-Permitted Actions

Aggregate metrics and flag trends.

### Human-Review Triggers

Override spike, error increase, model change.

### Risk Classifications

- Green: administrative preparation within approved rules
- Yellow: uncertainty, material comparison, recommendation, or draft
- Red: binding communication, final decision, unauthorized action, or incident

### Reviewer Roles

Workflow administrator or ops manager.

### Escalation Path

Incident pattern → incident owner.

### Audit Fields

`metrics, versions, samples, corrective_action`

### Forbidden Actions

Do not hide errors or self-expand scope.

### Implementation Notes

Use synthetic records for testing, separate draft from send permissions, require source evidence for Yellow and Red work, preserve original input, and configure a pause control.

## Related Knowledge Files

- `workflow-output-templates.md`
- `workflow-test-cases.md`
- `n8n-routing-patterns.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
