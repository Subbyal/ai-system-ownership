
flowchart TD
    A[Validated Input]
    B[AI Invocation]
    C{Output Valid?}
    D[Continue Workflow]
    E[Fallback Logic]

    A --> B
    B --> C
    C -->|Yes| D
    C -->|No| E
