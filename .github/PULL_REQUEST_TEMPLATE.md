<!--
Title: Conventional Commits, e.g. "feat(auth): add Telegram login" — it becomes the squash commit message.
-->

## What and why

<!-- What does this change do, and why is it needed? -->

Closes #

## How it was tested

<!-- Commands, test cases, screenshots. -->

## Checklist

- [ ] The PR title follows Conventional Commits (`feat:`, `fix:`, `feat!:` for breaking changes)
- [ ] Tests and documentation are added or updated
- [ ] `pre-commit run --all-files` passes locally
- [ ] No secrets in plain text; any `Secret` / `*.sops.yaml` is SOPS-encrypted
- [ ] Breaking changes and migration steps are described above
