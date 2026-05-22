# AGENTS.md - Organization Governance

## ⛔ CRITICAL RESTRICTIONS

- **NEVER execute `git push`** - The user will push manually after review
- **NEVER use GPT models** - Use Claude models only (claude-sonnet-4, Claude Opus 4.5)
- **Everything in English** - Code, comments, commits, documentation, logs, PR descriptions

## Organization Context

**helpers4** is a collection of open-source utilities across 5 repos: `typescript`, `devcontainer`, `action`, `website`, `.github` (this repo). All licensed LGPL-3.0.

## Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/) with a gitmoji between the scope and the description.

**Format:** `<type>(<scope>): <emoji> <description>`

**Scopes:** defined in `.vscode/settings.json` (`conventionalCommits.scopes`)

| Type | Primary | Alternatives (gitmoji.dev) | When to use |
|------|---------|---------------------------|-------------|
| feat | ✨ | 🚸 UX, ♿️ a11y, 🌐 i18n, 💬 text/literals | New feature |
| fix | 🐛 | 🚑️ hotfix, 🔒️ security, 🩹 trivial, 🥅 errors, 🚨 warnings, ✏️ typo | Bug fix |
| docs | 📝 | 💡 source comments, 📄 license | Documentation |
| refactor | ♻️ | 🎨 structure, 🔥 remove code, ⚰️ dead code, 🚚 move/rename | Code refactoring |
| test | ✅ | 🧪 failing test, 💚 fix CI test | Tests |
| chore | 🔧 | 🙈 gitignore, 🔖 tag/release, 📌 pin deps, 🩺 healthcheck | Maintenance |
| perf | ⚡️ | — | Performance |
| style | 💄 | 🎨 code style | Code style / UI |
| ci | 👷 | 💚 fix CI | CI/CD |
| build | 📦️ | ➕ add dep, ➖ remove dep, ⬆️ upgrade dep, ⬇️ downgrade dep | Build system |
| revert | ⏪️ | — | Revert |

> Pick the **most specific** gitmoji that matches the change. The primary is the safe default; reach for an alternative when it adds real signal. Full list: https://gitmoji.dev

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
│   ├── manual-fallback-website-typescript.yml   # Manual fallback: force TS website update
│   ├── manual-fallback-website-devcontainer.yml # Manual fallback: force DC website update
│   └── manual-fallback-website-action.yml       # Manual fallback: force Action website update
├── ISSUE_TEMPLATE/                      # Org-wide issue templates
├── PULL_REQUEST_TEMPLATE.md             # Org-wide PR template
├── AGENTS.md                            # This file
├── LICENSE                              # LGPL-3.0
└── .vscode/settings.json
```

### Workflows

**auto-assign.yml:**
- Triggers on issues/PRs opened
- Auto-assigns to @baxyz
- Adds 'triage' label to issues
- Uses `actions/github-script@v7`

**manual-fallback-website-*.yml** (3 similar workflows):
- Purpose: Manual fallback to force website updates when needed
- Trigger: `workflow_dispatch` only
- Flow: Operator-triggered dispatch to website repo
- Payload includes version/source context used by website workflows
- Auth: GitHub App token via `TRIGGANATOR_ID` + `TRIGGANATOR_KEY`

### Cross-Repo Release Pipeline

```
typescript release (in typescript repo) → website rebuilds TS docs
devcontainer release (in devcontainer repo) → website rebuilds DC docs
action release (in action repo) → website rebuilds Action docs
manual-fallback-website-*.yml (in .github repo) → force rerun when automatic flow fails
```

### Important Notes

- Workflows must exist in `main` branch to run
- Dispatch events are async — website doesn't auto-update immediately
- Automatic dispatch source of truth is each source repository release workflow
- `.github` manual-fallback workflows are for recovery / force-rerun only
## Repository Links

- TypeScript: https://github.com/helpers4/typescript
- DevContainer: https://github.com/helpers4/devcontainer
- Actions: https://github.com/helpers4/action
- Website: https://github.com/helpers4/website
- Organization: https://github.com/helpers4

## Questions?

If you need clarification on any aspect, open an issue or comment on the PR. We're here to help!
