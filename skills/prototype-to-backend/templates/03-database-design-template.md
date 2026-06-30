# 03 数据库设计 / Database Design

## 数据库假设 / Database Assumption

- 默认目标 / Default target: SQL Server compatible relational database.
- 如果项目使用其他数据库，请同步调整字段类型、索引和分页语法。

## 表清单 / Table List

| 表名 / Table | 中文名 / Chinese Name | 用途 / Purpose | 主实体 / Main Entity | 备注 / Notes |
| --- | --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | 待填写 | 待填写 |

## 表 / Table: 待填写

### 字段 / Columns

| 字段名 / Column | SQL Server 类型 / Type | 可空 / Nullable | 默认值 / Default | 键 / Key | 说明 / Description | 来源字段 / Source Field |
| --- | --- | --- | --- | --- | --- | --- |
| id | BIGINT | No | identity | PK | 主键 / Primary key | System |
| created_at | DATETIME2(3) | No | SYSUTCDATETIME() |  | 创建时间 / Creation time | System |
| updated_at | DATETIME2(3) | No | SYSUTCDATETIME() |  | 更新时间 / Last update time | System |
| deleted | BIT | No | 0 |  | 软删除标记 / Soft delete flag | System |

### 主键、外键与约束 / Keys And Constraints

| 名称 / Name | 类型 / Type | 字段 / Columns | 规则 / Rule | 备注 / Notes |
| --- | --- | --- | --- | --- |
| 待填写 | PK / FK / UNIQUE / CHECK | 待填写 | 待填写 | 待填写 |

### 索引 / Indexes

| 索引名 / Index | 字段 / Columns | 唯一 / Unique | 原因 / Reason | 来源 / Source |
| --- | --- | --- | --- | --- |
| 待填写 | 待填写 | Yes / No | Search / join / unique lookup | 待填写 |

## 通用审计字段 / Common Audit Fields

| 字段 / Field | SQL Server 类型 / Type | 是否建议 / Recommended | 备注 / Notes |
| --- | --- | --- | --- |
| created_by | BIGINT | Yes | 创建人用户ID / Creator user id |
| created_at | DATETIME2(3) | Yes | 创建时间 / Creation time |
| updated_by | BIGINT | Yes | 最后更新人用户ID / Last updater user id |
| updated_at | DATETIME2(3) | Yes | 最后更新时间 / Last update time |
| deleted | BIT | Yes | 软删除标记 / Soft delete flag |
| tenant_id | BIGINT | Optional | 多租户场景使用 / Use when multi-tenant |

## 字典表 / Dictionary Tables

| 字典编码 / Dictionary Code | 表/存储方式 / Table or Storage | 取值 / Values | 维护方 / Maintainer | 备注 / Notes |
| --- | --- | --- | --- | --- |
| 待填写 | 待填写 | 待填写 | System / Admin | 待填写 |

## 数据迁移说明 / Data Migration Notes

- 现有数据影响 / Existing data impact:
- 数据回填要求 / Backfill requirements:
- 回滚考虑 / Rollback considerations:

## 假设 / Assumptions

- 待填写

## 待确认问题 / Open Questions

- 待填写
