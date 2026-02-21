# Style Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -g \; show-options -gw | grep style`

```tmux
clock-mode-style 24
```

## Copy

```tmux
copy-mode-current-match-style bg=magenta,fg=black
copy-mode-mark-style bg=red,fg=black
copy-mode-match-style bg=cyan,fg=black
copy-mode-position-style "#{E:mode-style}"
copy-mode-selection-style "#{E:mode-style}"
```

```tmux
cursor-style default
```

## Menu

```tmux
menu-border-style default
menu-selected-style bg=yellow,fg=black
menu-style default
```

## Message

```tmux
message-command-style bg=black,fg=yellow
message-style bg=yellow,fg=black
```

```tmux
mode-style noattr,bg=yellow,fg=black
```

## Pane

```tmux
pane-active-border-style "#{?pane_in_mode,fg=yellow,#{?synchronize-panes,fg=red,fg=green}}"
pane-border-style default
pane-scrollbars-style bg=black,fg=white,width=1,pad=0
pane-status-current-style default
pane-status-style default
```

## Popup

```tmux
popup-border-style default
popup-style default
```

```tmux
prompt-cursor-style default
```

## Session

```tmux
session-status-current-style default
session-status-style default
```

## Status

```tmux
status-left-style default
status-right-style default
status-style bg=green,fg=black
```

## Window

```tmux
window-active-style default
window-status-activity-style reverse
window-status-bell-style reverse
window-status-current-style default
window-status-last-style default
window-status-style default
window-style default
```
