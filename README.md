# FaTTY-Legacy (community fork)

A maintained fork of [FaTTY](https://github.com/juho-p/fatty), the Cygwin terminal emulator with tabs. Upstream has been dormant since 2021 and archived in 2024; this fork keeps it buildable with current toolchains and backports features that upstream mintty gained since, in small, reviewable pieces.

Changes stay close to upstream sources so future merges remain possible. See [CHANGELOG.md](CHANGELOG.md) for what changed in each version.

The code base is kept as of FaTTY 1.6.0 (mintty 2.0.2). Changes are limited to cherry-picked mintty upstream changes and a few additions for personal use, so it is opinionated rather than a release-for-release match with mintty.

For a fork that keeps pace with the latest mintty source, see [paolo-sz/fatty](https://github.com/paolo-sz/fatty).

The rest of this file is the original upstream README, kept for reference.

---

FaTTY
-----

![FaTTY](http://i.imgur.com/ZMpvcNH.png)

FaTTY is the [Cygwin](http://cygwin.com) Terminal emulator with tabs. It is
useful for Windows and Cygwin users who want powerful terminal.

FaTTY is based on [mintty](https://github.com/mintty/mintty). The main
difference to mintty is that you can run multiple session in single window
using tabs.

* Most features from mintty should work
* To create new tab, press ctrl-shift-T
* ctrl-shift-W closes the tab
* To change active tab, click it with mouse or press shift-(left arrow|right arrow)
* To move tab, press ctrl-shift-(arrow direction)

If you find bugs (there are probably many), you may report them on Github or
send pull requests

### Installing

To install, run cygwin setup\*.exe and have at least following packages marked for
install:

* gcc-g++
* make
* w32api-headers
* git

Then, in Cygwin terminal run following commands:

    git clone https://github.com/juho-p/fatty.git
    cd fatty
    make
    cp src/fatty.exe /bin
  
You can then try running it by typing `fatty`
  
Then you probably want to create shortcut to your Windows desktop to run fatty.
After that, you have decent terminal with tabs for your Cygwin!

To spawn a new tab, for example in a desktop shortcut, use `fatty -b "source $HOME/.bashrc; uname -a; exec bash"`.
You can spawn multiple tabs by providing `-b` option multiple times
(`fatty -b "commands for tab 1" -b "commands for tab 2" ...`). Always
execute bash (or other shell of your choice).

You might also want to remove the line `cd "${HOME}"` from `/etc/profile` (if
there are such line) if you want your new tabs to open same directory as your
current tab.
