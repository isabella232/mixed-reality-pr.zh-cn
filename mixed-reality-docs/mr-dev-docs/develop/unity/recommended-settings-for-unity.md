---
title: 建议用于 Unity 的设置
description: 了解特定于混合现实应用（可通过项目设置切换）的 Unity 性能和发布行为。
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity， 设置， 混合现实， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， 性能， 质量设置， 照明设置， 深度缓冲区， xr， 跟踪丢失
ms.openlocfilehash: 7516ec89c49a12e7cb143d7e53d00efde0e44c4e
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743386"
---
# <a name="recommended-settings-for-unity"></a>建议用于 Unity 的设置

Unity 提供了一组默认选项，这些选项通常是所有平台的平均情况。 但是，Unity 提供了一些特定于混合现实的行为，可以通过项目设置进行切换。

## <a name="performant-environment-set-up"></a>性能环境设置

### <a name="low-quality-settings"></a>低质量设置

将 Unity 质量设置修改为"非常低"非常重要，以便应用程序以适当的帧速率运行并运行良好，尤其是对于 HoloLens 开发。 对于沉浸式头戴显示设备的开发，根据为 VR 体验提供电源的桌面规格，仍可在没有最低质量参数的情况下实现帧速率。

在 Unity 2019 LTS+ 中，可以通过进入"编辑项目设置质量"并单击向下箭头到"非常低的质量级别"来设置默认值，来设置项目  >    >  的质量级别。

### <a name="lighting-settings"></a>照明设置

与"质量"场景设置类似，为混合现实应用程序设置最佳照明设置非常重要。 在 Unity 中，通常对场景具有最大性能影响的"照明"设置是 **"实时全局照明"。** 可以通过访问"窗口渲染照明设置""实时全局照明"  >    >    >  **来关闭"全局照明"。**

还有另一个照明设置 **，"烘焙全局照明"。** 此设置可以在沉浸式头戴显示设备上提供性能高、视觉效果突出的结果，但不适用于 HoloLens 开发。 **烘焙全局照明** 仅针对静态 GameObject 进行计算，由于未知且不断变化的环境的性质，在 HoloLens 场景中找不到这些对象。

有关详细信息[，请阅读 Unity 中的 Global Unity。](https://docs.unity3d.com/Manual/GIIntro.html) 

>[!NOTE]
> **实时全局照明** 按 **场景设置，** 因此开发人员必须针对其项目中每个 Unity 场景保存此属性。

### <a name="single-pass-instancing-rendering-path"></a>单通道实例化呈现路径

在混合现实应用程序中，场景呈现两次，每只眼睛一次呈现给用户。 与传统 3D 开发相比，这实际上是需要计算的工作量的两倍。 在 Unity 中选择最有效的呈现路径以节省 CPU 和 GPU 时间非常重要。 单通道实例呈现可优化混合现实应用的 Unity 呈现管道，建议默认为每个项目启用此设置。

在 Unity 项目中启用此功能

1)  打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）    
2) 从“立体渲染方法”下拉菜单中选择“单通道实例化”（必须选中“支持虚拟现实”复选框）  

有关此呈现方法的更多详细信息，请阅读 Unity 中的以下文章。

- [如何使用高级立体渲染最大化 AR 和 VR 的性能](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单通道实例化](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 如果开发人员的现有自定义着色器不是针对实例化编写的，则单通道实例化渲染会发生一个常见问题。 启用此功能后，开发人员可能会注意到，某些 GameObject 只在一只眼睛中呈现。 这是因为，关联的自定义着色器没有与实例化相关的适当属性。
>
> 请参阅 Unity 文章 [HoloLens 的 单通道立体渲染](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)来了解如何解决此问题

### <a name="enable-depth-buffer-sharing"></a>启用深度缓冲区共享

为了从用户的认知中实现更好的全息影像稳定性，建议在 Unity 中启用 **"深度缓冲区共享** "属性。 启用此功能后，Unity 将与你的应用程序平台共享应用程序Windows Mixed Reality地图。 然后，该平台可以针对应用程序呈现的任何给定帧更好地优化场景的全息影像稳定性。

在 Unity 项目中启用此功能

1) 打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）    
2) 选中 **"在支持** 虚拟现实的 **虚拟网络中Windows Mixed Reality** SDK  >   **("** 启用深度缓冲区共享"复选框) 

