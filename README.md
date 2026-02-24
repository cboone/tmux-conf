# tmux conf

Reference documentation for tmux default configuration settings, plus personal tmux config.

The `defaults/` directory contains files generated from a clean tmux server with no user configuration (`tmux -L unconfigured -f /dev/null start-server`), capturing every built-in option and key binding. These files are automatically updated whenever a new version of tmux is released.

## Default Reference Files

| File                     | Contents                                                                        |
| ------------------------ | ------------------------------------------------------------------------------- |
| `all-options.conf`       | Combined server, session, and window options                                    |
| `binding-notes.conf`     | Key binding notes for prefix table (`list-keys -N`)                             |
| `bindings.conf`          | Default key bindings for all key tables (copy-mode, copy-mode-vi, prefix, root) |
| `colour-options.conf`    | Color-related options                                                           |
| `format-options.conf`    | Format string options (`status-format`, `window-status-format`, etc.)           |
| `global-options.conf`    | Session-level options (`show-options -g`)                                       |
| `separator-options.conf` | Separator options                                                               |
| `server-options.conf`    | Server-level options (`show-options -gs`)                                       |
| `style-options.conf`     | Style-related options                                                           |
| `window-options.conf`    | Window-level options (`show-options -gw`)                                       |

## Formatted Defaults

The `defaults/formatted/` directory contains the same data as Markdown files, reformatted for readability. Options are grouped by name prefix with section headers, and key bindings are organized by table and action type. Each group appears in its own fenced code block under a descriptive heading.

To regenerate the formatted files from the raw defaults:

```bash
bin/format-defaults
```

## Regenerating Defaults

Run the update script to regenerate all files at once:

```bash
./bin/update-defaults
```

The script reads the tmux command from each file's header comment, runs it against an unconfigured tmux server, and writes the output back. It prints progress and the tmux version used.

## License

[MIT License](./LICENSE). TL;DR: Do whatever you want with this software, just keep the copyright notice included. The authors aren't liable if something goes wrong.
