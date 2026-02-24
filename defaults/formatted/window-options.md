# Window Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gw`

## Cursor

```tmux
cursor-colour none
cursor-style default
```

## Menu

```tmux
menu-style default
menu-selected-style bg=yellow,fg=black
menu-border-style default
menu-border-lines single
```

```tmux
aggressive-resize off
```

## Allow

```tmux
allow-passthrough off
allow-rename off
```

```tmux
alternate-screen on
```

## Automatic

```tmux
automatic-rename on
automatic-rename-format "#{?pane_in_mode,[tmux],#{pane_current_command}}#{?pane_dead,[dead],}"
```

## Clock

```tmux
clock-mode-colour blue
clock-mode-style 24
```

## Copy

```tmux
copy-mode-match-style bg=cyan,fg=black
copy-mode-current-match-style bg=magenta,fg=black
copy-mode-mark-style bg=red,fg=black
```

```tmux
fill-character ''
```

## Main

```tmux
main-pane-height 24
main-pane-width 80
```

## Mode

```tmux
mode-keys emacs
mode-style bg=yellow,fg=black
```

## Monitor

```tmux
monitor-activity off
monitor-bell on
monitor-silence 0
```

## Other

```tmux
other-pane-height 0
other-pane-width 0
```

## Pane

```tmux
pane-active-border-style "#{?pane_in_mode,fg=yellow,#{?synchronize-panes,fg=red,fg=green}}"
pane-base-index 0
pane-border-format "#{?pane_active,#[reverse],}#{pane_index}#[default] \"#{pane_title}\""
pane-border-indicators colour
pane-border-lines single
pane-border-status off
pane-border-style default
pane-colours
```

## Popup

```tmux
popup-style default
popup-border-style default
popup-border-lines single
```

## Remain

```tmux
remain-on-exit off
remain-on-exit-format "Pane is dead (#{?#{!=:#{pane_dead_status},},status #{pane_dead_status},}#{?#{!=:#{pane_dead_signal},},signal #{pane_dead_signal},}, #{t:pane_dead_time})"
```

```tmux
scroll-on-clear on
synchronize-panes off
```

## Window

```tmux
window-active-style default
window-size latest
window-style default
window-status-activity-style reverse
window-status-bell-style reverse
window-status-current-format "#I:#W#{?window_flags,#{window_flags}, }"
window-status-current-style default
window-status-format "#I:#W#{?window_flags,#{window_flags}, }"
window-status-last-style default
window-status-separator " "
window-status-style default
```

```tmux
wrap-search on
xterm-keys on
```
