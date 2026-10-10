# Troubleshooting

## Checks

| Symptom | Cause | Solution |
|---|---|---|
| markdownlint `MD041` on `.github/PULL_REQUEST_TEMPLATE.md` | The template starts with a `##` heading, not `#` | Keep the `<!-- markdownlint-disable-file MD041 -->` first line; it is invisible in pull requests |
| lychee fails on `.../security/advisories/new` or `.../issues/new` | These pages require sign-in | They are excluded in `docs.yml`; add similar sign-in pages to the `--exclude` list |
| lychee fails on a link to a repository that does not exist yet | Planned repositories have no page | Keep planned repositories in the profile without links until they exist |
| `mkdocs build --strict` fails with "not included in the nav" | A new page in `docs/` is missing from `nav` | Add the page to `nav` in `mkdocs.yml` |
| A required status check never appears in the ruleset | The check has not run yet | Open a pull request, let it run, then add the check |

## Dependencies

| Symptom | Cause | Solution |
|---|---|---|
| Renovate proposes a downgrade of a pre-commit hook (for example v6 → v3.4.0) | The built-in pre-commit manager misreads SHA-pinned hooks | It is disabled in `renovate.json`; the regex manager handles `rev: <sha> # vX` |
| Dependency Dashboard shows **Config Migration Needed** for `pip-compile` | Renovate now reads the lock files (`*.txt`) instead of `*.in` | `managerFilePatterns` points to `requirements-*.txt`; the files keep the pip-compile header, which Renovate uses to rerun the command |
| `pip install --require-hashes` fails | `*.txt` was edited by hand or generated without hashes | Regenerate: `pip-compile --generate-hashes --allow-unsafe --strip-extras -o .github/requirements-docs.txt .github/requirements-docs.in`; keep the generated header and remove `--no-index` from it if your pip configuration adds it |

## GitHub settings

| Symptom | Cause | Solution |
|---|---|---|
| A workflow fails to use a secret or variable value | The value was pasted with a trailing space or tab | Re-enter the value; scripts in other repositories trim whitespace, GitHub does not |
| Push rejected with `GH013` | The ruleset requires a pull request and signed commits | Push a branch and open a pull request; sign commits |
| Scorecard run fails with 401 | `SCORECARD_TOKEN` expired or lacks Administration: Read-only | [Rotate the token](operations.md#rotate-the-scorecard-token) |

## Still stuck

Open an issue in this repository (English or Russian) with the failing log, or see
[SUPPORT.md](https://github.com/sogeor/.github/blob/master/SUPPORT.md).
