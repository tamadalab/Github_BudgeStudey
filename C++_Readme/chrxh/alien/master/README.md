<h1 align="center">
<a href="https://alien-project.org" target="_blank">ALIEN - Explore worlds of artificial life</a>
</h1>

<h1 align="center">
<img src="img/alien.png" width=100%>
</h1>
<p>
<b><i>A</i></b>rtificial <b><i>LI</i></b>fe <b><i>EN</i></b>vironment <b>(ALIEN)</b> is an artificial life simulation tool based on a specialized 2D particle engine in CUDA for soft bodies and fluids. Each simulated body consists of a network of particles that can be upgraded with higher-level functions, ranging from pure information processing capabilities to physical equipment (such as sensors, muscles, weapons, constructors, etc.) whose executions are orchestrated by neural networks. The bodies can be thought of as agents or digital organisms operating in a common environment. Their blueprints can be stored in genomes and passed on to offspring.
</p>
<p>
The simulation code is written entirely in CUDA and optimized for large-scale real-time simulations with millions of particles.
The development is driven by the desire to better understand the conditions for (pre-)biotic evolution and the growing complexity of biological systems.
An important goal is to make the simulator user-friendly through a modern user interface, visually appealing rendering and a playful approach. 
</p>

<p>
  Please join our <a href="https://discord.gg/7bjyZdXXQ2" target="_blank">Discord server</a> as a place for discussions, new developments and feedback around ALIEN and artificial life in general.
</p>

# Main features
### Physics and graphics engine
- Particles for simulating soft and rigid body mechanics, fluids, heat dissipation, damage, adhesion etc.
- Real-time user interactions with running simulations
- Simulation runs entirely on GPU via CUDA
- Rendering and post-processing via OpenGL using CUDA-OpenGL interoperability

https://user-images.githubusercontent.com/73127001/229868357-131fa71f-d03d-45db-ac76-9d192f5464af.mp4

### Artificial Life engine extensions
- Multi-cellular organisms are simulated as particle networks
- Genetic system and cell by cell construction of offspring
- Neural networks for controlling higher-level functions (e.g. sensors and muscles)
- Various colors may be used to customize cell types according to own specifications
- Spatially varying simulation parameters

https://user-images.githubusercontent.com/73127001/229569056-0db6562b-0147-43c8-a977-5f12c1b6277b.mp4

### Extensive editing tools
- Graph editor for manipulating every particle and connection
- Freehand and geometric drawing tools
- Genetic editor for designing customized organisms
- Mass-operations and (up/down) scaling functions

### Networking
- Built-in simulation browser
- Download and upload simulation files
- Rate simulations by giving stars

