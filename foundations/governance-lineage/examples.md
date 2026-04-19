
---

# ✅ `examples.md`

```markdown
# Examples

## Document Processing

A document enters a system and produces multiple outputs:

- raw file
- parsed text
- retrieval chunks
- graph entities
- embeddings

Lineage tracks:

- which outputs derive from the document
- how each transformation occurred
- which version produced each artifact

Governance ensures:

- only authorized users access the document
- updates propagate correctly
- deletions remove downstream artifacts

---

## Internal Knowledge Assistant

A user asks a question and receives an answer based on retrieved documents.

A strong system:

- tracks which documents were retrieved
- records which chunks were used
- stores which model generated the response
- captures timestamps and context

This allows the system to:

- explain the answer
- audit the interaction
- improve retrieval quality over time

---

## Data Correction

A source record is corrected.

A strong lineage system identifies:

- which downstream artifacts depend on that record
- which systems must be updated
- which outputs may now be invalid

Governance ensures:

- updates follow defined rules
- affected systems remain consistent
