# Retrieval Basics Flow

```mermaid
flowchart TD

    A[User Query] --> B[Query Interpretation]

    B --> C[Keyword Retrieval]
    B --> D[Vector Retrieval]
    B --> E[Structured Filters]
    B --> F[Graph Retrieval]

    C --> G[Candidate Results]
    D --> G
    E --> G
    F --> G

    G --> H[Ranking and Re-ranking]
    H --> I[Filtered Context]

    I --> J[Application, Search, or LLM]
