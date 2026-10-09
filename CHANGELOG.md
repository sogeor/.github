# Changelog

All notable changes to this project are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- `GOVERNANCE.md`, `SUPPORT.md`, `ROADMAP.md`, `CHANGELOG.md`, `CODEOWNERS`.
- `validate` workflow (yamllint, actionlint, zizmor, gitleaks) and pre-commit hooks.
- `docs` workflow (markdownlint, lychee, `mkdocs build --strict`) and `mkdocs.yml`.
- OpenSSF Scorecard workflow and Renovate configuration.
- Documentation in `docs/`: overview, getting started, repository setup checklist, configuration,
  operations, architecture, security, troubleshooting, ADR 0001.

### Changed

- Profile rewritten for the cluster constructor architecture and the current repository names.
- Pull request template renamed to `.github/PULL_REQUEST_TEMPLATE.md`.

## [0.1.0] - 2026-10-09

### Added

- Organization profile, default security policy, contributing rules, code of conduct,
  issue and pull request templates.
