# Human Review Checkpoint Map

**Purpose:** Provide the master framework for deciding what AI may do, when automation must pause, who decides, and what evidence must be recorded.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

**A practical control system for AI-assisted business funding workflows**

Use this lead magnet to decide:

- What AI may handle automatically
- What must pause for human review
- Who owns the decision
- Which exceptions trigger escalation
- What evidence must be recorded
- Which actions AI must never take
- Whether a workflow is ready to launch

> **Operating rule:** Automate the preparation. Escalate the uncertainty. Assign the decision. Record what happened.

---

## Who This Is For

This checkpoint map is designed for:

- Business funding brokers
- Funding agency owners
- ISOs and referral partners
- Processors and operations teams
- Fintech builders
- CRM and automation consultants
- Small-business finance teams
- AI workflow designers

It is not legal advice and does not guarantee regulatory compliance. Requirements vary by organization, product, jurisdiction, and role.

---

# One-Page Human Review Map

## Step 1 — Classify the Task

Every AI-supported action belongs in one of three zones.

| Zone | Meaning | Typical AI Role | Human Role |
|---|---|---|---|
| **Green** | Low-risk administrative work | Execute automatically within approved rules | Review samples and monitor errors |
| **Yellow** | Decision support or uncertain output | Analyze, flag, recommend, or draft | Review evidence and approve the next step |
| **Red** | Binding, high-impact, or sensitive action | Stop, prepare context, and escalate | Decide, approve, communicate, and accept accountability |

### Green Zone Examples

- Creating CRM records
- Deduplicating leads
- Naming and sorting files
- Scheduling appointments
- Transcribing calls
- Summarizing notes
- Identifying blank fields
- Sending neutral reminders
- Routing tasks
- Building document checklists

### Yellow Zone Examples

- Prequalification estimates
- Product matching
- Lead scoring
- Bank-statement observations
- Cash-flow analysis
- Anomaly flags
- Eligibility comparisons
- Suggested reason codes
- Compliance scans
- Recommended next actions

### Red Zone Examples

- Promising approval
- Communicating a denial
- Setting or changing binding terms
- Declaring documents fraudulent
- Issuing final compliance conclusions
- Sending adverse-action explanations
- Authorizing closing or disbursement
- Resolving disputes or appeals
- Submitting altered or unverified information

---

# The Eight Human Checkpoints

## 1. Data and Consent

**AI may:**

- Capture form submissions
- Normalize names, addresses, and phone numbers
- Identify duplicate records
- Create CRM entries
- Route leads by approved criteria

**Human review triggers:**

- Missing or ambiguous consent
- Data from an unapproved source
- Sensitive information entered in an unrestricted field
- Applicant disputes how data was collected
- Outreach channel is not clearly authorized
- Ownership or identity fields conflict

**Required human decision:**

- Confirm the data may be used
- Correct or delete unsupported data
- Approve the communication channel
- Escalate privacy or consent concerns

---

## 2. Document Quality

**AI may:**

- Classify uploaded documents
- Extract dates, balances, deposits, and names
- Detect missing pages
- Flag unreadable or password-protected files
- Compare document fields across sources

**Human review triggers:**

- Low-confidence extraction
- Illegible or incomplete documents
- Mismatched business names or addresses
- Numbers do not reconcile
- Possible alteration or tampering
- Material information appears inconsistent
- A required document is missing

**Required human decision:**

- Verify source documents
- Request corrected files
- Determine whether the inconsistency is material
- Escalate suspected alteration without accusing the applicant

---

## 3. Eligibility and Product Fit

**AI may:**

- Compare applicant data against documented criteria
- Organize possible product categories
- Identify unmet requirements
- Summarize missing information
- Prepare questions for the reviewer

**Human review triggers:**

- Provider criteria may have changed
- Multiple products carry materially different costs or structures
- Applicant goals conflict with the recommendation
- A recommendation relies on estimated data
- The broker has a financial incentive that may affect the recommendation
- The applicant sits near a policy boundary

