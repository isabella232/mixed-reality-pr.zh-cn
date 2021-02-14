---
title: 在不 MRTK 的情况下配置项目
description: 了解如何在没有混合现实工具包的情况下为 Windows Mixed Reality 配置新的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能
ms.openlocfilehash: 6a9bc0d9a565de1d25e1906c439e39773cb99244
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496075"
---
# <a name="configuring-your-project-without-mrtk"></a>配置项目时不使用 MRTK

Windows Mixed Reality (WMR) 是作为 Windows 10 操作系统的一部分引入的 Microsoft 平台。 WMR 平台使你能够生成在全息和 VR 显示设备上呈现数字内容的应用程序。

尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。  如果你使用的是 MRTK，则以下文档将演示如何正确设置用于混合现实开发的项目。  需要更改的设置分为两类：每个项目的设置和每场景设置。

> [!NOTE]
> 你始终可以在以后导入 MRTK，因此，不会产生要首先进行手动路由的损失。

如果选择 WMR 手动设置，则需要更改的设置将分为两个类别：每个项目和每场景。

## <a name="per-project-settings"></a>每个项目的设置

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：

1.  选择 **文件 > 生成设置 ...**
2.  选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3.  将 **体系结构** 设置为 **ARM 64**
4.  将 **目标设备** 设置为 **HoloLens**
5.  将 **生成类型** 设置为 **D3D**
6.  将 **UWP SDK** 设置为 **安装的最新版本**
7.  将 **生成配置** 设置为 **发布** ，因为调试存在已知的性能问题

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图。

### <a name="for-xrsdk"></a>对于 XRSDK 

1. 在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"，然后选择 " **XR 插件管理**"

2. 选择 "**安装 XR 插件管理**"

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality** "

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. 展开 " **XR 插件管理**" 部分，并选择 " **Windows Mixed Reality** "
5. 选中所有框并将 **深度提交模式** 设置为 **深度16位**

![突出显示了 Windows Mixed Reality 部分的 "项目设置" 窗口的屏幕截图已在 unity 编辑器中打开](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>对于旧版 XR 

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。

1. 从生成设置中打开 **播放机设置** ... **窗口** 并展开 **XR 设置** 组
2. 在 " **XR 设置** " 部分中，选择 " **支持的虚拟现实** " 以添加虚拟现实设备列表
3. 将 **深度格式** 设置为 **16 位深度** 并启用 **深度缓冲共享**
4. 将 **立体声渲染模式** 设置为 **单一传递实例**
5. 如果要使用全息远程处理，请选择 " **支持 WSA 全息远程处理** " 

![突出显示了 "播放机设置" 部分的 "项目设置" 窗口的屏幕截图](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>更新清单

您的应用程序现在可以处理全息呈现和空间输入。 但是，你的应用程序需要在其清单中声明相应的功能，才能利用某些功能。 可以通过转到 " **播放机设置" > "通用 Windows 平台 >" 发布设置 "> 功能**，找到项目功能。 

建议在 Unity 中创建清单声明，以将其包含在所有以后导出的项目中。 为混合现实启用常用 Unity Api 的适用功能包括：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (访问 HoloLens 上的 [空间映射](../../design/spatial-mapping.md)网格) &mdash; *无需对耳机进行常规空间跟踪* | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分别 (存储捕获的内容)  | 
|  麦克风  |  捕获音频) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 时的 VideoCapture ( | 
|  InternetClient  |  DictationRecognizer (并使用 Unity 探查器)  | 

### <a name="quality-settings"></a>质量设置

HoloLens 具有移动类 GPU。 如果你的应用面向 HoloLens，你需要调整应用中的质量设置以实现最快的性能，以确保它保持完整的帧速率：

1. 选择 "**编辑 > 项目设置 > 质量**"
2. 选择 **Windows 应用商店** 徽标下的 **下拉列表**，并选择 "**非常低**"。 如果 Windows 应用商店列和 **极低** 的行中的框为绿色，将知道设置正确应用
3. 在 **阴影** 部分，选择 "**禁用阴影**"

![突出显示了 "质量设置" 部分的 "项目设置" 窗口的屏幕截图](images/wmr-config-img-10.png)<br>
*Unity 质量设置*

## <a name="per-scene-settings"></a>每场景设置

### <a name="unity-camera-settings"></a>Unity 照相机设置

如果选中 " **支持虚拟现实** "，则 [Unity 相机](camera-in-unity.md) 组件会处理 [头跟踪和 stereoscopic 呈现](../platform-capabilities-and-apis/rendering.md)。 这意味着不需要使用自定义相机替换主相机对象。

如果你的应用程序专门面向 HoloLens，则需要更改一些设置以优化设备的透明显示。 这些设置允许你的全息内容透过物理环境显示：

1. 在 **层次结构** 中，选择 **主相机**
2. 在 " **检查器** " 面板中，将转换 **位置** 设置为 **0，0，0，** 以使用户头部的位置从 Unity 世界原点开始。
3. 将 **清除标志** 更改为 **纯色**。
4. 将 **背景** 色更改为 **RGBA 0，0，0，0**。 在 HoloLens 中，黑色呈现为透明。
5. 更改 **剪辑平面-接近** 于 [HoloLens 建议](camera-in-unity.md#clip-planes) 0.85 (米) 。

![在 Unity 编辑器中打开的 "检查器" 选项卡的屏幕截图](images/wmr-config-img-11.png)<br>
*Unity 照相机设置*

> [!IMPORTANT]
> 如果删除并创建新相机，请确保将新相机标记为 " **MainCamera**"。

## <a name="next-steps"></a>后续步骤

现在，你的项目已准备就绪，可以开始开发混合现实体验：

* 添加 [核心构建基块](unity-development-overview.md#2-core-building-blocks)
* 查看可用 [的平台功能和 api](unity-development-overview.md#3-advanced-features)
* 了解如何 [部署应用](../platform-capabilities-and-apis/using-visual-studio.md#)
* 使用 [混合现实模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)