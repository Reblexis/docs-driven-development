# Method

This document describes the model behind docs-driven development in more depth. The [README](../README.md) is the whole methodology; this is commentary and mechanics.

## Docs as a programming language

In conventional development, code is the source of truth and docs describe it — which is why docs rot: they can drift from reality and nothing breaks. Docs-driven development inverts the dependency. The docs are the program; the code is a build artifact. Drift between them is a bug in the code, detectable and fixable by agents, not silent entropy.

The human's job is to hold opinions and express them at the abstraction level where they actually exist. The agents' job is everything below that level.

## The determinism dial

Every sentence in the docs sits somewhere on a spectrum:

- **Pinned.** "An agent at zero or negative balance never runs; it replies with a deterministic auto-response." One reasonable reading. Behavior is fixed.
- **Constrained.** "Agents respond to messages within a minute under normal load." A family of implementations qualifies; all are correct.
- **Open.** "The fleet should feel alive." Direction, not specification. Implementers have wide freedom and cannot be wrong on details, only on spirit.

All three are legitimate. The skill of writing docs-driven docs is choosing the right level per topic — not maximizing precision. Precision is a cost: it consumes your attention and forecloses agent judgment. Spend it only where divergence is expensive.

## Layers

Docs form a hierarchy, top to bottom:

1. **Vision** — what this thing is and why it exists. Short, stable, mostly open-level language.
2. **Contracts** — how components, agents, or services interact: interfaces, protocols, invariants, guarantees. This is where precision concentrates, because ambiguity here is where two correct implementations collide.
3. **Specifications** — detailed behavior of individual components, written only where the detail matters. Many components need no spec at all beyond the contracts they participate in.

Lower layers must be consistent with higher ones. A conflict between layers is resolved upward: the higher layer wins, and the lower doc gets fixed.

## Boundaries are where precision lives

Ambiguity inside one component is free — nobody else depends on those choices. Ambiguity at a boundary between components is where reasonable readings diverge and integration breaks. The practical discipline: when confusion or divergence appears, locate which boundary sentence was underspecified and tighten that sentence. Do not respond to one divergence event by making the whole document more rigid.

## How code stays aligned

Agents derive whatever verification they need — tests, checks, review passes — from the docs. These are implementation details below the human's abstraction floor; the human never reads or writes them. Whether changed docs are met by evolving the existing code or rewriting it is purely a question of cost: if the code is fully aligned with the docs at the end, either path was correct. When a fix in the code turns out to encode a real behavioral rule, that rule belongs in the docs, so it survives any future rewrite.

## What the human actually does

Programming does not disappear — it moves. The human edits living documents: adding intent, resolving reported ambiguities, promoting learned rules. Early in a project this editing is frequent, because underspecification is discovered by watching implementations diverge. That editing is the programming. The difference is that every keystroke happens at an abstraction level where the human has a genuine opinion.
