<p align="center">
  <img src="https://raw.githubusercontent.com/helpers4/typescript/main/logo/Logo.svg" alt="helpers4" width="180" />
</p>

<h1 align="center">helpers4</h1>

<p align="center">
  <strong>Open-source utilities for TypeScript projects, development environments, and CI/CD pipelines.</strong>
</p>

<p align="center">
  <a href="https://helpers4.dev"><img src="https://img.shields.io/badge/docs-helpers4.dev-blue?logo=astro&logoColor=white" alt="Documentation" /></a>
  <a href="https://github.com/helpers4"><img src="https://img.shields.io/github/license/helpers4/typescript?label=license&color=blue" alt="License LGPL-3.0" /></a>
  <img src="https://img.shields.io/badge/everything-open--source-brightgreen" alt="Open Source" />
</p>

---

## What is helpers4?

**helpers4** is a collection of open-source utilities split across focused repositories, all designed around the same philosophy: **small, composable, well-tested tools** that you can adopt one piece at a time.

---

## Repositories

### [`typescript`](https://github.com/helpers4/typescript) — TypeScript helpers

<a href="https://www.npmjs.com/package/@helpers4/all"><img src="https://img.shields.io/npm/v/@helpers4/all?label=npm&color=cb3837" alt="npm" /></a>
<a href="https://www.npmjs.com/package/@helpers4/all"><img src="https://img.shields.io/npm/dm/@helpers4/all?color=blue" alt="downloads" /></a>
<img src="https://img.shields.io/badge/coverage-100%25-brightgreen" alt="coverage" />
<img src="https://img.shields.io/badge/tree--shakable-✓-green" alt="tree-shakable" />

Zero-dependency, tree-shakable utility functions for any TypeScript or JavaScript project. Published as individual npm packages per category — install only what you need.

```bash
npm install @helpers4/string @helpers4/array
```

```typescript
import { capitalize } from '@helpers4/string';
import { chunk }      from '@helpers4/array';

capitalize('hello world');  // "Hello world"
chunk([1, 2, 3, 4, 5], 2); // [[1, 2], [3, 4], [5]]
```

Available categories: `array` · `ci` · `color` · `commit` · `date` · `function` · `guard` · `id` · `map` · `markdown` · `node` · `number` · `object` · `observable` · `promise` · `set` · `string` · `type` · `url` · `version` — or install everything with `@helpers4/all`.

📖 [helpers4.dev/typescript](https://helpers4.dev/typescript)

---

### [`devcontainer`](https://github.com/helpers4/devcontainer) — DevContainer Features

<a href="https://github.com/helpers4/devcontainer"><img src="https://img.shields.io/badge/ghcr.io-helpers4%2Fdevcontainer-blue?logo=github&logoColor=white" alt="GHCR" /></a>
<a href="https://containers.dev/features"><img src="https://img.shields.io/badge/devcontainer-features-blue?logo=visual-studio-code&logoColor=white" alt="DevContainer Features" /></a>

Production-ready DevContainer Features published to GHCR. Drop them into any `devcontainer.json` for instant, reproducible development environments.

```json
{
  "features": {
    "ghcr.io/helpers4/devcontainer/essential-dev:1": {},
    "ghcr.io/helpers4/devcontainer/typescript-dev:1": {},
    "ghcr.io/helpers4/devcontainer/vite-plus:1": {},
    "ghcr.io/helpers4/devcontainer/git-absorb:1": {},
    "ghcr.io/helpers4/devcontainer/dotfiles-sync:1": {},
    "ghcr.io/helpers4/devcontainer/shell-history-per-project:1": {}
  }
}
```

Available features: `essential-dev` · `github-dev` · `typescript-dev` · `angular-dev` · `vite-plus` · `package-auto-install` · `pnpm-store` · `git-absorb` · `dotfiles-sync` · `auto-header` · `shell-history-per-project` · `claude-dev` · `copilot-dev` · `mistral-dev` · `peon-ping`

📖 [helpers4.dev/devcontainer](https://helpers4.dev/devcontainer)

---

### [`action`](https://github.com/helpers4/action) — GitHub Actions

<a href="https://github.com/marketplace?type=actions&query=helpers4"><img src="https://img.shields.io/badge/GitHub-Marketplace-blue?logo=github&logoColor=white" alt="GitHub Marketplace" /></a>

Reusable GitHub Actions for consistent CI/CD pipelines.

```yaml
- uses: helpers4/action/conventional-commits@v1
  with:
    validate-pr-title: true
    pr-comment: error
```

Available actions: `conventional-commits` — validates that all commit messages and PR titles follow the [Conventional Commits](https://www.conventionalcommits.org/) specification.

📖 [helpers4.dev/action](https://helpers4.dev/action)

---

## Documentation

Full documentation for all projects lives at **[helpers4.dev](https://helpers4.dev)**.

---

## License

All helpers4 repositories are licensed under the **[GNU Lesser General Public License v3.0 (LGPL-3.0-or-later)](https://www.gnu.org/licenses/lgpl-3.0.html)**.
