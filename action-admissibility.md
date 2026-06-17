# KYE™ Action Admissibility vocabulary

Names introduced by **KYE Action Admissibility Profile™**
(`kye-action-admissibility-v1`) — the upstream pre-action layer.
This document lists names only. Admissibility-scoring algorithms,
prohibited-action-class detection heuristics, intent-ambiguity
detection, source / data admissibility decision rules, agent-proposal
quarantine triggers and sector admission packs are part of the patent
track and are not published here.

> **KYE™ does not only attribute delegated actions after they exist.
> It checks whether proposed actions are admissible before they enter
> the authority pipeline.**

## Decision values

| Value | Meaning |
|---|---|
| `admit`                     | Admissible. Route onward to authority decisioning. |
| `reject`                    | Structurally invalid or prohibited. Do not enter pipeline. |
| `require_clarification`     | Intent ambiguous. Request principal clarification first. |
| `require_human_review`      | Admissible only after human reviewer admits. |
| `quarantine`                | Pattern matches a watched class. Freeze and escalate. |
| `route_to_authority_check`  | Synonym for `admit` — explicit routing instruction. |

## Inadmissibility classes

What admissibility actively detects:

`invalid_intent` · `ambiguous_intent` · `out_of_scope_proposal` ·
`prohibited_action_class` · `disallowed_data_source` ·
`inadmissible_evidence` · `unsafe_tool_path` · `coercion_signal` ·
`incentive_conflict` · `continuity_break` ·
`policy_ineligible_action` · `missing_authority_context` ·
`missing_principal` · `missing_accountable_owner` ·
`unsupported_jurisdiction`.

## Required objects

| Object | Schema |
|---|---|
| Profile descriptor | `action-admissibility-profile.json` |
| Proposed Action | `proposed-action.json` |
| Admission Gate™ | `admission-gate.json` |
| Admissibility Decision | `admissibility-decision.json` |
| Admissibility Evidence | `admissibility-evidence.json` |

## Required checks

`intent_present` · `intent_clear` · `principal_resolved` ·
`actor_resolved` · `accountable_owner_known` · `capability_known` ·
`resource_known` · `data_source_allowed` · `prohibited_action_class` ·
`continuity_preserved` · `formal_rule_block` · `evidence_ready` ·
`jurisdiction_supported` · `risk_state_acceptable` ·
`no_coercion_signal` · `no_incentive_conflict` ·
`no_unsafe_tool_path`.

## Reason codes

See `reason-codes.md` under the **Action Admissibility profile reason
codes** group (20 codes).

## Admissibility signals

`kye.admissibility.proposed_action_created` ·
`kye.admissibility.check_started` ·
`kye.admissibility.admitted` ·
`kye.admissibility.rejected` ·
`kye.admissibility.requires_clarification` ·
`kye.admissibility.requires_human_review` ·
`kye.admissibility.quarantined` ·
`kye.admissibility.routed_to_authority_check` ·
`kye.admissibility.evidence_generated`.

## Patent-safe boundary

Admissibility-scoring algorithm, prohibited-action-class detection
heuristics, intent-ambiguity detection rules, source / data
admissibility decision rules, agent-proposal quarantine triggers and
sector admission packs are **not** in this repository.
