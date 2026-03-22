# Syntax Overview

Ved syntax is designed to be:

- explicit
- minimal
- structurally clear

## Core Constructs

- domain
- state
- goal
- transition
- effect

## Example

```ved
domain WorkerPool {
  state {
    desired: int
    actual: int
  }

  goal Stable {
    predicate actual == desired
  }

  transition ScaleUp {
    step {
      emit ProvisionWorker()
    }
  }
}
```

Syntax prioritizes readability over expressiveness.
