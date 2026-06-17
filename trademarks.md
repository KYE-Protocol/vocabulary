# KYE Protocol™ — protected trademark dictionary (SSOT)

This is the **single source of truth** for every protected mark of the
KYE Protocol™ project. Every public-facing surface (this site, the
whitepaper, the legal page, READMEs, blog posts, SDK docs) must carry
the ™ symbol on the **first prominent use** of any of these marks
within a single page or document. Subsequent uses on the same page
may drop the symbol.

The audit script `scripts/audit-trademarks.mjs` enforces this against
`public/site/*.html` on every `npm test` run, so first-prominent-use
gaps cannot land on `main` undetected.

The structured form of this list is at
[`trademarks.json`](trademarks.json) — that file is what the audit
script reads.

## Protected marks (15)

| # | Mark | Class | Notes |
|---|---|---|---|
| 1 | **KYE™** | wordmark | Short form; standalone references |
| 2 | **KYE Protocol™** | wordmark | Full name of the protocol |
| 3 | **Know Your Entity™** | descriptive wordmark | Source of the KYE acronym |
| 4 | **Authority Finality™** | concept mark | The protocol-level *property*: an action's chain is provably terminal — six bound fields signed and replayable |
| 4a | **KYE Chain of Authority™** | concept mark | The *structural artefact*: the linked, attenuating delegation chain from root principal down to the actor. Narrative parallel to chain-of-custody for documents. KYE prefix mitigates §2(e) descriptiveness refusal on the bare phrase. |
| 5 | **Authority Graph™** | concept mark | Graph projection of authority |
| 6 | **Decision Map™** | concept mark | Per-decision projection |
| 7 | **Evidence Graph™** | concept mark | Evidence projection |
| 8 | **Blast Radius Map™** | concept mark | Compromise-cascade projection |
| 9 | **Compliance Map™** | concept mark | Framework-control projection |
| 10 | **KYE Compliance Mapping Rail™** | infrastructure mark | Runtime → control binding |
| 11 | **KYE Cloud Gateway™** | commercial mark | Hosted commercial offering |
| 11a | **KYE Reference Gateway™** | implementation mark | The protocol's open-source reference implementation. Ships under commercial licence to design partners. |
| 11b | **KYE Runtime Gateway™** | implementation mark | Generic name for any production-grade KYE™ Gateway deployment built on the reference. |
| 12 | **KYE Conformant™** | certification mark | L3 conformance badge |
| 13 | **KYE Certified™** | certification mark | L4 certification badge |
| 14 | **KYE Self-Tested™** | certification mark | L1 self-test badge |
| 15 | **KYE Self-Attested™** | certification mark | L2 self-attestation badge |
| 16 | **KYE Core Conformant™** | certification mark (capability-scoped) | Core authority + delegation + scope + state + audit + decision-code fixtures. Program in development. |
| 17 | **KYE Authority Conformant™** | certification mark (capability-scoped) | Authority Finality™ binding tested end-to-end. Program in development. |
| 18 | **KYE Capability Conformant™** | certification mark (capability-scoped) | Capability registry + grant + invoke + quarantine + cascade fixtures. Program in development. |
| 19 | **KYE Evidence Conformant™** | certification mark (capability-scoped) | Evidence Pack™ generation, signing, replay and OSCAL projection. Program in development. |
| 20 | **KYE Sovereign AI Profile™** | profile | Umbrella connector profile family for sovereign / national AI ecosystems. v1.1 preview. |
| 21 | **KYE Public Sector Profile™** | profile | Agency + civil-servant + citizen-service authority binding. v1.1 preview. |
| 22 | **KYE National AI Agent Profile™** | profile | Registry + capability + permitted-action binding for AI agents at national scale. v1.1 preview. |
| 23 | **KYE Government API Authority Profile™** | profile | Pre-authorisation hook for government APIs. v1.1 preview. |
| 24 | **KYE Public Services Evidence Profile™** | profile | Evidence-pack format for citizen-impacting AI-assisted decisions. v1.1 preview. |
| 25 | **KYE Sovereign Data Access Profile™** | profile | Dataset + data-space authority + provenance binding. v1.1 preview. |
| 26 | **KYE Sovereign Model Registry Profile™** | profile | Model entity + risk state + permitted-action binding. v1.1 preview. |
| 27 | **KYE Cross-Agency Delegation Profile™** | profile | Ministerial + agency + regulatory delegation binding. v1.1 preview. |
| 28 | **KYE National Sandbox Profile™** | profile | Supervisor + participant authority binding for regulated sandboxes. v1.1 preview. |
| 29 | **KYE Sovereign AI Authority Gateway™** | app | Runtime authority gateway for sovereign AI ecosystems. Planned commercial app. |
| 30 | **KYE National AI Agent Registry™** | app | Register and govern AI agents, models, datasets at national scale. Planned commercial app. |
| 31 | **KYE Public Sector Decision Map™** | app | Replay AI-assisted public-sector decisions. Planned commercial app. |
| 32 | **KYE Sovereign AI Evidence Pack™** | app | Evidence-pack format + viewer for sovereign AI ecosystems. Planned commercial app. |
| 33 | **KYE National Sandbox Authority Harness™** | app | Sandbox harness for regulated national AI / open-finance / healthcare programs. Planned commercial app. |
| 34 | **KYE Authority Wallet™** | app | Mobile authority-control + proof app for AI-agent actions. Create agents, grant scoped authority, approve / deny / revoke, inspect Decision Map™, view evidence packs. |
| 35 | **KYE Authority Wallet Demo™** | app | Proprietary mobile demo (Expo / React Native). Synthetic data, simulated agent / payment flows. |
| 36 | **KYE Authority Wallet Pro™** | commercial | Paid production version. Real Gateway integration, enterprise approval workflows, push notifications, evidence archive. Planned. |
| 37 | **KYE Mobile Approval Gateway™** | commercial | Enterprise mobile-approval module for banks, payments, healthcare, legal. Push-approval-as-part-of-decision. Planned. |
| 38 | **KYE Continuity Profile™** | profile | Preserves the chain between intent, interpretation, delegated authority, state, decision, execution and evidence. v1.0. |
| 39 | **Authority Continuity™** | concept | Authority remained continuous from intent to action. |
| 40 | **Agency Continuity™** | concept | Same property in agentic-systems language. |
| 41 | **Continuity Decision Map™** | concept | Per-continuity-decision projection. |
| 42 | **Continuity Evidence Pack™** | concept | Replayable bundle for one continuity check. |
| 43 | **Delegated Agency Graph™** | concept | Cross-chain visualisation. |
| 44 | **KYE Continuity Gateway™** | app | Runtime gateway for continuity checks. Planned. |
| 45 | **KYE Intent Trace App™** | app | Signal → action visualiser. Planned. |
| 46 | **KYE Agency Drift Monitor™** | app | Drift detection + alerting. Planned. |
| 47 | **KYE Discoverability Profile™** | profile | Policy-filtered discovery of KYE entities, authorities, capabilities, decisions, evidence, profiles, connectors. v1.0. |
| 48 | **KYE Authority Directory™** | app | Searchable directory of entities, agents, capabilities, grants and profiles. Planned. |
| 49 | **KYE Discovery Console™** | app | Enterprise search + investigation console. Planned. |
| 50 | **KYE Authority Path Finder™** | app | Find principal → delegation → actor → capability paths. Planned. |
| 51 | **KYE Evidence Finder™** | app | Search and verify decisions, audit events and evidence packs. Planned. |
| 52 | **KYE Connector Discovery Hub™** | app | Discover profiles, connectors, apps, plugins and certified implementations. Planned. |
| 53 | **KYE Ontology Profile™** | profile | Semantic layer — shared meaning of entities, authorities, capabilities, scopes, states, decisions, evidence, profiles, connectors and sectors. v1.0. |
| 54 | **KYE Semantic Layer™** | concept | Product-friendly synonym for KYE Ontology Profile™. |
| 55 | **KYE Ontology Registry™** | app | Managed registry for terms, relationships, mappings and semantic assertions. Planned. |
| 56 | **KYE Semantic Authority Mapper™** | app | Maps OAuth scopes, IAM roles, payment mandates, legal delegations, healthcare consents into KYE’s authority model without losing meaning. Planned. |
| 57 | **KYE Semantic Graph™** | app | Graph view of the ontology + live instances; semantic-path search and risk-ranked traversal. Planned. |
| 58 | **KYE Ontology Conformance™** | app | Conformance fixture suite + certification track for ontology-correct implementations. Planned. |
| 59 | **KYE Operating Model Profile™** | profile | Enterprise adoption layer — journey from use-case intake to runtime authority control. v1.0. |
| 60 | **KYE AI Worker Readiness App™** | app | Readiness assessment for AI workers — pilot / controlled / production. Planned. |
| 61 | **KYE Entity Authority Record™** | concept | Living governance record per delegated actor. |
| 62 | **KYE Authority Gates™** | concept | Runtime gates before high-impact AI actions. |
| 63 | **KYE Authority Gate Designer™** | app | Visual gate composer + simulator. Planned. |
| 64 | **KYE Commit Boundary™** | concept | Separates recommendation from committed action. |
| 65 | **KYE Commit Boundary Monitor™** | app | Runtime monitor for recommendation→committed-action transitions. Planned. |
| 66 | **KYE Governed Entity Catalog™** | app | Discovery surface for governed agents, models, tools, services, connectors, apps and certified implementations. Planned. |
| 67 | **KYE Cloud Portal™** | app | Enterprise dashboard for the operating-model journey + runtime evidence. Planned. |
| 68 | **KYE Academy™** | app | Training and certification track for KYE Operating Model Profile™ owners and operators. Planned. |
| 69 | **KYE Assurance Card Profile™** | profile | Lifecycle assurance layer that turns runtime evidence into a living assurance record. v1.0. |
| 70 | **KYE Assurance Card™** | concept | Living lifecycle assurance record per delegated entity. |
| 71 | **KYE Assurance Card Builder™** | app | Generate living assurance cards from KYE runtime objects. Planned. |
| 72 | **KYE Assurance Card Library™** | app | Discoverable library of governed AI use cases + assurance patterns. Planned. |
| 73 | **KYE Human Involvement Planner™** | app | Define where authorised humans must review, approve, limit or override AI-enabled actions. Planned. |
| 74 | **KYE Human Involvement Plan™** | concept | Schema-bound record of human-judgement points across the lifecycle of a delegated AI system. |
| 75 | **KYE Provenance & Supply Chain Evidence App™** | app | Track datasets, models, tools, suppliers, licences and hardware lineage. Planned. |
| 76 | **KYE AI Supply Chain & Provenance Profile™** | concept | Provenance + supply-chain dimension of an assurance card subject. |
| 77 | **KYE Assurance Review Scheduler™** | app | Scheduled + event-triggered + scope-change + incident + retention + decommissioning review cycles. Planned. |
| 78 | **KYE Assurance Review Cycle™** | concept | Schema-bound review lifecycle for an assurance-card subject. |
| 79 | **KYE Governed Use Case Library™** | app | Sector-curated library of governed AI use cases linking authority records, gates, commit boundaries, decisions, evidence packs and assurance cards. Planned. |
| 80 | **KYE Formal Rules Profile™** | profile | Rights, obligations and governance layer — permissions, obligations, prohibitions, powers, exceptions and governance meta-rules as machine-readable authority objects. v1.0. |
| 81 | **KYE Rights & Obligations Engine™** | app | Runtime engine evaluating permissions, obligations, prohibitions, powers, exceptions and governance rules. Planned. |
| 82 | **KYE Obligation Ledger™** | app | Append-only ledger tracking every obligation lifecycle. Planned. |
| 83 | **KYE Rule Prover™** | app | Pre-runtime consistency checker for rule sets. Planned. |
| 84 | **KYE Rule Compiler™** | app | Compiles formal KYE rules into runtime PDP/PEP policies, authority gates, commit boundaries, signal events and evidence requirements. Planned. |
| 85 | **KYE Contract-to-Authority Mapper™** | app | Extracts permissions, obligations, prohibitions and powers from contracts into KYE formal rules. Planned. |
| 86 | **KYE Action Admissibility Profile™** | profile | Upstream pre-action layer — checks whether a proposed action is admissible into the authority pipeline before any authority / formal-rule / commit-boundary check runs. v1.0. |
| 87 | **KYE Admissibility Engine™** | app | Runtime engine performing the admission check across intent, source, data, policy and rule dimensions. Planned. |
| 88 | **KYE Admission Gate™** | concept | The gate object the Admissibility Engine evaluates, placed UPSTREAM of authority gates. |
| 89 | **KYE Pre-Action Filter™** | concept | Product-friendly synonym for the admission surface. |

