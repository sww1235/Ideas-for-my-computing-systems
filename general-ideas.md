# General Ideas

## Base Principles

want to be able to rebuild from nothing.

-   build kernal and minimum amount of functionality to run script
-   use as base for other installs script that installs remainder of core tools
-   primarily suckless tools, staticlly compiled binaries

~~Have basic clonable image on USB flashdrive using kernal w/ generic drivers +
networking + ssh + bash~~

~~Recompile kernal on each machine once image is cloned based on hardware to
slim down kernal~~

Use powerful build machine to compile/crosscompile custom linux kernels and
other necessary software for each architecture/machine. This machine will start
out using a prebuilt distro and potentially change to a custom image later.

PXE boot(potentially have syslinux in chain somewhere) each machine that needs
to image with very slim image. Then a script will prep the filesystem on the
local disk, partioning, bootloader, etc, then copy necessary files from mounted
nfs share.

further scripts to customize for each individual system

look at using modified version of
[terrorshell](http://www.github.com/sww1235/terrorshell) for bashrc etc.

look at [dotbot](https://github.com/anishathalye/dotbot)

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

look at [sinit/runit](https://github.com/inthecloud247/runit-for-lfs) for init
script stuff

#### Notes about LFS

LFS is built using an established linux based host system.

All LFS specific work takes place on a separate mounted partition which is
mounted at $LFS. This partition will have a file system created on it.

$LFS will be the / of your new LFS based system. Most steps in LFS are done
using chroot so that commands you run see $LFS as / .

## syslinux ideas

See [potential pxelinux config file](../pxelinux.cfg) for actual potential
config. what is listed below are just ideas.

-   Hard drive testing tools

    -   Western Digital Tools (WD Tools)
    -   Seagate Tools (Sea Tools)
    -   Hitachi
    -   Parted Magic

-   Password Reset Tool

-   Memtest86+

-   DBAN

-   BIOS Flashing

-   DOS Command Line

-   Hiren's Boot CD

-   Quick Wipe
