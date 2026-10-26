# Working on The Halls of Amenti

## Current state

This is a planning foundation. Read [README.md](README.md),
[docs/architecture.md](docs/architecture.md),
[docs/data-model.md](docs/data-model.md), and
[docs/roadmap.md](docs/roadmap.md) before implementing features. Distinguish
proposed designs from implemented behavior in documentation and reports.

## Project intent

Connect a reference library with community contributions through source-linked
topic discovery. Preserve personal accounts faithfully, attribute interpretations,
and make the reasoning behind suggested connections visible. Assess particular
claims rather than assigning credibility scores to people or identities.

## Development guidance

- Keep changes focused on the current milestone and compatible with the existing
  repository once an implementation exists.
- Keep exact source versions and passage locators behind every extracted claim
  and substantive relationship.
- Distinguish aliases, similarity, an author's interpretation, and evidence for a
  specific claim. AI-generated relationships are identifiable proposals.
- Track source dependencies; summaries and reprints are not independent sources.
- Apply access permissions before passages reach an AI model. Include attachment
  access, snippets, counts, relationship views, caches, and exports in the design.
- Use clearly labeled synthetic fixtures for examples and tests. Keep real
  participant records, source collections, credentials, and backups out of Git.
- Keep processing/model versions and source dependencies sufficient to regenerate
  affected indexes and summaries after a correction or access change.
- Prefer portable records and a small number of services. Add infrastructure when
  a measured workload or concrete requirement justifies it.
- For implemented features, verify the relevant acceptance criteria in the
  roadmap and report meaningful limitations. Documentation-only changes need
  link and consistency review rather than an application test scaffold.

Framework, hosting, embedding-model, and licensing choices are currently open.
Record adopted decisions with their rationale when implementation requires them.
