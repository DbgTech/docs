<!--
# Fuchsia

Pink + Purple == Fuchsia (a new Operating System)

Welcome to Fuchsia! This document has everything you need to get started with
Fuchsia.

*** note
NOTE: The Fuchsia source includes
[Zircon](https://fuchsia.googlesource.com/zircon/+/master/README.md),
the core platform that underpins Fuchsia.
The Fuchsia build process will build Zircon as a side-effect;
to work on Zircon only, read and follow Zircon's
[Getting Started](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md)
doc.
***
-->

# Fuchsia

粉色 + 紫色 == Fuchsia（一个新的操作系统）

欢迎来到Fuchsia！这篇文档有你开始Fuchsia的所有信息。

*** note
注意: Fuchsia的源码包括[Zircon](https://fuchsia.googlesource.com/zircon/+/master/README.md)，Zircon是Fuchsia的核心平台。Zircon的编译会作为Fuchsia编译过程的附带产物；如果只想看Zircon，请阅读Zircon的[Getting Started](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md)文档。
***

[TOC]

<!--

## Prerequisites

### Prepare your build environment (once per build environment)

#### Debian

```
sudo apt-get install build-essential curl git python unzip
```

#### macOS

1.  Install Command Line Tools:

    ```
    xcode-select --install
    ```

1.  In addition to Command Line Tools, you also need to
    install a recent version of [Xcode](https://developer.apple.com/xcode/).
-->

## 预备知识

### 准备你的编译环境

#### Debian

```
sudo apt-get install build-essential curl git python unzip
```

#### macOS

1. 安装命令行工具。

    ```
    xcode-select --install
    ```
2. 除了安装命令行工具，你还需要安装一个最新版本的[Xcode](https://developer.apple.com/xcode/)。

<!--
## Get the Source

Follow [the instructions to get the Fuchsia source](/development/source_code/README.md)
and then return to this document.
-->

## 获取源码

参照[获取Fuchsia源码的说明](/development/source_code/README.md)获取源码，然后回到这篇文档继续阅读。

<!--
## Build Fuchsia

Note: A quick overview of the basic build-and-pave workflow can be found [here](/development/workflows/build_and_pave_quickstart.md).

### Build

If you added `.jiri_root/bin` to your path as part of getting the source code,
the `fx` command should already be in your path. If not, the command is also
available as `scripts/fx`.

```
fx set x64
fx full-build
```

The first command selects the build configuration you wish to build and
generates the build system itself in an output directory
(e.g., `out/debug-x64`).

The second command actually executes the build, transforming the source code in
build products. If you modify the source tree, you can do an incremental build
by re-running the `fx full-build` command alone.

Alternatively, you can use the [underlying build system directly](development/build/README.md).

#### [optional] Customize Build Environment

By default you will get a x64 debug build. You can skip this section unless
you want something else.

Run `fset-usage` to see a list of build options. Some examples:

```
fx set x64                 # x64 debug build
fx set arm64               # arm64 debug build
fx set x64 --release       # x64 release build
```
-->

## 编译Fuchsia

注: 快速浏览基本的编译流可以参考[这里](/development/workflows/build_and_pave_quickstart.md).

### 编译

如果你已经将`.jiri_root/bin`添加到环境变量作为获取源码的一部分，`fx`命令应该已经在可执行路径了。如果没有，可以使用`scripts/fx`来执行命令。

```
fx set x64
fx full-build
```

第一条命令选择编译配置，即你想要编译和生成编译系统本身所在目录（即`out/debug-x64`）。

第二条命令

#### [optional] Accelerate builds with `ccache` and `goma`

`ccache` accelerates builds by caching artifacts from previous builds. `ccache`
is enabled automatically if the `CCACHE_DIR` environment variable is set and
refers to a directory that exists.

[Googlers only: `goma` accelerates builds by distributing compilation across
many machines.  If you have `goma` installed in `~/goma`, it is used by default.
It is also used by default in preference to `ccache`.]

To override the default behaviors, pass flags to `fx set`:

```
--ccache     # force use of ccache even if goma is available
--no-ccache  # disable use of ccache
--no-goma    # disable use of goma
```

## Boot Fuchsia

### Installing and booting from hardware

To get Fuchsia running on hardware requires using the paver, which these
[instructions](/development/workflows/paving.md) will help you get up and running with.

Note: A quick overview of the basic build-and-pave workflow can be found [here](/development/workflows/build_and_pave_quickstart.md).

### Boot from QEMU

If you don't have the supported hardware, you can run Fuchsia under emulation
using [QEMU](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/qemu.md).
Fuchsia includes prebuilt binaries for QEMU under `buildtools/qemu`.

The `fx run` command will launch Zircon within QEMU, using the locally built
disk image:

```
fx run
```

There are various flags for `fx run` to control QEMU's configuration:
* `-m` sets QEMU's memory size in MB.
* `-g` enables graphics (see below).
* `-N` enables networking (see below).

Use `fx run -h` to see all available options.

#### QEMU tips

* `ctrl+a x` will exit QEMU in text mode.
* `ctrl+a ?` or `ctrl+a h` prints all supported commands.

#### Enabling Graphics

Note: Graphics under QEMU are extremely limited due to a lack of Vulkan
support. Only the Zircon UI renders.

To enable graphics under QEMU, add the `-g` flag to `fx run`:

```
fx run -g
```

#### Enabling Network

First, [configure](https://fuchsia.googlesource.com/zircon/+/master/docs/qemu.md#Enabling-Networking-under-QEMU)
a virtual interface for QEMU's use.

Once this is done you can add the `-N` and `-u` flags to `fx run`:

```
fx run -N -u $FUCHSIA_SCRIPTS_DIR/start-dhcp-server.sh
```

The `-u` flag runs a script that sets up a local DHCP server and NAT to
configure the IPv4 interface and routing.

## Explore Fuchsia

When Fuchsia has booted and displays the "$" shell prompt, you can run programs!

For example, to receive deep wisdom, run:

```
fortune
```

To shutdown or reboot Fuchsia, use the `dm` command:

```
dm help
dm shutdown
```

### Change some source

Almost everything that exists on a Fuchsia system is stored in a Fuchsia
package. A typical development
[workflow](/development/workflows/package_update.md)
involves re-building and pushing Fuchsia packages to a development device or
QEMU virtual device.

Make a change to the rolldice binary in `garnet/bin/rolldice/src/main.rs`.

In a separate shell, start the development update server, if it isn't already
running:

```
fx serve -v
```

Re-build and push the rolldice package to a running Fuchsia device with:

```
fx build-push rolldice
```

From a shell prompt on the Fuchsia device, run the updated package with:

```
run rolldice
```

### Select a tab

Fuchsia shows multiple tabs after booting [with graphics
enabled](#enabling-graphics). The currently selected tab is highlighted in
yellow at the top of the screen. You can switch to the next tab using Alt-Tab on
the keyboard.

- Tab zero is the console and displays the boot and component log.
- Tabs 1, 2 and 3 contain shells.
- Tabs 4 and higher contain components you've launched.

Note: to select tabs, you may need to enter "console mode". See the next section for details.

### Launch a graphical component

QEMU does not support Vulkan and therefore cannot run our graphics stack.

Most graphical components in Fuchsia use the
[Mozart](https://fuchsia.googlesource.com/garnet/+/master/bin/ui/) system compositor. You can launch
such components, commonly found in `/system/apps`, like this:

```
launch spinning_square_view
```

Source code for Mozart example apps is
[here](https://fuchsia.googlesource.com/garnet/+/master/examples/ui).

When you launch something that uses Mozart, uses hardware-accelerated graphics, or if you build
the [default](https://fuchsia.googlesource.com/topaz/+/master/packages/default) package (which will
boot into the Fuchsia System UI), Fuchsia will enter "graphics mode", which will not display any
of the text shells. In order to use the text shell, you will need to enter "console mode" by
pressing Alt-Escape. In console mode, Alt-Tab will have the behavior described in the previous
section, and pressing Alt-Escape again will take you back to the graphical shell.

If you would like to use a text shell inside a terminal emulator from within the graphical shell
you can launch the [term](https://fuchsia.googlesource.com/topaz/+/master/app/term) by selecting the
"Ask Anything" box and typing `moterm`.

## Running tests

Compiled test binaries are installed in `/pkgfs/packages/`.
You can run a test by invoking it in the terminal. E.g.

```
/pkgfs/packages/ledger_tests/0/test/ledger_unittests
```

If you want to leave Fuchsia running and recompile and re-run a test, run
Fuchsia with networking enabled in one terminal, then in another terminal, run:

```
fx run-test <test name> [<test args>]
```

You may wish to peruse the [testing FAQ](development/workflows/testing_faq.md).

## Contribute changes

* See [CONTRIBUTING.md](CONTRIBUTING.md).

## Additional helpful documents

* [Fuchsia documentation](/README.md) hub
* Working with Zircon - [copying files, network booting, log viewing, and
more](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md#Copying-files-to-and-from-Zircon)
* [Information on the system bootstrap component](https://fuchsia.googlesource.com/garnet/+/master/bin/sysmgr/).
