# Canonical Identity

## Overview

Canonical identity assigns a stable, deterministic identifier to a resource at the moment it enters a system.

The goal is simple: the same thing should carry the same identity everywhere it appears, even when different systems represent it in different ways such as metadata records, graph nodes, search documents, embeddings, or derived artifacts.

Canonical identity creates the anchor that keeps multiple representations aligned over time.

---

## Core Idea

Define identity once, as early as possible, and propagate it through every downstream layer.

Do not tie the canonical identifier to storage location, processing pipeline, or application context. Instead, tie it directly to the resource itself.

This becomes critical when the same source material appears in multiple forms, such as:

- a raw file in object storage
- a parsed document in a processing layer
- chunks in a retrieval pipeline
- nodes and edges in a graph
- embeddings in a vector index
- metadata records in a catalog

Without canonical identity, these layers drift apart and lose alignment.

---

## What Problem This Solves

Many systems assign identity independently in each layer.

For example:

- storage assigns one ID
- a database generates another
- a vector store creates another
- an application introduces its own reference key

This fragmentation makes it difficult to answer basic questions such as:

- Are these two records the same thing?
- Which graph node came from this document?
- Which embedding belongs to this version?
- If a source changes, what must be updated downstream?
- If something is deleted, where else does it exist?

Canonical identity solves this by giving the system one stable reference point.

---

## Design Principle

Assign a canonical identifier at ingestion, before any transformation or projection.

Carry that identifier through:

- metadata registration
- parsing and normalization
- chunking
- indexing
- graph projection
- vectorization
- retrieval
- audit and lineage tracking

Systems may use internal identifiers, but every layer must map back to the same canonical identity.

---

## Characteristics of a Good Canonical Identifier

A strong canonical identifier is:

- **deterministic**  
  The same input produces the same identifier every time.

- **stable**  
  The identifier does not change when storage, systems, or applications change.

- **portable**  
  Systems can propagate the identifier across representations.

- **system-independent**  
  The identifier does not depend on a specific vendor or datastore.

- **traceable**  
  The identifier allows every derived artifact to link back to the source.

---

## Common Approaches

Different systems implement canonical identity in different ways.

### Content-based identity

Generate a deterministic hash from the resource or a canonical representation of it.

Use this when you need idempotency and duplicate detection.

Examples:
- file content hash
- normalized document hash
- structured canonical serialization hash

### Source-based identity

Derive a stable identifier from a trusted upstream system.

Use this when the source system already defines authoritative identity.

Examples:
- source system name plus source record ID
- domain key plus entity ID

### Composite identity

Combine multiple stable fields into a deterministic identifier.

Use this when neither content nor a single external key provides sufficient identity.

Examples:
- source system plus object type plus external ID
- dataset plus entity type plus normalized business key

---

## Tradeoffs

Canonical identity introduces tradeoffs that require careful design.

### Content-based identity

Advantages:
- supports deduplication
- enables idempotent ingestion
- remains independent of vendor systems

Challenges:
- small content changes can create new identifiers
- requires a normalization strategy
- may not align with business identity

### Source-based identity

Advantages:
- aligns with upstream systems
- feels intuitive to business users

Challenges:
- depends on source stability
- makes cross-system deduplication harder
- inherits upstream inconsistencies

### Composite identity

Advantages:
- offers flexibility
- can reflect business meaning

Challenges:
- requires careful field selection
- can become brittle if source fields change

---

## How It Works in Practice

A typical flow looks like this:

1. A resource enters the system through ingestion.
2. The system defines a canonical representation for identity.
3. The system generates a deterministic identifier.
4. The system registers the resource with that identifier.
5. Every downstream artifact stores a reference to the same identifier.
6. The system uses that identifier to manage updates, reprocessing, and reconciliation.

This approach allows the system to distinguish between:

- the original source resource
- derived artifacts
- multiple representations of the same logical object

---

## Example

Consider a PDF policy document.

The system may produce:

- a raw file in storage
- an extracted text version
- multiple retrieval chunks
- graph entities and relationships
- embeddings for each chunk
- a metadata record in a catalog

Without canonical identity, each layer assigns its own identifier and the system loses coherence.

With canonical identity, the system assigns one identifier at ingestion. Every chunk, graph element, embedding, and metadata record references that identifier directly or through lineage mappings.

Now the system can answer:

- which chunks came from this document
- which graph records derive from it
- which embeddings require updates
- whether the document already exists
- what downstream artifacts exist for audit or deletion

---

## Relationship to Lineage

Canonical identity and lineage solve different problems.

- Canonical identity answers: what is this?
- Lineage answers: where did this come from and what happened to it?

Canonical identity provides the anchor. Lineage records the transformations and relationships around that anchor.

Strong systems require both.

---

## Relationship to Retrieval

Canonical identity strengthens retrieval systems by:

- enabling deduplication
- linking chunks to source documents
- supporting citations and traceability
- simplifying re-indexing and updates
- enforcing governance over source material

In retrieval-driven systems, identity helps turn search results into trustworthy evidence.

---

## Where This Pattern Fits

Canonical identity acts as a foundation pattern.

It becomes critical in systems that include:

- document ingestion
- metadata catalogs
- semantic layers
- graph models
- vector retrieval
- lineage and governance
- multi-stage pipelines
- multi-representation architectures

The more representations a system creates, the more important canonical identity becomes.

---

## Design Guidance

Use canonical identity when:

- the same resource appears in multiple systems
- reconciliation matters
- provenance matters
- deduplication matters
- the system must support updates or deletion
- you want consistent behavior across representations

Be cautious when:

- source records change frequently
- business identity must remain stable despite content changes
- normalization rules are unclear

In these cases, separate:

- source identity
- canonical resource identity
- version identity

when needed.

---

## Summary

Canonical identity provides the stable reference point that keeps a system coherent across ingestion, storage, retrieval, graph projection, vectorization, and governance.

Define it early, propagate it consistently, and use it to reconcile every downstream representation.

When you manage identity well, systems become easier to reason about, easier to audit, and easier to evolve.
