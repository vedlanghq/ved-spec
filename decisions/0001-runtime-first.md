# Decision 0001: Runtime-First Development

## Context

Lexum requires a deterministic execution model.

## Decision

The runtime will be implemented before the compiler.

## Rationale

- validates core semantics early
- avoids premature syntax design
- ensures execution model correctness

## Consequences

- compiler design depends on runtime capabilities
- early focus on scheduler and persistence
