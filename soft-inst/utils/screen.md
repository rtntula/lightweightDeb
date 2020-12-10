# Screen

> [`<`](../index.md)

## Basic commands

- create a named screen session

```
$ screen -S session.one
```

- detach the session: C-a d
- list sessions

```
$ screen -ls
There are screens on:
  2581.session.one        (12/09/2020 10:48:19 PM)        (Detached)
```

> The 2581 part here is the session's PID.

- reattach a session

```
$ screen -r 2581
```

To identify a session to reattach you need to specify an unambiguous part of its name or its pid or if there's only one session -- just use `-r` option and hit Enter.

- get rid of a sesison

```
$ screen -X -S 2581 quit
```



- scroll the content of a split window: C-a Esc and use arrows or h,j,k,l. Hit Esc to exit this mode.
