# Document Ingestion and Search Flow

```mermaid
flowchart LR

    subgraph Ingestion
        A[Source Systems] --> B[Document Collection]
        B --> C[Raw Storage]
        C --> D[Canonical Identity]
        D --> E[Normalization + Metadata]
        E --> F[Chunking]
    end

    subgraph Indexing
        F --> G[Search Index]
        E --> H[Metadata Store]
        F --> I[Vector Index]
    end

    subgraph Query
        J[User Query] --> K[Query Processing]
    end

    subgraph Retrieval
        K --> L[Keyword Search]
        K --> M[Metadata Filters]
        K --> N[Vector Search]

        G --> L
        H --> M
        I --> N

        L --> O[Candidate Results]
        M --> O
        N --> O

        O --> P[Ranking]
    end

    P --> Q[Results]
