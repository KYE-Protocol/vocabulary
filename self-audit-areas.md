# KYE Self-Audit Canonical Areas (V1)

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the `evidence-replay` profile + `compliance-evidence` rule pack (post-§29 landing).

A complete `KYESelfAuditRun` MUST cover the 17 canonical areas below.
A finding's `area` field is drawn from this list.

## Areas

`schema` · `dictionary` · `profile` · `registry` ·
`entity_state` · `authority_grant` · `delegation_path` ·
`capability_state` · `credential_binding` · `policy_binding` ·
`decision_correctness` · `reason_code_correctness` ·
`audit_trail_integrity` · `evidence_completeness` ·
`webhook_delivery_integrity` · `graph_consistency` ·
`recovery_revocation_correctness`

## Finding severity

`info` · `low` · `medium` · `high` · `critical`

## Self-audit result

`passed` · `passed_with_warnings` · `failed` · `incomplete` · `not_applicable`

## Attestation status

`draft` · `signed` · `published` · `expired` · `revoked` · `superseded`

## Required signal types

```
kye.self_audit.started
kye.self_audit.completed
kye.self_audit.failed
kye.self_audit.finding_created
kye.self_audit.critical_finding_detected
kye.conformance.self_test_passed
kye.conformance.self_test_failed
kye.attestation.created
kye.attestation.signed
kye.attestation.published
kye.attestation.expired
kye.attestation.revoked
kye.audit.integrity_check_failed
kye.evidence.completeness_check_failed
kye.policy.coverage_gap_detected
kye.decision.replay_mismatch
```

— KYE Protocol™ project, 2026.
