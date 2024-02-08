# ATTENTION

This is a slight modification of an opensource software originally downloaded from: [http://www.users.uswest.net/~hmahon/](http://www.users.uswest.net/~hmahon/).
the original uploader of this repo and I are NOT the original authors of this software! Please read the `README.aee` file for further information.

The version I've downloaded is 2.2.21.

Some screenshots:

![aee in Konsole](https://github.com/anoraktrend/aee/blob/master/.imgs.d/aee%20with%20better%20font.png?raw=true)

![aee with it's menu open](https://github.com/anoraktrend/aee/blob/master/.imgs.d/aee%20menu.png?raw=true)

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
