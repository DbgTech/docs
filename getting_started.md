<!--
# Fuchsia

Pink + Purple == Fuchsia (a new Operating System)

Welcome to Fuchsia! This document has everything you need to get started with Fuchsia.

*** note
NOTE: The Fuchsia source includes
[Zircon](https://fuchsia.googlesource.com/zircon/+/master/README.md), the core platform that underpins Fuchsia. The Fuchsia build process will build Zircon as a side-effect;
to work on Zircon only, read and follow Zircon's [Getting Started](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md) doc.
***
-->

# Fuchsia

粉色 + 紫色 == Fuchsia（一个新的操作系统）

欢迎来到Fuchsia！这篇文档有你开始Fuchsia的所有信息。

*** note
注意: Fuchsia的源码包括[Zircon](https://fuchsia.googlesource.com/zircon/+/master/README.md)，Zircon是支持Fuchsia的核心平台。Zircon的编译会作为Fuchsia编译过程的附带产物；如果只想看Zircon，请阅读Zircon的[Getting Started](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md)文档。
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

If you added `.jiri_root/bin` to your path as part of getting the source code, the `fx` command should already be in your path. If not, the command is also available as `scripts/fx`.

```
fx set x64
fx full-build
```

The first command selects the build configuration you wish to build and generates the build system itself in an output directory (e.g., `out/debug-x64`).

The second command actually executes the build, transforming the source code in build products. If you modify the source tree, you can do an incremental build by re-running the `fx full-build` command alone.

Alternatively, you can use the [underlying build system directly](development/build/README.md).

#### [optional] Customize Build Environment

By default you will get a x64 debug build. You can skip this section unless you want something else.

Run `fset-usage` to see a list of build options. Some examples:

```
fx set x64                 # x64 debug build
fx set arm64               # arm64 debug build
fx set x64 --release       # x64 release build
```
-->

## 编译Fuchsia

注: 快速浏览基本的编译流程可以参考[这里](/development/workflows/build_and_pave_quickstart.md).

### 编译

如果你已经将`.jiri_root/bin`添加到环境变量作为获取源码的一部分，`fx`命令应该已经在可执行路径可以找到。如果没有，可以使用`scripts/fx`来执行命令。

```
fx set x64
fx full-build
```

第一条命令选择编译配置，即你想要编译和生成编译系统本身所在目录（即`out/debug-x64`）。

第二条命令是真正执行编译，将源码转变为产品。如果修改了源码树，重新执行`fx full-build`命令可以进行增量编译。

另一种可选的方式是直接使用[更底层的编译系统](development/build/README.md)。

<!--
#### [optional] Accelerate builds with `ccache` and `goma`

`ccache` accelerates builds by caching artifacts from previous builds. `ccache` is enabled automatically if the `CCACHE_DIR` environment variable is set and refers to a directory that exists.

[Googlers only: `goma` accelerates builds by distributing compilation across many machines.  If you have `goma` installed in `~/goma`, it is used by default. It is also used by default in preference to `ccache`.]

To override the default behaviors, pass flags to `fx set`:

```
--ccache     # force use of ccache even if goma is available
--no-ccache  # disable use of ccache
--no-goma    # disable use of goma
```
-->

#### [可选] 使用`ccache`和`goma`加速编译

`ccache`通过缓存先前编译的产物加速编译。`ccache`可以通过`CCACHE_DIR`环境变量设置来自动开启，并且引用已存的目录。

[仅限Googlers：`goma`通过分布编译到许多机器上来加速编译。如果你在`~/goma`目录安装了`goma`，默认就会使用它。如果使用了`ccache`也是会默认使用`goma`。]

通过给`fx set`命令传递标记覆盖默认的设置。

```
--ccache     # 即使goma不可用，也强制使用ccache
--no-ccache  # 关闭ccache的使用
--no-goma    # 关闭goma的使用
```

<!--
## Boot Fuchsia

### Installing and booting from hardware

To get Fuchsia running on hardware requires using the paver, which these [instructions](/development/workflows/paving.md) will help you get up and running with.

Note: A quick overview of the basic build-and-pave workflow can be found [here](/development/workflows/build_and_pave_quickstart.md).

### Boot from QEMU

If you don't have the supported hardware, you can run Fuchsia under emulation using [QEMU](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/qemu.md). Fuchsia includes prebuilt binaries for QEMU under `buildtools/qemu`.

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
-->

## 引导Fuchsia

### 安装并从硬件引导

要想让Fuchsia在硬件上运行需要使用paver，参考[这份说明](/development/workflows/paving.md)帮你在硬件上建立起系统并运行。

> 注：基本的编译安排流程的快速浏览可以在[这里](/development/workflows/build_and_pave_quickstart.md)找到。

### 从QEMU引导

如果你没有支持Fuchsia的硬件，你可以使用[QEMU](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/qemu.md)在模拟器上运行。Fuchsia中包含了预编译的QEMU二进制文件，在`buildtools/qemu`目录下。

命令`fx run`会在QEMU中使用本地编译的磁盘映像启动Zircon。

```
fx run
```

`fx run`命令有很多参数用于控制QEMU的配置：
* `-m` 设置QEMU的内存大小，单位MB。
* `-g` 开启图形界面（参考下面文档）。
* `-N` 开启网络（参考下面文档）。

使用`fx run -h`命令查看所有可用的选项。

<!--
#### QEMU tips

* `ctrl+a x` will exit QEMU in text mode.
* `ctrl+a ?` or `ctrl+a h` prints all supported commands.

#### Enabling Graphics

Note: Graphics under QEMU are extremely limited due to a lack of Vulkan support. Only the Zircon UI renders.

To enable graphics under QEMU, add the `-g` flag to `fx run`:

```
fx run -g
```
-->

#### QEMU小贴士

* `ctrl+a x`在文字模式会推出QEMU。
* `ctrl+a ?` 或 `ctrl+a h` 打印所有支持的命令。

#### 开启图形界面

注: 在QEMU下的图形界面显示非常有限，只有Zircon的UI渲染器，这与缺乏Vulkan支持有关。

开启QEMU下的图形界面，直接在`fx run`命令后添加`-g`选项即可。

```
fx run -g
```

<!--
#### Enabling Network

First, [configure](https://fuchsia.googlesource.com/zircon/+/master/docs/qemu.md#Enabling-Networking-under-QEMU) a virtual interface for QEMU's use.

Once this is done you can add the `-N` and `-u` flags to `fx run`:

```
fx run -N -u $FUCHSIA_SCRIPTS_DIR/start-dhcp-server.sh
```

The `-u` flag runs a script that sets up a local DHCP server and NAT to configure the IPv4 interface and routing.

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
-->

#### 开启网络

首先，为QEMU使用网络[配置](https://fuchsia.googlesource.com/zircon/+/master/docs/qemu.md#Enabling-Networking-under-QEMU)一个虚拟网卡接口。

配置完后，可以使用添加`-N`和`-u`选项的`fx run`命令执行：

```
fx run -N -u $FUCHSIA_SCRIPTS_DIR/start-dhcp-server.sh
```

选项`-u`执行一个脚本，用于配置一个本地的DHCP服务器和NAT，配置IPv4接口和路由。

## 探索Fuchsia

当Fuchsia引导完毕，并且显示了"$"的Shell提示符，你就可以执行程序了！

例如，接收深层wisdom，运行:

```
fortune
```

关机或重新引导Fuchsia，使用`dm`命令：

```
dm help
dm shutdown
```

<!--
### Change some source

Almost everything that exists on a Fuchsia system is stored in a Fuchsia package. A typical development [workflow](/development/workflows/package_update.md) involves re-building and pushing Fuchsia packages to a development device or QEMU virtual device.

Make a change to the rolldice binary in `garnet/bin/rolldice/src/main.rs`.

In a separate shell, start the development update server, if it isn't already running:

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

Fuchsia shows multiple tabs after booting [with graphics enabled](#enabling-graphics). The currently selected tab is highlighted in yellow at the top of the screen. You can switch to the next tab using Alt-Tab on the keyboard.

- Tab zero is the console and displays the boot and component log.
- Tabs 1, 2 and 3 contain shells.
- Tabs 4 and higher contain components you've launched.

Note: to select tabs, you may need to enter "console mode". See the next section for details.
-->

### 修改一些源码

在Fuchsia系统上，几乎所有的程序都存在于Fuchsia包中。典型的开发参考[开发流程](/development/workflows/package_update.md)，其中包括重新编译Fuchsia包，上传Fuchsia包到开发设备或QEMU虚拟设备等内容。修改在`garnet/bin/rolldice/src/main.rs`中的骰子滚动程序。

如果开发更新服务器没有运行，就需要在单独的一个Shell中启动它:

```
fx serve -v
```

重新编译，并且将滚动骰子程序包推送到执行的Fuchsia设备可以使用如下命令：

```
fx build-push rolldice
```

在Fuchsia设备中的一个Shell提示符中输入如下命令，执行更新的程序包：

```
run rolldice
```

### 选择一个Tab

Fuchsia在引导后，如果[开启了图形界面](#enabling-graphics)后，它会展现多个标签。当前选中的标签会在屏幕顶部用黄色高亮。使用键盘上的`Alt-Tab`组合键切换到下一个标签。

- 标签0是控制台，显示引导和组件日志。
- 标签1，2和3包含了shells。
- 标签4以及更高编号标签包含了你启动的组件。

注: 选择标签需要进入"console mode"，详细内容参考下面一部分。

<!--
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

When you launch something that uses Mozart, uses hardware-accelerated graphics, or if you build the [default](https://fuchsia.googlesource.com/topaz/+/master/packages/default) package (which will
boot into the Fuchsia System UI), Fuchsia will enter "graphics mode", which will not display any of the text shells. In order to use the text shell, you will need to enter "console mode" by pressing Alt-Escape. In console mode, Alt-Tab will have the behavior described in the previous section, and pressing Alt-Escape again will take you back to the graphical shell.

If you would like to use a text shell inside a terminal emulator from within the graphical shell you can launch the [term](https://fuchsia.googlesource.com/topaz/+/master/app/term) by selecting the "Ask Anything" box and typing `moterm`.
-->

### 启动图形组件

QEMU不支持Vulkan，因此不能运行起来图形栈。

Fuchsia中的大部分图形组件使用[Mozart](https://fuchsia.googlesource.com/garnet/+/master/bin/ui/)系统排版器。你可以启动这些组件，通常位于`/system/apps`，例如:

```
launch spinning_square_view
```

Mozart例子应用程序的源码可以参考[这里](https://fuchsia.googlesource.com/garnet/+/master/examples/ui)。

当你启动一些使用了Mozart的程序时，就会使用硬件加速，或者如果你编译[Fuchsia默认包](https://fuchsia.googlesource.com/topaz/+/master/packages/default)（它会引导进Fuchsia的系统UI），Fuchsia会进入图形模式，这种模式下不会展现任何的文本Shell。如果要使用文本Shell，需要通过按键`Alt-Escape`进入控制台模式。在控制台模式，`Alt-Tab`键就有了前面一部分描述的行为，切换标签。通过按`Alt-Escape`键可以在此返回到图形Shell中。

如果你喜欢在终端模拟器中使用文本Shell，可以选择`Ask Anything`框，输入`moterm`启动[term](https://fuchsia.googlesource.com/topaz/+/master/app/term)。

<!--
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
-->

## 运行测试用例

编译的测试二进制程序都安装进了`/pkgfs/packages/`目录。在终端通过调用这些程序执行测试程序，比如：

```
/pkgfs/packages/ledger_tests/0/test/ledger_unittests
```

如果你想要退出Fuchsia运行，重新编译和重新运行测试程序。在其中一个终端中运行带有网络的Fuchsia，然后在另外一个终端中执行：
```
fx run-test <test name> [<test args>]
```

你可以细读[测试问答内容](development/workflows/testing_faq.md)。

## 贡献变化

* 参考[CONTRIBUTING.md](CONTRIBUTING.md)。

## 其他有帮助的文档

* [Fuchsia文档](/README.md)
* 用Zircon工作 - [拷贝文件，网络引导，查看日志以及更多功能](https://fuchsia.googlesource.com/zircon/+/master/docs/getting_started.md#Copying-files-to-and-from-Zircon)
* [系统引导组件的更多信息](https://fuchsia.googlesource.com/garnet/+/master/bin/sysmgr/)。
