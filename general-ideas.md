# General Ideas

## Base Principles

want to be able to rebuild from nothing.

-   build kernal and minimum amount of functionality to run script
-   use as base for other installs script that installs remainder of core tools
-   primarily suckless tools, staticlly compiled binaries

further scripts to customize for each individual system

look at using modified version of
[terrorshell](http://www.github.com/sww1235/terrorshell) for bashrc etc.

use a set of statically linked basic tools

## Base OS

look at [tiny core linux](http://tinycorelinux.net/concepts.html),
[ttylinux](http://freecode.com/projects/ttylinux/) or
[Linux From Scratch (LFS)](http://www.linuxfromscratch.org/lfs/view/stable/index.html)
for base OS.

### LFS specific ideas

if using LFS for base OS, then install the build environment (Ubuntu Server) on
a USB stick and and only update if absolutely necessary.

Boot off of USB on build machine either with a blank drive connected or mount a
network volume on which to build the lfs system.

look at [sinit/runit](https://github.com/inthecloud247/runit-for-lfs) for init script stuff
