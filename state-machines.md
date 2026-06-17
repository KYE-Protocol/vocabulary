# KYE™ State Machine Vocabulary

Every KYE Protocol™ entity carries a `state` field governed by a registered
state machine. This document describes the **state model** in plain terms.

This document defines names and concepts only. The transition-guard
evaluation logic, evidence-class matching, and audit-chain construction
are part of the normative specification and are not published here.

## The state model

A **state machine** in KYE Protocol™ is a named, versioned, immutable
graph of states and transitions. Each machine:

- has a stable `state_machine_id` (a `kye:sm:…` URN)
- declares a set of **states** — each with a human label and a
  stability class (`transient`, `stable`, `terminal`)
- declares a set of **transitions** — each with a `from` state, a
  `to` state, and an **evidence class** that must be satisfied

An entity record holds:

- `state` — the current state value (string, from the machine's state set)
- `state_machine_id` — which machine governs this entity
- `state_machine_version` — the semver of the machine at adoption time

## State event log

Every transition appends a `state_event` record. The record is
append-only — it is never updated or deleted. Fields:

| Field | Description |
|---|---|
| `entity_id` | The entity that transitioned |
| `from_state` | State before the transition |
| `to_state` | State after the transition |
| `transition_id` | Identifies the declared transition in the machine |
| `triggered_by` | The principal or system that triggered the event |
| `evidence_ref` | Reference to the evidence pack or decision record that satisfied the guard |
| `recorded_at` | ISO 8601 timestamp (UTC) |

## Stability classes

| Class | Meaning |
|---|---|
| `transient` | Short-lived; the machine expects the entity to leave this state quickly (e.g., `pending_verification`) |
| `stable` | Normal operating state (e.g., `active`, `limited`) |
| `terminal` | No outbound transitions (e.g., `tombstoned`) |

## Common state names

The following names are pre-defined in the KYE Protocol™ core vocabulary.
State machines MAY use any subset and MAY add custom states via derivation.

| State | Stability class | Meaning |
|---|---|---|
| `discovered` | transient | Entity seen but not yet registered |
| `registered` | transient | Registered with an immutable ID; pending first verification |
| `pending_verification` | transient | Awaiting evidence to advance |
| `verified` | stable | Verification satisfied |
| `active` | stable | Participating in governed actions |
| `limited` | stable | Operating under reduced scope |
| `under_review` | transient | Review in progress |
| `approval_required` | transient | Actions require explicit approval |
| `suspended` | stable | Temporarily prevented from acting |
| `stopped` | stable | Prevented from acting by a stop-cascade event |
| `quarantined` | stable | Isolated pending investigation |
| `revoked` | stable | Authority removed; recovery requires explicit process |
| `transferred` | terminal | Ownership or trust domain changed |
| `archived` | terminal | Retained for audit; no active participation |
| `tombstoned` | terminal | Permanently deactivated; no outbound transitions |

## Machine identity convention

State machine IDs follow the pattern:

```
kye:sm:<trust-domain>:<name>.<entity-class>.<major>
```

Examples:

```
kye:sm:kyeprotocol.com:core.principal.v1
kye:sm:kyeprotocol.com:core.workspace.v1
kye:sm:kyeprotocol.com:lib.banking.account.v1
kye:sm:acme.example:derived.principal.v1
```

The `core.*` machines are published by KYE Protocol™ and available in
the KYE State Library™. Tenant-derived machines use the tenant's trust
domain and record `parent_machine_id` pointing to the library entry they
derived from.

## What this document does not specify

- the algorithm that evaluates evidence-class guards
- the signing or integrity mechanism for state events
- the cross-entity propagation rules when a parent state changes
- the recovery process after `revoked` or `stopped`

Those are part of the normative specification.
