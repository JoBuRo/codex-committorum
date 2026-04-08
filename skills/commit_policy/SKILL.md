---
name: commit-policy
description: Use when deciding commit boundaries, splitting mixed diffs, or writing commit messages for a completed increment.
---

# Commit Policy

## Purpose

Use this skill to keep changes atomic, reviewable, and historically useful.

A commit should contain one logical change and explain why that change was necessary.

## Use this skill when

- preparing a commit
- deciding whether a patch is too broad
- splitting a mixed diff
- writing a commit message
- deciding whether a preparatory refactor belongs in a separate commit

## Rules

- One logical concern per commit.
- Keep tests with the code they justify.
- Avoid mixing behavior changes, refactors, and incidental cleanup.
- Avoid rename-plus-logic-plus-formatting commits unless strongly justified.
- Prefer multiple small commits over one mixed commit.
- Keep history focused, explainable, and easy to review.

## Commit message rule

The code shows what changed.  
The commit message should explain why the change exists.

Use this structure:

<title>

Prior to this change, <problem or missing behavior>.

This change <how the patch addresses it>.

## Review questions

Before finalizing a commit, check:

1. Is this one logical concern?
2. Would a reviewer understand why every changed file belongs?
3. Does the message explain why the change exists?
4. Should preparatory refactoring be split from behavior change?
5. Is any cleanup better folded into a previous commit via fixup or amend?

## Deliverable

Provide:

- proposed commit boundary
- rationale for the boundary
- commit message
- suggested split if the diff is mixed

## Notes

This skill governs commit slicing and rationale preservation.  
It does not define implementation workflow or contract design.
