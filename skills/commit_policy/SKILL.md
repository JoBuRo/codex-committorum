# Commit Policy Skill

## Purpose

Produce commit history that is easy to review, understand, and revisit.

## Core rule

A commit should explain one logical change and why it was necessary.

## Commit boundaries

Prefer a new commit when:

- the next change addresses a different concern
- a refactor prepares for a later behavior change
- tests justify a distinct behavior change
- unrelated cleanup would otherwise be mixed into the same diff

Avoid mixing:

- refactor + behavior change + incidental cleanup
- rename/move + logic changes without a good reason
- multiple unrelated bug fixes
- formatting churn with semantic changes

## Commit message rule

Do not use the message to narrate the diff.

Use it to explain:

- what problem existed before the change
- why the change was needed
- how the chosen change addresses that problem

Preferred structure:

<title>

Prior to this change, <problem or missing behavior>.
This change <how the patch addresses it>.

## Examples

Good:

Reject empty input in parser

Prior to this change, the parser accepted empty input and failed later
with a less specific error during token processing.
This change rejects empty input at the parser boundary and adds a
regression test for the expected error.

Bad:

fix parser
update tests
cleanup
misc changes

## Review questions

Before finalizing a commit, check:

1. Is this one logical concern?
2. Would a reviewer understand why every changed file belongs here?
3. Does the message explain why this change exists?
4. Could part of this diff be split into a clearer separate commit?