## Markup convention

In HTML, the canonical first-prominent-use markup is:

```html
KYE Protocol<span class="tm">™</span>
```

Plain `™` is also accepted (the audit script counts both). The
`<span class="tm">` wrapper is preferred for reduced font size on
the symbol.

## What the audit checks

For each HTML file under `public/site/`, the audit:

1. Finds the **first occurrence** of each mark (case-sensitive).
2. Verifies that occurrence is immediately followed by either
   `<span class="tm">™</span>` or `™` (within ~50 characters,
   to account for nested tags or whitespace).
3. Skips files where the mark never appears.
4. Reports any first-prominent use without ™ as a hard failure.

The script is intentionally strict: subsequent uses on the same
page are not checked, but the first one must be ™-marked.

## When you add a new protected mark

1. Add the mark to `trademarks.json` (and refresh the table above).
2. Update the universal footer-bottom notice in every page under
   `public/site/` (search for `are trademarks of the KYE Protocol`).
3. Update the legal page §2 (`public/site/legal.html#trademark`)
   and the legal-faq (`public/site/legal-faq.html#trademark-faq`).
4. Run `npm run test:trademarks` locally to confirm the new mark
   is correctly flagged everywhere it appears.

---

This file is published under Apache License 2.0 with the rest of the
public protocol surface. The marks themselves remain trademarks of
the KYE Protocol™ project; reproducing this dictionary does not
grant any right to use the marks beyond the [trademark policy](../site/legal.html#trademark).
