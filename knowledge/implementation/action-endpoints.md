# Proposed Action Endpoints

**Purpose:** Document the proposed No-Auth, API Key, and OAuth Action catalog, payload boundaries, confirmation rules, and rollout.

```yaml
knowledge_file:
  version: "1.0"
  status: production-ready
  product: "Funding Workflow Guardrail Builder"
  last_updated: "2026-07-15"
```

## Status

All endpoints are **proposed contracts** until implemented, secured, tested, and deployed. This file does not represent a live production API.

## Action Design Principles

Use the least powerful authentication tier, separate analysis from external writes, require confirmation before writes, prohibit live PII in No-Auth Actions, use idempotency keys, return structured errors, record user/target/outcome, and create n8n workflows disabled by default.

## Authentication Categories

- **No-Auth:** Public, non-persistent utilities for redacted or synthetic input.
- **API Key:** Protected owner-controlled analysis and rendering. A shared key is not user identity.
- **OAuth:** User-specific access to projects, Drive, Notion, Airtable, CRM, n8n, audits, and notifications.

## Confirmation Rules

Before a write Action, state the target system, resource to create or update, payload summary, permissions used, and expected result. Obtain explicit confirmation.

## Read Versus Write Actions

Read and analysis Actions may run without confirmation when they do not expose or change sensitive data. Writes, notifications, workflow creation, incidents, and exports require confirmation.

## Sensitive-Data Restrictions

No live applicant PII in No-Auth endpoints; redact logs; use secure references; never return credentials; require OAuth and approved storage for user-specific records; avoid duplicating documents into Action logs.

## Error Handling

```json
{
  "success": false,
  "error_code": "VALIDATION_ERROR",
  "message": "risk_zone must be Green, Yellow, or Red",
  "retryable": false,
  "request_id": "REQ-2026-001"
}
```

Do not claim success when the target rejects a write.

## Idempotency and Audit

Write endpoints accept `idempotency_key`. Record identity, operation ID, project/workflow, target system, payload hash or summary, confirmation time, result, error, created resource ID, and API/policy version.

## No-Auth Endpoint Catalog

| Method | Path | operationId | Purpose |
|---|---|---|---|
| GET | `/api/guardrails/templates` | `getGuardrailTemplates` | Return public template metadata |
| POST | `/api/guardrails/classify-task` | `classifyFundingWorkflowTask` | Classify a redacted abstract task |
| POST | `/api/guardrails/build-map` | `buildAnonymousGuardrailMap` | Generate a non-persistent map |
| POST | `/api/guardrails/score-readiness` | `scoreAnonymousWorkflowReadiness` | Calculate the 40-point score |
| POST | `/api/guardrails/validate-map` | `validateGuardrailMap` | Detect missing controls |
| POST | `/api/guardrails/generate-routing-preview` | `generateRoutingLogicPreview` | Create non-executable routing pseudocode |
| POST | `/api/guardrails/redact-preview` | `redactWorkflowDescription` | Detect and mask sensitive patterns |
| POST | `/api/guardrails/export-preview` | `createAnonymousGuardrailExport` | Create temporary export |

## API Key Endpoint Catalog

| Method | Path | operationId | Purpose |
|---|---|---|---|
| GET | `/api/policies/current` | `getCurrentGuardrailPolicyLibrary` | Return versioned policy templates |
| POST | `/api/policies/check` | `runGuardrailPolicyCheck` | Check map against rules |
| POST | `/api/claims/scan` | `scanFundingWorkflowLanguage` | Flag risky claims |
| POST | `/api/schemas/validate` | `validateGuardrailSchema` | Validate JSON, YAML, CSV, or fields |
| POST | `/api/n8n/spec` | `generateN8nGuardrailSpecification` | Generate disabled-draft specification |
| POST | `/api/crm/spec` | `generateCrmGuardrailSpecification` | Generate CRM routing |
| POST | `/api/exports/render` | `renderGuardrailArtifact` | Render artifacts |
| POST | `/api/evaluations/run` | `runWorkflowGuardrailEvaluation` | Run synthetic tests |

## OAuth Endpoint Catalog

