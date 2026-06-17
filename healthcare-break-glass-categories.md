# KYE Protocol™ — Healthcare break-glass categories

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> `internal` and `internal`.

A break-glass grant in the Healthcare profile MUST carry a
category-coded `reason_code` from the list below. Categories drive the
post-hoc-review SLA, the audit retention class, and the regulator
notification rule.

## 1. Emergency clinical categories

`healthcare.bg.emergency_treatment` —
imminent threat to life or limb; care provider invoking break-glass
without prior consent. Post-hoc review: ≤ 24 h.

`healthcare.bg.unconscious_patient` —
patient cannot give consent; authorised next-of-kin not yet reached.
Post-hoc review: ≤ 48 h.

`healthcare.bg.public_health_emergency` —
declared public-health emergency (e.g. mass-casualty event) authorising
broader access. Post-hoc review: ≤ 72 h; regulator notified.

`healthcare.bg.psychiatric_hold` —
involuntary hold under jurisdictional mental-health statute. Post-hoc
review: ≤ 24 h; legal counsel CC'd.

## 2. Care-coordination categories

`healthcare.bg.care_handoff_emergency` —
unplanned transfer of patient (e.g. interhospital). Post-hoc review:
≤ 24 h.

`healthcare.bg.dependent_care` —
parent / guardian acting for a minor or dependent without contemporaneous
consent. Post-hoc review: ≤ 7 days.

## 3. Investigative categories

`healthcare.bg.research_waiver` —
research access under an IRB / ethics-board waiver; authority bound to
the waiver attestation. Post-hoc review: ≤ 30 days.

`healthcare.bg.fraud_investigation` —
internal investigation of suspected fraud; authority bound to a
compliance-officer attestation. Post-hoc review: ≤ 30 days.

`healthcare.bg.law_enforcement_subpoena` —
court-issued subpoena; authority bound to subpoena attestation.
Post-hoc review: ≤ 30 days; legal counsel CC'd.

`healthcare.bg.regulatory_audit` —
regulator-issued audit demand. Post-hoc review: ≤ 30 days.

## 4. Operational categories

`healthcare.bg.system_recovery` —
recovery of records during a system outage where normal authority is
unreachable. Post-hoc review: ≤ 48 h.

`healthcare.bg.data_subject_request_extraordinary` —
extraordinary data-subject access request (e.g. emergency disclosure to
the patient themselves). Post-hoc review: ≤ 7 days.

## 5. Forbidden categories (MUST be rejected)

`healthcare.bg.curiosity` ·
`healthcare.bg.unauthorised_research` ·
`healthcare.bg.commercial_disclosure` ·
`healthcare.bg.media_disclosure`

A break-glass request whose `reason_code` is in §5 MUST be rejected
with `reason_code=break_glass_category_forbidden`.

— KYE Protocol™ project, 2026.
