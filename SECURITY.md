# Security Policy

## Supported versions

Only the latest release of each Sogeor project receives security fixes.

## Reporting a vulnerability

**Do not open a public issue for security problems.**

Report vulnerabilities privately:

1. **Preferred:** use GitHub private vulnerability reporting — open the repository's **Security** tab and click **Report a vulnerability**.
2. **Alternatively:** email **<security@sogeor.com>** with the subject `SECURITY: <repository>`.

Please include:

- the affected repository, version or commit;
- a description of the issue and its impact;
- steps to reproduce or a proof of concept;
- any known mitigation.

## What to expect

| Step | Target time |
|---|---|
| Acknowledgement of the report | 3 business days |
| Initial assessment | 7 days |
| Fix for critical and high severity issues | 30 days |

We will keep you informed, credit you in the advisory if you wish, and coordinate the disclosure date with you. Please give us a reasonable time to release a fix before any public disclosure.

## Scope

In scope: code and configuration in the [sogeor](https://github.com/sogeor) repositories and services under `*.sogeor.com`.
Out of scope: denial-of-service or volumetric testing, social engineering, physical attacks, and findings in third-party services.

Testing against production services must not access other users' data, degrade service or persist beyond what is needed to demonstrate the issue. Good-faith research that follows this policy will not be pursued legally.
