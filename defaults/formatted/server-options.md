# Server Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gs`

```tmux
backspace C-?
buffer-limit 50
codepoint-widths
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
```

## Default

```tmux
default-client-command new-session
default-terminal tmux-256color
```

```tmux
escape-time 10
```

## Exit

```tmux
exit-empty on
exit-unattached off
```

## Extended

```tmux
extended-keys off
extended-keys-format xterm
```

```tmux
focus-events off
history-file ''
input-buffer-size 1048576
message-limit 1000
prefix-timeout 0
prompt-history-limit 100
set-clipboard external
```

## Terminal

```tmux
terminal-features[0] xterm*:clipboard:ccolour:cstyle:focus:title
terminal-features[1] screen*:title
terminal-features[2] rxvt*:ignorefkeys
terminal-overrides[0] linux*:AX@
```

```tmux
user-keys
variation-selector-always-wide on
```
