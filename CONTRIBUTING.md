# Contributing

These are the default rules for all [sogeor](https://github.com/sogeor) repositories.
A repository's own `CONTRIBUTING.md` adds stack-specific requirements, tests and local setup.

## Process

1. Open an issue in the repository for bugs and feature requests (English or Russian).
   Report vulnerabilities privately per [SECURITY.md](SECURITY.md).
2. Create a branch `feat/...` or `fix/...` and open a pull request to `master`.
3. Requirements for a pull request to be accepted:
   - [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) messages;
   - signed commits;
   - all required checks green;
   - `README.md` and `CHANGELOG.md` updated when behavior changes;
   - an ADR draft in `docs/adr-drafts/` for architectural changes.

By contributing you agree that your contribution is licensed under the repository license (Apache-2.0).

## Conventions

- Everything in the repositories is in English.
- External dependencies are pinned to exact versions; GitHub Actions by full SHA with a version comment.
- No secrets in any form; examples use `CHANGE_ME`.
- `pre-commit` with gitleaks and the stack linters runs before every commit:

```bash
pre-commit install
pre-commit run --all-files
```

## Code of conduct

This project follows the [Code of Conduct](CODE_OF_CONDUCT.md).
