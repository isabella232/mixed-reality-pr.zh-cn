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
# <a name="hologram-stabilization"></a><span data-ttu-id="6f89a-104">全息影像稳定</span><span class="sxs-lookup"><span data-stu-id="6f89a-104">Hologram stabilization</span></span>

## <a name="performance"></a><span data-ttu-id="6f89a-105">性能</span><span class="sxs-lookup"><span data-stu-id="6f89a-105">Performance</span></span>

<span data-ttu-id="6f89a-106">为了使基础混合现实平台和设备产生最佳结果，必须实现帧速率。</span><span class="sxs-lookup"><span data-stu-id="6f89a-106">In order for the underlying mixed reality platform and device to produce the best results, it is important to achieve performing frame rates.</span></span> <span data-ttu-id="6f89a-107">目标帧速率 (例如 60 FPS 或 90 FPS) 平台和设备不同。</span><span class="sxs-lookup"><span data-stu-id="6f89a-107">The target framerate (ex: 60 FPS or 90 FPS) will vary across platforms and devices.</span></span> <span data-ttu-id="6f89a-108">但是，满足帧速率的混合现实应用程序将具有稳定的全息影像以及高效的头部跟踪、手部跟踪等。</span><span class="sxs-lookup"><span data-stu-id="6f89a-108">However, mixed reality applications meeting framerate will have stable holograms as well as efficient head tracking, hand tracking and more.</span></span>  

## <a name="environment-tracking"></a><span data-ttu-id="6f89a-109">环境跟踪</span><span class="sxs-lookup"><span data-stu-id="6f89a-109">Environment tracking</span></span>

<span data-ttu-id="6f89a-110">稳定的全息渲染严重依赖于平台和设备的头部&跟踪。</span><span class="sxs-lookup"><span data-stu-id="6f89a-110">Stable holographic rendering heavily relies on head-pose tracking by the platform & device.</span></span> <span data-ttu-id="6f89a-111">Unity 将呈现基础平台估计和提供的相机姿势中每个帧的场景。</span><span class="sxs-lookup"><span data-stu-id="6f89a-111">Unity will render the scene every frame from the camera pose estimated and supplied by the underlying platform.</span></span> <span data-ttu-id="6f89a-112">如果此跟踪未正确跟踪实际头部移动，则全息影像在视觉上将显示不准确。</span><span class="sxs-lookup"><span data-stu-id="6f89a-112">If this tracking does not correctly follow actual head movement, then holograms will appear visually inaccurate.</span></span> <span data-ttu-id="6f89a-113">对于 HoloLens 等 AR 设备来说，这一点尤其明显，并且非常重要，用户可以将虚拟全息影像与现实世界关联。</span><span class="sxs-lookup"><span data-stu-id="6f89a-113">This is especially evident and important for AR devices like HoloLens where users can relate virtual holograms to the real world.</span></span> <span data-ttu-id="6f89a-114">性能对于可靠的头部跟踪非常重要，但也可能还有其他 [重要](/windows/mixed-reality/environment-considerations-for-hololens)功能。</span><span class="sxs-lookup"><span data-stu-id="6f89a-114">Performance is significant for reliable head tracking, but there can be [other important features](/windows/mixed-reality/environment-considerations-for-hololens), as well.</span></span> <span data-ttu-id="6f89a-115">影响用户体验的环境元素类型取决于目标平台的具体信息。</span><span class="sxs-lookup"><span data-stu-id="6f89a-115">The types of environment elements impacting user experience will depend on the targeted platform specifics.</span></span>

## <a name="windows-mixed-reality"></a><span data-ttu-id="6f89a-116">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6f89a-116">Windows Mixed Reality</span></span>

<span data-ttu-id="6f89a-117">该Windows Mixed Reality平台提供了 [一些用于](/windows/mixed-reality/hologram-stability) 稳定平台上全息影像的参考资料。</span><span class="sxs-lookup"><span data-stu-id="6f89a-117">The Windows Mixed Reality platform provides some [reference material](/windows/mixed-reality/hologram-stability) for stabilizing holograms on the platform.</span></span> <span data-ttu-id="6f89a-118">不过，开发人员可以利用一些关键工具来改进用户的全息影像视觉体验。</span><span class="sxs-lookup"><span data-stu-id="6f89a-118">There are a handful of key tools though that developers can utilize to improve the hologram visual experience for users.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="6f89a-119">深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="6f89a-119">Depth buffer sharing</span></span>

