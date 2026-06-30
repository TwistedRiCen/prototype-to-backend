# Design Review Example

## Scenario

The generated backend artifacts describe a Chinese procurement approval system with purchase requests, suppliers, purchase orders, receiving, and invoice matching. The initial design includes entities, SQL Server tables, REST APIs, approval flow, state machine, permissions, and open questions.

This example shows how the built-in grill-me style review should challenge the generated design instead of summarizing it.

## Example Review Summary

- Overall readiness: Medium. The core procurement request flow is visible, but several backend rules are not complete enough for implementation.
- Major risks: Missing command APIs, weak line-item table constraints, incomplete approval closure, incomplete revoke/reject transitions, and missing data-scope permissions.
- Blocking questions: Whether partial receiving is allowed, whether rejected requests can be edited and resubmitted, and whether purchase orders can split by supplier.
- Recommended next step: Resolve blocking product questions, then update API, database, workflow, state machine, and permission artifacts before development starts.

## API Completeness Review

| Issue | Why It Matters | Recommendation | Severity |
|---|---|---|---|
| Missing API for resubmitting a rejected purchase request. | The state machine includes `REJECTED`, but developers cannot implement the recovery path without a command endpoint and validation rules. | Add `POST /api/purchase-requests/{id}/resubmit` or define that `submit` supports both `DRAFT` and `REJECTED`; document request DTO, permission, transaction boundary, and audit event. | High |
| Import/export behavior is only listed as a button, not as backend APIs. | Import tasks need file validation, error reporting, async processing, idempotency, and audit logging. A button alone is not implementable. | Add import template download, upload, validation result, async task query, and export APIs; include file format and error report rules. | Medium |

## Database Design Review

| Issue | Why It Matters | Recommendation | Severity |
|---|---|---|---|
| `purchase_request_item` lacks line number and uniqueness constraints. | Duplicate or unstable line ordering can break approval snapshots, order generation, receiving, and audit comparison. | Add `line_no INT NOT NULL`, unique constraint `(purchase_request_id, line_no)`, and preserve line snapshots after submission. | High |
| Supplier data is referenced directly by id without snapshot fields. | Supplier names, tax numbers, and bank accounts may change after order creation, causing historical purchase orders to display changed data. | Add supplier snapshot fields on purchase order or introduce versioned supplier profile records. | Medium |

## Workflow and Approval Review

| Issue | Why It Matters | Recommendation | Severity |
|---|---|---|---|
| Approval flow does not define what happens after rejection. | Without closure rules, backend implementation may inconsistently allow edit, resubmit, archive, or delete. | Define whether rejection returns to applicant for edit, ends the process, or creates a new version. Put unresolved choice in Open Questions. | Blocking |
| Transfer and return actions are mentioned but not scoped by node. | Workflow engines need node-level rules to validate who can transfer, where a return can go, and whether comments are required. | Add node-specific action matrix for approve, reject, return, revoke, and transfer. | High |

## State Machine Review

| Issue | Why It Matters | Recommendation | Severity |
|---|---|---|---|
| Revoke rules are missing for `PENDING_APPROVAL`. | Users may see a revoke button, but backend behavior can be unsafe if approval is already being processed concurrently. | Define allowed revoke statuses, optimistic lock checks, target status, audit record, and notification behavior. | High |
| Reject and return are not clearly separated. | These actions often have different business meaning and different next statuses. Mixing them creates reporting and workflow bugs. | Define separate transitions, for example `PENDING_APPROVAL -> REJECTED` and `PENDING_APPROVAL -> RETURNED`, or confirm that only one action exists. | Medium |

## Permission and Data Scope Review

| Issue | Why It Matters | Recommendation | Severity |
|---|---|---|---|
| Approval permission is defined as a broad button permission only. | A user with the button permission might approve records not assigned to them if data scope is not enforced. | Combine `procurement:request:approve` with workflow task ownership checks and department/tenant data scope. | Blocking |
| Export permission is missing. | Export often exposes bulk business data and should not be inherited from view permission by accident. | Add `procurement:request:export` and define export data scope, masking rules, and audit logging. | Medium |

## Recommended Fix Checklist

| Task | Related Artifact | Priority | Owner |
|---|---|---|---|
| Add resubmit, revoke, import, export, and approval-history APIs. | `04-api-design.md` | P0 | Backend |
| Add line-level constraints and supplier snapshot/versioning strategy. | `03-database-design.md` | P0 | Backend / DBA |
| Close rejection, return, revoke, and transfer workflow branches. | `05-state-machine.md`, `06-workflow.md` | P0 | Product / Backend |
| Split button permission from workflow task ownership and data scope. | `07-permission-model.md` | P0 | Backend |
| Move unresolved product decisions into Open Questions. | `09-open-questions.md` | P0 | Product |
