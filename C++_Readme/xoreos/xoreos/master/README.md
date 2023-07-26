xoreos README
=============

xoreos is an open source implementation of BioWare's Aurora engine and its
derivatives, licensed under the terms of the [GNU General Public License
version 3](https://www.gnu.org/licenses/gpl.html) (or later). The goal is
to have all games using this engines working in a portable manner, starting
from Neverwinter Nights and ending with Dragon Age II.


Games
-----

The following games are valid targets for xoreos:

- [Neverwinter Nights](https://en.wikipedia.org/wiki/Neverwinter_Nights)
- [Neverwinter Nights 2](https://en.wikipedia.org/wiki/Neverwinter_Nights_2)
- [Knights of the Old Republic](https://en.wikipedia.org/wiki/Star_Wars:_Knights_of_the_Old_Republic)
- [Knights of the Old Republic II: The Sith Lords](https://en.wikipedia.org/wiki/Star_Wars:_Knights_of_the_Old_Republic_II_The_Sith_Lords)
- [Jade Empire](https://en.wikipedia.org/wiki/Jade_Empire)
- [Sonic Chronicles: The Dark Brotherhood](https://en.wikipedia.org/wiki/Sonic_Chronicles:_The_Dark_Brotherhood)
- [The Witcher](https://en.wikipedia.org/wiki/The_Witcher_%28video_game%29)
- [Dragon Age: Origins](https://en.wikipedia.org/wiki/Dragon_Age:_Origins)
- [Dragon Age II](https://en.wikipedia.org/wiki/Dragon_Age_II)


Status
------

Currently, the "foundation" work of managing resources, reading many basic
file formats, displaying graphics and playing sounds has been done. All
targeted games show partial ingame graphics, such as the area geometry and
objects, letting you fly around in a "spectator mode". Some games show partial
menus, and something resembling a starting point for a script system is there.

No actual "normal" gameplay is implemented yet, though.

For further information about the status of specific games, please visit
[our wiki](https://wiki.xoreos.org/index.php?title=Games).

Note: We are always looking for people to join our efforts in reimplementing
those games. If you'd like to help, feel free to contact us!
Please also read over our [CONTRIBUTING.md](CONTRIBUTING.md) for some
guidelines. Thanks.


CI Status
---------

- [![Build status (linux autotools gcc)](https://github.com/xoreos/xoreos/actions/workflows/linux_autotools_gcc.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/linux_autotools_gcc.yml/)
- [![Build status (linux autotools clang)](https://github.com/xoreos/xoreos/actions/workflows/linux_autotools_clang.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/linux_autotools_clang.yml/)
- [![Build status (linux cmake gcc)](https://github.com/xoreos/xoreos/actions/workflows/linux_cmake_gcc.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/linux_cmake_gcc.yml/)
- [![Build status (linux cmake clang)](https://github.com/xoreos/xoreos/actions/workflows/linux_cmake_clang.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/linux_cmake_clang.yml/)
- [![Build status (macos autotools clang)](https://github.com/xoreos/xoreos/actions/workflows/macos_autotools_clang.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/macos_autotools_clang.yml/)
- [![Build status (macos cmake clang)](https://github.com/xoreos/xoreos/actions/workflows/macos_cmake_clang.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/macos_cmake_clang.yml/)
- [![Build status (windows cmake msvc)](https://github.com/xoreos/xoreos/actions/workflows/windows_cmake_msvc.yml/badge.svg)](https://github.com/xoreos/xoreos/actions/workflows/windows_cmake_msvc.yml/)
- [![Coverity Status](https://scan.coverity.com/projects/544/badge.svg)](https://scan.coverity.com/projects/544)


Getting xoreos
--------------

You can get xoreos in multiple ways:

You can download an archive with a binary of the latest release from our
[downloads page](https://xoreos.org/downloads/index.html). This includes
binaries for Microsoft Windows, Mac OS X and GNU/Linux, as well as packages
for various GNU/Linux distributions. All of them are available for both 32-
and 64-bit x86 architectures.

Or, if you're running Arch Linux, you can install xoreos directly from the
[AUR](https://aur.archlinux.org/packages/xoreos/).

Or, if you're running Gentoo Linux, you can install xoreos directly from our
[overlay](https://github.com/xoreos/gentoo-overlay).

Lastly, you can compile xoreos yourself; either from a release source package,
found on our [downloads page](https://xoreos.org/downloads/index.html), or a
fresh [repository](https://github.com/xoreos/xoreos) checkout. For details
on how to compile xoreos on various operating system, please read the
[Compiling xoreos](https://wiki.xoreos.org/index.php?title=Compiling_xoreos)
page on our wiki.


Running xoreos
--------------

First, you need to fully install and/or copy the game you want to play with
xoreos onto your hard disk. How you do this depends on the game, your operating
system and where/how you have bought the game.

xoreos does not yet have a launcher GUI or anything like this. You need to
start it from the command line. Run xoreos with the command line option
"--help" (without the quotes) to get a help text about further command line
options.

The quickest way to start a game in path /path/to/game/ would be to call

    xoreos -p/path/to/game/

If you're on Windows and the path is, say, D:\\Path\\To\\Game\\, call

    xoreos -pD:\\Path\\To\\Game\\

For a more in-depth documentation on how to run xoreos, please also read the
[Running xoreos](https://wiki.xoreos.org/index.php?title=Running_xoreos)
page on our wiki.


Config file
-----------

In general, xoreos can read the configuration which game to run from either
the command line, a config file or both. Additionally, when you first specify
a new game on the command line, xoreos will add a related entry in the config
file (creating it first, if necessary).

To accurately identify a specific instance of an installed game, xoreos uses the
concept of a "target". Each target has a separate section in the config file,
and each of their options apply only to that target. The special target
"xoreos" is a global section applying to all games, although the same option
in a game target overrides the global option.

For example:

```ini
[xoreos]
width=1024
height=768
fullscreen=false

[nwn]
path=/home/drmccoy/games/nwn/
fullscreen=true
volume_music=0.500000
volume_sfx=0.850000
volume_voice=0.850000
```

You can then start the game with the target "nwn" with

    xoreos nwn

and xoreos will do the rest. This will start the game in the path
/home/drmccoy/games/nwn/, running it in fullscreen at 1024x768.

As you can see with the volume options, xoreos also saves settings you made in
the game' actual GUI into the target's section of the config file.

The place where xoreos expects the config file depends on your operating system:

- On GNU/Linux, the place is $XDG\_CONFIG\_HOME/xoreos/xoreos.conf.
  $XDG\_CONFIG\_HOME defaults to $HOME/.config/
- On Mac OS X, the place is $HOME/Library/Preferences/xoreos/xoreos.conf
- On Windows, xoreos.conf is in the subdirectory xoreos in either $APPDATA
  or $USERPROFILE, depending on your Windows version

For a more elaborate example with more in-depth explanations, please see
[xoreos.conf.example](doc/xoreos.conf.example) in the doc directory, or the
[Running xoreos](https://wiki.xoreos.org/index.php?title=Running_xoreos)
page on our wiki.


Links
-----

- [xoreos website](https://xoreos.org/)
- [xoreos wiki](https://wiki.xoreos.org/)
- [Screenshots](https://xoreos.org/screenshots/index.html)
- [Main source repository](https://github.com/xoreos/xoreos)
- [All xoreos repositories](https://github.com/xoreos/)
- [Doxygen documentation](https://xoreos.org/doxygen/)


Contact
-------

To contact us, please either write to [mailing list](https://xoreos.org/mailman/listinfo/xoreos-devel),
or join our IRC channel #xoreos on [Libera IRC](https://libera.chat/).