<span data-ttu-id="6f89a-120">Unity 开发人员可以选择与平台共享应用程序的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6f89a-120">Unity developers have the option of sharing the application's depth buffer with the platform.</span></span> <span data-ttu-id="6f89a-121">这提供了当前帧的全息影像存在位置的信息，平台可以利用这些信息通过硬件辅助过程（称为"重新Late-Stage来稳定全息影像。</span><span class="sxs-lookup"><span data-stu-id="6f89a-121">This provides information, where holograms exist for a current frame, that the platform can utilize to stabilize holograms via a hardware-assisted process known as Late-Stage Reprojection.</span></span>

#### <a name="late-stage-reprojection"></a><span data-ttu-id="6f89a-122">后期阶段重新项目</span><span class="sxs-lookup"><span data-stu-id="6f89a-122">Late-stage reprojection</span></span>

<span data-ttu-id="6f89a-123">在呈现帧的末尾，Windows Mixed Reality 平台使用应用程序生成的颜色 & 深度呈现目标，并转换最终屏幕输出，以考虑自上一次头姿势预测后的任何轻微运动。</span><span class="sxs-lookup"><span data-stu-id="6f89a-123">At the end of rendering a frame, the Windows Mixed Reality platform takes the color & depth render targets produced by the application and transforms the final screen output to account for any slight head movement since the last head pose prediction.</span></span> <span data-ttu-id="6f89a-124">应用程序的游戏循环需要执行时间。</span><span class="sxs-lookup"><span data-stu-id="6f89a-124">An application's game loop takes time to execute.</span></span> <span data-ttu-id="6f89a-125">例如，在 60 FPS，这意味着应用程序将占用 ~ 16.667 ms 来呈现帧。</span><span class="sxs-lookup"><span data-stu-id="6f89a-125">For example, at 60 FPS, this means the application is taking ~16.667ms to render a frame.</span></span> <span data-ttu-id="6f89a-126">尽管这可能看起来像是远少于的时间，但用户的位置和方向会变化，导致照相机呈现时的新投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="6f89a-126">Even though this may seem like a miniscule amount of time, the user's position and orientation of their head will change resulting in new projection matrices for the camera in rendering.</span></span> <span data-ttu-id="6f89a-127">后期阶段 reprojection 转换最终图像中的像素，以考虑此新透视。</span><span class="sxs-lookup"><span data-stu-id="6f89a-127">Late-stage reprojection transforms the pixels in the final image to account for this new perspective.</span></span>

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a><span data-ttu-id="6f89a-128">每像素与稳定平面 LSR</span><span class="sxs-lookup"><span data-stu-id="6f89a-128">Per-pixel vs stabilization plane LSR</span></span>

