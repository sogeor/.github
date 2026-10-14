# Getting started

Goal: a local clone with all checks passing and a live preview of the documentation.

## Prerequisites

| Tool | Version | Used for |
|---|---|---|
| Git | any recent | Clone, signed commits |
| Python | 3.12 | pre-commit, yamllint, zizmor, MkDocs |
| Node.js | 20 or newer | markdownlint-cli2 through pre-commit |
| GPG or SSH signing key | — | Signed commits are required by the branch ruleset |

On Windows, run the Python steps in WSL (Ubuntu 24.04 ships Python 3.12).

## 1. Clone and install tools

```bash
git clone https://github.com/sogeor/.github.git sogeor-.github
cd sogeor-.github
python3 -m pip install --user pre-commit
pre-commit install
```

Expected result: `pre-commit installed at .git/hooks/pre-commit`.

## 2. Run all checks

```bash
pre-commit run --all-files
```

Expected result: every hook reports `Passed` or `Skipped`. The same checks run in the `validate`
and `docs` workflows.

## 3. Preview the documentation

```bash
python3 -m pip install --user --require-hashes -r .github/requirements-docs.txt
python3 -m mkdocs serve
```

Expected result: the site at `http://127.0.0.1:8000` with every page in the navigation. To check
the build as CI does, run `python3 -m mkdocs build --strict`.

## 4. Propose a change

1. Create a branch: `git switch -c docs/<short-name>` (`feat/`, `fix/`, `docs/`, `chore/`).
2. Commit with a signed [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) message:
   `git commit -S -m "docs: <what changed>"`.
3. Push and open a pull request; fill in the template. It is merged with **Squash and merge**.

How to check: the pull request shows green `linters` and `docs / docs` checks.

If something fails, see [Troubleshooting](troubleshooting.md).
