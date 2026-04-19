# Internal Knowledge Assistant Flow

```mermaid
flowchart TD

    A[Internal Sources] --> B[Ingestion]
    B --> C[Canonical Identity]
    C --> D[Chunking + Metadata]

    D --> E[Vector Index]
    D --> F[Metadata Store]
    D --> G[Graph Layer]

    H[User Query] --> I[Query Interpretation]

    I --> J[Keyword Retrieval]
    I --> K[Vector Retrieval]
    I --> L[Structured Filters]

    %% 🔗 CONNECT THE TWO HALVES
    E --> K
    F --> J
    F --> L
    G --> L

    J --> M[Candidate Results]
    K --> M
    L --> M

    M --> N[Ranking and Filtering]
    N --> O[Context Assembly]

    O --> P[LLM]
    P --> Q[Answer + Citations]
