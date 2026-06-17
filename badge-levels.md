# KYE Conformance Badge Levels (canonical)

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the `conformance-certification` rule pack + `badge-levels` dictionary (post-§29 landing).

KYE distinguishes **conformant** (passes a test suite) from **certified**
(reviewed + listed in the public registry). Six tiers plus four
profile-scoped variants.

## Trust hierarchy

| Level | Badge                              | Awarded by             | Renewal  |
|-------|------------------------------------|------------------------|----------|
| L0    | KYE Declared / Compatible          | Self                   | n/a      |
| L1    | **KYE Self-Tested™**               | Self (open suite)      | quarterly |
| L2    | **KYE Self-Attested™**             | Self (signed)          | quarterly |
| L3    | **KYE Conformant™** + variants     | Program (verified run) | annual |
| L4    | **KYE Certified™**                 | Program + reviewer   | annual   |

## L3 variants (issued separately)

- KYE Core Conformant™
- KYE Authority Conformant™
- KYE Capability Conformant™
- KYE Evidence Conformant™
- KYE Recovery Conformant™
- KYE Payments Conformant™
- KYE Healthcare Conformant™
- KYE Sector Profile Conformant™ *(parameterised — banking / energy / aviation / …)*
- KYE EU AI Act Profile Ready™

## Permitted commercial wording

| Wording                  | Permitted? | Notes                                                |
|--------------------------|-----------|------------------------------------------------------|
| **KYE Conformant™**      | ✓          | Backed by a passing run against a published suite    |
| **KYE Certified™**       | ✓          | Only after program review + signed registry record |
| **KYE Self-Tested™**     | ✓          | Free badge after running the open conformance pack   |
| **KYE Self-Attested™**   | ✓          | Free badge after a signed self-audit declaration     |
| **KYE Ready™**           | ✓          | Soft go-to-market label for partner ecosystem        |
| **Powered by KYE™**      | ✓          | Uses KYE APIs / SDKs (no certification claim)        |
| KYE Compliant            | ⚠ avoid    | Reads as legal / regulatory; reserve for sector use  |

## Required evidence per badge

| Badge                 | Evidence required                                                |
|-----------------------|------------------------------------------------------------------|
| KYE Self-Tested™      | `conformance-run.json` (passed)                                  |
| KYE Self-Attested™    | `self-audit-run.json` + `self-attestation.json` (signed)         |
| KYE Conformant™ (L3)  | `conformance-run.json` (verified) + `certification-record.json`  |
| KYE Certified™ (L4)   | L3 evidence + manual review + signed `certification-record.json` listed in registry |

Every badge MUST be tied to: protocol version · profile-set version ·
test-suite version · product / version · expiry · public verification
URL · revocation status · signed certification record. Permanent
badges are **not permitted**.

## Use in copy

> **KYE Conformance & Certification** lets customers verify that an
> implementation correctly supports entity authority, state,
> delegation, capability governance, decisions, audit trails,
> evidence packs, and Decision Maps™.
>
> **Govern the governance layer.** KYE implementations can
> continuously audit their own engines, schemas, profiles, registries,
> policies, decisions, audit trails, evidence packs, and Decision
> Maps™ — then publish signed self-attestations or pursue official
> KYE certification.

— KYE Protocol™ project, 2026.
