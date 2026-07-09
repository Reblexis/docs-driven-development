# Docs-Driven Development

Software whose source is documentation.

Code still exists — but as a derived artifact, produced and maintained by AI agents. Humans write documentation at whatever level of abstraction they choose; agents make reality match it.

## The idea

A programming language forces you to decide everything: every name, every structure, every edge case — including the thousands of things you have no opinion about. Documentation as source inverts this. You write precisely where behavior matters to you, and stay abstract where it doesn't. Where you are precise, behavior is pinned. Where you are abstract, you have deliberately delegated the decision.

This makes natural language a programming language with an adjustable determinism dial: deterministic exactly up to the level you choose, and free below it.

From that, everything else follows:

- The docs are the source of truth. Code exists to satisfy them; where they disagree, the code is wrong.
- To change what the software does, change the docs. The code is then made to conform.
- Ambiguity below the precision of the docs is not error but deliberate freedom — the implementer decides.
- When ambiguity produces divergence that matters, the docs were too loose exactly there, and the fix is precision exactly there.

## What this deliberately does not say

How documentation should be structured, how conformance is checked, who may write which docs, how existing projects convert — all left open. Those answers are more specific designs derived from this idea: written down, owned by each project, and free to differ between projects. Adopting docs-driven development is itself the same move as using it — write down what your thing should be, and let agents make reality match.

One example of such a derived design: [ddd-practice](https://github.com/Reblexis/ddd-practice) — adopting DDD in existing projects and developing with AI agents.

## This repo follows its own standard

This README is the source of truth for this repository. Everything else in it is a derived artifact that exists to satisfy this document, and is wrong wherever it disagrees with it. Changes to what this repo does happen here first.

The repo ships an installable skill for AI agents, at [`skill/`](skill/SKILL.md): it describes how to adopt and operate docs-driven development, consistently with this document, and installs by copying the folder into an agent's skills directory. Everything else about the skill is its implementation.

## License

[MIT](LICENSE)
