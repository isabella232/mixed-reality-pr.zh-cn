---
title: 全息影像稳定化
description: 处于不同环境和帧速率条件下的全息影像性能。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，环境跟踪，TMP，
ms.openlocfilehash: e2c83e7e4ca909e31803d55aabbc0c2344e89139
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143891"
---
# <a name="hologram-stabilization"></a>全息影像稳定性

## <a name="performance"></a>性能

为了使底层混合现实平台和设备产生最佳结果，实现帧速率非常重要。 目标帧速率 (例如： 60 FPS 或 90 FPS) 在不同的平台和设备之间有所不同。 不过，以帧速率为的混合现实应用程序将具有稳定的全息影像，并具有有效的头跟踪、手动跟踪等。  

## <a name="environment-tracking"></a>环境跟踪

稳定的全息呈现很大程度上取决于平台 & 设备的头姿势跟踪。 Unity 将从相机中呈现每个帧，这是由基础平台估计和提供的。 如果此跟踪没有正确地遵循实际头运动，则全息影像将显示不准确。 这对于 AR 设备（如 HoloLens）尤其明显且非常重要，用户可在其中将虚拟全息关联到现实世界。 性能对于可靠的头跟踪非常重要，但也有 [其他重要功能](/windows/mixed-reality/environment-considerations-for-hololens)。 影响用户体验的环境元素类型将取决于目标平台细节。

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 平台提供了一些用于平台上的稳定影像的 [参考材料](/windows/mixed-reality/hologram-stability) 。 虽然开发人员可以利用这些重要工具来改进用户的全息图视觉体验。

### <a name="depth-buffer-sharing"></a>深度缓冲区共享

Unity 开发人员可以选择使用平台共享应用程序的深度缓冲区。 这提供了一些信息，其中，对于当前帧，该平台可通过硬件辅助过程（称为 Late-Stage Reprojection）将其用于稳定的全息影像。

#### <a name="late-stage-reprojection"></a>后期阶段 reprojection

在呈现帧结束时，Windows Mixed Reality 平台采用应用程序生成的颜色 & 深度呈现器目标，并转换最终屏幕输出，以考虑自上次头部姿势预测以来任何略微头部运动。 应用程序的游戏循环需要一段时间来执行。 例如，在 60 FPS 时，这意味着应用程序需要大约 16.667 毫秒来呈现帧。 即使这看起来可能只是一小段时间，用户头部的位置和方向也会发生变化，从而在渲染时为相机带来新的投影矩阵。 后期阶段重新项目会转换最终图像中的像素，以考虑到这一新透视图。

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>每像素与稳定平面 LSR

