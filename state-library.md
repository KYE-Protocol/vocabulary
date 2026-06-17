# KYE™ State Library Vocabulary

The **KYE State Library™** is the open-source catalogue of reference state
machines for KYE Protocol™. This document describes the library model in
plain terms.

This document defines names and the adoption / derivation model only.
The signing mechanism, integrity-lock construction, and transparency-log
inclusion are part of the normative specification.

## What the library is

The KYE State Library™ is a curated set of **reference state machines** —
pre-built graphs of states and transitions that cover common entity
lifecycle patterns across regulated industries.

Each library entry is:

- **open source** — published under MIT or Apache-2.0
- **signed** — the entry JSON is signed; the signature is verifiable
  against the KYE Protocol™ transparency log
- **versioned** — entries follow `<name>@<semver>`; minor bumps add
  states or transitions; major bumps are breaking and require a new entry
- **sector-tagged** — each entry declares one or more `sector` values
  from the list below

## v1 sector coverage

The v1 library ships 30 starter entries across 9 sectors:

| Sector | Stable ID | Example machines |
|---|---|---|
| Banking | `banking` | `retail_account.v1`, `corporate_account.v1`, `credit_facility.v1` |
| Payments | `payments` | `payment_mandate.v1`, `payment_instruction.v1` |
| Insurance | `insurance` | `policy_holder.v1`, `claim.v1` |
| Healthcare | `healthcare` | `patient.v1`, `clinical_record.v1` |
| Pharma | `pharma` | `trial_participant.v1`, `batch_release.v1` |
| Logistics | `logistics` | `shipment.v1`, `warehouse_asset.v1` |
| Energy | `energy` | `grid_asset.v1`, `operator_credential.v1` |
| Regtech | `regtech` | `regulated_entity.v1`, `compliance_obligation.v1` |
| AI Governance | `ai_governance` | `model.v1`, `ai_agent.v1`, `audit_stream.v1` |

## Adoption

A tenant **adopts** a library entry by setting `state_machine_id` on an
entity (or entity class) to the library entry's `kye:sm:…` URN and
recording the `state_machine_version`. Adoption is a point-in-time
snapshot — the entity continues to use that version even when the library
publishes a newer minor version.

Upgrading to a newer version is an explicit operation that adds a
`state_event` recording the version change.

## Derivation

A tenant may **derive** a tightened variant from a library entry:

1. The derived machine references the parent entry via `parent_machine_id`.
2. Derivation may only **add** states, **add** guard conditions, or
   **restrict** allowed transitions. It may not remove terminal classes
   or remove evidence requirements.
3. The derived machine is signed by the tenant. The signature is recorded
   in the tenant's State Registry™.
4. The derivation delta (the set of additions / restrictions) is stored
   as a separate signed record alongside the derived machine.

Derivation does **not** transfer the parent library entry's open-source
licence to proprietary use — the derived delta is the tenant's own work;
the base entry remains under its original licence.

## Integrity lock

Once a library entry is published (signed + included in the transparency
log), its content is immutable. A published entry is never edited in
place. Corrections or additions produce a new semver entry. This ensures
that any tenant that has adopted `foo@1.2.3` has an unchanging contract
for the lifetime of that version.

## Naming convention

Library entry IDs follow the pattern:

```
kye:sm:kyeprotocol.com:lib.<sector>.<name>.<major>
```

Examples:

```
kye:sm:kyeprotocol.com:lib.banking.retail_account.v1
kye:sm:kyeprotocol.com:lib.ai_governance.model.v1
kye:sm:kyeprotocol.com:lib.healthcare.patient.v1
```

## What this document does not specify

- the signing algorithm or key management for library entries
- how library entries are verified against the transparency log
- the process for submitting new library entries
- the runtime enforcement of derivation constraints

Those are part of the normative specification.
