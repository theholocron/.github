@../github-private/CLAUDE.md

@../github-private/CLAUDE.md

# CLAUDE.md

Conventions for working on `theholocron/.github`. Loaded automatically by
Claude Code into every conversation in this repo.

> **Local path:** `~/Code/theholocron/.github-repo/`
> **GitHub repo:** `theholocron/.github`

## What this repo is

Org-level community health files, reusable CI workflows, composite actions,
and workflow starter templates for the `theholocron` org. Other repos in the
org call the reusable workflows here with `uses: theholocron/.github/.github/workflows/<name>.yml@main`.

## Source of truth — what is generated vs. hand-maintained

**Do not edit generated files directly in this repo.** They will be
overwritten on the next sync.

| Path | Owned here? | Source |
|---|---|---|
| `.github/workflows/*.yml` | **No — generated** | `holocron/packages/cli/src/templates/index.ts` (`REUSABLE_WORKFLOWS`) |
| `.github/actions/*/action.yml` | **No — generated** | `holocron/packages/cli/src/templates/index.ts` (`ACTIONS`) |
| `workflow-templates/*.yml` | **No — generated** | `holocron/packages/cli/src/templates/` |
| `workflow-templates/*.properties.json` | **No — generated** | `holocron/packages/cli/src/templates/` |
| `.github/ISSUE_TEMPLATE/` | Yes | Hand-maintained here |
| `.github/pull_request_template.md` | Yes | Hand-maintained here |
| `.github/CODEOWNERS` | Yes | Hand-maintained here |
| `.github/labeler.yml` | Yes | Hand-maintained here |
| `.github/dependabot.yml` | Yes | Hand-maintained here |
| `.github/CONTRIBUTING.md` | Yes | Hand-maintained here |
| `.github/CODE_OF_CONDUCT.md` | Yes | Hand-maintained here |
| `.github/SECURITY.md` | Yes | Hand-maintained here |
| `.github/GOVERNANCE.md` | Yes | Hand-maintained here |
| `.github/SUPPORT.md` | Yes | Hand-maintained here |
| `.github/FUNDING.yml` | Yes | Hand-maintained here |
| `profile/` | Yes | Hand-maintained here |
| `.alexignore` | Yes | Hand-maintained here |
| `.alexrc.json` | Yes | Hand-maintained here — keep in sync with org standard; no `package.json` so `holocron setup` cannot run here |
| `.editorconfig` | Yes | Hand-maintained here |
| `.editorconfig-checker.json` | Yes | Hand-maintained here — keep in sync with org standard; no `package.json` so `holocron setup` cannot run here |
| `.gitattributes` | Yes | Hand-maintained here |
| `.gitignore` | Yes | Hand-maintained here |
| `CLAUDE.md` | Yes | Hand-maintained here |
| `holocron.config.json` | Yes | Hand-maintained here |
| `LICENSE` | Yes | Hand-maintained here |
| `README.md` | Yes | Hand-maintained here |
| `yamllint.config.yml` | Yes | Hand-maintained here |

Every generated file begins with:

```yaml
# AUTO-GENERATED — do not edit in theholocron/.github directly.
# Source:  theholocron/holocron · packages/cli/src/templates/index.ts
# Synced:  <timestamp>
# Tool:    holocron sync-github
# Changes: edit source in theholocron/holocron and push to alpha or main.
```

## How to update a generated workflow or action

1. Open `theholocron/holocron` (local path: `~/Code/theholocron/holocron/`)
2. Edit `packages/cli/src/templates/index.ts` — workflows are in the `REUSABLE_WORKFLOWS`
   export, actions are in the `ACTIONS` export (the `workflows/` and `actions/` YAML files
   were removed; `index.ts` is the single source of truth)
3. Push to `alpha` — **this is the active trigger branch right now** (see note below)
4. The `sync-github.yml` CI workflow in `holocron` runs `holocron sync-github`,
   opens a PR here on branch `chore/sync-templates`
5. Review and merge that PR — do not hand-edit the generated files

The sync command validates generated workflows with `actionlint` before
opening the PR, so CI on the PR should pass cleanly.

