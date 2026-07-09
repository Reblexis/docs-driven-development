---
name: docs-driven-development
description: >
  Adopt and operate docs-driven development in a repo: docs are the source
  of truth, code is a derived artifact that conforms to them. Use when asked
  to "adopt docs-driven development", "bootstrap docs", "run a conformance
  audit", "reconcile code against docs", or when making ANY behavioral
  change in a repo that declares itself docs-driven (behavior changes start
  as doc changes). Also use when a divergence between what docs say and
  what code does is discovered.
---

# Docs-driven development

The core idea: https://github.com/Reblexis/docs-driven-development
(this skill folder ships inside that repo; `docs/idea.md` there is the
whole idea). This skill is one derived practice of that idea, not part
of it — projects may operate differently, and their own docs win.

The rules, in brief: docs are the source of truth and code exists to
satisfy them; where they disagree, the code is wrong. Behavior changes
start as doc changes. Docs are hierarchical and minimal: vision at the
root, precision concentrated at boundaries between components, internals
left abstract. Ambiguity below the written precision is the implementer's
freedom; ambiguity that makes two conforming implementations collide is a
doc bug, fixed by tightening the one sentence that caused it.

## Operating in a docs-driven repo

Before changing what the software DOES: find the governing doc sentence.
If the change contradicts it, edit the doc first (or propose the edit to
whoever owns that doc layer), then conform the code. If the docs are
silent and the change is internal, that is your freedom: just build it.
If the docs are silent and the change crosses a boundary other components
or agents depend on, write the missing sentence at the right layer before
building.

When you fix a bug and the fix encodes a real behavioral rule, promote
that rule into the docs so it survives any future rewrite.

Report to the human in terms of docs and observable behavior, never code.
Decisions you need from the human are doc questions, framed as proposed
doc edits.

## Adopting: bootstrap a repo

1. **Declare.** Add a short "docs govern" statement to the repo's most
   authoritative doc (create one if none exists): docs are the source of
   truth, code is derived, behavior changes start as doc changes. Link
   the methodology repo. Governing docs live in `./docs`, clearly
   separated; the root README is at most an entry point.
2. **Bootstrap the hierarchy** from existing code plus the owner's
   intent. Usually: a vision doc (why this exists, principles), a
   contracts doc (interfaces, protocols, invariants others depend on),
   and per-component specs only where detail matters. Reuse and promote
   whatever docs already exist; do not duplicate.
3. **Run the first conformance reconciliation** (below). Its findings
   prove the loop works and produce the first doc tightenings.

## The conformance reconciliation loop

Run periodically, after significant code churn, or on demand.

1. Read the governing docs fully. List every checkable claim, starting
   with the pinned (precise) ones.
2. Audit the implementation against each claim. An auditor other than
   the code's author (a separate agent or session) works best.
3. Classify each divergence:
   - **CODE BUG** - the doc is right, the code fails it. Fix the code.
   - **DOC BUG** - the code behavior is sensible, the doc describes
     reality wrongly or stalely. Fix the doc.
   - **AMBIGUITY** - two readings are plausible and the code picked one.
     Tighten the sentence that was underspecified - nothing more.
   - **UNSPECIFIED** - the code does something significant the docs are
     silent on. If it crosses a boundary others depend on, write it into
     the docs (or remove the behavior); if internal, leave it alone.
4. Also report what verified as conforming, so clean areas are known.
5. Apply fixes, commit doc fixes and code fixes with messages that say
   which divergence they resolve, and surface to the doc owner anything
   that changes intent rather than corrects drift.

## Installing this skill for an agent

Copy (or symlink) this `skill/` folder into the agent's skills directory
as `docs-driven-development/`, e.g.:

    git clone https://github.com/Reblexis/docs-driven-development
    ln -s "$PWD/docs-driven-development/skill" ~/.claude/skills/docs-driven-development
