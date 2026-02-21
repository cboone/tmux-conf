# Plan: GitHub Action to update defaults on new tmux releases

## Context

The `bin/update-defaults` script regenerates `defaults/*.conf` files from an unconfigured tmux server. Currently this is a manual process. Since tmux releases are published on GitHub (`tmux/tmux`), a scheduled workflow can detect new releases, build tmux from source, regenerate the defaults, and open a PR automatically.

## Approach

Create a single workflow file at `.github/workflows/update-defaults.yml` that:

1. Runs weekly (Monday 06:00 UTC) and supports manual `workflow_dispatch` with an optional version override
2. Fetches the latest stable tmux release via the GitHub API (`repos/tmux/tmux/releases/latest`)
3. Checks for an existing open PR for that version to avoid duplicates
4. Builds tmux from the release tarball (no `autoconf`/`automake` needed)
5. Runs `bin/update-defaults`
6. If files changed, creates a PR via `peter-evans/create-pull-request@v7`

No version-tracking file is needed. `peter-evans/create-pull-request` natively skips PR creation when there is no diff.

## Workflow steps

| # | Step | Detail |
|---|------|--------|
| 1 | Detect version | `gh api repos/tmux/tmux/releases/latest --jq '.tag_name'`, or use the `workflow_dispatch` input |
| 2 | Check for existing PR | `gh pr list --head chore/update-defaults-tmux-VERSION --state open` |
| 3 | Checkout repo | `actions/checkout@v4` |
| 4 | Install deps | `apt-get install libevent-dev libncurses-dev bison` |
| 5 | Build tmux | Download release tarball, `./configure && make && sudo make install` |
| 6 | Regenerate | `./bin/update-defaults` with `TERM=xterm-256color` |
| 7 | Open PR | `peter-evans/create-pull-request@v7` with branch `chore/update-defaults-tmux-VERSION` |

Steps 3-7 are skipped if step 2 finds an existing open PR.

## Naming conventions

- **Branch**: `chore/update-defaults-tmux-VERSION` (e.g., `chore/update-defaults-tmux-3.7`)
- **Commit**: `chore: regenerate defaults for tmux VERSION`
- **PR title**: same as commit message
- **PR body**: links to the workflow run and tmux release notes

## Permissions

- `contents: write` (push branch)
- `pull-requests: write` (create PR)

## Concurrency

A `concurrency` block prevents overlapping runs:

```yaml
concurrency:
  group: update-defaults
  cancel-in-progress: true
```

## Files to create/modify

- **Create**: `.github/workflows/update-defaults.yml`
- **Optional**: create `automation` label via `gh label create` (the PR references it; can be omitted)

## Verification

1. Push the workflow to the `feature/automate-updates` branch
2. Trigger manually via `gh workflow run update-defaults.yml` (no version input, to test auto-detection)
3. Trigger manually with a specific version input (e.g., `3.6a`) to test the override path
4. Confirm the generated PR has the correct title, body, branch, and file changes
5. Confirm a second run for the same version skips PR creation (duplicate check)
