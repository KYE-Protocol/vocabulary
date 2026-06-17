# KYE™ Ontology vocabulary

Names introduced by **KYE Ontology Profile™** (`kye-ontology-v1`). This
document lists names only. Semantic-resolution algorithms,
false-equivalence detection heuristics, cross-profile mapping
reconciliation, tenant overlay resolution and risk-weighted ontology
traversal are part of the normative specification and the patent track,
and are not published here.

> **Schemas make data valid. Ontologies make data meaningful.**

## Ontology domains

Twelve domains. Each KYE term declares exactly one.

| Domain | Surface |
|---|---|
| `entity` | Any nameable subject — human, org, agent, model, tool, device, dataset, credential, instrument, asset. |
| `authority` | Authority kinds — delegation, mandate, consent, approval, permission, entitlement, licence, power_of_attorney, role_authority, regulatory_authority, contractual_authority, emergency_authority. |
| `capability` | Named verbs — payment_initiation, card_purchase, data_access, contract_signing, clinical_access, tool_invocation, infrastructure_command, credential_rotation, settlement_approval, evidence_export. |
| `scope` | Constraint kinds — amount_limit, time_window, merchant_category, jurisdiction, data_class, environment, resource_class, approval_threshold, purpose_limitation, retention_limit. |
| `state` | State dimensions — entity_state, authority_state, delegation_state, credential_state, capability_state, risk_state, recovery_state, continuity_state, discovery_state, certification_state. |
| `decision` | Verdict kinds — allow, allow_with_constraints, require_approval, deny, continuity_*. |
| `evidence` | Artefact kinds — audit_event, decision_map, evidence_pack, payload_hash, signature, state_snapshot, intent_trace, continuity_context, discovery_audit_event. |
| `continuity` | Drift types and continuity dimensions. |
| `discoverability` | Discovery modes, risk-discovery types, masking classes. |
| `connector` | Connector Profile™ family kinds. |
| `sector` | Sector namespaces — payments, open_finance, legal, health, pensions, cyber, critical_infrastructure, sovereign_ai, telecom, pharma_gxp. |
| `certification` | Conformance / certification artefacts. |

## Predicates

Stable predicate dictionary. New predicates require an RFC.

`grants` · `limits` · `inherits_from` · `requires` · `requires_authority` ·
`requires_scope` · `requires_state` · `requires_evidence` ·
`requires_approval_from` · `expires_at` · `revokes` · `supersedes` ·
`depends_on` · `constrains` · `narrows` · `blocks` · `allows` ·
`requires_step_up` · `requires_human_review` · `triggers` ·
`triggers_signal` · `invalidates_authority` · `proves` · `supports` ·
`binds_to` · `references` · `verifies` · `replays` · `maps_to_control` ·
`acts_on_behalf_of` · `has_authority` · `uses_capability` ·
`evidenced_by` · `equivalent_to` · `related_not_identical` ·
`not_equivalent_to` · `aliased_by` · `subsumes` · `subsumed_by`.

## Mapping types

External-system → KYE term mappings declare exactly one of:

| Type | Meaning |
|---|---|
| `equivalent` | Source and KYE term are interchangeable for runtime purposes. |
| `related_not_identical` | Overlap exists; source DOES NOT prove the KYE term alone; additional KYE objects MUST be presented (`requires_additional_kye_objects`). |
| `not_equivalent` | The source term MUST NOT be treated as the KYE term. |
| `aliased_by` | Label-level alias only; same KYE term. |
| `subsumes` | Source narrower than the KYE term. |
| `subsumed_by` | Source broader than the KYE term. |

A mapping with `related_not_identical` MUST list
`requires_additional_kye_objects` so the policy engine can deny when the
source term is presented alone (reason code:
`external_term_not_equivalent`).

## Required objects

| Object | Schema | Role |
|---|---|---|
| Ontology profile descriptor | `ontology-profile.json` | Profile manifest. |
| Ontology term | `ontology-term.json` | One canonical term. |
| Ontology relationship | `ontology-relationship.json` | (subject, predicate, object) triple with constraints. |
| Ontology mapping | `ontology-mapping.json` | External-system → KYE term mapping with mapping_type + required objects. |
| Semantic assertion | `semantic-assertion.json` | Decision-bound semantics, hash-chained into the audit ledger. |

## Serializations

| Layer | Format | Status |
|---|---|---|
| Runtime API | JSON Schema 2020-12 | required |
| Semantic interoperability | JSON-LD context | recommended |
| External research / KG integration | RDF / OWL | optional |

JSON-LD context published alongside this document (`jsonld-context.json`).

## Reason codes

See `reason-codes.md` under the **Ontology profile reason codes** group.

## Ontology signals

Term lifecycle: `kye.ontology.term.created` ·
`kye.ontology.term.updated` · `kye.ontology.term.deprecated` ·
`kye.ontology.term.revoked`.

Relationship lifecycle: `kye.ontology.relationship.created` ·
`kye.ontology.relationship.updated` ·
`kye.ontology.relationship.deprecated`.

Mapping lifecycle: `kye.ontology.mapping.created` ·
`kye.ontology.mapping.validated` ·
`kye.ontology.mapping.conflict_detected` ·
`kye.ontology.mapping.deprecated`.

Semantic assertion: `kye.semantic_assertion.created` ·
`kye.semantic_assertion.verified` ·
`kye.semantic_assertion.conflict_detected`.

Semantic graph: `kye.semantic_graph.updated` ·
`kye.semantic_graph.rebuilt` ·
`kye.semantic_graph.validation_failed`.

## Patent-safe boundary

The semantic-resolution algorithm, false-equivalence detection
heuristics, cross-profile reconciliation engine, tenant overlay
resolution and risk-weighted ontology traversal are **not** in this
repository. See the public landing page for the profile overview;
counsel-controlled material remains private.