根据设备终结点和在 Windows Mixed Reality 上运行的 OS 版本，Late-Stage重新保护算法将按像素或通过稳定平面 [执行](/windows/mixed-reality/hologram-stability#stabilization-plane)。

##### <a name="per-pixel-depth-based"></a>基于每像素深度

基于每像素深度的重现涉及利用深度缓冲区修改每个像素的图像输出，从而稳定不同距离的全息影像。 例如，距离 1 米的球体可能位于距离 10 米的支柱的前面。 如果用户稍微倾斜了头部，表示球体的像素将不同于表示支柱的远距离像素的转换。 每像素重新预测将考虑每个像素的此距离差，以更准确地重新进行重现。

##### <a name="stabilization-plane"></a>稳定平面

如果无法创建准确的深度缓冲区来与平台共享，另一种形式的 LSR 会利用稳定平面。 场景中的所有全息影像都将获得一些稳定，但全息影像在所需平面中会获得最大硬件稳定性。 平面的点和法线可以通过 Unity 提供的 *HolographicSettings.SetFocusPointForFrame* [API 提供给平台](/windows/mixed-reality/focus-point-in-unity)。

#### <a name="depth-buffer-format"></a>深度缓冲区格式

如果面向用于开发的 HoloLens，强烈建议使用16位深度缓冲格式，而不是24位。 这可以节省极大的性能，但深度值的精度较低。 若要弥补降低精度并避免进行 [z 向](https://en.wikipedia.org/wiki/Z-fighting)，建议从1000m 默认值（由 Unity 设置）中减少 [far 剪裁平面](https://docs.unity3d.com/Manual/class-Camera.html) 。

> [!NOTE]
> 如果使用的是 *16 位深度格式*，模具缓冲区所需的效果将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反，选择 *24 位深度格式* 通常会创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果适用于终结点图形平台）。

#### <a name="depth-buffer-sharing-in-unity"></a>Unity 中的深度缓冲区共享

为了利用基于深度的 LSR，开发人员需要执行两个重要的步骤。

1. 在 "**编辑**  >  **项目设置**  >  **播放器**" 下  >  **XR 设置**  >  **虚拟现实 sdk** > 启用 **深度缓冲共享**
    1. 如果面向 HoloLens，则建议同时选择 **16 位深度格式** 。
1. 在屏幕上呈现颜色时，还呈现深度

Unity 中的不[透明 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)通常会自动写入深度。 但是，默认情况下，透明 & 文本对象通常不会写入深度。 如果利用 MRTK 标准着色器或文本网格 Pro，则可以轻松地进行修正。

> [!NOTE]
> 若要快速确定场景中哪些对象不会直观写入深度缓冲区，可以使用 MRTK 配置文件中 *编辑器设置* 下的 " [*呈现深度缓冲区*" 实用工具](../configuration/mixed-reality-configuration-guide.md#editor-utilities)。

##### <a name="transparent-mrtk-standard-shader"></a>透明 MRTK 标准着色器

对于使用 [MRTK 标准着色器](../features/rendering/MRTK-standard-shader.md)的透明材料，请在 " *检查器* " 窗口中选择要查看的材料。 然后单击 " *立即修复* " 按钮，将材料转换为深度 (例如 Z-写入) 。

以前

![修复 MRTK 标准着色器前的深度缓冲区](../features/images/performance/DepthBufferFixNow_Before.PNG)

之后

![深度缓冲区固定 MRTK 标准着色器](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>文本网格 Pro

对于文本网格 Pro 对象，请选择 TMP GameObject 以在检查器中查看它。 在材料组件下，切换所分配材料的着色器，以使用 MRTK TextMeshPro 着色器。

![文本网格 Pro 深度缓冲区修复](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>自定义着色器

如果编写自定义着色器，将 [ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 标志添加到 *Pass* 块定义的顶部，以将着色器配置为写入深度缓冲区。

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>不透明的后备

如果上述方法对给定的方案不起作用， (即 使用 Unity UI) ，可能会将另一个对象写入深度缓冲区。 常见示例是在场景中的浮动面板上使用 Unity UI 文本。 通过使面板不透明或至少写入深度，&面板的文本将被平台稳定，因为它们的 z 值非常接近。

### <a name="worldanchors-hololens"></a>HoloLens (WorldAnchors) 

除了确保满足正确的配置以确保视觉稳定性外，必须确保全息影像在正确的物理位置保持稳定。 若要在物理空间中的重要位置通知平台，开发人员可以利用 GameObject 上需要停留在一个位置的[WorldAnchors。](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是添加到 GameObject 的组件，可绝对控制该对象的转换。

HoloLens 等设备不断扫描和了解环境。 因此，当 HoloLens 跟踪&移动位置时，其估计值将更新 [，Unity 坐标系会进行调整](/windows/mixed-reality/coordinate-systems-in-unity)。 例如，如果 GameObject 从相机开始放置 1 米，当 HoloLens 跟踪环境时，它可能会意识到 GameObject 所在的物理点实际距离 1.1 米。 这可能会导致全息影像偏移。 将 WorldAnchor 应用于 GameObject 将使定位点能够控制对象的转换，使对象保留在正确的物理位置 (即 在运行时) 更新为 1.1 m，而不是1m。 若要跨应用会话保持 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) ，开发人员可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 来 [保存和加载 WorldAnchors](/windows/mixed-reality/persistence-in-unity)。

> [!NOTE]
> 将 WorldAnchor 组件添加到 GameObject 后，不能修改该 GameObject 的转换 (例如 transform： position = x) 。 开发人员必须删除 WorldAnchor 才能编辑转换。

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

如果你想要使用其他方法手动处理锚点，请查看 Microsoft World 锁定工具。 

> [!div class="nextstepaction"]
> [具有 MR 功能工具的安装](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>另请参阅

- [性能](../performance/perf-getting-started.md)
- [HoloLens 环境注意事项](/windows/mixed-reality/environment-considerations-for-hololens)
- [全息影像稳定性 Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Unity 中的焦点](/windows/mixed-reality/focus-point-in-unity)
- [Unity 中的坐标系统](/windows/mixed-reality/coordinate-systems-in-unity)
- [Unity 中的持久性](/windows/mixed-reality/persistence-in-unity)
- [了解混合现实的性能](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [针对 Unity 的性能建议](/windows/mixed-reality/performance-recommendations-for-unity)