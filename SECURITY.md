# Security Policy

This is the default policy for all [sogeor](https://github.com/sogeor) repositories.
A repository's own `SECURITY.md` takes precedence.

## Supported versions

The `master` branch and the latest release tag of each repository.

## Reporting a vulnerability

Do not open a public issue. Use **Private Vulnerability Reporting** of the affected repository:
`https://github.com/sogeor/<repository>/security/advisories/new`.

Reports are accepted in English or Russian. Initial response within 7 days.
Fix targets: Critical — 7 days, High — 30 days, Medium — 90 days.

## Response process

1. Acknowledge the report within 7 days.
2. Confirm and assess severity (CVSS) privately in a draft security advisory.
3. Fix in a private fork of the advisory and release the fix.
4. Publish the advisory and a CHANGELOG entry, crediting the reporter unless they ask for anonymity.
5. Request a CVE through GitHub when applicable.

Fix targets apply from confirmation.

## Out of scope

- Vulnerabilities in third-party dependencies without demonstrated impact on this project (report them upstream);
- the lab infrastructure itself (hosts, domains): do not scan or attack it;
- social engineering and denial of service.