此外，建议在此面板中的"深度格式"设置下选择 **"16** 位深度"，尤其是对于 HoloLens 开发。  与 24 位相比，选择 16 位将显著减少带宽要求，因为需要移动/处理的数据更少。

为了使Windows Mixed Reality优化全息影像稳定性，它依赖于深度缓冲区的准确性，并匹配屏幕上的任何渲染全息影像。 因此，在启用深度缓冲区共享时，呈现颜色时，还必须呈现深度。 在 Unity 中，大多数不透明或 TransparentCutout 材料默认呈现深度，但透明对象和文本对象不会呈现深度，尽管这依赖于着色器等。

如果使用混合 [现实工具包标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)，则呈现透明对象的深度：

1) 选择使用 MRTK 标准着色器透明材料，然后打开"检查器编辑器"窗口
2) 选择深度 **缓冲区共享** 警告中的"立即修复"按钮。 也可将"呈现模式"设置为"自定义 **"来手动****执行此操作**;然后将"**模式"** 设置为 **"透明**"，最后将 **"深度写入"设置为****"打开"**

> [!IMPORTANT]
> 更改这些值以及相机的近/远平面设置时，开发人员应小心 Z 冲突。 当两个游戏对象尝试呈现到同一像素，并且深度缓冲区的保真度受限（即，由于深度缓冲区的保真度限制）时， (Z 冲突 z depth) ，Unity 无法识别位于另一个对象前面的对象。 开发人员将注意到两个游戏对象在两个游戏对象之间闪烁 *，因为他们需要* 相同的 z 深度值。 这可以通过切换到 24 位深度格式来解决，因为每个对象在相机的 z 深度方面需要计算更大的值范围。
>
> 但是，建议改为将相机的近平面和远平面修改为更小的范围，并保留 16 位深度格式，尤其是对于 HoloLens 开发。 z 深度是沿近相机平面和远相机平面以非线性方式映射到值范围。 可以通过在场景中选择主相机，在"检查器"**下** 修改这一点，更改"近&远剪裁平面"值，以减小其 (范围，即 从 1000m 到 100m 或其他 x 值，等等) 

>[!IMPORTANT]
> [使用 16 位](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 深度格式时，Unity 不会创建模具缓冲区。 因此，某些 Unity UI 效果和其他需要模具的效果将不起作用，除非选择 24 位深度格式，这将创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)。

### <a name="building-for-il2cpp"></a>IL2CPP 生成

Unity 已弃用对 .NET 脚本后端的支持，因此建议开发人员使用 **IL2CPP** 进行 UWP Visual Studio 生成。 尽管这带来了各种优势，但从 Unity for **IL2CPP** 生成 Visual Studio 解决方案的速度可能会比旧的 .NET 方法慢。 因此，强烈建议遵循生成 **IL2CPP** 的最佳实践，以节省开发迭代时间。

1) 利用增量生成，每次将项目生成到同一目录，并在那里重新使用预生成文件
2) 在生成文件夹中禁用项目的反恶意软件&扫描
   - 在 **& 设置应用下打开** "病毒Windows 10威胁防护"
   - 在 **"病毒和****威胁&下选择"管理设置"**
   - 在 **"排除项"部分下选择** " **添加或删除排除** 项"
   - 选择 **"添加排除** 项"，然后选择包含 Unity 项目代码和生成输出的文件夹
3) 使用 SSD 进行生成

有关详细信息 [，请阅读优化 IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 的生成时间。

> [!NOTE]
> 此外，设置[缓存服务器](https://docs.unity3d.com/Manual/CacheServer.html)可能会有所帮助，尤其是对于包含大量资产（不包括脚本文件）或不断变化的场景/资产的 Unity 项目而言。 打开项目时，Unity 会在开发人员计算机上将符合条件的资产存储为内部缓存格式。 必须重新导入项，因此，项在修改后会重新经过处理。 此过程可以执行一次，结果可保存在缓存服务器，因此可与其他开发人员共享以节省时间，无需让每个开发人员在本地重新导入新的更改。

## <a name="publishing-properties"></a>发布属性

### <a name="holographic-splash-screen"></a>全息初始屏幕

HoloLens 具有移动类 CPU 和 GPU，这意味着应用加载可能需要更长的时间。 加载应用时，用户只看到黑色，因此他们可能会想知道这一点。 若要在加载过程中保护它们，可以添加全息初始屏幕。

切换全息初始屏幕：

1) 转到"**编辑**  >  **项目设置**  >  **""播放器"** 页
2) 选择 **"Windows 应用商店"** 选项卡并打开" **初始图像"** 部分
3) 在"Windows 全息图像""全息> **图像"属性下应用** 图像。
    - 切换"显示 **Unity 初始屏幕"** 选项将启用或禁用 Unity 品牌初始屏幕。 如果没有 Unity Pro 许可证，则始终显示 Unity 品牌初始屏幕。
    - 如果 **应用全息初始** 图像，则无论启用还是禁用"显示 Unity 初始屏幕"复选框，都会始终显示该图像。 只有具有 Unity Pro 许可证的开发人员才能指定自定义全息初始图像。

