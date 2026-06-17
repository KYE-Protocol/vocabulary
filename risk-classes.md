# Risk classes

Canonical risk tier vocabulary used by the KYE Risk Engine™. Five tiers, EU-AI-Act-aligned, with explicit per-framework floor mappings.

| Tier | Score range | Meaning | Mandatory controls |
|---|---|---|---|
| **`minimal`** | 0–20 | Effectively negligible risk — spam filters, recommendation systems on entertainment, AI-assisted typing. | None. Lifecycle logging recommended. |
| **`limited`** | 20–50 | Transparency-only risk — must disclose AI involvement to the natural person (EU AI Act Art. 50). | Identification disclosure; audit-chain emission of every interaction. |
| **`high`** | 50–85 | Conformity assessment required (EU AI Act Annex III: biometric ID, education, employment, essential public services, law enforcement, migration, justice, democratic processes). | Dual-channel sign-off; scenario testing before action; replay-proof generation; human-in-the-loop for irreversibles. |
| **`unacceptable`** | 85–99 | Exceeds high-tier controls — only deployable with regulator-approved derogation. | Every high-tier control PLUS regulator notification, ≤1-hour kill-switch SLA, dual-signed Operating Model amendment. |
| **`prohibited`** | 99–100 | The Risk Engine MUST block. Mirrors EU AI Act Art. 5 prohibited practices: social scoring by public authorities, real-time remote biometric identification in public spaces, exploitation of vulnerabilities, subliminal manipulation. | Decision Engine returns deny + reason `PROHIBITED_PRACTICE`. No Operating Model amendment can override. |

## Per-framework floor mappings

| Tier | EU AI Act | DORA | GDPR | NIST AI RMF | ISO 42001 | FCA OpRes | PCI DSS | SOX |
|---|---|---|---|---|---|---|---|---|
| `minimal` | minimal | non_critical | normal | map_1 | low | non_important | non_chd | non_icfr |
| `limited` | limited | non_critical | normal | map_2 | low | non_important | non_chd | non_icfr |
| `high` | high | critical_or_important | high | map_3 | high | important_business_service | chd_present | icfr_relevant |
| `unacceptable` | unacceptable | critical_or_important | high | map_4 | high | important_business_service | chd_present | icfr_relevant |
| `prohibited` | prohibited | critical_or_important | high | map_4 | high | important_business_service | chd_present | icfr_relevant |

## Source files

| Artefact | Path |
|---|---|
| Canonical dictionary | `internal` |
| Schema | `internal` |
| Example | `public/examples/risk-assessment.json` |
| Runtime engine | `internal` |
| HTTP agent | `internal` |
| OpenAPI rail | `internal` |
| Mechanism | `internal` |
| Patent | `internal` |
