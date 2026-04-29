# KYE™ Vocabulary

Stable names for entities, relationships, actions, lifecycle states, obligations, data classes, and reason codes used by [KYE Protocol™](https://github.com/KYE-Protocol).

This is the **patent-safe public surface**. It defines names so that KYE™ artifacts can be written, exchanged, and discussed across implementations. Mechanism specifications are released on a separate track.

| File | Contents |
|---|---|
| [`entity-types.md`](entity-types.md) | Entity type names |
| [`relationships.md`](relationships.md) | Relationship type names |
| [`actions.md`](actions.md) | Action names |
| [`lifecycle-states.md`](lifecycle-states.md) | Lifecycle state names |
| [`obligations.md`](obligations.md) | Obligation names |
| [`data-classes.md`](data-classes.md) | Data classification names |
| [`reason-codes.md`](reason-codes.md) | Reason code names |

## Stability

Vocabulary names are intended to be stable:

- additions are additive and backwards-compatible
- renames are not permitted; new names supersede old names with explicit aliasing in the normative specification
- removals require a deprecation cycle

## Profile-specific vocabulary

Profile-specific vocabulary (for example, payment actions, healthcare obligations, or treasury approval types) lives in profile documents. Where those profiles are released publicly, they will appear under their own repositories.

## License

Apache License 2.0 — see [`LICENSE`](LICENSE).

KYE™, KYE Protocol™, KYE Passport™, KYE Gateway™, KYE Payments™, and KYE Certified™ are trademarks of the KYE Protocol™ maintainers. The Apache 2.0 license does not grant trademark rights.

## Patent notice

KYE Protocol™ is the subject of pending patent applications. This repository deliberately publishes only **vocabulary and naming**. It does not publish mechanism details. See the [org profile](https://github.com/KYE-Protocol) for the full patent notice.
