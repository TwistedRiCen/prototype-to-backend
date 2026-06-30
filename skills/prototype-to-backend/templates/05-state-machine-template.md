# 05 State Machine

## State Owner

- Entity:
- Chinese status field:
- Technical status field:
- Source pages:

## Status Values

| Status code | Chinese label | Meaning | Terminal | Evidence | Confidence |
| --- | --- | --- | --- | --- | --- |
| DRAFT | 草稿 | Editable before submission | No | TBD | Confirmed / Assumed |

## Actions

| Action | Chinese label | Actor | Preconditions | Permission code | Source button |
| --- | --- | --- | --- | --- | --- |
| submit | 提交 | TBD | TBD | TBD | TBD |

## Transitions

| From | Action | To | Actor | Guard rule | Side effects | Open question |
| --- | --- | --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | TBD | TBD | TBD |

## Terminal States

| Status | Meaning | Can reopen? | Notes |
| --- | --- | --- | --- |
| TBD | TBD | Yes / No / Unknown | TBD |

## Rollback / Revoke / Reject Rules

| Rule type | Allowed from | Target status | Actor | Constraints | Evidence |
| --- | --- | --- | --- | --- | --- |
| Revoke | TBD | TBD | TBD | TBD | TBD |

## State Validation Checklist

- Is every button mapped to an allowed status?
- Are list filters consistent with status values?
- Are rejected and revoked states distinct?
- Are terminal states protected from updates?
- Are audit records required for every transition?

## Assumptions

- TBD

## Open Questions

- TBD
