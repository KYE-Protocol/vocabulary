# KYE™ Assurance Card vocabulary

Names introduced by **KYE Assurance Card Profile™**
(`kye-assurance-card-v1`) — the lifecycle assurance layer that turns
KYE™ runtime evidence into a living assurance record. This document
lists names only. Assurance-card generation, runtime-evidence binding,
review-automation, sector-pack content and use-case library
recommendation algorithms are part of the patent track and are not
published here.

> **System cards describe the assurance case. KYE™ proves what
> happened. KYE makes assurance executable.**

## Lifecycle stages

Eight ordered stages every assurance-card subject progresses through.

`design` · `pilot` · `deploy` · `monitor` · `incident_review` ·
`scope_change_review` · `retention_review` · `decommission`.

## Required objects

| Object | Schema |
|---|---|
| Profile descriptor | `assurance-card-profile.json` |
| Assurance Card | `assurance-card.json` |
| Human Involvement Plan | `human-involvement-plan.json` |
| Provenance Evidence | `provenance-evidence.json` |
| Assurance Review Cycle | `assurance-review-cycle.json` |
| Decommissioning Plan | `decommissioning-plan.json` |

## Subject types

`ai_agent` · `workflow` · `service` · `model` · `tool` · `connector` ·
`system`.

## Lifecycle states

`proposed` · `design` · `pilot` · `controlled_production` ·
`production` · `deprecated` · `suspended` · `revoked`.

## Review triggers

Ten named triggers any review cycle MAY listen on:

`scheduled` · `scope_change` · `new_capability` · `incident` ·
`risk_state_change` · `model_update` · `authority_change` ·
`supplier_change` · `licence_change` · `retention` · `decommission`.

## Human involvement types

`influence` · `direct` · `limit` · `approve` · `override` · `review`.

## Human involvement stages

`design` · `pilot` · `deploy` · `pre_commit` · `post_commit` ·
`incident` · `scope_change` · `retention` · `decommission`.

## Off-boarding actions

`revoke_authority` · `quarantine_credentials` · `rotate_keys` ·
`archive_evidence` · `notify_owner` · `notify_supplier` ·
`update_catalog` · `remove_from_runtime`.

## Cascade-revocation scopes

`entity_only` · `entity_and_descendants` · `tenant_wide`.

## Provenance verification methods

`self_attested` · `third_party_attestation` · `signed_evidence` ·
`registry_check`.

## Reason codes

See `reason-codes.md` under the **Assurance Card profile reason
codes** group (17 codes).

## Assurance signals

See `kye-assurance-card-v1.md` §6. Five families: assurance-card
lifecycle, human involvement, provenance, review cycle, decommissioning.

## Patent-safe boundary

The assurance-card generation engine, runtime-evidence binding
heuristics, review-automation engine, sector-pack content (defence,
public-sector, payments, health) and use-case library recommendation
algorithm are **not** in this repository.
