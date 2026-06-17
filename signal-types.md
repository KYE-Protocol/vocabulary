# KYE Protocol™ — Signal types (canonical inventory)

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the canonical signals dictionary (`public/vocabulary/signals.md`).

Every signal `signal_type` value MUST be from this canonical
inventory. A signal whose type is not in this list is a conformance
failure (`reason_code=signal_type_unknown`).

## 1. Entity lifecycle

`entity.discovered` · `entity.registered` · `entity.verified` ·
`entity.activated` · `entity.limited` · `entity.under_review` ·
`entity.suspended` · `entity.quarantined` · `entity.stopped` ·
`entity.compromised` · `entity.transferred` · `entity.merged` ·
`entity.deprecated` · `entity.archived` · `entity.tombstoned`

## 2. Authority

`authority.granted` · `authority.elevated` · `authority.limited` ·
`authority.suspended` · `authority.revoked` · `authority.disputed` ·
`authority.frozen`

## 3. Delegation

`delegation.requested` · `delegation.approved` · `delegation.activated` ·
`delegation.attenuated` · `delegation.expired` · `delegation.revoked` ·
`delegation.parent_revoked` · `delegation.transferred` ·
`delegation.blocked`

## 4. Credential

`credential.issued` · `credential.presented` · `credential.verified` ·
`credential.rotating` · `credential.rotated` · `credential.expired` ·
`credential.revoked` · `credential.compromised` · `credential.lost` ·
`credential.recovered` · `credential.erased`

## 5. Attestation

`attestation.registered` · `attestation.refreshed` ·
`attestation.stale` · `attestation.revoked` · `attestation.failed`

## 6. Capability

`capability.registered` · `capability.granted` ·
`capability.invoked` · `capability.deny` · `capability.require_approval` ·
`capability.quarantined` · `capability.superseded` ·
`capability.revoked` · `capability.authority_revoked` ·
`capability.dependency_blocked` · `capability.notifications_published` ·
`capability.invocation_cancelled`

## 7. Recovery / break-glass

`recovery.requested` · `recovery.evidence_pending` ·
`recovery.under_review` · `recovery.window_expired` ·
`recovery.escalated` · `recovery.approved` · `recovery.rejected` ·
`recovery.completed` · `recovery.cancelled` ·
`break_glass.requested` · `break_glass.granted` ·
`break_glass.used` · `break_glass.expired` · `break_glass.frozen` ·
`compromise.reported` · `compromise.cascade_completed`

## 8. Risk

`risk.normal` · `risk.elevated` · `risk.high` · `risk.critical` ·
`risk.blocked` · `risk.cleared` · `risk.threshold_exceeded` ·
`risk.score_updated`

## 9. State composition

`state.composition_violation` · `state.transition_committed` ·
`state.transition_rejected`

## 10. Audit / runtime

`audit.event_appended` · `audit.chain_verified` ·
`audit.point_in_time_replayed` · `runtime.cascade_started` ·
`runtime.cascade_completed`

## 11. Webhook / signal-bus

`webhook.delivered` · `webhook.failed` · `webhook.retried` ·
`webhook.dead_lettered` · `webhook.signing_key_rotated` ·
`signal.replayed` · `signal.subscribe_acknowledged`

## 12. Federation

`federation.entity_imported` · `federation.entity_exported` ·
`federation.scope_attenuation_violation` ·
`federation.conflict_resolved` · `federation.replication_lag_high` ·
`federation.key_archived`

## 13. Transparency

`transparency.statement_appended` · `transparency.receipt_issued` ·
`transparency.inclusion_verified`

## 14. Telemetry

`telemetry.decision_emitted` · `telemetry.redacted` ·
`telemetry.export_failed`

## 15. Payments

(per `public/vocabulary/payments-decision-codes.md` §1, §11; emitted as
signal types `payment.<code>`.)

## 16. Healthcare

`healthcare.consent_presented` · `healthcare.consent_withdrawn` ·
`healthcare.redaction_applied` · `healthcare.external_send_blocked` ·
`healthcare.break_glass_invoked` · `healthcare.post_hoc_review_filed`

## 17. Treasury / custody

`treasury.intent_created` · `treasury.rebalanced` ·
`treasury.reconciled` · `treasury.exception_filed` ·
`custody.withdraw_requested` · `custody.withdraw_completed` ·
`custody.attestation_required` · `custody.cold_storage_unsealed`

## 18. Conformance

`conformance.fixture_run_started` · `conformance.fixture_run_completed` ·
`conformance.report_signed`

## 19. Keys

`keys.rotation_requested` · `keys.rotated` · `keys.archived` ·
`keys.suite_changed`

## 20. Payload artefacts (KYE Payload Trust Profile™)

`payload.received` · `payload.verified` · `payload.rejected` ·
`payload.expired` · `payload.replay_detected` · `payload.tampered` ·
`payload.bound_to_decision` · `payload.executed` · `payload.failed` ·
`payload.archived`

## 21. Taxonomies (KYE Taxonomy & Metadata Profile™)

`taxonomy.created` · `taxonomy.updated` · `taxonomy.published` ·
`taxonomy.deprecated` · `taxonomy.term_added` ·
`taxonomy.term_updated` · `taxonomy.term_deprecated` ·
`taxonomy.mapping_created` · `taxonomy.mapping_deprecated`

## 22. Metadata bindings (KYE Taxonomy & Metadata Profile™)

`metadata.schema_created` · `metadata.schema_updated` ·
`metadata.schema_deprecated` · `metadata.validation_failed` ·
`metadata.classification_changed` · `metadata.binding_created` ·
`metadata.binding_removed`

## 23. Authority graph (KYE Graph Profile™)

`graph.node_created` · `graph.node_updated` · `graph.node_archived` ·
`graph.edge_created` · `graph.edge_updated` · `graph.edge_revoked` ·
`graph.decision_map_emitted` · `graph.blast_radius_computed` ·
`graph.compliance_map_refreshed` · `graph.traversal_failed`

## 24. Policy administration (KYE PAP — v1.1 preview)

`policy.uploaded` · `policy.activated` · `policy.deactivated` ·
`policy.version_published` · `policy.rolled_back`

— KYE Protocol™ project, 2026.
