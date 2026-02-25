# Session Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -g`

```tmux
activity-action other
assume-paste-time 1
base-index 0
bell-action any
```

## Default

```tmux
default-command ''
# default-shell $SHELL
default-size 80x24
```

```tmux
destroy-unattached off
detach-on-destroy on
```

## Display

```tmux
display-panes-active-colour red
display-panes-colour blue
display-panes-time 1000
display-time 750
```

```tmux
history-limit 2000
initial-repeat-time 0
key-table root
```

## Lock

```tmux
lock-after-time 0
lock-command "lock -np"
```

## Message

```tmux
message-command-style bg=black,fg=yellow
message-line 0
message-style bg=yellow,fg=black
```

```tmux
mouse off
prefix C-b
prefix2 None
renumber-windows off
repeat-time 500
```

## Set

```tmux
set-titles off
set-titles-string "#S:#I:#W - \"#T\" #{session_alerts}"
```

```tmux
silence-action other
```

## Status

```tmux
status on
status-bg default
status-fg default
status-format[0] "#[align=left range=left #{E:status-left-style}]#[push-default]#{T;=/#{status-left-length}:status-left}#[pop-default]#[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{W:#[range=window|#{window_index} #{E:window-status-style}#{?#{&&:#{window_last_flag},#{!=:#{E:window-status-last-style},default}}, #{E:window-status-last-style},}#{?#{&&:#{window_bell_flag},#{!=:#{E:window-status-bell-style},default}}, #{E:window-status-bell-style},#{?#{&&:#{||:#{window_activity_flag},#{window_silence_flag}},#{!=:#{E:window-status-activity-style},default}}, #{E:window-status-activity-style},}}]#[push-default]#{T:window-status-format}#[pop-default]#[norange default]#{?loop_last_flag,,#{window-status-separator}},#[range=window|#{window_index} list=focus #{?#{!=:#{E:window-status-current-style},default},#{E:window-status-current-style},#{E:window-status-style}}#{?#{&&:#{window_last_flag},#{!=:#{E:window-status-last-style},default}}, #{E:window-status-last-style},}#{?#{&&:#{window_bell_flag},#{!=:#{E:window-status-bell-style},default}}, #{E:window-status-bell-style},#{?#{&&:#{||:#{window_activity_flag},#{window_silence_flag}},#{!=:#{E:window-status-activity-style},default}}, #{E:window-status-activity-style},}}]#[push-default]#{T:window-status-current-format}#[pop-default]#[norange list=on default]#{?loop_last_flag,,#{window-status-separator}}}#[nolist align=right range=right #{E:status-right-style}]#[push-default]#{T;=/#{status-right-length}:status-right}#[pop-default]#[norange default]"
status-format[1] "#[align=left]#{R: ,#{n:#{session_name}}}P: #[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{P:#[range=pane|#{pane_id} #{E:pane-status-style}]#[push-default]#P[#{pane_width}x#{pane_height}]#[pop-default]#[norange list=on default]  ,#[range=pane|#{pane_id} list=focus #{?#{!=:#{E:pane-status-current-style},default},#{E:pane-status-current-style},#{E:pane-status-style}}]#[push-default]#P[#{pane_width}x#{pane_height}]*#[pop-default]#[norange list=on default] }"
status-format[2] "#[align=left]#{R: ,#{n:#{session_name}}}S: #[norange default]#[list=on align=#{status-justify}]#[list=left-marker]<#[list=right-marker]>#[list=on]#{S:#[range=session|#{session_id} #{E:session-status-style}]#[push-default]#S#{session_alert}#[pop-default]#[norange list=on default]  ,#[range=session|#{session_id} list=focus #{?#{!=:#{E:session-status-current-style},default},#{E:session-status-current-style},#{E:session-status-style}}]#[push-default]#S*#{session_alert}#[pop-default]#[norange list=on default] }"
status-interval 15
status-justify left
status-keys emacs
status-left "[#{session_name}] "
status-left-length 10
status-left-style default
status-position bottom
status-right "#{?window_bigger,[#{window_offset_x}#,#{window_offset_y}] ,}\"#{=21:pane_title}\" %H:%M %d-%b-%y"
status-right-length 40
status-right-style default
status-style bg=green,fg=black
```

## Prompt

```tmux
prompt-cursor-colour cyan
prompt-cursor-style default
```

## Update

```tmux
update-environment[0] DISPLAY
update-environment[1] KRB5CCNAME
update-environment[2] MSYSTEM
update-environment[3] SSH_ASKPASS
update-environment[4] SSH_AUTH_SOCK
update-environment[5] SSH_AGENT_PID
update-environment[6] SSH_CONNECTION
update-environment[7] WINDOWID
update-environment[8] XAUTHORITY
```

## Visual

```tmux
visual-activity off
visual-bell off
visual-silence off
```

```tmux
word-separators "!\"#$%&'()*+,-./:;<=>?@[\\]^`{|}~"
```
