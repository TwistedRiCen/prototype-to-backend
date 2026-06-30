# OA Approval Example

## Scenario

The prototype describes an OA leave approval process with pages for leave application, pending approvals, approval history, and leave statistics.

## Example System Overview Excerpt

| Role | Chinese term | Responsibilities |
| --- | --- | --- |
| Employee | 员工 | Create, edit, submit, and revoke own leave requests |
| Department Manager | 部门经理 | Approve or reject department leave requests |
| HR Specialist | 人事专员 | Review records and export leave statistics |

## Example Domain Model Excerpt

| Chinese term | Technical name | Type | Notes |
| --- | --- | --- | --- |
| 请假申请 | LeaveRequest | Aggregate Root | Header record for one leave request |
| 请假类型 | LeaveType | Dictionary | Annual leave, sick leave, personal leave |
| 审批记录 | ApprovalRecord | Entity | Stores node, action, approver, comment, time |

## Example State Machine Excerpt

| From | Action | To | Actor | Guard rule |
| --- | --- | --- | --- | --- |
| DRAFT | submit | PENDING_MANAGER_APPROVAL | Employee | Required fields and leave balance must pass validation |
| PENDING_MANAGER_APPROVAL | approve | APPROVED | Department Manager | Approver must be assigned to applicant department |
| PENDING_MANAGER_APPROVAL | reject | REJECTED | Department Manager | Reject comment may be required, not confirmed |
| PENDING_MANAGER_APPROVAL | revoke | REVOKED | Employee | Revoke before final approval, not confirmed |

## Example Workflow Excerpt

| Node | Participant | Actions | Open question |
| --- | --- | --- | --- |
| Submit | Applicant | Submit, save draft | Can applicant choose approver manually? |
| Manager Approval | Department manager | Approve, reject, return | Is return different from reject? |
| HR Record | HR specialist or system | Archive, export | Is HR approval required or only record keeping? |

## Example Open Questions

- Is leave balance validated in this system or through an external HR system?
- Does sick leave require an attachment?
- Are weekends and public holidays excluded automatically?
- Is approval required for cancellation after the leave request is approved?