**Required human decision:**

- Confirm criteria are current
- Verify the recommendation fits the stated use case
- Disclose limitations or conflicts where appropriate
- Route the applicant to an authorized provider or reviewer

---

## 4. Risk and Anomaly Review

**AI may:**

- Flag duplicate submissions
- Identify unusual deposit patterns
- Highlight repeated returned payments
- Detect inconsistent ownership information
- Compare dates and document versions
- Surface unexpected revenue changes

**Human review triggers:**

- High-risk flag without clear evidence
- Potential fraud or document manipulation
- Conflicting explanations
- Reused or duplicated files
- Material discrepancy between application and documents
- Pattern may have a legitimate explanation

**Required human decision:**

- Review the evidence
- Request clarification
- Decide whether escalation is necessary
- Avoid converting an anomaly into an unsupported accusation

---

## 5. Decision Authority

**AI may:**

- Prepare a one-page deal summary
- Perform calculations
- Organize policy criteria
- List open questions and exceptions
- Recommend next administrative steps

**Human review triggers:**

- The action may materially affect the applicant
- Approval, denial, pricing, or eligibility is involved
- The case falls outside standard policy
- Required evidence is missing
- Conflicting factors remain unresolved

**Required human decision:**

- Confirm who has authority
- Make or communicate the authorized decision
- Record the evidence used
- Document any override

---

## 6. Communications and Disclosures

**AI may:**

- Draft missing-document reminders
- Draft neutral status updates
- Prepare call notes
- Summarize next procedural steps
- Suggest approved message templates

**Human review triggers:**

- Message promises approval or funding speed
- Final pricing or repayment terms are mentioned
- A denial or adverse action is communicated
- Suspected fraud is discussed
- A complaint or dispute is involved
- The message departs from approved language
- Sensitive information is included

**Required human decision:**

- Approve or revise the message
- Confirm the statement is accurate
- Ensure the sender has authority
- Preserve any required notice or disclosure process

---

## 7. Final Terms and Closing

**AI may:**

- Compare document versions
- Highlight changed values
- Confirm checklist completion
- Prepare a closing summary
- Route documents for signature

**Human review triggers:**

- Funding amount changed
- Pricing or payment terms changed
- Applicant information changed
- Required disclosures are missing
- Final documents conflict with prior representations
- A closing condition remains unresolved

**Required human decision:**

- Verify final terms
- Confirm the correct agreement is used
- Approve closing or disbursement
- Document material changes

---

## 8. Monitoring, Overrides, and Feedback

**AI may:**

- Log workflow activity
- Measure false positives
- Track review volume
- Surface repeated exceptions
- Generate monitoring reports

**Human review triggers:**

- Error rates increase
- Reviewers frequently override the same recommendation
- Complaints cluster around one workflow
- A prompt, model, vendor, or policy changes
- The workflow acts outside its approved scope
- Sensitive data is mishandled

**Required human decision:**

- Pause or limit the workflow
- Investigate incidents
- Update rules or thresholds
- Retrain staff
- Record corrective action
- Reapprove the workflow before relaunch

---

# Exception Trigger Library

Use these triggers to decide when automation must pause.

## Data Triggers

- Missing consent
- Unverified source
- Conflicting identity data
- Duplicate applicant
- Unsupported data enrichment
- Sensitive data in the wrong field
- Stale or incomplete record

## Document Triggers

- Low extraction confidence
- Missing pages
- Inconsistent totals
- Unreadable file
- Password protection
- Suspected alteration
- Business name mismatch
- Date mismatch
- Duplicate document
- Unsupported file type

## Eligibility Triggers

- Criteria not recently verified
- Applicant near a policy threshold
- Missing required data
- Multiple plausible product paths
- Recommendation conflicts with stated use of funds
- Recommendation based on estimated values
- Material exception required

## Risk Triggers

