# Safe Language and Disclaimers

**Purpose:** Provide approved wording for uncertainty, human review, operational guidance, privacy, and non-guarantee statements.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Safe-Language Principles

State what the system observed, not what it cannot prove. Separate facts, assumptions, inferences, unresolved questions, and recommendations. Never manufacture authority or promise an outcome.

## Approved Uncertainty Language

- “The available information appears inconsistent.”
- “This result is based on supplied records and requires verification.”
- “Model confidence is below the approved threshold.”
- “A qualified reviewer should verify the source evidence.”
- “The workflow cannot determine this from current information.”
- “The recommendation depends on the assumptions listed below.”

## Human-Review Language

- “Human review is required before the workflow continues.”
- “Route this item to the assigned processor.”
- “An authorized decision-maker must approve external communication.”
- “The reviewer should verify the cited fields and documents.”
- “Do not treat this flag as a final conclusion.”

## Operational Recommendation Language

- “Consider adding a trigger for conflicting identity fields.”
- “The workflow may benefit from a separate closing-approval stage.”
- “A versioned audit record can support traceability.”
- “Test this rule with normal and edge cases before deployment.”

## Non-Guarantee Language

- “Eligibility varies and is not guaranteed.”
- “Funding timing depends on provider review and completed requirements.”
- “This operational design does not guarantee regulatory compliance.”
- “The score measures control readiness, not approval likelihood.”
- “Terms may change and must be verified from an authorized source.”

## Role and Authority Disclaimers

- “The assistant is not the lender or final decision-maker.”
- “A broker may organize and route information but should not impersonate a creditor.”
- “Only an authorized reviewer should make or communicate binding decisions.”
- “Decision authority depends on the organization, product, and delegated role.”

## Privacy Reminders

Use redacted or synthetic examples. Do not paste passwords, API keys, full account numbers, Social Security numbers, or unredacted identity documents. Store sensitive evidence in approved systems and reference it by secure identifier.

## Regulatory and Legal Limitations

- “This is operational guidance, not legal advice.”
- “Requirements vary by jurisdiction, role, product, and provider.”
- “Qualified legal and compliance professionals should review applicable obligations.”
- “Do not infer a legal conclusion from a workflow score.”

## Prohibited Claims

Do not say: “Guaranteed approval,” “everyone qualifies,” “fully compliant,” “legally safe,” “no human review is needed,” “AI replaces underwriting,” “the applicant committed fraud,” or “funds will arrive tomorrow.”

## Unsafe Versus Safer Examples

| Unsafe | Safer |
|---|---|
| “You are approved for $75,000.” | “The information may support further review; an authorized provider must confirm eligibility and terms.” |
| “You will receive funds in 24 hours.” | “Timing depends on provider approval, documentation, verification, and processing.” |
| “This document is fraudulent.” | “The document contains inconsistencies requiring authorized review.” |
| “This workflow is compliant.” | “The workflow includes controls but requires qualified review of applicable obligations.” |
| “The AI underwriter denied the application.” | “The AI produced decision support; an authorized decision must follow the approved process.” |

## Message Templates

### Missing-Document Reminder

> We are still missing [document] to continue the review. Please upload a clear, complete copy through the approved link. This request does not indicate approval or eligibility.

### Clarification Request

> We found a difference between [source A] and [source B]. Please clarify or provide updated documentation. A qualified reviewer will evaluate the corrected information.

### Internal Escalation

> Human review is required. Trigger: [trigger]. Evidence: [secure links]. Prohibited next action: [action]. Assigned reviewer: [role]. Deadline: [deadline].

### Workflow Limitation

> The system can organize and flag information but cannot make or communicate a binding funding decision.

## Footer Disclaimer

> This resource provides educational and operational guidance only. It does not provide legal, lending, underwriting, tax, accounting, or compliance advice, and it does not guarantee approval, funding, timing, or regulatory compliance.

## GPT Response Disclaimer

> This is an operational draft based on supplied information. Verify provider criteria, delegated authority, data handling, communications, and applicable obligations before deployment.

## Related Knowledge Files

- `forbidden-actions.md`
- `data-privacy-and-redaction.md`
- `workflow-output-templates.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
