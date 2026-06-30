# 03 Database Design

## Database Assumption

- Default target: SQL Server compatible relational database.
- If the project uses another database, adjust types and indexes accordingly.

## Table List

| Table | Chinese name | Purpose | Main entity | Notes |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | TBD |

## Table: TBD

### Columns

| Column | SQL Server type | Nullable | Default | Key | Description | Source field |
| --- | --- | --- | --- | --- | --- | --- |
| id | BIGINT | No | identity | PK | Primary key | System |
| created_at | DATETIME2(3) | No | SYSUTCDATETIME() |  | Creation time | System |
| updated_at | DATETIME2(3) | No | SYSUTCDATETIME() |  | Last update time | System |
| deleted | BIT | No | 0 |  | Soft delete flag | System |

### Keys And Constraints

| Name | Type | Columns | Rule | Notes |
| --- | --- | --- | --- | --- |
| TBD | PK / FK / UNIQUE / CHECK | TBD | TBD | TBD |

### Indexes

| Index | Columns | Unique | Reason | Source |
| --- | --- | --- | --- | --- |
| TBD | TBD | Yes / No | Search / join / unique lookup | TBD |

## Common Audit Fields

| Field | SQL Server type | Required | Notes |
| --- | --- | --- | --- |
| created_by | BIGINT | Recommended | Creator user id |
| created_at | DATETIME2(3) | Recommended | Creation time |
| updated_by | BIGINT | Recommended | Last updater user id |
| updated_at | DATETIME2(3) | Recommended | Last update time |
| deleted | BIT | Recommended | Soft delete flag |
| tenant_id | BIGINT | Optional | Use when multi-tenant |

## Dictionary Tables

| Dictionary code | Table / storage | Values | Maintainer | Notes |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | System / Admin | TBD |

## Data Migration Notes

- Existing data impact:
- Backfill requirements:
- Rollback considerations:

## Assumptions

- TBD

## Open Questions

- TBD