- Unexplained revenue swing
- Repeated returned payments
- Conflicting ownership information
- Possible synthetic or reused documents
- Duplicate submissions
- Suspicious timing patterns
- Applicant disputes system output

## Communication Triggers

- Approval language
- Denial language
- Guaranteed outcome language
- Binding terms
- Legal or compliance interpretation
- Fraud accusation
- Complaint response
- Adverse-action explanation
- Sensitive information in outbound message

## Workflow Triggers

- AI exceeds its assigned role
- Reviewer lacks authority
- No evidence is attached
- Confidence falls below threshold
- Required checklist item is incomplete
- Override reason is missing
- Model, prompt, or policy changed
- Audit log is unavailable

---

# Reviewer Assignment Fields

Use these fields in Notion, Airtable, HubSpot, your CRM, or a workflow database.

| Field | Purpose |
|---|---|
| Workflow ID | Unique record for the workflow instance |
| Applicant or Lead ID | Links the review to the correct file |
| Workflow Stage | Intake, documents, eligibility, risk, communication, closing, monitoring |
| Risk Zone | Green, Yellow, or Red |
| AI Action | What the system performed |
| AI Recommendation | What the system suggested |
| Confidence Score | Confidence or certainty value |
| Review Trigger | Why human review was required |
| Source Evidence | Documents, fields, pages, or records used |
| Assigned Reviewer | Person responsible for review |
| Reviewer Authority | What the reviewer is authorized to decide |
| Review Deadline | Required completion time |
| Human Decision | Approved, corrected, escalated, rejected, or paused |
| Override Reason | Why the human changed the AI recommendation |
| Communication Approved By | Person approving outbound messaging |
| Policy Version | Rule set used during review |
| Audit Log URL | Link to activity history |
| Final Status | Current workflow state |
| Incident Flag | Whether the case requires investigation |

---

# Override Log Template

Use one row per override.

| Date | Workflow ID | AI Recommendation | Human Decision | Override Reason | Evidence | Reviewer | Rule Update Needed? |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  | Yes / No |

## Good Override Reasons

- Source document contradicted extracted data
- Criteria changed after the automation was configured
- Applicant supplied new evidence
- AI confidence was overstated
- Recommendation relied on incomplete information
- Human reviewer identified an exception
- Policy requires additional review
- Communication language was inaccurate or too strong

## Weak Override Reasons

- “Felt wrong”
- “I know this applicant”
- “The AI usually gets it right”
- “We needed to move faster”
- “The lender will figure it out”

An override should improve accountability, not bury it.

---

# Forbidden Actions Checklist

AI must not be authorized to perform these actions without explicit, accountable human control.

- [ ] Guarantee approval or funding
- [ ] Promise a specific funding speed
- [ ] Invent eligibility criteria
- [ ] Invent rates, fees, or repayment terms
- [ ] Communicate a binding approval
- [ ] Communicate a denial without authorized review
- [ ] Create unsupported adverse-action reasons
- [ ] Declare an applicant or document fraudulent
- [ ] Alter applicant-provided information
- [ ] Submit unverified information
- [ ] Provide final legal or compliance conclusions
- [ ] Override required consent
- [ ] Contact an applicant through an unauthorized channel
- [ ] Expose sensitive financial information
- [ ] Remove audit records
- [ ] Close a complaint or dispute automatically
- [ ] Approve closing or disbursement
- [ ] Operate outside the documented workflow scope

---

# Pre-Launch QA Score

Score each item from **0 to 2**.

- **0 = Missing**
- **1 = Partially implemented**
- **2 = Fully implemented and tested**