> **Note — `alpha` is the current sync trigger, not `main`.**
> All v2 work in `holocron` lives on `alpha`; `main` still tracks the v1
> stable line, so syncing from `main` would push stale templates. Once `alpha`
> is merged to `main` and a stable release is cut, the sync trigger should be
> flipped to fire on `main` pushes. Tracked in
> [theholocron/.github#25](https://github.com/theholocron/.github/issues/25).

## Action pinning — non-negotiable rule

**Always pin third-party actions to a full commit SHA, never a tag.**

```yaml
# Correct
- uses: actions/checkout@9c091bb21b7c1c1d1991bb908d89e4e9dddfe3e0 # v7.0.0

# Wrong — tags are mutable and can be force-pushed
- uses: actions/checkout@v7
- uses: actions/checkout@v4.2.2
```

The only exception is **our own composite actions**, which are pinned to
`@main` because we control the ref and it stays current automatically:

```yaml
- uses: theholocron/.github/.github/actions/setup@main
- uses: theholocron/.github/.github/actions/setup-node@main
- uses: theholocron/.github/.github/actions/install@main
```

When adding a new third-party action:
1. Find the latest release tag on its GitHub releases page
2. Click the tag → copy the full commit SHA from the URL or `git rev-parse`
3. Use `owner/action@<sha> # v<version>` format

## Composite actions (`.github/actions/`)

Three actions exist. All are generated; edit the templates in `holocron` to change them.

| Action | Purpose | Call |
|---|---|---|
| `setup` | Runs `setup-node` + `install` | `theholocron/.github/.github/actions/setup@main` |
| `setup-node` | pnpm + Node 22 + pnpm cache | `theholocron/.github/.github/actions/setup-node@main` |
| `install` | `pnpm install --frozen-lockfile` | `theholocron/.github/.github/actions/install@main` |

## Reusable workflows (`.github/workflows/`)

All workflows use `on: workflow_call` — they are not triggered directly.
Caller repos call them with `uses: theholocron/.github/.github/workflows/<name>.yml@main`.

| Workflow | Triggered by callers on | Purpose |
|---|---|---|
| `lint.yml` | push + PR | super-linter CI gate: Prettier, YAML, ESLint, Gitleaks, ActionLint |
| `review.yml` | PR only | ReviewDog inline annotations: ESLint, tsc, ShellCheck, Hadolint, etc. |
| `test.yml` | push + PR | vitest + Codecov |
| `typecheck.yml` | push + PR | `pnpm typecheck` (`tsc --noEmit`) |
| `codeql.yml` | push/PR to main + weekly | CodeQL security scan |
| `release.yml` | push to main or alpha | semantic-release + OIDC Trusted Publishing |
| `stale.yml` | daily schedule | marks stale issues/PRs |
| `greetings.yml` | PR + issues | first-time contributor welcome |
| `dependencies.yml` | PR | Dependabot semver-patch auto-merge |
| `bookkeeping-pr.yml` | PR opened/edited | labels PRs from Conventional Commit title |
| `audit.yml` | push + PR | BundleWatch bundle size |
| `sync-github.yml` | push to main or alpha in `holocron` | re-generates and PRs these files |

## Workflow starter templates (`workflow-templates/`)

Each `<name>.yml` + `<name>.properties.json` pair powers the
"By your organization" section in GitHub's Actions → New workflow UI.
Templates are thin callers of the matching reusable workflow. Generated;
edit source in `holocron`.

## Which repos call these workflows

Any `theholocron/*` repo with a `holocron.config.json` and a
`pnpm holocron setup` run will have thin caller files in
`.github/workflows/` that delegate to workflows here.

Key repos in the org:
- `theholocron/holocron` — the CLI source; also the origin of all syncs
- `theholocron/configs` — shared config packages (`@theholocron/*-config`)
- `theholocron/clients` — HTTP clients and API wrappers
- `theholocron/.github-private` — internal member documentation
- `theholocron/.github` — this repo

The `sync-github` workflow in `holocron` can target multiple repos:
- **Primary repo** (`theholocron/.github`) — receives composite actions +
  reusable workflows + templates via PR (branch protection assumed)
- **Secondary repos** — receive reusable workflows + thin callers via direct
  push to main

## `holocron.config.json`

This repo uses `holocron.config.json` (not `.ts`) because it has no
`package.json` — `@theholocron/cli` cannot be resolved at runtime without one.
This repo's config uses `"preset": "balanced"` because it has no test or build
workflows of its own.

## Workflow

- Conventional Commit types for this repo: `ci:` for workflow changes, `docs:`
  for community health files, `chore:` for maintenance.
- For generated file updates, the sync mechanism opens the PR automatically —
  don't manually apply those changes.

## Quality

- No test suite in this repo (no code logic to test).
- `pnpm lint` runs `yamllint` on workflow files.
- Generated workflows are validated by `actionlint` during the sync step in
  `holocron` before the PR is opened here.
- Branch protection on `main` requires the PR to pass CI before merge.

## Releases

This repo has no npm publish step. Changes take effect as soon as they land
on `main` because callers reference `@main`.

Community health files (CONTRIBUTING, CODE_OF_CONDUCT, etc.) are picked up
by GitHub automatically from the org's `.github` repo — no deploy step needed.
