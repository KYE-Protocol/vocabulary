# KYE™ Lifecycle States

Every KYE™ entity progresses through a defined set of states. This document lists state names recognized by KYE™.

State transition rules, atomicity requirements, and propagation behaviors are part of the normative specification and are not published in this repository.

## States

| State | Meaning |
|---|---|
| `discovered` | Entity has been discovered but not yet registered |
| `registered` | Entity has been registered with an immutable ID |
| `pending_verification` | Entity is awaiting verification |
| `verified` | Entity has been verified |
| `active` | Entity is active and may participate in governed actions |
| `limited` | Entity is operating under reduced scope |
| `under_review` | Entity is under review |
| `approval_required` | Entity actions require approval |
| `suspended` | Entity is suspended |
| `stopped` | Entity has been stopped |
| `quarantined` | Entity has been quarantined |
| `revoked` | Entity has been revoked |
| `transferred` | Entity has been transferred |
| `archived` | Entity has been archived |
| `tombstoned` | Entity is tombstoned and cannot be reactivated |

## High-level transition expectations

The full transition graph is normative and out of scope for this document. Two high-level expectations:

- A `tombstoned` entity has no outbound transitions.
- A `revoked` entity does not return directly to `active`; recovery requires an explicit re-registration or successor process.

The mechanisms enforcing these expectations are part of the normative specification.
