# Operations

## Add a repository to the profile

Goal: the organization page lists a new repository with its status.

1. Create a branch: `git switch -c docs/profile-<repo>`.
2. In `profile/README.md`, find the row of the repository in **Repositories**, turn the name into a
   link to `https://github.com/<owner>/<repo>` and set the status (`Planned`, `In progress`,
   `Ready`).
3. After the first Scorecard run of that repository, append the badge to the status cell:

   ```markdown
   [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/<owner>/<repo>/badge)](https://scorecard.dev/viewer/?uri=github.com/<owner>/<repo>)
   ```

4. Add a line to `CHANGELOG.md` under **Unreleased**, commit, open a pull request.

Expected result: after the merge the organization page shows the link and the badge.
How to check: the `docs / docs` check passes (lychee verifies the new link).

## Change a default file

1. Edit the file (`SECURITY.md`, `CONTRIBUTING.md`, issue forms and so on) in a branch.
2. Check which repositories override it: they are not affected. See
   [Configuration → Inherited defaults](configuration.md#inherited-defaults).
3. Open a pull request; after the merge the change applies at once to every repository that
   inherits the file.

How to check: open **Issues → New issue** or **Security → Policy** in a repository without its own
file.

## Rotate the Scorecard token

The token expires after one year; rotate it a week earlier.

1. Generate a new token as in [Setup](setup.md#6-repository-secret-for-scorecard).
2. **Settings → Secrets and variables → Actions → `SCORECARD_TOKEN` → Update secret**.
3. **Actions → scorecard → Run workflow** is not available (no manual trigger); push any change to
   `master` or wait for the weekly run.
4. Delete the old token in **Developer settings → Fine-grained tokens**.

Expected result: the next **scorecard** run succeeds.

## Update the reusable workflows

`docs.yml` and `scorecard.yml` call [`sogeor/workflows`](https://github.com/sogeor/workflows) by commit SHA with a version comment.

1. Renovate opens a pull request with the new SHA after a new `workflows` release is 7 days old.
2. Read the `workflows` CHANGELOG for changed inputs and required check names.
3. If a job name changes, add the new check to the ruleset before merging and remove the old one after.
4. Update the **Versions** table in `README.md`.

How to check: `docs / docs` passes on the pull request; after the merge the next **scorecard** run succeeds.

## Update tool versions

Renovate opens pull requests on the first day of the month. After merging one:

1. Update the **Versions** table in `README.md`.
2. If `ACTIONLINT_VERSION` or `GITLEAKS_VERSION` in `validate.yml` changed, update the matching
   `*_SHA256` from the release checksums file.

How to check: `validate` passes on the pull request.

## Release

Releases are optional for this repository. When one is made: move **Unreleased** in
`CHANGELOG.md` to a version, merge, create a tag `vX.Y.Z` on `master` and a GitHub Release with
the changelog excerpt.
