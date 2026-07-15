# n8n Human-Review Routing Patterns

**Purpose:** Teach the GPT how to draft safe, implementation-ready n8n routing specifications without claiming deployment.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Architecture

A guardrailed n8n workflow separates trigger, input validation, data minimization, AI processing, risk classification, confidence evaluation, exception detection, human-review routing, wait state, human callback, decision branch, audit logging, notification, failure handling, and incident handling.

## Trigger Patterns

- Webhook for new intake
- CRM record created or updated
- Document uploaded
- Scheduled monitoring run
- Human decision callback
- Provider status update
- Complaint or dispute event

Validate authenticity, required fields, source, and idempotency before processing.

## Validation Node

Check schema, required fields, approved source, consent, duplicate event ID, file type and size, sensitive fields, and workflow version. Invalid input routes to review or safe rejection before AI processing.

## AI-Processing Node

Permitted tasks include classification, extraction, summarization, drafting, comparison, and question generation. Return structured output, source references, confidence when meaningful, and unresolved questions.

## Risk-Classification Output

```json
{
  "risk_zone": "Yellow",
  "reason": "Material mismatch between reported and extracted values",
  "review_required": true,
  "trigger_ids": ["DOC-MATERIAL-MISMATCH"]
}
```

## Confidence Threshold

Use a configured threshold from a policy source. Do not hard-code an invented universal threshold. Record the threshold version and measured confidence.

## Human Review Queue

Create one record with workflow ID, trigger, zone, evidence, reviewer role, deadline, prohibited next action, and callback or review ID. Do not include unnecessary sensitive data in notifications.

## Wait States

- Wait for authenticated webhook callback
- Poll approved review database
- Resume on CRM status change
- Time out into escalation queue

Never auto-approve on timeout.

## Human Decision Callback

Expected decisions: Approved, Corrected, Returned for Information, Escalated, Rejected, Paused, or Incident Review. Validate reviewer identity and authority.

## Decision Branch

- Approved → continue only approved next step
- Corrected → update with provenance and rerun affected checks
- Returned → send approved neutral request
- Escalated → assign next reviewer
- Rejected → stop operational step; do not create unauthorized credit denial
- Paused → freeze affected path
- Incident → trigger incident process

## Failure and Retry Handling

Retry transient technical failures with bounded attempts. Do not retry binding external actions blindly. Use idempotency keys, route repeated failures to review, log each attempt, and stop on schema or authorization errors.

## Disabled-Draft Principle

When an authenticated Action creates an n8n workflow, create it disabled by default. Review credentials, permissions, test cases, and external endpoints before activation.

## Credential Safety

Never embed credentials in workflow JSON. Use n8n credential records or secure environment configuration, least privilege, and separate test/production credentials.

## Sample Node Sequence

```text
Webhook Trigger
→ Verify Signature
→ Validate Schema
→ Minimize Data
→ AI Extraction
→ Risk Classifier
→ Confidence Check
→ Exception Rules
→ Green: Audit + Continue
→ Yellow: Create Review + Wait
→ Red: Block + Assign Authorized Reviewer
→ Decision Callback
→ Audit Decision
→ Approved Next Step
```

## Pseudocode

```text
IF audit_service_unavailable:
    pause_workflow()
    create_incident("AUDIT-FAILURE")
ELSE IF incident_trigger:
    pause_workflow()
    notify_incident_owner()
ELSE IF risk_zone == "Red":
    block_external_action()
    create_review(required_authority="authorized")
ELSE IF risk_zone == "Yellow" OR confidence < configured_threshold:
    create_review(required_authority="stage_reviewer")
    wait_for_human_decision()
ELSE:
    continue_approved_administrative_step()
    write_audit_event()
```

## Example Webhook Payload

```json
{
  "event_id": "EVT-2026-1004",
  "workflow_id": "WF-2026-041",
  "event_type": "document_uploaded",
  "source": "approved-client-portal",
  "applicant_or_lead_id": "LEAD-882",
  "document_reference": "document://DOC-104",
  "consent_status": "verified",
  "workflow_version": "1.0"
}
```

## Example Workflow Specification

```yaml
workflow:
  name: "Human Review Checkpoint Router"
  status: "disabled_draft"
  version: "1.0"
  nodes:
    - id: "trigger"
      type: "webhook"
      purpose: "Receive approved event"
    - id: "validate"
      type: "validation"
      purpose: "Validate source, schema, consent, and event ID"
    - id: "analyze"
      type: "ai_processing"
      purpose: "Perform permitted extraction or summarization"
    - id: "classify"
      type: "rules"
      purpose: "Assign risk zone and triggers"
    - id: "review_router"
      type: "conditional"
      purpose: "Route Yellow and Red work"
    - id: "audit"
      type: "database"
      purpose: "Write versioned audit events"
  activation_requirements:
    - "credentials reviewed"
    - "test cases passed"
    - "review callback authenticated"
    - "pause control verified"
```

## Testing Checklist

- [ ] Duplicate events are idempotent
- [ ] Missing consent stops outreach
- [ ] Low confidence creates review
- [ ] Red action cannot send externally
- [ ] Timeout escalates, not approves
- [ ] Audit failure pauses
- [ ] Prompt injection fails safely
- [ ] Callback validates identity
- [ ] Draft remains disabled

## Related Knowledge Files

- `workflow-test-cases.md`
- `action-endpoints.md`
- `audit-log-schema.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
