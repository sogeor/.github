# 0001. Record architecture decisions

- Status: accepted
- Date: 2026-10-10

## Context and problem statement

Decisions about organization-wide defaults (which files are inherited, which settings every
repository uses) need to be traceable for contributors and for people adopting the model.

## Decision outcome

Record decisions as [MADR](https://adr.github.io/madr/) files in `docs/adr/`, numbered
`NNNN-title.md`, with status `proposed`, `accepted`, `deprecated` or `superseded by NNNN`.
A pull request that changes organization-wide defaults adds or updates an ADR.

### Consequences

- Decisions and their reasons are reviewable in the same pull request as the change.
- Platform-wide decisions live in the `docs` repository; this directory keeps decisions about
  organization defaults.
