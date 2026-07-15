# Pre-Launch QA Scorecard

**Purpose:** Provide the full 40-point readiness assessment for AI-assisted funding workflows.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Scorecard Purpose

The scorecard measures whether basic operational controls are documented, implemented, assigned, and tested. It does not certify legal or regulatory compliance.

## Scoring Instructions

- **0 — Missing:** No usable control or evidence.
- **1 — Partial:** Documented or partly implemented but not fully tested.
- **2 — Complete:** Implemented, assigned, evidenced, and tested.

## Full Scoring Table

| # | Control | Evidence expected | Score |
|---:|---|---|---:|
| 1 | Named workflow owner | Owner documented with backup and pause authority | 0–2 |
| 2 | Green, Yellow, and Red classifications | Every action classified; mixed tasks separated | 0–2 |
| 3 | Human-review triggers | Specific, testable, evidence-linked rules | 0–2 |
| 4 | Reviewer authority | Authority recorded for Yellow and Red actions | 0–2 |
| 5 | Source evidence | Outputs link to fields, records, documents, or pages | 0–2 |
| 6 | Confidence thresholds | Tested thresholds documented where confidence applies | 0–2 |
| 7 | Low-confidence escalation | Below-threshold output pauses or routes to review | 0–2 |
| 8 | Sensitive-data protection | Minimization, access, redaction, and secure storage | 0–2 |
| 9 | Consent mapping | Collection, use, and outreach permissions mapped | 0–2 |
| 10 | Approved communication templates | Templates versioned and controlled | 0–2 |
| 11 | Forbidden-action blocks | Technical or procedural prevention implemented | 0–2 |
| 12 | Override logging | Original output, decision, reason, evidence, and reviewer retained | 0–2 |
| 13 | Audit retention | Documented retention and access policy | 0–2 |
| 14 | Complaint and dispute escalation | Owner, status, evidence, and deadline defined | 0–2 |
| 15 | Model, prompt, and rule versioning | Material changes create new tested versions | 0–2 |
| 16 | Monitoring metrics | Errors, overrides, incidents, queue time, and drift tracked | 0–2 |
| 17 | Incident-response procedure | Containment, evidence, ownership, remediation, restart | 0–2 |
| 18 | Staff training | Reviewers understand roles, limits, and escalation | 0–2 |
| 19 | Edge-case testing | Normal, failure, adversarial, and authority cases tested | 0–2 |
| 20 | Human pause or disable control | Authorized human can stop affected workflow | 0–2 |

**Maximum score:** 40

## Score Interpretation

| Score | Status | Recommendation |
|---:|---|---|
| 34–40 | Controlled launch candidate | Launch narrowly, monitor, and sample outputs |
| 26–33 | Conditional | Fix weak controls before scaling |
| 16–25 | High risk | Keep in internal or mandatory-review pilot |
| 0–15 | Not ready | Do not deploy beyond testing |

## Critical Fail Conditions

Regardless of total score, do not launch high-impact automation when there is no workflow owner, Red actions can leave without approval, sensitive data is exposed, audit logging is unavailable, reviewer authority is undefined, Red triggers do not stop execution, no pause control exists, consent is ignored, applicant facts can be altered silently, or incident response is absent.

## Launch Blockers

For every zero score, record control owner, required evidence, target date, test, residual risk, and approval needed.

## Pilot Recommendations

- Use synthetic or low-risk records.
- Limit users and volume.
- Keep mandatory review for Yellow and Red work.
- Disable binding external communications.
- Track every override.
- Include an incident simulation.
- Define rollback and pause procedures.

## Remediation Plan Template

| Control | Current score | Gap | Owner | Fix | Test | Deadline | New score |
|---|---:|---|---|---|---|---|---:|
|  |  |  |  |  |  |  |  |

## Example Completed Scorecard

| Category | Points earned | Maximum |
|---|---:|---:|
| Ownership and classification | 4 | 4 |
| Triggers, authority, evidence | 5 | 6 |
| Confidence and data controls | 6 | 8 |
| Communications and forbidden actions | 3 | 4 |
| Audit, complaints, versioning | 5 | 6 |
| Monitoring, incident, training | 5 | 6 |
| Testing and pause control | 4 | 4 |
| **Total** | **32** | **40** |

**Interpretation:** Conditional. Fix reviewer-authority gaps and complete incident testing before increasing volume.

## JSON Score Output

```json
{
  "workflow_name": "Document Collection Router",
  "score": 32,
  "maximum_score": 40,
  "status": "Conditional",
  "critical_fail": false,
  "zero_score_controls": [],
  "priority_fixes": [
    "Document reviewer authority",
    "Complete incident simulation",
    "Add evidence-link validation"
  ],
  "recommended_scope": "Limited pilot with mandatory Yellow and Red review",
  "compliance_guarantee": false
}
```

## Related Knowledge Files

- `workflow-test-cases.md`
- `forbidden-actions.md`
- `audit-log-schema.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