<span data-ttu-id="6f89a-129">根据 Windows Mixed Reality 设备上运行的设备终结点和操作系统版本，Late-Stage 的 Reprojection 算法将按像素或通过 [稳定平面](/windows/mixed-reality/hologram-stability#stabilization-plane)执行。</span><span class="sxs-lookup"><span data-stu-id="6f89a-129">Depending on the device endpoint and OS version running on a Windows Mixed Reality device, the Late-Stage Reprojection algorithm will either be performed per-pixel or via a [stabilization plane](/windows/mixed-reality/hologram-stability#stabilization-plane).</span></span>

##### <a name="per-pixel-depth-based"></a><span data-ttu-id="6f89a-130">基于像素的深度</span><span class="sxs-lookup"><span data-stu-id="6f89a-130">Per-pixel depth-based</span></span>

<span data-ttu-id="6f89a-131">基于像素深度的 reprojection 涉及到使用深度缓冲区来修改每个像素的图像输出，进而以不同的距离来修改稳定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="6f89a-131">Per-pixel depth-based reprojection involves utilizing the depth buffer to modify the image output per pixel and thus stabilize holograms at various distances.</span></span> <span data-ttu-id="6f89a-132">例如，球1m 可能位于10m 的支柱的前面。</span><span class="sxs-lookup"><span data-stu-id="6f89a-132">For example, a sphere 1m away may be in front of a pillar that is 10m away.</span></span> <span data-ttu-id="6f89a-133">如果用户稍微倾斜其球，表示球的像素将具有不同的变换（表示支柱）。</span><span class="sxs-lookup"><span data-stu-id="6f89a-133">The pixels representing the sphere will have a different transform than the far away pixels representing the pillar if the user has tilted their head slightly.</span></span> <span data-ttu-id="6f89a-134">以像素为单位的 reprojection 将在每个像素上考虑此距离差异，以获得更精确的 reprojection。</span><span class="sxs-lookup"><span data-stu-id="6f89a-134">Per-pixel reprojection will take into account this distance difference at every pixel for more accurate reprojection.</span></span>

##### <a name="stabilization-plane"></a><span data-ttu-id="6f89a-135">稳定平面</span><span class="sxs-lookup"><span data-stu-id="6f89a-135">Stabilization plane</span></span>

<span data-ttu-id="6f89a-136">如果无法创建与平台共享的准确的深度缓冲区，则另一种形式的 LSR 将使用稳定平面。</span><span class="sxs-lookup"><span data-stu-id="6f89a-136">If it is not possible to create an accurate depth buffer to share with the platform, another form of LSR utilizes a stabilization plane.</span></span> <span data-ttu-id="6f89a-137">场景中的所有全息影像都将接收到一些稳定性，但所需平面的全息影像将接收到最大硬件稳定性。</span><span class="sxs-lookup"><span data-stu-id="6f89a-137">All holograms in a scene will receive some stabilization, but holograms lying in the desired plane will receive the maximum hardware stabilization.</span></span> <span data-ttu-id="6f89a-138">可以通过 [Unity 提供](/windows/mixed-reality/focus-point-in-unity)的 *SetFocusPointForFrame* API 将平面的点和法线提供给平台。</span><span class="sxs-lookup"><span data-stu-id="6f89a-138">The point and normal for the plane can be supplied to the platform via the *HolographicSettings.SetFocusPointForFrame* [API provided by Unity](/windows/mixed-reality/focus-point-in-unity).</span></span>

#### <a name="depth-buffer-format"></a><span data-ttu-id="6f89a-139">深度缓冲区格式</span><span class="sxs-lookup"><span data-stu-id="6f89a-139">Depth buffer format</span></span>

<span data-ttu-id="6f89a-140">如果面向用于开发的 HoloLens，强烈建议使用16位深度缓冲格式，而不是24位。</span><span class="sxs-lookup"><span data-stu-id="6f89a-140">If targeting HoloLens for development, it is highly recommended to utilize the 16-bit depth buffer format compared to 24-bit.</span></span> <span data-ttu-id="6f89a-141">这可以节省极大的性能，但深度值的精度较低。</span><span class="sxs-lookup"><span data-stu-id="6f89a-141">This can save tremendously on performance although depth values will have less precision.</span></span> <span data-ttu-id="6f89a-142">若要弥补降低精度并避免进行 [z 向](https://en.wikipedia.org/wiki/Z-fighting)，建议从1000m 默认值（由 Unity 设置）中减少 [far 剪裁平面](https://docs.unity3d.com/Manual/class-Camera.html) 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-142">To compensate for the lower precision and avoid [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), it is recommended to reduce the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) from the 1000m default value set by Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="6f89a-143">如果使用的是 *16 位深度格式*，模具缓冲区所需的效果将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-143">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="6f89a-144">相反，选择 *24 位深度格式* 通常会创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果适用于终结点图形平台）。</span><span class="sxs-lookup"><span data-stu-id="6f89a-144">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>

#### <a name="depth-buffer-sharing-in-unity"></a><span data-ttu-id="6f89a-145">Unity 中的深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="6f89a-145">Depth buffer sharing in Unity</span></span>

<span data-ttu-id="6f89a-146">为了利用基于深度的 LSR，开发人员需要执行两个重要的步骤。</span><span class="sxs-lookup"><span data-stu-id="6f89a-146">In order to utilize depth-based LSR, there are two important steps that developers need to take.</span></span>

1. <span data-ttu-id="6f89a-147">在 "**编辑**  >  **项目设置**  >  **播放器**" 下  >  **XR 设置**  >  **虚拟现实 sdk** > 启用 **深度缓冲共享**</span><span class="sxs-lookup"><span data-stu-id="6f89a-147">Under **Edit** > **Project Settings** > **Player** > **XR Settings** > **Virtual Reality SDKs** > Enable **Depth Buffer Sharing**</span></span>
    1. <span data-ttu-id="6f89a-148">如果面向 HoloLens，则建议同时选择 **16 位深度格式** 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-148">If targeting HoloLens, it is recommended to select **16-bit depth format** as well.</span></span>
1. <span data-ttu-id="6f89a-149">在屏幕上呈现颜色时，还呈现深度</span><span class="sxs-lookup"><span data-stu-id="6f89a-149">When rendering color on screen, render depth as well</span></span>

<span data-ttu-id="6f89a-150">Unity 中的不[透明 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)通常会自动写入深度。</span><span class="sxs-lookup"><span data-stu-id="6f89a-150">[Opaque GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity will generally write to depth automatically.</span></span> <span data-ttu-id="6f89a-151">但是，默认情况下，透明 & 文本对象通常不会写入深度。</span><span class="sxs-lookup"><span data-stu-id="6f89a-151">However, transparent & text objects will generally not write to depth by default.</span></span> <span data-ttu-id="6f89a-152">如果利用 MRTK 标准着色器或文本网格 Pro，则可以轻松地进行修正。</span><span class="sxs-lookup"><span data-stu-id="6f89a-152">If utilizing the MRTK Standard Shader or Text Mesh Pro, this can be easily remedied.</span></span>

> [!NOTE]
> <span data-ttu-id="6f89a-153">若要快速确定场景中哪些对象不会直观写入深度缓冲区，可以使用 MRTK 配置文件中 *编辑器设置* 下的 " [*呈现深度缓冲区*" 实用工具](../configuration/mixed-reality-configuration-guide.md#editor-utilities)。</span><span class="sxs-lookup"><span data-stu-id="6f89a-153">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

##### <a name="transparent-mrtk-standard-shader"></a><span data-ttu-id="6f89a-154">透明 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="6f89a-154">Transparent MRTK Standard shader</span></span>

<span data-ttu-id="6f89a-155">对于使用 [MRTK 标准着色器](../features/rendering/MRTK-standard-shader.md)的透明材料，请在 " *检查器* " 窗口中选择要查看的材料。</span><span class="sxs-lookup"><span data-stu-id="6f89a-155">For transparent materials using the [MRTK Standard shader](../features/rendering/MRTK-standard-shader.md), select the material to view it in the *Inspector* window.</span></span> <span data-ttu-id="6f89a-156">然后单击 " *立即修复* " 按钮，将材料转换为深度 (例如</span><span class="sxs-lookup"><span data-stu-id="6f89a-156">Then click the *Fix Now* button to convert the material to write to depth (i.e</span></span> <span data-ttu-id="6f89a-157">Z-写入) 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-157">Z-Write On).</span></span>

<span data-ttu-id="6f89a-158">以前</span><span class="sxs-lookup"><span data-stu-id="6f89a-158">Before</span></span>

![修复 MRTK 标准着色器前的深度缓冲区](../features/images/performance/DepthBufferFixNow_Before.PNG)

<span data-ttu-id="6f89a-160">之后</span><span class="sxs-lookup"><span data-stu-id="6f89a-160">After</span></span>

![深度缓冲区固定 MRTK 标准着色器](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a><span data-ttu-id="6f89a-162">文本网格 Pro</span><span class="sxs-lookup"><span data-stu-id="6f89a-162">Text Mesh Pro</span></span>

<span data-ttu-id="6f89a-163">对于文本网格 Pro 对象，请选择 TMP GameObject 以在检查器中查看它。</span><span class="sxs-lookup"><span data-stu-id="6f89a-163">For Text Mesh Pro objects, select the TMP GameObject to view it in the inspector.</span></span> <span data-ttu-id="6f89a-164">在材料组件下，切换所分配材料的着色器以使用 MRTK TextMeshPro 着色器。</span><span class="sxs-lookup"><span data-stu-id="6f89a-164">Under the material component, switch the shader for the assigned material to use the MRTK TextMeshPro shader.</span></span>

![文本网格 Pro 深度缓冲修补程序](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a><span data-ttu-id="6f89a-166">自定义着色器</span><span class="sxs-lookup"><span data-stu-id="6f89a-166">Custom shader</span></span>

<span data-ttu-id="6f89a-167">如果编写自定义着色器，请将 [ZWrite 标志](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 添加到 *传递* 块定义的顶部，以将着色器配置为写入深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6f89a-167">If writing a custom shader, add the [ZWrite flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) to the top of the *Pass* block definition to configure the shader to write to the depth buffer.</span></span>

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

##### <a name="opaque-backings"></a><span data-ttu-id="6f89a-168">不透明 backings</span><span class="sxs-lookup"><span data-stu-id="6f89a-168">Opaque backings</span></span>

<span data-ttu-id="6f89a-169">如果上面的方法不适用于给定方案 (即</span><span class="sxs-lookup"><span data-stu-id="6f89a-169">If the above methods do not work for a given scenario (i.e</span></span> <span data-ttu-id="6f89a-170">使用 Unity UI) ，可以将另一个对象写入深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6f89a-170">using Unity UI), it is possible to have another object write to the depth buffer.</span></span> <span data-ttu-id="6f89a-171">常见的示例是在场景中的浮动面板上使用 Unity UI 文本。</span><span class="sxs-lookup"><span data-stu-id="6f89a-171">A common example is using Unity UI Text on a floating panel in a scene.</span></span> <span data-ttu-id="6f89a-172">通过使面板不透明或至少写入深度，该面板 & 的文本都将被平台稳定，因为其 z 值彼此接近。</span><span class="sxs-lookup"><span data-stu-id="6f89a-172">By making the panel opaque or at least writing to depth, then both the text & the panel will be stabilized by the platform since their z-values are so close to each other.</span></span>

### <a name="worldanchors-hololens"></a><span data-ttu-id="6f89a-173">WorldAnchors (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="6f89a-173">WorldAnchors (HoloLens)</span></span>

<span data-ttu-id="6f89a-174">除了确保满足正确的配置以确保视觉稳定性，还必须确保全息影像在正确的物理位置上保持稳定。</span><span class="sxs-lookup"><span data-stu-id="6f89a-174">Along with ensuring the correct configurations are met to ensure visual stability, it is important to ensure holograms remain stable at their correct physical locations.</span></span> <span data-ttu-id="6f89a-175">若要将平台通知到物理空间中的重要位置，开发人员可以利用 Gameobject 上的 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-175">To inform the platform on important locations in a physical space, developers can leverage [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) on GameObjects that need to stay in one place.</span></span> <span data-ttu-id="6f89a-176">[WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是一个添加到 GameObject 的组件，可对该对象的转换进行绝对控制。</span><span class="sxs-lookup"><span data-stu-id="6f89a-176">A [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) is a component added to a GameObject that takes absolute control over that object's transform.</span></span>

<span data-ttu-id="6f89a-177">HoloLens 等设备会持续扫描并了解环境。</span><span class="sxs-lookup"><span data-stu-id="6f89a-177">Devices such as HoloLens are constantly scanning and learning about the environment.</span></span> <span data-ttu-id="6f89a-178">因此，当 HoloLens 在空间中 & 位置跟踪移动时，将更新其估计值并 [调整 Unity 坐标系统](/windows/mixed-reality/coordinate-systems-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="6f89a-178">Thus, as the HoloLens tracks movement & position in space, its estimates will be updated and the [Unity coordinate system adjusted](/windows/mixed-reality/coordinate-systems-in-unity).</span></span> <span data-ttu-id="6f89a-179">例如，如果 GameObject 是从照相机开始，而在 HoloLens 跟踪环境时，它可能会认识到 GameObject 所在的物理点实际上是 1.1 m。</span><span class="sxs-lookup"><span data-stu-id="6f89a-179">For example, if a GameObject is placed 1m from the camera at start, as the HoloLens tracks the environment, it may realize the physical point where the GameObject is located is actually 1.1m away.</span></span> <span data-ttu-id="6f89a-180">这将导致全息图偏移。</span><span class="sxs-lookup"><span data-stu-id="6f89a-180">This would result in the hologram drifting.</span></span> <span data-ttu-id="6f89a-181">将 WorldAnchor 应用于 GameObject 会使定位点控制对象的转换，以便对象将保留在正确的物理位置 (即</span><span class="sxs-lookup"><span data-stu-id="6f89a-181">Applying a WorldAnchor to a GameObject will enable the anchor to control the object's transform so that the object will remain at the correct physical location (i.e</span></span> <span data-ttu-id="6f89a-182">在运行时) 更新为 1.1 m，而不是1m。</span><span class="sxs-lookup"><span data-stu-id="6f89a-182">update to 1.1m away instead of 1m at runtime).</span></span> <span data-ttu-id="6f89a-183">若要跨应用会话保持 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) ，开发人员可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 来 [保存和加载 WorldAnchors](/windows/mixed-reality/persistence-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="6f89a-183">To persist [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) across app sessions, developers can employ the [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) to [save and load WorldAnchors](/windows/mixed-reality/persistence-in-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="6f89a-184">将 WorldAnchor 组件添加到 GameObject 后，不能修改该 GameObject 的转换 (例如</span><span class="sxs-lookup"><span data-stu-id="6f89a-184">Once a WorldAnchor component has been added to a GameObject, it is not possible to modify that GameObject's transform (i.e</span></span> <span data-ttu-id="6f89a-185">transform： position = x) 。</span><span class="sxs-lookup"><span data-stu-id="6f89a-185">transform.position = x).</span></span> <span data-ttu-id="6f89a-186">开发人员必须删除 WorldAnchor 才能编辑转换。</span><span class="sxs-lookup"><span data-stu-id="6f89a-186">A developer must remove the WorldAnchor to edit the transform.</span></span>

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

<span data-ttu-id="6f89a-187">如果你想要使用其他方法手动处理锚点，请查看 Microsoft World 锁定工具。</span><span class="sxs-lookup"><span data-stu-id="6f89a-187">If you want an alternative to manually working with Anchors, check out the Microsoft World Locking Tools.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="6f89a-188">用 MR 功能工具安装</span><span class="sxs-lookup"><span data-stu-id="6f89a-188">Install with the MR Feature Tool</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a><span data-ttu-id="6f89a-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f89a-189">See also</span></span>

- [<span data-ttu-id="6f89a-190">性能</span><span class="sxs-lookup"><span data-stu-id="6f89a-190">Performance</span></span>](../performance/perf-getting-started.md)
- [<span data-ttu-id="6f89a-191">HoloLens 环境注意事项</span><span class="sxs-lookup"><span data-stu-id="6f89a-191">Environment Considerations for HoloLens</span></span>](/windows/mixed-reality/environment-considerations-for-hololens)
- [<span data-ttu-id="6f89a-192">全息影像稳定性 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6f89a-192">Hologram Stability Windows Mixed Reality</span></span>](/windows/mixed-reality/hologram-stability)
- [<span data-ttu-id="6f89a-193">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="6f89a-193">Focus point in Unity</span></span>](/windows/mixed-reality/focus-point-in-unity)
- [<span data-ttu-id="6f89a-194">Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="6f89a-194">Coordinate systems in Unity</span></span>](/windows/mixed-reality/coordinate-systems-in-unity)
- [<span data-ttu-id="6f89a-195">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="6f89a-195">Persistence in Unity</span></span>](/windows/mixed-reality/persistence-in-unity)
- [<span data-ttu-id="6f89a-196">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="6f89a-196">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="6f89a-197">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="6f89a-197">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)