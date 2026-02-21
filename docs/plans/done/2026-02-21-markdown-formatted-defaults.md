# Convert Formatted Defaults to Markdown

## Context

The `defaults/formatted/` directory currently contains `.conf` files with comment-style headers (`# GroupName`) and `# ===...===` section dividers. This works but does not leverage markdown rendering: no table of contents, no anchor links, no per-group copy buttons on GitHub. Converting to `.md` with real headers and fenced code blocks makes these reference files more navigable and useful when viewed on GitHub.

## Design Decisions

- **One code block per group.** Named groups (2+ options sharing a prefix) get an H3 header and their own fenced code block. Consecutive singletons share one code block with no header. Isolated singletons between named groups get their own small code block.
- **Blockquote for source command.** The tmux generation command appears as `> \`tmux ...\`` at the top of each file, visually distinct from both headers and content.
- **Code fence language tag:** ` ```tmux ` for syntax highlighting.
- **Header hierarchy:** H1 = file title, H2 = major sections (only in `all-options.md` and `bindings.md`), H3 = option/action groups.

## Target Output Examples

### Single-scope file (e.g., `server-options.md`)

```markdown
# Server Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gs`

```tmux
backspace C-?
buffer-limit 50
codepoint-widths
```

### Command

```tmux
command-alias[0] split-pane=split-window
...
```

```tmux
copy-command ''
```

### Default

```tmux
default-client-command new-session
default-terminal tmux-256color
```
```

### Multi-scope file (`all-options.md`)

H1 = "All Options", H2 = scope sections ("Server Options", "Session Options", "Window Options"), H3 = groups within each scope.

### Bindings file (`bindings.md`)

H1 = "Key Bindings", H2 = key tables ("copy-mode (emacs)", "prefix", etc.), H3 = action groups ("Cancel", "Cursor", etc.).

## Implementation Steps

### 1. Add a title helper function

Add a function (or associative array) that maps filenames to display titles:
- `server-options` -> "Server Options"
- `global-options` -> "Session Options" (matches the existing convention, not the filename)
- `window-options` -> "Window Options"
- `bindings` -> "Key Bindings"
- `all-options` -> "All Options"
- Others: capitalize and replace hyphens with spaces

### 2. Rewrite `format_grouped_options()` for markdown output

Current behavior: writes `# header`, then option lines with `# GroupName` comments and blank-line spacing.

New behavior:
- Track whether currently inside an open code fence
- Open a fence (`\`\`\`tmux`) before emitting option lines
- Close the fence before emitting an H3 header or at end of output
- Replace `# ${key^}` with `### ${key^}` (outside the fence)
- Consecutive singletons accumulate inside one open fence
- When transitioning from singleton to named group (or vice versa), close the current fence first

Does NOT emit H1/blockquote (that is the caller's responsibility, since `format_all_options` handles H1 differently).

### 3. Update `format_options()` to emit H1 + blockquote

Before calling `format_grouped_options`, write the H1 title and blockquote source command to the output file. Pass the body content through `format_grouped_options` which appends to the same file (or use a compound group redirect).

### 4. Rewrite `format_all_options()` for markdown output

- Emit H1 ("All Options") + blockquote
- Replace the three-line `# ===...===` banners with `## Server Options (\`show-options -gs\`)` (etc.)
- Within each scope section, use the same code-fence grouping logic from step 2
- Can either call `format_grouped_options` per section or inline the same logic (current code inlines it; keep that pattern but add fence tracking)

### 5. Rewrite `format_bindings()` for markdown output

- Emit H1 ("Key Bindings") + blockquote
- Replace key table banners with H2 headers
- Replace action group `# ${gkey^}` comments with H3 headers
- Add fence tracking: open fence before binding lines, close before headers

### 6. Update `main()` for new file extension

- Change output paths from `.conf` to `.md`
- Add cleanup step: `rm -f "${FMT_DIR}"/*.conf` to remove old `.conf` files
- Update status messages to reflect `.md`

### 7. Delete old `.conf` files from `defaults/formatted/`

The cleanup step in `main()` handles this, but the git changeset will show the `.conf` files as deleted.

### 8. Update documentation

- **README.md:** Update "Formatted Defaults" section to mention markdown files
- **CLAUDE.md** and **.claude/CLAUDE.md:** Update file listings to show `.md` extensions and describe the markdown format

## Files to Modify

- `bin/format-defaults` (primary, all formatting logic changes)
- `defaults/formatted/*.conf` (deleted, replaced by `.md` files)
- `README.md`
- `CLAUDE.md`
- `.claude/CLAUDE.md`

## Verification

1. Run `bin/format-defaults` and confirm it produces `.md` files in `defaults/formatted/`
2. Spot-check `server-options.md` for correct H1, blockquote, H3 headers, and fenced code blocks
3. Spot-check `all-options.md` for correct H2 scope sections within the H1
4. Spot-check `bindings.md` for correct H2 key tables and H3 action groups
5. Confirm no `.conf` files remain in `defaults/formatted/`
6. Visually review a rendered markdown file (e.g., via `glow` or GitHub preview) to confirm structure
