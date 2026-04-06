# TDD Workflow Skill

## Purpose

Use tests to verify interface behavior early, make assumptions reviewable, and drive changes in small, correct increments.

## When to apply

Apply this workflow by default for:

- behavior changes
- bug fixes
- interface changes

Do not require strict test-first for:

- mechanical refactors
- scaffolding
- non-behavioral structural work

## Workflow

1. Identify the relevant interface or unit contract.
2. State the intended behavior in concrete terms.
3. Add or update the smallest failing test that verifies that behavior.
4. Show the failing test early when collaborating with a human.
5. Confirm that the failure is for the intended reason.
6. Implement the minimum code required to make the test pass.
7. Re-run the narrowest relevant test target.
8. Refactor only if needed and only after behavior is green.
9. Stop at the next sensible commit boundary.

## Test design rules

- Test through the public interface.
- Keep tests narrow in scope.
- Prefer one behavior per test where practical.
- Use mocks only at the unit boundary for dependencies not owned by the unit.
- Do not mock internals.
- Use regression tests for bug fixes.
- Add integration or e2e tests when real collaboration across boundaries matters.

## Collaboration rules

When working with a human:

- present the test early
- make assumptions visible in the test
- use the test to validate expected behavior before implementation expands
- revise the test if the contract or assumptions are wrong

Remember:

- the interface defines the contract
- the test verifies that the implementation satisfies the contract

## Exceptions

If strict test-first is not practical, state why explicitly and use the closest disciplined alternative.