| Method | Path | operationId | Purpose |
|---|---|---|---|
| GET | `/api/me/connections` | `listConnectedGuardrailSystems` | List approved connections |
| GET | `/api/projects` | `listGuardrailProjects` | List projects |
| POST | `/api/projects` | `createGuardrailProject` | Create project |
| GET | `/api/projects/{projectId}` | `getGuardrailProject` | Read project |
| PATCH | `/api/projects/{projectId}` | `updateGuardrailProject` | Update project |
| POST | `/api/projects/{projectId}/versions` | `createGuardrailProjectVersion` | Create snapshot |
| POST | `/api/review-queues/notion` | `createNotionHumanReviewQueue` | Create Notion queue |
| POST | `/api/review-queues/airtable` | `createAirtableHumanReviewBase` | Create Airtable base |
| POST | `/api/review-queues/crm` | `createCrmHumanReviewWorkflow` | Create CRM workflow |
| POST | `/api/exports/google-drive` | `exportGuardrailPackToGoogleDrive` | Save files to Drive |
| POST | `/api/n8n/workflows/draft` | `createN8nGuardrailWorkflowDraft` | Create disabled n8n draft |
| POST | `/api/audit-logs` | `appendHumanOverrideRecord` | Write override record |
| GET | `/api/audit-logs/summary` | `getGuardrailOverrideSummary` | Summarize overrides |
| POST | `/api/incidents` | `createGuardrailIncident` | Create incident |
| POST | `/api/notifications/reviewer` | `notifyAssignedHumanReviewer` | Send approved notification |

## No-Auth Request and Response

```json
{
  "task": "Draft a neutral missing-document reminder",
  "organization_role": "funding_broker",
  "data_classification": "synthetic",
  "workflow_stage": "Communications and Disclosures"
}
```

```json
{
  "risk_zone": "Green",
  "conditions": [
    "Use an approved neutral template",
    "Verify channel consent",
    "Do not include approval or funding-speed claims"
  ],
  "human_review_required": false,
  "review_triggers": ["complaint_received", "consent_disputed", "outcome_language_detected"]
}
```

## API Key Request and Response

```json
{
  "policy_version": "guardrails-1.0",
  "workflow_map": {
    "name": "Document Router",
    "tasks": [{"task": "Extract deposits", "risk_zone": "Yellow"}]
  }
}
```

```json
{
  "valid": false,
  "findings": [{
    "severity": "high",
    "control": "source_evidence",
    "message": "Yellow task lacks required source reference"
  }]
}
```

## OAuth Write Example

```json
{
  "idempotency_key": "IDEM-2026-001",
  "project_id": "PRJ-104",
  "target_connection_id": "CONN-NOTION-22",
  "confirmed": true,
  "queue_name": "Human Review Queue",
  "schema_version": "1.0"
}
```

```json
{
  "success": true,
  "resource_id": "NOTION-DB-REDACTED",
  "resource_type": "human_review_queue",
  "status": "created",
  "request_id": "REQ-2026-001"
}
```

## Action-to-Knowledge Mapping

| Action area | Knowledge file |
|---|---|
| Classification | `green-yellow-red-classifier.md` |
| Checkpoints | `eight-workflow-checkpoints.md` |
| Triggers | `exception-trigger-library.md` |
| Reviewer assignment | `reviewer-role-matrix.md` |
| Escalation | `escalation-paths.md` |
| Audit and override | `audit-log-schema.md`, `override-log-template.md` |
| QA scoring | `prelaunch-qa-scorecard.md` |
| n8n | `n8n-routing-patterns.md` |
| CRM and queues | `crm-routing-patterns.md`, `notion-airtable-review-queue.md` |
| Privacy | `data-privacy-and-redaction.md` |

## Recommended Rollout

1. GPT Instructions and Knowledge pack; no Actions.
2. Six No-Auth utilities: templates, classify, build map, score, validate, routing preview.
3. API Key policy checks, language scans, schema validation, rendering, and evaluations.
4. OAuth projects, review queues, disabled n8n drafts, Drive exports, audits, and incidents.

## Initial Minimum Viable Action Set

`getGuardrailTemplates`, `classifyFundingWorkflowTask`, `buildAnonymousGuardrailMap`, `scoreAnonymousWorkflowReadiness`, `validateGuardrailMap`, and `generateRoutingLogicPreview`.

## Related Knowledge Files

- `data-privacy-and-redaction.md`
- `n8n-routing-patterns.md`
- `crm-routing-patterns.md`

## Operational Summary

Use this file as operational guidance for designing human-in-the-loop funding workflows. It does not guarantee legal or regulatory compliance, replace an authorized decision-maker, or authorize AI to make unsupported binding decisions. When uncertainty, material impact, conflicting evidence, or authority questions exist, pause the affected workflow step and route the matter to a qualified human reviewer.
