<!--
# Development

This document is a top-level entry point to all of Fuchsia documentation related
to **developing** Fuchsia and software running on Fuchsia.
-->

# 开发

这篇文档是所有Fuchsia文档中关于**开发**Fuchsia和运行在其上软件的文档的顶级入口点。

<!--
## Developer workflow

This sections describes the workflows and tools for building, running, testing
and debugging Fuchsia and programs running on Fuchsia.

 - [Getting started](../getting_started.md) - **start here**. This document
   covers getting the source, building and running Fuchsia.
 - [Source code](source_code/README.md)
 - [Multiple device setup](workflows/multi_device.md)
 - [Pushing a package](workflows/package_update.md)
 - [Changes that span layers](workflows/multilayer_changes.md)
 - [Debugging](workflows/debugging.md)
 - [Tracing][tracing]
 - [Trace-based Benchmarking][trace_based_benchmarking]
 - [Build system](build/README.md)
 - [Workflow FAQ](workflows/workflow_faq.md)
 - [Testing FAQ](workflows/testing_faq.md)

## Languages

 - [C/C++](languages/c-cpp/README.md)
 - [Dart](languages/dart/README.md)
 - [FIDL](languages/fidl/README.md)
 - [Go](languages/go/README.md)
 - [Rust](languages/rust/README.md)
 - [Flutter modules](languages/dart/mods.md) - how to write a graphical module
   using Flutter
-->

## 开发者流程

这一部分描述编译，运行，测试和调试Fuchsia及其程序的流程与工具。

 - [开始](../getting_started.md) - **从这里开始**。这篇文档概括了如何获取源码，编译和运行Fuchsia。
 - [源码获取](source_code/README.md)
 - [多设备设置](workflows/multi_device.md)
 - [上传软件包](workflows/package_update.md)
 - [跨层变化](workflows/multilayer_changes.md)
 - [调试](workflows/debugging.md)
 - [追踪][tracing]
 - [基于追踪的基准测试][trace_based_benchmarking]
 - [编译系统](build/README.md)
 - [流程问答](workflows/workflow_faq.md)
 - [测试问答](workflows/testing_faq.md)

## 语言

 - [C/C++](languages/c-cpp/README.md)
 - [Dart](languages/dart/README.md)
 - [FIDL](languages/fidl/README.md)
 - [Go](languages/go/README.md)
 - [Rust](languages/rust/README.md)
 - [Flutter modules](languages/dart/mods.md) - 如何使用Flutter编写图形模块。

<!--
## API

 - [System](api/system.md) - Rubric for designing the Zircon System Interface
 - [FIDL](api/fidl.md) - Rubric for designing FIDL protocols
 - [C](api/c.md) - Rubric for designing C library interfaces

## SDK

 - [SDK](sdk/README.md) - information about developing the Fuchsia SDK

## Hardware

This section covers Fuchsia development hardware targets.

 - [Acer Switch Alpha 12][acer_12]
 - [Intel NUC][intel_nuc] (also [this](hardware/developing_on_nuc.md))
 - [Pixelbook](hardware/pixelbook.md)

## Conventions

This section covers Fuchsia-wide conventions and best practices.

 - [Layers](source_code/layers.md) - the Fuchsia layer cake, ie. how Fuchsia
   subsystems are split into a stack of layers
 - [Repository structure](source_code/layer_repository_structure.md) - standard way
   of organizing code within a Fuchsia layer repository
 - [Documentation standards](/best-practices/documentation_standards.md)

## Miscellaneous

 - [CTU analysis in Zircon](workflows/ctu_analysis.md)
 - [Persistent disks in QEMU](workflows/qemu_persistent_disk.md)


[acer_12]: https://fuchsia.googlesource.com/zircon/+/master/docs/targets/acer12.md "Acer 12"
[intel_nuc]: https://fuchsia.googlesource.com/zircon/+/master/docs/targets/nuc.md "Intel NUC"
[pixelbook]: hardware/pixelbook.md "Pixelbook"
[tracing]: https://fuchsia.googlesource.com/garnet/+/master/docs/tracing_usage_guide.md
[trace_based_benchmarking]: benchmarking/trace_based_benchmarking.md
-->

## API

 - [系统](api/system.md) - 设计Zircon系统接口的规则。
 - [FIDL](api/fidl.md) - 设计FIDL协议的规则。
 - [C](api/c.md) - 设计C库接口的规则。

## SDK

 - [SDK](sdk/README.md) - 关于开发Fuchsia SDK的信息。

## 硬件

这部分描述Fuchsia开发的硬件目标有哪些。

 - [Acer Switch Alpha 12][acer_12]
 - [Intel NUC][intel_nuc] (也包括[这篇](hardware/developing_on_nuc.md))
 - [Pixelbook](hardware/pixelbook.md)

## 约定

这篇描述Fuchsia系统范围内的约定和最佳实践方法。

 - [Layers](source_code/layers.md) - Fuchsia层蛋糕，即Fuchsia子系统如何分割为分层的栈形式。
 - [仓库结构](source_code/layer_repository_structure.md) - 在Fuchsia层代码库中代码组织的标准方式。
 - [文档标准](/best-practices/documentation_standards.md)

## 杂项

 - [Zircon中的CTU分析](workflows/ctu_analysis.md)
 - [Qemu中的永久磁盘](workflows/qemu_persistent_disk.md)


[acer_12]: https://fuchsia.googlesource.com/zircon/+/master/docs/targets/acer12.md "Acer 12"
[intel_nuc]: https://fuchsia.googlesource.com/zircon/+/master/docs/targets/nuc.md "Intel NUC"
[pixelbook]: hardware/pixelbook.md "Pixelbook"
[tracing]: https://fuchsia.googlesource.com/garnet/+/master/docs/tracing_usage_guide.md
[trace_based_benchmarking]: benchmarking/trace_based_benchmarking.md
