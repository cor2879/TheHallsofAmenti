# Roadmap

## Goal and current status

The first useful outcome is a traceable answer to a research question: find relevant passages, explain their connections, distinguish independent sources from repetitions, and regenerate a reviewed topic page. This foundation is a documentation proposal. It does not implement ingestion, search, access controls, or publication.

Development should follow one complete vertical slice before expanding the corpus or adding infrastructure.

## 1. Foundation

Agree the source, passage, assertion, relationship, provenance, and review vocabulary described in the accompanying architecture and data-model documents. Keep source statements, human interpretations, and machine suggestions distinguishable throughout the workflow.

Prepare a small fixture set explicitly labeled **synthetic demonstration material**. Include a document using “Grey,” one using “Gray,” a person with the surname Grey, an attributed historical comparison, and copies derived from one original. These fixtures establish expected behavior without implying that invented accounts are evidence.

## 2. First working prototype

Implement this sequence using the fixtures:

1. Ingest permitted text, recording its source identity, version, reuse basis, and content hash.
2. Preserve exact passages with stable identifiers and locators into the retained source version. Keep original text separate from normalized search text.
3. Create a canonical research topic for “Grey aliens,” including the spelling variant “Gray aliens.” Resolve labels using context and retain distinct records for ambiguous uses.
4. Retrieve exact text matches, ranked semantic candidates, and explicitly recorded reference relationships. Each result explains **why it was found** and links to its supporting passage.
5. Group sources by known derivation, citation, or syndication. Preserve uncertain dependencies as uncertain.
6. Let a reviewer accept, reject, or revise proposed assertions and relationships, retaining the decision and its rationale.
7. Regenerate a draft topic page from reviewed records, with citations, competing interpretations, and unresolved questions. Publication remains a separate human action.

Coverage indicators should describe the caller’s eligible indexed corpus, including visible sources and passages awaiting or failing processing. Exact search should expose all matching eligible records through pagination. Semantic discovery returns ranked candidates: report the search scope and returned count without presenting those candidates as an exhaustive set of conceptual matches. Similarity is a retrieval signal, never a belief score.

### Acceptance checklist

- [ ] Known Grey/Gray fixture passages appear through the intended spelling and topic searches, with exact supporting text and a useful why-found explanation.
- [ ] The unrelated surname Grey does not become an alias or automatic member of the topic; a literal text search may still return it.
- [ ] A historical comparison records who made the comparison and where. It does not become an unqualified equivalence between traditions or entities.
- [ ] Syndicated copies remain findable but are grouped with their originating source rather than counted as independent corroboration.
- [ ] Clear alias matches can link automatically. Interpretive or identity assertions remain proposed until reviewed; publishing a draft topic page is a separate human action.
- [ ] A source correction or withdrawal identifies affected passages, assertions, links, cached answers, and topic pages, and invalidates or regenerates the appropriate derivatives.
- [ ] Coverage counts distinguish indexed material from pending work and distinguish semantic candidates from exhaustive exact matches.
- [ ] Before restricted contributions, unauthorized access to a restricted fixture reveals no title, excerpt, relationship, existence, or count through any retrieval path.

## 3. Curated public-reference pilot

Replace or supplement fixtures with a modest, deliberately selected corpus whose permitted uses are recorded. Preserve editions, translations, attribution, and publication/capture dates. Review expected matches and misleading associations across different source types. Expand only when users can reliably trace a page’s statements back to its sources.

## 4. Restricted contributions

Introduce participant material after access checks succeed across retrieval, files, graph traversal, generated answers, caches, and exports. A restricted fixture must leak no title, excerpt, relationship, existence, or count to an unauthorized caller. Verify permission changes and withdrawal propagation before inviting sensitive submissions.

## 5. Scale by measurement

Measure retrieval quality, review workload, ingestion throughput, latency, and operating cost. Add specialized search or graph infrastructure only when a measured limitation justifies it.

Runtime, hosting, budget, embedding provider/model, and project/content licensing choices remain pending. They do not block this documentation foundation.
