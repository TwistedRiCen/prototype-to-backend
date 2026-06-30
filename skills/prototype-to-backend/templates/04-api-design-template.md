# 04 API Design

## API Design Principles

- Prefer RESTful resource paths.
- Keep API names framework-agnostic unless a stack is specified.
- Include permission, validation, transaction, and idempotency notes for every command API.

## API List

| API | Method | Path | Purpose | Permission code | Transaction | Idempotency |
| --- | --- | --- | --- | --- | --- | --- |
| TBD | GET / POST / PUT / PATCH / DELETE | TBD | TBD | TBD | Yes / No | Required / Not required |

## API Detail: TBD

### Endpoint

- Method:
- Path:
- Purpose:
- Source page/action:
- Permission code:

### Request DTO

| Field | Type | Required | Validation | Description |
| --- | --- | --- | --- | --- |
| TBD | TBD | Yes / No | TBD | TBD |

### Response VO

| Field | Type | Description | Notes |
| --- | --- | --- | --- |
| TBD | TBD | TBD | TBD |

### Business Rules

- Confirmed:
- Assumed:

### Validation Rules

| Rule | Error case | Suggested error code | Evidence |
| --- | --- | --- | --- |
| TBD | TBD | TBD | TBD |

### Transaction Boundary

- Tables written:
- External calls:
- Rollback behavior:

### Exception Cases

| Case | Expected behavior | Error code | Open question? |
| --- | --- | --- | --- |
| TBD | TBD | TBD | Yes / No |

## Batch / Import / Export APIs

| API | File format | Async? | Template source | Error report |
| --- | --- | --- | --- | --- |
| TBD | XLSX / CSV / PDF / Other | Yes / No | TBD | TBD |

## Open Questions

- TBD
