# Procurement System Example

## Scenario

The product materials include a procurement system prototype covering purchase requests, purchase orders, supplier management, receiving, invoice matching, and payment request approval.

## Example Capability Map

| Capability | Pages | Backend operations | Entities |
| --- | --- | --- | --- |
| Purchase request management | 采购申请列表, 采购申请详情 | create, edit, submit, approve, reject, revoke | PurchaseRequest, PurchaseRequestItem |
| Supplier management | 供应商列表, 供应商档案 | create, qualify, enable, disable | Supplier, SupplierQualification |
| Purchase order management | 采购订单列表, 采购订单详情 | generate order, confirm, close | PurchaseOrder, PurchaseOrderItem |
| Receiving | 验收入库 | receive goods, partial receive, reject goods | GoodsReceipt, GoodsReceiptItem |

## Example Database Tables

| Table | Purpose | Notes |
| --- | --- | --- |
| purchase_request | Request header | Includes applicant, department, status, total amount |
| purchase_request_item | Request line items | Item name, specification, quantity, estimated price |
| supplier | Supplier master data | Qualification status and enabled flag |
| purchase_order | Purchase order header | Links supplier and purchase request |
| goods_receipt | Receiving header | Supports partial receiving if confirmed |

## Example API Design Excerpt

| Method | Path | Purpose | Transaction | Idempotency |
| --- | --- | --- | --- | --- |
| POST | `/api/purchase-requests` | Create purchase request draft | Yes | Not required |
| POST | `/api/purchase-requests/{id}/submit` | Submit approval | Yes | Required |
| POST | `/api/purchase-orders/generate` | Generate purchase order from approved request | Yes | Required |
| POST | `/api/goods-receipts` | Create receiving record | Yes | Required |

## Example Permission Points

| Action | Permission code | Data scope |
| --- | --- | --- |
| View purchase requests | `procurement:request:view` | Own / Department / All |
| Approve purchase requests | `procurement:request:approve` | Assigned workflow tasks |
| Maintain suppliers | `procurement:supplier:manage` | All |
| Confirm receiving | `procurement:receipt:create` | Warehouse or assigned receiver |

## Example Open Questions

- Can one purchase request generate multiple purchase orders by supplier?
- Is partial receiving allowed for all purchase orders?
- Does invoice matching belong to this system or a finance system?
- What is the exact rule for supplier qualification expiration?
- Are prices tax-inclusive or tax-exclusive?
