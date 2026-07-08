# theholocron/.github

Org-level community health files, reusable CI workflows, composite actions,
and workflow starter templates for the `theholocron` org — and any org that
wants to reuse them.

## Using reusable workflows

Any public repo can call these workflows directly. A full CI setup is a handful
of thin caller files in `.github/workflows/`:

```yaml
# .github/workflows/lint.yml
name: Lint
on: [push, pull_request]
permissions:
  contents: write
  statuses: write
jobs:
  lint:
    uses: theholocron/.github/.github/workflows/lint.yml@main
    secrets: inherit
```

For `theholocron` repos the recommended approach is [`holocron setup`](#holocron-setup),
which writes and maintains these files automatically from `holocron.config.json`.

## Available workflows

| Workflow | Trigger | Purpose |
|---|---|---|
| `lint.yml` | push + PR | super-linter CI gate — Prettier, YAML, ESLint configs, Gitleaks, ActionLint |
| `test.yml` | push + PR | vitest + Codecov coverage upload |
| `typecheck.yml` | push + PR | `pnpm typecheck` (`tsc --noEmit`) |
| `codeql.yml` | push/PR to main + weekly | CodeQL security scan (javascript-typescript) |
| `review.yml` | PR only | ReviewDog annotation layer — ESLint, tsc, ShellCheck, Hadolint, ActionLint, Gitleaks, YamlLint, dotenv-linter, Alex |
| `release.yml` | push to main | semantic-release + OIDC Trusted Publishing (no `NPM_TOKEN` needed) |
| `stale.yml` | daily schedule | marks stale issues/PRs |
| `greetings.yml` | PR + issues | first-time contributor welcome message |
| `dependencies.yml` | PR | Dependabot auto-merge for semver-patch updates |
| `bookkeeping-pr.yml` | PR opened/edited | labels PRs from Conventional Commit title (`fix:` → bug, `feat:` → enhancement, etc.) |
| `audit.yml` | push + PR | BundleWatch bundle size analysis |

Each workflow accepts inputs to customise behaviour — see the workflow files in
`.github/workflows/` for the full input/secret declarations.

## Composite actions

Reusable action steps callable from any workflow:

```yaml
- uses: theholocron/.github/.github/actions/setup@main
```

| Action | Purpose |
|---|---|
| `setup` | Orchestrates `setup-node` + `install` in one step |
| `setup-node` | pnpm + Node 22 with pnpm dependency caching |
| `install` | `pnpm install --frozen-lockfile` |

## Workflow starter templates

The `workflow-templates/` directory powers the **"By your organization"**
section in GitHub's **Actions → New workflow** UI. Every template is a thin
caller of the matching reusable workflow above — repos that adopt a template
get the same logic as repos that use `holocron setup`.

## `holocron setup`

For `theholocron` repos, the CLI manages everything from a `holocron.config.json`
at the repo root:

```jsonc
{
  "project": {
    "name": "my-project",
    "repo": "theholocron/my-project",
    "repoPolicy": {
      "preset": "strict",
      "requiredChecks": ["Lint entire codebase", "Run tests and collect coverage", "tsc --noEmit"]
    },
    "workflows": ["lint", "test", "typecheck", "codeql", "review", "release"]
  },
  "providers": {
    "vault": ["doppler", { "project": "my-project", "config": "dev" }],
    "source": "github",
    "ci": "github",
    "secrets": "github"
  }
}
```

Running `pnpm holocron setup` (or `npx @theholocron/cli setup`) will:

- Enable all GitHub security features (Dependabot, secret scanning, CodeQL, etc.)
- Apply repo settings (squash-only merges, auto-merge, no wiki, etc.)
- Create branch protection rulesets with the configured required checks
- Write thin workflow caller files to `.github/workflows/`
- Provision `.github/dependabot.yml` with grouped update configuration

See [theholocron/holocron](https://github.com/theholocron/holocron) for the full CLI docs.

## Source of truth

The workflow and action files in this repo are **generated** from
[theholocron/holocron](https://github.com/theholocron/holocron) — do not edit them
directly here. To update a workflow:

1. Edit `packages/cli/src/templates/workflows/<name>.yml` in `holocron`
2. Push to `alpha` — the `sync-github` CI workflow opens a PR here automatically

Community health files (`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, issue templates,
`CODEOWNERS`, `labeler.yml`, etc.) are hand-maintained in this repo directly.
