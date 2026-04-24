# Workflows Runbook

This folder contains organization-level workflows for helpers4.

## Website update workflows: auto vs manual

### Automatic source of truth

Website update dispatch events are sent by release workflows in source repositories:

- `helpers4/typescript/.github/workflows/release.yml` → `typescript-release`
- `helpers4/devcontainer/.github/workflows/release.yml` → `devcontainer-release`
- `helpers4/action/.github/workflows/release.yml` → `action-release`

### Manual fallback workflows in this repo

Use these only when you need to force a rerun:

- `manual-fallback-website-typescript.yml`
- `manual-fallback-website-devcontainer.yml`
- `manual-fallback-website-action.yml`

These workflows dispatch events to `helpers4/website` and do not replace automatic release triggers.

## When to use manual fallback

Use manual fallback if:

- automatic dispatch failed,
- website workflow failed after dispatch and needs retrigger,
- docs need forced regeneration for operations reasons.

## Quick operations

### Force TypeScript docs regeneration

1. Open **Actions** in `helpers4/.github`.
2. Run **Manual Fallback - Trigger Website Update (TypeScript)**.
3. Provide `version` (for example `2.0.0-alpha.20`).
4. Verify `helpers4/website` workflow **On TypeScript Release**.

### Force DevContainer docs regeneration

1. Run **Manual Fallback - Trigger Website Update (DevContainer)**.
2. Verify `helpers4/website` workflow **On DevContainer Release**.

### Force Action docs regeneration

1. Run **Manual Fallback - Trigger Website Update (Action)**.
2. Verify `helpers4/website` workflow **On Action Release**.
