# Screen

<http://aperiodic.net/screen/quick_reference>

## Escape key

All screen commands are prefixed by an escape key, by default `C-a` (that's `Control-a`, sometimes written `^a`).
To send a literal `C-a` to the programs in screen, use `C-a a`.
This is useful when working with screen within screen.
For example `C-a a n` will move screen to a new window on the screen within screen.

## Start a new screen session with session name

```bash
screen -S <name>
```

## List running
```bash
sessions/screens	screen -ls
```

## Attach to a running session

```bash
screen -x
```

## Attach to session with name

```bash
screen -r <name>
```

## The “ultimate attach”

(Attaches to a screen session. If the session is attached elsewhere, detaches that other display. If no session exists, creates one. If multiple sessions exist, uses the first one.)

```bash
screen -dRR
```

## Detach a running session

```bash
screen -d <name>
```

## Getting out

```bash
detach C-a d
```

* detach and logout (quick exit) `C-a D D`
* exit screen	`C-a \` Exit all of the programs in screen. (not recommended)
* force-exit screen	`C-a C-\` (not recommended)
* getting out of the screen session	`exit`




