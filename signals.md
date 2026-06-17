# KYE Protocol™ — Signal types: semantic vocabulary (v1)

> **Status:** Normative public surface. Apache 2.0.
> Companion to `public/vocabulary/signal-types.md` (full enumeration) and the
> private signal registry at `internal`.
>
> This document describes the **meaning** of each v3 signal type.
> Implementation internals (signing algorithms, PDP mechanics) are out of scope.

## What is a KYE Protocol™ signal?

A **signal** is an asynchronous, envelope-wrapped event emitted by a KYE Protocol™
system component whenever a governed state change occurs. Signals enable loosely-coupled
subscribers — partner systems, audit stores, compliance dashboards — to react to KYE
lifecycle events without polling.

Every signal envelope carries:

- a globally-unique `signal_id`
- a `signal_type` token from this vocabulary
- a `tenant_id` / `workspace_id` routing header
- a type-specific `payload` object
- an `idempotency_key` for at-least-once delivery safety
- a cryptographic `signature` binding the envelope to a verified emitter identity

## Signal type descriptions

### Entity lifecycle signals

**`entity.created`**
Emitted when a new KYE entity — organisation, agent, model, dataset, or other governed
class — is first registered in a trust domain. Subscribers receive the full entity
snapshot so they can initialise derived records without a follow-on read.

**`entity.updated`**
Emitted when one or more fields of an existing entity record are mutated. The payload
includes the post-mutation snapshot and a list of changed field paths, enabling
subscribers to apply targeted updates.

**`entity.deleted`**
Emitted when a KYE entity is hard-deleted or tombstoned. Downstream systems should
treat this as authoritative: any cached or derived data for the named entity MUST be
purged or marked inactive upon receipt.

### State signals

**`state.transitioned`**
Emitted by the State Engine when an entity successfully fires a transition in its
governing state machine. The payload names the machine, the before-state, the
after-state, the transition identifier, and any evidence artefacts that satisfied
the transition guards.

**`library.adopted`**
Emitted when a tenant binds a canonical State Library entry to their operating
environment, creating a tenant-specific state machine derivation. Indicates that the
tenant's entities governed by that machine are now subject to the library's transition
rules and evidence requirements.

### Decision signals

**`decision.admitted`**
Emitted when the policy decision point admits an action for a governed entity. Subscribers
may use this to track authorised activity for audit, billing, or telemetry purposes.

**`decision.denied`**
Emitted when the policy decision point denies an action. The payload includes structured
denial reasons and the policy references that caused the denial. Subscribers such as
SIEM exporters and the Drift Detector should act on this signal to identify anomalous
access patterns.

### Drift signal

**`drift.detected`**
Emitted when an entity's observed behaviour diverges from its declared operating model.
Drift categories include capability overreach, authority gaps, state inconsistencies,
policy violations, and identity mismatches. Severity is graded `low | medium | high | critical`.

### Evidence signal

**`evidence.sealed`**
Emitted when an evidence pack is cryptographically sealed and its integrity hash recorded.
The payload includes the pack identifier, its SHA-256 digest, and the key identifier of
the signing key. Subscribers may use this to verify pack integrity independently.

### Incident signals

**`incident.opened`**
Emitted when a new compliance or operational incident is opened. Carries a severity grade
and a list of implicated entity identifiers.

**`incident.closed`**
Emitted when an incident is resolved and closed. Carries the resolution summary and the
root-cause category to enable trend analysis.

### DSAR signals

**`dsar.requested`**
Emitted when a Data Subject Access Request (DSAR) is submitted by or on behalf of a data
subject. Subscribers should initiate the appropriate fulfilment workflow upon receipt.
Carries the request type (access, erasure, rectification, portability, restriction, objection)
and the statutory deadline.

**`dsar.fulfilled`**
Emitted when a DSAR is fully processed and the response dispatched to the data subject.
The outcome field distinguishes `fulfilled`, `partially_fulfilled`, and `refused` outcomes.

### Revocation signal

**`revocation.cascaded`**
Emitted by the Revocation Cascade Orchestrator once a root-entity revocation has been
propagated to all dependent entities (agents, connectors, delegations). The payload lists
every entity that was revoked as a consequence, enabling subscribers to update derived
authority records in a single atomic step.

### Compliance and audit signals

**`compliance_card.refreshed`**
Emitted whenever a tenant's compliance card is recalculated. The payload identifies the
card, its new version number, and the overall compliance status (`compliant`, `at_risk`,
or `non_compliant`).

**`audit_pack.assembled`**
Emitted when the Evidence Pack Assembler has compiled an audit pack from staged artefacts,
covering a defined time window. The pack is ready for sealing and external submission.

### Infrastructure signal

**`webhook.failed`** _(dead-letter)_
Emitted to the dead-letter queue when the Webhook Dispatcher has exhausted all delivery
retries for an outbound webhook. The payload records the original signal identifier,
the target subscriber, the number of attempts made, and the last error received. This
signal triggers human review and optional manual replay.

---

_KYE Protocol™ project, 2026. Apache 2.0._
