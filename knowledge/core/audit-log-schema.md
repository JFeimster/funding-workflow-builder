# Audit Log Schema

**Purpose:** Define the minimum evidence and metadata required to reconstruct AI-assisted workflow activity.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Audit-Log Purpose

The log should answer what happened, what evidence was used, which rule fired, what AI recommended, who reviewed it, what authority the reviewer held, what decision was made, whether an override occurred, and which policy/model versions were active.

## Field Dictionary

| Field | Type | Required | Definition |
|---|---|---|---|
| workflow_id | string | Yes | Unique workflow instance |
| applicant_or_lead_id | string | Yes | Internal reference; avoid raw sensitive identifiers |
| workflow_stage | enum | Yes | Approved stage or checkpoint |
| event_type | enum | Yes | analysis, trigger, review, decision, communication, incident, change |
| ai_action | string | Yes | What the system did |
| ai_recommendation | string | Conditional | Recommendation or draft |
| risk_zone | enum | Yes | Green, Yellow, or Red |
| confidence_score | number/null | Conditional | Tested score when applicable |
| review_trigger | array | Conditional | Triggered rule IDs |
| source_evidence | array | Yes for Yellow/Red | Document, page, field, or record references |
| assigned_reviewer | string/null | Required for review | User or role |
| reviewer_authority | string/null | Required for Red | Delegated authority |
| human_decision | enum/null | After review | approved, corrected, escalated, rejected, paused |
| override_reason | string/null | For override | Evidence-based reason |
| communication_approval | object/null | For controlled messages | Approver, template, timestamp |
| policy_version | string | Yes | Rule version |
| model_or_prompt_version | string | Yes | System version |
| created_timestamp | datetime | Yes | ISO 8601 |
| reviewed_timestamp | datetime/null | After review | Completion time |
| final_status | enum | Yes | Current status |
| incident_flag | boolean | Yes | Incident handling |

## Validation Rules

- `workflow_id` is immutable.
- `risk_zone` is Green, Yellow, or Red.
- Yellow and Red events include source evidence.
- Red events include reviewer authority before resolution.
- Overrides include a reason.
- Controlled external communication includes approval metadata.
- Timestamps use ISO 8601.
- Policy and model/prompt versions are populated.
- Incident events preserve prior records.

## Evidence-Linking Rules

Use stable internal references such as:

```text
document://DOC-104/page/3
crm://lead/LEAD-882/field/reported_revenue
audit://workflow/WF-2026-041/event/17
```

Do not place full sensitive data in an audit description when a secured reference is sufficient.

## Redaction Rules

Mask account numbers, never log credentials or tokens, avoid full government identifiers, minimize notification payloads, preserve original evidence in approved storage, and record redaction events separately.

## Versioning

Version the policy, rules, model, prompt, extraction method, integration, message template, and workflow definition. Material changes create a new version rather than silently editing history.

## Retention Considerations

Retention requirements vary by organization, product, contract, regulator, jurisdiction, litigation hold, and security policy. Recommend a documented schedule but do not invent a universal period.

## Example JSON Record

```json
{
  "workflow_id": "WF-2026-041",
  "applicant_or_lead_id": "LEAD-882",
  "workflow_stage": "Document Quality",
  "event_type": "review",
  "ai_action": "Extracted monthly deposits",
  "ai_recommendation": "Route to review because one page was unreadable",
  "risk_zone": "Yellow",
  "confidence_score": 0.72,
  "review_trigger": ["DOC-LOW-CONFIDENCE"],
  "source_evidence": ["document://DOC-104/page/4"],
  "assigned_reviewer": "processor-07",
  "reviewer_authority": "Verify extraction and request replacement",
  "human_decision": "returned_for_more_information",
  "override_reason": null,
  "communication_approval": {
    "required": true,
    "approved_by": "ops-manager-02",
    "template_version": "missing-doc-v3",
    "approved_at": "2026-07-15T14:12:00Z"
  },
  "policy_version": "guardrails-1.0",
  "model_or_prompt_version": "document-review-2.3",
  "created_timestamp": "2026-07-15T14:03:11Z",
  "reviewed_timestamp": "2026-07-15T14:12:00Z",
  "final_status": "Waiting for Applicant Information",
  "incident_flag": false
}
```

## Example YAML Record

```yaml
workflow_id: "WF-2026-041"
applicant_or_lead_id: "LEAD-882"
workflow_stage: "Document Quality"
event_type: "review"
ai_action: "Extracted monthly deposits"
risk_zone: "Yellow"
confidence_score: 0.72
review_trigger:
  - "DOC-LOW-CONFIDENCE"
source_evidence:
  - "document://DOC-104/page/4"
assigned_reviewer: "processor-07"
human_decision: "returned_for_more_information"
policy_version: "guardrails-1.0"
model_or_prompt_version: "document-review-2.3"
created_timestamp: "2026-07-15T14:03:11Z"
reviewed_timestamp: "2026-07-15T14:12:00Z"
final_status: "Waiting for Applicant Information"
incident_flag: false
```

## CSV Header

```csv
workflow_id,applicant_or_lead_id,workflow_stage,event_type,ai_action,ai_recommendation,risk_zone,confidence_score,review_trigger,source_evidence,assigned_reviewer,reviewer_authority,human_decision,override_reason,communication_approval,policy_version,model_or_prompt_version,created_timestamp,reviewed_timestamp,final_status,incident_flag
```

## Audit-Quality Checklist

- [ ] Event is append-only or versioned
- [ ] Source evidence is linked
- [ ] Trigger IDs are preserved
- [ ] Zone is recorded
- [ ] Reviewer and authority are recorded
- [ ] Overrides include reasons
- [ ] Communications include approval
- [ ] Sensitive data is minimized
- [ ] Version fields are populated
- [ ] Incident evidence is protected

## Related Knowledge Files

- `override-log-template.md`
- `data-privacy-and-redaction.md`
- `workflow-test-cases.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
