# Proposed conceptual data model

**Status: proposal.** This document defines the records and distinctions needed for the initial knowledge base. It is not a SQL migration, finalized schema, or commitment to a database product. See the [project overview](../README.md), [architecture](architecture.md), and [roadmap](roadmap.md).

The model preserves what a source says, identifies related material, and makes interpretations traceable. Indexing concepts organize terminology; claims about identity and events remain attributed and separately assessed.

## Core records

| Record | Purpose and essential distinctions |
| --- | --- |
| **Source work** | The underlying interview, article, book, dataset, or other work; creator, title, source type, and bibliographic identity. |
| **Edition or translation** | A particular published expression of a work; editor, translator, language, publication date, and edition details. |
| **Source version** | The specific acquired file, snapshot, transcript revision, or recording; origin URL, acquisition time, checksum, format, and applicable permissions. A checksum detects changes; it does not authenticate the contents. |
| **Passage** | A citeable segment of a source version, with page, paragraph, timestamp, or other locator. OCR and transcription corrections retain links to the original material. |
| **Concept and label** | A stable reference concept with preferred and alternative labels, language, scope, and ambiguity notes. Labels support lookup; they do not imply historical continuity or identity. |
| **Mention** | An occurrence of a term or description in a passage, linked to a proposed concept with contextual resolution and review status. |
| **Claim** | A specific assertion attributed to a speaker or source, with the supporting passage and distinction between reported observation and interpretation. |
| **Relation assertion** | A proposed connection between records, including predicate, attribution, source passage, and stance: supports, disputes, compares, hypothesizes, or leaves unresolved. |
| **Source dependency** | A documented or suspected citation, reproduction, syndication, or shared source relationship. Unknown independence remains unknown. |
| **Event** | A reported occurrence with uncertain time and place, associated accounts, and tentative links to other events. Similar descriptions do not automatically merge events. |
| **Assessment** | A dated review of a claim or relationship, naming the reviewer, reasoning, evidence status, limitations, and disagreements. Assessments remain separate from source statements. |
| **Rights and access policy** | Copyright or license information, contributor consent, permitted uses, audience, embargo, retention, and withdrawal handling. Permission to read does not automatically permit republication or model training. |
| **Processing run and derived record** | Input versions, software or model version, processing configuration, timestamps, and outputs such as extracted claims, summaries, search indexes, and embeddings. |

## Time, provenance, and interpretation

Keep claimed event time, estimated composition time, publication time, first recorded account time, and acquisition time separate. Represent approximate dates as ranges or qualified values, including unknown values; avoid artificial precision.

A relationship to a historical passage must identify the edition or translation actually consulted. A modern interpretation is its own attributed claim, not a replacement for the older passage. Conflicting interpretations can coexist without duplicating or rewriting the underlying source.

Retain the path from each excerpt and assessment to its original source chain. Retrieval should distinguish document count from distinct underlying source chains, and identify uncertain dependencies. Multiple copies of one interview do not become multiple independent accounts.

## Synthetic example

The following records are invented solely to illustrate the model:

- Concept `C-001` has preferred label **Grey alien** and spelling variant **Gray alien**. The label **Greys** requires context before resolution.
- Passage `P-101` contains “gray alien.” Mention `M-101` resolves that wording to `C-001`; this is a vocabulary match.
- A fictional modern essay compares `C-001` with a description in fictional **Temple Text A**, translation **T-1**. Relation assertion `R-201` records that the essay's author **compares** the concepts and cites both passages.
- A second fictional essay disputes that comparison. It receives a separate claim and stance, preserving the disagreement.

Neither comparison creates an alias or establishes shared identity. Search can surface both interpretations with their passages and explain why each result appeared.

## Retrieval and permissions

Each search result should carry its passage, source version, match reason, relevant dates and translation, stance, dependency context, and review status. **Extraction confidence** describes confidence that software parsed the source correctly; **evidence status** describes a reviewed assertion. Neither substitutes for the other.

Derived material must retain dependencies and enforce the permissions of its inputs. A derivative of multiple inputs defaults to the audience authorized for all of those inputs. Access checks must cover snippets, summaries, graph links, counts, and embeddings, as well as original files. Corrections or permission changes trigger updates to dependent indexes and caches. Withdrawal procedures must state retention and backup limits and cannot promise recall of already distributed public copies.
