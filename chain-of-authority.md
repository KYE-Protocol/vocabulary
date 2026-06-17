# KYE Protocol™ — KYE Chain of Authority™ (vocabulary)

> **Status:** Normative concept. v1.0. Apache 2.0.

## Definition

**KYE Chain of Authority™** is the *structural artefact* of authority
under KYE Protocol™: the linked, attenuating delegation chain that
runs from the root principal down to the entity actually performing
an action.

Each link is a signed delegation that:

- names the entity it delegates from and to,
- carries a capability and a scope,
- attenuates (never broadens) the parent's scope,
- is bound to a state-vector at the moment of signing,
- is hash-linked into the audit chain.

The chain itself is the artefact. **Authority Finality™** is the
*property* of that chain — that the chain is provably terminal,
public-key-verifiable, and replayable. Two concepts, one structure.

## Narrative parallel

Chain-of-custody for *documents* is what courts already accept. KYE
Chain of Authority™ is the equivalent for *actions*: a signed,
linked, end-to-end record of who delegated what to whom, under what
scope, in what state, with what audit trail.

> KYE™ produces the KYE Chain of Authority™ the way digital
> signatures produce chain-of-custody for documents. Courts already
> accept signed documents; KYE™ gives them signed delegations.

## How the chain is built

| Position | Field | Source |
|---|---|---|
| Root | `principal_entity_id` of the topmost grant | `core` profile |
| Each link | `delegation_id` with `parent_delegation_id`, `capability_id`, `scope_id`, `state_snapshot` | `delegation` profile |
| Terminal | `actor.entity_id` | `entity` profile |
| Verifiable | each link is COSE/JWS-signed; chain is hash-linked into the audit chain | `transparency` profile |

## Use in copy

> Before the bank authorises the payment, the gateway checks the
> entire **KYE Chain of Authority™** — root principal → business →
> agent → action — and emits the signed Decision Map™ + Evidence Pack™.

## Trademark

**KYE Chain of Authority™** is a trademark of the KYE Protocol™
project. The KYE prefix is intentional: it mitigates a §2(e)
descriptiveness refusal that would face the bare phrase
"Chain of Authority" in USPTO / UKIPO / EUIPO filings.

Conformant implementations may use the mark to refer to the artefact
they produce. Forks may not.

## Relationship to Authority Finality™

| | KYE Chain of Authority™ | Authority Finality™ |
|---|---|---|
| Type | Structural artefact | Property / outcome |
| Question it answers | *What is the chain?* | *Is the chain final and provable?* |
| Plural? | Yes — many chains per gateway | No — single property of any chain |
| Schema | Composed from `delegation` chain + `state-composition.json` | Asserted by the runtime over the composed chain |

— KYE Protocol™ project, 2026.
