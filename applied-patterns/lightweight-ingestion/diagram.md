# Lightweight Ingestion Flow

```mermaid
flowchart LR

    subgraph Source
        A[Source Files or Systems]
    end

    subgraph Ingestion
        B[Collection]
        C[Raw Storage]
        D[Normalization]
        E[Metadata]
    end

    subgraph Access
        F[Simple Data Store]
        G[Access and Retrieval]
    end

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
