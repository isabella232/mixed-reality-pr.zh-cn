---
title: 全息影像稳定化
description: 不同环境和帧速率条件下全息影像的性能。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 环境跟踪， TMP，
ms.openlocfilehash: 338ae2719764b84b7c58c1422e08fe02176eccf0
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333429"
---
# <a name="hologram-stabilization"></a>全息影像稳定

## <a name="performance"></a>性能

为了使基础混合现实平台和设备产生最佳结果，必须实现帧速率。 目标帧速率 (例如 60 FPS 或 90 FPS) 平台和设备不同。 但是，满足帧速率的混合现实应用程序将具有稳定的全息影像以及高效的头部跟踪、手部跟踪等。  

## <a name="environment-tracking"></a>环境跟踪

稳定的全息渲染严重依赖于平台和设备的头部&跟踪。 Unity 将呈现基础平台估计和提供的相机姿势中每个帧的场景。 如果此跟踪未正确跟踪实际头部移动，则全息影像在视觉上将显示不准确。 对于 HoloLens 等 AR 设备来说，这一点尤其明显，并且非常重要，用户可以将虚拟全息影像与现实世界关联。 性能对于可靠的头部跟踪非常重要，但也可能还有其他 [重要](/windows/mixed-reality/environment-considerations-for-hololens)功能。 影响用户体验的环境元素类型取决于目标平台的具体信息。

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

该Windows Mixed Reality平台提供了 [一些用于](/windows/mixed-reality/hologram-stability) 稳定平台上全息影像的参考资料。 不过，开发人员可以利用一些关键工具来改进用户的全息影像视觉体验。

### <a name="depth-buffer-sharing"></a>深度缓冲区共享

Unity 开发人员可以选择与平台共享应用程序的深度缓冲区。 这提供了当前帧的全息影像存在位置的信息，平台可以利用这些信息通过硬件辅助过程（称为"重新Late-Stage来稳定全息影像。

#### <a name="late-stage-reprojection"></a>后期阶段重新项目

在呈现帧的末尾，Windows Mixed Reality 平台使用应用程序生成的颜色 & 深度呈现目标，并转换最终屏幕输出，以考虑自上一次头姿势预测后的任何轻微运动。 应用程序的游戏循环需要执行时间。 例如，在 60 FPS，这意味着应用程序将占用 ~ 16.667 ms 来呈现帧。 尽管这可能看起来像是远少于的时间，但用户的位置和方向会变化，导致照相机呈现时的新投影矩阵。 后期阶段 reprojection 转换最终图像中的像素，以考虑此新透视。

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>每像素与稳定平面 LSR

根据 Windows Mixed Reality 设备上运行的设备终结点和操作系统版本，Late-Stage 的 Reprojection 算法将按像素或通过 [稳定平面](/windows/mixed-reality/hologram-stability#stabilization-plane)执行。

##### <a name="per-pixel-depth-based"></a>基于像素的深度

基于像素深度的 reprojection 涉及到使用深度缓冲区来修改每个像素的图像输出，进而以不同的距离来修改稳定的全息影像。 例如，球1m 可能位于10m 的支柱的前面。 如果用户稍微倾斜其球，表示球的像素将具有不同的变换（表示支柱）。 以像素为单位的 reprojection 将在每个像素上考虑此距离差异，以获得更精确的 reprojection。

##### <a name="stabilization-plane"></a>稳定平面

如果无法创建与平台共享的准确的深度缓冲区，则另一种形式的 LSR 将使用稳定平面。 场景中的所有全息影像都将接收到一些稳定性，但所需平面的全息影像将接收到最大硬件稳定性。 可以通过 [Unity 提供](/windows/mixed-reality/focus-point-in-unity)的 *SetFocusPointForFrame* API 将平面的点和法线提供给平台。

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

对于文本网格 Pro 对象，请选择 TMP GameObject 以在检查器中查看它。 在材料组件下，切换所分配材料的着色器以使用 MRTK TextMeshPro 着色器。

![文本网格 Pro 深度缓冲修补程序](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>自定义着色器

如果编写自定义着色器，请将 [ZWrite 标志](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 添加到 *传递* 块定义的顶部，以将着色器配置为写入深度缓冲区。

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

##### <a name="opaque-backings"></a>不透明 backings

如果上面的方法不适用于给定方案 (即 使用 Unity UI) ，可以将另一个对象写入深度缓冲区。 常见的示例是在场景中的浮动面板上使用 Unity UI 文本。 通过使面板不透明或至少写入深度，该面板 & 的文本都将被平台稳定，因为其 z 值彼此接近。

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens) 

除了确保满足正确的配置以确保视觉稳定性，还必须确保全息影像在正确的物理位置上保持稳定。 若要将平台通知到物理空间中的重要位置，开发人员可以利用 Gameobject 上的 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 。 [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是一个添加到 GameObject 的组件，可对该对象的转换进行绝对控制。

HoloLens 等设备会持续扫描并了解环境。 因此，当 HoloLens 在空间中 & 位置跟踪移动时，将更新其估计值并 [调整 Unity 坐标系统](/windows/mixed-reality/coordinate-systems-in-unity)。 例如，如果 GameObject 是从照相机开始，而在 HoloLens 跟踪环境时，它可能会认识到 GameObject 所在的物理点实际上是 1.1 m。 这将导致全息图偏移。 将 WorldAnchor 应用于 GameObject 会使定位点控制对象的转换，以便对象将保留在正确的物理位置 (即 在运行时) 更新为 1.1 m，而不是1m。 若要跨应用会话保持 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) ，开发人员可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 来 [保存和加载 WorldAnchors](/windows/mixed-reality/persistence-in-unity)。

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
> [用 MR 功能工具安装](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>另请参阅

- [性能](../performance/perf-getting-started.md)
- [HoloLens 环境注意事项](/windows/mixed-reality/environment-considerations-for-hololens)
- [全息影像稳定性 Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Unity 中的焦点](/windows/mixed-reality/focus-point-in-unity)
- [Unity 中的坐标系统](/windows/mixed-reality/coordinate-systems-in-unity)
- [Unity 中的持久性](/windows/mixed-reality/persistence-in-unity)
- [了解混合现实的性能](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [针对 Unity 的性能建议](/windows/mixed-reality/performance-recommendations-for-unity)