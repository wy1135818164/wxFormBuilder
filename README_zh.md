# wxFormBuilder

[![Windows Status](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/windows.yml/badge.svg?branch=master)](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/windows.yml)
[![Linux Status](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/linux.yml/badge.svg?branch=master)](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/linux.yml)
[![macOS Status](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/macos.yml/badge.svg?branch=master)](https://github.com/wxFormBuilder/wxFormBuilder/actions/workflows/macos.yml)
wxFormBuilder是wxWidgets框架的GUI构建器。

代码生成支持[C++](https://wxwidgets.org/), [Python](https://wxpython.org/),
[Lua](https://github.com/pkulchenko/wxlua) 和 [PHP](https://github.com/wxphp/wxphp).
导出 [XRC](https://docs.wxwidgets.org/trunk/overview_xrc.html)。
为了支持额外的小部件，可以使用自定义插件。

wxFormBuilder可以在Windows、各种Linux发行版和macOS上运行。

## 下载二进制文件

* [GitHub Releases](https://github.com/wxFormBuilder/wxFormBuilder/releases)
* [GitHub CI Builds](https://github.com/wxFormBuilder/wxFormBuilder/actions)

## 从源代码安装

从源代码构建需要CMake版本3.21，如果该版本在您的操作系统的包存储库中不可用，请使用
[CMake](https://cmake.org/download/) 网站提供多种平台的二进制下载。
wxFormBuilder使用[wxWidgets](https://wxwidgets.org/) 框架本身，强烈建议使用当前稳定版本3.2.x，
以前的稳定版本3.0.X会导致多种问题，应该避免使用。

### Windows

在Windows上构建已通过 [MSVC](https://visualstudio.com), [Mingw-w64](https://mingw-w64.org) 和
[MSYS2](https://msys2.org) 支持32位和64位模式。使用MSYS2更方便一些，因为它提供了所需的功能
预编译的库和CMake可以自动找到它们。使用其他编译器时，可能需要指定库
手动位置。下面的说明使用MSYS2。

安装 MSYS2 并打开MINGW32或MINGW64 shell。

安装前提条件:

```sh
pacman -Syu
pacman -S ${MINGW_PACKAGE_PREFIX}-toolchain ${MINGW_PACKAGE_PREFIX}-cmake ${MINGW_PACKAGE_PREFIX}-make base-devel git
pacman -S ${MINGW_PACKAGE_PREFIX}-wxWidgets3.2 ${MINGW_PACKAGE_PREFIX}-boost
```

编译:

```sh
git clone --recursive https://github.com/wy1135818164/wxFormBuilder
cd wxFormBuilder
cmake -S . -B _build -G "MSYS Makefiles" --install-prefix "$PWD/_install" -DCMAKE_BUILD_TYPE=Release
cmake --build _build --config Release -j `nproc`
cmake --install _build --config Release
```

运行:

```sh
_install/wxFormBuilder
```

---

### Linux

Linux上的构建已经在Ubuntu和Fedora上进行了测试，并在64位模式下使用GCC，但应该可以在更多的发行版上运行。

#### Ubuntu

安装前提条件:

```sh
sudo apt install libwxgtk3.2-dev libwxgtk-media3.2-dev libboost-dev cmake make git
```

编译:

```sh
git clone --recursive https://github.com/wxFormBuilder/wxFormBuilder
cd wxFormBuilder
cmake -S . -B _build -G "Unix Makefiles" --install-prefix "$PWD/_install" -DCMAKE_BUILD_TYPE=Release
cmake --build _build --config Release -j `nproc`
cmake --install _build --config Release
```

运行:

```sh
_install/bin/wxformbuilder
```

#### Fedora

安装前提条件:

```sh
sudo dnf install wxGTK-devel wxGTK-media boost-devel cmake make git
```

Building:

```sh
git clone --recursive https://github.com/wxFormBuilder/wxFormBuilder
cd wxFormBuilder
cmake -S . -B _build -G "Unix Makefiles" --install-prefix "$PWD/_install" -DCMAKE_BUILD_TYPE=Release
cmake --build _build --config Release -j `nproc`
cmake --install _build --config Release
```

Running:

```sh
_install/bin/wxformbuilder
```

---

### macOS

在macOS上的构建已经在64位模式下使用Xcode和make与Clang进行了测试。可以通过[Homebrew](https://brew.sh/)安装所需的库。

安装前提条件:

```sh
brew update
brew install wxwidgets boost cmake make git
```

编译:

```sh
git clone --recursive https://github.com/wxFormBuilder/wxFormBuilder
cd wxFormBuilder
cmake -S . -B _build -G "Unix Makefiles" --install-prefix "$PWD/_install" -DCMAKE_BUILD_TYPE=Release
cmake --build _build --config Release -j `sysctl -n hw.ncpu`
cmake --install _build --config Release
```

运行:

```sh
open _install/wxFormBuilder.app
```

## Build custom plugins

For building custom wxFormBuilder plugins, refer to the [SDK documentation](./sdk/README.md).
