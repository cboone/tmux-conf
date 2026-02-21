# Tmux Conf

## Overview

tmux default and personal config. The `defaults/` directory contains reference files showing tmux's built-in options, generated using an unconfigured tmux server (`tmux -L unconfigured -f /dev/null start-server`).

## Structure

- `defaults/` - Reference documentation of tmux default settings:
  - `all-options.conf` - Combined server, session, and window options
  - `bindings.conf` - Default key bindings for all key tables (copy-mode, copy-mode-vi, prefix, root)
  - `colour-options.conf` - Color-related options
  - `format-options.conf` - Format string options (status-format, window-status-format, etc.)
  - `global-options.conf` - Session-level options (`show-options -g`)
  - `separator-options.conf` - Separator options
  - `server-options.conf` - Server-level options (`show-options -gs`)
  - `style-options.conf` - Style-related options
  - `window-options.conf` - Window-level options (`show-options -gw`)

## Development

### Regenerating Default Options

Each file includes a comment showing the tmux command used to generate it. To regenerate:

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
