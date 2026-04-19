# Examples

## Document Ingestion

A PDF enters the system.

- canonical_id is assigned at ingestion
- chunks reference canonical_id
- embeddings reference canonical_id
- graph entities reference canonical_id

All downstream representations map to the same source identity.
