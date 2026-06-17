# KYE™ Entity Types

This document lists the entity types KYE Protocol™ recognizes. Type names are stable identifiers used in entity records, policy inputs, and dictionaries.

This document defines **names only**. The lifecycle, validation rules, and attestation requirements for each type are part of the normative specification, which is published separately.

## Hierarchy

Every KYE™ entity resolves into one canonical containment tree (v3-final, locked 2026-05-14). The tree is parent-required at every node. Model, Tool, External App, and Audit Stream are **first-class Workspace-level entities** in v3 — they are not subtypes of Principal.

```
Tenant                                          (kye:tenant:…)    — billing + isolation root
  ├── Legal Entity                              (kye:lglent:…)    — registered company / regulator-facing legal person
  ├── Billing Account                           (kye:bill:…)      — Stripe customer + payment method + tax id
  ├── Domains                                   (kye:dom:…)       — verified DNS domains, branded URLs
  ├── Policies                                  (kye:pol:…)       — active Operating Model™, rule bundles, attestations
  └── Workspaces                                (kye:wsp:…)        — environment / dataspace (prod, sandbox, region-specific)
        ├── Projects                            (kye:prj:…)       — units of work; scoped budgets + quotas
        ├── Teams                               (kye:team:…)      — RBAC + ownership group
        ├── Resources                           (kye:res:…)       — D1 tables, R2 buckets, queues, connectors
        ├── Principals                          (kye:prin:…)      — the acting parties (Human / System / Agent)
        ├── Models                              (kye:model:…)     — inference artefacts; versioned
        ├── Tools                               (kye:tool:…)      — named callables; declared side-effects
        ├── External Apps                       (kye:extapp:…)    — 3rd-party integrations; partner connectors
        └── Audit Streams                       (kye:audstream:…) — append-only event destinations (SIEM, S3, Kafka)
```

Each entity carries a `state` field governed by a registered state machine (see `public/vocabulary/state-machines.md`). Every entity also carries a `state_machine_id` identifying which machine governs it. Relationships between entities are explicit typed edges (see `public/vocabulary/relationships.md`).

### Tenant-level siblings (5)

| Sibling | Stable type | ID class | Required parent | Purpose |
|---|---|---|---|---|
| Legal Entity     | `legal_entity`    | `lglent`    | `tenant_id` | registered legal person; regulator-facing record (company number, country, jurisdiction). One Tenant MAY hold multiple Legal Entities (group structure, foreign subsidiaries). |
| Billing Account  | `billing_account` | `bill`      | `tenant_id` | Stripe customer id, default payment method, billing email, tax id, currency. One Tenant MAY hold multiple Billing Accounts (split billing per business unit). |
| Domains          | `domain`          | `dom`       | `tenant_id` | verified DNS domains the Tenant owns (`acme.com`, `acme-uk.com`). Used for branded sender, federation routing, SSO. |
| Policies         | `policy_bundle`   | `pol`       | `tenant_id` | active Operating Model™, rule bundles, attestation policies, sub-processor list. One Tenant MAY hold multiple Policy Bundles (one per regime: PRA / DORA / EU AI Act). |
| Workspaces       | `workspace`       | `wsp`       | `tenant_id` | environment / dataspace. One Tenant MAY hold many Workspaces (prod / sandbox / eu-west-1 / consumer-bank / corporate-bank). |

### Workspace-level siblings (8)

| Sibling | Stable type | ID class | Required parent | Purpose |
|---|---|---|---|---|
| Projects      | `project`      | `prj`       | `workspace_id` | unit of work; scoped budget + quota; one Operating Model fragment per Project |
| Teams         | `team`         | `team`      | `workspace_id` | RBAC + ownership group; who-owns-what; bounded delegation surface; approval routing |
| Resources     | `resource`     | `res`       | `workspace_id` | D1 tables, R2 buckets, queues, connectors that live inside the workspace. Resources are leaves — they don't contain other entities |
| Principals    | `principal`    | `prin`      | `workspace_id`; `team_id` optional | the acting party — referenced as `actor_entity_id` / `principal_entity_id` in every Decision Map™ row |
| Models        | `model`        | `model`     | `workspace_id` | an inference artefact (LLM, vision model, embedding model); carries `provider`, `family`, `version`, `weights_hash`. First-class in v3. |
| Tools         | `tool`         | `tool`      | `workspace_id` | a named callable (function, MCP tool, API endpoint); carries `function_signature`, `declared_capabilities[]`, `side_effects[]`. First-class in v3. |
| External Apps | `external_app` | `extapp`    | `workspace_id` | a 3rd-party integration or partner connector acting on behalf of the tenant; carries `partner_org_id`, `connector_kind`, `oauth_subject`. First-class in v3. |
| Audit Streams | `audit_stream` | `audstream` | `workspace_id` | an append-only event-log destination the Workspace writes to (SIEM, S3, Splunk, Kafka topic); governed by an authority grant, not an IAM binding. New in v3. |

### Principal subtypes (v3: 4 subtypes)

