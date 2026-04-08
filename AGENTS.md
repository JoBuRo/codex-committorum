# AGENTS.md

This file defines workflow; `doctrine.md` defines governing engineering principles.

## Instruction priority

When guidance conflicts, apply this order:

1. Runtime/system constraints (platform safety rules)
2. Task-specific user request
3. `doctrine.md`
4. `AGENTS.md`
5. Local file/project conventions in touched code

If still ambiguous, choose the safest non-destructive option that preserves correctness and contract clarity.

## Doctrine alignment

- Interfaces define contracts.
- Tests verify that implementations satisfy those contracts.
- Treat `doctrine.md` as the canonical engineering doctrine.
- Use `AGENTS.md` as the execution workflow and delivery checklist.
- When adding architecture, testing, abstraction, naming, or refactoring decisions, align with `doctrine.md` defaults unless task constraints require a justified exception.
- If deviating from doctrine, state the rationale briefly in the change explanation.

## Avoid (Anti-patterns)

- Contract-blind changes: modifying behavior without first identifying the interface contract.
- Implementation-before-spec: shipping behavior changes before adding/updating the smallest relevant test (except mechanical refactors/scaffolding).
- Mixed-concern diffs: combining unrelated behavior changes, refactors, and cleanup in one patch.
- Speculative architecture: introducing layers/abstractions without current, concrete pressure.
- Boundary leakage: allowing infrastructure details to bleed into core domain logic.
- Hidden mutability: mutating shared state across boundaries instead of explicit, localized transformations.
- Internal mocking: mocking internals instead of only mocking dependencies at true unit boundaries.
- Comment-as-crutch: adding comments that restate code instead of improving names/structure.
- Generic naming: using vague names that do not reflect domain concepts or invariants.
- Why-free commits: commit messages that describe only what changed, not why it was necessary.
- Doctrine drift: deviating from `doctrine.md` defaults without brief rationale.

## Working norms

- Start from the domain model.
- Prefer the simplest design that preserves correctness and clarity.
- Treat interfaces as contracts.
- Use tests to verify that implementations satisfy those contracts.
- Prefer small, coherent, reviewable changes.
- Keep diffs focused and commit history explanatory.

## Required workflow

For behavior changes, bug fixes, and interface changes:

1. Identify the relevant interface behavior or contract.
2. Write or update the narrowest meaningful failing test that verifies that behavior.
3. Show the failing test before implementation when practical, especially for behavior changes, bug fixes, and interface changes.
4. Confirm that the test reflects the intended contract.
5. Implement the minimum change required to make the test pass.
6. Run the narrowest relevant test set first.
7. Refactor only if the current design materially impedes the change.
8. Keep the change at a sensible commit boundary.

For mechanical refactors or scaffolding:

- test-first is not mandatory
- preserve existing behavior
- add or update tests when needed to protect behavior or verify the interface
- when deviating from the default workflow, state the reason briefly and use the closest disciplined alternative

## Testing rules

- Prefer narrow unit tests.
- Test units through their public interface.
- A unit is a cohesive abstraction with a clear interface.
- In Python, a class is often a unit.
- Use mocks only at the unit boundary for dependencies not owned by the unit.
- Do not mock internals.
- Use integration/e2e tests for real boundary collaboration and critical flows.

## Architecture rules

- Use just enough architecture for the current level of complexity.
- Prefer ports-and-adapters thinking where applicable.
- Protect the core model and isolate effects.
- Preserve the ability to work in vertical slices.
- Prefer changes that can be implemented, tested, and reviewed as a vertical slice when the task permits.
- Do not introduce speculative layers or ceremonial abstractions.

## Refactoring rules

- Refactor when the current change is materially harder because of the existing design.
- Raise refactoring priority when the affected area is likely to see more near-term work.
- Prefer preparatory refactoring before behavior changes.
- Avoid speculative cleanup.

## Naming and comments

- Use domain-driven names.
- Prefer compact but descriptive names.
- Prefer longer names when they materially improve clarity.
- Avoid comments that restate the code.
- Use comments only for rationale, constraints, or non-obvious behavior.

## Commit rules

- Keep commits atomic and reviewable.
- One logical concern per commit.
- Avoid mixing refactors, behavior changes, and unrelated cleanup.
- Use commit messages to explain why the change exists.

Commit message template:

```
<title>

Prior to this change, <problem or missing behavior>.

This change <how the patch addresses it>.

```

## Skill usage

Use the skills under `.agents/skills/` as follows:

- `contract-first-change`: use first for behavior changes, bug fixes, and interface changes to identify the contract and prepare the first verifying test.
- `tdd-workflow`: use after the contract and first verifying test are clear, to implement the change in small red/green/refactor steps.
- `refactor-triage`: use when the current design makes the change materially harder and it is unclear whether a preparatory refactor is justified.
- `commit-policy`: use when deciding commit boundaries, splitting mixed diffs, or writing commit messages.

Do not use `tdd-workflow` to decide what the contract should be.  
Do not use `contract-first-change` as the full implementation workflow.
