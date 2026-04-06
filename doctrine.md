# Development Doctrine

## Core idea

Build software through small, test-informed steps, centered on a clear domain model and simple, explicit data structures.

Interfaces define contracts. Tests verify that implementations satisfy those contracts.

Architecture should evolve with the system, but boundaries and abstractions should be introduced deliberately when they improve clarity, isolate effects, protect the model, and preserve the ability to work in vertical slices.

## Priorities

1. Correctness
2. Clarity of the domain model
3. Simplicity
4. Maintainability
5. Performance when required

## Modeling

- Model important domain concepts explicitly.
- Prefer the simplest model that captures the real invariants of the domain.
- Make invalid states hard or impossible to represent where practical.
- Prefer strong typing and ADT-style modeling when they improve clarity and safety.
- Treat data structures, interfaces, and invariants as central architectural decisions.
- Hide messy interfaces, side effects, and low-level details behind cleaner abstractions.
- Prefer immutable data structures by default, unless the runtime or framework cost is too high.

## Interfaces and contracts

- Treat interfaces as contracts.
- Unit interfaces are internal contracts within the system.
- System interfaces are contracts with external users or external systems.
- Design interfaces deliberately so assumptions, invariants, and valid interactions are clear.
- Tests verify that an implementation satisfies the contract exposed by the interface.
- Tests serve as executable evidence to consumers that the contract behaves as expected.

## Testing

- Prefer narrow unit tests as the primary specification and verification tool.
- A unit is a cohesive abstraction with a clear interface; its exact shape depends on the language.
- In languages like Python, a class is often a unit.
- Test the unit through its public interface.
- Use mocks at the boundary of the unit when it depends on interfaces or collaborators it does not own.
- Do not mock internals.
- Use integration and end-to-end tests to validate real collaboration across boundaries and critical flows.
- Use acceptance tests when they clarify externally meaningful behavior.
- Add specialized tests such as fuzzing or performance tests when justified by risk or requirements.

## Agent-assisted TDD

- For behavior changes, bug fixes, and interface changes, prefer writing the test first.
- In agent-assisted development, show the proposed failing test early.
- Use the test as the first reviewable verification artifact for the intended interface behavior.
- Review tests early to validate assumptions before implementation proceeds.
- For mechanical refactors, scaffolding, or other non-behavioral work, test-first is not mandatory.

## Architecture

- Use just enough architecture for the current complexity.
- Choose architecture to fit the kind of system instead of applying one template everywhere.
- For many applications, a domain / application / infrastructure split is useful.
- For libraries and lower-level systems, choose a structure that better matches the problem.
- Prefer ports-and-adapters thinking: protect the core, isolate effects, and keep boundaries explicit.
- Avoid ceremonial architecture and speculative layering.
- Preserve the ability to work in vertical slices.

## Abstraction

- Use abstraction to communicate concepts, reduce cognitive load, and hide messy details.
- Introduce abstraction when it names a stable idea, improves readability, or controls complexity.
- Do not abstract only because duplication exists.
- Do not avoid abstraction when a concept is clearly emerging.
- Avoid abstraction that is speculative or ceremonial.

## State and effects

- Prefer immutable data by default.
- Favor APIs that make transformations explicit rather than mutating hidden state.
- Use mutation when language, runtime, framework, or performance constraints justify it.
- Keep mutation localized and hidden behind clear abstractions where possible.

## Duplication

- Treat duplication as a design smell by default.
- Remove duplication when it obscures a shared concept or increases maintenance burden.
- Allow intentional duplication only when it yields substantial benefits, such as stronger decoupling, organizational autonomy, or clearer boundaries.

## Naming and comments

- Treat naming as a core design activity.
- Prefer compact but descriptive names.
- When forced to choose, prefer clarity over brevity.
- Use names that reflect the domain and the role of the abstraction.
- Prefer code that is readable through naming, structure, and decomposition.
- Avoid comments that merely restate the code.
- Use comments sparingly for intent, rationale, constraints, tradeoffs, or non-obvious behavior.

## Refactoring

- Refactor when the existing design materially impedes the current change.
- Raise the priority of refactoring when the affected area is likely to receive more near-term work.
- Prefer preparatory refactoring before behavior changes when it clarifies the model, improves testability, or reduces friction.
- Avoid speculative refactoring that is not justified by current or clearly emerging pressure.

## Change discipline

- Work in small, coherent increments.
- Keep cleanup optional and fold it into prior commits when appropriate via amend or fixup.
- Keep history focused, explainable, and reviewable.
- Avoid mixed, unfocused diffs.

## Commit messages

- Use commit messages to explain why a change exists.
- Do not use commit messages merely to restate what the diff already shows.
- Preserve the motivating problem, constraint, or deficiency in the history.

Preferred structure:

<title>

Prior to this change, <problem or missing behavior>.
This change <how the patch addresses it>.
