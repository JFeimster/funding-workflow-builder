# Human Override Log Template

**Purpose:** Standardize how humans document decisions that differ from AI recommendations or automated routes.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## What Counts as an Override

An override occurs when a human changes an AI recommendation, selects a different route, corrects extracted data, rejects generated communication, changes a risk zone, reopens or pauses a case, approves an exception, or rejects an automated next step.

Routine review that confirms the AI output is not an override.

## Why Overrides Matter

Overrides reveal poor data, bad thresholds, stale criteria, weak prompts, model drift, missing rules, reviewer inconsistency, useful edge cases, and incidents.

## Valid Override Reasons

- Source evidence contradicted the output
- Applicant supplied new verified information
- Criteria or policy changed
- Confidence was overstated
- Recommendation used incomplete evidence
- A documented exception applied
- A conflict of interest existed
- Draft language was inaccurate
- Reviewer authority required a different route

## Weak or Unacceptable Reasons

“Felt wrong,” “the AI is usually right,” “we needed speed,” “I know the applicant,” blank reasons, or copying the recommendation into the reason field.

## Required Fields

| Field | Requirement |
|---|---|
| Override ID | Unique |
| Workflow ID | Required |
| Original recommendation | Required |
| Original risk zone | Required |
| Human decision | Required |
| New risk zone | When changed |
| Override reason | Required |
| Supporting evidence | Required |
| Reviewer | Required |
| Reviewer authority | Required |
| Root-cause category | Required |
| Rule update needed | Yes/No |
| Model update needed | Yes/No |
| Incident indicator | Yes/No |
| Timestamps | Required |

## Root-Cause Categories

Data quality, extraction error, missing evidence, criteria change, policy exception, prompt issue, model issue, integration issue, reviewer judgment, communication issue, security/privacy, or unknown pending investigation.

## Markdown Template

| Date | Override ID | Workflow ID | AI recommendation | Human decision | Reason | Evidence | Reviewer | Authority | Root cause | Rule update? | Incident? |
|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |  | Yes/No | Yes/No |

## Example JSON

```json
{
  "override_id": "OVR-2026-019",
  "workflow_id": "WF-2026-041",
  "original_ai_recommendation": "Route to product category A",
  "original_risk_zone": "Yellow",
  "human_decision": "Return for additional information",
  "new_risk_zone": "Yellow",
  "override_reason": "Recommendation relied on an estimated revenue field that conflicted with source statements.",
  "supporting_evidence": ["document://DOC-104/page/2"],
  "reviewer": "processor-07",
  "reviewer_authority": "Verify financial data and pause routing",
  "root_cause_category": "Data quality",
  "rule_update_needed": true,
  "model_update_needed": false,
  "incident_indicator": false
}
```

## Example Completed Records

| Scenario | AI recommendation | Human decision | Evidence-based reason |
|---|---|---|---|
| Unreadable page | Continue analysis | Request replacement | Source page could not be verified |
| Stale criteria | Route to product B | Pause routing | Criteria source was older than approved version |
| Strong claim | Send message | Block and revise | Draft implied guaranteed funding |
| Duplicate flag | Escalate as fraud | Merge related record | Resubmission, not deception |

## Reporting Metrics

Track override rate by stage, rule, model/prompt version, root cause, review time, reviewer disagreement, incident conversion, and rule updates. A low override rate may indicate rubber-stamping.

## Monthly Review Process

Sample confirmed and overridden outputs, identify repeated root causes, compare reviewers, verify thresholds, review complaints and incidents, update rules, version/test changes, and record corrective action.

## Common Failures

Overwriting the original recommendation, missing authority, unsupported reasons, absent evidence, ignoring repeated patterns, and deleting inconvenient history.

## Related Knowledge Files

- `audit-log-schema.md`
- `prelaunch-qa-scorecard.md`
- `workflow-test-cases.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
