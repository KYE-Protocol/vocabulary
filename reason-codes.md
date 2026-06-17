# KYE™ Reason Code Vocabulary

Reason codes accompany decisions, signals, and lifecycle changes. This document lists reason codes recognized by KYE™.

This document defines **names only**.

| Code | Meaning |
|---|---|
| `policy_violation` | Action violated policy |
| `credential_revoked` | Credential was revoked |
| `delegation_revoked` | Delegation was revoked |
| `assurance_below_minimum` | Assurance level below minimum |
| `risk_threshold_exceeded` | Risk threshold exceeded |
| `external_export_blocked` | External export blocked |
| `workload_attestation_failed` | Workload attestation failed |
| `manual_incident_response` | Manual incident response action |
| `legal_hold_applied` | Legal hold applied |
| `consent_withdrawn` | Consent withdrawn |

## Payload Trust profile reason codes

| Code | Meaning |
|---|---|
| `payload_signature_missing` | Payload signature absent |
| `payload_signature_invalid` | Payload signature does not verify against declared credential |
| `payload_hash_mismatch` | `payload_hash` does not match the canonicalised bytes |
| `payload_canonicalization_unsupported` | Gateway does not support the declared canonicalisation suite |
| `payload_nonce_missing` | Freshness window present but nonce empty |
| `payload_nonce_reused` | Nonce already seen inside the freshness window |
| `payload_expired` | Receive time is past `expires_at` |
| `payload_actor_mismatch` | `actor_entity_id` does not match the credential's subject |
| `payload_capability_mismatch` | `capability_id` is not granted to the actor |
| `payload_decision_binding_missing` | Action attempted without a successful `bound_to_decision` transition |

## Taxonomy & Metadata profile reason codes

| Code | Meaning |
|---|---|
| `taxonomy_term_unknown` | Term value is not registered in the referenced taxonomy |
| `taxonomy_term_deprecated` | Term resolved to an active taxonomy but the term itself is `status=deprecated` |
| `taxonomy_version_mismatch` | Mapped value uses a taxonomy version not accepted by the policy |
| `metadata_schema_unknown` | `metadata_schema_id` is not registered |
| `metadata_required_field_missing` | A required field defined by the metadata schema is absent |
| `metadata_field_taxonomy_violation` | A field value is not from the schema's declared taxonomy |
| `metadata_classification_drift` | Classification field changed without re-binding evidence |
| `data_class_not_allowed` | Resource carries a data class that is not permitted for the actor's profile |

## Graph profile reason codes

| Code | Meaning |
|---|---|
| `graph_authority_path_missing` | No valid authority path from actor to action / resource |
| `graph_delegation_path_missing` | No active delegation path between actor and principal |
| `graph_delegation_path_disputed` | Delegation path contains a node in `disputed` state |
| `graph_capability_dependency_compromised` | A capability dependency is in `state=compromised` |
| `graph_capability_dependency_high_risk` | A capability dependency carries `risk_state=high` |
| `graph_blast_radius_too_broad` | Compromise blast radius exceeds the configured safety bound |
| `graph_traversal_depth_exceeded` | Query depth limit reached without a complete result |
| `graph_node_not_found` | Referenced node URN is not registered |
| `graph_edge_revoked` | Edge has been revoked since the last cache snapshot |

## Ontology profile reason codes

| Code | Meaning |
|---|---|
| `ontology_term_missing` | Referenced KYE term is not registered |
| `ontology_term_deprecated` | Referenced KYE term is `status=deprecated` |
| `ontology_mapping_missing` | A required external-system → KYE mapping was not found |
| `ontology_mapping_conflict` | Two mappings make incompatible claims for the same source term |
| `semantic_equivalence_rejected` | Asserted equivalence violates a `not_equivalent_to` rule |
| `semantic_relationship_ambiguous` | Resolution returned multiple candidate predicates |
| `semantic_resolution_failed` | Resolver could not produce a canonical KYE term |
| `semantic_assertion_verified` | Semantic assertion verified successfully |
| `semantic_assertion_conflict` | Semantic assertion conflicts with a hash-chained prior assertion |
| `external_term_not_equivalent` | Source term presented as KYE authority without required additional KYE objects |
| `profile_term_mismatch` | Term used outside its declared profile_refs |
| `sector_term_requires_mapping` | Cross-sector decision requires a validated mapping; none present |
| `ontology_policy_denied` | Action denied by an ontology-level policy rule |

## Operating Model profile reason codes

| Code | Meaning |
|---|---|
| `use_case_owner_missing` | Use-case intake lacks an `owner_entity_id` |
| `use_case_purpose_missing` | Use-case intake lacks a `business_objective` |
| `data_classification_missing` | Use-case intake lacks `data_classes` |
| `authority_model_missing` | No `KYEEntityAuthorityRecord` exists for the actor |
| `review_path_missing` | A `KYEReviewPath` is required but not configured |
| `evidence_requirements_missing` | Required evidence list is empty for a high-risk capability |
| `revocation_path_missing` | Authority record lacks a revocation policy |
| `commit_boundary_missing` | A capability with `external_effect_possible` lacks a `KYECommitBoundary` |
| `authority_gate_missing` | A capability requires a `KYEAuthorityGate` that does not exist |
| `human_review_required` | Risk tier mandates human review before commit |
| `autonomous_execution_not_allowed` | Readiness assessment forbids autonomous execution |
| `payment_execution_gate_required` | Payment execution must be guarded by a payment gate |
| `external_send_gate_required` | Outbound message must be guarded by an external-send gate |
| `clinical_action_gate_required` | Clinical action must be guarded by a clinical-action gate |
| `legal_commit_gate_required` | Contract / signature must be guarded by a legal-commit gate |
| `infrastructure_command_gate_required` | Infrastructure command must be guarded by an infrastructure gate |
| `readiness_incomplete` | Readiness assessment dimensions are incomplete |
| `pilot_ready_with_controls` | Readiness sufficient for pilot under enumerated controls |
| `production_ready` | Readiness sufficient for production execution |

