# Governance and Lineage Flow

```mermaid
flowchart TD

    A[Source Data] --> B[Ingestion]

    B --> C[Canonical Identity Assigned]

    C --> D[Transformation Layer]
    D --> E[Derived Artifacts]

    E --> F[Metadata Store]
    E --> G[Graph]
    E --> H[Vector Index]

    F --> I[Retrieval Layer]
    G --> I
    H --> I

    I --> J[Applications / AI Systems]

    subgraph Governance
        K[Ownership]
        L[Policies]
        M[Access Control]
        N[Versioning]
    end

    subgraph Lineage
        O[Source Tracking]
        P[Transformation History]
        Q[Dependency Mapping]
    end

    C --> O
    D --> P
    E --> Q

    F --> K
    F --> L
    F --> M
    F --> N
