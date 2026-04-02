<h1 align="center">helpers4 — .github</h1>

<p align="center">
  <strong>Shared GitHub resources, reusable workflows, and community health files for the helpers4 organization.</strong>
</p>

<p align="center">
  <a href="https://github.com/helpers4/.github/blob/main/LICENSE"><img src="https://img.shields.io/github/license/helpers4/.github?color=blue" alt="license" /></a>
  <a href="https://github.com/helpers4/.github"><img src="https://img.shields.io/github/last-commit/helpers4/.github" alt="last commit" /></a>
</p>

---

## Overview

This repository stores shared GitHub resources for the **helpers4** organization. It provides reusable CI/CD workflows, issue templates, PR templates, and community health files that apply to all repositories across the organization.

## Architecture

| Resource | Location | Purpose |
|----------|----------|---------|
| Workflow templates | `workflow-templates/` | Shown in GitHub UI under *Actions > New workflow* |
| Reusable workflows | `.github/workflows/` | Centralized CI/CD logic called by templates |
| Issue templates | `ISSUE_TEMPLATE/` | Bug report & feature request forms |
| PR template | `PULL_REQUEST_TEMPLATE.md` | Standardized pull request format |
| Community files | Root | Code of Conduct, Contributing, Security, Support |

## Shared Workflows

Templates reference reusable workflows using:

```yaml
uses: helpers4/.github/.github/workflows/<workflow-file>@main
```

**Why this pattern?**
- **Single source of truth** — change CI logic once, apply everywhere
- **No duplication** — repositories reference, not copy
- **Simple onboarding** — templates appear in GitHub's workflow picker

## Enable in a New Repository

1. Open the target repository on GitHub
2. Go to **Actions** → **New workflow**
3. Select a template from the organization section
4. Commit the generated workflow file

> **Note:** Workflows in the `.github` repository are not automatically executed in all repositories. They provide shared templates and reusable logic that other repositories opt into.

## Maintenance

- Update workflow logic in `.github/workflows/reusable-*.yml`
- Adjust defaults in `workflow-templates/*.yml` as needed
- Keep `*.properties.json` files for template metadata (name, description, icon)

## License

This project is licensed under the [GNU Lesser General Public License v3.0](LICENSE).

## Contributors

<table>
<tr>
    <td align="center" style="word-wrap: break-word; width: 150.0; height: 150.0">
        <a href="https://github.com/baxyz">
            <img src="https://avatars.githubusercontent.com/u/7852177?v=4" width="100;" alt="Bérenger"/>
            <br />
            <sub style="font-size:14px"><b>Bérenger</b></sub>
        </a>
    </td>
</tr>
</table>