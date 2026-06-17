# KYE™ Vocabulary

The KYE™ vocabulary defines stable names for entities, relationships, actions, lifecycle states, obligations, data classes, and reason codes.

| File | Contents |
|---|---|
| `entity-types.md` | Entity type names |
| `relationships.md` | Relationship type names |
| `actions.md` | Action names |
| `lifecycle-states.md` | Lifecycle state names |
| `obligations.md` | Obligation names |
| `data-classes.md` | Data classification names |
| `reason-codes.md` | Reason code names |
| `continuity-discoverability.md` | Continuity decision values, drift types, discovery modes, risk-discovery types |
| `ontology.md` | Ontology domains, predicates, mapping types, required objects, signals |
| `operating-model.md` | Operating-model journey stages, gate types, commit-boundary archetypes, risk tiers, lifecycle states |
| `assurance-card.md` | Assurance-card lifecycle stages, subject types, review triggers, human-involvement types, off-boarding actions, cascade-revocation scopes |
| `formal-rules.md` | Formal-rule families, normative operators, decision outputs, permission/obligation/power/exception types, conflict types, resolution strategies |
| `action-admissibility.md` | Admissibility decision values, inadmissibility classes, required checks, signals |

These are the **public** vocabulary documents. They define names so that KYE artifacts can be written, exchanged, and discussed across implementations.

The semantics — how names map to validation rules, policy evaluation, lifecycle enforcement, audit propagation, proof construction, and transparency submission — are part of the normative specification, which is published separately.

## Stability

Vocabulary names are intended to be stable. Changes follow this discipline:

- additions are additive and backwards-compatible
- renames are not permitted; new names supersede old names with explicit aliasing in the normative specification
- removals require a deprecation cycle

## Profile-specific vocabulary

Profile-specific vocabulary (for example, payment actions, healthcare obligations, or treasury approval types) lives in profile documents. Where those profiles are released publicly, they will appear under their own directories. Until then, profile vocabulary is not published in this repository.
