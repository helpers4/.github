# .github

This repository stores shared GitHub resources for the `helpers4` organization.

## Shared workflows

We use this pattern:

- **Template workflows** in `workflow-templates/` (shown in GitHub UI: *Actions > New workflow*)
- **Reusable workflows** in `.github/workflows/` (centralized logic)

Templates call reusable workflows using:
`uses: helpers4/.github/.github/workflows/<file>@main`

## Why this pattern

- Avoids duplicating CI logic across repositories
- Makes updates easier (change once, apply everywhere)
- Keeps onboarding simple with ready-to-use templates

## Enable in a project repository

1. Open the target repository on GitHub
2. Go to **Actions** > **New workflow**
3. Select a template from the organization section
4. Commit the generated workflow file

> Note: workflows in the `.github` repository are not automatically executed in all repositories. They provide shared templates and reusable logic.

## Maintenance

- Update workflow logic in `.github/workflows/reusable-*.yml`
- Adjust default values in `workflow-templates/*.yml` when needed
- Keep `*.properties.json` files for better template display in GitHub UI (name, description, category, icon)