# KYE™ Relationship Vocabulary

Relationships are typed edges between entities. This document lists the relationship types KYE™ recognizes.

This document defines **names only**. Validation rules, evidence requirements, and lifecycle constraints are part of the normative specification.

## Ownership and control

| Relationship | Meaning |
|---|---|
| `owned_by` | Source is owned by target |
| `controlled_by` | Source is controlled by target |
| `operated_by` | Source is operated by target |
| `custodied_by` | Source is in custody of target |

## Authority and delegation

| Relationship | Meaning |
|---|---|
| `acts_on_behalf_of` | Source acts on behalf of target |
| `delegated_by` | Source's authority was delegated by target |
| `authorized_by` | Source's action was authorized by target |
| `approved_by` | Source was approved by target |

## Issuance and verification

| Relationship | Meaning |
|---|---|
| `issued_by` | Source was issued by target |
| `verified_by` | Source was verified by target |
| `attested_by` | Source was attested by target |
| `revoked_by` | Source was revoked by target |

## Use, invocation, and execution

| Relationship | Meaning |
|---|---|
| `uses` | Source uses target |
| `invokes` | Source invokes target |
| `hosts` | Source hosts target |
| `deploys` | Source deploys target |
| `executes` | Source executes target |
| `accesses` | Source accesses target |

## Provenance

| Relationship | Meaning |
|---|---|
| `trained_from` | Source was trained from target |
| `derived_from` | Source was derived from target |

## Governance and observation

| Relationship | Meaning |
|---|---|
| `scoped_to` | Source is scoped to target |
| `governed_by` | Source is governed by target |
| `allowed_by` | Source is allowed by target |
| `denied_by` | Source is denied by target |
| `observed_by` | Source is observed by target |
| `monitored_by` | Source is monitored by target |

## Lifecycle and structure

| Relationship | Meaning |
|---|---|
| `belongs_to` | Source belongs to target |
| `transferred_to` | Source was transferred to target |
| `mapped_to_control` | Source maps to a control identifier |
| `mapped_to_framework` | Source maps to a control framework |
