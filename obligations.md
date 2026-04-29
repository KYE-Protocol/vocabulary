# KYE™ Obligation Vocabulary

Obligations are named requirements that may attach to a policy decision. This document lists obligation names recognized by KYE™.

The way obligations are evaluated, enforced, and proved is part of the normative specification.

## Audit and proof

| Obligation | Meaning |
|---|---|
| `audit.emit` | An audit event must be emitted |
| `proof.required` | A proof artifact must be produced |
| `transparency.submit` | A signed statement must be submitted to a transparency service |
| `trace.capture.required` | Execution trace must be captured |

## Data handling

| Obligation | Meaning |
|---|---|
| `redaction.required` | Output must be redacted |
| `watermark.required` | Output must be watermarked |
| `citable.output.required` | Output must include citations |
| `external.send.block` | Output must not be sent externally |
| `memory.write.block` | Memory writes are blocked |

## Approval and review

| Obligation | Meaning |
|---|---|
| `approval.required` | Human approval is required |
| `human.review.required` | Human review is required |
| `dry_run.only` | Action is permitted in dry-run only |
| `break_glass.justification.required` | Break-glass justification is required |

## Monitoring

| Obligation | Meaning |
|---|---|
| `monitor.realtime` | Real-time monitoring is required |
| `tool.allowlist.enforce` | Tool allowlist must be enforced |
| `high_risk.decision.block` | High-risk decisions must be blocked |
