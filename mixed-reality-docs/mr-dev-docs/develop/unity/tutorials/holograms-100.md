---
title: HoloLens（第一代）基础知识 100 - Unity 入门
description: 了解如何为设备和设备创建第一个基本混合现实"hello world"HoloLens Windows Mixed Reality应用程序。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实， Windows Mixed Reality， HoloLens， 沉浸式， vr， mr， 入门， 全息影像， 学院， 教程， 混合现实学院， unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196495"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens (第一代) 基础知识 100：Unity 入门

>[!IMPORTANT]
>混合现实学院教程的设计HoloLens (第一代) Unity 2017 和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不会使用_** 最新工具集或交互进行更新HoloLens 2并且可能与较新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

本教程将指导你创建使用 Unity 构建的基本混合现实应用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 基础知识 100：Unity 入门</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

* 配置Windows 10正确工具的[一台电脑](../../install-the-tools.md)。

## <a name="chapter-1---create-a-new-project"></a>第 1 章 - 创建新Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要使用 Unity 生成应用，首先需要创建一个项目。 此项目组织成几个文件夹，其中最重要的是"资产"文件夹。 此文件夹保存从数字内容创建工具（如 Maya、MaxShop 4D 或 Photoshop）导入的所有资产、使用 Visual Studio 或你喜欢的代码编辑器创建的所有代码，以及 Unity 在编辑器中撰写场景、动画和其他 Unity 资产类型时创建的任何数量的内容文件。

若要生成和部署 UWP 应用，Unity 可以将项目导出为包含Visual Studio资产和代码文件的解决方案。

1. 启动 Unity
2. 选择“新建”
3. 输入项目名称 (例如"MixedRealityIntroduction") 
4. 输入保存项目的位置
5. 确保已 **选择"3D"** 切换开关
6. 选择 **"创建项目"**

恭喜，现已准备好开始使用混合现实自定义项。

## <a name="chapter-2---setup-the-camera"></a>第 2 章 - 设置相机

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 主相机处理头部跟踪和立体声渲染。 若要将主相机与混合现实一同使用，需要做出一些更改。

1. 选择"文件>新建场景"

首先，如果将用户的起始位置想象成 (**X：** 0， **Y**： 0， **Z**： 0) 。 由于主相机正在跟踪用户头部的移动，因此可以通过设置主相机的起始位置来设置用户的起始位置。

1. 在 **"层次结构"** 面板中选择 **"主相机** "
2. 在"**检查** 器"面板中，找到"转换"组件，将"位置"从 (**X**： 0， **Y**： 1， **Z**： -10) 更改为 (**X**： 0， **Y**： 0， **Z**： 0) 

其次，默认的相机背景需要一些思考。

**对于HoloLens，** 现实世界应出现在相机呈现的所有内容后面，而不是 Skybox 纹理后面。

1. 在"**层次结构"面板中** 仍选中"主相机"后，在"检查器"面板中查找"相机"组件，将"清除标志"下拉列表从 **Skybox** 更改为 **纯色**。 
2. 选择" **背景** 颜色选取器"，将 **RGBA** 值 (0、0、0、0) 

**对于以沉浸式** 头戴显示设备为目标的混合现实应用程序，可以使用 Unity 提供的默认 Skybox 纹理。

1. 在"**层次结构"面板中** 仍选中"主相机"后，在"检查器"面板中查找"相机"组件，将"**清除** 标志"下拉列表保留为 **"Skybox"。** 

第三，让我们考虑 Unity 中的近剪贴平面，并防止在用户接近对象或对象接近用户时，对象呈现得过于接近用户眼睛。

