# Green, Yellow, and Red Task Classifier

**Purpose:** Give the GPT a precise, repeatable method for classifying AI-supported funding workflow actions.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Classifier Purpose

The classifier determines the minimum control required for each action. Classification applies to the action, not the tool. The same model may perform Green tasks safely and Red tasks unsafely.

## Zone Definitions

### Green Zone
Low-risk, administrative, reversible work performed within approved rules. AI may execute automatically when inputs, permissions, templates, logging, and error handling are controlled.

### Yellow Zone
Decision support, uncertainty, material influence, sensitive interpretation, or low-confidence work. AI may analyze, flag, recommend, calculate, or draft. A qualified human reviews evidence before the workflow proceeds.

### Red Zone
Binding, high-impact, sensitive, legally consequential, authority-dependent, or difficult-to-reverse work. AI stops autonomous execution, prepares context, assigns an authorized human, and records the decision.

## Classification Decision Tree

1. Does the action create or communicate a binding outcome? **Red.**
2. Could it materially affect access, price, treatment, eligibility, closing, or dispute rights? **Yellow at minimum; Red if it decides or communicates the outcome.**
3. Does it require authority the system does not possess? **Red.**
4. Does it interpret uncertain, conflicting, or sensitive evidence? **Yellow.**
5. Is it administrative, reversible, approved, and logged? **Green.**
6. Is it bundled with higher-risk steps? Classify at the highest risk unless separated technically and operationally.

## Risk Factors

- Material impact on the applicant
- Binding or external communication
- Authority requirement
- Irreversibility
- Sensitive financial or identity data
- Uncertainty or low confidence
- Conflicting sources
- Policy exceptions
- Complaint, dispute, or fraud context
- Inability to reconstruct the action

## Decision Tests

### Material-Impact Test
Ask whether the action could change whether an applicant proceeds, which product is shown, what terms are presented, how urgently a case is handled, whether the applicant is discouraged, or how a complaint is resolved.

### Binding-Action Test
An action is Red when it commits the organization, communicates a final decision, changes final terms, authorizes closing or disbursement, resolves a dispute, or creates a formal reason or conclusion.

### Authority Test
Identify who may perform the action and whether the AI is support only. Lack of authority makes autonomous execution Red.

### Reversibility Test
A reversible internal tag is lower risk than an external denial. If reversal cannot fully repair harm, increase the classification.

### Data-Sensitivity Test
Sensitive data raises required security controls. Unauthorized exposure, transfer, or storage is Red.

### Confidence and Uncertainty Test
High confidence does not convert a Red task into Green. Low confidence converts otherwise routine analysis into Yellow. Conflicting evidence always requires review.

## Funding Workflow Examples

| # | Task | Zone | Reason |
|---:|---|---|---|
| 1 | Create a CRM record from an approved form | Green | Administrative and reversible |
| 2 | Normalize business-name capitalization | Green | Formatting only |
| 3 | Deduplicate exact-match lead records | Green | Administrative with merge safeguards |
| 4 | Transcribe a recorded call with consent | Green | Preparation; source retained |
| 5 | Summarize call notes | Green | No binding decision |
| 6 | Name uploaded files | Green | Administrative |
| 7 | Detect blank required fields | Green | Completeness check |
| 8 | Send a neutral missing-document reminder | Green | Approved template; no outcome claim |
| 9 | Assign an internal task | Green | Administrative routing |
| 10 | Generate a document checklist | Green | Preparation |
| 11 | Archive a completed internal task | Green | Reversible |
| 12 | Create a daily queue report | Green | Monitoring only |
| 13 | Estimate a prequalification range | Yellow | May influence expectations |
| 14 | Recommend possible product categories | Yellow | Decision support; criteria must be current |
| 15 | Score lead priority | Yellow | May affect treatment |
| 16 | Extract deposits from bank statements | Yellow | Financial evidence requires confidence and source |
| 17 | Flag unusual revenue movement | Yellow | Anomaly is not a conclusion |
| 18 | Compare reported revenue to documents | Yellow | Conflict requires review |
| 19 | Draft a product-fit explanation | Yellow | Human approval before delivery |
| 20 | Suggest missing-document questions | Yellow | Review before sending when material |
| 21 | Draft a compliance-risk flag | Yellow | Not a final legal conclusion |
| 22 | Recommend escalation based on confidence | Yellow | Human validates trigger |
| 23 | Calculate repayment scenarios | Yellow | Terms and assumptions must be verified |
| 24 | Identify a possible duplicate application | Yellow | May have legitimate explanation |
| 25 | Promise approval | Red | Binding or misleading outcome statement |
| 26 | Communicate a denial | Red | High-impact decision communication |
| 27 | Set final pricing | Red | Binding term |
| 28 | Change repayment frequency | Red | Material term change |
| 29 | Declare a bank statement fraudulent | Red | Serious conclusion requiring investigation |
| 30 | Generate final adverse-action reasons | Red | Must reflect actual decision factors |
| 31 | Authorize closing | Red | Authority-dependent action |
| 32 | Authorize disbursement | Red | Binding financial action |
| 33 | Resolve a complaint automatically | Red | Accountable review required |
| 34 | Submit altered applicant data | Red | Unverified or changed evidence |
| 35 | Override applicant consent | Red | Unauthorized action |
| 36 | Delete an audit record | Red | Destroys traceability |

## Edge Cases

- **Neutral reminder with deadline:** Green when deadline and template are verified; Yellow when the deadline may affect eligibility or comes from uncertain data.
- **Product matching:** Yellow by default; Red if presented as final approval or binding offer.
- **Fraud detection:** Pattern flag is Yellow; accusation or external conclusion is Red.
- **Calculations:** Green for pure arithmetic with verified inputs and internal use; Yellow when assumptions influence recommendations; Red when converted into binding terms without approval.

## Mixed-Risk and Bundled Tasks

Split mixed tasks into separate controls. Example: extract revenue → Yellow; compare criteria → Yellow; draft summary → Yellow; communicate approval → Red. If draft and send cannot be separated, classify the bundle Red.

## Required Output Format

```yaml
task:
  name: "Compare reported revenue with statement deposits"
  risk_zone: "Yellow"
  reason: "Material financial evidence may influence product fit."
  ai_permitted_actions:
    - "Extract figures"
    - "Show calculations"
    - "Flag discrepancies"
  human_control:
    - "Verify source pages"
    - "Resolve discrepancies"
  review_trigger: "Any material mismatch or confidence below threshold"
  prohibited_action: "Do not make or communicate a final eligibility decision"
```

## Common Classification Mistakes

- Classifying the tool instead of the action
- Treating confidence as authority
- Calling a draft-and-send workflow “drafting”
- Treating fraud flags as administrative
- Ignoring downstream effects of scores
- Classifying everything Red and making the system unusable
- Leaving bundled actions inseparable

## Related Knowledge Files

- `human-review-checkpoint-map.md`
- `forbidden-actions.md`
- `workflow-test-cases.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
