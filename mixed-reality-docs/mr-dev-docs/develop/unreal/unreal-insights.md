---
title: 使用 Unreal Insights 进行分析
description: 了解如何在 Insights 上HoloLens 2 Unreal HoloLens 2。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal， Unreal Engine 4， UE4， HoloLens， HoloLens 2， 开发， 亵渎， unreal 见解， 文档， 指南， 功能， 全息影像， 游戏开发， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228590"
---
# <a name="profiling-with-unreal-insights"></a>使用 Unreal Insights 进行分析 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html)是一种分析系统，用于收集、分析和可视化 Unreal Engine 的数据。 分析系统可帮助你找到优化瓶颈以及应用性能可以使用提升的区域。 通常，你Insights编辑器中启用 Unreal，但HoloLens 2则需要使用命令行。  

## <a name="setup"></a>设置

Unreal 允许你使用启用 Unreal HoloLens 的命令行参数在 HoloLens 启动器中创建和配置"自定义Insights。

1.  在命令提示符下，使用 **ipconfig** 命令查找计算机的 IP 地址。 IP 地址是 ipconfig 列出的 IPv4 地址。 稍后在设置命令行参数时，请记住这一点。

> [!IMPORTANT]
> 如果支持 VPN，可能需要改为提供通过 VPN 提供的 IP 地址。

![ipconfig 命令的命令行结果的屏幕截图](images/unreal-insights-img-01.png)

2.  转到 Unreal Engine 面板的顶部，打开 **"设备管理器"** 按钮 **下的"启动"** 按钮：

![启动选项的屏幕截图，其中突出显示了设备管理器](images/unreal-insights-img-02.png)

3.  在"设备管理器"中 **，选择"添加未列出的设备"：**

![Unreal 引擎中打开的设备管理器的屏幕截图](images/unreal-insights-img-03.png)

4. 单击 **"选择平台"并选择****HoloLens：**

!["添加未列出的设备"下拉列表的屏幕截图，其中突出显示了HoloLens设备](images/unreal-insights-img-04.png)

5.  如果使用 IPoverUSB，请输入 127.0.0.1：10080 作为设备标识符。 在HoloLens字段中输入用户和密码，并 **按需要填写**"显示名称"。

> [!IMPORTANT]
> 设备标识符是在步骤 1 HoloLens运行 Unreal Insights计算机的 IP 地址。

![设备管理器HoloLens设备详细信息的屏幕截图](images/unreal-insights-img-05.png)

6.  选择 **"** 添加HoloLens设备管理器的设备列表中应显示你的设备：

![添加到HoloLens列表的屏幕截图](images/unreal-insights-img-06.png)

## <a name="launch"></a>启动

1. 在 **Project Launcher"** 按钮下的 UE4 面板 **中打开"启动"** 按钮：

![启动选项的屏幕截图，其中突出显示了项目启动器](images/unreal-insights-img-07.png)

2. 选择按钮 **+** ，在"自定义启动配置文件" **下创建自定义配置文件**。 创建后，始终可以稍后编辑此配置文件：

![项目启动器屏幕截图，其中突出显示了自定义启动配置文件](images/unreal-insights-img-08.png)

3. 选择 **自定义启动** 配置文件上的HoloLens配置文件"按钮并配置：
    * 选择 **"食谱****到书籍"** 以启用复制到设备
    * 可能需要在"存档"部分查看"是否要存档？"，以保留生成的 .appxbundle，而不是删除 以节省磁盘空间。 指定 .appxbundle 的位置，并切换到开发版本（如果需要）

![配置文件配置中食谱选项的屏幕截图，其中突出显示了书籍和HoloLens菜单](images/unreal-insights-img-09.png)

4. 将 **"希望如何部署生成？"** 设置为"复制到 **设备"** 以激活 UI 的 **"** 启动"部分：

![项目启动器屏幕截图，其中突出显示了"复制到设备"的部署选项](images/unreal-insights-img-10.png)

5. 在 **"启动"部分设置** "其他 **命令行参数** "。 参数将写入到ue4commandline.txt文件中，打包到捆绑包中，在启动时使用。 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * 尝试初学者 **：-tracehost=IP_OF_YOUR_PC -trace=Log，Bookmark，Frame，CPU，GPU，LoadTime，File，Net**
    * 可以在[Unreal Insights文档中找到可用启动参数的完整列表](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)。

> [!NOTE]
> "IP_OF_YOUR_PC"是在步骤 1 中发现的 IP 地址。 这是运行 Unreal Insights 的计算机的 IP 地址，而不是 HoloLens。

> [!IMPORTANT]
> 跟踪可能会非常快速地成为大型跟踪。 仅启用需要保持低跟踪大小的通道。

![启动配置选项的屏幕截图](images/unreal-insights-img-11.png)

6. 在应用Insights之前启动 Unreal，否则 Unreal Insights将无法在应用之前进行适当的初始化：
    * Unreal Insights可执行文件存储在二进制文件引擎文件夹中，通常如下所示："C：\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![正在运行的 unreal insights 可执行文件的屏幕截图](images/unreal-insights-img-12.png)

6.  选择 **"** 返回"以返回到"**返回Project Launcher根**
7.  返回编辑器，单击 **自定义启动** 配置文件上的"启动"

![自定义启动配置文件的屏幕截图](images/unreal-insights-img-13.png)

8.  监视项目已打包、安装在设备上并启动

## <a name="profiling"></a>分析

返回到 Unreal Insights，**选择设备** 实时连接以开始分析

自定义配置文件在项目之间共享。 从此处开始，可以使用创建的自定义配置文件，而不必每次这样做。 每次启动 Unreal 时，只需重新创建与设备的连接，只需在安装部分中执行步骤 3 到[](#setup)6。

## <a name="see-also"></a>另请参阅
* [Unreal Insights 文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

