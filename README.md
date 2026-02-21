# Tmux Conf

Reference documentation for tmux default configuration settings, plus personal tmux config.

The `defaults/` directory contains files generated from a clean tmux server with no user configuration (`tmux -L unconfigured -f /dev/null start-server`), capturing every built-in option and key binding.

## Default Reference Files

| File                     | Contents                                                                        |
| ------------------------ | ------------------------------------------------------------------------------- |
| `all-options.conf`       | Combined server, session, and window options                                    |
| `bindings.conf`          | Default key bindings for all key tables (copy-mode, copy-mode-vi, prefix, root) |
| `colour-options.conf`    | Color-related options                                                           |
| `format-options.conf`    | Format string options (`status-format`, `window-status-format`, etc.)           |
| `global-options.conf`    | Session-level options (`show-options -g`)                                       |
| `separator-options.conf` | Separator options                                                               |
| `server-options.conf`    | Server-level options (`show-options -gs`)                                       |
| `style-options.conf`     | Style-related options                                                           |
| `window-options.conf`    | Window-level options (`show-options -gw`)                                       |

## Installation

Clone the repository:

```bash
git clone https://github.com/cboone/tmux-conf.git
```

## Regenerating Defaults

Each file includes a comment showing the exact tmux command used to generate it. To regenerate:

```bash
# Server options
tmux -L unconfigured -f /dev/null start-server \; show-options -gs

# Session (global) options
tmux -L unconfigured -f /dev/null start-server \; show-options -g

# Window options
tmux -L unconfigured -f /dev/null start-server \; show-options -gw

# Key bindings
tmux -L unconfigured -f /dev/null start-server \; list-keys

# All options combined
tmux -L unconfigured -f /dev/null start-server \; show-options -gs \; show-options -g \; show-options -gw
```

## License

[MIT License](./LICENSE). TL;DR: Do whatever you want with this software, just keep the copyright notice included. The authors aren't liable if something goes wrong.
