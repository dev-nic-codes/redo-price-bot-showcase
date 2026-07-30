# Architecture

```mermaid
flowchart LR
    M["Validated REDO market snapshot"] --> P["Scheduled price post"]
    E["Normalized trade event"] --> Q["Durable alert outbox"]
    Q --> D1["Alert destination A"]
    Q --> D2["Alert destination B"]
    Q --> DN["Additional destinations"]
    O["Private controls"] --> P
    O --> Q
```

The outbox records delivery progress separately for each configured destination. A retry continues from incomplete work. The queue format, identifiers, provider routes, and Telegram calls are proprietary.
