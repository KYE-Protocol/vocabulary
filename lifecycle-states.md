# KYE™ Lifecycle States

Every KYE Protocol™ entity carries a `state` field governed by a
registered state machine (see `public/vocabulary/state-machines.md`).
This document lists the **canonical state names** that the core KYE
vocabulary pre-defines.

State transition rules, guard evaluation, atomicity requirements, and
propagation behaviors are part of the normative specification and are
not published in this repository.

## State machine linkage

Each entity record holds three state-related fields:

| Field | Description |
|---|---|
| `state` | The current state value (one of the names below, or a custom name defined by the entity's machine) |
| `state_machine_id` | URN of the registered state machine governing this entity (e.g., `kye:sm:kyeprotocol.com:core.principal.v1`) |
| `state_machine_version` | Semver of the machine version in force |

The full state event log lives in the append-only `state_events` table.
See `public/vocabulary/state-machines.md` for the event record fields.

## States

| State | Stability class | Meaning |
|---|---|---|
| `discovered` | transient | Entity has been discovered but not yet registered |
| `registered` | transient | Entity has been registered with an immutable ID |
| `pending_verification` | transient | Entity is awaiting verification |
| `verified` | stable | Entity has been verified |
| `active` | stable | Entity is active and may participate in governed actions |
| `limited` | stable | Entity is operating under reduced scope |
| `under_review` | transient | Entity is under review |
| `approval_required` | transient | Entity actions require approval |
| `suspended` | stable | Entity is temporarily prevented from acting |
| `stopped` | stable | Entity has been stopped by a stop-cascade event |
| `quarantined` | stable | Entity has been quarantined pending investigation |
| `revoked` | stable | Entity has been revoked |
| `transferred` | terminal | Entity has been transferred to a new trust domain |
| `archived` | terminal | Entity has been archived |
| `tombstoned` | terminal | Entity is tombstoned and cannot be reactivated |

## Entity-class to state machine mapping

Each entity class links to its canonical state machine in the
KYE State Library™:

| Entity class | Default state machine ID |
|---|---|
| `tenant` | `kye:sm:kyeprotocol.com:core.tenant.v1` |
| `legal_entity` | `kye:sm:kyeprotocol.com:core.legal_entity.v1` |
| `billing_account` | `kye:sm:kyeprotocol.com:core.billing_account.v1` |
| `domain` | `kye:sm:kyeprotocol.com:core.domain.v1` |
| `policy_bundle` | `kye:sm:kyeprotocol.com:core.policy_bundle.v1` |
| `workspace` | `kye:sm:kyeprotocol.com:core.workspace.v1` |
| `project` | `kye:sm:kyeprotocol.com:core.project.v1` |
| `team` | `kye:sm:kyeprotocol.com:core.team.v1` |
| `resource` | `kye:sm:kyeprotocol.com:core.resource.v1` |
| `principal` | `kye:sm:kyeprotocol.com:core.principal.v1` |
| `model` | `kye:sm:kyeprotocol.com:lib.ai_governance.model.v1` |
| `tool` | `kye:sm:kyeprotocol.com:lib.ai_governance.tool.v1` |
| `external_app` | `kye:sm:kyeprotocol.com:core.external_app.v1` |
| `audit_stream` | `kye:sm:kyeprotocol.com:core.audit_stream.v1` |

Tenants may adopt sector-specific library machines or derive tightened
variants (see `public/vocabulary/state-library.md`).

## High-level transition expectations

The full transition graph is normative and out of scope for this document. Two high-level expectations:

- A `tombstoned` entity has no outbound transitions.
- A `revoked` entity does not return directly to `active`; recovery requires an explicit re-registration or successor process.

The mechanisms enforcing these expectations are part of the normative specification.
