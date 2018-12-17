<!--
# Glossary
-->

# 术语

<!--
## Overview

The purpose of this document is to provide short definitions for a collection of technical terms used in the Fuchsia source tree.

#### Adding new definitions

- A definition should be limited to two or three sentences and deliver a high-level description of a term.
- When another non-trivial technical term needs to be employed as part of the description, consider adding a definition for that term and linking to it from the original definition.
- A definition should be complemented by a list of links to more detailed documentation and related topics.
-->

## 概述

本文的目的是为一些 Fuchsia 源码树中使用的技术术语提供简短定义。

#### 添加新的定义

- 定义应该局限于两三句话，并且是对术语的高度概括描述。
- 如果在定义中需要使用另外一个非临时技术术语，请考虑为该术语添加定义，并且将它链接到原始定义上。
- 术语定义应该由一些连接到详细文档和相关话题的链接列表作为补充。

<!--
## Terms

#### **Agent**

A component whose life cycle is not tied to any story, is a singleton in user scope, and provides services to other components. An agent can be invoked by other components or by the system in response to triggers like push notifications. An agent can provide services to components, send and receive messages, and make proposals to give suggestions to the user.

#### **AppMgr**

The Application Manager (AppMgr) is responsible for launching components and managing the namespaces in which those components run. It is the first process started in the `fuchsia` job by the [DevMgr](#DevMgr).

#### **Armadillo**

An implementation of a session shell.
- [Source](https://fuchsia.googlesource.com/topaz/+/master/shell/armadillo/)
-->

## 术语

#### **Agent**

Agent是一个组件，它的生命周期不与任何的story绑定，它在用户范围内是单例模式，给其他的组件提供的服务。Agent由其他的组件或有系统调用，用于响应一些事件触发，比如推送通知。Agent可以给组件提供服务，发送和接收消息，给用户提出建议等。

#### **AppMgr**

应用程序管理器（AppMgr）负责启动组件，管理组件运行的名字空间。它是在Fuchsia任务中被[DevMgr](#DevMgr)启动的第一个进程。

#### **Armadillo**

会话Shell的一个实现。
- [源码](https://fuchsia.googlesource.com/topaz/+/master/shell/armadillo/)

<!--
#### **Base shell**

The platform-guaranteed set of software functionality which provides a basic user-facing interface for boot, first-use, authentication, escape from and selection of session shells, and device recovery.

#### **Component**

A component is a unit of execution and accounting. It consists of a manifest file and associated code, which comes from a Fuchsia package. A component runs in a sandbox, accesses objects via its [namespace](#Namespace) and publishes objects via its export directory. [Modules](#Module) and [Agents](#Agent) are examples of components. Components are most commonly distributed inside [Fuchsia Packages](#fuchsia-package).
-->

#### **Base shell**

平台保证的软件功能集合，它为引导，用户使用，授权，退出和选择会话Shell以及设备恢复等提供了基本的面向用户的接口。

#### **Component**

组件是一个执行和记账单元。它包含了配置文件和相关的代码，这些文件来自于Fuchsia包。组件运行于沙箱中，通过[名字空间](#Namespace)访问对象，通过导出目录公开对象。[Modules](#Module)和[Agents](#Agent)都是组件的例子。组件通常在[Fuchsia包](#fuchsia-package)中分发。

<!--
#### **Component manifest**

A component manifest (.cmx) is a JSON file with the file extension `.cmx`, typically located in the package’s `meta/` directory with information that declares how to run the component and what capabilities it receives upon launch. In particular, the component manifest describes how the component is sandboxed. See [Component manifest](the-book/package_metadata.md#Component-manifest) for a detailed description.

These files end in `.cmx`, so they are also known as "cmx files".

#### **Channel**

A Channel is the fundamental IPC primitive provided by Zircon.  It is a bidirectional, datagram-like transport that can transfer small messages including [Handles](#Handle).
- [Channel Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/channel.md)
-->

#### **Component manifest**

组件配置文件（.cmx）是带有文件扩展名`.cmx`的JSON文件，它通常位于包中的`meta/`目录，用于描述如何运行组件，以及启动后它所具有的权限。特别地，组件配置文件描述了如何构建组件运行的沙箱。参考[Component manifest](the-book/package_metadata.md#Component-manifest)中更详细的介绍。

这些文件以`.cmx`为扩展名，所以他们也叫做"cmx files"。

#### **Channel**

信道是Zircon提供的基础IPC原语。它是一种双向的，基于数据报的传输，用于传输可以包含[句柄](#Handle)的小消息。
- [Channel概述](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/channel.md)

<!--
#### **DevHost**

A Device Host (DevHost) is a process containing one or more device drivers.  They are created by the Device Manager, as needed, to provide isolation between drivers for stability and security.

#### **DevMgr**

The Device Manager (DevMgr) is responsible for enumerating, loading, and managing the life cycle of device drivers, as well as low level system tasks (providing filesystem servers for the boot filesystem, launching [AppMgr]( #AppMgr), and so on).

#### **DDK**

The Driver Development Kit is the documentation, APIs, and ABIs necessary to build Zircon Device Drivers.  Device drivers are implemented as ELF shared libraries loaded by Zircon's Device Manager.
- [DDK Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/ddk/overview.md)
- [DDK includes](https://fuchsia.googlesource.com/zircon/+/master/system/ulib/ddk/include/ddk/)

#### **Driver**

A driver is a dynamic shared library which [DevMgr](#DevMgr) can load into a [DevHost](#DevHost)
and that enables, and controls one or more devices.
- [Reference](https://fuchsia.googlesource.com/zircon/+/master/docs/ddk/driver-development.md)
- [Driver Sources](https://fuchsia.googlesource.com/zircon/+/master/system/dev)
-->

#### **DevHost**

设备Host(DevHost)是包含一个或多个设备驱动程序的进程。它们由设备管理器创建，为了稳定和安全性考虑，相互之间提供了隔离。

#### **DevMgr**

设备管理器(DevMgr)负责枚举，加载和管理设备驱动程序的生命周期，也包括底层系统任务（为引导文件系统，启动[AppMgr](#AppMgr)等提供文件系统服务器)。

#### **DDK**

驱动开发包是构建Zircon设备驱动的文档，API和ABI。设备驱动被实现为ELF共享库，由Zircon的设备管理器加载。
- [DDK概述](https://fuchsia.googlesource.com/zircon/+/master/docs/ddk/overview.md)
- [DDK头文件](https://fuchsia.googlesource.com/zircon/+/master/system/ulib/ddk/include/ddk/)

#### **Driver**

驱动是动态共享库，由[DevMgr](#DevMgr)加载到[DevHost](#DevHost)进程，用于开启和控制一个或多个设备。
- [参考](https://fuchsia.googlesource.com/zircon/+/master/docs/ddk/driver-development.md)
- [Driver源码](https://fuchsia.googlesource.com/zircon/+/master/system/dev)

<!--
#### **Environment**

A container for a set of components, which provides a way to manage their lifecycle and provision services for them. All components in an environment receive access to (a subset of) the environment's services.

#### **Escher**

Graphics library for compositing user interface content. Its design is inspired by modern real-time and physically based rendering techniques though we anticipate most of the content it renders to have non-realistic or stylized qualities suitable for user interfaces.

#### **FAR**

The Fuchsia Archive Format is a container for files to be used by Zircon and Fuchsia.
- [FAR Spec](the-book/archive_format.md)
-->

#### **Environment**

组件集合的容器，它提供了一种管理组件生命周期和提供服务的方法。在一个环境中的所有组件可以访问环境服务的子集。

#### **Escher**

用于构成用户接口的图形库。它由现代的实时和基于物理渲染技术的灵感而设计，我们可以预料它所渲染的大部分内容都会有非现实的或具有风格化质感的用户接口。

#### **FAR**

Zircon和Fuchsia使用的Fuchsia存档格式（FAR）。
- [FAR说明](the-book/archive_format.md)

<!--
#### **fdio**

fdio is the Zircon IO Library.  It provides the implementation of posix-style open(), close(), read(), write(), select(), poll(), etc, against the RemoteIO RPC protocol.  These APIs are return-not-supported stubs in libc, and linking against libfdio overrides these stubs with functional implementations.
- [Source](https://fuchsia.googlesource.com/zircon/+/master/system/ulib/fdio/)

#### **FIDL**

The Fuchsia Interface Definition Language (FIDL) is a language for defining protocols for use over [Channels](#channel). FIDL is programming language agnostic and has bindings for many popular languages, including C, C++, Dart, Go, and Rust. This approach lets system components written in a variety of languages interact seamlessly.

#### **Flutter**

[Flutter](https://flutter.io/) is a functional-reactive user interface framework optimized for Fuchsia and is used by many system components. Flutter also runs on a variety of other platform, including Android and iOS. Fuchsia itself does not require you to use any particular language or user interface framework.

#### **Fuchsia Package**

A Fuchsia Package is a unit of software distribution. It is a collection of files, such as: manifests, metadata, zero or more executables (e.g. [Components](#component)), and assets.
-->

#### **fdio**

fdio是Zircon的`I/O`库。它提供了Posix风格的IO接口实现，包括`open()`, `close()`, `read()`, `write()`, `select()`, `poll()`等，与RemoteIO RPC协议作对比。这些API在libc中都是未实现的直接返回，在链接时使用libfdio用基础实现覆盖这些stubs。
- [源码](https://fuchsia.googlesource.com/zircon/+/master/system/ulib/fdio/)

#### **FIDL**

Fuchsia接口定义语言(FIDL)是一门语言，用于定义使用[Channels](#channel)进行通信的协议。FIDL是可编程的语言隔离的，它已经被许多流行语言绑定，包括C，`C++`，Dart，Go和Rust。这种方法使得系统可以用各种不同的语言编写的组件无缝交互。

#### **Flutter**

[Flutter](https://flutter.io/)是一个函数响应式的用户接口框架，它已经针对Fuchsia进行了优化，且已经被许多系统组件使用。Flutter也可以运行在各种其他平台上，包括Android和iOS。Fuchsia自身并不要求你使用任何特定语言或用户接口框架。

#### **Fuchsia Package**

Fuchsia包是软件分发的单元。它是文件的集合，包括配置文件，元数据，零个或多个可执行文件(比如. [Components](#component))以及软件资源。

<!--
#### **FVM**

Fuchsia Volume Manager is a partition manager providing dynamically allocated groups of blocks known as slices into a virtual block address space. The FVM partitions provide a block interface enabling filesystems to interact with it in a manner largely consistent with a regular block device.
- [Filesystems](the-book/filesystems.md)

#### **Garnet**

Garnet is one of the four layers of the Fuchsia codebase.
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/garnet/+/master)

#### **GN**

GN is a meta-build system which generates build files so that Fuchsia can be built with [Ninja](#ninja). GN is fast and comes with solid tools to manage and explore dependencies. GN files, named `BUILD.gn`, are located all over the repository.
- [Language and operation](https://gn.googlesource.com/gn/+/master/docs/language.md)
- [Reference](https://gn.googlesource.com/gn/+/master/docs/reference.md)
- [Fuchsia build overview](development/build/overview.md)
-->

#### **FVM**

Fuchsia卷管理器是一个分区管理器，它提供了动态分配块组，即虚拟块地址空间的切片。FVM分区提供了块接口，它使得文件系统以一种与常用块设备一致的方式进行交互。
- [Filesystems](the-book/filesystems.md)

#### **Garnet**

Garnet是Fuchsia代码基的四层之一。
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/garnet/+/master)

#### **GN**

GN是一种元编译系统，用于生成编译文件，这样Fuchsia就可以用[Ninja](#ninja)进行编译。GN速度快，并且带有许多管理和浏览依赖的有用工具。GN的文件以`BUILD.gn`命名，在整个源码仓库中都有。
- [语言和操作](https://gn.googlesource.com/gn/+/master/docs/language.md)
- [参考文档](https://gn.googlesource.com/gn/+/master/docs/reference.md)
- [Fuchsia编译概述](development/build/overview.md)

<!--
#### **Handle**

A Handle is how a userspace process refers to a [kernel object](#Kernel-Object). They can be passed to other processes over [Channel](#Channel)s.
- [Reference](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/handles.md)

#### **Hub**

The hub is a portal for introspection.  It enables tools to access detailed structural information about realms and component instances at runtime, such as their names, job and process ids, and published services.
- [Hub](the-book/hub.md)

#### **Jiri**

Jiri is a tool for multi-repo development. It is used to checkout the Fuchsia codebase. It supports various subcommands which makes it easy for developers to manage their local checkouts.
- [Reference](https://fuchsia.googlesource.com/jiri/+/master/README.md)
- [Sub commands](https://fuchsia.googlesource.com/jiri/+/master/README.md#main-commands-are)
- [Behaviour](https://fuchsia.googlesource.com/jiri/+/master/behaviour.md)
- [Tips and tricks](https://fuchsia.googlesource.com/jiri/+/master/howdoi.md)

#### **Job**

A Job is a [kernel object](#Kernel-Object) that groups a set of related processes, their child processes and their jobs (if any). Every process in the system belongs to a job and all jobs form a single rooted tree.
- [Job Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/job.md)
-->

#### **Handle**

句柄是用户空间引用[内核对象](#Kernel-Object)的东西。它们可以通过[Channel](#Channel)传递给其他的进程。
- [参考](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/handles.md)

#### **Hub**

Hub是反射的入口。它使得工具可以在运行时访问realms和component实例，比如它们的名字，任务和进程ID以及发布服务。
- [Hub](the-book/hub.md)

#### **Jiri**

Jiri用于多仓库开发。它用于检出Fuchsia代码库。它支持各种子命令，使得开发者可以方便管理他们本地的检出代码。
- [参考](https://fuchsia.googlesource.com/jiri/+/master/README.md)
- [子命令](https://fuchsia.googlesource.com/jiri/+/master/README.md#main-commands-are)
- [行为](https://fuchsia.googlesource.com/jiri/+/master/behaviour.md)
- [提示与技巧](https://fuchsia.googlesource.com/jiri/+/master/howdoi.md)

#### **Job**

任务是一个[内核对象](#Kernel-Object)，它将一些关联的进程，以及他们的子进程和它们的任务分为一组。系统中的每一个进程都属于一个任务，所有任务形成了单一根节点的树。
- [Job Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/job.md)


<!--
#### **Kernel Object**

A kernel object is a kernel data structure which is used to regulate access to system resources such as memory, i/o, processor time and access to other processes. Userspace can only reference kernel objects via [Handles](#Handle).
- [Reference](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/objects.md)

#### **Ledger**

[Ledger](https://fuchsia.googlesource.com/peridot/+/master/docs/ledger/README.md) is a distributed storage system for Fuchsia. Applications use Ledger either directly or through state synchronization primitives exposed by the Modular framework that are based on Ledger under-the-hood.

#### **LK**

Little Kernel (LK) is the embedded kernel that formed the core of the Zircon Kernel. LK is more microcontroller-centric and lacks support for MMUs, userspace, system calls -- features that Zircon added.
- [LK on Github](https://github.com/littlekernel/lk)
-->

#### **Kernel Object**

内核对象是一个内核数据结构，它用于平常的系统资源访问，比如内存，IO，处理器时间和访问其他的进程。用户空间只能通过[Handles](#Handle)引用内核对象。
- [参考](https://fuchsia.googlesource.com/zircon/+/HEAD/docs/objects.md)

#### **Ledger**

[Ledger](https://fuchsia.googlesource.com/peridot/+/master/docs/ledger/README.md)是Fuchsia的一个分布式的存储系统。应用程序可以直接使用或者通过状态同步原语来使用它。

#### **LK**

小内核(LK)是嵌入式内核，它形成了Zircon内核的核心。LK是微控制器使用的，缺少MMU，用户空间和系统调用支持，Zircon加入了这些支持。
- [LK on Github](https://github.com/littlekernel/lk)

<!--
#### **Maxwell**

Services to expose ambient and task-related context, suggestions and infrastructure for leveraging machine intelligence.

#### **Module**

A component with a `module` metadata file which primarily describes the Module's data compatibility and semantic role.

Modules show UI and participate in Stories at runtime.
- [module metadata format](https://fuchsia.googlesource.com/peridot/+/HEAD/docs/modular/manifests/module.md)

#### **Mozart**

The view subsystem. Includes views, input, compositor, and GPU service.

#### **Musl**

Fuchsia's standard C library (libc) is based on Musl Libc.
- [Source](https://fuchsia.googlesource.com/zircon/+/master/third_party/ulib/musl/)
- [Musl Homepage](https://www.musl-libc.org/)
-->

#### **Maxwell**

用于导出周边和任务相关上下文，建议的服务以及用于平衡机器智能的基础架构。

#### **Module**

带有`module`元数据文件的组件，元数据文件描述了Module的数据兼容和原语角色。

Modules显示UI，参与运行时的Stories。
- [module元数据格式](https://fuchsia.googlesource.com/peridot/+/HEAD/docs/modular/manifests/module.md)

#### **Mozart**

子系统的视图，包括视图，输入，输出排版和GPU服务。

#### **Musl**

Fuchsia的标准C库基于Musl Libc。
- [源码](https://fuchsia.googlesource.com/zircon/+/master/third_party/ulib/musl/)
- [Musl主页](https://www.musl-libc.org/)

<!--
#### **Namespace**

A namespace is the composite hierarchy of files, directories, sockets, [service](#Service)s, and other named objects which are offered to components by their [environment](#Environment).
- [Fuchsia Namespace Spec](the-book/namespaces.md)

#### **Netstack**

TODO(tkilbourn): add definition.

#### **Ninja**

Ninja is the build system executing Fuchsia builds. It is a small build system with a strong emphasis on speed. Unlike other systems, Ninja files are not supposed to be manually written but should be generated by other systems, such as [GN](#gn) in Fuchsia.
- [Manual](https://ninja-build.org/manual.html)
- [Ninja rules in GN](https://gn.googlesource.com/gn/+/master/docs/reference.md#ninja_rules)
- [Fuchsia build overview](development/build/overview.md)

#### **Package**

Package is an overloaded term. Package may refer to a [Fuchsia Package](#fuchsia-package) or a [GN build package](#GN).

#### **Paver**

A tool in Zircon that installs partition images to internal storage of a device.
- [Guide for installing Fuchsia with paver](/development/workflows/paving.md).
-->

#### **Namespace**

名字空间是文件，目录，套接字和[服务](#Service)组织的层次。其他的命名对象都是由它们[环境](#Environment)的组件提供。
- [Fuchsia名字空间描述](the-book/namespaces.md)

#### **Netstack**

TODO(tkilbourn): 加入定义。

#### **Ninja**

Ninja是执行Fuchsia编译的编译系统。它是一个增强速度的小型编译系统。与其他的系统不同，Ninja文件并不是手动编写，它们都是其他系统，比如Fuchsia中的[GN](#gn)，自动生成的。
- [手册](https://ninja-build.org/manual.html)
- [GN中的Ninja规则](https://gn.googlesource.com/gn/+/master/docs/reference.md#ninja_rules)
- [Fuchsia编译概述](development/build/overview.md)

#### **Package**

包是一个重载的属于，Package可能指[Fuchsia包](#fuchsia-package)或[GN编译包](#GN).

#### **Paver**

Zircon中的一个安装分区映像的到设备内部存储的工具。
- [使用Paver安装Fuchsia的指南](/development/workflows/paving.md).

<!--
#### **Peridot**

Peridot is one of the four layers of the Fuchsia codebase.
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/peridot/+/master)

#### **Realm**

Synonym for [environment](#environment).

#### **RemoteIO**

RemoteIO is the Zircon RPC protocol used between fdio (open/close/read/write/ioctl) and filesystems, device drivers, etc.  As part of [FIDL](#FIDL) v2, it will become a set of FIDL Interfaces (File, Directory, Device, ...) allowing easier interoperability, and more flexible asynchronous IO for clients or servers.

#### **Service**

A service is an implementation of a [FIDL](#FIDL) interface. Components can offer their creator a set of services, which the creator can either use directly or offer to other components.

Services can also be obtained by interface name from a [Namespace](#namespace), which lets the component that created the namespace pick the implementation of the interface. Long-running services, such as [Mozart](#mozart), are typically obtained through a [Namespace](#namespace), which lets many clients connect to a common implementation.
-->

#### **Peridot**

Peridot是Fuchsia代码基的四层之一。
- [Fuchsia层蛋糕介绍](development/source_code/layers.md)
- [源码](https://fuchsia.googlesource.com/peridot/+/master)

#### **Realm**

与[environment](#environment)是同义词。

#### **RemoteIO**

RemoteIO是Zircon用于fdio(open/close/read/write/ioctl)，文件系统，设备驱动等之间的RPC协议。作为[FIDL](#FIDL)第二版本的一部分，它将会变成FIDL接口(File, Directory, Device, ...)的一部分，允许客户程序和服务器程序执行更容易的互操作性和更加灵活的异步`I/O`。

#### **Service**

服务是[FIDL](#FIDL)接口的一个实现。组件可以提供给他们创建者一个服务集合，创建者既可以直接使用也可以提供给他们的组件。

服务可以从[名字空间](#namespace)通过接口名字获取，这使得创建命名空间的组件实现接口。长期运行服务，例如[Mozart](#mozart)，通常通过[Namespace](#namespace)获取，这使得许多客户端连接到一个共同实现上。

<!--
#### **Story**

A user-facing logical container encapsulating human activity, satisfied by one or more related modules. Stories allow users to organize activities in ways they find natural, without developers having to imagine all those ways ahead of time.

#### **Story Shell**

The system responsible for the visual presentation of a story. Includes the presenter component, plus structure and state information read from each story.

#### **Topaz**

Topaz is one of the four layers of the Fuchsia codebase.
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/topaz/+/master)

#### **Session Shell**

The replaceable set of software functionality that works in conjunction with devices to create an environment in which people can interact with mods, agents and suggestions.
-->

#### **Story**

封装了人可读的Activity的用户逻辑接口容器，由一个或多个相关模块组成。故事允许用户按照他们认为自然的形式组织Activity，不需要开发者必须提前想象这些动作。

#### **Story Shell**

系统负责故事的视觉展现。包括展现者组件，以及从每一个故事读取的结构和状态信息。

#### **Topaz**

Topaz是Fuchsia代码基的四层之一。
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/topaz/+/master)

#### **Session Shell**

软件功能的可替代集合，它与创建与人交互的模块，Agent和提醒的环境的设备结合使用。

<!--
#### **VDSO**

The VDSO is a Virtual Shared Library -- it is provided by the [Zircon](#Zircon) kernel and does not appear in the filesystem or a package.  It provides the Zircon System Call API/ABI to userspace processes in the form of an ELF library that's "always there." In the Fuchsia SDK and [Zircon DDK] (#DDK) it exists as `libzircon.so` for the purpose of having something to pass to the linker representing the VDSO.

#### **VMAR**

A Virtual Memory Address Range is a Zircon [kernel object](#Kernel-Object) that controls where and how VMOs may be mapped into the address space of a process.
- [VMAR Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/vm_address_region.md)

#### **VMO**

A Virtual Memory Object is a Zircon [kernel object](#Kernel-Object) that represents a collection of pages (or the potential for pages) which may be read, written, mapped into the address space of a process, or shared with another process by passing a [Handle](#Handle) over a [Channel](#Channel).
- [VMO Overview](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/vm_object.md)

#### **Zedboot** ####

Zedboot is a recovery image that is used to install and boot a full Fuchsia system. Zedboot is actually an instance of the Zircon kernel with a minimal set of drivers and services running used to bootstrap a complete Fuchsia system on a target device. Upon startup, Zedboot listens on the network for instructions from a bootserver which may instruct Zedboot to [install](#paver) a new OS. Upon completing the installation Zedboot will reboot into the newly installed system.
-->

#### **VDSO**

VDSO是虚拟共享库--由[Zircon](#Zircon)内核提供，不会出现在文件爱你系统或包中。它以总是存在的ELF库形式向用户空间提供了Zircon系统调用`API/ABI`。在Fuchsia SDK和[Zircon DDK](#DDK)中，它以`libzircon.so`形式存在，用于给链接器传递代表VDSO的一些东西。

#### **VMAR**

虚拟内存地址区是Zircon的[内核对象](#Kernel-Object)，它控制了VMO如何已经映射到进程地址空间的什么位置。
- [VMAR概述](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/vm_address_region.md)

#### **VMO**

虚拟内存对象是Zircon的[内核对象](#Kernel-Object)，它代表了一系列的可读，可写并且映射到进程地址空间的内存页（或者页面可能性），或者是与其他的进程共享的内存页，可以用[Handle](#Handle)表示，并且通过[Channel](#Channel)进行进程间传递。
- [VMO概述](https://fuchsia.googlesource.com/zircon/+/master/docs/objects/vm_object.md)

#### **Zedboot** ####

Zedboot是一个恢复映像，它用于安装和引导完整的Fuchsia系统。Zedboot实际上是带有最小驱动和服务集合的Zircon内核实例，用于在目标设备上引导一个完整的Fuchsia系统。在启动中，Zedboot监听来自引导服务器的网络指令，他会指导Zedboot[安装](#paver)一个新的系统。一旦完成了安装，Zedboot会重新引导进入新安装的系统中。

<!--
#### **Zircon**

Zircon is the [microkernel](https://en.wikipedia.org/wiki/Microkernel) and lowest level userspace components (driver runtime environment, core drivers, libc, etc) at the core of Fuchsia.  In a traditional monolithic kernel, many of the userspace components of Zircon would be part of the kernel itself. Zircon is also one of the four layers of the Fuchsia codebase.
- [Zircon Documentation](https://fuchsia.googlesource.com/zircon/+/master/README.md)
- [Zircon Concepts](https://fuchsia.googlesource.com/zircon/+/master/docs/concepts.md)
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/zircon/+/master)

#### **ZX**

ZX is an abbreviation of "Zircon" used in Zircon C APIs/ABIs (`zx_channel_create()`, `zx_handle_t`, `ZX_EVENT_SIGNALED`, etc) and libraries (libzx in particular).

#### **ZXDB**

The native low-level system debugger.
- [Reference](https://fuchsia.googlesource.com/garnet/+/master/docs/debugger.md)
-->

#### **Zircon**

Zircon是Fuchsia核心的一个[微内核](https://en.wikipedia.org/wiki/Microkernel)和底层用户空间组件（驱动运行时环境，核心驱动，libc等）。在传统的宏内核中，Zircon的许多用户空间组件会是内核的组成部分。Zircon也是Fuchsia代码基中的四层之一。
- [Zircon Documentation](https://fuchsia.googlesource.com/zircon/+/master/README.md)
- [Zircon Concepts](https://fuchsia.googlesource.com/zircon/+/master/docs/concepts.md)
- [The Fuchsia layer cake](development/source_code/layers.md)
- [Source](https://fuchsia.googlesource.com/zircon/+/master)

#### **ZX**

ZX是用于Zircon C APIs/ABIs(`zx_channel_create()`, `zx_handle_t`, `ZX_EVENT_SIGNALED`等)以及库(特别是libzx)中的`Zircon`的简写。

#### **ZXDB**

本地的底层系统调试器。
- [参考](https://fuchsia.googlesource.com/garnet/+/master/docs/debugger.md)
