# KYE™ Operating Model vocabulary

Names introduced by **KYE Operating Model Profile™**
(`kye-operating-model-v1`) — the enterprise adoption layer of KYE™.
This document lists names only. Readiness scoring engine, risk-tiering
heuristics, side-effect classification, commit-boundary detection,
authority-gate recommendation and runtime enforcement internals are part
of the normative specification and the patent track, and are not
published here.

> **KYE™ turns AI-governance operating models into runtime authority
> decisions and replayable evidence.**

## Journey stages

Ten ordered stages every operating-model implementation enforces.

`intake` · `assess` · `classify` · `map_authority` · `place_gates` ·
`configure_runtime` · `execute` · `evidence` · `review` · `improve`.

## Required objects

| Object | Schema |
|---|---|
| Profile descriptor | `operating-model-profile.json` |
| Use-case intake | `use-case-intake.json` |
| Readiness assessment | `readiness-assessment.json` |
| Entity Authority Record™ | `entity-authority-record.json` |
| Authority Gate™ | `authority-gate.json` |
| Commit Boundary™ | `commit-boundary.json` |
| Review path | `review-path.json` |
| Training record | `training-record.json` |
| Adoption evidence pack | `adoption-evidence-pack.json` |
| Governed catalogue entry | `governed-catalog-entry.json` |

## Authority-gate types

Eight named types. Implementations MAY add `custom`.

| Type | Surface |
|---|---|
| `payment_execution`         | Before a prepared payment becomes an executed payment. |
| `external_message`          | Before an outbound message (email, customer-facing notification, signal handler) leaves the tenant. |
| `contract_signature`        | Before a contract / e-signature is sealed. |
| `clinical_action`           | Before a clinical action is performed (orders, escalations, triage). |
| `infrastructure_command`    | Before an infrastructure command is issued (deploy, rotate, terminate). |
| `data_export`               | Before a data export leaves the tenant. |
| `credential_rotation`       | Before a credential is rotated. |
| `evidence_export`           | Before an evidence pack is exported beyond the tenant. |
| `data_access`               | Before sensitive data is read. |
| `custom`                    | Implementer-defined gate. |

## Commit-boundary archetypes

| Before the boundary | After the boundary |
|---|---|
| `draft email`            | `send email` |
| `payment.prepare`        | `payment.execute` |
| `recommend refund`       | `issue refund` |
| `draft contract`         | `sign contract` |
| `suggest clinical step`  | `perform clinical step` |
| `plan infrastructure change` | `execute infrastructure command` |
| `recommend access grant` | `issue access grant` |
| `propose policy edit`    | `apply policy edit` |

## Decision policy values

`allow` · `deny` · `require_approval` · `require_step_up` ·
`quarantine`.

## Risk tiers

`low` · `medium` · `high` · `critical`.

## Lifecycle states

`proposed` · `pilot` · `controlled_production` · `production` ·
`deprecated` · `suspended` · `revoked`.

## Reason codes

See `reason-codes.md` under the **Operating Model profile reason codes**
group (19 codes).

## Operating-model signals

See `kye-operating-model-v1.md` §6. Five families: use-case lifecycle,
readiness lifecycle, authority-record lifecycle, authority-gate
lifecycle, commit-boundary lifecycle, and catalogue lifecycle.

## Patent-safe boundary

The readiness-scoring algorithm, risk-tier classification thresholds,
side-effect classification rules, commit-boundary detection algorithm,
authority-gate recommendation engine, and runtime gate-enforcement
internals are **not** in this repository.