**对于HoloLens，** 可以将近剪辑平面设置为建议HoloLens 0.85 米。 [](../camera-in-unity.md#using-clipping-planes)

1. 在 **"** 层次结构"面板中仍选中"主相机"后，在"检查器"面板中查找"相机"组件，将"近剪辑平面"字段从默认的 **0.3** 更改为HoloLens **0.85"**。 

**对于以沉浸式** 头戴显示设备为目标的混合现实应用程序，可以使用 Unity 提供的默认设置。

1. 在"**层次结构"面板中** 仍选中"主相机"后，在"检查器"面板中查找"相机"组件，将"近剪辑平面"字段保留为默认的 **0.3**。  

最后，让我们保存到目前为止的进度。 若要保存场景更改，请选择"文件">将场景另 **存** 为"，将场景命名为 **"** 主 **"，** 然后选择"保存"。

## <a name="chapter-3---setup-the-project-settings"></a>第 3 章 - 设置Project 设置

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我们将设置一些 Unity 项目设置，以帮助我们面向 Windows SDK 进行开发。 我们还将为应用程序设置一些质量设置。 最后，我们将确保将生成目标设置为通用Windows平台。

### <a name="unity-performance-and-quality-settings"></a>Unity 性能和质量设置

**适用于 HoloLens 的 Unity 质量设置**

![适用于 HoloLens 的 Unity 质量设置](images/qualitysettings.png)

由于保持高帧HoloLens非常重要，因此我们希望优化质量设置以提高性能。 有关更详细的性能信息，请参阅 [Unity 的性能建议](../performance-recommendations-for-unity.md)。

1. 选择 **"编辑> Project 设置 >质量"**
2. 选择"**通用平台**"徽标Windows **下拉列表，** 然后选择"**非常低"。** 当"通用平台"列和"非常低"行中的框为绿色Windows将知道设置已正确应用。

**对于面向遮挡的混合现实应用程序显示**，可以将质量设置保留为默认值。

### <a name="target-windows-10-sdk"></a>目标 Windows 10 SDK

**Holographic SDK Windows目标**

![Holographic SDK Windows目标](../images/xrsettings.png)

我们需要让 Unity 知道，我们尝试导出的应用应创建沉浸式 [视图](../../../design/app-views.md) ，而不是 2D 视图。 为此，我们在面向 Windows 10 SDK 的 Unity 上启用虚拟现实支持。

1. 转到"**编辑> Project 设置 >播放器"。**
2. 在 **"Player 平台**"设置"检查器面板"中，选择"**通用Windows平台**"图标。
3. 展开“XR 设置”组。
4. 在“呈现”部分，选中“支持虚拟现实”复选框，添加新“虚拟现实 SDK 的”列表  。
5. 验证列表中是否显示“Windows 混合现实”。 如果没有，请选择列表底部的“+”按钮，然后选择“Windows 混合现实” 。

>[!NOTE]
>如果未看到"通用平台Windows图标，请仔细检查以确保在安装过程中选择了"通用Windows平台生成支持"。 如果没有，可能需要使用正确的 Windows 安装重新安装 Unity。

有关应用所有项目设置的出色工作。 接下来，让我们添加全息影像！

## <a name="chapter-4---create-a-cube"></a>第 4 章 - 创建多维数据集

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

在 Unity 项目中创建多维数据集就像在 Unity 中创建任何其他对象一样。 将立方体放在用户前面很容易，因为 Unity 的坐标系映射到现实世界 -其中 Unity 中的一个计量器在现实世界中大约是一个计量。

1. 在"层次结构"面板的左上角，选择"创建"下拉列表，然后选择"**三维对象>多维数据集"。**
2. 在"层次结构 **"面板中选择****新创建的** 多维数据集
3. 在检查 **器** 中， **找到"转换** "组件 **，将"** 位置"更改为 (**X：** 0， **Y**： 0， **Z**： 2) 。 *这会将立方体定位在用户起始位置的前面 2 米处。*
4. 在"转换"组件中，将"旋转"更改为" (**X：** 45， **Y**： 45， **Z**：  45) "，将"缩放" 更改为 (**X**： 0.25， **Y**： 0.25， **Z**： 0.25) 。 *这会将立方体缩放到 0.25 米。*
5. 若要保存场景更改，请选择"文件>**保存场景"。**

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>第 5 章 - 从 Unity 编辑器在设备上验证

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

创建多维数据集后，可以快速检查设备。 可以直接在 Unity 编辑器中执行此操作。

### <a name="initial-setup"></a>初始设置

1. 在开发电脑上的 Unity 中，打开"文件>**生成设置** 窗口。
2. 将 **"平台**"**更改为"通用Windows平台"，** 然后单击"**切换平台"**

### <a name="for-hololens-use-unity-remoting"></a>例如HoloLens Unity 远程处理

1. 在 HoloLens，安装并运行[Holographic Remoting Player（](../../platform-capabilities-and-apis/holographic-remoting-player.md)可从 Windows Store 获得）。 在设备上启动应用程序，它将进入等待状态，并显示设备的 IP 地址。 记下 IP。
2. **> 全息仿真打开 > XR 的窗口**。
3. 将 **仿真模式** 从 **None** 更改为 **远程到设备**。
4. 在 **远程计算机** 上，输入前面记下的 HoloLens 的 IP 地址。
5. 单击“连接”  。
6. 确保 **连接状态** 更改为 " **已连接** 绿色"。
7. 现在，你可以在 Unity 编辑器中单击 " **播放** "。

现在，可以在设备和编辑器中查看多维数据集。 您可以暂停、检查对象和调试，就像您在编辑器中运行应用一样，因为这实质上是发生的事情，但使用视频、音频和设备输入通过网络在主机和设备之间来回传输。

### <a name="for-other-mixed-reality-supported-headsets"></a>适用于其他混合现实支持的耳机

1. 使用 USB 电缆和 HDMI 或显示器端口电缆将耳机连接到开发 PC。
2. 启动 **混合现实门户** 并确保已完成首次运行体验。
3. 现在，可以从 Unity 按下 "播放" 按钮。

现在，你将能够在混合现实耳机和编辑器中看到多维数据集呈现。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第6章-从 Visual Studio 生成并部署到设备

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

现在，我们已准备好将项目编译到 Visual Studio 并部署到目标设备。

### <a name="export-to-the-visual-studio-solution"></a>导出到 Visual Studio 解决方案

1. 打开 **文件 > 生成设置**"窗口。
1. 单击 " **添加打开的场景** " 添加场景。
1. 将 **平台** 更改为 "**通用 Windows 平台**"，然后单击 "**切换平台**"。
1. 在 **通用 Windows 平台** 设置 "中，确保 **SDK** 为 **通用 10**。
1. 对于目标设备，请将封闭像素的 **任何设备** 保留为 "显示" 或 "切换到 **HoloLens**"。
1. **UWP 生成类型** 应为 **D3D**。
1. **UWP SDK** 可以保持 **最新安装的版本**。
1. 单击“生成”。
1. 在文件资源管理器中，单击 " **新建文件夹** "，然后将文件夹命名为 **"App"**。
1. 选择 **应用** 文件夹后，单击 " **选择文件夹** " 按钮。
1. 当 Unity 完成生成后，将出现一个 Windows 文件资源管理器窗口。
1. 在文件资源管理器中打开 **应用程序** 文件夹。
1. 在此示例中打开生成的 Visual Studio 解决方案 (MixedRealityIntroduction) 

### <a name="compile-the-visual-studio-solution"></a>编译 Visual Studio 解决方案

最后，我们将编译导出的 Visual Studio 解决方案，对其进行部署，然后在设备上试用。

1. 使用 Visual Studio 中的顶部工具栏将目标从 "**调试**" 更改为 "**发布**"，将 "从 **ARM** " 更改为 " **X86**"。

有关部署到设备与模拟器的说明有所不同。 按照与你的设置相匹配的说明进行操作。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>通过 Wi-Fi 部署到混合现实设备

1. 单击 " **本地计算机** " 按钮旁边的箭头，将部署目标更改为 " **远程计算机**"。
2. 输入混合现实设备的 IP 地址，并将 "**身份验证模式**" 更改为 "通用 (未加密协议) 用于 HoloLens 和 **Windows** 其他设备。
3. 单击 " **调试" > "开始（不调试**）"。

**对于 HoloLens**，如果这是首次部署到设备，则需 [使用 Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md)配对。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>通过 USB 部署到混合现实设备

确保设备通过 USB 电缆接通电源。

1. **对于 "HoloLens**"，单击 "**本地计算机**" 按钮旁边的箭头，然后将 "部署目标" 更改为 "**设备**"。
2. **对于连接到电脑的封闭像素设备**，请将设置保留为 "本地计算机"。 确保已运行 **混合现实门户** 。
3. 单击 " **调试" > "开始（不调试**）"。

### <a name="deploy-to-emulator"></a>部署到 Emulator

1. 单击 "**设备**" 按钮旁边的箭头，然后单击 "从下拉选择 **HoloLens Emulator**"。
2. 单击 " **调试" > "开始（不调试**）"。

### <a name="try-out-your-app"></a>试用你的应用

部署你的应用后，请尝试四处移动该多维数据集，并观察它是否在世界各地。

## <a name="see-also"></a>另请参阅

* [Unity 开发概述](../unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳做法](../best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 基础知识 101](holograms-101.md)
* [MR 基础知识 101E](holograms-101e.md)