# KYE™ Formal Rules vocabulary

Names introduced by **KYE Formal Rules Profile™**
(`kye-formal-rules-v1`) — the rights, obligations and governance
layer. This document lists names only. Rule-conflict-detection
algorithms, rule-proof internals, rule-compilation engine, contract-
to-authority extraction, semantic obligation mapping and sector-rule-
pack content are part of the patent track and are not published here.

> **A rule should not only be written. It should be enforceable,
> discoverable, revocable, provable and replayable.**

## Rule families

Six normative families. Every `KYEFormalRule` declares exactly one.

| Family | Operator | Meaning |
|---|---|---|
| `permission`  | `P`   | Subject MAY perform the action under stated authority + scope + state. |
| `obligation`  | `O`   | Subject MUST perform the required action when the trigger condition applies. |
| `prohibition` | `F`   | Subject MUST NOT perform the prohibited action under stated conditions. |
| `power`       | `Pow` | Subject HAS authority to create, modify, revoke, waive or override a normative state. |
| `immunity`    | `Imm` | Subject / state CANNOT be altered by the referenced actor or rule. |
| `exception`   | `Ex`  | Rule is displaced or modified under enumerated exceptional conditions. |

A seventh family `meta_governance` is recorded under
`KYEGovernanceRule` and describes who may change rules, which rules
dominate, and how conflicts resolve.

## Normative operators

Compact notation used inside `normative_effect.operator`:

| Operator | Family | Meaning |
|---|---|---|
| `P`   | permission  | "may" |
| `O`   | obligation  | "must" |
| `F`   | prohibition | "must not" |
| `Pow` | power       | "has authority to" |
| `Imm` | immunity    | "cannot be altered by" |
| `Ex`  | exception   | "displaced by, in conditions" |

KYE™ does not commit to a specific deontic-logic syntax in the public
surface. The operators above are the canonical product-friendly
abbreviations.

## Decision outputs

Beyond Core's `{allow, deny, require_approval, require_step_up,
quarantine}`, the Formal Rules Profile™ adds:

`prohibited` · `obligation_created` · `obligation_satisfied` ·
`obligation_breached` · `override_required` · `evidence_required` ·
`human_review_required`.

## Permission types

`delegated_capability_permission` · `role_based_permission` ·
`scope_based_permission` · `regulatory_permission` ·
`contractual_permission`.

## Obligation types

`pre_execution_approval` · `post_action_review` ·
`evidence_emission` · `notification` · `data_retention` ·
`data_deletion` · `regulatory_report` · `remediation` · `custom`.

## Obligation states

`pending` · `satisfied` · `breached` · `waived` · `expired` ·
`disputed` · `remediated` · `superseded`.

## Power types

`grant_power` · `revocation_power` · `modification_power` ·
`waiver_power` · `override_power` · `delegation_power`.

## Exception types

`emergency_override` · `business_continuity` ·
`regulatory_instruction` · `incident_response` ·
`scheduled_maintenance` · `custom`.

## Conflict types

`permission_prohibition_conflict` · `obligation_circularity` ·
`obligation_without_satisfaction_path` · `unbounded_obligation` ·
`unrevocable_authority` · `circular_delegation` ·
`missing_evidence_requirement` · `priority_tie` · `scope_overlap` ·
`exception_overlap`.

## Resolution strategies

`specific_rule_overrides_general_rule` ·
`prohibition_overrides_permission` · `later_rule_overrides_earlier` ·
`higher_priority_wins` · `explicit_governance_override` ·
`unresolved`.

## Required objects

| Object | Schema |
|---|---|
| Profile descriptor | `formal-rules-profile.json` |
| Formal Rule | `formal-rule.json` |
| Permission | `permission.json` |
| Obligation | `obligation.json` |
| Prohibition | `prohibition.json` |
| Power | `power.json` |
| Exception | `exception.json` |
| Governance Rule | `governance-rule.json` |
| Rule Conflict | `rule-conflict.json` |
| Rule Proof | `rule-proof.json` |
| Obligation State | `obligation-state.json` |

## Reason codes

See `reason-codes.md` under the **Formal Rules profile reason codes**
group (33 codes).

## Patent-safe boundary

Rule-conflict-detection algorithm, rule-proof internals, rule-
compilation engine, contract-to-authority extraction, semantic
obligation mapping and sector-specific formal-rule packs are **not**
in this repository.
