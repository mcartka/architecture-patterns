# Examples

## Internal Knowledge Assistant

An employee asks:

What is the current travel reimbursement policy for contractors?

A strong retrieval layer may:

- use keyword retrieval for policy phrases and exact terminology
- use vector retrieval for semantically related policy language
- filter results to current policy documents only
- rank the latest approved policy above archived versions
- return chunks with source references and dates

This gives the assistant grounded evidence instead of loosely related text.

---

## Support Troubleshooting

A support engineer searches for guidance on a recurring integration error.

A strong retrieval layer may combine:

- keyword retrieval for the exact error code
- vector retrieval for similar incident summaries
- structured filters for product and version
- graph retrieval for linked systems and dependencies

This helps the system retrieve both the exact issue and the broader operational context.

---

## Case Review

An analyst needs all relevant material for a case.

A strong retrieval layer may combine:

- structured retrieval for case ID and date range
- document retrieval for notes and supporting files
- graph retrieval for linked people, organizations, and events

This creates a more complete evidence set than any single retrieval mode would produce alone.
