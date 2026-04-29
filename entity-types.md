# KYE™ Entity Types

This document lists the entity types KYE™ recognizes. Type names are stable identifiers used in entity records, policy inputs, and dictionaries.

This document defines **names only**. The lifecycle, validation rules, and attestation requirements for each type are part of the normative specification, which is published separately.

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

- Type names are lowercase ASCII with underscores.
- Type names are stable identifiers and must not be reused for unrelated semantics.
- Adding a new type requires a vocabulary proposal. Mechanism details are out of scope for this document.
