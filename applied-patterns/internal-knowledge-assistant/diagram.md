# Internal Knowledge Assistant Flow

```mermaid
flowchart LR

    subgraph S1[Ingestion]
        A[Internal Sources] --> B[Ingestion]
        B --> C[Canonical Identity]
        C --> D[Chunking + Metadata]
    end

    subgraph S2[Representations]
        E[Vector Index]
        F[Metadata Store]
        G[Graph Layer]
    end

    subgraph S3[Query]
        H[User Query] --> I[Query Interpretation]
    end

    subgraph S4[Retrieval]
        J[Keyword Retrieval]
        K[Vector Retrieval]
        L[Structured Filters]
        M[Candidate Results]
        N[Ranking]
    end

    subgraph S5[Generation]
        O[Context Assembly]
        P[LLM]
        Q[Answer + Citations]
    end

    D --> E
    D --> F
    D --> G

    I --> J
    I --> K
    I --> L

    F --> J
    E --> K
    F --> L
    G --> L

    J --> M
    K --> M
    L --> M

    M --> N
    N --> O
    O --> P
    P --> Q
