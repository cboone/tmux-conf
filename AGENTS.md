# Tmux Conf

## Overview

tmux default and personal config. The `defaults/` directory contains reference files generated from an unconfigured tmux server. Each file includes a comment with the command used to produce it.

## Structure

- `defaults/` - tmux built-in options and key bindings (`.conf` files)

## Development

Regenerate any defaults file by running the tmux command in its header comment. The general pattern is:

```bash
tmux -L unconfigured -f /dev/null start-server \; <show-command>
```
