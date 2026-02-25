# All Options

> `tmux -L unconfigured -f /dev/null start-server \; show-options -gs \; show-options -g \; show-options -gw`

## Server Options (`show-options -gs`)

```tmux
backspace C-?
buffer-limit 50
```

### Command

```tmux
command-alias[0] split-pane=split-window
command-alias[1] splitp=split-window
command-alias[2] "server-info=show-messages -JT"
command-alias[3] "info=show-messages -JT"
command-alias[4] "choose-window=choose-tree -w"
command-alias[5] "choose-session=choose-tree -s"
```

```tmux
codepoint-widths
copy-command ''
```

### Default

```tmux
default-client-command new-session
default-terminal tmux-256color
```

```tmux
editor mg
escape-time 10
```

### Exit

```tmux
exit-empty on
exit-unattached off
```

### Extended

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

### Terminal

```tmux
terminal-overrides[0] linux*:AX@
terminal-features[0] xterm*:clipboard:ccolour:cstyle:focus:title
terminal-features[1] screen*:title
terminal-features[2] rxvt*:ignorefkeys
```

```tmux
user-keys
variation-selector-always-wide on
```

## Session Options (`show-options -g`)

```tmux
activity-action other
assume-paste-time 1
base-index 0
bell-action any
```

### Default

```tmux
default-command ''
default-shell /bin/zsh
default-size 80x24
```

```tmux
destroy-unattached off
detach-on-destroy on
```

### Display

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

### Lock

```tmux
lock-after-time 0
lock-command "lock -np"
```

### Message

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

### Set

```tmux
set-titles off
set-titles-string "#S:#I:#W - \"#T\" #{session_alerts}"
```

```tmux
silence-action other
```

### Status

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

### Prompt

```tmux
prompt-cursor-colour cyan
prompt-cursor-style default
```

### Update

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

### Visual

```tmux
visual-activity off
visual-bell off
visual-silence off
```

```tmux
word-separators "!\"#$%&'()*+,-./:;<=>?@[\\]^`{|}~"
```

## Window Options (`show-options -gw`)

### Cursor

```tmux
cursor-colour none
cursor-style default
```

### Menu

```tmux
menu-style default
menu-selected-style bg=yellow,fg=black
menu-border-style default
menu-border-lines single
```

### Pane

```tmux
pane-status-current-style default
pane-status-style default
```

### Session

```tmux
session-status-current-style default
session-status-style default
```

```tmux
aggressive-resize off
```

### Allow

```tmux
allow-passthrough off
allow-rename off
allow-set-title on
```

```tmux
alternate-screen on
```

### Automatic

```tmux
automatic-rename on
automatic-rename-format "#{?pane_in_mode,[tmux],#{pane_current_command}}#{?pane_dead,[dead],}"
```

### Clock

```tmux
clock-mode-colour blue
clock-mode-style 24
```

### Copy

```tmux
copy-mode-match-style bg=cyan,fg=black
copy-mode-current-match-style bg=magenta,fg=black
copy-mode-mark-style bg=red,fg=black
copy-mode-position-format "#[align=right]#{t/p:top_line_time}#{?#{e|>:#{top_line_time},0}, ,}[#{scroll_position}/#{history_size}]#{?search_timed_out, (timed out),#{?search_count, (#{search_count}#{?search_count_partial,+,} results),}}"
copy-mode-position-style "#{E:mode-style}"
copy-mode-selection-style "#{E:mode-style}"
```

```tmux
fill-character ''
```

### Main

```tmux
main-pane-height 24
main-pane-width 80
```

### Mode

```tmux
mode-keys emacs
mode-style noattr,bg=yellow,fg=black
```

### Monitor

```tmux
monitor-activity off
monitor-bell on
monitor-silence 0
```

### Other

```tmux
other-pane-height 0
other-pane-width 0
```

### Pane

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
pane-scrollbars-style bg=black,fg=white,width=1,pad=0
pane-scrollbars-position right
```

### Popup

```tmux
popup-style default
popup-border-style default
popup-border-lines single
```

### Remain

```tmux
remain-on-exit off
remain-on-exit-format "Pane is dead (#{?#{!=:#{pane_dead_status},},status #{pane_dead_status},}#{?#{!=:#{pane_dead_signal},},signal #{pane_dead_signal},}, #{t:pane_dead_time})"
```

```tmux
scroll-on-clear on
synchronize-panes off
tiled-layout-max-columns 0
```

### Window

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
