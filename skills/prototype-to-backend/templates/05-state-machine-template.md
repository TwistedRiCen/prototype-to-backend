# 05 状态机 / State Machine

## 状态归属 / State Owner

- 实体 / Entity:
- 中文状态字段 / Chinese status field:
- 技术状态字段 / Technical status field:
- 来源页面 / Source pages:

## 状态值 / Status Values

| 状态编码 / Status Code | 中文标签 / Chinese Label | 含义 / Meaning | 终态 / Terminal | 证据 / Evidence | 置信度 / Confidence |
| --- | --- | --- | --- | --- | --- |
| DRAFT | 草稿 | 提交前可编辑 / Editable before submission | No | 待填写 | Confirmed / Assumed |

## 动作 / Actions

| 动作 / Action | 中文标签 / Chinese Label | 操作人 / Actor | 前置条件 / Preconditions | 权限编码 / Permission Code | 来源按钮 / Source Button |
| --- | --- | --- | --- | --- | --- |
| submit | 提交 | 待填写 | 待填写 | 待填写 | 待填写 |

## 状态流转 / Transitions

| 原状态 / From | 动作 / Action | 目标状态 / To | 操作人 / Actor | 守卫规则 / Guard Rule | 副作用 / Side Effects | 待确认 / Open Question |
| --- | --- | --- | --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | 待填写 | 待填写 | 待填写 | 待填写 |

## 终态 / Terminal States

| 状态 / Status | 含义 / Meaning | 是否可重新打开 / Can Reopen | 备注 / Notes |
| --- | --- | --- | --- |
| 待填写 | 待填写 | Yes / No / Unknown | 待填写 |

## 回退、撤回、驳回规则 / Rollback, Revoke, Reject Rules

| 规则类型 / Rule Type | 允许来源状态 / Allowed From | 目标状态 / Target Status | 操作人 / Actor | 限制 / Constraints | 证据 / Evidence |
| --- | --- | --- | --- | --- | --- |
| Revoke | 待填写 | 待填写 | 待填写 | 待填写 | 待填写 |

## 状态校验清单 / State Validation Checklist

- 每个按钮是否都映射到了允许状态？
- 列表筛选项是否覆盖所有状态值？
- 驳回和退回是否语义不同？
- 终态是否禁止业务更新？
- 每次流转是否需要审计记录？

## 假设 / Assumptions

- 待填写

## 待确认问题 / Open Questions

- 待填写
