# Funding Workflow Guardrail Builder Knowledge Pack

Version: 1.0  
Last updated: 2026-07-15

## Purpose

This pack contains 20 production-ready Markdown Knowledge files for the Funding Workflow Guardrail Builder Custom GPT.

## Recommended Upload Order

Upload files 1–20 in numerical order. Keep behavioral rules, Action confirmation requirements, and the core operating instructions in the GPT Instructions. Use these files as reference Knowledge.

## File List

| # | File | Category | Purpose |
|---:|---|---|---|
| 1 | `product-overview.md` | Core | Product role, users, modes, inputs, outputs, and limitations |
| 2 | `human-review-checkpoint-map.md` | Core | Master human-in-the-loop framework |
| 3 | `green-yellow-red-classifier.md` | Core | Task risk-classification method and examples |
| 4 | `eight-workflow-checkpoints.md` | Core | Detailed checkpoint controls |
| 5 | `exception-trigger-library.md` | Core | Pause and escalation trigger catalog |
| 6 | `reviewer-role-matrix.md` | Core | Reviewer roles, authority, and assignments |
| 7 | `escalation-paths.md` | Core | Exception and incident escalation routes |
| 8 | `audit-log-schema.md` | Core | Audit evidence and field schema |
| 9 | `override-log-template.md` | Core | Human override documentation |
| 10 | `forbidden-actions.md` | Core | Autonomous-action prohibitions |
| 11 | `prelaunch-qa-scorecard.md` | Core | 40-point readiness score |
| 12 | `safe-language-and-disclaimers.md` | Core | Safe wording and limitations |
| 13 | `n8n-routing-patterns.md` | Implementation | n8n workflow design patterns |
| 14 | `crm-routing-patterns.md` | Implementation | CRM stages, fields, and routing |
| 15 | `notion-airtable-review-queue.md` | Implementation | Notion and Airtable queue designs |
| 16 | `workflow-output-templates.md` | Implementation | Reusable output formats |
| 17 | `example-funding-workflows.md` | Implementation | Twelve synthetic workflow examples |
| 18 | `workflow-test-cases.md` | Implementation | Evaluation and failure test suite |
| 19 | `data-privacy-and-redaction.md` | Implementation | Sensitive-data handling and redaction |
| 20 | `action-endpoints.md` | Implementation | Proposed Action catalog and contracts |

## Upload Instructions

1. Open the Custom GPT editor.
2. Confirm the GPT Instructions contain the product role and safety boundaries.
3. Upload the 20 Markdown files in the listed order.
4. Do not upload `README.md`, `knowledge-pack-manifest.json`, or `validation-report.json` as Knowledge unless you need administration context.
5. Test with synthetic workflows before any live use.
6. Verify the GPT cites source evidence, distinguishes brokers from creditors, and stops Red actions.

## Version Information

- Product version: 1.0
- Knowledge status: production-ready
- Core terminology: Green, Yellow, Red; eight human checkpoints; 40-point QA score

## Safety Note

This pack provides educational and operational guidance only. It does not provide legal, lending, underwriting, tax, accounting, or compliance advice and does not guarantee approval, funding, timing, or regulatory compliance.

## Replacing Older Versions

1. Archive the current pack.
2. Review the new manifest and change summary.
3. Remove superseded Knowledge files.
4. Upload replacement files.
5. Test classifications, triggers, outputs, and Actions.
6. Record the active Knowledge version.
