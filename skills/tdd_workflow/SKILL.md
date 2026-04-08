---
name: tdd-workflow
description: Use to implement a behavior change through the repo's preferred red-green-refactor workflow after the contract and first verifying test are already clear.
---

# TDD Workflow

## Purpose

Use this skill to execute a behavior change in small, verified increments.

This skill assumes that the relevant interface behavior is already understood and that the first meaningful verifying test has already been identified, usually via `contract-first-change`.

## Use this skill when

- implementing a bug fix after the contract is clear
- implementing a behavior change after the contract is clear
- implementing an interface change after the contract is clear
- continuing work from an already reviewed failing test

## Do not use this skill for

- deciding what the contract should be
- purely mechanical refactors
- scaffolding with no stable behavior yet
- structural cleanup with no intended behavior change

## Workflow

1. Start from the already identified failing test.
2. Run the smallest relevant test target and confirm the failure is for the intended reason.
3. Implement the minimum code required to make the test pass.
4. Re-run the narrowest relevant tests first.
5. Add the next narrowest meaningful test if more behavior remains.
6. Refactor only after behavior is green.
7. Stop at the next sensible commit boundary.

## Rules

- Prefer one behavior increment at a time.
- Keep implementation minimal during green.
- Do not mix unrelated refactors into the same increment.
- Preserve focus on public interface behavior.
- If the design materially impedes the change, pause and use `refactor-triage`.
- If the contract is still unclear, return to `contract-first-change`.

## Deliverable

For each increment, provide:

- behavior under verification
- failing or newly added test
- minimal implementation change
- tests run
- proposed next step or boundary

## Notes

This skill does not define the contract.  
The interface defines the contract.  
The test verifies that the implementation satisfies it.
