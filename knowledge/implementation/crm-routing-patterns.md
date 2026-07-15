# CRM Human-Review Routing Patterns

**Purpose:** Define platform-neutral CRM stages, fields, ownership, task triggers, escalations, overrides, and reporting.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## CRM Workflow Principles

Use the CRM as the workflow system of record, preserve applicant-provided values separately from corrected or verified values, separate lead status from funding decision status, apply role-based permissions, and route Yellow and Red records to review queues.

## Suggested Pipeline Stages

1. New Intake
2. Data Validation
3. Waiting for Applicant Information
4. Documents Received
5. Document Review
6. Product-Fit Review
7. Risk or Exception Review
8. Authorized Decision Pending
9. Communication Approval
10. Final Terms Review
11. Closing Review
12. Completed
13. Closed — No Decision Made
14. Incident Review

Do not use “Denied” as an internal convenience status unless the organization is authorized and the status accurately reflects the approved process.

## Review Statuses

AI Processing; AI Prepared — No Exception; Human Review Required; Waiting for Applicant Information; Escalated to Authorized Reviewer; Approved for Next Step; Returned for Correction; Communication Approval Required; Paused; Incident Review Required; Completed.

## Generic Field Dictionary

| Field | Type | Purpose |
|---|---|---|
| workflow_id | Text | Immutable workflow reference |
| workflow_stage | Select | Current stage |
| risk_zone | Select | Green, Yellow, Red |
| confidence_score | Number | Confidence when applicable |
| review_trigger | Multi-select | Triggered rule IDs |
| source_evidence | URL/Relation | Secure evidence links |
| assigned_reviewer | Owner/User | Current reviewer |
| reviewer_authority | Select | Administrative, workflow, exception, binding, incident |
| review_deadline | Datetime | Operational SLA |
| human_decision | Select | Approved, corrected, returned, escalated, rejected, paused |
| override_reason | Long text | Evidence-based reason |
| communication_approved | Boolean | Controlled message approval |
| policy_version | Text | Rule set |
| model_prompt_version | Text | AI version |
| incident_flag | Boolean | Incident routing |
| final_status | Status | Workflow state |

## Task Triggers

Create tasks when a document is missing, confidence is low, a material mismatch exists, criteria are stale, the applicant disputes output, a high-impact message is drafted, terms change, a deadline approaches, an override is recorded, or an incident is created.

## Ownership Rules

Assign by stage and authority, exclude conflicted reviewers, use backup owner after deadline, preserve owner history, do not assign Red work to unqualified users, and reassign complaints involving the original reviewer.

## SLA and Deadline Fields

Store created time, due time, first response, decision time, escalation time, and aging bucket. Use organization-approved SLAs and do not invent legal deadlines.

## Escalation Stages

| Condition | Stage |
|---|---|
| Yellow review overdue | Escalated Review |
| Red action attempted | Authorized Decision Pending |
| Complaint or dispute | Complaint Review |
| Audit or privacy failure | Incident Review |
| Material terms changed | Final Terms Review |

## Reporting Fields

Volume by zone, review time, trigger frequency, override rate, repeat-error category, incident count, complaint count, queue aging, model/policy version, and reviewer disagreement.

## HubSpot Mapping Example

| Generic field | HubSpot-style property |
|---|---|
| workflow_id | `guardrail_workflow_id` |
| risk_zone | `guardrail_risk_zone` |
| review_trigger | `guardrail_review_triggers` |
| assigned_reviewer | HubSpot owner |
| human_decision | `guardrail_human_decision` |
| final_status | Deal stage or custom status |

Use custom objects when one lead may contain multiple review events.

## Salesforce-Style Example

| Generic object | Salesforce-style design |
|---|---|
| Workflow | `Guardrail_Workflow__c` |
| Review event | Child `Human_Review__c` |
| Override | Child `AI_Override__c` |
| Incident | Child record or Case relation |
| Evidence | Secure content link |

## Generic CRM YAML

```yaml
pipeline:
  name: "Funding Workflow Review"
  record_key: "workflow_id"
  stages:
    - "Data Validation"
    - "Document Review"
    - "Human Review Required"
    - "Authorized Decision Pending"
    - "Communication Approval"
    - "Completed"
  ownership:
    Yellow: "stage_reviewer"
    Red: "authorized_reviewer"
  controls:
    - "block outbound message when communication_approved is false"
    - "block closing when risk_zone is Red and human_decision is blank"
```

## CSV Header

```csv
workflow_id,applicant_or_lead_id,workflow_stage,risk_zone,confidence_score,review_trigger,source_evidence,assigned_reviewer,reviewer_authority,review_deadline,human_decision,override_reason,communication_approved,policy_version,model_prompt_version,incident_flag,final_status
```

## Related Knowledge Files

- `notion-airtable-review-queue.md`
- `audit-log-schema.md`
- `action-endpoints.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
