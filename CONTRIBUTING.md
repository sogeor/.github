# Contributing to Sogeor

Thank you for your interest in Sogeor. This document applies to every repository in the [sogeor](https://github.com/sogeor) organization unless a repository has its own `CONTRIBUTING.md`.

## Before you start

- **License.** Sogeor repositories are *source-available*, not open source. You may read the code, open issues and submit pull requests, but you may not copy, redistribute or reuse it. Read the `LICENSE` file of the repository.
- **Contributor License Agreement.** Before your first pull request can be merged you will be asked to accept the [CLA](CLA.md) by posting a comment. A bot will guide you.
- **Code of Conduct.** All participation is covered by the [Code of Conduct](CODE_OF_CONDUCT.md).
- **Security issues** must not be reported in public issues. See [SECURITY.md](SECURITY.md).

## Reporting bugs and requesting features

Use the issue forms of the repository. Search existing issues first. A good bug report contains the version or commit, steps to reproduce, expected and actual behaviour, and logs with secrets removed.

## Pull requests

1. Open an issue first for anything larger than a small fix, so the approach can be agreed on.
2. Fork the repository and create a branch from `master`.
3. Install the hooks: `pre-commit install`. They run gitleaks, linters and the checks that block unencrypted secrets.
4. Keep the change focused. One pull request solves one problem.
5. Add or update tests and documentation.
6. Run the checks locally (see the repository README, section *Development*).
7. Open the pull request using the template and link the issue.

### Pull request title: Conventional Commits

Pull requests are squash-merged, and the **title becomes the commit message**. It must follow [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(<optional scope>): <description>
```

| Type | Meaning | Version change |
| --- | --- | --- |
| `feat` | new functionality | minor |
| `fix` | bug fix | patch |
| `perf` | performance improvement | patch |
| `deps` | dependency update | patch |
| `revert` | revert of a previous change | patch |
| `docs`, `refactor`, `test`, `build`, `ci`, `chore` | no user-visible change | none |

Append `!` after the type (`feat!: …`) or add a `BREAKING CHANGE:` footer for incompatible changes. Versions follow [Semantic Versioning](https://semver.org/); releases and `CHANGELOG.md` are generated automatically by release-please.

Examples: `feat(auth): add Telegram login`, `fix(api): correct pagination offset`, `docs: describe local setup`.

### Commits

- Sign your commits (`git commit -S`); unsigned commits cannot be merged into `master`.
- Never commit secrets. Kubernetes `Secret` manifests and `*.sops.yaml` files must be encrypted with SOPS.

## Review

A maintainer reviews every pull request. All required checks must pass: tests, linters, secret scanning, the PR title check and the CLA check. Maintainers may ask for changes or close pull requests that do not fit the project.
