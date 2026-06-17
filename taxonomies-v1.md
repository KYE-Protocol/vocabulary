# KYE Protocol™ — Canonical taxonomies (V1)

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the 17 canonical dictionaries (`internal`) (post-§29 landing).
>
> KYE is **taxonomy-first**. Authority decisions need shared
> classification or every implementation invents different words for
> the same thing. V1 ships with 16 canonical taxonomies. Profiles MAY
> register additional taxonomies but MUST NOT redefine canonical
> terms.

## 1. The 16 V1 taxonomies

| # | Taxonomy ID                         | Purpose                                            |
|---|-------------------------------------|----------------------------------------------------|
| 1 | `kye:taxonomy:entity_type`          | Entity classes — humans, businesses, agents, services, models, tools, workflows. |
| 2 | `kye:taxonomy:entity_state`         | Lifecycle states — provisional, active, suspended, quarantined, stopped, tombstoned. |
| 3 | `kye:taxonomy:capability_type`      | Skill, tool, MCP tool, function, connector, playbook, model_profile, payment_action, api_operation. |
| 4 | `kye:taxonomy:capability_state`     | active, deprecated, broken, quarantined, revoked, superseded. |
| 5 | `kye:taxonomy:action_type`          | Verbs the runtime evaluates (read, write, transfer, payment.prepare, …). |
| 6 | `kye:taxonomy:resource_type`        | Wallet, dataset, document, vehicle, vessel, shipment. |
| 7 | `kye:taxonomy:data_class`           | Personal, financial, special-category, regulated, public. |
| 8 | `kye:taxonomy:side_effect_level`    | read / write / move_money / external_send / mutate_critical. |
| 9 | `kye:taxonomy:risk_state`           | nominal / elevated / watch / denylisted.            |
| 10| `kye:taxonomy:environment`          | dev / staging / production / regulated_production.  |
| 11| `kye:taxonomy:decision`             | allow / allow_with_constraints / require_approval / require_step_up / require_human_review / require_recovery / quarantine / deny. |
| 12| `kye:taxonomy:reason_code`          | Canonical reason codes referenced by every decision. |
| 13| `kye:taxonomy:evidence_type`        | Audit event, transparency receipt, evidence pack, payload artefact. |
| 14| `kye:taxonomy:compliance_framework` | EU_AI_ACT, ISO_42001, SOC2, ISO_27001, PCI_DSS, PSD3, DORA, NIS2, HIPAA, NIST_800_207. |
| 15| `kye:taxonomy:sector`               | Healthcare, financial_services, defence, energy, manufacturing, automotive, maritime, logistics, aviation, public_sector. |
| 16| `kye:taxonomy:jurisdiction`         | ISO-3166 jurisdictions plus EU as a regulatory bloc. |

## 2. Required signal types

Every taxonomy and metadata mutation MUST emit:

| Event                                | Emitted on                          |
|--------------------------------------|-------------------------------------|
| `kye.taxonomy.created`               | New taxonomy registered             |
| `kye.taxonomy.updated`               | Taxonomy metadata changed           |
| `kye.taxonomy.published`             | Version moved from draft to active  |
| `kye.taxonomy.deprecated`            | Term or version deprecated          |
| `kye.taxonomy.term_added`            | New term added to a taxonomy        |
| `kye.taxonomy.term_updated`          | Term metadata or status changed     |
| `kye.taxonomy.term_deprecated`       | Term marked deprecated              |
| `kye.taxonomy.mapping_created`       | Taxonomy term mapped to framework   |
| `kye.metadata.schema_created`        | New `KYEMetadataSchema` registered  |
| `kye.metadata.schema_updated`        | Schema fields or constraints changed |
| `kye.metadata.validation_failed`     | A metadata block failed validation  |
| `kye.metadata.classification_changed`| Classification field changed        |
| `kye.metadata.binding_created`       | Metadata bound to a subject URN     |
| `kye.metadata.binding_removed`       | Metadata binding removed            |

## 3. Use in copy

> **No authority without context.** KYE uses taxonomies and metadata
> to make every entity, capability, action, resource, risk, and
> evidence object governable.
>
> KYE is **taxonomy-first** and **metadata-first**, so every authority
> decision understands the entity, capability, resource, action, risk,
> sector, jurisdiction, state, and evidence context behind it.

— KYE Protocol™ project, 2026.
