# Persistence Model

Runtime maintains:

- append-only event journal
- periodic state snapshots

Goals:

- crash recovery
- replay debugging
- historical inspection

Persistence overhead must be bounded.
