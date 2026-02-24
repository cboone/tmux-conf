# Server Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gs`

```tmux
backspace C-?
buffer-limit 50
```

## Command

```tmux
command-alias[0] split-pane=split-window
command-alias[1] splitp=split-window
command-alias[2] "server-info=show-messages -JT"
command-alias[3] "info=show-messages -JT"
command-alias[4] "choose-window=choose-tree -w"
command-alias[5] "choose-session=choose-tree -s"
```

```tmux
copy-command ''
default-terminal tmux-256color
editor /usr/bin/vi
escape-time 500
```

## Exit

```tmux
exit-empty on
exit-unattached off
```

```tmux
extended-keys off
focus-events off
history-file ''
message-limit 1000
prompt-history-limit 100
set-clipboard external
```

## Terminal

```tmux
terminal-overrides
terminal-features[0] xterm*:clipboard:ccolour:cstyle:focus:title
terminal-features[1] screen*:title
terminal-features[2] rxvt*:ignorefkeys
```

```tmux
user-keys
```
