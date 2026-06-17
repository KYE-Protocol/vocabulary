# KYE Protocol™ — Payments decision and lifecycle codes

> **Status:** Normative. v1.0. Apache 2.0. Companion to
> `internal` + `internal`.

This file enumerates the public payment decision codes, hold reasons,
reversal reasons, and dispute outcomes used by the KYE-Payments profile
and its overlays (EU, Card, High-Assurance).

## 1. sPDP decisions

`payment.allow` · `payment.allow_with_constraints` ·
`payment.require_approval` · `payment.deny`

## 2. Deny reason codes

`payment.deny.amount_above_authority_cap` ·
`payment.deny.currency_not_in_scope` ·
`payment.deny.rail_not_in_scope` ·
`payment.deny.beneficiary_not_in_allowlist` ·
`payment.deny.beneficiary_in_denylist` ·
`payment.deny.sanctions_screen_failed` ·
`payment.deny.kyc_step_up_required` ·
`payment.deny.aml_threshold_exceeded` ·
`payment.deny.payment_authority_revoked` ·
`payment.deny.delegation_revoked` ·
`payment.deny.attestation_stale` ·
`payment.deny.risk_state_blocked` ·
`payment.deny.daily_velocity_exceeded` ·
`payment.deny.weekly_velocity_exceeded` ·
`payment.deny.monthly_velocity_exceeded`

## 3. Approval-required reason codes

`payment.approval.amount_above_minor_threshold` ·
`payment.approval.amount_above_major_threshold` ·
`payment.approval.cross_border_first_time` ·
`payment.approval.high_risk_corridor` ·
`payment.approval.beneficiary_first_time` ·
`payment.approval.psd2_sca_required` ·
`payment.approval.regulatory_dual_control`

## 4. Hold reason codes

`payment.hold.risk_review` · `payment.hold.sanctions_screen` ·
`payment.hold.kyc_step_up` · `payment.hold.fraud_review` ·
`payment.hold.regulatory_block` · `payment.hold.rail_pending` ·
`payment.hold.cutoff_window` · `payment.hold.dispute_pending`

## 5. Reversal reason codes

`payment.reversal.initiator_request` ·
`payment.reversal.fraud_detected` ·
`payment.reversal.duplicate_submission` ·
`payment.reversal.amount_correction` ·
`payment.reversal.beneficiary_invalid` ·
`payment.reversal.regulatory_finding` ·
`payment.reversal.sanctions_match`

## 6. Dispute reason codes

`payment.dispute.unauthorized` ·
`payment.dispute.fraud_card_present` ·
`payment.dispute.fraud_card_not_present` ·
`payment.dispute.product_not_received` ·
`payment.dispute.product_not_as_described` ·
`payment.dispute.duplicate` ·
`payment.dispute.amount_disagreement` ·
`payment.dispute.credit_not_processed` ·
`payment.dispute.cancelled_recurring` ·
`payment.dispute.regulatory_chargeback`

## 7. Charge-back outcomes

`payment.charged_back.evidence_insufficient` ·
`payment.charged_back.regulatory_finding` ·
`payment.charged_back.merchant_no_response` ·
`payment.charged_back.fraud_confirmed`

## 8. Dispute-resolved outcomes

`payment.dispute_resolved.evidence_sufficient` ·
`payment.dispute_resolved.merchant_credit_issued` ·
`payment.dispute_resolved.cardholder_withdrew` ·
`payment.dispute_resolved.arbitration_in_favour`

## 9. Reconciliation outcomes

`payment.reconciled.matched` ·
`payment.reconciled.matched_with_variance` ·
`payment.reconciled.unmatched` ·
`payment.reconciled.late`

## 10. Settlement events

`payment.settlement.posted` ·
`payment.settlement.deferred` ·
`payment.settlement.failed` ·
`payment.settlement.partial`

## 11. ISO 20022 message-class alignment

Used by the High-Assurance overlay only:

`pacs.008` (FIToFICustomerCreditTransfer) ·
`pacs.009` (FinancialInstitutionCreditTransfer) ·
`pacs.004` (PaymentReturn) ·
`pacs.002` (FIToFIPaymentStatusReport) ·
`camt.054` (BankToCustomerDebitCreditNotification)

— KYE Protocol™ project, 2026.
