---
title: 在没有 MRTK 的情况下配置项目
description: 了解如何在没有混合现实Windows Mixed Reality配置新的 Unity 项目Toolkit。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity， 混合现实， 开发， 入门， 新项目， Windows Mixed Reality， UWP， XR， 性能
ms.openlocfilehash: 85f8dee3208ce2c2a3bd328641544cbba0525cabdd1bf99404065572aeb354cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210972"
---
# <a name="configuring-your-project-without-mrtk"></a>配置项目时不使用 MRTK

Windows Mixed Reality (WMR) 是作为操作系统的一Windows 10引入的 Microsoft 平台。 使用 WMR 平台，可以生成在全息和 VR 显示设备上呈现数字内容的应用程序。

虽然 Microsoft 和社区已创建开放源代码工具（如混合现实[Toolkit (MRTK) ）](/windows/mixed-reality/mrtk-unity/configuration/usingupm)来自动设置 WMR 环境，但许多开发人员希望从头构建自己的体验。  以下文档将演示如何正确设置混合现实开发项目，无论你是否使用 MRTK。  需要更改的设置分为两类：每项目设置和按场景设置。

> [!NOTE]
> 以后始终可以导入 MRTK，因此先执行手动路由不会有什么损失。

如果选择 WMR 手动设置，则需要更改的设置将细分为两个类别：每个项目和每个场景。

## <a name="per-project-settings"></a>每项目设置

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"MAC"&"独立"平台](images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到通用 Windows 平台：

1.  选择 **"文件>生成设置...**
2.  在 **"Windows"列表中选择**"通用平台"，然后选择"**切换平台"**
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"通用Windows平台"](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../design/app-views.md)沉浸式视图而不是 2D 视图。

### <a name="for-xrsdk"></a>对于 XRSDK 

1. 在 Unity 编辑器中，导航到 **"编辑> Project"，然后选择****"XR 插件管理"**

2. 选择 **"安装 XR 插件管理"**

![unity 编辑器中Project 设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR"，****然后选择Windows Mixed Reality**

![unity 编辑器中Project"设置"窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. 展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows Platform 设置"** 选项卡
5. 如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。** 
    * 可以选择任一运行时。  如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，并查看使用适用于 Unity 的混合现实 [OpenXR](./xr-project-setup.md)插件指南，在返回到本教程之前，请正确设置这些设备

> [!NOTE]
> 从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。  迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。 有关详细信息，请参阅 [使用混合现实 OpenXR 插件](./xr-project-setup.md)。

6. 如果决定选择"深度Windows Mixed Reality插件，请选中所有框，将"深度提交 **模式**"设置为"深度 **16 位"**

![unity 编辑器中Project设置窗口的屏幕截图，其中突出显示了Windows Mixed Reality部分](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>对于旧版 XR 

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。

1. 从 **"生成设置..."** 打开"**播放器设置..."窗口** 并展开 **XR 设置** 组
2. 在 **"XR** **设置"** 部分中，选择"支持虚拟现实"以添加"虚拟现实设备"列表
3. 将 **深度格式设置为** **16 位深度** 并启用 **深度缓冲区共享**
4. 将 **立体声渲染模式设置为****单通道实例**
5. 如果要 **使用全息远程处理** ，请选择"支持的 WSA 全息远程处理" 

![unity 编辑器中Project"设置"窗口的屏幕截图，其中突出显示了"播放器设置"部分](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>更新清单

应用现在可以处理全息渲染和空间输入。 但是，应用需要在其清单中声明相应的功能，以利用某些功能。 可以通过访问"适用于通用 设置 > 设置 平台的 **播放器"Windows">"设置 >功能设置 >功能**。 

建议在 Unity 中创建清单声明，以将其包括在导出的所有将来项目中。 为混合现实启用常用 Unity API 的适用功能包括：

|  功能  |  需要该功能的 API | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (上访问空间 [](../../design/spatial-mapping.md)映射网格HoloLens) 头戴显示设备常规 &mdash; *空间跟踪不需要任何功能* | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 或 VideoCapture， (捕获的内容存储时分别)  | 
|  麦克风  |  VideoCapture (捕获音频) 、听写Recognizer、GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (和 以使用 Unity Profiler)  | 

### <a name="quality-settings"></a>质量设置

HoloLens具有移动类 GPU。 如果应用面向 HoloLens，则首先需要先在应用中优化质量设置，以加快性能，确保其保持全帧速率。  在开发中取得进一步进展后，可以考虑提高质量设置，以找到质量和性能之间的正确平衡： 

1. 选择 **"编辑> Project 设置 >质量"** 
2. 选择 **"Windows"** **徽标下的**   下拉列表，然后选择" **非常低"。** 当"Store"列中的框和"非常低"行为绿色Windows，你会知道设置已正确应用 
3. 在" **阴影"**   部分中，选择" **禁用阴影"** 

![unity 编辑器中Project"设置"窗口的屏幕截图，其中突出显示了"质量设置"部分](images/wmr-config-img-10.png)<br>
*Unity 质量设置*

## <a name="per-scene-settings"></a>按场景设置

### <a name="unity-camera-settings"></a>Unity 相机设置

选中 **"支持虚拟现实** "后 [，Unity 相机](camera-in-unity.md) 组件将处理头部 [跟踪和立体声渲染](../platform-capabilities-and-apis/rendering.md)。 这意味着，无需将主相机对象替换为自定义相机。

如果应用专门针对HoloLens，则需要更改一些设置，以针对设备的透明显示进行优化。 这些设置允许全息内容向物理世界显示：

1. 在" **层次结构"中**，选择 **"主相机"**
2. 在 **"检查** 器"面板中，将转换位置设置为 **0、0、0，** 以便用户头部的位置从 Unity 世界原点开始。
3. 将 **"清除标志"****更改为"纯色"。**
4. 将"**背景色"** 更改为 **"RGBA 0，0，0，0"。** 黑色在图像中呈现为HoloLens。
5. 更改 **裁剪平面 - 接近** HoloLens建议 0.85 (米) 。 [](camera-in-unity.md#using-clipping-planes)

![Unity 编辑器中打开的检查器选项卡的屏幕截图](images/wmr-config-img-11.png)<br>
*Unity 相机设置*

> [!IMPORTANT]
> 如果删除并创建新相机，请确保新相机标记为 **MainCamera**。

## <a name="next-steps"></a>后续步骤

项目准备就绪后，可以开始开发混合现实体验：

* 添加 [核心构建基块](unity-development-overview.md#2-core-building-blocks)
* 查看可用的 [平台功能和 API](unity-development-overview.md#3-advanced-features)
* 了解如何 [部署应用](../platform-capabilities-and-apis/using-visual-studio.md#)
* 使用 [混合现实模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)