# Style Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -g \; show-options -gw | grep style`

## Message

```tmux
message-command-style bg=black,fg=yellow
message-style bg=yellow,fg=black
```

## Status

```tmux
status-format[0] "#[align=left range=left #{E:status-left-style}]#[push-default]#{T;=/#{status-left-length}:status-left}#[pop-default]#[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{W:#[range=window|#{window_index} #{E:window-status-style}#{?#{&&:#{window_last_flag},#{!=:#{E:window-status-last-style},default}}, #{E:window-status-last-style},}#{?#{&&:#{window_bell_flag},#{!=:#{E:window-status-bell-style},default}}, #{E:window-status-bell-style},#{?#{&&:#{||:#{window_activity_flag},#{window_silence_flag}},#{!=:#{E:window-status-activity-style},default}}, #{E:window-status-activity-style},}}]#[push-default]#{T:window-status-format}#[pop-default]#[norange default]#{?loop_last_flag,,#{window-status-separator}},#[range=window|#{window_index} list=focus #{?#{!=:#{E:window-status-current-style},default},#{E:window-status-current-style},#{E:window-status-style}}#{?#{&&:#{window_last_flag},#{!=:#{E:window-status-last-style},default}}, #{E:window-status-last-style},}#{?#{&&:#{window_bell_flag},#{!=:#{E:window-status-bell-style},default}}, #{E:window-status-bell-style},#{?#{&&:#{||:#{window_activity_flag},#{window_silence_flag}},#{!=:#{E:window-status-activity-style},default}}, #{E:window-status-activity-style},}}]#[push-default]#{T:window-status-current-format}#[pop-default]#[norange list=on default]#{?loop_last_flag,,#{window-status-separator}}}#[nolist align=right range=right #{E:status-right-style}]#[push-default]#{T;=/#{status-right-length}:status-right}#[pop-default]#[norange default]"
status-format[1] "#[align=left]#{R: ,#{n:#{session_name}}}P: #[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{P:#[range=pane|#{pane_id} #{E:pane-status-style}]#[push-default]#P[#{pane_width}x#{pane_height}]#[pop-default]#[norange list=on default]  ,#[range=pane|#{pane_id} list=focus #{?#{!=:#{E:pane-status-current-style},default},#{E:pane-status-current-style},#{E:pane-status-style}}]#[push-default]#P[#{pane_width}x#{pane_height}]*#[pop-default]#[norange list=on default] }"
status-format[2] "#[align=left]#{R: ,#{n:#{session_name}}}S: #[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{S:#[range=session|#{session_id} #{E:session-status-style}]#[push-default]#S#{session_alert}#[pop-default]#[norange list=on default]  ,#[range=session|#{session_id} list=focus #{?#{!=:#{E:session-status-current-style},default},#{E:session-status-current-style},#{E:session-status-style}}]#[push-default]#S*#{session_alert}#[pop-default]#[norange list=on default] }"
status-left-style default
status-right-style default
status-style bg=green,fg=black
```

```tmux
prompt-cursor-style default
cursor-style default
```

## Menu

```tmux
menu-style default
menu-selected-style bg=yellow,fg=black
menu-border-style default
```

## Pane

```tmux
pane-status-current-style default
pane-status-style default
```

## Session

```tmux
session-status-current-style default
session-status-style default
```

```tmux
clock-mode-style 24
```

## Copy

```tmux
copy-mode-match-style bg=cyan,fg=black
copy-mode-current-match-style bg=magenta,fg=black
copy-mode-mark-style bg=red,fg=black
copy-mode-position-style "#{E:mode-style}"
copy-mode-selection-style "#{E:mode-style}"
```

```tmux
mode-style noattr,bg=yellow,fg=black
```

## Pane

```tmux
pane-active-border-style "#{?pane_in_mode,fg=yellow,#{?synchronize-panes,fg=red,fg=green}}"
pane-border-style default
pane-scrollbars-style bg=black,fg=white,width=1,pad=0
```

## Popup

```tmux
popup-style default
popup-border-style default
```

## Window

```tmux
window-active-style default
window-style default
window-status-activity-style reverse
window-status-bell-style reverse
window-status-current-style default
window-status-last-style default
window-status-style default
```