## Assurance Card profile reason codes

| Code | Meaning |
|---|---|
| `assurance_card_missing` | Subject entity has no associated `KYEAssuranceCard` |
| `assurance_card_owner_missing` | Assurance card lacks an `owner_entity_id` |
| `intended_use_undocumented` | `intended_use.summary` is missing |
| `prohibited_uses_missing` | `intended_use.prohibited_uses` is empty for a high-risk subject |
| `provenance_missing` | No `KYEProvenanceEvidence` is bound to the assurance card |
| `human_involvement_plan_missing` | Subject performs commit-level capabilities but no `KYEHumanInvolvementPlan` is bound |
| `approval_threshold_breach` | Action exceeds an approval threshold without recorded human approval |
| `review_overdue` | `KYEAssuranceReviewCycle.next_review_due` has passed |
| `scope_change_review_required` | Authority record / gates / commit-boundaries changed without a triggered review |
| `incident_review_required` | Incident occurred without a triggered review |
| `retention_window_expired` | Retention window expired without archival or decommissioning |
| `decommissioning_plan_missing` | Subject is `deprecated` / `revoked` without an active `KYEDecommissioningPlan` |
| `assurance_card_runtime_evidence_unbound` | Assurance card lacks references to runtime decision maps / evidence packs |
| `provenance_supplier_unverified` | A supplier in the provenance evidence is `verified=false` |
| `provenance_licence_change_unrecorded` | Licence change detected but not recorded as a review trigger |
| `evidence_replay_failed` | Offline replay of bound evidence failed verification |
| `bypass_of_human_involvement_attempted` | Runtime detected an attempt to bypass a `KYEHumanInvolvementPlan` involvement point |

## Formal Rules profile reason codes

| Code | Meaning |
|---|---|
| `permission_granted` | Standing permission resolved as allow |
| `permission_missing` | No matching permission for this capability + scope + state |
| `permission_expired` | Permission's `valid_until` has passed |
| `permission_revoked` | Permission was revoked by an exercised power |
| `permission_scope_exceeded` | Action exceeds the permission's declared scope |
| `obligation_created` | Decision created a new obligation |
| `obligation_pending` | Obligation has been created but not yet satisfied |
| `obligation_satisfied` | Obligation satisfaction conditions all met |
| `obligation_breached` | Obligation deadline passed without satisfaction |
| `obligation_waived` | Obligation waived by an exercised power |
| `obligation_expired` | Obligation expired without satisfaction or waiver |
| `obligation_disputed` | Obligation flagged as disputed pending review |
| `obligation_not_satisfied` | Action denied because a required obligation is unsatisfied |
| `prohibition_triggered` | Prohibition condition matched the requested action |
| `prohibited_action_requested` | Subject requested an action enumerated in `prohibited_capability` |
| `prohibited_action_without_approval` | Action prohibited unless an approval event is present |
| `power_missing` | Holder does not hold the required power for this operation |
| `power_exercised` | Power was successfully exercised |
| `power_not_valid` | Holder's power is in an invalid state |
| `power_revoked` | Power has been revoked |
| `override_requested` | Governance override requested |
| `override_approved` | Governance override approved |
| `override_denied` | Governance override denied |
| `override_expired` | Override expired without re-approval |
| `override_requires_second_approver` | Override requires a second approver per governance rule |
| `rule_conflict_detected` | Two or more rules conflict |
| `permission_prohibition_conflict` | Permission and prohibition both matched |
| `obligation_without_satisfaction_path` | Obligation has no path to `satisfied` |
| `unbounded_obligation` | Obligation lacks a deadline or termination condition |
| `circular_delegation` | Delegation chain forms a cycle |
| `missing_evidence_requirement` | Rule requires evidence not declared in the rule set |
| `rule_priority_resolved` | Rule conflict resolved by priority |
| `specific_rule_overrides_general_rule` | Specific rule won over general rule on resolution |

## Action Admissibility profile reason codes

| Code | Meaning |
|---|---|
| `proposed_action_admissible` | Proposed action passes all checked dimensions |
| `intent_invalid` | Declared intent is structurally invalid |
| `intent_ambiguous` | Declared / interpreted intent ambiguity exceeds threshold |
| `intent_missing` | No intent reference attached to the proposed action |
| `principal_missing` | No principal entity resolves on the proposed action |
| `actor_missing` | No actor entity resolves on the proposed action |
| `accountable_owner_missing` | No accountable owner resolves on the proposed action |
| `capability_unknown` | Requested capability is not registered |
| `resource_unknown` | Target resource is not registered |
| `data_source_disallowed` | Source of input data is disallowed by policy |
| `evidence_inadmissible` | Required evidence references are missing or untrusted |
| `prohibited_action_class` | Action matches a prohibited class for this actor / sector |
| `unsafe_tool_path_detected` | Proposed tool path matches an unsafe pattern |
| `coercion_signal_detected` | Pressure / coercion signal detected upstream of the proposal |
| `incentive_conflict_detected` | Agent incentive conflicts with declared intent |
| `continuity_drift_blocks_admission` | Continuity drift detected upstream blocks admission |
| `policy_ineligible_action` | Proposal ineligible under the active policy set |
| `formal_rule_blocks_admission` | A formal rule (typically a prohibition) blocks admission |
| `jurisdiction_unsupported` | No supported jurisdiction binding for the proposed action |
| `risk_state_blocks_admission` | Current risk state of the actor / principal blocks admission |
