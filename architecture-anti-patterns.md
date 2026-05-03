# Lexum Architectural Anti-Patterns

This document defines patterns and practices that are explicitly discouraged
or disallowed in the design and implementation of Lexum.

These anti-patterns exist to protect determinism, clarity, and long-term
system reliability.

---

## 1. Hidden State Mutation

### Description

State changes occurring outside explicit transition logic.

### Why This Is a Problem

- Breaks determinism
- Makes behaviour unpredictable
- Prevents accurate replay

### Examples

- modifying state during effect execution
- implicit mutations inside helper functions

### Guideline

All state changes must occur through explicit, tracked transitions.

---

## 2. Implicit Side Effects

### Description

External interactions that are not declared or recorded.

### Why This Is a Problem

- Breaks replayability
- Introduces nondeterminism
- Makes debugging unreliable

### Examples

- direct API calls inside execution logic
- accessing system time without abstraction

### Guideline

All external interactions must be modeled as explicit effects.

---

## 3. Unbounded Execution

### Description

Execution paths that can run indefinitely without yielding.

### Why This Is a Problem

- Starves scheduler
- Reduces system responsiveness
- Breaks fairness guarantees

### Examples

- infinite loops inside transitions
- heavy computation without slicing

### Guideline

Execution must be structured into bounded slices.

---

## 4. Cross-Domain State Leakage

### Description

One domain directly mutating or accessing another domain’s state.

### Why This Is a Problem

- Violates isolation
- Breaks authority model
- Creates tight coupling

### Examples

- direct shared memory across domains
- bypassing message or effect boundaries

### Guideline

All cross-domain interaction must be explicit and controlled.

---

## 5. Goal-Free Execution Logic

### Description

Transitions that do not contribute to any defined goal.

### Why This Is a Problem

- Creates arbitrary behaviour
- Reduces system analyzability
- Encourages imperative scripting

### Examples

- periodic actions without convergence target
- transitions triggered without purpose

### Guideline

All execution should contribute to achieving or maintaining goals.

---

## 6. Conflicting or Unresolved Goals

### Description

Multiple goals that cannot be satisfied simultaneously.

### Why This Is a Problem

- Causes oscillation
- Prevents convergence
- Makes behaviour unstable

### Examples

- one goal increases resources while another decreases them
- goals with incompatible constraints

### Guideline

Goal interactions must be explicit and conflict-resolved.

---

## 7. Overloaded Transitions

### Description

Single transitions performing too many responsibilities.

### Why This Is a Problem

- Reduces clarity
- Makes reasoning difficult
- Increases error surface

### Examples

- transitions that handle multiple unrelated states
- mixing recovery logic with scaling logic

### Guideline

Transitions should be small, focused, and composable.

---

## 8. Runtime-Dependent Behaviour

### Description

Logic that depends on uncontrolled runtime conditions.

### Why This Is a Problem

- Breaks determinism
- Produces inconsistent behaviour across runs

### Examples

- relying on system time directly
- depending on thread scheduling order

### Guideline

All nondeterministic inputs must be explicitly modeled.

---

## 9. Silent Failure Handling

### Description

Failures that are ignored or handled without visibility.

### Why This Is a Problem

- Masks system issues
- Prevents proper recovery
- Reduces observability

### Examples

- swallowing errors
- retry loops without logging

### Guideline

Failures must be explicit, observable, and recoverable.

---

## 10. State Explosion Without Control

### Description

Unbounded growth of state over time.

### Why This Is a Problem

- Degrades performance
- Increases memory usage
- Makes recovery slower

### Examples

- never pruning historical data
- accumulating unused state fields

### Guideline

State lifecycle and compaction must be considered.

---

## 11. Implicit Authority Escalation

### Description

Accessing higher-level scopes without explicit permission.

### Why This Is a Problem

- Breaks security model
- Violates isolation guarantees

### Examples

- bypassing scope hierarchy checks
- hidden privilege escalation

### Guideline

All authority changes must be explicit and validated.

---

## 12. Over-Abstracted Language Constructs

### Description

Adding features that obscure behaviour instead of clarifying it.

### Why This Is a Problem

- Reduces readability
- Increases learning curve
- Hides system logic

### Examples

- excessive syntactic sugar
- implicit control-flow transformations

### Guideline

Prefer explicit constructs over clever abstractions.

---

## 13. Premature Distributed Complexity

### Description

Introducing distributed runtime features before core semantics are stable.

### Why This Is a Problem

- Increases system complexity drastically
- Obscures core design validation
- Slows development

### Examples

- multi-node scheduling before single-node correctness
- distributed persistence before local replay works

### Guideline

Prove correctness locally before scaling out.

---

## 14. Divergence Without Detection

### Description

System behaviour drifting away from goals without awareness.

### Why This Is a Problem

- Prevents convergence
- Leads to unstable systems

### Examples

- infinite retry loops
- oscillating state changes

### Guideline

The system should detect and surface divergence patterns.

---

## 15. Mixing Control Plane and Business Logic

### Description

Using Lexum to implement application-level functionality.

### Why This Is a Problem

- Blurs responsibilities
- Reduces clarity of purpose
- Complicates runtime

### Examples

- embedding business workflows in Lexum domains
- using Lexum for request-response logic

### Guideline

Lexum is for control-plane orchestration, not application logic.

---

## Closing Note

These anti-patterns define boundaries that protect Ved's design.

Violations may not always be immediately harmful, but they introduce long-term
instability and complexity.

When in doubt:

- prefer explicitness
- preserve determinism
- maintain clarity
