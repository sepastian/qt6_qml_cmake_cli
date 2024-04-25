This repository shows how to build a QT6 desktop app based on QML, using CMake for compliation, on the command line.

Sometimes, system package managers do not offer a recent version of Qt. For example, at the time of writing, Ubuntu 22.04 included Qt 6.2.4, when the most recent version of Qt release was 6.7.1.

Thus, this exmaple uses the excellent `aqtinstall` to install a recent version of Qt before compilation. See (Dependencies)[#dependencies] below.

# Dependencies

## Install `aqtinstall`

Follow [the official docs](https://aqtinstall.readthedocs.io/en/latest/getting_started.html#installing-qt).

## Install Qt 6.7.1 for Linux Desktop

```shell
# Find the most recent version of Qt available for Linux desktops.

aqt list-qt linux desktop
# 5.9.0 ...
# :
# 6.7.0 6.7.1

# 6.7.1 is the most recent version.
# Find out, which architectures are availble for this version.

aqt list-qt linux desktop --arch 6.7.1
# linux_gcc_64

# Install Qt 6.7.1 for Linux desktop.
aqt install-qt linux desktop 6.7.1 linux-gcc-64
```

Qt 6.7.1 should now be installed in `./6.7.1/`.

# Building the App

When building, set the `CMAKE_PREFIX_PATH` to where aqtinstall installed Qt 6.7.1. In our example, that's `./6.7.1/`.

```shell
CMAKE_PREFIX_PATH=/tmp/hello/6.7.1/gcc_64/ cmake -B build/
cd build/
make -j $(nproc)
```

If everything goes well, run the app with `./myapp`.

The application show an empty window. It has been taken from [here](https://www.qt.io/blog/introduction-to-the-qml-cmake-api).
