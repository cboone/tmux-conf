# Window Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gw`

```tmux
aggressive-resize off
```

## Allow

```tmux
allow-passthrough off
allow-rename off
allow-set-title on
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
copy-mode-current-match-style bg=magenta,fg=black
copy-mode-mark-style bg=red,fg=black
copy-mode-match-style bg=cyan,fg=black
copy-mode-position-format "#[align=right]#{t/p:top_line_time}#{?#{e|>:#{top_line_time},0}, ,}[#{scroll_position}/#{history_size}]#{?search_timed_out, (timed out),#{?search_count, (#{search_count}#{?search_count_partial,+,} results),}}"
copy-mode-position-style "#{E:mode-style}"
copy-mode-selection-style "#{E:mode-style}"
```

## Cursor

```tmux
cursor-colour none
cursor-style default
```

```tmux
fill-character ''
```

## Main

```tmux
main-pane-height 24
main-pane-width 80
```

## Menu

```tmux
menu-border-lines single
menu-border-style default
menu-selected-style bg=yellow,fg=black
menu-style default
```

## Mode

```tmux
mode-keys emacs
mode-style noattr,bg=yellow,fg=black
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
pane-scrollbars off
pane-scrollbars-position right
pane-scrollbars-style bg=black,fg=white,width=1,pad=0
pane-status-current-style default
pane-status-style default
```

## Popup

```tmux
popup-border-lines single
popup-border-style default
popup-style default
```

## Remain

```tmux
remain-on-exit off
remain-on-exit-format "Pane is dead (#{?#{!=:#{pane_dead_status},},status #{pane_dead_status},}#{?#{!=:#{pane_dead_signal},},signal #{pane_dead_signal},}, #{t:pane_dead_time})"
```

```tmux
scroll-on-clear on
```

## Session

```tmux
session-status-current-style default
session-status-style default
```

```tmux
synchronize-panes off
tiled-layout-max-columns 0
```

## Window

```tmux
window-active-style default
window-size latest
window-status-activity-style reverse
window-status-bell-style reverse
window-status-current-format "#I:#W#{?window_flags,#{window_flags}, }"
window-status-current-style default
window-status-format "#I:#W#{?window_flags,#{window_flags}, }"
window-status-last-style default
window-status-separator " "
window-status-style default
window-style default
```

```tmux
wrap-search on
xterm-keys on
```
