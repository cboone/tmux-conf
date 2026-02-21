# Add Formatted Defaults

## Context

The `defaults/` directory contains raw tmux output files with no visual grouping. A script will read these raw files and produce formatted versions in `defaults/formatted/`, grouping related options and bindings automatically by prefix pattern matching.

## Approach: `bin/format-defaults` shell script

A single shell script that reads raw files from `defaults/` and writes formatted output to `defaults/formatted/`. All grouping logic is automatic, based on option name prefixes and binding action patterns. No hand-maintained lookup tables.

### Option file formatting

Applies to: `server-options.conf`, `global-options.conf`, `window-options.conf`, `colour-options.conf`, `format-options.conf`, `separator-options.conf`, `style-options.conf`

Algorithm:
1. Pass through the header comment and blank line after it
2. For each option line, extract the option name (first field, strip `[N]` array index suffixes)
3. Derive a group key: first hyphen-delimited word of the option name (e.g., `status-left-style` -> `status`, `copy-mode-mark-style` -> `copy`)
4. When the group key changes from the previous line:
   - If the new group has 2+ consecutive options with the same key: insert a blank line, then a `# <Key capitalized>` header
   - If the new group is a singleton: insert a blank line only (no header), unless it's adjacent to another singleton (then no blank line either, to avoid excessive spacing)
5. Preserve option lines exactly as they appear in the raw file

This produces clean clusters for the major groups (`status-*`, `pane-*`, `window-*`, `copy-*`, `display-*`, `terminal-*`, `update-*`, `visual-*`, etc.) while keeping stray singletons compact.

### `all-options.conf` formatting

Algorithm:
1. Read option names from the three individual raw files (`server-options.conf`, `global-options.conf`, `window-options.conf`) to build scope membership sets
2. Process `all-options.conf` line by line; when an option's scope differs from the previous line's scope, insert a section divider:
   ```
   # ============================================================
   # Server options (show-options -gs)
   # ============================================================
   ```
3. Within each scope section, apply the same prefix-based grouping as the individual option files

### `bindings.conf` formatting

Algorithm:
1. Parse each `bind-key` line to extract: repeat flag (`-r`), key table (`-T <table>`), key name, and action
2. Collect all bindings per table (including distinguishing repeat vs non-repeat prefix bindings as separate sections)
3. For each binding, derive an action group key:
   - If action contains `send-keys -X <cmd>` (or `-FX`): group key = first word of `<cmd>` before first hyphen (e.g., `cursor-left` -> `cursor`, `scroll-down` -> `scroll`)
   - If action starts with `command-prompt ... { <cmd> ... }`: group key = first word of `<cmd>` (e.g., `rename-window` -> `rename`)
   - If action starts with `confirm-before ...`: extract the inner command after the `-p "..."` flag; group key = first word of that command (e.g., `kill-window` -> `kill`)
   - Otherwise: group key = first word of the action before first hyphen (e.g., `select-window` -> `select`, `new-window` -> `new`)
4. Sort bindings within each table by group key, then alphabetically by key name within each group
5. Output with:
   - Prominent section dividers between key tables
   - `# <Group key capitalized>` sub-headers for groups with 2+ bindings
   - Blank line separation between groups
   - Singleton groups handled the same way as option files (no header, merge adjacent singletons)

### File list

**Input** (read-only): all 9 files in `defaults/`

**Output** (generated): 9 files in `defaults/formatted/`, same filenames

**Script**: `bin/format-defaults`

## Additional Changes

1. **Fix raw `format-options.conf`**: Add the missing header comment (separate commit)
2. **Update README.md**: Document the `defaults/formatted/` directory and the script
3. **Update `.claude/CLAUDE.md`**: Add formatted directory to repository structure

## Commit Strategy

1. `fix: add missing header comment to defaults/format-options.conf`
2. `feat: add format-defaults script`
3. `feat(formatted): generate formatted defaults`
4. `docs: document formatted defaults and format script`

## Verification

- Run `bin/format-defaults` and confirm it produces output in `defaults/formatted/`
- For each option file: strip comments and blank lines from both raw and formatted, diff to confirm identical option content
- For `bindings.conf`: count `bind-key` lines in raw vs formatted, confirm equal
- For `all-options.conf`: confirm all three scope sections are present and all options accounted for
