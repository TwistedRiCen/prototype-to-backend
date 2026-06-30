# Axure HTML Package Example

## Example User Prompt

Analyze the Axure HTML prototype package in `./prototype/采购管理系统/` and generate backend development artifacts. Focus on entities, tables, APIs, approval flows, permissions, and open questions. Do not generate frontend code.

## Recommended Agent Behavior

1. Inspect sitemap and page tree files first.
2. Extract page titles, menu hierarchy, notes, interactions, visible labels, form fields, table columns, and buttons.
3. Build a page inventory before deriving backend artifacts.
4. Process large prototypes module by module, for example `采购申请`, `供应商管理`, `采购订单`, `验收入库`.
5. Keep a cumulative index of pages, entities, APIs, permission points, and unresolved questions.

## Example Extracted Page Inventory

| Page title | Module | Backend signals |
| --- | --- | --- |
| 采购申请列表 (Purchase Request List) | Procurement Request | search filters: application no., applicant, department, status, date range; actions: create, view, submit, revoke |
| 采购申请详情 (Purchase Request Detail) | Procurement Request | entity fields, line items, attachments, approval history |
| 供应商档案 (Supplier Profile) | Supplier Management | supplier master data, qualification status, enabled flag |

## Example Derived Backend Artifacts

### Entity Candidates

| Chinese term | Technical name | Notes |
| --- | --- | --- |
| 采购申请 | PurchaseRequest | Aggregate root, contains request header and line items |
| 采购明细 | PurchaseRequestItem | Child entity for requested goods or services |
| 供应商 | Supplier | Master data, may require qualification workflow |

### API Candidates

| Method | Path | Purpose | Permission |
| --- | --- | --- | --- |
| GET | `/api/purchase-requests` | Search purchase requests | `procurement:request:view` |
| POST | `/api/purchase-requests` | Create draft request | `procurement:request:create` |
| POST | `/api/purchase-requests/{id}/submit` | Submit for approval | `procurement:request:submit` |

### Open Questions

- Are purchase request numbers generated before save or only after submission?
- Can the applicant edit a rejected request, or must they create a new one?
- Is supplier selection required during request creation or only during order creation?
- Are department data permissions based on applicant department or cost-bearing department?
