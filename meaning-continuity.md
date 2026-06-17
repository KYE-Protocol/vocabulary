# KYE™ Meaning Continuity vocabulary

Names introduced by **KYE Meaning Continuity™**
(`kye-meaning-continuity-v1`) — the meaning-preservation sub-profile
of **KYE Continuity Profile™** v1.1.0. This document lists names
only. Meaning-score computation, constraint-loss detection across
handoffs, drift-cascade routing, reconfirmation-flow trigger
thresholds, evidence-pack composition rules and sector-specific
meaning packs are part of the patent track and are not published
here.

> **KYE Continuity Profile™ preserves the chain. KYE Meaning
> Continuity™ preserves the meaning along the chain.**

## Decision values

| Value | Meaning |
|---|---|
| `meaning_preserved`         | Meaning preserved end-to-end. Route onward. |
| `meaning_degraded`          | Non-material drift detected. Onward with note. |
| `meaning_broken`            | Material meaning loss detected. Block. |
| `meaning_unknown`           | Insufficient evidence to score. Pause. |
| `require_clarification`     | Ambiguity in interpretation. Ask the principal. |
| `require_reconfirmation`    | Material constraint changed. Ask the principal to reconfirm. |
| `require_human_review`      | Drift cannot be resolved automatically. Escalate. |
| `quarantine`                | Pattern matches a watched drift class. Freeze. |

## Routing outcomes

`pause_admission` · `quarantine_proposed_action` ·
`route_to_admissibility` · `route_to_authority_check`.

## Drift types

What meaning continuity actively detects:

| Drift type | Meaning |
|---|---|
| `constraint_loss`         | A material constraint declared by the principal was dropped during interpretation or handoff. |
| `context_loss`            | The contextual record under which the intent was declared has been lost or unreferenced. |
| `memory_conflict`         | Memory used during interpretation conflicts with the principal's declared intent. |
| `timing_drift`            | Time elapsed between intent and evaluation has changed the meaning of the action. |
| `handoff_drift`           | Meaning has drifted across one or more handoff boundaries. |
| `incentive_drift`         | Optimisation goal in effect at evaluation time differs from the principal's declared goal. |
| `state_transition_drift`  | A state transition between intent and evaluation has changed the meaning. |
| `interpretation_drift`    | The interpreted goal differs materially from the declared goal. |
| `assumption_injection`    | Assumptions not declared by the principal have been added during interpretation. |
| `meaning_compression`     | Constraints or scope have been compressed below what the principal declared. |
| `meaning_expansion`       | Constraints or scope have been expanded beyond what the principal declared. |

## Continuity modules (Continuity v1.1.0)

`intent_continuity` · `meaning_continuity` · `context_continuity` ·
`memory_continuity` · `incentive_continuity` · `timing_continuity` ·
`handoff_continuity` · `state_continuity` · `execution_continuity`.

## Required objects

| Object | Schema |
|---|---|
| Meaning Continuity Context  | `meaning-continuity-context.json` |
| Handoff Trace               | `handoff-trace.json` |
| Meaning Drift Event         | `meaning-drift-event.json` |
| Meaning Continuity Decision | `meaning-continuity-decision.json` |

## Reason codes

`meaning_preserved` · `meaning_degraded` · `meaning_broken` ·
`meaning_unknown` · `meaning_drift_detected` ·
`authorised_meaning_preserved` · `authorised_meaning_lost` ·
`constraint_lost` · `constraint_changed` · `constraint_added` ·
`assumption_added` · `context_lost` ·
`context_changed_since_intent` · `memory_conflict_detected` ·
`memory_stale` · `memory_missing` ·
`incentive_conflict_detected` · `timing_changed_meaning` ·
`handoff_boundary_drift` · `handoff_integrity_degraded` ·
`state_transition_changed_meaning` ·
`principal_reconfirmation_required` ·
`meaning_evidence_incomplete`.

## Required obligations

`pause_admission` · `request_clarification` ·
`request_reconfirmation` · `prevent_commit_until_reconfirmed` ·
`emit_meaning_drift_event` · `include_in_evidence_pack` ·
`notify_principal` · `escalate_to_human_review` ·
`quarantine_actor` · `bind_to_admissibility_decision`.

## Handoff types

`human_to_agent_instruction` · `agent_to_agent_delegation` ·
`agent_to_sub_agent_delegation` · `agent_to_tool_request` ·
`tool_to_agent_response` · `agent_to_human_clarification` ·
`agent_to_human_reconfirmation`.

## Meaning continuity signals

`kye.meaning_continuity.check_started` ·
`kye.meaning_continuity.check_completed` ·
`kye.meaning_continuity.preserved` ·
`kye.meaning_continuity.degraded` ·
`kye.meaning_continuity.broken` ·
`kye.meaning_continuity.requires_reconfirmation` ·
`kye.meaning_continuity.requires_human_review` ·
`kye.meaning_continuity.evidence_pack_generated`.

## Meaning drift signals

`kye.meaning_drift.detected` ·
`kye.meaning_drift.resolved` ·
`kye.meaning_drift.quarantined` ·
`kye.meaning_drift.reconfirmation_requested` ·
`kye.meaning_drift.reconfirmation_completed`.

## Handoff signals

`kye.handoff.trace_created` ·
`kye.handoff.boundary_crossed` ·
`kye.handoff.drift_detected` ·
`kye.handoff.integrity_degraded`.

## Memory / context / timing supporting signals

`kye.memory_context.used` ·
`kye.memory_context.conflict_detected` ·
`kye.memory_context.stale` ·
`kye.context_snapshot.changed` ·
`kye.timing.meaning_changed`.

## Patent-safe boundary

Meaning-score computation, constraint-loss detection across
handoffs, drift-cascade routing rules, reconfirmation-flow trigger
thresholds, evidence-pack composition rules and sector-specific
meaning packs are **not** in this repository. The intelligent
runtime is part of the normative specification held privately and
is delivered as a commercial product.