# But for what is this useful?
- A first attempt to answer: Feed your curiosity by watching evolution at work! As soon as self-replicating machines come into play and mutations are turned on, the simulation itself does everything.
- Perhaps the most honest answer: Fun! It is almost like a game with a pretty fast and realistic physics engine. You can make hundreds of thousands of machines accelerate and destroy with the mouse cursor. It feels like playing god in your own universe with your own rules. Different render styles and a visual editor offer fascinating insights into the events. There are a lot of videos on the [YouTube channel](https://youtube.com/channel/UCtotfE3yvG0wwAZ4bDfPGYw) for illustration.
- A more academic answer: A tool to tackle fundamental questions of how complexity or life-like structure may arise from simple components. How do entire ecosystems adapt to environmental changes and find a new equilibrium? How to find conditions that allow open-ended evolution?

# Documentation
A documentation for the previous major version, which introduces the reader to the simulator with tutorial-like articles, can be found at [alien-project.gitbook.io/docs](https://alien-project.gitbook.io/docs). Please notice that many of the information therein are no longer up to date.

A new documentation is currently under construction. However a lot of useful information is provided in the program itself via help windows and tooltips.

Further information and artwork:
* [Website](https://alien-project.org)
* [YouTube](https://youtube.com/channel/UCtotfE3yvG0wwAZ4bDfPGYw)
* [Twitter](https://twitter.com/chrx_h)
* [Reddit](https://www.reddit.com/r/AlienProject)
* [Discord](https://discord.gg/7bjyZdXXQ2)

# Minimal system requirements
An Nvidia graphics card with compute capability 6.0 or higher is needed. Please check [https://en.wikipedia.org/wiki/CUDA#GPUs_supported](https://en.wikipedia.org/wiki/CUDA#GPUs_supported).

# Installer
An installer for the latest beta for Windows: [download link](https://alien-project.org/media/files/alien-installer-v4-beta.zip)

In the case that the program crashes for an unknown reason, please refer to the troubleshooting section in [alien-project.org/downloads.html](https://alien-project.org/downloads.html).

# How to build the sources
The build process is mostly automated using the cross-platform CMake build system and the vcpkg package manager, which is included as a Git submodule.

### Getting the sources
To obtain the sources, please open a command prompt in a suitable directory (which should not contain whitespace characters) and enter the following command:
```
git clone --recursive https://github.com/chrxh/alien.git
```
Note: The `--recursive` parameter is necessary to check out the vcpkg submodule as well. Besides that, submodules are not normally updated by the standard `git pull` command. Instead, you need to write `git pull --recurse-submodules`.

### Build instructions
Prerequisites: [CUDA Toolkit 11.2+](https://developer.nvidia.com/cuda-downloads) and a toolchain for CMake (e.g. GCC 9.x+ or [MSVC v142+](https://visualstudio.microsoft.com/de/free-developer-offers/))

Build steps:
```
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
cmake --build . --config Release -j8
```
If everything goes well, the ALIEN executable can be found under the build directory in `./alien` or `.\Release\alien.exe` depending on the used toolchain and platform.

# Contributing to the project
Contributions to the project are very welcome. The most convenient way is to communicate via [GitHub Issues](https://github.com/chrxh/alien/issues), [Pull requests](https://github.com/chrxh/alien/pulls) or the [Discussion forum](https://github.com/chrxh/alien/discussions) depending on the subject. For example, it could be
- Providing new content (simulation or genome files)
- Producing or sharing media files
- Reporting of bugs, wanted features, questions or feedback via GitHub Issues or in the Discussion forum.
- Pull requests for bug fixes, code cleanings, optimizations or minor tweaks. If you want to implement new features, refactorings or other major changes, please use the [Discussion forum](https://github.com/chrxh/alien/discussions) for consultation and coordination in advance.
- Extensions or corrections to the [alien-docs](https://alien-project.gitbook.io/docs). It has its [own repository](https://github.com/chrxh/alien-docs).

A short architectural overview of the source code can be found in the [documentation](https://alien-project.gitbook.io/docs/under-the-hood).

# Dependency list
- [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit)
- [Dear ImGui](https://github.com/ocornut/imgui)
- [ImPlot](https://github.com/epezent/implot)
- [ImFileDialog](https://github.com/dfranx/ImFileDialog)
- [boost](https://www.boost.org)
- [Glad](https://glad.dav1d.de)
- [GLFW](https://www.glfw.org)
- [glew](https://github.com/nigels-com/glew)
- [stb](https://github.com/nothings/stb)
- [cereal](https://github.com/USCiLab/cereal)
- [zlib](https://www.zlib.net)
- [zstr](https://github.com/mateidavid/zstr)
- [OpenSSL](https://github.com/openssl/openssl)
- [cpp-httplib](https://github.com/yhirose/cpp-httplib)
- [IconFontCppHeaders](https://github.com/juliettef/IconFontCppHeaders)
- [googletest](https://github.com/google/googletest)
- [vcpkg](https://vcpkg.io/en/index.html)

# Screenshots
#### Different plant-like populations around a radiation source
![Screenshot1](https://user-images.githubusercontent.com/73127001/229311601-839649a6-c60c-4723-99b3-26086e3e4340.jpg)

<h1 align="center"></h1>

#### Close-up of different types of organisms so that their cell networks can be seen
![Screenshot2](https://user-images.githubusercontent.com/73127001/229311604-3ee433d4-7dd8-46e2-b3e6-489eaffbda7b.jpg)

<h1 align="center"></h1>

#### Different swarms attacking an ecosystem
![Screenshot3](https://user-images.githubusercontent.com/73127001/229311606-2f590bfb-71a8-4f71-8ff7-7013de9d7496.jpg)

<h1 align="center"></h1>

#### Genome editor
![Screenshot3b](https://user-images.githubusercontent.com/73127001/229313813-c9ce70e2-d61f-4745-b64f-ada0b6758901.jpg)

# License
ALIEN is licensed under the [GPLv3](LICENSE).