|  显示 Unity 初始屏幕  |  全息初始图像  |  行为 |
|----------|----------|----------|
|  开  |  无  |  显示默认 Unity 初始屏幕 5 秒或直到加载应用（以较长者为准）。 |
|  开  |  自定义  |  显示自定义初始屏幕 5 秒或直到加载应用（以较长者为准）。 |
|  关  |  无  |  显示透明的黑色 (没有) ，直到加载应用。 |
|  关  |  自定义  |  显示自定义初始屏幕5秒或在加载应用之前，以较长者为准。 |

有关详细信息，请阅读 [Unity 初始屏幕文档](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) 。

### <a name="tracking-loss"></a>失跟

混合现实耳机依赖于查看它周围的环境，以构建 [全球锁定的坐标系](coordinate-systems-in-unity.md)，使全息影像保持在位置。 当耳机无法在世界各地定位时，耳机被称为 *丢失跟踪*。 在这些情况下，依赖于全球锁定坐标系的功能（如空间阶段、空间锚和空间映射）不起作用。

如果发生跟踪丢失，则 Unity 的默认行为是停止渲染全息影像，暂停 [游戏循环](https://docs.unity3d.com/Manual/ExecutionOrder.html)，并显示一条跟踪丢失的通知，以使用户看起来更舒适。 还可以以跟踪丢失图像的形式提供自定义通知。 对于依赖于整个体验的跟踪的应用，足以让 Unity 完全处理此过程，直到重新获得跟踪。 开发人员可以在跟踪丢失期间提供要显示的自定义图像。

自定义跟踪丢失映像：

1) 中转到 "**编辑**  >  **项目设置**  >  **播放器**" 页面
2) 在 " **Windows 应用商店** " 选项卡上选择并打开 " **初始图像** " 部分
3) 应用 " **Windows 全息 > 跟踪丢失映像** " 属性下的映像。

#### <a name="opt-out-of-automatic-pause"></a>选择退出自动暂停

某些应用可能不需要跟踪 (例如， [仅面向打印的应用](coordinate-systems-in-unity.md) （如360度视频查看器）) 或者可能需要在跟踪丢失时继续处理。 您可以选择禁用跟踪行为的默认丢失，但您需要负责隐藏/禁用任何对象，这在跟踪丢失方案中无法正确呈现。 在大多数情况下，建议在这种情况下呈现的内容只是正文锁定的内容，并在主相机周围居中。

选择退出自动暂停行为：

1) 请参阅 **编辑**  >  **项目设置**  >  **播放器** 页面
2) 选择 " **Windows 应用商店** " 选项卡，并打开 " **初始图像** " 部分
3) 修改 " **跟踪丢失时暂停" 和 "显示图像** " 复选框中的 Windows 全息 >。

#### <a name="tracking-loss-events"></a>跟踪丢失事件

若要在跟踪丢失时定义自定义行为，请处理全局 [跟踪丢失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

为了使应用程序能够利用特定功能，它必须在其清单中声明相应的功能。 清单声明可以在 Unity 中进行，因此它们包含在以后的每个项目导出中。

可以通过以下方式为混合现实应用程序启用功能：

1) 中转到 "**编辑**  >  **项目设置**  >  **播放器**" 页面
2) 选择 " **Windows 应用商店** " 选项卡，打开 " **发布设置** " 部分，并查找 **功能** 列表

为全息应用启用常用 Api 的适用功能包括：
<br>

|  功能  |  需要功能的 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  网络摄像头  |  PhotoCapture 和 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分别 (存储捕获的内容)  |
|  麦克风  |  捕获音频) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 时的 VideoCapture ( |
|  InternetClient  |  DictationRecognizer (并使用 Unity 探查器)  |

## <a name="see-also"></a>另请参阅

* [Unity 开发概述](unity-development-overview.md)
* [了解混合现实的性能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)