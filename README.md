# Docs-Driven Development

Software whose source is documentation.

Code still exists — but as a derived artifact, written and maintained by AI agents, never by humans. Humans write docs at whatever level of abstraction they choose; agents make reality match them.

## The idea

A programming language forces you to decide everything: every name, every data structure, every edge case — including the thousands of decisions you have no opinion about. Documentation as source inverts this. You write precisely where behavior matters, and stay abstract where it doesn't. Where you are precise, behavior is pinned. Where you are abstract, you have deliberately delegated the decision.

This makes natural language a programming language with an adjustable determinism dial — deterministic exactly up to the level you choose, and free below it.

## The rules

1. **Docs are the source of truth.** Code exists only to satisfy them. Where code and docs disagree, the code is wrong.
2. **Behavior changes start as doc changes.** To change what the software does, change the doc first, then conform the code.
3. **Docs are hierarchical and minimal.** Vision at the root; precision added only where divergence is costly. Interfaces and contracts between components deserve the most precision; internals stay abstract.
4. **Ambiguity below the specified precision is freedom, not error.** Implementers decide and move on.
5. **Ambiguity that causes divergence is a doc bug.** Fix it by tightening the specific sentence that was underspecified — nothing more.

That's the whole methodology. Everything else is practice.

## Going deeper

- [Method](docs/method.md) — the model in depth: layers, the determinism dial, boundaries, drift, and how code stays aligned.
- [Adoption](docs/adoption.md) — how to adopt this in a new or existing project.

## License

[MIT](LICENSE)
