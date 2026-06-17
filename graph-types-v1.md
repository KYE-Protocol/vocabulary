# KYE Protocol™ — Graph node, edge, and query dictionaries (V1)

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the `graph` dictionary + graph-traversal additions to the `runtime-authority` profile (post-§29 landing).
>
> KYE is **graph-first** because authority is relational. The
> dictionaries below are the canonical values for `node_type`,
> `edge_type`, and `graph_query_type` referenced by `graph-node.json`,
> `graph-edge.json`, and `decision-map.json`. Specific traversal
> algorithms are part of the patent track and are not described here.

## 1. `node_type`

`entity` · `human` · `organisation` · `ai_agent` · `api_client` ·
`wallet` · `device` · `credential` · `capability` · `skill` · `tool` ·
`workflow` · `prompt` · `model` · `resource` · `policy` ·
`authority_grant` · `delegation` · `scope` · `state` ·
`payload_artifact` · `decision` · `audit_event` · `evidence_pack` ·
`compliance_control` · `taxonomy_term` · `metadata_schema`

## 2. `edge_type`

`owns` · `controls` · `maintains` · `issues` · `approves` ·
`delegates_to` · `acts_on_behalf_of` · `grants_authority_to` ·
`has_authority` · `authorises_capability` · `uses_capability` ·
`depends_on` · `calls` · `accesses` · `bound_to_credential` ·
`has_state` · `governed_by_policy` · `requires_approval_from` ·
`evaluated_by` · `allowed_by` · `denied_by` · `produced_decision` ·
`produced_audit_event` · `included_in_evidence_pack` ·
`maps_to_framework_control` · `supersedes` · `revokes` ·
`quarantines` · `recovers`

## 3. `graph_query_type`

`authority_path` · `delegation_path` · `capability_dependency` ·
`decision_map` · `evidence_graph` · `risk_propagation` ·
`blast_radius` · `compliance_mapping` · `lineage` · `ownership` ·
`policy_coverage`

## 4. Trademarked graph projections

| Term                  | Score | Use                           |
|-----------------------|-------|-------------------------------|
| **Authority Graph™**  | 97    | Core KYE concept              |
| **Decision Map™**     | 96    | Per-decision explainability   |
| **Evidence Graph™**   | 95    | Decision ↔ evidence linkage   |
| **Blast Radius Map™** | 94    | Compromise impact analysis    |
| **Compliance Map™**   | 94    | Framework control projection  |

## 5. Use in copy

> **KYE is graph-first because authority is relational.** It maps
> every entity, delegation, capability, credential, policy, state,
> decision, and evidence object into a traversable Authority Graph™.
>
> Every KYE decision comes with a **Decision Map™** &mdash; a
> replayable graph showing who or what acted, for whom, using which
> capability, under what authority, in what state, and with what
> evidence.

— KYE Protocol™ project, 2026.
