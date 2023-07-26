# Contour - a modern & actually fast Terminal Emulator
[![CI Build](https://github.com/contour-terminal/contour/workflows/Build/badge.svg)](https://github.com/contour-terminal/contour/actions?query=workflow%3ABuild)
[![codecov](https://codecov.io/gh/contour-terminal/contour/branch/master/graph/badge.svg)](https://codecov.io/gh/contour-terminal/contour)
[![C++20](https://img.shields.io/badge/standard-C%2B%2B%2020-blue.svg?logo=C%2B%2B)](https://isocpp.org/)
[![Discord](https://img.shields.io/discord/479301317337284608.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.gg/ncv4pG9)
[![Twitch Live Stream](https://img.shields.io/badge/Twitch-Live%20Stream-blue?style=flat-square)](https://twitch.tv/christianparpart)
<img alt="open collective badge" src="https://opencollective.com/contour-terminal-emulator/tiers/backer/badge.svg?label=backer&color=brightgreen" />

![screenshot showcasing notcurses ncneofetch on KDE/Fedora](docs/screenshots/contour-notcurses-ncneofetch.png "Screenshot")

`contour` is a modern and actually fast, modal, virtual terminal emulator,
for everyday use. It is aiming for power users with a modern feature mindset.

## Features

- ✅ Available on all 4 major platforms, Linux, OS/X, FreeBSD, Windows.
- ✅ GPU-accelerated rendering.
- ✅ Font ligatures support (such as in Fira Code).
- ✅ Unicode: Emoji support (-: 🌈 💝 😛 👪 - including ZWJ, VS15, VS16 emoji :-)
- ✅ Unicode: Grapheme cluster support
- ✅ Bold and italic fonts
- ✅ High-DPI support.
- ✅ Vertical Line Markers (quickly jump to markers in your history!)
- ✅ Vi-like input modes for improved selection and copy'n'paste experience and Vi-like `scrolloff` feature.
- ✅ Blurred behind transparent background when using Windows 10 or KDE window manager on Linux.
- ✅ Blurrable Background image support.
- ✅ Runtime configuration reload
- ✅ 256-color and Truecolor support
- ✅ Key binding customization
- ✅ Color Schemes
- ✅ Profiles (grouped customization of: color scheme, login shell, and related behaviours)
- ✅ [Synchronized rendering](https://github.com/contour-terminal/contour/wiki/VTExtensions#synchronized-output) (via `SM ? 2026` / `RM ? 2026`)
- ✅ Text reflow (configurable via `SM ? 2028` / `RM ? 2028`)
- ✅ Clickable hyperlinks via [OSC 8](https://gist.github.com/egmontkob/eb114294efbcd5adb1944c9f3cb5feda)
- ✅ Clipboard setting via OSC 52
- ✅ Sixel inline images
- ✅ Terminal page [buffer capture VT extension](https://github.com/contour-terminal/contour/wiki/VTExtensions#buffer-capture) to quickly extract contents.
- ✅ Builtin [Fira Code inspired progress bar](https://github.com/contour-terminal/contour/issues/521) support.
- ✅ Read-only mode, protecting against accidental user-input to the running application, such as <kbd>Ctrl</kbd>+<kbd>C</kbd>.
- ✅ VT320 Host-programmable and Indicator status line support.
- ✅ and much more ...

## Installation

`contour` is packaged and available for installation on multiple distributions.
 - `Fedora` use official [package](https://packages.fedoraproject.org/pkgs/contour-terminal/contour-terminal/)

```sh
sudo dnf install contour-terminal
```

 - `Arch` use AUR [package](https://aur.archlinux.org/packages/contour-git)

### Installing via Flatpak

#### Install from Flathub

Click the following button install Contour from the Flathub store.

[![Get it on Flathub](https://raw.githubusercontent.com/flatpak-design-team/flathub-mockups/master/assets/download-button/download.svg?sanitize=true)](https://flathub.org/apps/details/org.contourterminal.Contour)


#### Prerequisites

- Make sure you have flatpak installed in your system ([here is a tutorial on how to install it](https://flatpak.org/getting.html)), and make sure that the version is >= 0.10 (check it using this command: `flatpak --version`)
- Add the [flathub](https://flathub.org) repository using the following command: `flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`.
- Proceed with one of the following options:
  - [Install from Flathub](#install-from-flathub)
  - [Install from GitHub release](https://github.com/contour-terminal/contour/releases)

## Requirements

- **operating system**: A *recent* operating system (OS/X 12, Windows 10+, an up-to-date Linux, or FreeBSD)
- **GPU**: driver must support at least OpenGL 3.3 hardware accelerated or as software rasterizer.
- **CPU**: x86-64 AMD or Intel with AES-NI instruction set or ARMv8 with crypto extensions.

## Configuration

In order to set up Contour, it is necessary to modify the configuration file
`contour.yml`, which is initially generated in the `$HOME/.config/contour`
directory. Some features also require shell integration. These can be generated
via the CLI (see below), these currently exist for zsh, fish and tcsh.

## Installing from source

Contour is best installed from supported package managers, but you can build
from source by following the instruction below.

### UNIX-like systems (Linux, FreeBSD, OS/X)

#### Prerequisites

```sh
./scripts/install-deps.sh
```

This script *might* ask you for the administrator password if a package dependency
can be insalled via the system package manager.

#### Compile

```sh
cmake -S . -B build -G Ninja
cmake --build build/

# Optionally, if you want to install from source
cmake --build build/ --target install
```

#### Windows 10 or newer

#### Prerequisites

For Windows, you must have Windows 10, 2018 Fall Creators Update, and Visual Studio 2019, installed.
It will neither build nor run on any prior Windows OS, due to libterminal making use of [ConPTY API](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

1. Set up [vcpkg](https://vcpkg.io/en/getting-started.html), preferably somewhere high up in the folder hierarchy, and add the folder to your `PATH`.

```
cd C:\
git clone git clone https://github.com/Microsoft/vcpkg.git
.\vcpkg\bootstrap-vcpkg.bat
```

2. Install Visual Studio Build Tools (make sure to select the CLI tools for
   C++, which you might need to do in the separate components tab).
3. Install Qt6 (i.e. to C:\Qt)
4. Open the _developer_ version of Powershell.
5. In the `contour` source folder execute `.\scripts\install-deps.ps1`. This step may take a _very_ long time.


#### Compile

In the _developer_ version of Powershell:

```psh
# change paths accordingly if you installed QT and vcpkg to somewhere else
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=C:\vcpkg\scripts\buildsystems\vcpkg.cmake -DCMAKE_PREFIX_PATH=C:\Qt\6.5.0\msvc2019_64\lib\cmake
cmake --build build/

# Optionally, if you want to install from source
cmake --build build/ --target install
```

#### Distribution Packages

[![Packaging status](https://repology.org/badge/vertical-allrepos/contour-terminal.svg)](https://repology.org/project/contour-terminal/versions)

## CLI - Command Line Interface

```txt
  Usage:

    contour [terminal] [config FILE] [profile NAME] [debug TAGS] [live-config] [dump-state-at-exit PATH]
                       [early-exit-threshold UINT] [working-directory DIRECTORY] [class WM_CLASS]
                       [platform PLATFORM[:OPTIONS]] [session SESSION_ID] [PROGRAM ARGS...]
    contour font-locator [config FILE] [profile NAME] [debug TAGS]
    contour info vt
    contour help
    contour version
    contour license
    contour parser-table
    contour list-debug-tags
    contour generate terminfo to FILE
    contour generate config to FILE
    contour generate integration shell SHELL to FILE
    contour capture [logical] [words] [timeout SECONDS] [lines COUNT] to FILE
    contour set profile [to NAME]

```

# References

* [VT510](https://vt100.net/docs/vt510-rm/): VT510 Manual, see Chapter 5.
* [ECMA-35](http://www.ecma-international.org/publications/standards/Ecma-035.htm):
    Character Code Structure and Extension Techniques
* [ECMA-43](http://www.ecma-international.org/publications/standards/Ecma-043.htm):
    8-bit Coded Character Set Structure and Rules
* [ECMA-48](http://www.ecma-international.org/publications/standards/Ecma-048.htm):
    Control Functions for Coded Character Sets
* [ISO/IEC 8613-6](https://www.iso.org/standard/22943.html):
    Character content architectures
* [xterm](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html): xterm control sequences
* [console\_codes](http://man.he.net/man4/console_codes) Linux console codes
* [Summary of ANSI standards for ASCII terminals](http://www.inwap.com/pdp10/ansicode.txt)
* [Text Terminal HOWTO (Chapter 7.2, PTY)](http://tldp.org/HOWTO/Text-Terminal-HOWTO-7.html#ss7.2)
* [ANSI escape code](https://en.wikipedia.org/wiki/ANSI_escape_code) in Wikipedia

### License

```
Contour - A modern C++ Terminal Emulator
-------------------------------------------

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
