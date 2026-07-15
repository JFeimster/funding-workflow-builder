# Exception Trigger Library

**Purpose:** Provide reusable conditions that pause automation, create human-review records, or escalate incidents.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Trigger Design Rules

A trigger must be specific enough to detect, connected to source evidence, assigned to a reviewer, tied to a deadline and status, and clear about allowed and prohibited AI actions.

## Structured Trigger Table

| Trigger | Description | Zone | Stage | Evidence | Reviewer | Allowed AI action | Prohibited AI action | Default status | Deadline |
|---|---|---|---|---|---|---|---|---|---|
| Missing consent | Consent absent, ambiguous, expired, or disputed | Red | Data and Consent | Consent record and source | Data owner | Quarantine and request clarification | Do not initiate outreach | Human Review Required | Immediate |
| Unverified source | Lead or data arrived from unapproved source | Yellow | Data and Consent | Source metadata | Intake specialist | Identify source and hold record | Do not enrich or distribute | Waiting for Source Verification | 1 business day |
| Identity conflict | Names, addresses, ownership, or entity records conflict | Yellow | Data and Consent | Source records | Processor | Compare evidence and request clarification | Do not merge records | Human Review Required | 1 business day |
| Sensitive-data exposure | Sensitive data logged or sent improperly | Red | Data and Consent | Incident evidence | Security owner | Contain and preserve evidence | Do not copy or continue | Incident Review Required | Immediate |
| Missing document | Required document absent | Yellow | Document Quality | Checklist and history | Processor | Request missing item | Do not infer values | Waiting for Applicant Information | 1 business day |
| Unreadable document | File or page cannot be reliably read | Yellow | Document Quality | Original file and page | Processor | Request replacement | Do not mark verified | Returned for Correction | 1 business day |
| Low extraction confidence | Extraction below tested threshold | Yellow | Document Quality | Confidence and source page | Processor | Verify manually | Do not continue material analysis | Human Review Required | Same day |
| Material mismatch | Application and source conflict | Yellow | Document Quality | Comparison output | Processor | Resolve discrepancy | Do not pick silently | Human Review Required | Same day |
| Criteria not verified | Criteria lack current authoritative source | Yellow | Eligibility and Product Fit | Criteria source and date | Product owner | Verify current criteria | Do not claim eligibility | Escalated | 1 business day |
| Policy-boundary case | Applicant near or outside threshold | Yellow | Eligibility and Product Fit | Criteria comparison | Authorized reviewer | Apply exception process | Do not auto-reject | Human Review Required | 1 business day |
| Goal mismatch | Recommendation conflicts with stated need | Yellow | Eligibility and Product Fit | Goal and recommendation | Broker | Reassess fit | Do not hide mismatch | Human Review Required | Same day |
| Possible duplicate | Record may duplicate another | Yellow | Risk and Anomaly Review | Hashes and links | Risk reviewer | Verify relationship | Do not accuse fraud | Human Review Required | Same day |
| Suspected manipulation | Pattern suggests alteration | Red | Risk and Anomaly Review | Original evidence and rule | Risk reviewer | Investigate and contain | Do not send accusation | Escalated | Immediate |
| Applicant disputes output | Applicant challenges score or summary | Red | Risk and Anomaly Review | Disputed output and sources | Complaint owner | Pause and review | Do not restate as fact | Dispute Review Required | Immediate |
| Approval language | Draft states or implies approval | Red | Communications and Disclosures | Draft and authority | Authorized communicator | Verify decision and wording | Do not send automatically | Communication Approval Required | Immediate |
| Denial language | Draft communicates rejection | Red | Communications and Disclosures | Decision source and draft | Authorized creditor representative | Verify reasons and process | Do not send from broker AI | Communication Approval Required | Immediate |
| Fraud accusation | Draft labels applicant fraudulent | Red | Communications and Disclosures | Evidence and status | Risk owner | Block and investigate | Do not communicate accusation | Incident Review Required | Immediate |
| Complaint received | Applicant expresses complaint or harm | Red | Communications and Disclosures | Interaction record | Complaint owner | Acknowledge and escalate | Do not auto-close | Complaint Review Required | Immediate |
| Terms changed | Amount, price, frequency, or conditions changed | Red | Final Terms and Closing | Version comparison | Closing reviewer | Reverify and reapprove | Do not execute old approval | Human Review Required | Immediate |
| Audit unavailable | Required logging failed | Red | Monitoring, Overrides, and Feedback | System logs and error | Workflow administrator | Pause affected path | Do not continue high-impact action | Incident Review Required | Immediate |
| Model or prompt changed | Material model, prompt, policy, or rule update | Yellow | Monitoring, Overrides, and Feedback | Change record and tests | Workflow administrator | Retest and approve | Do not deploy silently | Change Review Required | Before deployment |
| Repeated override pattern | Same recommendation frequently overturned | Yellow | Monitoring, Overrides, and Feedback | Override metrics | Operations manager | Investigate root cause | Do not ignore drift | Monitoring Review Required | Weekly |
| Incident detected | Security, privacy, harmful output, or unauthorized action | Red | Monitoring, Overrides, and Feedback | Incident evidence | Incident owner | Contain and remediate | Do not delete evidence | Incident Review Required | Immediate |

## Machine-Readable YAML Example

```yaml
trigger:
  id: "DOC-LOW-CONFIDENCE"
  name: "Low extraction confidence"
  category: "extraction_confidence"
  risk_zone: "Yellow"
  workflow_stage: "Document Quality"
  condition:
    field: "extraction_confidence"
    operator: "less_than"
    value_from: "approved_threshold"
  evidence_required:
    - "original_document_id"
    - "page_reference"
    - "extraction_output"
    - "model_version"
  assigned_reviewer_role: "Processor"
  allowed_ai_actions:
    - "attach source page"
    - "show uncertain fields"
    - "create review record"
  prohibited_ai_actions:
    - "mark values as verified"
    - "continue product-fit analysis"
  default_status: "Human Review Required"
  escalation_deadline: "same_business_day"
```

## Trigger Priority

1. Red overrides Yellow.
2. Incident and privacy triggers take immediate priority.
3. Binding communications remain blocked.
4. Duplicate alerts about one event should create one coordinated review record while retaining every trigger ID.

## Trigger Tuning

Review false positives, missed exceptions, reviewer overrides, and complaint patterns. Do not weaken a control solely to reduce queue volume. Fix poor data, vague rules, or bad thresholds first.

## Related Knowledge Files

- `eight-workflow-checkpoints.md`
- `escalation-paths.md`
- `workflow-test-cases.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
