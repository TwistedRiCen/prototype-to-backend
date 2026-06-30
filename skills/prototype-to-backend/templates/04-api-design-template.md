# 04 接口设计 / API Design

## 接口设计原则 / API Design Principles

- 优先使用 RESTful resource paths.
- 未指定技术栈时保持框架无关 / Keep framework-agnostic unless a stack is specified.
- 每个命令类接口都要说明权限、校验、事务和幂等要求。

## 接口清单 / API List

| 接口 / API | 方法 / Method | 路径 / Path | 用途 / Purpose | 权限编码 / Permission Code | 事务 / Transaction | 幂等 / Idempotency |
| --- | --- | --- | --- | --- | --- | --- |
| 待填写 | GET / POST / PUT / PATCH / DELETE | 待填写 | 待填写 | 待填写 | Yes / No | Required / Not required |

## 接口详情 / API Detail: 待填写

### Endpoint

- 方法 / Method:
- 路径 / Path:
- 用途 / Purpose:
- 来源页面/动作 / Source page or action:
- 权限编码 / Permission code:

### 请求 DTO / Request DTO

| 字段 / Field | 类型 / Type | 必填 / Required | 校验规则 / Validation | 说明 / Description |
| --- | --- | --- | --- | --- |
| 待填写 | 待填写 | Yes / No | 待填写 | 待填写 |

### 响应 VO / Response VO

| 字段 / Field | 类型 / Type | 说明 / Description | 备注 / Notes |
| --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | 待填写 |

### 业务规则 / Business Rules

- 已确认 / Confirmed:
- 假设 / Assumed:

### 校验规则 / Validation Rules

| 规则 / Rule | 错误场景 / Error Case | 建议错误码 / Suggested Error Code | 证据 / Evidence |
| --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | 待填写 |

### 事务边界 / Transaction Boundary

- 写入表 / Tables written:
- 外部调用 / External calls:
- 回滚行为 / Rollback behavior:

### 异常场景 / Exception Cases

| 场景 / Case | 期望行为 / Expected Behavior | 错误码 / Error Code | 是否待确认 / Open Question |
| --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | Yes / No |

## 批量、导入、导出接口 / Batch, Import, Export APIs

| 接口 / API | 文件格式 / File Format | 异步 / Async | 模板来源 / Template Source | 错误报告 / Error Report |
| --- | --- | --- | --- | --- |
| 待填写 | XLSX / CSV / PDF / Other | Yes / No | 待填写 | 待填写 |

## 待确认问题 / Open Questions

- 待填写
