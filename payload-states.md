# KYE Protocol™ — Payload artefact states

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the `action-admissibility` rule pack + `pep` profile and
> `internal`.
>
> A payload artefact carries **state** but never **authority**. The
> states below are the canonical values for the `state` field of the
> KYE Payload Artefact schema.

## 1. Lifecycle states

`created` — payload object instantiated by the actor; not yet signed.

`signed` — payload is in a state the Gateway will accept for verification.
Construction details are part of the patent track and not disclosed here.

`submitted` — sent by the actor to the Gateway.

`received` — the Gateway has the bytes.

`verified` — payload-trust checks completed; the payload is eligible
for adjudication. The specific checks are part of the patent track.

`bound_to_decision` — verified and adjudicated; the decision URN is
recorded on the artefact.

`executed` — the capability ran; the side-effect was committed.

`failed` — execution faulted after a successful decision binding.

`archived` — payload retained per retention policy; no further
mutation permitted.

## 2. Denial states

`rejected` — one of the verification checks failed; see `reason_code`
for which.

`expired` — receive time is past `expires_at`.

`replayed` — the payload-trust profile rejected this submission as
non-fresh.

`tampered` — the payload-trust profile rejected this submission for an
integrity violation.

## 3. Required deny reason codes

`payload_signature_missing` ·
`payload_signature_invalid` ·
`payload_hash_mismatch` ·
`payload_canonicalization_unsupported` ·
`payload_nonce_missing` ·
`payload_nonce_reused` ·
`payload_expired` ·
`payload_actor_mismatch` ·
`payload_capability_mismatch` ·
`payload_decision_binding_missing`

## 4. Required signal types

Every state transition MUST emit the corresponding signal:

| Transition | Signal type |
|---|---|
| `submitted → received` | `payload.received` |
| `received → verified` | `payload.verified` |
| `received → rejected` | `payload.rejected` |
| `verified → bound_to_decision` | `payload.bound_to_decision` |
| `bound_to_decision → executed` | `payload.executed` |
| `executed → failed` | `payload.failed` |
| `* → expired` | `payload.expired` |
| `* → replayed` | `payload.replay_detected` |
| `* → tampered` | `payload.tampered` |
| `* → archived` | `payload.archived` |

## 5. Use in copy

> **KYE governs acting entities, principal entities, capability
> entities, and evidence artefacts.** Payloads are *evidence
> artefacts* that bind signed requests to authority decisions and
> audit trails.
>
> KYE binds signed payloads to entity authority, capability state,
> policy decisions, and replayable audit evidence.

— KYE Protocol™ project, 2026.
