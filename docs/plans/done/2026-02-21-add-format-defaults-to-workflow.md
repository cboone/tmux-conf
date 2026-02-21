# ~~Add format-defaults to the weekly GitHub Actions workflow~~

## Context

The `update-defaults.yml` workflow runs weekly to detect new tmux releases,
build tmux, regenerate raw `defaults/*.conf` files via `bin/update-defaults`,
and open a PR with the changes. The `bin/format-defaults` script converts those
raw `.conf` files into grouped Markdown in `defaults/formatted/`, but it is not
part of the automated pipeline. This means formatted docs drift out of sync
whenever a new tmux version lands.

## Changes

**File:** `.github/workflows/update-defaults.yml`

1. Add a new step after "Regenerate defaults" that runs `./bin/format-defaults`.
2. Update the PR body to mention that formatted Markdown files are also
   regenerated (both `defaults/*.conf` and `defaults/formatted/*.md`).

No other files need to change.

## Verification

1. Review the diff to confirm the new step runs after `update-defaults` and
   carries the same `if` guard (`steps.check-pr.outputs.skip != 'true'`).
2. Trigger the workflow manually via `workflow_dispatch` to confirm end-to-end
   behavior (requires a push to a branch with the updated workflow).
