# Key Binding Notes

> `tmux -L unconfigured -f /dev/null start-server \; list-keys -N`

```tmux
C-b !       Break pane to a new window
```

## Choose

```tmux
C-b =       Choose a paste buffer from a list
C-b D       Choose and detach a client from a list
C-b s       Choose a session from a list
C-b w       Choose a window from a list
```

```tmux
C-b M       Clear the marked pane
C-b c       Create a new window
C-b C       Customize options
C-b -       Delete the most recent paste buffer
C-b /       Describe key binding
C-b d       Detach the current client
```

## Display

```tmux
C-b <       Display window menu
C-b >       Display pane menu
C-b i       Display window information
C-b q       Display pane numbers
```

## Enter

```tmux
C-b [       Enter copy mode
C-b PPage   Enter copy mode and scroll up
```

## Kill

```tmux
C-b &       Kill current window
C-b x       Kill the active pane
```

## List

```tmux
C-b #       List all paste buffers
C-b ?       List key bindings
```

## Move

```tmux
C-b .       Move the current window
C-b ;       Move to the previously active pane
C-b S-Up    Move the visible part of the window up
C-b S-Down  Move the visible part of the window down
C-b S-Left  Move the visible part of the window left
C-b S-Right Move the visible part of the window right
```

```tmux
C-b ]       Paste the most recent paste buffer
```

## Prompt

```tmux
C-b '       Prompt for window index to select
C-b :       Prompt for a command
```

```tmux
C-b r       Redraw the current client
```

## Rename

```tmux
C-b $       Rename current session
C-b ,       Rename current window
```

```tmux
C-b DC      Reset so the visible part of the window follows the cursor
```

## Resize

```tmux
C-b M-Up    Resize the pane up by 5
C-b M-Down  Resize the pane down by 5
C-b M-Left  Resize the pane left by 5
C-b M-Right Resize the pane right by 5
C-b C-Up    Resize the pane up
C-b C-Down  Resize the pane down
C-b C-Left  Resize the pane left
C-b C-Right Resize the pane right
```

## Rotate

```tmux
C-b M-o     Rotate through the panes in reverse
C-b C-o     Rotate through the panes
```

```tmux
C-b f       Search for a pane
```

## Select

```tmux
C-b Space   Select next layout
C-b 0       Select window 0
C-b 1       Select window 1
C-b 2       Select window 2
C-b 3       Select window 3
C-b 4       Select window 4
C-b 5       Select window 5
C-b 6       Select window 6
C-b 7       Select window 7
C-b 8       Select window 8
C-b 9       Select window 9
C-b l       Select the previously current window
C-b n       Select the next window
C-b o       Select the next pane
C-b p       Select the previous window
C-b Up      Select the pane above the active pane
C-b Down    Select the pane below the active pane
C-b Left    Select the pane to the left of the active pane
C-b Right   Select the pane to the right of the active pane
C-b M-5     Select the tiled layout
C-b M-n     Select the next window with an alert
C-b M-p     Select the previous window with an alert
```

```tmux
C-b C-b     Send the prefix key
```

## Set

```tmux
C-b M-1     Set the even-horizontal layout
C-b M-2     Set the even-vertical layout
C-b M-3     Set the main-horizontal layout
C-b M-4     Set the main-vertical layout
C-b M-6     Set the main-horizontal-mirrored layout
C-b M-7     Set the main-vertical-mirrored layout
```

## Show

```tmux
C-b t       Show a clock
C-b ~       Show messages
```

## Split

```tmux
C-b "       Split window vertically
C-b %       Split window horizontally
```

```tmux
C-b E       Spread panes out evenly
C-b C-z     Suspend the current client
```

## Swap

```tmux
C-b {       Swap the active pane with the pane above
C-b }       Swap the active pane with the pane below
```

## Switch

```tmux
C-b (       Switch to previous client
C-b )       Switch to next client
C-b L       Switch to the last client
```

```tmux
C-b m       Toggle the marked pane
C-b z       Zoom the active pane
```
