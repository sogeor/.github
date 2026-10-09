# Security

## What is guaranteed

- No secrets in the repository: gitleaks runs in pre-commit and CI; GitHub secret scanning with
  push protection is enabled.
- Every change to `master` is a signed commit that passed the required checks.
- Workflows use actions pinned by full SHA, minimal `permissions` and `persist-credentials: false`;
  they are checked by actionlint and zizmor.
- Downloaded tools are verified by SHA-256; Python tools are installed with `--require-hashes`.

## What is not guaranteed

- Links in the profile point to repositories that may not exist yet; their status is informational.
- The default security policy does not replace a repository's own policy where one exists.

## Threat model

| Threat | Trust boundary | Countermeasure |
|---|---|---|
| Tampered profile or policy (misleading reporters, phishing links) | Contributor → `master` | Required PR checks, signed commits, `CODEOWNERS` review by the maintainer |
| Malicious pull request changing workflows (CWE-829, CWE-94) | Fork PR → Actions runner | `pull_request` trigger only, read-only token, no secrets in `validate` and `docs`; zizmor checks for template injection |
| Compromised third-party action or tool (CWE-494) | Upstream → runner | Actions pinned by SHA, checksums for downloads, hashed Python requirements, Renovate PRs reviewed manually |
| Leaked Scorecard token | Repository secret → runner | Fine-grained PAT, read-only, one repository, one-year expiry; used only in the `scorecard` workflow on `master` |
