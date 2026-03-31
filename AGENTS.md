# AGENTS.md - Organization Governance

## ⛔ CRITICAL RESTRICTIONS

- **NEVER execute `git push`** - The user will push manually after review
- **NEVER use GPT models** - Use Claude models only (claude-sonnet-4, Claude Opus 4.5)
- **Everything in English** - Code, comments, commits, documentation, logs, PR descriptions

## Organization Context

**helpers4** is a collection of open-source utilities across 5 repos: `typescript`, `devcontainer`, `action`, `website`, `.github` (this repo). All licensed AGPL-3.0.

## Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/) with a gitmoji between the scope and the description.

**Format:** `<type>(<scope>): <emoji> <description>`

**Scopes:** governance, workflows, CI-CD, templates

| Emoji | Type | Description |
|-------|------|-------------|
| ✨ | feat | New feature |
| 🐛 | fix | Bug fix |
| 📝 | docs | Documentation |
| ♻️ | refactor | Code refactoring |
| ✅ | test | Tests |
| 🔧 | chore | Maintenance |
| 🚀 | perf | Performance |
| 💄 | style | Code style |
| 👷 | ci | CI/CD |
| 📦 | build | Build system |
| ⏪ | revert | Revert |

**Examples:**
- `feat(workflows): ✨ add release automation`
- `docs(governance): 📝 update contributing guide`
- `chore(CI-CD): 🔧 bump action versions`

---

## This Repository

**Purpose:** Organization-level GitHub configuration — shared workflows, issue/PR templates, and cross-repo automation. This is a special `.github` repository (GitHub reads it for org-wide defaults).

### Project Structure

```
.github/
├── workflows/
│   ├── auto-assign.yml                  # Auto-assign issues/PRs to @baxyz
│   ├── trigger-website-typescript.yml   # Notify website on TS release
│   ├── trigger-website-devcontainer.yml # Notify website on DC release
│   └── trigger-website-action.yml       # Notify website on Action release
├── ISSUE_TEMPLATE/                      # Org-wide issue templates
├── PULL_REQUEST_TEMPLATE.md             # Org-wide PR template
├── AGENTS.md                            # This file
├── LICENSE                              # AGPL-3.0
└── .vscode/settings.json
```

### Workflows

**auto-assign.yml:**
- Triggers on issues/PRs opened
- Auto-assigns to @baxyz
- Adds 'triage' label to issues
- Uses `actions/github-script@v7`

**trigger-website-*.yml** (3 similar workflows):
- Purpose: Cross-repo notification when a release happens
- Trigger: `repository_dispatch` or `workflow_dispatch`
- Flow: Extract version from tag → send `createDispatchEvent()` to website repo
- Payload includes version + source repo info
- Requires secret: `HELPERS4_WEBSITE_TOKEN` (cross-repo GitHub token with `repo` scope)

### Cross-Repo Release Pipeline

```
typescript release → trigger-website-typescript.yml → website rebuilds TS docs
devcontainer release → trigger-website-devcontainer.yml → website rebuilds DC docs
action release → trigger-website-action.yml → website rebuilds Action docs
```

### Important Notes

- Workflows must exist in `main` branch to run
- Dispatch events are async — website doesn't auto-update immediately
- `HELPERS4_WEBSITE_TOKEN` must have `repo` scope for cross-repo dispatch
## Repository Links

- TypeScript: https://github.com/helpers4/typescript
- DevContainer: https://github.com/helpers4/devcontainer
- Actions: https://github.com/helpers4/action
- Website: https://github.com/helpers4/website
- Organization: https://github.com/helpers4

## Questions?

If you need clarification on any aspect, open an issue or comment on the PR. We're here to help!
