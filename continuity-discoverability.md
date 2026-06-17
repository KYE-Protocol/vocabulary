# KYE™ Continuity + Discoverability vocabulary

Names introduced by **KYE Continuity Profile™** (`kye-continuity-v1`) and
**KYE Discoverability Profile™** (`kye-discoverability-v1`). This document
lists names only. Detection algorithms, scoring weights, thresholds, and
graph-traversal mechanisms are part of the normative specification and the
patent track, and are not published here.

## KYE Continuity Profile™

### Continuity decision values

| Value | Meaning |
|---|---|
| `continuity_preserved` | Interpreted intent matches declared intent; authority + state + scope intact; no material drift detected. |
| `continuity_degraded` | One or more dimensions show drift; action proceeds with constraints + obligation list. |
| `continuity_broken` | Material drift on at least one dimension; action MUST NOT proceed without re-anchoring. |

The companion `continuity_score` is a numeric in `[0, 1]`. The mapping from
score to decision value is part of the normative specification.

### Drift types

Ten named drift categories. Detection rules are not published.

| Name | Surface |
|---|---|
| `intent_drift` | Interpreted goal diverges from declared goal. |
| `authority_drift` | Authority record at decision time differs from authority at delegation time. |
| `scope_drift` | Action lies outside intersected scope along the chain. |
| `state_drift` | Authority / principal / actor state changed since grant. |
| `capability_drift` | Capability invoked is not the capability granted. |
| `execution_drift` | Runtime behaviour diverges from declared plan. |
| `incentive_drift` | Pressure / incentive context conflicts with declared intent. |
| `oversight_drift` | Required oversight chain is missing or stale. |
| `evidence_drift` | Evidence references are missing, mutated, or unverifiable. |
| `delegation_drift` | Delegation chain has been broken, attenuated past tolerance, or re-rooted. |

### Reason codes (continuity)

Continuity-status reason codes are listed in `reason-codes.md` under the
**Continuity** group. Names follow the `<dimension>_drift_detected`
convention (e.g., `intent_drift_detected`, `scope_drift_detected`).

### Required objects

| Object | Role |
|---|---|
| `KYEContinuityDecision` | The signed continuity verdict for a single decision point. |
| `KYEAgencyDriftEvent` | One record per detected drift; hash-chained into the audit ledger. |
| `Continuity Decision Map™` | The replayable artefact bound to a continuity decision. |
| `Continuity Evidence Pack™` | Signed bundle composing intent + interpretation + state + pressure + incentive + decision + execution + drift events. |

### Continuity signals

`kye.intent.declared`, `kye.intent.drift_detected`,
`kye.agency_drift.detected`, `kye.agency_drift.review_required`,
`kye.agency_drift.resolved`, `kye.agency_drift.quarantined`.

## KYE Discoverability Profile™

### Discovery modes

| Mode | Surface |
|---|---|
| `directory_lookup` | Resolve a known KYE URN to its current authority record + state. |
| `path_finder` | Find the delegation path(s) from a principal to an actor for a capability. |
| `graph_walk` | Traverse the authority graph under a discovery policy with row-level masking. |
| `risk_discovery` | Non-mutating traversal returning the *would-result* set for a candidate action (stale / over-permissioned / pre-revocation blast radius). |
| `connector_discovery` | Locate Connector Profile™ implementations + their conformance state. |
| `evidence_finder` | Resolve audit-event + evidence-pack pointers bound to a decision. |

### Risk discovery types

| Type | Returns |
|---|---|
| `stale` | Authority records that have not been exercised within a profile-defined window. |
| `over_permissioned` | Authority records whose granted scope materially exceeds observed exercise. |
| `pre_revocation_blast_radius` | The downstream set that *would* be quarantined if a target authority were revoked. |

The detection windows, scoring weights, and side-effect-level thresholds are
part of the normative specification.

### Required objects

| Object | Role |
|---|---|
| `KYE Authority Directory™` | The directory index of cryptographically-bound authority records. |
| `KYE Discovery Console™` | The operator surface over the directory + path finder + risk discovery. |
| `KYE Authority Path Finder™` | The path-resolution engine over the authority graph. |
| `KYE Evidence Finder™` | The resolver over audit-event + evidence-pack indexes. |
| `KYE Connector Discovery Hub™` | The discovery surface for Connector Profile™ implementations. |

### Reason codes (discovery)

Discovery reason codes are listed in `reason-codes.md` under the
**Discovery** group. Names follow the `discovery_<mode>_<outcome>`
convention.

### Discovery signals

`kye.discovery.queried`, `kye.discovery.masked`,
`kye.discovery.federation_traversed`, `kye.discovery.policy_denied`,
`kye.risk.stale_detected`, `kye.risk.over_permissioned_detected`,
`kye.risk.blast_radius_computed`.

## Cross-profile composition

KYE Continuity Profile™ and KYE Discoverability Profile™ MAY compose with
any KYE Connector Profile™. The profiles do not redefine identity, scope
attenuation, or audit-chain semantics; they extend the runtime decision
surface and the discovery surface respectively.

## Patent-safe boundary

Algorithm content for drift detection, score computation, blast-radius
traversal, intent-interpretation binding, and pre-revocation pruning is
**not** in this repository. See the public landing pages for the profile
overviews; counsel-controlled material remains private.
