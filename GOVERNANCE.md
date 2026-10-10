# Governance

## Model

The sogeor organization follows a single-maintainer model. The maintainer makes final decisions
on scope, design and releases of every repository. Significant design decisions are recorded as
ADRs in the [`docs`](https://github.com/sogeor/docs) repository.

Anyone may propose changes through issues and pull requests. Proposals are accepted when they
fit the [roadmap](ROADMAP.md), pass all required checks and follow [CONTRIBUTING.md](CONTRIBUTING.md).

This is the default for all repositories; a repository's own `GOVERNANCE.md` takes precedence.

## Roles

| Role | Who | Responsibilities |
|---|---|---|
| Maintainer | [@bloogefest](https://github.com/bloogefest) | Reviews and merges pull requests; triages issues; handles vulnerability reports ([SECURITY.md](SECURITY.md)); manages secrets, branch rules and organization settings; keeps the profile, roadmap and documentation current. |
| Contributor | Anyone | Opens issues and pull requests that follow [CONTRIBUTING.md](CONTRIBUTING.md). |
| Renovate (bot) | Mend Renovate | Opens dependency update pull requests; never merges. |

## Decisions

- Routine changes: merged by the maintainer once required checks pass.
- Architectural changes: an ADR in `docs/adr/` (status `proposed`) is added in the same pull request.
- Security fixes: handled privately per [SECURITY.md](SECURITY.md).

## Continuity

The organization `sogeor` owns all repositories. If the maintainer becomes unavailable, an
organization owner can take over the maintainer role.
