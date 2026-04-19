# Canonical Identity Flow

```mermaid
flowchart TD

    A[Source System A] --> D[Ingestion / Mapping Layer]
    B[Source System B] --> D
    C[Source System C] --> D

    D --> E[Canonical Identity Assigned]

    E --> F[Metadata Store]
    E --> G[Graph Representation]
    E --> H[Vector Index]

    F --> I[Retrieval Layer]
    G --> I
    H --> I

    I --> J[Applications / APIs]
