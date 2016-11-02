http://aperiodic.net/screen/quick_reference

start a new screen session with session name	screen -S <name>
list running sessions/screens	screen -ls
attach to a running session	screen -x
… to session with name	screen -r <name>
the “ultimate attach”	screen -dRR (Attaches to a screen session. If the session is attached elsewhere, detaches that other display. If no session exists, creates one. If multiple sessions exist, uses the first one.)
detach a running session	screen -d <name>
Edit
Escape key
All screen commands are prefixed by an escape key, by default C-a (that's Control-a, sometimes written ^a). To send a literal C-a to the programs in screen, use C-a a. This is useful when working with screen within screen. For example C-a a n will move screen to a new window on the screen within screen.
Edit
Getting out
detach	C-a d
detach and logout (quick exit)	C-a D D
exit screen	C-a \ Exit all of the programs in screen. (not recommended)
force-exit screen	C-a C-\ (not recommended)
getting out of the screen session	exit
Edit



