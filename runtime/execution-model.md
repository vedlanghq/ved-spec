# Execution Model

Ved runtime operates as a deterministic control loop.

## Core Cycle

1. Observe current state
2. Evaluate goals
3. Select transition
4. Execute bounded slice
5. Persist state mutation
6. Emit effects
7. Repeat

## Properties

- deterministic execution
- replayable behaviour
- bounded computation
- persistent state evolution

External interactions are isolated and recorded.
