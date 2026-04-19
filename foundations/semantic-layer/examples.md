
## `examples.md`

```markdown
# Examples

## Customer Across Multiple Systems

An organization stores customer-related information in three systems:

- CRM uses `client`
- billing uses `account_holder`
- support uses `customer_name`

A semantic layer does not force those systems to rename their fields.

Instead, it defines **Customer** as the shared business concept and maps each source field into that concept.

This allows:

- analytics teams to report consistently
- applications to use a common interpretation
- search systems to retrieve across systems
- AI systems to ground responses in agreed meaning

---

## Case Management

A case management environment may store:

- person records in one system
- events in another
- documents in a shared repository
- locations in a separate database

A semantic layer can define concepts such as:

- Person
- Case
- Event
- Document
- Location

It can also define relationships such as:

- Person involved_in Case
- Case includes Event
- Document supports Case
- Event occurred_at Location

This creates a consistent conceptual model across heterogeneous systems.
