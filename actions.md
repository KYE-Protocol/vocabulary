# KYE™ Action Vocabulary

Actions are stable identifiers for governed operations. This document lists action names recognized by KYE™.

This document defines **names only**. Action semantics, side effects, and required obligations are part of the normative specification.

## Entity lifecycle

```
entity.register
entity.verify
entity.suspend
entity.stop
entity.quarantine
entity.revoke
entity.archive
entity.tombstone
entity.transfer
```

## Identifiers and relationships

```
identifier.bind
identifier.verify
identifier.revoke
relationship.create
relationship.revoke
```

## Delegations and scopes

```
delegation.create
delegation.approve
delegation.suspend
delegation.revoke
scope.create
scope.attenuate
scope.revoke
access_right.grant
access_right.revoke
```

## Credentials and attestations

```
credential.issue
credential.verify
credential.present
credential.revoke
attestation.issue
attestation.verify
attestation.revoke
workload.attest
workload.bind
```

## Runtime actions (illustrative)

```
document.read
document.render
document.export
record.read
record.update
tool.invoke
model.invoke
workflow.execute
```

## Audit, proof, and transparency

```
audit.export
proof.generate
transparency.submit
transparency.verify
```

## Signals

```
signal.publish
signal.subscribe
signal.ack
```

## Naming rules

- Action names are lowercase ASCII, dot-separated, in `noun.verb` form.
- Action names are stable identifiers.
- Profile-specific actions (for example, payment actions) are listed in the relevant profile dictionary.
