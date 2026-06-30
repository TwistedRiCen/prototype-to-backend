---
name: prototype-to-backend
description: Use when converting HTML product prototypes, Axure HTML packages, online prototype URLs, PRDs, screenshots, or enterprise business mockups into backend-ready analysis, database, API, workflow, permission, task breakdown, and open-question artifacts.
---

# Prototype To Backend

## Overview

Use this skill to turn product prototypes and requirement materials into backend implementation artifacts. Focus on business meaning, data, APIs, workflows, permissions, validation, and delivery planning. Do not generate frontend code unless the user explicitly asks for it.

## Input Priority

Prefer source artifacts in this order:

1. Axure HTML package or other exported HTML prototype.
2. Online prototype URL with accessible pages, sitemap, notes, and interactions.
3. Product requirement document, user story, process document, or spreadsheet.
4. Screenshots only when richer artifacts are unavailable.

For Axure HTML packages, inspect the page tree, sitemap files, page titles, notes, interactions, visible text, form controls, table headers, buttons, and navigation before deriving backend artifacts.

## Working Rules

- Preserve Chinese business terms when analyzing Chinese enterprise systems, and add English technical names beside them, for example `采购申请 (PurchaseRequest)`.
- Separate confirmed facts, assumptions, and open questions. Never turn ambiguous prototype behavior into a definite rule.
- Put every uncertain business rule, missing field, missing permission, missing status, unclear workflow branch, or integration dependency into Open Questions.
- Prefer Spring Boot, REST, and SQL database friendly output when no stack is specified, but keep designs framework-agnostic unless the user names a stack.
- Use SQL Server compatible data types by default for database examples, unless the project clearly uses another database.
- Keep backend scope primary: no UI styling analysis, no frontend component code, no CSS, no page implementation.
- For large prototypes, analyze by module or batch and maintain a cumulative index of pages, entities, APIs, permissions, and open questions.

## Analysis Workflow

1. Inventory the input: list pages, modules, menus, forms, lists, dialogs, buttons, visible status labels, and referenced documents.
2. Extract backend signals: identify entities, identifiers, fields, search filters, table columns, actions, validations, state changes, workflow nodes, permissions, logs, and integration hints.
3. Build artifacts from evidence: map screens and actions to domain model, tables, APIs, state machine, workflow, permissions, and tasks.
4. Mark confidence: label each major rule as `Confirmed`, `Assumed`, or `Open Question`.
5. Generate outputs using the templates in `templates/`. Omit sections only when they are irrelevant, not when they are merely unknown.

## Required Output Set

Generate these files or sections unless the user asks for a narrower scope:

- `01-system-overview.md`: purpose, roles, module tree, menu tree, page inventory, capability map.
- `02-domain-model.md`: entities, aggregate roots, value objects, relationships, lifecycle, identifiers.
- `03-database-design.md`: tables, fields, SQL Server types, keys, indexes, constraints, audit fields, soft delete, dictionaries.
- `04-api-design.md`: REST APIs, DTOs, response VOs, permission codes, validation, transactions, idempotency.
- `05-state-machine.md`: statuses, actions, transitions, terminal states, rollback, revoke, reject rules.
- `06-workflow.md`: approval nodes, participants, actions, return/reject/revoke/transfer rules, variables, notifications.
- `07-permission-model.md`: menu, button, data permissions, roles, permission naming convention.
- `08-development-plan.md`: milestones, module tasks, entity/table tasks, API tasks, workflow tasks, tests, risk, priority.
- `09-open-questions.md`: unclear rules, missing fields/statuses/permissions/workflows, integrations, confirmation checklist.

## Extraction Checklist

Prioritize these signals:

| Signal | Backend interpretation |
| --- | --- |
| Menu item or page title | Module, capability, menu permission |
| Form field | Entity property, DTO field, validation rule |
| Search condition | Query API parameter, index candidate |
| Table column | List VO field, database field candidate |
| Button or link | Command API, permission point, state transition |
| Status label | State machine value, dictionary item |
| Approval action | Workflow transition and audit record |
| Required marker | Validation rule |
| Import/export button | Batch job, file template, async task, audit requirement |
| User/department selector | Organization scope, data permission, foreign key |

## Naming Conventions

- Entity class names: English PascalCase, preserving Chinese term in description.
- Table names: lowercase snake case, for example `purchase_request`.
- API paths: resource-oriented, for example `/api/purchase-requests/{id}/submit`.
- Permission codes: `module:resource:action`, for example `procurement:request:approve`.
- Status codes: uppercase snake case, for example `PENDING_APPROVAL`.

## Template Usage

Use the templates under `templates/` as the default structure. Keep evidence notes concise and practical. If a section cannot be completed from the prototype, write `Not confirmed` and add the item to `09-open-questions.md`.

## Quality Bar

Good output is specific enough for backend developers to start implementation, but honest about uncertainty. Every proposed table, API, workflow rule, and permission should trace back to observed prototype evidence, PRD text, or an explicitly marked assumption.
