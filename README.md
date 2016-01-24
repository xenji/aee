# ATTENTION

This is just a personal backup of an opensource software originally downloaded from: [http://www.users.uswest.net/~hmahon/](http://www.users.uswest.net/~hmahon/).
I am NOT the author of this software! Please read the `README.aee` file for further information.

The version I've downloaded is 2.2.21.

# Important info for OSX users:

The detection of the terminfo directory in the make file creation seems to be broken (although the code looks totally correct from my naive point of view).

If you use iTerm2 with xterm-256colors and the aee borders and decorations (ncurses) look like crap, go into the file `create.mk.aee` and change the if/else detection of the terminfo from this:

```bash
# test for terminfo directory (exists on SysV systems)

if [ -d /usr/lib/terminfo -o -d /usr/share/lib/terminfo -o -d /usr/share/terminfo ]
then
	terminfo_exists=""
else
	terminfo_exists="-DCAP"
fi
```

to this:

```bash
# test for terminfo directory (exists on SysV systems)

if [ -d /usr/lib/terminfo -o -d /usr/share/lib/terminfo -o -d /usr/share/terminfo ]
then
	#terminfo_exists=""
else
	#terminfo_exists="-DCAP"
fi

terminfo_exists="-DCAP"
```

Then recompile and take a look. It should now draw a correct border style.
