# Simple Metadata Catalog Flow

```mermaid
flowchart LR

    subgraph Sources
        A[Datasets and Documents]
    end

    subgraph Catalog
        B[Identification]
        C[Metadata Capture]
        D[Metadata Registry]
    end

    subgraph Access
        E[Search and Filter]
        F[Discovery]
    end

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
