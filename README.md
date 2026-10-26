# The Halls of Amenti

A shared library for experience, sources, and inquiry.

The Halls of Amenti is a proposed knowledge commons that connects a core reference
library with community contributions. Its goal is to help people discover relevant
threads across personal accounts, historical and religious texts, esoteric
writings, research, public records, and news, while making the origin and meaning
of each connection inspectable.

## Project status

**Planning foundation.** This repository currently contains design documents and
an implementation roadmap. There is no application, deployed service, database,
or populated research corpus yet. Technology choices below are proposals.

## Intended experience

When a contributor mentions a subject, the system should surface related passages
from the material it has indexed and explain why each result appeared:

- A direct mention or alternative spelling.
- A similar description.
- A comparison or interpretation attributed to a particular author.
- A relevant event, source citation, or research question.
- Supporting, conflicting, or unresolved material for a specific claim.

For example, a **Grey aliens** topic could recognize **Gray aliens** and
contextually relevant uses of **Greys**, then offer source-linked comparisons.
An ambiguous word, resemblance, or later interpretation remains distinguishable
from independently corroborated evidence.

## Design principles

- Preserve contributors' wording and control over authorized uses.
- Link findings and comparisons to exact source passages and versions.
- Separate concepts, mentions, claims, interpretations, and assessments.
- Record copying and citation chains so repeated coverage stays recognizable.
- Make AI suggestions reviewable and keep their origin visible.
- Support participation with limited time, money, or technical experience.
- Keep records and source files exportable as the project grows.

## Design documents

| Document | Purpose |
| --- | --- |
| [Architecture](docs/architecture.md) | Proposed storage, ingestion, discovery, and access design |
| [Data model](docs/data-model.md) | Source records, concepts, claims, and attributed relationships |
| [Roadmap](docs/roadmap.md) | First prototype, acceptance criteria, and later stages |
| [Contributor guidance](AGENTS.md) | Working context for future development and AI-assisted changes |

The proposed starting architecture is **PostgreSQL with full-text search and
pgvector, object storage for original files, and a background ingestion worker**.
The application framework, hosting provider, embedding model, budget, and software
license remain open decisions.

## First implementation milestone

Demonstrate one complete path: ingest a small permitted text collection, preserve
passage citations, recognize a topic and its aliases, surface relevant passages
with explanations, review a suggested relationship, and update the topic view.
The [roadmap](docs/roadmap.md) defines the expected behavior.

This repository is for code, design documents, and clearly labeled synthetic test
fixtures. Research originals, participant accounts, credentials, and database
backups belong in their designated storage with appropriate access controls.
