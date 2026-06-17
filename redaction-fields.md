# KYE Protocol™ — Telemetry redaction field list

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> the canonical telemetry dictionary (`public/vocabulary/telemetry.md`).

Every telemetry-emitting Gateway MUST replace the values of the JSON
paths below with a per-tenant redaction token before export.

## 1. PII

`pii.full_name` · `pii.first_name` · `pii.last_name` ·
`pii.email` · `pii.phone` · `pii.address.line1` ·
`pii.address.line2` · `pii.address.postal_code` ·
`pii.address.country` · `pii.dob` · `pii.gov_id` ·
`pii.passport_number` · `pii.tax_id` · `pii.ssn` ·
`pii.driving_licence` · `pii.biometric_template`

## 2. Financial

`payment.account_number` · `payment.iban` · `payment.routing_number` ·
`payment.card_pan` · `payment.card_cvv` · `payment.card_expiry` ·
`payment.beneficiary.name` · `payment.beneficiary.address` ·
`treasury.wallet_address` · `custody.private_key_handle`

## 3. Healthcare

`healthcare.mrn` · `healthcare.diagnosis_codes` ·
`healthcare.medication_list` · `healthcare.lab_results` ·
`healthcare.notes_freetext` · `healthcare.insurance_id` ·
`healthcare.next_of_kin`

## 4. Authentication / secrets

`auth.password` · `auth.password_hash` · `auth.totp_secret` ·
`auth.recovery_code` · `auth.api_key` · `auth.bearer_token` ·
`auth.refresh_token` · `auth.session_id` · `auth.client_secret` ·
`auth.private_key_pem`

## 5. Capability invocations

`capability.input.user_message` · `capability.output.completion` ·
`capability.input.attached_file_bytes` ·
`capability.tool_arguments.user_supplied`

## 6. Free-form fields

Any field whose JSON path matches `*.notes` · `*.comment` ·
`*.message` · `*.body` and that is not on a structured-allowlist
(see `public/vocabulary/structured-allowlist.md`) is treated as
free-form and MUST be redacted.

— KYE Protocol™ project, 2026.
