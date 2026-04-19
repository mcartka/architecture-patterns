# Examples

## Document Processing

A document enters the system and produces multiple outputs:

- raw file
- parsed text
- retrieval chunks
- graph entities
- embeddings

Lineage tracks:

- which outputs derive from the document
- which transformations produced each output
- which version of the document generated each artifact

Governance ensures:

- only authorized users access the document
- updates propagate to downstream artifacts
- deletions remove all derived representations

---

## Internal Knowledge Assistant

A user asks a question and the system retrieves supporting documents.

A strong system:

- tracks which documents were retrieved
- records which chunks contributed to the answer
- captures which model generated the response
- logs timestamps and execution context

This allows the system to:

- explain how the answer was constructed
- audit system behavior
- improve retrieval and ranking over time

---

## Data Correction

A source record changes.

A strong lineage system identifies:

- which downstream artifacts depend on that record
- which systems require updates
- which outputs may now be invalid

Governance ensures:

- updates follow defined rules
- affected artifacts are reprocessed or invalidated
- the system remains consistent after the change
