# Forbidden AI Actions

**Purpose:** Define actions AI must not perform autonomously and controls required to block them.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Absolute Prohibitions

AI must not autonomously make or communicate an unauthorized binding decision, invent facts or authority, alter source evidence, override consent, expose sensitive data or credentials, delete audit evidence, continue after a Red trigger, or expand its own scope.

## Forbidden-Action Catalog

| Category | Prohibited behavior | Required control |
|---|---|---|
| Approval promises | Guarantee or imply approval before authorized decision | Block phrases and require decision reference |
| Denial communications | Communicate rejection or final ineligibility | Require authorized creditor review |
| Binding terms | Create or present final amount, price, fees, frequency, or conditions | Allow drafts only from verified terms and require approval |
| Pricing changes | Modify pricing or repayment terms | Block automated writes to final-term fields |
| Fraud conclusions | Declare applicant or document fraudulent | Permit anomaly flags only |
| Adverse-action reasons | Invent or finalize unsupported reasons | Require actual factor source and authorized review |
| Legal conclusions | State conduct is legal or illegal | Use operational language and refer to counsel |
| Compliance conclusions | Guarantee compliance | Describe controls and unresolved questions |
| Data alteration | Change applicant facts without provenance | Store correction separately |
| Unverified submissions | Submit inferred facts as verified | Require verification status |
| Consent overrides | Treat contact data as permission | Require channel-specific consent |
| Unauthorized communications | Contact through unapproved channel | Enforce permissions |
| Sensitive-data exposure | Send or log secrets or identifiers | Redact and secure |
| Audit-log deletion | Remove or rewrite evidence | Use append-only records |
| Complaint closure | Resolve complaint autonomously | Assign complaint owner |
| Dispute resolution | Reject disputed output automatically | Pause and review |
| Closing authorization | Approve final agreement execution | Require authorized closing owner |
| Disbursement authorization | Trigger funds movement | Require separate authorized approval |
| Workflow-scope expansion | Add tools or permissions without review | Require change approval |
| Credential handling | Request or store passwords and tokens | Use secure credential stores |

## Actions Allowed Only With Human Approval

AI may prepare product-fit recommendations, exception summaries, high-impact drafts, terms comparisons, decision memos, complaint summaries, and closing checklists. An authorized human verifies evidence, possesses authority, approves the output, and records the action.

## Broker-Specific Prohibitions

A broker or referral-partner AI must not speak as the creditor, state approval without accurately communicating an authorized provider decision, state final ineligibility, invent provider criteria, promise timing, create unsupported adverse-action explanations, or present a recommendation as a binding offer.

## Creditor or Lender Distinction

A creditor may use automated systems under its own documented authority and obligations, but automation does not remove accountability. This file does not determine which decisions may be automated under applicable law or policy.

## Unsafe Versus Safer Wording

| Unsafe | Safer |
|---|---|
| “You are guaranteed approval.” | “The information may support further review; eligibility is not guaranteed.” |
| “Your statement is fraudulent.” | “The document contains inconsistencies requiring authorized review.” |
| “The AI denied you.” | “An authorized reviewer must verify the actual decision and communication.” |
| “This workflow is fully compliant.” | “The workflow includes controls but requires qualified review.” |
| “Funds will arrive tomorrow.” | “Timing depends on approval, completed requirements, and processing.” |

## Technical Enforcement Controls

- Deny-list high-risk intents
- Require decision IDs before controlled messages
- Separate draft and send permissions
- Use least-privilege credentials
- Block writes to final-term fields
- Require authenticated human callback
- Enforce role-based access
- Maintain append-only logs
- Scan outbound language
- Disable workflow on audit failure
- Test prompt injection and tool misuse

## Detection and Incident Response

When a forbidden action is attempted: stop it, record input and attempted action, preserve versions, notify owner, assess external harm, correct data or communication, and test before restart.

## Forbidden-Actions Checklist

- [ ] Approval promises
- [ ] Denial communications
- [ ] Binding terms
- [ ] Pricing changes
- [ ] Fraud conclusions
- [ ] Adverse-action reasons
- [ ] Legal conclusions
- [ ] Compliance conclusions
- [ ] Data alteration
- [ ] Unverified submissions
- [ ] Consent overrides
- [ ] Unauthorized communications
- [ ] Sensitive-data exposure
- [ ] Audit-log deletion
- [ ] Complaint closure
- [ ] Dispute resolution
- [ ] Closing authorization
- [ ] Disbursement authorization
- [ ] Workflow-scope expansion
- [ ] Credential handling

## Related Knowledge Files

- `safe-language-and-disclaimers.md`
- `action-endpoints.md`
- `workflow-test-cases.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