In v3, `principal_class` has exactly four values — `human`, `system`,
`agent`, and `external_app` (the schema enum on
`kye.entity.principal.v1`, "reduced from six to four"). The v2 values
`model` and `tool` are **deprecated** — promoted to standalone entity
classes (`kye:model:…`, `kye:tool:…`). `external_app` is retained as a
principal_class (a 3rd-party integration acting on behalf of the tenant)
and ALSO exists as a standalone entity class (`kye:extapp:…`, see the
table above). See `constitution/DEVIATIONS.md` for the migration window.

Every Principal MUST resolve to exactly one subtype via its `principal_class` field:

| Subclass | Examples | Subclass-specific fields |
|---|---|---|
| `human`  | person, employee, contractor, operator, approver, auditor, regulator, customer, patient, support_user | full_name, email_hash, idp_subject, role |
| `system` | workload, service_account, api_client, serverless_function, container, vm, cluster, runtime, queue_consumer, webhook_endpoint, connector | service_principal_id, runs_in_workspace, owning_team_id |
| `agent`  | ai_agent, agent_runtime | model_entity_id (→ `kye:model:…`), tool_entity_ids[] (→ `kye:tool:…`), operating_loop_kind |
| `external_app` | 3rd-party integration / partner connector acting on behalf of the tenant | partner_org_id, connector_kind, oauth_subject |

Note that in v3 an `agent` Principal references its Model via a
`kye:model:…` entity ID and its Tools via `kye:tool:…` entity IDs —
it does not embed them as subtypes.

The hierarchy is enforced at schema time (`kye.entity.{tenant, legal_entity, billing_account, domain, policy_bundle, workspace, project, team, resource, principal, model, tool, external_app, audit_stream}.v1`) and at runtime by the PDP. KYE Onboarding Agent™ auto-creates a default Workspace + Team + admin Principal for every newly-granted Tenant so existing API keys, decisions, and audit rows always resolve to a valid parent chain.

## Human entities

| Type | Description |
|---|---|
| `person` | A natural person |
| `employee` | A person employed by a legal entity |
| `contractor` | A person engaged under a service contract |
| `operator` | A person operating a system or workflow |
| `approver` | A person empowered to approve actions |
| `auditor` | A person performing audit review |
| `regulator` | A regulatory authority representative |
| `customer` | A consumer of a product or service |
| `patient` | A patient in a healthcare context |
| `support_user` | A support-context user |

## Organizational entities

| Type | Description |
|---|---|
| `business` | A commercial organization |
| `legal_entity` | A registered legal entity |
| `subsidiary` | A subsidiary of a parent company |
| `parent_company` | A parent company |
| `department` | A department within an organization |
| `team` | A team within an organization |
| `public_authority` | A public-sector authority |
| `processor` | A data processor |
| `subprocessor` | A sub-processor |
| `supplier` | A supplier or vendor |
| `relying_party` | A relying party in an identity exchange |

## Technical entities

| Type | Description |
|---|---|
| `workload` | A running computational unit |
| `service_account` | A non-human service identity |
| `api_client` | An API client |
| `serverless_function` | A serverless function |
| `container` | A container instance |
| `vm` | A virtual machine |
| `cluster` | A compute cluster |
| `runtime` | A runtime environment |
| `connector` | An integration connector |
| `webhook_endpoint` | A webhook receiver |
| `queue_consumer` | A message-queue consumer |

## AI entities

| Type | Description |
|---|---|
| `ai_agent` | An AI agent |
| `agent_runtime` | An AI agent runtime |
| `model` | A model |
| `model_version` | A specific model version |
| `prompt_template` | A prompt template |
| `memory_store` | An agent memory store |
| `vector_index` | A vector index |
| `tool` | A tool or plugin |
| `guardrail` | A guardrail component |
| `evaluator` | An evaluator component |
| `workflow` | A multi-step workflow |

## Credential entities

| Type | Description |
|---|---|
| `key` | A cryptographic key |
| `api_key` | An API key |
| `jwt` | A JWT-formatted credential |
| `certificate` | An X.509 certificate |
| `x509_svid` | A SPIFFE X.509 SVID |
| `jwt_svid` | A SPIFFE JWT SVID |
| `verifiable_credential` | A W3C verifiable credential |
| `delegation_credential` | A delegation credential |
| `scope_credential` | A scope credential |
| `approval_credential` | An approval credential |

## Data and resource entities

| Type | Description |
|---|---|
| `dataset` | A dataset |
| `database` | A database |
| `table` | A database table |
| `file` | A file |
| `document` | A document |
| `record` | A record |
| `payment_instruction` | A payment instruction |
| `clinical_record` | A clinical record |
| `cardholder_object` | A cardholder data object (regulated) |
| `evidence_pack` | A compliance evidence pack |
| `policy_bundle` | A policy bundle |

## Naming rules

+ Type names are lowercase ASCII with underscores.
+ Type names are stable identifiers and must not be reused for unrelated semantics.
+ Adding a new type requires a vocabulary proposal. Mechanism details are out of scope for this document.
