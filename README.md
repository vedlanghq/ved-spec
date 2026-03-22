# Ved Specification

This repository contains the formal design and architectural specifications
for the Ved programming language.

Ved is a deterministic control-plane programming language for building
reliable long-running distributed systems.

## Purpose

This repository defines:

- language semantics
- runtime execution model
- compiler architecture
- system guarantees
- design principles and constraints

It is the source of truth for all Ved design decisions.

## Structure

- `language/` — syntax and semantics
- `runtime/` — execution and persistence model
- `compiler/` — compilation pipeline
- `principles.md` — core architectural rules
- `anti-patterns.md` — prohibited patterns
- `guarantees/` — system-level guarantees

## Status

Ved is in early design and prototyping stage.
Specifications will evolve as implementation progresses.

## Contribution

Design changes should be discussed before implementation.
