# Notion and Airtable Human Review Queue

**Purpose:** Provide complete database designs for review records, overrides, incidents, and policy versions.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Shared Data Model

Use four related record types: Workflow Reviews, Overrides, Incidents, and Policy/Model Versions. Store secure links to evidence instead of duplicating sensitive documents.

## Notion Database Name

**Human Review Queue**

## Notion Properties

| Property | Type |
|---|---|
| Review Record | Title |
| Workflow ID | Text |
| Applicant or Lead | Relation or Text |
| Workflow Stage | Select |
| Risk Zone | Select |
| Review Trigger | Multi-select |
| AI Action | Text |
| AI Recommendation | Text |
| Confidence Score | Number |
| Assigned Reviewer | Person |
| Reviewer Authority | Select |
| Source Evidence | URL, Files, or Relation |
| Human Decision | Select |
| Override | Relation |
| Review Deadline | Date |
| Communication Approved | Checkbox |
| Policy Version | Relation or Text |
| Incident | Relation |
| Final Status | Status |
| Created Time | Created Time |
| Last Edited | Last Edited Time |

## Notion Views

- **Needs Review:** Human Review Required or Escalated
- **Urgent Red:** Red and not completed
- **Low Confidence:** Below configured threshold
- **Overrides:** Override relation is not empty
- **Incidents:** Incident relation is not empty
- **Monitoring:** Group by stage and policy version

## Notion Formula Examples

Review aging:

```text
dateBetween(now(), prop("Created Time"), "hours")
```

Needs escalation:

```text
if(and(prop("Final Status") != "Completed", now() > prop("Review Deadline")), "Escalate", "")
```

Validate formulas against current Notion syntax before production use.

## Airtable Base Structure

### Workflow Reviews
Primary field: Review Record. Fields match the shared schema.

### Overrides
Override ID, Workflow Review link, original recommendation, human decision, reason, evidence, reviewer, root cause, rule update, incident indicator.

### Incidents
Incident ID, review link, severity, detection time, affected system, data involved, external action, containment, owner, corrective action, restart approval, status.

### Policy Versions
Version ID, effective date, owner, change summary, approved by, test result, active status.

## Airtable Views

Open Yellow Reviews; Open Red Reviews; Overdue Reviews; Overrides This Month; Incidents; Change Approval Pending; Completed QA Sample.

## Airtable Automation Patterns

- Red zone → assign authorized reviewer and notify
- Deadline passes → escalate owner
- Human decision differs → create Override record
- Incident flag → create Incident and pause workflow
- Policy version changes → require retest status

Do not auto-send binding applicant communications.

## Example Synthetic Record

```json
{
  "review_record": "REV-2026-014",
  "workflow_id": "WF-2026-041",
  "applicant_or_lead": "LEAD-882",
  "workflow_stage": "Document Quality",
  "risk_zone": "Yellow",
  "review_trigger": ["Low extraction confidence"],
  "ai_action": "Extracted deposits",
  "confidence_score": 0.72,
  "assigned_reviewer": "processor-07",
  "reviewer_authority": "Verify extraction",
  "human_decision": "Returned for More Information",
  "final_status": "Waiting for Applicant Information"
}
```

## CSV Import Header

```csv
review_record,workflow_id,applicant_or_lead,workflow_stage,risk_zone,review_trigger,ai_action,ai_recommendation,confidence_score,assigned_reviewer,reviewer_authority,source_evidence,human_decision,override_reason,review_deadline,communication_approved,policy_version,incident_flag,final_status
```

## Setup Checklist

- [ ] Create review, override, incident, and version tables
- [ ] Configure select values consistently
- [ ] Restrict sensitive fields
- [ ] Create reviewer and escalation views
- [ ] Add deadlines
- [ ] Test relations
- [ ] Test Red-action blocking
- [ ] Test incident path
- [ ] Document owners and permissions
- [ ] Use synthetic data before live records

## Permission Considerations

Reviewers should access only needed records. Incident records may require narrower access. Public views must exclude applicant data. OAuth integrations should request minimum scopes.

This file describes a proposed design. It does not claim any database has been created.

## Related Knowledge Files

- `crm-routing-patterns.md`
- `data-privacy-and-redaction.md`
- `action-endpoints.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
