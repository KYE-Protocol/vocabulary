# KYE Protocol™ — Authority Finality™ (vocabulary)

> **Status:** Normative concept. v1.0. Apache 2.0.

## Definition

**Authority Finality™** is the *property* that, for any action taken
by any entity governed by KYE Protocol™, the runtime can prove — with
public-key-verifiable evidence — *who or what acted, on behalf of
whom, using which capability, under what authority, in what state, and
with what audit trail*.

The structural artefact this property is asserted over is the
**KYE Chain of Authority™** ([vocabulary](./chain-of-authority.md)) —
the linked, attenuating delegation chain from root principal to actor.
Authority Finality™ answers *is the chain final and provable?*;
KYE Chain of Authority™ is the chain itself.

Authority Finality™ is **technical and evidentiary**. It does not
replace legal agreements, signatures, or regulatory obligations; it
provides the substrate that lets those obligations be **proved** after
the fact.

## Six properties of an Authority-Final action

A KYE-conformant gateway exposes, for every adjudicated action, the
following six properties bound by a single `policy_decision_id`:

| Property | Field | Source |
|---|---|---|
| Who or what is acting | `actor.entity_id` | `entity` profile |
| On behalf of whom | top of `delegation_chain` | `delegation` profile |
| Using which capability | `capability_id` (when invocation) | `capability` profile |
| Under what authority | `delegation_id` + `scope_id` | `core` profile |
| In what state | composed 6-tuple per `state-composition.json` | `state` profile |
| With what audit trail | `audit_event_id` + `proof_bundle_id` | `audit` + `transparency` profiles |

## Use in copy

> KYE Protocol™ helps establish **Authority Finality™** for AI-agent
> actions — creating a replayable evidence layer for accountability,
> compliance, dispute resolution, and legally defensible audit trails.

## Trademark

**Authority Finality™** is a trademark of the KYE Protocol™ project.
It identifies the property defined here. Conformant implementations
may use the mark to claim the property; forks may not.

— KYE Protocol™ project, 2026.
