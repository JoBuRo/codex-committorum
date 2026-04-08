---
name: contract-first-change
description: Use for behavior changes, bug fixes, and interface changes to identify the relevant contract first and prepare the first verifying test before implementation.
---

# Contract-First Change

## Purpose

Use this skill when a task changes observable behavior at a unit or system boundary.

The interface defines the contract.  
Tests verify that the implementation satisfies that contract.

This skill is about clarifying the contract and preparing the first reviewable verification artifact before implementation begins.

## Use this skill when

- changing observable behavior
- fixing a bug
- changing a public or internal interface
- clarifying behavior at a boundary
- making assumptions explicit before implementation

## Do not use this skill for

- purely mechanical refactors
- scaffolding with no stable behavior yet
- formatting-only changes
- rename-only changes with no behavioral impact

## Workflow

1. Identify the relevant interface or boundary.
2. State the intended contract or behavior in concrete terms.
3. Identify important assumptions, invariants, edge cases, and failure modes.
4. Write or update the narrowest meaningful failing test that verifies that intended behavior.
5. Show the failing test early for review when practical.
6. Confirm that the test reflects the intended contract before implementation proceeds.
7. Hand off execution to the `tdd-workflow` skill.

## Rules

- The interface defines the contract.
- The test verifies the implementation of that contract.
- Prefer verifying behavior through the public interface.
- Make assumptions visible in the test.
- Use mocks only at true unit boundaries for dependencies not owned by the unit.
- Do not mock internals.
- Do not proceed into broader implementation before the contract and first test are clear.

## Deliverable

Before implementation, provide:

- the relevant interface or boundary
- the intended contract or behavior
- the first failing test
- notable assumptions, invariants, or edge cases

## Notes

This skill is not the full red/green/refactor loop.  
Once the contract and first verifying test are clear, use `tdd-workflow` to implement the change in small validated steps.
