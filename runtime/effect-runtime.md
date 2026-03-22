# Effect Runtime

Effect runtime translates effect intents into real actions.

Responsibilities:

- retry logic
- backoff policies
- result recording
- failure classification

Effect execution must not compromise determinism.
