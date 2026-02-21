# Tmux Conf

## Overview

tmux default and personal config. The `defaults/` directory contains reference files generated from an unconfigured tmux server. Each file includes a comment with the command used to produce it.

## Structure

- `bin/` - scripts for maintaining the repository
- `defaults/` - tmux built-in options and key bindings (`.conf` files)

## Development

Regenerate all defaults files by running `./bin/update-defaults`. The script reads the tmux command from each file's header comment and rewrites the file with fresh output.
