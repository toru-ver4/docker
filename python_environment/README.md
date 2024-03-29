# Python Environment

## Overview

Build a python development environment.

## Requirements

* Docker for Windows
* Visual Studio Code
* VcXsrv (X11 Server)

## Build

```powershell
docker build -t takuver4/python_dev:rev12 .
```

## Push

```powershell
docker push takuver4/python_dev:rev12
```

```powershell
docker run -it -P --name python_dev_12 -v C:\Users\toruv\OneDrive\work\sample_code:/work/src -e DISPLAY=host.docker.internal:0.0 --rm takuver4/python_dev:rev12 bash
```

## Create a container using `docker-compose up`

```powershell
docker-compose up -d
```

### (Option) Create a container using `docker run`

```powershell
$WORKING_DIR = "C:\Users\toruv\OneDrive\work\sample_code";
$DATA_DIR = "D:\abuse";
$PYTHON_LIB_DIR_ON_LINUX = "/usr/local/lib/python3.10/site-packages:/work/src/ty_lib";
docker run -it -d -P --name python_dev_12 `
-v ${WORKING_DIR}:/work/src -v ${DATA_DIR}:/work/overuse `
-e DISPLAY=host.docker.internal:0.0 `
-e PYTHONPATH=$PYTHON_LIB_DIR_ON_LINUX --rm takuver4/python_dev:rev12
```

## Attach Visual Studio Code

![figure](./figures/attach_visual_studio_coode.png)

## Information

### pip list

```txt
Package                       Version
----------------------------- ---------
alabaster                     0.7.13
anyio                         4.0.0
argon2-cffi                   23.1.0
argon2-cffi-bindings          21.2.0
arrow                         1.2.3
asttokens                     2.4.0
async-lru                     2.0.4
attrs                         23.1.0
Babel                         2.12.1
backcall                      0.2.0
beautifulsoup4                4.12.2
bleach                        6.0.0
cachetools                    5.3.1
certifi                       2023.7.22
cffi                          1.15.1
charset-normalizer            3.2.0
colour-datasets               0.2.2
colour-science                0.4.3
comm                          0.1.4
contourpy                     1.1.0
cycler                        0.11.0
debugpy                       1.8.0
decorator                     5.1.1
defusedxml                    0.7.1
docutils                      0.18.1
exceptiongroup                1.1.3
executing                     1.2.0
fastjsonschema                2.18.0
flake8                        6.1.0
fonttools                     4.42.1
fqdn                          1.5.1
idna                          3.4
imageio                       2.31.3
imagesize                     1.4.1
iniconfig                     2.0.0
ipykernel                     6.25.2
ipython                       8.15.0
ipython-genutils              0.2.0
ipywidgets                    8.1.1
isoduration                   20.11.0
jedi                          0.19.0
Jinja2                        3.1.2
json5                         0.9.14
jsonpointer                   2.4
jsonschema                    4.19.0
jsonschema-specifications     2023.7.1
jupyter                       1.0.0
jupyter_client                8.3.1
jupyter-console               6.6.3
jupyter_core                  5.3.1
jupyter-events                0.7.0
jupyter-lsp                   2.2.0
jupyter_server                2.7.3
jupyter_server_terminals      0.4.4
jupyterlab                    4.0.5
jupyterlab-pygments           0.2.2
jupyterlab_server             2.25.0
jupyterlab-widgets            3.0.9
kiwisolver                    1.4.5
MarkupSafe                    2.1.3
matplotlib                    3.7.3
matplotlib-inline             0.1.6
mccabe                        0.7.0
mistune                       3.0.1
mpmath                        1.3.0
nbclient                      0.8.0
nbconvert                     7.8.0
nbformat                      5.9.2
nest-asyncio                  1.5.7
notebook                      7.0.3
notebook_shim                 0.2.3
numpy                         1.25.2
opencv-python                 4.8.0.76
overrides                     7.4.0
packaging                     23.1
pandocfilters                 1.5.0
parso                         0.8.3
pexpect                       4.8.0
pickleshare                   0.7.5
Pillow                        10.0.0
pip                           23.2.1
platformdirs                  3.10.0
pluggy                        1.3.0
prometheus-client             0.17.1
prompt-toolkit                3.0.39
psutil                        5.9.5
ptyprocess                    0.7.0
pure-eval                     0.2.2
pycodestyle                   2.11.0
pycparser                     2.21
pyflakes                      3.1.0
Pygments                      2.16.1
pyparsing                     3.1.1
pyqtgraph                     0.13.3
PySide2                       5.15.2.1
PySimpleGUI                   4.60.5
pytest                        7.4.2
python-dateutil               2.8.2
python-json-logger            2.0.7
PyYAML                        6.0.1
pyzmq                         25.1.1
qtconsole                     5.4.4
QtPy                          2.4.0
referencing                   0.30.2
requests                      2.31.0
rfc3339-validator             0.1.4
rfc3986-validator             0.1.1
rpds-py                       0.10.3
scipy                         1.11.2
Send2Trash                    1.8.2
setuptools                    59.6.0
shiboken2                     5.15.2.1
six                           1.16.0
sniffio                       1.3.0
snowballstemmer               2.2.0
soupsieve                     2.5
Sphinx                        7.2.6
sphinx-rtd-theme              1.3.0
sphinxcontrib-applehelp       1.0.7
sphinxcontrib-devhelp         1.0.5
sphinxcontrib-htmlhelp        2.0.4
sphinxcontrib-jquery          4.1
sphinxcontrib-jsmath          1.0.1
sphinxcontrib-qthelp          1.0.6
sphinxcontrib-serializinghtml 1.1.9
stack-data                    0.6.2
sympy                         1.12
terminado                     0.17.1
tinycss2                      1.2.1
tomli                         2.0.1
tornado                       6.3.3
tqdm                          4.66.1
traitlets                     5.10.0
typing_extensions             4.7.1
uri-template                  1.3.0
urllib3                       2.0.4
wavio                         0.0.7
wcwidth                       0.2.6
webcolors                     1.13
webencodings                  0.5.1
websocket-client              1.6.3
widgetsnbextension            4.0.9
xlrd                          1.2.0
```

### dpkg -l

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                    Architecture Description
+++-======================================-==========================================-============-================================================================================================
ii  adduser                                3.118ubuntu5                               all          add and remove users and groups
ii  apt                                    2.4.10                                     amd64        commandline package manager
ii  autoconf                               2.71-2                                     all          automatic configure script builder
ii  automake                               1:1.16.5-1.3                               all          Tool for generating GNU Standards-compliant Makefiles
ii  autotools-dev                          20220109.1                                 all          Update infrastructure for config.{guess,sub} files
ii  base-files                             12ubuntu4.4                                amd64        Debian base system miscellaneous files
ii  base-passwd                            3.5.52build1                               amd64        Debian base system master password and group files
ii  bash                                   5.1-6ubuntu1                               amd64        GNU Bourne Again SHell
ii  binutils                               2.38-4ubuntu2.3                            amd64        GNU assembler, linker and binary utilities
ii  binutils-common:amd64                  2.38-4ubuntu2.3                            amd64        Common files for the GNU assembler, linker and binary utilities
ii  binutils-x86-64-linux-gnu              2.38-4ubuntu2.3                            amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  blt                                    2.5.3+dfsg-4.1build2                       amd64        graphics extension library for Tcl/Tk - run-time
ii  bsdutils                               1:2.37.2-4ubuntu3                          amd64        basic utilities from 4.4BSD-Lite
ii  build-essential                        12.9ubuntu3                                amd64        Informational list of build-essential packages
ii  bzip2                                  1.0.8-5build1                              amd64        high-quality block-sorting file compressor - utilities
ii  ca-certificates                        20230311ubuntu0.22.04.1                    all          Common CA certificates
ii  cargo                                  0.67.1+ds0ubuntu0.libgit2-0ubuntu0.22.04.2 amd64        Rust package manager
ii  cbindgen                               0.20.0-1                                   amd64        Generates C bindings from Rust code
ii  clang                                  1:14.0-55~exp2                             amd64        C, C++ and Objective-C compiler (LLVM based), clang binary
ii  clang-14                               1:14.0.0-1ubuntu1.1                        amd64        C, C++ and Objective-C compiler
ii  cmake                                  3.22.1-1ubuntu1.22.04.1                    amd64        cross-platform, open-source make system
ii  cmake-data                             3.22.1-1ubuntu1.22.04.1                    all          CMake data files (modules, templates and documentation)
ii  coreutils                              8.32-4.1ubuntu1                            amd64        GNU core utilities
ii  cpp                                    4:11.2.0-1ubuntu1                          amd64        GNU C preprocessor (cpp)
ii  cpp-11                                 11.4.0-1ubuntu1~22.04                      amd64        GNU C preprocessor
ii  curl                                   7.81.0-1ubuntu1.13                         amd64        command line tool for transferring data with URL syntax
ii  dash                                   0.5.11+git20210903+057cd650a4ed-3build1    amd64        POSIX-compliant shell
ii  debconf                                1.5.79ubuntu1                              all          Debian configuration management system
ii  debianutils                            5.5-1ubuntu2                               amd64        Miscellaneous utilities specific to Debian
ii  dh-elpa-helper                         2.0.9ubuntu1                               all          helper package for emacs lisp extensions
ii  diffutils                              1:3.8-0ubuntu2                             amd64        File comparison utilities
ii  doxygen                                1.9.1-2ubuntu2                             amd64        Documentation system for C, C++, Java, Python and other languages
ii  dpkg                                   1.21.1ubuntu2.2                            amd64        Debian package management system
ii  dpkg-dev                               1.21.1ubuntu2.2                            all          Debian package development tools
ii  e2fsprogs                              1.46.5-2ubuntu1.1                          amd64        ext2/ext3/ext4 file system utilities
ii  emacsen-common                         3.0.4                                      all          Common facilities for all emacsen
ii  ffmpeg                                 7:4.4.2-0ubuntu0.22.04.1                   amd64        Tools for transcoding, streaming and playing of multimedia files
ii  findutils                              4.8.0-1ubuntu3                             amd64        utilities for finding files--find, xargs
ii  fontconfig                             2.13.1-4.2ubuntu5                          amd64        generic font configuration library - support binaries
ii  fontconfig-config                      2.13.1-4.2ubuntu5                          all          generic font configuration library - configuration
ii  fonts-dejavu-core                      2.37-2build1                               all          Vera font family derivate with additional characters
ii  freeglut3:amd64                        2.8.1-6                                    amd64        OpenGL Utility Toolkit
ii  freeglut3-dev:amd64                    2.8.1-6                                    amd64        OpenGL Utility Toolkit development files
ii  g++                                    4:11.2.0-1ubuntu1                          amd64        GNU C++ compiler
ii  g++-11                                 11.4.0-1ubuntu1~22.04                      amd64        GNU C++ compiler
ii  gcc                                    4:11.2.0-1ubuntu1                          amd64        GNU C compiler
ii  gcc-11                                 11.4.0-1ubuntu1~22.04                      amd64        GNU C compiler
ii  gcc-11-base:amd64                      11.4.0-1ubuntu1~22.04                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-12-base:amd64                      12.3.0-1ubuntu1~22.04                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gfortran-11                            11.4.0-1ubuntu1~22.04                      amd64        GNU Fortran compiler
ii  git                                    1:2.34.1-1ubuntu1.10                       amd64        fast, scalable, distributed revision control system
ii  git-man                                1:2.34.1-1ubuntu1.10                       all          fast, scalable, distributed revision control system (manual pages)
ii  googletest                             1.11.0-3                                   all          Google's C++ test framework sources
ii  gpac                                   2.0.0+dfsg1-2                              amd64        GPAC Project on Advanced Content - utilities
ii  gpac-modules-base:amd64                2.0.0+dfsg1-2                              amd64        GPAC Project on Advanced Content - modules
ii  gpgv                                   2.2.27-3ubuntu2.1                          amd64        GNU privacy guard - signature verification tool
ii  grep                                   3.7-1build1                                amd64        GNU grep, egrep and fgrep
ii  gzip                                   1.10-4ubuntu4.1                            amd64        GNU compression utilities
ii  hicolor-icon-theme                     0.17-2                                     all          default fallback theme for FreeDesktop.org icon themes
ii  hostname                               3.23ubuntu2                                amd64        utility to set/show the host name or domain name
ii  ibverbs-providers:amd64                39.0-1                                     amd64        User space provider drivers for libibverbs
ii  icu-devtools                           70.1-2                                     amd64        Development utilities for International Components for Unicode
ii  imagemagick                            8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3        amd64        image manipulation programs -- binaries
ii  imagemagick-6-common                   8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3        all          image manipulation programs -- infrastructure
ii  imagemagick-6.q16                      8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3        amd64        image manipulation programs -- quantum depth Q16
ii  init-system-helpers                    1.62                                       all          helper tools for all init systems
ii  lib32gcc-s1                            12.3.0-1ubuntu1~22.04                      amd64        GCC support library (32 bit Version)
ii  lib32stdc++6                           12.3.0-1ubuntu1~22.04                      amd64        GNU Standard C++ Library v3 (32 bit Version)
ii  liba52-0.7.4:amd64                     0.7.4-20                                   amd64        library for decoding ATSC A/52 streams
ii  libacl1:amd64                          2.3.1-1                                    amd64        access control list - shared library
ii  libaom-dev:amd64                       3.3.0-1                                    amd64        AV1 Video Codec Library -- Development Files
ii  libaom3:amd64                          3.3.0-1                                    amd64        AV1 Video Codec Library
ii  libapparmor1:amd64                     3.0.4-2ubuntu2.2                           amd64        changehat AppArmor library
ii  libapt-pkg6.0:amd64                    2.4.10                                     amd64        package management runtime library
ii  libarchive13:amd64                     3.6.0-1ubuntu1                             amd64        Multi-format archive and compression library (shared library)
ii  libasan6:amd64                         11.4.0-1ubuntu1~22.04                      amd64        AddressSanitizer -- a fast memory error detector
ii  libasound2:amd64                       1.2.6.1-1ubuntu1                           amd64        shared library for ALSA applications
ii  libasound2-data                        1.2.6.1-1ubuntu1                           all          Configuration files and profiles for ALSA drivers
ii  libass9:amd64                          1:0.15.2-1                                 amd64        library for SSA/ASS subtitles rendering
ii  libasyncns0:amd64                      0.8-6build2                                amd64        Asynchronous name service query library
ii  libatomic1:amd64                       12.3.0-1ubuntu1~22.04                      amd64        support library providing __atomic built-in functions
ii  libattr1:amd64                         1:2.5.1-1build1                            amd64        extended attribute handling - shared library
ii  libaudit-common                        1:3.0.7-1build1                            all          Dynamic library for security auditing - common files
ii  libaudit1:amd64                        1:3.0.7-1build1                            amd64        Dynamic library for security auditing
ii  libavc1394-0:amd64                     0.5.4-5build2                              amd64        control IEEE 1394 audio/video devices
ii  libavcodec58:amd64                     7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library with de/encoders for audio/video codecs - runtime files
ii  libavdevice58:amd64                    7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library for handling input and output devices - runtime files
ii  libavfilter7:amd64                     7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library containing media filters - runtime files
ii  libavformat58:amd64                    7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library with (de)muxers for multimedia containers - runtime files
ii  libavutil56:amd64                      7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library with functions for simplifying programming - runtime files
ii  libbinutils:amd64                      2.38-4ubuntu2.3                            amd64        GNU binary utilities (private shared library)
ii  libblas3:amd64                         3.10.0-2ubuntu1                            amd64        Basic Linear Algebra Reference implementations, shared library
ii  libblkid1:amd64                        2.37.2-4ubuntu3                            amd64        block device ID library
ii  libbluray2:amd64                       1:1.3.1-1                                  amd64        Blu-ray disc playback support library (shared library)
ii  libboost-all-dev                       1.74.0.3ubuntu7                            amd64        Boost C++ Libraries development files (ALL) (default version)
ii  libboost-atomic-dev:amd64              1.74.0.3ubuntu7                            amd64        atomic data types, operations, and memory ordering constraints (default version)
ii  libboost-atomic1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        atomic data types, operations, and memory ordering constraints
ii  libboost-atomic1.74.0:amd64            1.74.0-14ubuntu3                           amd64        atomic data types, operations, and memory ordering constraints
ii  libboost-chrono-dev:amd64              1.74.0.3ubuntu7                            amd64        C++ representation of time duration, time point, and clocks (default version)
ii  libboost-chrono1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        C++ representation of time duration, time point, and clocks
ii  libboost-chrono1.74.0:amd64            1.74.0-14ubuntu3                           amd64        C++ representation of time duration, time point, and clocks
ii  libboost-container-dev:amd64           1.74.0.3ubuntu7                            amd64        C++ library that implements several well-known containers - dev files (default version)
ii  libboost-container1.74-dev:amd64       1.74.0-14ubuntu3                           amd64        C++ library that implements several well-known containers - dev files
ii  libboost-container1.74.0:amd64         1.74.0-14ubuntu3                           amd64        C++ library that implements several well-known containers
ii  libboost-context-dev:amd64             1.74.0.3ubuntu7                            amd64        provides a sort of cooperative multitasking on a single thread (default version)
ii  libboost-context1.74-dev:amd64         1.74.0-14ubuntu3                           amd64        provides a sort of cooperative multitasking on a single thread
ii  libboost-context1.74.0:amd64           1.74.0-14ubuntu3                           amd64        provides a sort of cooperative multitasking on a single thread
ii  libboost-coroutine-dev:amd64           1.74.0.3ubuntu7                            amd64        provides a sort of cooperative multitasking on a single thread (default version)
ii  libboost-coroutine1.74-dev:amd64       1.74.0-14ubuntu3                           amd64        provides a sort of cooperative multitasking on a single thread
ii  libboost-coroutine1.74.0:amd64         1.74.0-14ubuntu3                           amd64        provides a sort of cooperative multitasking on a single thread
ii  libboost-date-time-dev:amd64           1.74.0.3ubuntu7                            amd64        set of date-time libraries based on generic programming concepts (default version)
ii  libboost-date-time1.74-dev:amd64       1.74.0-14ubuntu3                           amd64        set of date-time libraries based on generic programming concepts
ii  libboost-date-time1.74.0:amd64         1.74.0-14ubuntu3                           amd64        set of date-time libraries based on generic programming concepts
ii  libboost-dev:amd64                     1.74.0.3ubuntu7                            amd64        Boost C++ Libraries development files (default version)
ii  libboost-exception-dev:amd64           1.74.0.3ubuntu7                            amd64        library to help write exceptions and handlers (default version)
ii  libboost-exception1.74-dev:amd64       1.74.0-14ubuntu3                           amd64        library to help write exceptions and handlers
ii  libboost-fiber-dev:amd64               1.74.0.3ubuntu7                            amd64        cooperatively-scheduled micro-/userland-threads (default version)
ii  libboost-fiber1.74-dev:amd64           1.74.0-14ubuntu3                           amd64        cooperatively-scheduled micro-/userland-threads
ii  libboost-fiber1.74.0:amd64             1.74.0-14ubuntu3                           amd64        cooperatively-scheduled micro-/userland-threads
ii  libboost-filesystem-dev:amd64          1.74.0.3ubuntu7                            amd64        filesystem operations (portable paths, iteration over directories, etc) in C++ (default version)
ii  libboost-filesystem1.74-dev:amd64      1.74.0-14ubuntu3                           amd64        filesystem operations (portable paths, iteration over directories, etc) in C++
ii  libboost-filesystem1.74.0:amd64        1.74.0-14ubuntu3                           amd64        filesystem operations (portable paths, iteration over directories, etc) in C++
ii  libboost-graph-dev:amd64               1.74.0.3ubuntu7                            amd64        generic graph components and algorithms in C++ (default version)
ii  libboost-graph-parallel-dev            1.74.0.3ubuntu7                            amd64        generic graph components and algorithms in C++ (default version)
ii  libboost-graph-parallel1.74-dev        1.74.0-14ubuntu3                           amd64        generic graph components and algorithms in C++
ii  libboost-graph-parallel1.74.0          1.74.0-14ubuntu3                           amd64        generic graph components and algorithms in C++
ii  libboost-graph1.74-dev:amd64           1.74.0-14ubuntu3                           amd64        generic graph components and algorithms in C++
ii  libboost-graph1.74.0:amd64             1.74.0-14ubuntu3                           amd64        generic graph components and algorithms in C++
ii  libboost-iostreams-dev:amd64           1.74.0.3ubuntu7                            amd64        Boost.Iostreams Library development files (default version)
ii  libboost-iostreams1.74-dev:amd64       1.74.0-14ubuntu3                           amd64        Boost.Iostreams Library development files
ii  libboost-iostreams1.74.0:amd64         1.74.0-14ubuntu3                           amd64        Boost.Iostreams Library
ii  libboost-locale-dev:amd64              1.74.0.3ubuntu7                            amd64        C++ facilities for localization (default version)
ii  libboost-locale1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        C++ facilities for localization
ii  libboost-locale1.74.0:amd64            1.74.0-14ubuntu3                           amd64        C++ facilities for localization
ii  libboost-log-dev                       1.74.0.3ubuntu7                            amd64        C++ logging library (default version)
ii  libboost-log1.74-dev                   1.74.0-14ubuntu3                           amd64        C++ logging library
ii  libboost-log1.74.0                     1.74.0-14ubuntu3                           amd64        C++ logging library
ii  libboost-math-dev:amd64                1.74.0.3ubuntu7                            amd64        Boost.Math Library development files (default version)
ii  libboost-math1.74-dev:amd64            1.74.0-14ubuntu3                           amd64        Boost.Math Library development files
ii  libboost-math1.74.0:amd64              1.74.0-14ubuntu3                           amd64        Boost.Math Library
ii  libboost-mpi-dev                       1.74.0.3ubuntu7                            amd64        C++ interface to the Message Passing Interface (MPI) (default version)
ii  libboost-mpi-python-dev                1.74.0.3ubuntu7                            amd64        C++ interface to the Message Passing Interface (MPI), Python Bindings (default version)
ii  libboost-mpi-python1.74-dev            1.74.0-14ubuntu3                           amd64        C++ interface to the Message Passing Interface (MPI), Python Bindings
ii  libboost-mpi-python1.74.0              1.74.0-14ubuntu3                           amd64        C++ interface to the Message Passing Interface (MPI), Python Bindings
ii  libboost-mpi1.74-dev                   1.74.0-14ubuntu3                           amd64        C++ interface to the Message Passing Interface (MPI)
ii  libboost-mpi1.74.0                     1.74.0-14ubuntu3                           amd64        C++ interface to the Message Passing Interface (MPI)
ii  libboost-nowide-dev                    1.74.0.3ubuntu7                            amd64        Standard library functions with UTF-8 API on Windows development files (default version)
ii  libboost-nowide1.74-dev                1.74.0-14ubuntu3                           amd64        Standard library functions with UTF-8 API on Windows development files
ii  libboost-nowide1.74.0                  1.74.0-14ubuntu3                           amd64        Standard library functions with UTF-8 API on Windows
ii  libboost-numpy-dev                     1.74.0.3ubuntu7                            amd64        Boost.Python NumPy extensions development files (default version)
ii  libboost-numpy1.74-dev                 1.74.0-14ubuntu3                           amd64        Boost.Python NumPy extensions development files
ii  libboost-numpy1.74.0                   1.74.0-14ubuntu3                           amd64        Boost.Python NumPy extensions
ii  libboost-program-options-dev:amd64     1.74.0.3ubuntu7                            amd64        program options library for C++ (default version)
ii  libboost-program-options1.74-dev:amd64 1.74.0-14ubuntu3                           amd64        program options library for C++
ii  libboost-program-options1.74.0:amd64   1.74.0-14ubuntu3                           amd64        program options library for C++
ii  libboost-python-dev                    1.74.0.3ubuntu7                            amd64        Boost.Python Library development files (default version)
ii  libboost-python1.74-dev                1.74.0-14ubuntu3                           amd64        Boost.Python Library development files
ii  libboost-python1.74.0                  1.74.0-14ubuntu3                           amd64        Boost.Python Library
ii  libboost-random-dev:amd64              1.74.0.3ubuntu7                            amd64        Boost Random Number Library (default version)
ii  libboost-random1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        Boost Random Number Library
ii  libboost-random1.74.0:amd64            1.74.0-14ubuntu3                           amd64        Boost Random Number Library
ii  libboost-regex-dev:amd64               1.74.0.3ubuntu7                            amd64        regular expression library for C++ (default version)
ii  libboost-regex1.74-dev:amd64           1.74.0-14ubuntu3                           amd64        regular expression library for C++
ii  libboost-regex1.74.0:amd64             1.74.0-14ubuntu3                           amd64        regular expression library for C++
ii  libboost-serialization-dev:amd64       1.74.0.3ubuntu7                            amd64        serialization library for C++ (default version)
ii  libboost-serialization1.74-dev:amd64   1.74.0-14ubuntu3                           amd64        serialization library for C++
ii  libboost-serialization1.74.0:amd64     1.74.0-14ubuntu3                           amd64        serialization library for C++
ii  libboost-stacktrace-dev:amd64          1.74.0.3ubuntu7                            amd64        library to capture and print stack traces - development files (default version)
ii  libboost-stacktrace1.74-dev:amd64      1.74.0-14ubuntu3                           amd64        library to capture and print stack traces - development files
ii  libboost-stacktrace1.74.0:amd64        1.74.0-14ubuntu3                           amd64        library to capture and print stack traces
ii  libboost-system-dev:amd64              1.74.0.3ubuntu7                            amd64        Operating system (e.g. diagnostics support) library (default version)
ii  libboost-system1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        Operating system (e.g. diagnostics support) library
ii  libboost-system1.74.0:amd64            1.74.0-14ubuntu3                           amd64        Operating system (e.g. diagnostics support) library
ii  libboost-test-dev:amd64                1.74.0.3ubuntu7                            amd64        components for writing and executing test suites (default version)
ii  libboost-test1.74-dev:amd64            1.74.0-14ubuntu3                           amd64        components for writing and executing test suites
ii  libboost-test1.74.0:amd64              1.74.0-14ubuntu3                           amd64        components for writing and executing test suites
ii  libboost-thread-dev:amd64              1.74.0.3ubuntu7                            amd64        portable C++ multi-threading (default version)
ii  libboost-thread1.74-dev:amd64          1.74.0-14ubuntu3                           amd64        portable C++ multi-threading
ii  libboost-thread1.74.0:amd64            1.74.0-14ubuntu3                           amd64        portable C++ multi-threading
ii  libboost-timer-dev:amd64               1.74.0.3ubuntu7                            amd64        C++ wall clock and CPU process timers (default version)
ii  libboost-timer1.74-dev:amd64           1.74.0-14ubuntu3                           amd64        C++ wall clock and CPU process timers
ii  libboost-timer1.74.0:amd64             1.74.0-14ubuntu3                           amd64        C++ wall clock and CPU process timers
ii  libboost-tools-dev                     1.74.0.3ubuntu7                            amd64        Boost C++ Libraries development tools (default version)
ii  libboost-type-erasure-dev:amd64        1.74.0.3ubuntu7                            amd64        C++ runtime polymorphism based on concepts (default version)
ii  libboost-type-erasure1.74-dev:amd64    1.74.0-14ubuntu3                           amd64        C++ runtime polymorphism based on concepts
ii  libboost-type-erasure1.74.0:amd64      1.74.0-14ubuntu3                           amd64        C++ runtime polymorphism based on concepts
ii  libboost-wave-dev:amd64                1.74.0.3ubuntu7                            amd64        C99/C++ preprocessor library (default version)
ii  libboost-wave1.74-dev:amd64            1.74.0-14ubuntu3                           amd64        C99/C++ preprocessor library
ii  libboost-wave1.74.0:amd64              1.74.0-14ubuntu3                           amd64        C99/C++ preprocessor library
ii  libboost1.74-dev:amd64                 1.74.0-14ubuntu3                           amd64        Boost C++ Libraries development files
ii  libboost1.74-tools-dev                 1.74.0-14ubuntu3                           amd64        Boost C++ Libraries development tools
ii  libbrotli-dev:amd64                    1.0.9-2build6                              amd64        library implementing brotli encoder and decoder (development files)
ii  libbrotli1:amd64                       1.0.9-2build6                              amd64        library implementing brotli encoder and decoder (shared libraries)
ii  libbs2b0:amd64                         3.1.0+dfsg-2.2build1                       amd64        Bauer stereophonic-to-binaural DSP library
ii  libbsd0:amd64                          0.11.5-1                                   amd64        utility functions from BSD systems - shared library
ii  libbz2-1.0:amd64                       1.0.8-5build1                              amd64        high-quality block-sorting file compressor library - runtime
ii  libc-bin                               2.35-0ubuntu3.3                            amd64        GNU C Library: Binaries
ii  libc-dev-bin                           2.35-0ubuntu3.3                            amd64        GNU C Library: Development binaries
ii  libc6:amd64                            2.35-0ubuntu3.3                            amd64        GNU C Library: Shared libraries
ii  libc6-dev:amd64                        2.35-0ubuntu3.3                            amd64        GNU C Library: Development Libraries and Header Files
ii  libc6-i386                             2.35-0ubuntu3.3                            amd64        GNU C Library: 32-bit shared libraries for AMD64
ii  libcaca0:amd64                         0.99.beta19-2.2ubuntu4                     amd64        colour ASCII art library
ii  libcairo-gobject2:amd64                1.16.0-5ubuntu2                            amd64        Cairo 2D vector graphics library (GObject library)
ii  libcairo2:amd64                        1.16.0-5ubuntu2                            amd64        Cairo 2D vector graphics library
ii  libcap-ng0:amd64                       0.7.9-2.2build3                            amd64        An alternate POSIX capabilities library
ii  libcap2:amd64                          1:2.44-1ubuntu0.22.04.1                    amd64        POSIX 1003.1e capabilities (library)
ii  libcbor0.8:amd64                       0.8.0-2ubuntu1                             amd64        library for parsing and generating CBOR (RFC 7049)
ii  libcc1-0:amd64                         12.3.0-1ubuntu1~22.04                      amd64        GCC cc1 plugin for GDB
ii  libcdio-cdda2:amd64                    10.2+2.0.0-1build3                         amd64        library to read and control digital audio CDs
ii  libcdio-paranoia2:amd64                10.2+2.0.0-1build3                         amd64        library to read digital audio CDs with error correction
ii  libcdio19:amd64                        2.1.0-3build1                              amd64        library to read and control CD-ROM
ii  libchromaprint1:amd64                  1.5.1-2                                    amd64        audio fingerprint library
ii  libclang-common-14-dev                 1:14.0.0-1ubuntu1.1                        amd64        Clang library - Common development package
ii  libclang-cpp14                         1:14.0.0-1ubuntu1.1                        amd64        C++ interface to the Clang library
ii  libclang1-14                           1:14.0.0-1ubuntu1.1                        amd64        C interface to the Clang library
ii  libcodec2-1.0:amd64                    1.0.1-3                                    amd64        Codec2 runtime library
ii  libcom-err2:amd64                      1.46.5-2ubuntu1.1                          amd64        common error description library
ii  libcrypt-dev:amd64                     1:4.4.27-1                                 amd64        libcrypt development files
ii  libcrypt1:amd64                        1:4.4.27-1                                 amd64        libcrypt shared library
ii  libctf-nobfd0:amd64                    2.38-4ubuntu2.3                            amd64        Compact C Type Format library (runtime, no BFD dependency)
ii  libctf0:amd64                          2.38-4ubuntu2.3                            amd64        Compact C Type Format library (runtime, BFD dependency)
ii  libcurl3-gnutls:amd64                  7.81.0-1ubuntu1.13                         amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcurl4:amd64                         7.81.0-1ubuntu1.13                         amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
ii  libdatrie1:amd64                       0.2.13-2                                   amd64        Double-array trie library
ii  libdav1d-dev:amd64                     0.9.2-1                                    amd64        fast and small AV1 video stream decoder (development files)
ii  libdav1d5:amd64                        0.9.2-1                                    amd64        fast and small AV1 video stream decoder (shared library)
ii  libdb5.3:amd64                         5.3.28+dfsg1-0.8ubuntu3                    amd64        Berkeley v5.3 Database Libraries [runtime]
ii  libdbus-1-3:amd64                      1.12.20-2ubuntu4.1                         amd64        simple interprocess messaging system (library)
ii  libdc1394-25:amd64                     2.2.6-4                                    amd64        high level programming interface for IEEE 1394 digital cameras
ii  libde265-0:amd64                       1.0.8-1                                    amd64        Open H.265 video codec implementation
ii  libde265-dev:amd64                     1.0.8-1                                    amd64        Open H.265 video codec implementation - development files
ii  libdebconfclient0:amd64                0.261ubuntu1                               amd64        Debian Configuration Management System (C-implementation library)
ii  libdecor-0-0:amd64                     0.1.0-3build1                              amd64        client-side window decoration library
ii  libdeflate-dev:amd64                   1.10-2                                     amd64        headers for whole-buffer compression and decompression library
ii  libdeflate0:amd64                      1.10-2                                     amd64        fast, whole-buffer DEFLATE-based compression and decompression
ii  libdouble-conversion3:amd64            3.1.7-4                                    amd64        routines to convert IEEE floats to and from strings
ii  libdpkg-perl                           1.21.1ubuntu2.2                            all          Dpkg perl modules
ii  libdrm-amdgpu1:amd64                   2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-common                          2.4.113-2~ubuntu0.22.04.1                  all          Userspace interface to kernel DRM services -- common files
ii  libdrm-dev:amd64                       2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to kernel DRM services -- development files
ii  libdrm-intel1:amd64                    2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                  2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                   2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2:amd64                          2.4.113-2~ubuntu0.22.04.1                  amd64        Userspace interface to kernel DRM services -- runtime
ii  libedit2:amd64                         3.1-20210910-1build1                       amd64        BSD editline and history libraries
ii  libegl-dev:amd64                       1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- EGL development files
ii  libegl-mesa0:amd64                     23.0.4-0ubuntu1~22.04.1                    amd64        free implementation of the EGL API -- Mesa vendor library
ii  libegl1:amd64                          1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- EGL support
ii  libelf1:amd64                          0.186-1build1                              amd64        library to read and write ELF files
ii  liberror-perl                          0.17029-1                                  all          Perl module for error/exception handling in an OO-ish way
ii  libevdev2:amd64                        1.12.1+dfsg-1                              amd64        wrapper library for evdev devices
ii  libevent-2.1-7:amd64                   2.1.12-stable-1build3                      amd64        Asynchronous event notification library
ii  libevent-core-2.1-7:amd64              2.1.12-stable-1build3                      amd64        Asynchronous event notification library (core)
ii  libevent-dev                           2.1.12-stable-1build3                      amd64        Asynchronous event notification library (development files)
ii  libevent-extra-2.1-7:amd64             2.1.12-stable-1build3                      amd64        Asynchronous event notification library (extra)
ii  libevent-openssl-2.1-7:amd64           2.1.12-stable-1build3                      amd64        Asynchronous event notification library (openssl)
ii  libevent-pthreads-2.1-7:amd64          2.1.12-stable-1build3                      amd64        Asynchronous event notification library (pthreads)
ii  libexpat1:amd64                        2.4.7-1ubuntu0.2                           amd64        XML parsing C library - runtime library
ii  libexpat1-dev:amd64                    2.4.7-1ubuntu0.2                           amd64        XML parsing C library - development kit
ii  libext2fs2:amd64                       1.46.5-2ubuntu1.1                          amd64        ext2/ext3/ext4 file system libraries
ii  libfaad2:amd64                         2.10.0-2                                   amd64        freeware Advanced Audio Decoder - runtime files
ii  libfabric1:amd64                       1.11.0-3                                   amd64        libfabric communication library
ii  libffi8:amd64                          3.4.2-4                                    amd64        Foreign Function Interface library runtime
ii  libfftw3-double3:amd64                 3.3.8-2ubuntu8                             amd64        Library for computing Fast Fourier Transforms - Double precision
ii  libfido2-1:amd64                       1.10.0-1                                   amd64        library for generating and verifying FIDO 2.0 objects
ii  libflac8:amd64                         1.3.3-2ubuntu0.2                           amd64        Free Lossless Audio Codec - runtime C library
ii  libflite1:amd64                        2.2-3                                      amd64        Small run-time speech synthesis engine - shared libraries
ii  libfontconfig1:amd64                   2.13.1-4.2ubuntu5                          amd64        generic font configuration library - runtime
ii  libfreetype6:amd64                     2.11.1+dfsg-1ubuntu0.2                     amd64        FreeType 2 font engine, shared library files
ii  libfribidi0:amd64                      1.0.8-2ubuntu3.1                           amd64        Free Implementation of the Unicode BiDi algorithm
ii  libgbm1:amd64                          23.0.4-0ubuntu1~22.04.1                    amd64        generic buffer management API -- runtime
ii  libgc1:amd64                           1:8.0.6-1.1build1                          amd64        conservative garbage collector for C and C++
ii  libgcc-11-dev:amd64                    11.4.0-1ubuntu1~22.04                      amd64        GCC support library (development files)
ii  libgcc-s1:amd64                        12.3.0-1ubuntu1~22.04                      amd64        GCC support library
ii  libgcrypt20:amd64                      1.9.4-3ubuntu3                             amd64        LGPL Crypto library - runtime library
ii  libgdbm-compat4:amd64                  1.23-1                                     amd64        GNU dbm database routines (legacy support runtime version) 
ii  libgdbm6:amd64                         1.23-1                                     amd64        GNU dbm database routines (runtime version) 
ii  libgdk-pixbuf-2.0-0:amd64              2.42.8+dfsg-1ubuntu0.2                     amd64        GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                2.42.8+dfsg-1ubuntu0.2                     all          GDK Pixbuf library - data files
ii  libgfortran-11-dev:amd64               11.4.0-1ubuntu1~22.04                      amd64        Runtime library for GNU Fortran applications (development files)
ii  libgfortran5:amd64                     12.3.0-1ubuntu1~22.04                      amd64        Runtime library for GNU Fortran applications
ii  libgif-dev                             5.1.9-2build2                              amd64        library for GIF images (development)
ii  libgif7:amd64                          5.1.9-2build2                              amd64        library for GIF images (library)
ii  libgl-dev:amd64                        1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GL development files
ii  libgl1:amd64                           1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- legacy GL support
ii  libgl1-mesa-dev:amd64                  23.0.4-0ubuntu1~22.04.1                    amd64        transitional dummy package
ii  libgl1-mesa-dri:amd64                  23.0.4-0ubuntu1~22.04.1                    amd64        free implementation of the OpenGL API -- DRI modules
ii  libglapi-mesa:amd64                    23.0.4-0ubuntu1~22.04.1                    amd64        free implementation of the GL API -- shared library
ii  libgles-dev:amd64                      1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GLES development files
ii  libgles1:amd64                         1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GLESv1 support
ii  libgles2:amd64                         1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GLESv2 support
ii  libglew-dev:amd64                      2.2.0-4                                    amd64        OpenGL Extension Wrangler - development environment
ii  libglew2.2:amd64                       2.2.0-4                                    amd64        OpenGL Extension Wrangler - runtime environment
ii  libglib2.0-0:amd64                     2.72.4-0ubuntu2.2                          amd64        GLib library of C routines
ii  libglu1-mesa:amd64                     9.0.2-1                                    amd64        Mesa OpenGL utility library (GLU)
ii  libglu1-mesa-dev:amd64                 9.0.2-1                                    amd64        Mesa OpenGL utility library -- development files
ii  libglvnd-core-dev:amd64                1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- core development files
ii  libglvnd-dev:amd64                     1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- development files
ii  libglvnd0:amd64                        1.4.0-1                                    amd64        Vendor neutral GL dispatch library
ii  libglx-dev:amd64                       1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GLX development files
ii  libglx-mesa0:amd64                     23.0.4-0ubuntu1~22.04.1                    amd64        free implementation of the OpenGL API -- GLX vendor library
ii  libglx0:amd64                          1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- GLX support
ii  libgme0:amd64                          0.6.3-2                                    amd64        Playback library for video game music files - shared library
ii  libgmp10:amd64                         2:6.2.1+dfsg-3ubuntu1                      amd64        Multiprecision arithmetic library
ii  libgnutls30:amd64                      3.7.3-4ubuntu1.2                           amd64        GNU TLS library - main runtime library
ii  libgomp1:amd64                         12.3.0-1ubuntu1~22.04                      amd64        GCC OpenMP (GOMP) support library
ii  libgpac11:amd64                        2.0.0+dfsg1-2                              amd64        GPAC Project on Advanced Content - shared libraries
ii  libgpg-error0:amd64                    1.43-3                                     amd64        GnuPG development runtime library
ii  libgraphite2-3:amd64                   1.3.14-1build2                             amd64        Font rendering engine for Complex Scripts -- library
ii  libgsm1:amd64                          1.0.19-1                                   amd64        Shared libraries for GSM speech compressor
ii  libgssapi-krb5-2:amd64                 1.19.2-2ubuntu0.2                          amd64        MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgtest-dev:amd64                     1.11.0-3                                   amd64        Google's framework for writing C++ tests
ii  libgudev-1.0-0:amd64                   1:237-2build1                              amd64        GObject-based wrapper library for libudev
ii  libharfbuzz0b:amd64                    2.7.4-1ubuntu3.1                           amd64        OpenType text shaping engine (shared library)
ii  libheif-dev:amd64                      1.12.0-2build1                             amd64        ISO/IEC 23008-12:2017 HEIF file format decoder - development files
ii  libheif1:amd64                         1.12.0-2build1                             amd64        ISO/IEC 23008-12:2017 HEIF file format decoder - shared library
ii  libhogweed6:amd64                      3.7.3-1build2                              amd64        low level cryptographic library (public-key cryptos)
ii  libhwloc-dev:amd64                     2.7.0-2ubuntu1                             amd64        Hierarchical view of the machine - static libs and headers
ii  libhwloc-plugins:amd64                 2.7.0-2ubuntu1                             amd64        Hierarchical view of the machine - plugins
ii  libhwloc15:amd64                       2.7.0-2ubuntu1                             amd64        Hierarchical view of the machine - shared libs
ii  libibverbs-dev:amd64                   39.0-1                                     amd64        Development files for the libibverbs library
ii  libibverbs1:amd64                      39.0-1                                     amd64        Library for direct userspace use of RDMA (InfiniBand/iWARP)
ii  libice-dev:amd64                       2:1.0.10-1build2                           amd64        X11 Inter-Client Exchange library (development headers)
ii  libice6:amd64                          2:1.0.10-1build2                           amd64        X11 Inter-Client Exchange library
ii  libicu-dev:amd64                       70.1-2                                     amd64        Development files for International Components for Unicode
ii  libicu70:amd64                         70.1-2                                     amd64        International Components for Unicode
ii  libidn2-0:amd64                        2.3.2-2build1                              amd64        Internationalized domain names (IDNA2008/TR46) library
ii  libiec61883-0:amd64                    1.2.0-4build3                              amd64        partial implementation of IEC 61883 (shared lib)
ii  libilmbase-dev:amd64                   2.5.7-2                                    amd64        development files for IlmBase
ii  libilmbase25:amd64                     2.5.7-2                                    amd64        several utility libraries from ILM used by OpenEXR
ii  libinput-bin                           1.20.0-1ubuntu0.3                          amd64        input device management and event handling library - udev quirks
ii  libinput10:amd64                       1.20.0-1ubuntu0.3                          amd64        input device management and event handling library - shared library
ii  libisl23:amd64                         0.24-2build1                               amd64        manipulating sets and relations of integer points bounded by linear constraints
ii  libitm1:amd64                          12.3.0-1ubuntu1~22.04                      amd64        GNU Transactional Memory Library
ii  libjack-jackd2-0:amd64                 1.9.20~dfsg-1                              amd64        JACK Audio Connection Kit (libraries)
ii  libjbig-dev:amd64                      2.1-3.1ubuntu0.22.04.1                     amd64        JBIGkit development files
ii  libjbig0:amd64                         2.1-3.1ubuntu0.22.04.1                     amd64        JBIGkit libraries
ii  libjpeg-dev:amd64                      8c-2ubuntu10                               amd64        Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjpeg-turbo8:amd64                   2.1.2-0ubuntu1                             amd64        IJG JPEG compliant runtime library.
ii  libjpeg-turbo8-dev:amd64               2.1.2-0ubuntu1                             amd64        Development files for the IJG JPEG library
ii  libjpeg8:amd64                         8c-2ubuntu10                               amd64        Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjpeg8-dev:amd64                     8c-2ubuntu10                               amd64        Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjs-jquery                           3.6.0+dfsg+~3.5.13-1                       all          JavaScript library for dynamic web applications
ii  libjs-jquery-ui                        1.13.1+dfsg-1                              all          JavaScript UI library for dynamic web applications
ii  libjs-sphinxdoc                        4.3.2-1                                    all          JavaScript support for Sphinx documentation
ii  libjs-underscore                       1.13.2~dfsg-2                              all          JavaScript's functional programming helper library
ii  libjsoncpp25:amd64                     1.9.5-3                                    amd64        library for reading and writing JSON for C++
ii  libk5crypto3:amd64                     1.19.2-2ubuntu0.2                          amd64        MIT Kerberos runtime libraries - Crypto Library
ii  libkeyutils1:amd64                     1.6.1-2ubuntu3                             amd64        Linux Key Management Utilities (library)
ii  libkrb5-3:amd64                        1.19.2-2ubuntu0.2                          amd64        MIT Kerberos runtime libraries
ii  libkrb5support0:amd64                  1.19.2-2ubuntu0.2                          amd64        MIT Kerberos runtime libraries - Support library
ii  liblapack3:amd64                       3.10.0-2ubuntu1                            amd64        Library of linear algebra routines 3 - shared version
ii  liblcms2-2:amd64                       2.12~rc1-2build2                           amd64        Little CMS 2 color management library
ii  liblcms2-dev:amd64                     2.12~rc1-2build2                           amd64        Little CMS 2 color management library development headers
ii  libldap-2.5-0:amd64                    2.5.16+dfsg-0ubuntu0.22.04.1               amd64        OpenLDAP libraries
ii  liblilv-0-0:amd64                      0.24.12-2                                  amd64        library for simple use of LV2 plugins
ii  libllvm14:amd64                        1:14.0.0-1ubuntu1.1                        amd64        Modular compiler and toolchain technologies, runtime library
ii  libllvm15:amd64                        1:15.0.7-0ubuntu0.22.04.3                  amd64        Modular compiler and toolchain technologies, runtime library
ii  liblqr-1-0:amd64                       0.4.2-2.1                                  amd64        converts plain array images into multi-size representation
ii  liblsan0:amd64                         12.3.0-1ubuntu1~22.04                      amd64        LeakSanitizer -- a memory leak detector (runtime)
ii  libltdl-dev:amd64                      2.4.6-15build2                             amd64        System independent dlopen wrapper for GNU libtool
ii  libltdl7:amd64                         2.4.6-15build2                             amd64        System independent dlopen wrapper for GNU libtool
ii  liblz4-1:amd64                         1.9.3-2build2                              amd64        Fast LZ compression algorithm library - runtime
ii  liblzma-dev:amd64                      5.2.5-2ubuntu1                             amd64        XZ-format compression library - development files
ii  liblzma5:amd64                         5.2.5-2ubuntu1                             amd64        XZ-format compression library
ii  libmad0:amd64                          0.15.1b-10ubuntu1                          amd64        MPEG audio decoder library
ii  libmagickcore-6.q16-6:amd64            8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3        amd64        low-level image manipulation library -- quantum depth Q16
ii  libmagickwand-6.q16-6:amd64            8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3        amd64        image manipulation library -- quantum depth Q16
ii  libmd0:amd64                           1.0.4-1build1                              amd64        message digest functions from BSD systems - shared library
ii  libmd4c0:amd64                         0.4.8-1                                    amd64        Markdown for C
ii  libmfx1:amd64                          22.3.0-1                                   amd64        Intel Media SDK -- shared library
ii  libmount1:amd64                        2.37.2-4ubuntu3                            amd64        device mounting library
ii  libmp3lame0:amd64                      3.100-3build2                              amd64        MP3 encoding library
ii  libmpc3:amd64                          1.2.1-2build1                              amd64        multiple precision complex floating-point library
ii  libmpdec3:amd64                        2.5.1-2build2                              amd64        library for decimal floating point arithmetic (runtime library)
ii  libmpfr6:amd64                         4.1.0-3build3                              amd64        multiple precision floating-point computation
ii  libmpg123-0:amd64                      1.29.3-1build1                             amd64        MPEG layer 1/2/3 audio decoder (shared library)
ii  libmtdev1:amd64                        1.1.6-1build4                              amd64        Multitouch Protocol Translation Library - shared library
ii  libmysofa1:amd64                       1.2.1~dfsg0-1                              amd64        library to read HRTFs stored in the AES69-2015 SOFA format
ii  libncurses6:amd64                      6.3-2ubuntu0.1                             amd64        shared libraries for terminal handling
ii  libncursesw6:amd64                     6.3-2ubuntu0.1                             amd64        shared libraries for terminal handling (wide character support)
ii  libnettle8:amd64                       3.7.3-1build2                              amd64        low level cryptographic library (symmetric and one-way cryptos)
ii  libnghttp2-14:amd64                    1.43.0-1build3                             amd64        library implementing HTTP/2 protocol (shared library)
ii  libnl-3-200:amd64                      3.5.0-0.1                                  amd64        library for dealing with netlink sockets
ii  libnl-3-dev:amd64                      3.5.0-0.1                                  amd64        development library and headers for libnl-3
ii  libnl-route-3-200:amd64                3.5.0-0.1                                  amd64        library for dealing with netlink sockets - route interface
ii  libnl-route-3-dev:amd64                3.5.0-0.1                                  amd64        development library and headers for libnl-route-3
ii  libnorm1:amd64                         1.5.9+dfsg-2                               amd64        NACK-Oriented Reliable Multicast (NORM) library
ii  libnsl-dev:amd64                       1.3.0-2build2                              amd64        libnsl development files
ii  libnsl2:amd64                          1.3.0-2build2                              amd64        Public client interface for NIS(YP) and NIS+
ii  libnuma-dev:amd64                      2.0.14-3ubuntu2                            amd64        Development files for libnuma
ii  libnuma1:amd64                         2.0.14-3ubuntu2                            amd64        Libraries for controlling NUMA policy
ii  libobjc-11-dev:amd64                   11.4.0-1ubuntu1~22.04                      amd64        Runtime library for GNU Objective-C applications (development files)
ii  libobjc4:amd64                         12.3.0-1ubuntu1~22.04                      amd64        Runtime library for GNU Objective-C applications
ii  libogg0:amd64                          1.3.5-0ubuntu3                             amd64        Ogg bitstream library
ii  libopenal-data                         1:1.19.1-2build3                           all          Software implementation of the OpenAL audio API (data files)
ii  libopenal1:amd64                       1:1.19.1-2build3                           amd64        Software implementation of the OpenAL audio API (shared library)
ii  libopenexr-dev                         2.5.7-1                                    amd64        development files for the OpenEXR image library
ii  libopenexr25:amd64                     2.5.7-1                                    amd64        runtime files for the OpenEXR image library
ii  libopengl-dev:amd64                    1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- OpenGL development files
ii  libopengl0:amd64                       1.4.0-1                                    amd64        Vendor neutral GL dispatch library -- OpenGL support
ii  libopenjp2-7:amd64                     2.4.0-6                                    amd64        JPEG 2000 image compression/decompression library
ii  libopenjp2-7-dev:amd64                 2.4.0-6                                    amd64        development files for OpenJPEG, a JPEG 2000 image library
ii  libopenmpi-dev:amd64                   4.1.2-2ubuntu1                             amd64        high performance message passing library -- header files
ii  libopenmpi3:amd64                      4.1.2-2ubuntu1                             amd64        high performance message passing library -- shared library
ii  libopenmpt0:amd64                      0.6.1-1                                    amd64        module music library based on OpenMPT -- shared library
ii  libopus0:amd64                         1.3.1-0.1build2                            amd64        Opus codec runtime library
ii  libp11-kit0:amd64                      0.24.0-6build1                             amd64        library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpam-modules:amd64                   1.4.0-11ubuntu2.3                          amd64        Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                     1.4.0-11ubuntu2.3                          amd64        Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                         1.4.0-11ubuntu2.3                          all          Runtime support for the PAM library
ii  libpam0g:amd64                         1.4.0-11ubuntu2.3                          amd64        Pluggable Authentication Modules library
ii  libpango-1.0-0:amd64                   1.50.6+ds-2ubuntu1                         amd64        Layout and rendering of internationalized text
ii  libpangocairo-1.0-0:amd64              1.50.6+ds-2ubuntu1                         amd64        Layout and rendering of internationalized text
ii  libpangoft2-1.0-0:amd64                1.50.6+ds-2ubuntu1                         amd64        Layout and rendering of internationalized text
ii  libpciaccess-dev:amd64                 0.16-3                                     amd64        Generic PCI access library for X - development files
ii  libpciaccess0:amd64                    0.16-3                                     amd64        Generic PCI access library for X
ii  libpcre2-16-0:amd64                    10.39-3ubuntu0.1                           amd64        New Perl Compatible Regular Expression Library - 16 bit runtime files
ii  libpcre2-8-0:amd64                     10.39-3ubuntu0.1                           amd64        New Perl Compatible Regular Expression Library- 8 bit runtime files
ii  libpcre3:amd64                         2:8.39-13ubuntu0.22.04.1                   amd64        Old Perl 5 Compatible Regular Expression Library - runtime files
ii  libperl5.34:amd64                      5.34.0-3ubuntu1.2                          amd64        shared Perl library
ii  libpgm-5.3-0:amd64                     5.3.128~dfsg-2                             amd64        OpenPGM shared library
ii  libpixman-1-0:amd64                    0.40.0-1ubuntu0.22.04.1                    amd64        pixel-manipulation library for X and cairo
ii  libpmix-dev:amd64                      4.1.2-2ubuntu1                             amd64        Development files for the PMI Exascale library
ii  libpmix2:amd64                         4.1.2-2ubuntu1                             amd64        Process Management Interface (Exascale) library
ii  libpng-dev:amd64                       1.6.37-3build5                             amd64        PNG library - development (version 1.6)
ii  libpng16-16:amd64                      1.6.37-3build5                             amd64        PNG library - runtime (version 1.6)
ii  libpocketsphinx3:amd64                 0.8.0+real5prealpha+1-14ubuntu1            amd64        Speech recognition tool - front-end library
ii  libpostproc55:amd64                    7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library for post processing - runtime files
ii  libprocps8:amd64                       2:3.3.17-6ubuntu2                          amd64        library for accessing process information from /proc
ii  libpsl5:amd64                          0.21.0-1.2build2                           amd64        Library for Public Suffix List (shared libraries)
ii  libpsm-infinipath1                     3.3+20.604758e7-6.1                        amd64        PSM Messaging library for Intel Truescale adapters
ii  libpsm2-2                              11.2.185-1                                 amd64        Intel PSM2 library
ii  libpthread-stubs0-dev:amd64            0.4-1build2                                amd64        pthread stubs not provided by native libc, development files
ii  libpulse0:amd64                        1:15.99.1+dfsg1-1ubuntu2.1                 amd64        PulseAudio client libraries
ii  libpython3-dev:amd64                   3.10.6-1~22.04                             amd64        header files and a static library for Python (default)
ii  libpython3-stdlib:amd64                3.10.6-1~22.04                             amd64        interactive high-level object-oriented language (default python3 version)
ii  libpython3.10:amd64                    3.10.12-1~22.04.2                          amd64        Shared Python runtime library (version 3.10)
ii  libpython3.10-dev:amd64                3.10.12-1~22.04.2                          amd64        Header files and a static library for Python (v3.10)
ii  libpython3.10-minimal:amd64            3.10.12-1~22.04.2                          amd64        Minimal subset of the Python language (version 3.10)
ii  libpython3.10-stdlib:amd64             3.10.12-1~22.04.2                          amd64        Interactive high-level object-oriented language (standard library, version 3.10)
ii  libqt5core5a:amd64                     5.15.3+dfsg-2ubuntu0.2                     amd64        Qt 5 core module
ii  libqt5dbus5:amd64                      5.15.3+dfsg-2ubuntu0.2                     amd64        Qt 5 D-Bus module
ii  libqt5gui5:amd64                       5.15.3+dfsg-2ubuntu0.2                     amd64        Qt 5 GUI module
ii  libqt5network5:amd64                   5.15.3+dfsg-2ubuntu0.2                     amd64        Qt 5 network module
ii  libqt5widgets5:amd64                   5.15.3+dfsg-2ubuntu0.2                     amd64        Qt 5 widgets module
ii  libqt5x11extras5:amd64                 5.15.3-1                                   amd64        Qt 5 X11 extras
ii  libquadmath0:amd64                     12.3.0-1ubuntu1~22.04                      amd64        GCC Quad-Precision Math Library
ii  librabbitmq4:amd64                     0.10.0-1ubuntu2                            amd64        AMQP client library written in C
ii  libraw-dev:amd64                       0.20.2-2ubuntu2.22.04.1                    amd64        raw image decoder library (development files)
ii  libraw1394-11:amd64                    2.1.2-2build2                              amd64        library for direct access to IEEE 1394 bus (aka FireWire)
ii  libraw20:amd64                         0.20.2-2ubuntu2.22.04.1                    amd64        raw image decoder library
ii  librdmacm1:amd64                       39.0-1                                     amd64        Library for managing RDMA connections
ii  libreadline8:amd64                     8.1.2-1                                    amd64        GNU readline and history libraries, run-time libraries
ii  librhash0:amd64                        1.4.2-1ubuntu1                             amd64        shared library for hash functions computing
ii  librsvg2-2:amd64                       2.52.5+dfsg-3ubuntu0.2                     amd64        SAX-based renderer library for SVG files (runtime)
ii  librtmp1:amd64                         2.4+20151223.gitfa8646d.1-2build4          amd64        toolkit for RTMP streams (shared library)
ii  librubberband2:amd64                   2.0.0-2                                    amd64        audio time-stretching and pitch-shifting library
ii  libsamplerate0:amd64                   0.2.2-1build1                              amd64        Audio sample rate conversion library
ii  libsasl2-2:amd64                       2.1.27+dfsg2-3ubuntu1.2                    amd64        Cyrus SASL - authentication abstraction library
ii  libsasl2-modules-db:amd64              2.1.27+dfsg2-3ubuntu1.2                    amd64        Cyrus SASL - pluggable authentication modules (DB)
ii  libsdl2-2.0-0:amd64                    2.0.20+dfsg-2ubuntu1.22.04.1               amd64        Simple DirectMedia Layer
ii  libseccomp2:amd64                      2.5.3-2ubuntu2                             amd64        high level interface to Linux seccomp filter
ii  libselinux1:amd64                      3.3-1build2                                amd64        SELinux runtime shared libraries
ii  libsemanage-common                     3.3-1build2                                all          Common files for SELinux policy management libraries
ii  libsemanage2:amd64                     3.3-1build2                                amd64        SELinux policy management library
ii  libsensors-config                      1:3.6.0-7ubuntu1                           all          lm-sensors configuration files
ii  libsensors5:amd64                      1:3.6.0-7ubuntu1                           amd64        library to read temperature/voltage/fan sensors
ii  libsepol2:amd64                        3.3-1build1                                amd64        SELinux library for manipulating binary security policies
ii  libserd-0-0:amd64                      0.30.10-2                                  amd64        lightweight RDF syntax library
ii  libshine3:amd64                        3.1.1-2                                    amd64        Fixed-point MP3 encoding library - runtime files
ii  libsigsegv2:amd64                      2.13-1ubuntu3                              amd64        Library for handling page faults in a portable way
ii  libslang2:amd64                        2.3.2-5build4                              amd64        S-Lang programming library - runtime version
ii  libsm-dev:amd64                        2:1.2.3-1build2                            amd64        X11 Session Management library (development headers)
ii  libsm6:amd64                           2:1.2.3-1build2                            amd64        X11 Session Management library
ii  libsmartcols1:amd64                    2.37.2-4ubuntu3                            amd64        smart column output alignment library
ii  libsnappy1v5:amd64                     1.1.8-1build3                              amd64        fast compression/decompression library
ii  libsndfile1:amd64                      1.0.31-2build1                             amd64        Library for reading/writing audio files
ii  libsndio7.0:amd64                      1.8.1-1.1                                  amd64        Small audio and MIDI framework from OpenBSD, runtime libraries
ii  libsodium23:amd64                      1.0.18-1build2                             amd64        Network communication, cryptography and signaturing library
ii  libsord-0-0:amd64                      0.16.8-2                                   amd64        library for storing RDF data in memory
ii  libsoxr0:amd64                         0.1.3-4build2                              amd64        High quality 1D sample-rate conversion library
ii  libspeex1:amd64                        1.2~rc1.2-1.1ubuntu3                       amd64        The Speex codec runtime library
ii  libsphinxbase3:amd64                   0.8+5prealpha+1-13build1                   amd64        Speech recognition tool - shared library
ii  libsqlite3-0:amd64                     3.37.2-2ubuntu0.1                          amd64        SQLite 3 shared library
ii  libsratom-0-0:amd64                    0.6.8-1                                    amd64        library for serialising LV2 atoms to/from Turtle
ii  libsrt1.4-gnutls:amd64                 1.4.4-4                                    amd64        Secure Reliable Transport UDP streaming library (GnuTLS flavour)
ii  libss2:amd64                           1.46.5-2ubuntu1.1                          amd64        command-line interface parsing library
ii  libssh-4:amd64                         0.9.6-2ubuntu0.22.04.1                     amd64        tiny C SSH library (OpenSSL flavor)
ii  libssh-gcrypt-4:amd64                  0.9.6-2ubuntu0.22.04.1                     amd64        tiny C SSH library (gcrypt flavor)
ii  libssh2-1:amd64                        1.10.0-3                                   amd64        SSH2 client-side library
ii  libssl-dev:amd64                       3.0.2-0ubuntu1.10                          amd64        Secure Sockets Layer toolkit - development files
ii  libssl3:amd64                          3.0.2-0ubuntu1.10                          amd64        Secure Sockets Layer toolkit - shared libraries
ii  libstd-rust-1.66:amd64                 1.66.1+dfsg0ubuntu1-0ubuntu0.22.04.1       amd64        Rust standard libraries
ii  libstd-rust-dev:amd64                  1.66.1+dfsg0ubuntu1-0ubuntu0.22.04.1       amd64        Rust standard libraries - development files
ii  libstdc++-11-dev:amd64                 11.4.0-1ubuntu1~22.04                      amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++6:amd64                       12.3.0-1ubuntu1~22.04                      amd64        GNU Standard C++ Library v3
ii  libswresample3:amd64                   7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library for audio resampling, rematrixing etc. - runtime files
ii  libswscale5:amd64                      7:4.4.2-0ubuntu0.22.04.1                   amd64        FFmpeg library for image scaling and various conversions - runtime files
ii  libsystemd0:amd64                      249.11-0ubuntu3.9                          amd64        systemd utility library
ii  libtasn1-6:amd64                       4.18.0-4build1                             amd64        Manage ASN.1 structures (runtime)
ii  libtcl8.6:amd64                        8.6.12+dfsg-1build1                        amd64        Tcl (the Tool Command Language) v8.6 - run-time library files
ii  libthai-data                           0.1.29-1build1                             all          Data files for Thai language support library
ii  libthai0:amd64                         0.1.29-1build1                             amd64        Thai language support library
ii  libtheora0:amd64                       1.1.1+dfsg.1-15ubuntu4                     amd64        Theora Video Compression Codec
ii  libtiff-dev:amd64                      4.3.0-6ubuntu0.5                           amd64        Tag Image File Format library (TIFF), development files
ii  libtiff5:amd64                         4.3.0-6ubuntu0.5                           amd64        Tag Image File Format (TIFF) library
ii  libtiff5-dev:amd64                     4.3.0-6ubuntu0.5                           amd64        Tag Image File Format library (TIFF), development files (transitional package)
ii  libtiffxx5:amd64                       4.3.0-6ubuntu0.5                           amd64        Tag Image File Format (TIFF) library -- C++ interface
ii  libtinfo6:amd64                        6.3-2ubuntu0.1                             amd64        shared low-level terminfo library for terminal handling
ii  libtirpc-common                        1.3.2-2ubuntu0.1                           all          transport-independent RPC library - common files
ii  libtirpc-dev:amd64                     1.3.2-2ubuntu0.1                           amd64        transport-independent RPC library - development files
ii  libtirpc3:amd64                        1.3.2-2ubuntu0.1                           amd64        transport-independent RPC library
ii  libtk8.6:amd64                         8.6.12-1build1                             amd64        Tk toolkit for Tcl and X11 v8.6 - run-time files
ii  libtsan0:amd64                         11.4.0-1ubuntu1~22.04                      amd64        ThreadSanitizer -- a Valgrind-based detector of data races (runtime)
ii  libtwolame0:amd64                      0.4.0-2build2                              amd64        MPEG Audio Layer 2 encoding library
ii  libubsan1:amd64                        12.3.0-1ubuntu1~22.04                      amd64        UBSan -- undefined behaviour sanitizer (runtime)
ii  libucx0:amd64                          1.12.1~rc2-1                               amd64        Unified Communication X libraries
ii  libudev1:amd64                         249.11-0ubuntu3.9                          amd64        libudev shared library
ii  libudfread0:amd64                      1.1.2-1                                    amd64        UDF reader library
ii  libunistring2:amd64                    1.0-1                                      amd64        Unicode string library for C
ii  libusb-1.0-0:amd64                     2:1.0.25-1ubuntu2                          amd64        userspace USB programming library
ii  libuuid1:amd64                         2.37.2-4ubuntu3                            amd64        Universally Unique ID library
ii  libuv1:amd64                           1.43.0-1                                   amd64        asynchronous event notification library - runtime library
ii  libva-drm2:amd64                       2.14.0-1                                   amd64        Video Acceleration (VA) API for Linux -- DRM runtime
ii  libva-x11-2:amd64                      2.14.0-1                                   amd64        Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva2:amd64                           2.14.0-1                                   amd64        Video Acceleration (VA) API for Linux -- runtime
ii  libvdpau1:amd64                        1.4-3build2                                amd64        Video Decode and Presentation API for Unix (libraries)
ii  libvidstab1.1:amd64                    1.1.0-2                                    amd64        video stabilization library (shared library)
ii  libvorbis0a:amd64                      1.3.7-1build2                              amd64        decoder library for Vorbis General Audio Compression Codec
ii  libvorbisenc2:amd64                    1.3.7-1build2                              amd64        encoder library for Vorbis General Audio Compression Codec
ii  libvorbisfile3:amd64                   1.3.7-1build2                              amd64        high-level API for Vorbis General Audio Compression Codec
ii  libvpx7:amd64                          1.11.0-2ubuntu2                            amd64        VP8 and VP9 video codec (shared library)
ii  libwacom-common                        2.2.0-1                                    all          Wacom model feature query library (common files)
ii  libwacom9:amd64                        2.2.0-1                                    amd64        Wacom model feature query library
ii  libwayland-client0:amd64               1.20.0-1ubuntu0.1                          amd64        wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64               1.20.0-1ubuntu0.1                          amd64        wayland compositor infrastructure - cursor library
ii  libwayland-egl1:amd64                  1.20.0-1ubuntu0.1                          amd64        wayland compositor infrastructure - EGL library
ii  libwayland-server0:amd64               1.20.0-1ubuntu0.1                          amd64        wayland compositor infrastructure - server library
ii  libwebp-dev:amd64                      1.2.2-2ubuntu0.22.04.2                     amd64        Lossy compression of digital photographic images
ii  libwebp7:amd64                         1.2.2-2ubuntu0.22.04.2                     amd64        Lossy compression of digital photographic images
ii  libwebpdemux2:amd64                    1.2.2-2ubuntu0.22.04.2                     amd64        Lossy compression of digital photographic images.
ii  libwebpmux3:amd64                      1.2.2-2ubuntu0.22.04.2                     amd64        Lossy compression of digital photographic images
ii  libx11-6:amd64                         2:1.7.5-1ubuntu0.2                         amd64        X11 client-side library
ii  libx11-data                            2:1.7.5-1ubuntu0.2                         all          X11 client-side library
ii  libx11-dev:amd64                       2:1.7.5-1ubuntu0.2                         amd64        X11 client-side library (development headers)
ii  libx11-xcb1:amd64                      2:1.7.5-1ubuntu0.2                         amd64        Xlib/XCB interface library
ii  libx264-163:amd64                      2:0.163.3060+git5db6aa6-2build1            amd64        x264 video coding library
ii  libx265-199:amd64                      3.5-2                                      amd64        H.265/HEVC video stream encoder (shared library)
ii  libx265-dev:amd64                      3.5-2                                      amd64        H.265/HEVC video stream encoder (development files)
ii  libxapian30:amd64                      1.4.18-4                                   amd64        Search engine library
ii  libxau-dev:amd64                       1:1.0.9-1build5                            amd64        X11 authorisation library (development headers)
ii  libxau6:amd64                          1:1.0.9-1build5                            amd64        X11 authorisation library
ii  libxcb-composite0:amd64                1.14-3ubuntu3                              amd64        X C Binding, composite extension
ii  libxcb-damage0:amd64                   1.14-3ubuntu3                              amd64        X C Binding, damage extension
ii  libxcb-dri2-0:amd64                    1.14-3ubuntu3                              amd64        X C Binding, dri2 extension
ii  libxcb-dri3-0:amd64                    1.14-3ubuntu3                              amd64        X C Binding, dri3 extension
ii  libxcb-glx0:amd64                      1.14-3ubuntu3                              amd64        X C Binding, glx extension
ii  libxcb-icccm4:amd64                    0.4.1-1.1build2                            amd64        utility libraries for X C Binding -- icccm
ii  libxcb-image0:amd64                    0.4.0-2                                    amd64        utility libraries for X C Binding -- image
ii  libxcb-image0-dev:amd64                0.4.0-2                                    amd64        utility libraries for X C Binding -- image, development files
ii  libxcb-keysyms1:amd64                  0.4.0-1build3                              amd64        utility libraries for X C Binding -- keysyms
ii  libxcb-keysyms1-dev:amd64              0.4.0-1build3                              amd64        utility libraries for X C Binding -- keysyms, development files
ii  libxcb-present0:amd64                  1.14-3ubuntu3                              amd64        X C Binding, present extension
ii  libxcb-randr0:amd64                    1.14-3ubuntu3                              amd64        X C Binding, randr extension
ii  libxcb-randr0-dev:amd64                1.14-3ubuntu3                              amd64        X C Binding, randr extension, development files
ii  libxcb-render-util0:amd64              0.3.9-1build3                              amd64        utility libraries for X C Binding -- render-util
ii  libxcb-render-util0-dev:amd64          0.3.9-1build3                              amd64        utility libraries for X C Binding -- render-util
ii  libxcb-render0:amd64                   1.14-3ubuntu3                              amd64        X C Binding, render extension
ii  libxcb-render0-dev:amd64               1.14-3ubuntu3                              amd64        X C Binding, render extension, development files
ii  libxcb-shape0:amd64                    1.14-3ubuntu3                              amd64        X C Binding, shape extension
ii  libxcb-shm0:amd64                      1.14-3ubuntu3                              amd64        X C Binding, shm extension
ii  libxcb-shm0-dev:amd64                  1.14-3ubuntu3                              amd64        X C Binding, shm extension, development files
ii  libxcb-sync1:amd64                     1.14-3ubuntu3                              amd64        X C Binding, sync extension
ii  libxcb-util1:amd64                     0.4.0-1build2                              amd64        utility libraries for X C Binding -- atom, aux and event
ii  libxcb-xfixes0:amd64                   1.14-3ubuntu3                              amd64        X C Binding, xfixes extension
ii  libxcb-xinerama0:amd64                 1.14-3ubuntu3                              amd64        X C Binding, xinerama extension
ii  libxcb-xinerama0-dev:amd64             1.14-3ubuntu3                              amd64        X C Binding, xinerama extension, development files
ii  libxcb-xinput0:amd64                   1.14-3ubuntu3                              amd64        X C Binding, xinput extension
ii  libxcb-xkb-dev:amd64                   1.14-3ubuntu3                              amd64        X C Binding, XKEYBOARD extension, development files
ii  libxcb-xkb1:amd64                      1.14-3ubuntu3                              amd64        X C Binding, XKEYBOARD extension
ii  libxcb1:amd64                          1.14-3ubuntu3                              amd64        X C Binding
ii  libxcb1-dev:amd64                      1.14-3ubuntu3                              amd64        X C Binding, development files
ii  libxcomposite-dev:amd64                1:0.4.5-1build2                            amd64        X11 Composite extension library (development headers)
ii  libxcomposite1:amd64                   1:0.4.5-1build2                            amd64        X11 Composite extension library
ii  libxcursor1:amd64                      1:1.2.0-2build4                            amd64        X cursor management library
ii  libxdmcp-dev:amd64                     1:1.1.3-0ubuntu5                           amd64        X11 authorisation library (development headers)
ii  libxdmcp6:amd64                        1:1.1.3-0ubuntu5                           amd64        X11 Display Manager Control Protocol library
ii  libxext-dev:amd64                      2:1.3.4-1build1                            amd64        X11 miscellaneous extensions library (development headers)
ii  libxext6:amd64                         2:1.3.4-1build1                            amd64        X11 miscellaneous extension library
ii  libxfixes-dev:amd64                    1:6.0.0-1                                  amd64        X11 miscellaneous 'fixes' extension library (development headers)
ii  libxfixes3:amd64                       1:6.0.0-1                                  amd64        X11 miscellaneous 'fixes' extension library
ii  libxft2:amd64                          2.3.4-1                                    amd64        FreeType-based font drawing library for X
ii  libxi6:amd64                           2:1.8-1build1                              amd64        X11 Input extension library
ii  libxinerama1:amd64                     2:1.1.4-3                                  amd64        X11 Xinerama extension library
ii  libxkbcommon-dev:amd64                 1.4.0-1                                    amd64        library interface to the XKB compiler - development files
ii  libxkbcommon-x11-0:amd64               1.4.0-1                                    amd64        library to create keymaps with the XKB X11 protocol
ii  libxkbcommon-x11-dev:amd64             1.4.0-1                                    amd64        library to create keymaps with the XKB X11 protocol - development files
ii  libxkbcommon0:amd64                    1.4.0-1                                    amd64        library interface to the XKB compiler - shared library
ii  libxml2:amd64                          2.9.13+dfsg-1ubuntu0.3                     amd64        GNOME XML library
ii  libxml2-dev:amd64                      2.9.13+dfsg-1ubuntu0.3                     amd64        GNOME XML library - development files
ii  libxnvctrl0:amd64                      510.47.03-0ubuntu1                         amd64        NV-CONTROL X extension (runtime library)
ii  libxrandr2:amd64                       2:1.5.2-1build1                            amd64        X11 RandR extension library
ii  libxrender-dev:amd64                   1:0.9.10-1build4                           amd64        X Rendering Extension client library (development files)
ii  libxrender1:amd64                      1:0.9.10-1build4                           amd64        X Rendering Extension client library
ii  libxshmfence1:amd64                    1.3-1build4                                amd64        X shared memory fences - shared library
ii  libxss1:amd64                          1:1.2.3-1build2                            amd64        X11 Screen Saver extension library
ii  libxt-dev:amd64                        1:1.2.1-1                                  amd64        X11 toolkit intrinsics library (development headers)
ii  libxt6:amd64                           1:1.2.1-1                                  amd64        X11 toolkit intrinsics library
ii  libxv1:amd64                           2:1.0.11-1build2                           amd64        X11 Video extension library
ii  libxvidcore4:amd64                     2:1.3.7-1                                  amd64        Open source MPEG-4 video codec (library)
ii  libxxf86vm1:amd64                      1:1.1.4-1build3                            amd64        X11 XFree86 video mode extension library
ii  libxxhash0:amd64                       0.8.1-1                                    amd64        shared library for xxhash
ii  libzimg2:amd64                         3.0.3+ds1-1                                amd64        scaling, colorspace, depth conversion library (shared library)
ii  libzmq5:amd64                          4.3.4-2                                    amd64        lightweight messaging kernel (shared library)
ii  libzstd1:amd64                         1.4.8+dfsg-3build1                         amd64        fast lossless compression algorithm
ii  libzvbi-common                         0.2.35-19                                  all          Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0:amd64                         0.2.35-19                                  amd64        Vertical Blanking Interval decoder (VBI) - runtime files
ii  linux-libc-dev:amd64                   5.15.0-83.92                               amd64        Linux Kernel Headers for development
ii  llvm-14-linker-tools                   1:14.0.0-1ubuntu1.1                        amd64        Modular compiler and toolchain technologies - Plugins
ii  login                                  1:4.8.1-2ubuntu2.1                         amd64        system login tools
ii  logsave                                1.46.5-2ubuntu1.1                          amd64        save the output of a command in a log file
ii  lsb-base                               11.1.0ubuntu4                              all          Linux Standard Base init script functionality
ii  lto-disabled-list                      24                                         all          list of packages not to build with LTO
ii  m4                                     1.4.18-5ubuntu2                            amd64        macro processing language
ii  make                                   4.3-4.1build1                              amd64        utility for directing compilation
ii  mawk                                   1.3.4.20200120-3                           amd64        Pattern scanning and text processing language
ii  media-types                            7.0.0                                      all          List of standard media types and their usual file extension
ii  mesa-common-dev:amd64                  23.0.4-0ubuntu1~22.04.1                    amd64        Developer documentation for Mesa
ii  mount                                  2.37.2-4ubuntu3                            amd64        tools for mounting and manipulating filesystems
ii  mpi-default-bin                        1.14                                       amd64        Standard MPI runtime programs (metapackage)
ii  mpi-default-dev                        1.14                                       amd64        Standard MPI development files (metapackage)
ii  nasm                                   2.15.05-1                                  amd64        General-purpose x86 assembler
ii  ncurses-base                           6.3-2ubuntu0.1                             all          basic terminal type definitions
ii  ncurses-bin                            6.3-2ubuntu0.1                             amd64        terminal-related programs and man pages
ii  ninja-build                            1.10.1-1                                   amd64        small build system closest in spirit to Make
ii  ocl-icd-libopencl1:amd64               2.2.14-3                                   amd64        Generic OpenCL ICD Loader
ii  openmpi-bin                            4.1.2-2ubuntu1                             amd64        high performance message passing library -- binaries
ii  openmpi-common                         4.1.2-2ubuntu1                             all          high performance message passing library -- common files
ii  openssh-client                         1:8.9p1-3ubuntu0.3                         amd64        secure shell (SSH) client, for secure access to remote machines
ii  openssl                                3.0.2-0ubuntu1.10                          amd64        Secure Sockets Layer toolkit - cryptographic utility
ii  passwd                                 1:4.8.1-2ubuntu2.1                         amd64        change and administer password and group data
ii  patch                                  2.7.6-7build2                              amd64        Apply a diff file to an original
ii  perl                                   5.34.0-3ubuntu1.2                          amd64        Larry Wall's Practical Extraction and Report Language
ii  perl-base                              5.34.0-3ubuntu1.2                          amd64        minimal Perl system
ii  perl-modules-5.34                      5.34.0-3ubuntu1.2                          all          Core Perl modules
ii  pkg-config                             0.29.2-1ubuntu3                            amd64        manage compile and link flags for libraries
ii  procps                                 2:3.3.17-6ubuntu2                          amd64        /proc file system utilities
ii  pybind11-dev                           2.9.1-2                                    all          seamless operability between C++11 and Python
ii  python3                                3.10.6-1~22.04                             amd64        interactive high-level object-oriented language (default python3 version)
ii  python3-dev                            3.10.6-1~22.04                             amd64        header files and a static library for Python (default)
ii  python3-distutils                      3.10.8-1~22.04                             all          distutils package for Python 3.x
ii  python3-lib2to3                        3.10.8-1~22.04                             all          Interactive high-level object-oriented language (lib2to3)
ii  python3-minimal                        3.10.6-1~22.04                             amd64        minimal subset of the Python language (default python3 version)
ii  python3-pip                            22.0.2+dfsg-1ubuntu0.3                     all          Python package installer
ii  python3-pip-whl                        22.0.2+dfsg-1ubuntu0.3                     all          Python package installer (pip wheel)
ii  python3-pkg-resources                  59.6.0-1.2ubuntu0.22.04.1                  all          Package Discovery and Resource Access using pkg_resources
ii  python3-pybind11                       2.9.1-2                                    all          pybind11 helper module for Python 3
ii  python3-setuptools                     59.6.0-1.2ubuntu0.22.04.1                  all          Python3 Distutils Enhancements
ii  python3-setuptools-whl                 59.6.0-1.2ubuntu0.22.04.1                  all          Python Distutils Enhancements (wheel package)
ii  python3-tk:amd64                       3.10.8-1~22.04                             amd64        Tkinter - Writing Tk applications with Python 3.x
ii  python3-venv                           3.10.6-1~22.04                             amd64        venv module for python3 (default python3 version)
ii  python3-wheel                          0.37.1-2ubuntu0.22.04.1                    all          built-package format for Python
ii  python3.10                             3.10.12-1~22.04.2                          amd64        Interactive high-level object-oriented language (version 3.10)
ii  python3.10-dev                         3.10.12-1~22.04.2                          amd64        Header files and a static library for Python (v3.10)
ii  python3.10-minimal                     3.10.12-1~22.04.2                          amd64        Minimal subset of the Python language (version 3.10)
ii  python3.10-venv                        3.10.12-1~22.04.2                          amd64        Interactive high-level object-oriented language (pyvenv binary, version 3.10)
ii  qt5dxcb-plugin:amd64                   5.0.46+git20220314-1                       amd64        Qt platform theme integration plugin for DDE
ii  readline-common                        8.1.2-1                                    all          GNU readline and history libraries, common files
ii  rpcsvc-proto                           1.4.2-0ubuntu6                             amd64        RPC protocol compiler and definitions
ii  rustc                                  1.66.1+dfsg0ubuntu1-0ubuntu0.22.04.1       amd64        Rust systems programming language
ii  sed                                    4.8-1ubuntu2                               amd64        GNU stream editor for filtering/transforming text
ii  sensible-utils                         0.0.17                                     all          Utilities for sensible alternative selection
ii  shared-mime-info                       2.1-2                                      amd64        FreeDesktop.org shared MIME database and spec
ii  sysvinit-utils                         3.01-1ubuntu1                              amd64        System-V-like utilities
ii  tar                                    1.34+dfsg-1ubuntu0.1.22.04.1               amd64        GNU version of the tar archiving utility
ii  tk8.6-blt2.5                           2.5.3+dfsg-4.1build2                       amd64        graphics extension library for Tcl/Tk - library
ii  tzdata                                 2023c-0ubuntu0.22.04.2                     all          time zone and daylight-saving time data
ii  ubuntu-keyring                         2021.03.26                                 all          GnuPG keys of the Ubuntu archive
ii  ucf                                    3.0043                                     all          Update Configuration File(s): preserve user changes to config files
ii  unzip                                  6.0-26ubuntu3.1                            amd64        De-archiver for .zip files
ii  usrmerge                               25ubuntu2                                  all          Convert the system to the merged /usr directories scheme
ii  util-linux                             2.37.2-4ubuntu3                            amd64        miscellaneous system utilities
ii  wget                                   1.21.2-2ubuntu1                            amd64        retrieves files from the web
ii  x11-common                             1:7.7+23ubuntu2                            all          X Window System (X.Org) infrastructure
ii  x11proto-dev                           2021.5-1                                   all          X11 extension protocols and auxiliary headers
ii  xkb-data                               2.33-1                                     all          X Keyboard Extension (XKB) configuration data
ii  xorg-sgml-doctools                     1:1.11-1.1                                 all          Common tools for building X.Org SGML documentation
ii  xtrans-dev                             1.4.0-1                                    all          X transport library (development files)
ii  xz-utils                               5.2.5-2ubuntu1                             amd64        XZ-format compression utilities
ii  yasm                                   1.3.0-2.1                                  amd64        modular assembler with multiple syntaxes support
ii  zlib1g:amd64                           1:1.2.11.dfsg-2ubuntu9.2                   amd64        compression library - runtime
ii  zlib1g-dev:amd64                       1:1.2.11.dfsg-2ubuntu9.2                   amd64        compression library - development
```

### X Server

The [X410](https://x410.dev/) is recommended.

If you want to use the [VcXsrv](https://sourceforge.net/projects/vcxsrv/), please change the environment variable `DISPLAY`.

## Appendix A pyenv-win

### Install

```powershell
pip install pyenv-win --target "$env:USERPROFILE/.pyenv"
[System.Environment]::SetEnvironmentVariable("PYENV", "$env:USERPROFILE\.pyenv\pyenv-win", "Machine")
$modifiedSystemPath = [System.Environment]::GetEnvironmentVariable("Path", "Machine")
echo $modifiedSystemPath > c:\path_backup.txt  # just in case
$modifiedSystemPath += ";$env:USERPROFILE\.pyenv\pyenv-win\bin;$env:USERPROFILE\.pyenv\pyenv-win\shims"
[System.Environment]::SetEnvironmentVariable("Path", $modifiedSystemPath, "Machine")
```
