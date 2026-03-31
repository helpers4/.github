# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in any helpers4 project, please report it responsibly.

**Do NOT open a public issue.**

Instead, please use [GitHub Security Advisories](https://github.com/helpers4/.github/security/advisories/new) or contact us via the repository's **Security** tab.

## What to Include

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

## Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial assessment**: Within 1 week
- **Fix and disclosure**: Coordinated with reporter

## Supported Versions

Only the latest released version of each project is supported with security updates.

| Project | Supported |
|---|---|
| @helpers4/typescript | Latest major version |
| @helpers4/devcontainer | Latest release |
| @helpers4/action | Latest release |
| helpers4 website | Current deployment |

## Security Best Practices

Our repositories follow these practices:
- Minimal permissions in GitHub Actions workflows
- External PRs run in isolated environments without access to secrets
- GitHub App authentication over personal access tokens
- Automated dependency vulnerability scanning via Dependabot
- Branch protection rules on all default branches
