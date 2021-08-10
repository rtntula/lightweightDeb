# Screen

> [`<<`](../index.md)  
> [Источник: Linux Leech](www.youtube.com/watch?v=I4xVn6Io5Nw)

The app allows to keep processes running on a remote server even after closing up a ssh connection to it.

## Basic commands

### create a named screen session

```
$ screen -S session.one
```

### detach a session

- C-a d

### list sessions

```
$ screen -ls
There are screens on:
  2581.session.one        (12/09/2020 10:48:19 PM)        (Detached)
```

> The 2581 part here is the session's PID.

### reattach a session

```
$ screen -r 2581
```

To identify a session to reattach you need to specify an unambiguous part of its name or its pid or if there's only one session -- just use `-r` option and hit Enter.

### get rid of a sesison

```
$ screen -X -S 2581 quit
```

  - `-X` -- send a session a command (`quit`)
  - `-S` -- id-y a session by name (2581)

### create a window within a session

- C-a c

### rename the current window

- C-a A

### list windows

- C-a w

> As all windows are numbered we can get to a win by its number.

- C-a 2 -- to get to win no 2.
- C-a " -- to make a selectable win list

### move btw windows

- C-a n/p


### kill a window within a session

- C-a k

> If there's only one window within a session that session will be terminated as well.

- C-a \ -- to kill all the windows and end a session.

### splitting windows in panes

- C-a | -- to split vertically
- C-a S -- to split horizontally

> We should then go that new pane and open a window there.
- C-a X -- to kill a pane, but not a window

> After detachind a session and then reattaching it all the panes disappear, but the windows are still there.

### move btw panes

- C-a tab

### resizing panes

- C-a :resize -h 30 -- make the curr win 30 char wide
- C-a :resize -h 30% -- the same in percents
- C-a :resize -v 60% -- make the curr win to take 60% of the split height

### scroll the content of a split window

- C-a Esc and use arrows or h,j,k,l. Hit Esc to exit this mode.

### display help

- C-a ? -- to see key bindings

### alt way to control

- C-a :command
