# AGENTS.md — .github

→ [Org-wide rules](https://github.com/helpers4/.dev/blob/main/AGENTS.md): restrictions · commit format · license headers

## This Repository

**Purpose:** Org-level GitHub config — shared workflows, issue/PR templates, cross-repo automation.

```text
.github/
├── workflows/
│   ├── auto-assign.yml                          # Auto-assign issues/PRs to @baxyz + 'triage' label
│   ├── manual-fallback-website-typescript.yml   # Force TS doc rebuild (workflow_dispatch)
│   ├── manual-fallback-website-devcontainer.yml # Force DC doc rebuild (workflow_dispatch)
│   └── manual-fallback-website-action.yml       # Force Action doc rebuild (workflow_dispatch)
├── ISSUE_TEMPLATE/
├── PULL_REQUEST_TEMPLATE.md
└── .vscode/settings.json
```

**Cross-repo release pipeline:**

```text
<repo> release → dispatch → website rebuilds that section's docs
manual-fallback-website-*.yml → recovery when automatic dispatch fails
```

Auth for dispatches: GitHub App token via `TRIGGANATOR_ID` + `TRIGGANATOR_KEY`.
Workflows must exist on `main` to run. Dispatch events are async.