| Control | Score |
|---|---:|
| The workflow has a named owner | 0–2 |
| Every action is classified Green, Yellow, or Red | 0–2 |
| Human-review triggers are documented | 0–2 |
| Reviewer authority is clearly defined | 0–2 |
| AI outputs include source evidence | 0–2 |
| Confidence thresholds are documented | 0–2 |
| Low-confidence outputs stop or escalate | 0–2 |
| Sensitive data fields are protected | 0–2 |
| Consent requirements are mapped | 0–2 |
| Approved communication templates exist | 0–2 |
| Forbidden actions are technically blocked | 0–2 |
| Overrides are logged | 0–2 |
| Audit records are retained | 0–2 |
| Complaints and disputes have an escalation path | 0–2 |
| Model, prompt, and rule changes are versioned | 0–2 |
| Monitoring metrics are defined | 0–2 |
| Incident response procedures exist | 0–2 |
| Staff have completed workflow training | 0–2 |
| The workflow has been tested with edge cases | 0–2 |
| A human can pause or disable the workflow | 0–2 |

## Score Interpretation

| Score | Status | Recommendation |
|---|---|---|
| **34–40** | Launch-ready with monitoring | Proceed with controlled deployment and routine review |
| **26–33** | Conditional | Fix weak controls before expanding volume |
| **16–25** | High risk | Keep in pilot mode with mandatory review |
| **0–15** | Not ready | Do not deploy beyond internal testing |

A high score does not guarantee compliance. It means the workflow has basic operational controls worth testing.

---

# Notion Workflow Template

Create a database named:

**Human Review Queue**

## Suggested Properties

| Property | Type |
|---|---|
| Review Record | Title |
| Workflow ID | Text |
| Lead or Applicant | Relation or Text |
| Workflow Stage | Select |
| Risk Zone | Select |
| Review Trigger | Multi-select |
| AI Action | Text |
| AI Recommendation | Long Text |
| Confidence Score | Number |
| Assigned Reviewer | Person |
| Reviewer Authority | Select |
| Source Evidence | Files, URL, or Relation |
| Human Decision | Select |
| Override Reason | Long Text |
| Review Deadline | Date |
| Communication Approved | Checkbox |
| Policy Version | Text |
| Audit Log | URL |
| Incident Flag | Checkbox |
| Final Status | Status |
| Created Time | Created Time |
| Last Edited | Last Edited Time |

## Recommended Views

1. **Needs Review** — Yellow and Red records not completed  
2. **Urgent Exceptions** — Red records ordered by deadline  
3. **Low Confidence** — Confidence below the approved threshold  
4. **Overrides** — Human decision differs from AI recommendation  
5. **Incidents** — Incident Flag checked  
6. **Monitoring** — Completed records grouped by workflow stage  

---

# Airtable or CRM Import Fields

Use this header row for a CSV import:

```csv
review_record,workflow_id,applicant_id,workflow_stage,risk_zone,ai_action,ai_recommendation,confidence_score,review_trigger,source_evidence,assigned_reviewer,reviewer_authority,review_deadline,human_decision,override_reason,communication_approved_by,policy_version,audit_log_url,incident_flag,final_status
```

## Suggested Select Values

### workflow_stage

```text
Data and Consent
Document Quality
Eligibility and Product Fit
Risk and Anomaly Review
Decision Authority
Communications and Disclosures
Final Terms and Closing
Monitoring and Feedback
```

### risk_zone

```text
Green
Yellow
Red
```

### human_decision

```text
Approved
Corrected
Returned for More Information
Escalated
Rejected
Paused
Incident Review
```

### final_status

```text
AI Processing
AI Prepared — No Exception
Human Review Required
Waiting for Applicant Information
Escalated to Authorized Reviewer
Approved for Next Step
Returned for Correction
Closed — No Decision Made
Decision Communicated
Incident Review Required
```

---

# n8n Workflow Specification

## Workflow Name

**Human Review Checkpoint Router**

## Trigger

- New or updated funding workflow record
- New application submission
- New document upload
- AI analysis completed
- Communication draft created
- Risk flag generated

## Core Nodes

1. **Trigger Node**  
   Receives the application, document, or workflow event.

2. **Data Validation Node**  
   Confirms required fields are present.

3. **AI Analysis Node**  
   Extracts, summarizes, classifies, or drafts within approved limits.

