---
name: refactor-triage
description: Use when deciding whether refactoring is justified before or during a change, especially when the current design creates friction.
---

# Refactor Triage

## Purpose

Use this skill to decide whether refactoring is justified now, and whether it should happen before a behavior change.

Refactoring is justified when the existing design materially impedes the current change, especially if more near-term work in that area is likely.

## Use this skill when

- the current code makes the change awkward
- the unit is hard to test through its interface
- the boundary is wrong or unclear
- an abstraction is missing or misplaced
- near-term work in the same area is likely
- implementation pressure suggests a preparatory refactor

## Do not use this skill for

- purely aesthetic cleanup
- speculative improvement
- broad redesign without current pressure
- “fixing imperfections” that do not materially hinder the task

## Decision questions

1. Is the current change materially harder because of the current design?
2. Does the current structure obscure the domain concept or contract?
3. Is testability being hindered by the current structure?
4. Is more near-term work in this area likely?
5. Would a small preparatory refactor make the next steps meaningfully simpler?

## Outcomes

### Refactor now

Choose this when the current design materially impedes the change.

### Refactor later

Choose this when the issue is real but not currently blocking, and near-term follow-up is limited.

### Do not refactor

Choose this when the improvement is speculative, mostly aesthetic, or not worth the current cost.

## Rules

- Prefer preparatory refactoring before behavior changes.
- Keep preparatory refactors behavior-preserving.
- Do not smuggle speculative cleanup into a behavior change.
- Keep refactors as small and local as possible.
- Use `commit-policy` to decide whether the refactor should be a separate commit.

## Deliverable

Provide:

- recommendation: refactor now / later / no
- short rationale
- whether it should be a separate commit
- the specific friction being addressed

## Notes

This skill helps decide whether refactoring is justified.  
It does not replace the behavioral implementation workflow.
