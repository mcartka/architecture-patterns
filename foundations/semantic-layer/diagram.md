# Semantic Layer Flow

```mermaid
flowchart TD

    A[Source System A: client] --> D[Source Mapping Layer]
    B[Source System B: account_holder] --> D
    C[Source System C: customer_name] --> D

    D --> E[Semantic Concept: Customer]

    E --> F[Relationships]
    E --> G[Business Definitions]
    E --> H[Source Mappings]

    F --> I[Applications and APIs]
    G --> I
    H --> I

    I --> J[Analytics, Search, and AI Systems]
