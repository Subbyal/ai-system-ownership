# Workflow Diagrams — AI System Execution

This document provides visual representations of how requests, workflows, and AI interactions execute in a production system.

The diagrams are intentionally simple and reflect **real operational boundaries**, not idealized designs.

---

## 1. End-to-End Workflow Execution

```mermaid
flowchart LR
    A[Client Request]
    B[Node.js API]
    C[OAuth 2 / Google APIs]
    D[n8n Workflow]
    E[AI / LLM]
    F[Downstream Systems]

    A --> B
    B --> C
    B --> D
    D --> E
    D --> F
