---
title: 使用 Unreal Insights 进行分析
description: 了解如何在 HoloLens 2 上使用 Unreal Insights。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，开发，分析，Unreal insights，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779361"
---
# <a name="profiling-with-unreal-insights"></a>使用 Unreal Insights 进行分析

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html)是一种分析系统，用于从 Unreal 引擎收集、分析和可视化数据。 分析系统可以帮助你找到优化瓶颈，以及你的应用程序性能可以使用提升的区域。 通常情况下，你可以从编辑器 Insights 直接启用 Unreal，但对于 HoloLens 2，你将需要使用命令行。

## <a name="setup"></a>设置

Unreal 使你能够使用启用 Unreal Insights 的命令行参数在 HoloLens 启动器中创建和配置 "自定义配置文件"。

1. 在命令提示符下使用 **ipconfig** 命令查找计算机的 IP 地址。 IP 地址是由 ipconfig 列出的 IPv4 地址。 请记住，稍后在设置命令行参数时，请记住这一点。

> [!IMPORTANT]
> 如果你使用的是 VPN，你可能需要提供通过 VPN 提供的 IP 地址。

![Ipconfig 命令的命令行结果的屏幕截图](images/unreal-insights-img-01.png)

2. 从主编辑器窗口中的 "编辑" 工具栏打开 **Project 设置**。

![突出显示 Project 设置编辑下拉列表的屏幕截图](images/unreal-insights-img-15.png)

3. 向下滚动左侧面板，直到找到 "**平台**" 标题并选择 " **HoloLens**"。

![HoloLens 突出显示 Project 设置左面板中 "平台" 部分的屏幕截图](images/unreal-insights-img-15.png)

4. 确认 " **功能** " 部分已选中 "internet 客户端"、"Internet 客户端服务器" 和 "专用网络客户端服务器"。

![选择 Internet 客户端、Internet 客户端服务器和专用网络客户端服务器的功能选项的屏幕截图](images/unreal-insights-img-14.png)

## <a name="launch"></a>启动

1. 从 "**启动**" 按钮下的 UE4 面板打开 **Project Launcher** ：

![突出显示项目启动器的启动选项的屏幕截图](images/unreal-insights-img-07.png)

2. 选择 " **+** **自定义启动配置文件**" 下的按钮以创建自定义配置文件。 创建后，你始终可以在以后编辑此配置文件：

![突出显示自定义启动配置文件的项目启动器的屏幕截图](images/unreal-insights-img-08.png)

3. 在 HoloLens 自定义启动配置文件上选择 "**编辑配置文件**" 按钮。 在 " **生成** " 部分中，选中 " **生成 UAT** " 并设置 **其他命令行参数**。
   - 对于初学者，请尝试以下操作： **-tracehost = IP_OF_YOUR_PC 跟踪 = 日志、书签、框架、CPU、GPU、LoadTime、文件、网络**
   - 可以在 " [Unreal Insights 参考" 文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用启动参数的完整列表。

> [!NOTE]
> "IP_OF_YOUR_PC" 是我们在步骤1中找到的 IP 地址。 这是运行 Unreal 的计算机的 ip 地址 Insights，而不是 HoloLens 的 ip 地址。

> [!IMPORTANT]
> 跟踪可能会非常快。 只启用那些需要使跟踪大小保持较低的通道。

![配置文件配置中的生成选项的屏幕截图](images/unreal-insights-img-17.png)

4. **通过书籍** 选择要复制到设备的 "**库**"。 请确保在 **加工地图** 中选择了映射。

![使用 "库" 的配置文件配置中的 "库" 选项的屏幕截图，并 HoloLens 突出显示](images/unreal-insights-img-09.png)

5. 设置 **如何将生成打包** 到 **包 & 本地存储包**。 请记下所选的文件路径，因为稍后需要用到。

![配置文件配置设置为在本地打包和存储的配置文件中的包选项的屏幕截图](images/unreal-insights-img-18.png)

6. 设置 **你希望如何将生成部署到 "** 不 **部署**"。

![部署设置为 "不部署" 的配置文件配置中部署选项的屏幕截图](images/unreal-insights-img-19.png)

8. 选择 "**上一步**" 返回到 " **Project Launcher** " 对话框的根
9. 返回编辑器中，单击自定义启动配置文件中的 " **启动** "

![自定义启动配置文件的屏幕截图](images/unreal-insights-img-13.png)

10. 在生成项目时进行监视，然后将步骤 5) 的包路径中的 .appxbundle (部署到通过设备门户 HoloLens

11. 启动 Unreal Insights。 Unreal Insights 可执行文件存储在二进制引擎文件夹中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![运行的 unreal insights 可执行文件的屏幕截图](images/unreal-insights-img-12.png)

12. 在 HoloLens 上启动应用。

## <a name="profiling"></a>分析

返回到 Unreal Insights 中，选择要开始分析的设备的 **实时** 连接

自定义配置文件在项目之间共享。 从这里开始，你可以使用你创建的自定义配置文件，而不必每次都执行此操作。 每次启动 Unreal 时，你只需在 " [设置" 部分](#setup)中通过步骤3到步骤6重新创建与设备的连接。

## <a name="see-also"></a>另请参阅

- [Unreal Insights 文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
