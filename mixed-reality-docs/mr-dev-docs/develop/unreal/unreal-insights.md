---
title: 使用 Unreal Insights 进行分析
description: 了解如何在 HoloLens 2 上使用 Unreal Insights。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，开发，分析，Unreal insights，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580837"
---
# <a name="profiling-with-unreal-insights"></a>使用 Unreal Insights 进行分析 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) 是一种分析系统，用于从 Unreal 引擎收集、分析和可视化数据。 分析系统可以帮助你找到优化瓶颈，以及你的应用程序性能可以使用提升的区域。 通常，你可以直接从编辑器中启用 Unreal Insights，但对于 HoloLens 2，你需要使用命令行。  

## <a name="setup"></a>设置

Unreal 允许你使用启用 Unreal Insights 的命令行参数在 HoloLens 启动器中创建和配置 "自定义配置文件"。

1.  在命令提示符下使用 **ipconfig** 命令查找计算机的 IP 地址。 IP 地址是由 ipconfig 列出的 IPv4 地址。 请记住，稍后在设置命令行参数时，请记住这一点。

> [!IMPORTANT]
> 如果你使用的是 VPN，你可能需要提供通过 VPN 提供的 IP 地址。

![Ipconfig 命令的命令行结果的屏幕截图](images/unreal-insights-img-01.png)

2.  在 Unreal 引擎面板的顶部，打开 "**启动**" 按钮下的 **设备管理器**：

![突出显示了 "设备管理器" 的启动选项的屏幕截图](images/unreal-insights-img-02.png)

3.  在设备管理器中，选择 " **添加未列出的设备**"：

![在 Unreal 引擎中打开设备管理器的屏幕截图](images/unreal-insights-img-03.png)

4. 单击 " **选择平台** "，然后选择 " **HoloLens**：

![突出显示了 HoloLens 的 "添加未列出的设备" 下拉列表](images/unreal-insights-img-04.png)

5.  如果使用的是 IPoverUSB，请输入127.0.0.1：10080作为设备标识符。 在相应的字段中输入 HoloLens 用户和密码，并根据需要填写 **显示名称** 。

> [!IMPORTANT]
> 设备标识符是 HoloLens 的 IP 地址，而不是在步骤1中找到的运行 Unreal Insights 的计算机的 IP 地址。

![设备管理器中的 HoloLens 设备详细信息的屏幕截图](images/unreal-insights-img-05.png)

6.  选择 " **添加** "，HoloLens 应显示在设备管理器的设备列表中：

![HoloLens 已添加到设备列表的屏幕截图](images/unreal-insights-img-06.png)

## <a name="launch"></a>启动

1. 从 "**启动**" 按钮下的 "UE4" 面板打开 **项目启动器**：

![突出显示项目启动器的启动选项的屏幕截图](images/unreal-insights-img-07.png)

2. 选择 " **+** **自定义启动配置文件**" 下的按钮以创建自定义配置文件。 创建后，你始终可以在以后编辑此配置文件：

![突出显示自定义启动配置文件的项目启动器的屏幕截图](images/unreal-insights-img-08.png)

3. 在 HoloLens 自定义启动配置文件上选择 " **编辑配置文件** " 按钮，并配置：
    * **通过书籍** 选择要复制到设备的 **库**
    * 你可能想要检查 **是否要存档？** 在 " **存档** " 部分中，保留生成的 .appxbundle 而不是 "删除" 来节省磁盘空间。 指定 .appxbundle 的位置，并根据需要切换到开发版本

![配置文件中的 "库" 选项的屏幕截图，其 "库" 为 "已突出显示"](images/unreal-insights-img-09.png)

4. 设置 **你希望如何部署生成？** 要 **复制到设备** 以激活 UI 的 **启动** 部分，请执行以下操作：

![项目启动器的屏幕截图，其中突出显示了 "复制到设备" 的部署选项](images/unreal-insights-img-10.png)

5. 设置 "**启动**" 部分中的 **其他命令行参数**。 参数将写入 ue4commandline.txt 文件中，打包到捆绑包，并在启动时使用。 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * 对于初学者，请尝试以下操作： **-tracehost = IP_OF_YOUR_PC 跟踪 = 日志、书签、框架、CPU、GPU、LoadTime、文件、网络**
    * 可以在 [Unreal Insights 参考文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用启动参数的完整列表。

> [!NOTE]
> "IP_OF_YOUR_PC" 是我们在步骤1中找到的 IP 地址。 这是运行 Unreal Insights 的计算机的 IP 地址，而不是 HoloLens 的 IP 地址。

> [!IMPORTANT]
> 跟踪可能会非常快。 只启用那些需要使跟踪大小保持较低的通道。

![启动配置选项的屏幕截图](images/unreal-insights-img-11.png)

6. 在应用启动之前启动 Unreal Insights，否则 Unreal Insights 在应用之前将无法正确初始化：
    * Unreal Insights 可执行文件存储在二进制引擎文件夹中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![运行的 unreal insights 可执行文件的屏幕截图](images/unreal-insights-img-12.png)

6.  选择 " **上一步** " 返回到 " **项目启动器** " 对话框的根
7.  返回编辑器中，单击自定义启动配置文件中的 " **启动** "

![自定义启动配置文件的屏幕截图](images/unreal-insights-img-13.png)

8.  查看项目已打包、安装在设备上并启动

## <a name="profiling"></a>分析

返回到 Unreal Insights，选择要开始分析的设备的 **实时** 连接

自定义配置文件在项目之间共享。 从这里开始，你可以使用你创建的自定义配置文件，而不必每次都执行此操作。 每次启动 Unreal 时，你只需在 " [设置" 部分](#setup)中通过步骤3到步骤6重新创建与设备的连接。

## <a name="see-also"></a>另请参阅
* [Unreal Insights 文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

