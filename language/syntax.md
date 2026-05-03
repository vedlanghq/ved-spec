# Syntax Overview

Lexum syntax is designed to be:

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

```Lexum
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