4. **Risk Classifier Node**  
   Assigns Green, Yellow, or Red.

5. **Confidence Threshold Node**  
   Compares confidence against approved thresholds.

6. **Exception Rules Node**  
   Checks for consent, document, eligibility, risk, communication, and workflow exceptions.

7. **Human Review Router**  
   Assigns the correct reviewer based on stage, risk, and authority.

8. **Review Queue Node**  
   Creates a record in Notion, Airtable, CRM, or another approved system.

9. **Wait Node**  
   Pauses until a human decision is received.

10. **Decision Branch Node**  
    Routes Approved, Corrected, Escalated, Rejected, or Incident Review outcomes.

11. **Audit Log Node**  
    Stores AI output, evidence, human decision, override reason, and timestamps.

12. **Notification Node**  
    Sends approved alerts to the reviewer or operations team.

## Routing Logic

```text
IF risk_zone = Green
AND confidence_score >= approved_threshold
AND no_exception_trigger = true
THEN continue administrative workflow
AND write audit log

IF risk_zone = Yellow
OR confidence_score < approved_threshold
OR exception_trigger = true
THEN create human review record
AND pause workflow

IF risk_zone = Red
THEN block external action
AND assign authorized reviewer
AND require explicit human decision

IF incident_flag = true
THEN pause workflow
AND notify workflow owner
AND create incident review task
```

## Required Audit Payload

```json
{
  "workflow_id": "",
  "workflow_stage": "",
  "risk_zone": "",
  "ai_action": "",
  "ai_recommendation": "",
  "confidence_score": 0,
  "review_trigger": [],
  "source_evidence": [],
  "assigned_reviewer": "",
  "reviewer_authority": "",
  "human_decision": "",
  "override_reason": "",
  "policy_version": "",
  "created_at": "",
  "reviewed_at": "",
  "final_status": ""
}
```

---

# Copy/Paste AI Guardrail Prompt

```text
You are an operations support assistant inside a business funding workflow.

Your role is to organize information for qualified human review. You are not a lender, underwriter, attorney, compliance officer, or final decision-maker.

Return only:

1. Verified facts supported by the supplied materials
2. Missing or unreadable information
3. Conflicts between sources
4. Calculations with source values shown
5. Possible workflow or policy exceptions
6. Questions a qualified reviewer should answer
7. Recommended next administrative step
8. Risk classification: Green, Yellow, or Red
9. Whether human review is required
10. The exact trigger requiring review

Do not:

- Approve or deny funding
- Guarantee eligibility
- Invent provider criteria
- Accuse anyone of fraud
- Generate binding terms
- Provide legal conclusions
- Create unsupported adverse-action reasons
- Hide uncertainty
- Modify applicant-provided facts
- Continue when a Red Zone trigger is present

For every observation, cite the source field, document, page, or record used.
Label uncertain information clearly.
Escalate high-impact, ambiguous, or conflicting issues.
```

---

# Fast Implementation Checklist

- [ ] Pick one workflow to audit
- [ ] List every automated action
- [ ] Assign each action Green, Yellow, or Red
- [ ] Add exception triggers
- [ ] Define reviewer roles
- [ ] Define reviewer authority
- [ ] Add confidence thresholds
- [ ] Require source evidence
- [ ] Build the review queue
- [ ] Add the override log
- [ ] Block forbidden actions
- [ ] Test edge cases
- [ ] Score the workflow
- [ ] Launch in controlled mode
- [ ] Review overrides and incidents monthly

---

# Final Rule

A responsible AI funding workflow should always answer four questions:

1. **What may the AI do?**
2. **What triggers human review?**
3. **Who has authority to decide?**
4. **Where is the evidence recorded?**

If the workflow cannot answer all four, it is not ready for autonomous execution.

---

#

## Related Knowledge Files

- `eight-workflow-checkpoints.md`
- `exception-trigger-library.md`
- `prelaunch-qa-scorecard.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
