# Proposed architecture

**Status: proposal.** This document describes a possible foundation for The Halls of Amenti. It does not describe implemented software or commit the project to a cloud provider, application framework, model provider, or deployment runtime.

## Design goals

The repository would support a reference corpus and contributed accounts, with traceable connections across sources. A reader should be able to inspect why a passage was retrieved, which source version it came from, and who proposed or reviewed a connection.

The initial architecture would keep authoritative records in a relational database, original files in object storage, and search representations as replaceable derivatives. A knowledge graph is part of the data model; a dedicated graph database would be an optional implementation choice.

## Proposed components

| Component | Responsibility |
| --- | --- |
| PostgreSQL | Source catalogue, versions, passages, concepts, aliases, relationships, assessments, permissions, and job state |
| PostgreSQL full-text search | Words, phrases, names, and reviewed query expansions |
| pgvector | Passage embeddings and semantic similarity retrieval |
| Object storage | Original files, permitted captures, recordings, and extraction outputs |
| Background worker | Extraction, OCR, transcription, indexing, candidate connections, and invalidation jobs |
| Application/API | Submission, browsing, review, permission enforcement, and cited answers |

Structured relationship tables would connect concepts, mentions, claims, sources, and assessments. Each asserted connection would retain its supporting passage, attribution, and review state. Semantic similarity would propose a relationship rather than establish corroboration.

## Source lineage and citation anchors

Preserve the distinction between a **source**, a particular **source version**, and a **passage** within that version. Different editions, translations, captures, and extraction revisions should remain distinguishable.

Passages would retain stable identifiers, original wording, normalized search text, and appropriate citation anchors: page and section, text offsets with quoted context, timestamps, or image regions. A checksum identifies file content; it does not authenticate the assertions inside the file. Extraction and embedding records would identify their input versions and processing methods.

## Ingestion and updates

The proposed workflow is:

1. Register the source, provenance, access conditions, and permitted uses.
2. Preserve the authorized original and its version metadata.
3. Extract text or transcribe media, retaining citation anchors.
4. Identify exact duplicates and propose relationships among near-duplicates, editions, and republications.
5. Create passages, candidate concept mentions, and attributed statements.
6. Generate permitted search representations and discover possible connections.
7. Present proposed links for review and update affected research views.

Jobs should be repeatable without creating duplicate records and should expose failures and incomplete processing. Improved OCR or transcription would create a new extraction version and trigger deliberate updates to dependent passages, indexes, and summaries.

Access and reuse permissions are separate metadata. Public availability must not be recorded as permission to acquire, process, or redistribute an entire copyrighted work. A source can remain a catalogue entry with a link and permitted excerpts when full-text ingestion is unavailable. Coverage indicators should distinguish these entries from searchable full text.

## Retrieval and automatic connections

Search would combine reviewed aliases, full-text results, semantic passage matches, and relevant graph relationships. Candidate results would be combined, reranked, and grouped by source lineage so republications remain visible without appearing to be independent origins.

Each result should explain its match: explicit terminology, alias, descriptive resemblance, cited interpretation, or a relationship relevant to a particular claim. Historical terminology and later interpretations would remain separately attributed.

Retrieval completeness would be described relative to the indexed, authorized corpus. Semantic search cannot guarantee every relevant passage. Evaluation should use representative questions and reviewed expected results, including ambiguous terms and restricted collections. Approximate vector indexes introduce additional retrieval tradeoffs that require measurement.

## Permission boundaries

Authorization must constrain material before it reaches a model. Database policies and application checks would enforce access independently of generated text or prompts. Application roles must account for PostgreSQL privileges that can bypass row-level policies.

Restrictions would cover originals, attachments, passages, embeddings, graph edges, snippets, counts, caches, exports, and processing logs. Sharing a concept identifier would not grant access to its linked records. Public summaries would use sources approved for public use, including separately approved excerpts where contributors permit a wider audience.

Permission changes and withdrawals would invalidate dependent search entries and cached or generated outputs. Restoration procedures must reapply current restrictions before restored material becomes accessible.

## Preservation, export, and growth

Export should include portable metadata, relationships, provenance, permission records, and authorized files. Derived indexes should be rebuildable from retained, permitted inputs. Backups would cover both database and object storage, with documented retention and restoration exercises. Replication alone would not be the recovery plan.

Expansion should follow measured workload: passage counts, media volume, concurrency, retrieval quality, latency, and operating effort. Consider dedicated search infrastructure when retrieval requirements exceed the initial system, a graph service when repeated complex traversals dominate, and an analytical warehouse when aggregate reporting interferes with interactive use. Add worker capacity when ingestion becomes the constraint. No fixed document-count threshold is proposed.

## References

- [PostgreSQL full-text indexes](https://www.postgresql.org/docs/current/textsearch-indexes.html)
- [pgvector capabilities and retrieval considerations](https://github.com/pgvector/pgvector)
- [PostgreSQL row security](https://www.postgresql.org/docs/current/ddl-rowsecurity.html)
- [W3C Web Annotation Data Model](https://www.w3.org/TR/annotation-model/)
- [PostgreSQL backup and restore](https://www.postgresql.org/docs/current/backup.html)
