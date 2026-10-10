# Repository setup

The checklist of GitHub settings for **every** sogeor repository, including this one. Apply it
when you create a repository or fork this one. Steps are in order; each ends with a check.

!!! note "Placeholders"
    `<owner>` is your GitHub organization, `<repo>` is the repository name. Required status check
    names depend on the repository: `linters` and `docs` here, plus stack-specific jobs elsewhere.

## 1. Required files

Copy the files listed in [Configuration → Per-repository files](configuration.md#per-repository-files)
from this repository or from [`images`](https://github.com/sogeor/images), then adjust names and
status checks. Defaults inherited from this repository (security policy, contributing rules,
code of conduct, governance, support, issue and pull request templates) may be omitted or
overridden.

Check: the repository **Insights → Community Standards** page shows every item as present.

## 2. About

**Repository → ⚙ next to About** (right column on the main page):

| Field | Rule |
|---|---|
| Description | One English sentence, at most 350 characters: what it is and what is inside, nothing that is not done yet |
| Website | The page on the documentation site once it exists; empty until then |
| Topics | 10–20 lowercase hyphenated topics for the stack, purpose and domain that really exist in the repository |
| Include in the home page | Releases — on once releases exist; Deployments — on if the repository uses Environments; Packages — off |

When typing topics, finish each with **Space**: Enter picks the highlighted suggestion instead.

Values for this repository:

| Field | Value |
|---|---|
| Description | `Organization profile and default community health files for sogeor: security policy, contributing rules, issue and pull request templates, and the repository setup checklist.` |
| Website | empty |
| Topics | `github-profile` `community-health` `organization-profile` `issue-templates` `pull-request-template` `security-policy` `contributing` `code-of-conduct` `governance` `devsecops` `openssf-scorecard` `mkdocs` |
| Include in the home page | Releases — off; Deployments — off; Packages — off |

## 3. Pull requests

**Settings → General → Pull Requests:**

- Allow merge commits — off; Allow squash merging — on; Allow rebase merging — off.
- Automatically delete head branches — on.

Check: the merge button of a pull request offers only **Squash and merge**.

## 4. Branch ruleset

**Settings → Rules → Rulesets → New ruleset → New branch ruleset:**

| Setting | Value |
|---|---|
| Ruleset Name | `master` |
| Enforcement status | Active |
| Bypass list | **Add bypass → Repository admin**, mode **For pull requests only** |
| Target branches | **Add target → Include default branch** |
| Restrict deletions | on |
| Require signed commits | on |
| Require a pull request before merging | on, Required approvals `0` |
| Require status checks to pass | on, **Require branches to be up to date**; checks `linters`, `docs` |
| Block force pushes | on |

Status checks appear in **Add checks** only after they have run at least once: open the first
pull request, let the checks run, then add them.

Check: a direct `git push` to `master` is rejected with `GH013: Repository rule violations`.

## 5. Advanced Security

**Settings → Advanced Security:**

| Feature | Setting |
|---|---|
| Private vulnerability reporting | Enable; Require a CWE — off; Daily advisory limit — 10 |
| Dependency graph | On |
| Dependabot alerts | On |
| Dependabot security updates, version updates | Off — Renovate updates dependencies |
| CodeQL analysis | **Set up → Default** (analyzes GitHub Actions workflows) |
| Code quality | Off |
| Secret Protection | Enable, then **Push protection → Enable** |

Check: the **Security** tab shows **Report a vulnerability**.

## 6. Repository secret for Scorecard

1. **Profile → Settings → Developer settings → Personal access tokens → Fine-grained tokens →
   Generate new token:** Resource owner `<owner>`, **Only select repositories** → `<repo>`,
   **Repository permissions → Administration: Read-only**, expiration 1 year.
2. **Repository → Settings → Secrets and variables → Actions → New repository secret:**
   name `SCORECARD_TOKEN`, value — the token.

Check: after the next push to `master` the **scorecard** run succeeds and the Scorecard badge in
`README.md` shows a score.

## 7. Environments

Only for repositories whose workflows use secrets beyond `SCORECARD_TOKEN` (this repository has
none). **Settings → Environments → New environment**, then **Deployment branches and tags →
Selected branches and tags → Add rule → `master`**. Paste values without leading or trailing
spaces and tabs.

## 8. Renovate

1. Install the [Renovate GitHub App](https://github.com/apps/renovate) → **Configure** →
   `<owner>` → **Only select repositories** → add `<repo>` → **Save**.
2. The configuration is in `renovate.json`: no automerge, grouped updates, SHA-pinned
   pre-commit hooks through a regex manager, hash-locked Python requirements, Conventional Commits
   titles (`semanticCommits`).

Check: an issue **Dependency Dashboard** appears within an hour.

When merging a Renovate pull request with **Squash and merge**, check the **Commit message** field:
it must be a Conventional Commits title with the pull request number, for example
`chore(deps): update github-actions (#7)`.

After merging a Renovate pull request, update the **Versions** table in `README.md`: Renovate does
not change it.

## 9. Organization profile

Add the repository to `profile/README.md` in this repository: link, purpose, status and the
Scorecard badge after the first Scorecard run. See [Operations](operations.md#add-a-repository-to-the-profile).

## 10. OpenSSF Best Practices (optional)

Register the repository at [bestpractices.dev](https://www.bestpractices.dev), answer the criteria
in English with full URLs in "Met URL" fields, and add the badge to `README.md`.
