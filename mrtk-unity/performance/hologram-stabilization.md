---
title: 全息影像稳定
description: 不同环境和帧速率条件下全息影像的性能。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 环境跟踪， TMP，
ms.openlocfilehash: 7aab167f2d850a4bca88a2cc40aae4f3cc50fb4b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176481"
---
# <a name="hologram-stabilization"></a><span data-ttu-id="c2df5-104">全息影像稳定</span><span class="sxs-lookup"><span data-stu-id="c2df5-104">Hologram stabilization</span></span>

## <a name="performance"></a><span data-ttu-id="c2df5-105">性能</span><span class="sxs-lookup"><span data-stu-id="c2df5-105">Performance</span></span>

<span data-ttu-id="c2df5-106">为了使基础混合现实平台和设备产生最佳结果，必须实现帧速率。</span><span class="sxs-lookup"><span data-stu-id="c2df5-106">In order for the underlying mixed reality platform and device to produce the best results, it is important to achieve performing frame rates.</span></span> <span data-ttu-id="c2df5-107">目标帧速率 (例如 60 FPS 或 90 FPS) 平台和设备不同。</span><span class="sxs-lookup"><span data-stu-id="c2df5-107">The target framerate (ex: 60 FPS or 90 FPS) will vary across platforms and devices.</span></span> <span data-ttu-id="c2df5-108">但是，满足帧速率的混合现实应用程序将具有稳定的全息影像以及高效的头部跟踪、手部跟踪等。</span><span class="sxs-lookup"><span data-stu-id="c2df5-108">However, mixed reality applications meeting framerate will have stable holograms as well as efficient head tracking, hand tracking and more.</span></span>  

## <a name="environment-tracking"></a><span data-ttu-id="c2df5-109">环境跟踪</span><span class="sxs-lookup"><span data-stu-id="c2df5-109">Environment tracking</span></span>

<span data-ttu-id="c2df5-110">稳定的全息渲染严重依赖于平台和设备的头部&跟踪。</span><span class="sxs-lookup"><span data-stu-id="c2df5-110">Stable holographic rendering heavily relies on head-pose tracking by the platform & device.</span></span> <span data-ttu-id="c2df5-111">Unity 将呈现基础平台估计和提供的相机姿势中每个帧的场景。</span><span class="sxs-lookup"><span data-stu-id="c2df5-111">Unity will render the scene every frame from the camera pose estimated and supplied by the underlying platform.</span></span> <span data-ttu-id="c2df5-112">如果此跟踪未正确跟踪实际头部移动，则全息影像在视觉上将显示不准确。</span><span class="sxs-lookup"><span data-stu-id="c2df5-112">If this tracking does not correctly follow actual head movement, then holograms will appear visually inaccurate.</span></span> <span data-ttu-id="c2df5-113">对于 AR 设备（例如 HoloLens，用户可以将虚拟全息影像与现实世界关联，这一点尤其明显且非常重要。</span><span class="sxs-lookup"><span data-stu-id="c2df5-113">This is especially evident and important for AR devices like HoloLens where users can relate virtual holograms to the real world.</span></span> <span data-ttu-id="c2df5-114">性能对于可靠的头部跟踪非常重要，但也可能还有其他 [重要](/windows/mixed-reality/environment-considerations-for-hololens)功能。</span><span class="sxs-lookup"><span data-stu-id="c2df5-114">Performance is significant for reliable head tracking, but there can be [other important features](/windows/mixed-reality/environment-considerations-for-hololens), as well.</span></span> <span data-ttu-id="c2df5-115">影响用户体验的环境元素类型取决于目标平台的具体信息。</span><span class="sxs-lookup"><span data-stu-id="c2df5-115">The types of environment elements impacting user experience will depend on the targeted platform specifics.</span></span>

## <a name="windows-mixed-reality"></a><span data-ttu-id="c2df5-116">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c2df5-116">Windows Mixed Reality</span></span>

<span data-ttu-id="c2df5-117">该Windows Mixed Reality平台提供了[一些用于](/windows/mixed-reality/hologram-stability)稳定平台上全息影像的参考资料。</span><span class="sxs-lookup"><span data-stu-id="c2df5-117">The Windows Mixed Reality platform provides some [reference material](/windows/mixed-reality/hologram-stability) for stabilizing holograms on the platform.</span></span> <span data-ttu-id="c2df5-118">不过，开发人员可以利用一些关键工具来改进用户的全息影像视觉体验。</span><span class="sxs-lookup"><span data-stu-id="c2df5-118">There are a handful of key tools though that developers can utilize to improve the hologram visual experience for users.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="c2df5-119">深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="c2df5-119">Depth buffer sharing</span></span>

<span data-ttu-id="c2df5-120">Unity 开发人员可以选择与平台共享应用程序的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="c2df5-120">Unity developers have the option of sharing the application's depth buffer with the platform.</span></span> <span data-ttu-id="c2df5-121">这提供了当前帧的全息影像存在位置的信息，平台可以利用这些信息通过硬件辅助过程（称为"重新Late-Stage来稳定全息影像。</span><span class="sxs-lookup"><span data-stu-id="c2df5-121">This provides information, where holograms exist for a current frame, that the platform can utilize to stabilize holograms via a hardware-assisted process known as Late-Stage Reprojection.</span></span>

#### <a name="late-stage-reprojection"></a><span data-ttu-id="c2df5-122">后期阶段重新项目</span><span class="sxs-lookup"><span data-stu-id="c2df5-122">Late-stage reprojection</span></span>

<span data-ttu-id="c2df5-123">在呈现帧结束时，Windows Mixed Reality 平台采用应用程序生成的颜色 & 深度呈现目标，并转换最终屏幕输出，以考虑自上次头部姿势预测以来任何略微头部移动。</span><span class="sxs-lookup"><span data-stu-id="c2df5-123">At the end of rendering a frame, the Windows Mixed Reality platform takes the color & depth render targets produced by the application and transforms the final screen output to account for any slight head movement since the last head pose prediction.</span></span> <span data-ttu-id="c2df5-124">应用程序的游戏循环需要一段时间来执行。</span><span class="sxs-lookup"><span data-stu-id="c2df5-124">An application's game loop takes time to execute.</span></span> <span data-ttu-id="c2df5-125">例如，在 60 FPS 时，这意味着应用程序需要大约 16.667 毫秒来呈现帧。</span><span class="sxs-lookup"><span data-stu-id="c2df5-125">For example, at 60 FPS, this means the application is taking ~16.667ms to render a frame.</span></span> <span data-ttu-id="c2df5-126">即使这看起来可能只是一小段时间，用户头部的位置和方向也会发生变化，从而在渲染时为相机带来新的投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="c2df5-126">Even though this may seem like a miniscule amount of time, the user's position and orientation of their head will change resulting in new projection matrices for the camera in rendering.</span></span> <span data-ttu-id="c2df5-127">后期阶段重新项目会转换最终图像中的像素，以考虑到这一新透视图。</span><span class="sxs-lookup"><span data-stu-id="c2df5-127">Late-stage reprojection transforms the pixels in the final image to account for this new perspective.</span></span>

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a><span data-ttu-id="c2df5-128">每像素与稳定平面 LSR</span><span class="sxs-lookup"><span data-stu-id="c2df5-128">Per-pixel vs stabilization plane LSR</span></span>

<span data-ttu-id="c2df5-129">根据设备终结点和在 Windows Mixed Reality 上运行的 OS 版本，Late-Stage重新保护算法将按像素或通过稳定平面[执行](/windows/mixed-reality/hologram-stability#stabilization-plane)。</span><span class="sxs-lookup"><span data-stu-id="c2df5-129">Depending on the device endpoint and OS version running on a Windows Mixed Reality device, the Late-Stage Reprojection algorithm will either be performed per-pixel or via a [stabilization plane](/windows/mixed-reality/hologram-stability#stabilization-plane).</span></span>

##### <a name="per-pixel-depth-based"></a><span data-ttu-id="c2df5-130">基于每像素深度</span><span class="sxs-lookup"><span data-stu-id="c2df5-130">Per-pixel depth-based</span></span>

<span data-ttu-id="c2df5-131">基于每像素深度的重现涉及利用深度缓冲区修改每个像素的图像输出，从而稳定不同距离的全息影像。</span><span class="sxs-lookup"><span data-stu-id="c2df5-131">Per-pixel depth-based reprojection involves utilizing the depth buffer to modify the image output per pixel and thus stabilize holograms at various distances.</span></span> <span data-ttu-id="c2df5-132">例如，距离 1 米的球体可能位于距离 10 米的支柱的前面。</span><span class="sxs-lookup"><span data-stu-id="c2df5-132">For example, a sphere 1m away may be in front of a pillar that is 10m away.</span></span> <span data-ttu-id="c2df5-133">如果用户稍微倾斜了头部，表示球体的像素将不同于表示支柱的远距离像素的转换。</span><span class="sxs-lookup"><span data-stu-id="c2df5-133">The pixels representing the sphere will have a different transform than the far away pixels representing the pillar if the user has tilted their head slightly.</span></span> <span data-ttu-id="c2df5-134">每像素重新预测将考虑每个像素的此距离差，以更准确地重新进行重现。</span><span class="sxs-lookup"><span data-stu-id="c2df5-134">Per-pixel reprojection will take into account this distance difference at every pixel for more accurate reprojection.</span></span>

##### <a name="stabilization-plane"></a><span data-ttu-id="c2df5-135">稳定平面</span><span class="sxs-lookup"><span data-stu-id="c2df5-135">Stabilization plane</span></span>

<span data-ttu-id="c2df5-136">如果无法创建准确的深度缓冲区来与平台共享，另一种形式的 LSR 会利用稳定平面。</span><span class="sxs-lookup"><span data-stu-id="c2df5-136">If it is not possible to create an accurate depth buffer to share with the platform, another form of LSR utilizes a stabilization plane.</span></span> <span data-ttu-id="c2df5-137">场景中的所有全息影像都将获得一些稳定，但全息影像在所需平面中会获得最大硬件稳定性。</span><span class="sxs-lookup"><span data-stu-id="c2df5-137">All holograms in a scene will receive some stabilization, but holograms lying in the desired plane will receive the maximum hardware stabilization.</span></span> <span data-ttu-id="c2df5-138">平面的点和法线可以通过 Unity 提供的 *HolographicSettings.SetFocusPointForFrame* [API 提供给平台](/windows/mixed-reality/focus-point-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="c2df5-138">The point and normal for the plane can be supplied to the platform via the *HolographicSettings.SetFocusPointForFrame* [API provided by Unity](/windows/mixed-reality/focus-point-in-unity).</span></span>

#### <a name="depth-buffer-format"></a><span data-ttu-id="c2df5-139">深度缓冲区格式</span><span class="sxs-lookup"><span data-stu-id="c2df5-139">Depth buffer format</span></span>

<span data-ttu-id="c2df5-140">如果面向 HoloLens，强烈建议使用 16 位深度缓冲区格式（与 24 位相比）。</span><span class="sxs-lookup"><span data-stu-id="c2df5-140">If targeting HoloLens for development, it is highly recommended to utilize the 16-bit depth buffer format compared to 24-bit.</span></span> <span data-ttu-id="c2df5-141">尽管深度值的精度较低，但这会极大地节省性能。</span><span class="sxs-lookup"><span data-stu-id="c2df5-141">This can save tremendously on performance although depth values will have less precision.</span></span> <span data-ttu-id="c2df5-142">为了补偿较低的精度并避免 z[冲突](https://en.wikipedia.org/wiki/Z-fighting)，建议将远剪裁平面从 Unity[](https://docs.unity3d.com/Manual/class-Camera.html)设置的 1000m 默认值减小。</span><span class="sxs-lookup"><span data-stu-id="c2df5-142">To compensate for the lower precision and avoid [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), it is recommended to reduce the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) from the 1000m default value set by Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="c2df5-143">如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="c2df5-143">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="c2df5-144">相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 [8](https://docs.unity3d.com/Manual/SL-Stencil.html)位模具缓冲区（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="c2df5-144">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>

#### <a name="depth-buffer-sharing-in-unity"></a><span data-ttu-id="c2df5-145">Unity 中的深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="c2df5-145">Depth buffer sharing in Unity</span></span>

<span data-ttu-id="c2df5-146">若要利用基于深度的 LSR，开发人员需要执行两个重要步骤。</span><span class="sxs-lookup"><span data-stu-id="c2df5-146">In order to utilize depth-based LSR, there are two important steps that developers need to take.</span></span>

1. <span data-ttu-id="c2df5-147">在 **"**  >  **编辑Project 设置**  >  **播放器**  >  **XR 设置** 虚拟现实 SDK"下>  >  启用 **深度缓冲区共享**</span><span class="sxs-lookup"><span data-stu-id="c2df5-147">Under **Edit** > **Project Settings** > **Player** > **XR Settings** > **Virtual Reality SDKs** > Enable **Depth Buffer Sharing**</span></span>
    1. <span data-ttu-id="c2df5-148">如果面向 HoloLens，则建议同时选择 **16 位深度** 格式。</span><span class="sxs-lookup"><span data-stu-id="c2df5-148">If targeting HoloLens, it is recommended to select **16-bit depth format** as well.</span></span>
1. <span data-ttu-id="c2df5-149">在屏幕上呈现颜色时，呈现深度也</span><span class="sxs-lookup"><span data-stu-id="c2df5-149">When rendering color on screen, render depth as well</span></span>

<span data-ttu-id="c2df5-150">[Unity 中的不透明 GameObject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) 通常会自动写入深度。</span><span class="sxs-lookup"><span data-stu-id="c2df5-150">[Opaque GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity will generally write to depth automatically.</span></span> <span data-ttu-id="c2df5-151">但是，&默认情况下，透明文本对象通常不会写入深度。</span><span class="sxs-lookup"><span data-stu-id="c2df5-151">However, transparent & text objects will generally not write to depth by default.</span></span> <span data-ttu-id="c2df5-152">如果利用 MRTK 标准着色器或文本网格Pro，这很容易得到修正。</span><span class="sxs-lookup"><span data-stu-id="c2df5-152">If utilizing the MRTK Standard Shader or Text Mesh Pro, this can be easily remedied.</span></span>

> [!NOTE]
> <span data-ttu-id="c2df5-153">若要快速确定场景中哪些对象未以可视方式写入深度缓冲区，可以使用 MRTK 配置文件中 [](../configuration/mixed-reality-configuration-guide.md#editor-utilities)"编辑器"设置"呈现 *深度缓冲区*"实用工具。</span><span class="sxs-lookup"><span data-stu-id="c2df5-153">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

##### <a name="transparent-mrtk-standard-shader"></a><span data-ttu-id="c2df5-154">透明 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="c2df5-154">Transparent MRTK Standard shader</span></span>

<span data-ttu-id="c2df5-155">对于使用 [MRTK 标准着色器的](../features/rendering/MRTK-standard-shader.md)透明材料，请选择材料，在"检查器"窗口中 *查看* 材料。</span><span class="sxs-lookup"><span data-stu-id="c2df5-155">For transparent materials using the [MRTK Standard shader](../features/rendering/MRTK-standard-shader.md), select the material to view it in the *Inspector* window.</span></span> <span data-ttu-id="c2df5-156">然后单击" *立即修复* "按钮，将要写入的材料转换为深度 (即</span><span class="sxs-lookup"><span data-stu-id="c2df5-156">Then click the *Fix Now* button to convert the material to write to depth (i.e</span></span> <span data-ttu-id="c2df5-157">Z-Write on) 。</span><span class="sxs-lookup"><span data-stu-id="c2df5-157">Z-Write On).</span></span>

<span data-ttu-id="c2df5-158">以前</span><span class="sxs-lookup"><span data-stu-id="c2df5-158">Before</span></span>

![修复 MRTK 标准着色器之前的深度缓冲区](../features/images/performance/DepthBufferFixNow_Before.PNG)

<span data-ttu-id="c2df5-160">之后</span><span class="sxs-lookup"><span data-stu-id="c2df5-160">After</span></span>

![深度缓冲区修复了 MRTK 标准着色器](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a><span data-ttu-id="c2df5-162">文本网格Pro</span><span class="sxs-lookup"><span data-stu-id="c2df5-162">Text Mesh Pro</span></span>

<span data-ttu-id="c2df5-163">对于文本网格Pro对象，请选择 TMP GameObject 以在检查器中查看它。</span><span class="sxs-lookup"><span data-stu-id="c2df5-163">For Text Mesh Pro objects, select the TMP GameObject to view it in the inspector.</span></span> <span data-ttu-id="c2df5-164">在材料组件下，切换所分配材料的着色器，以使用 MRTK TextMeshPro 着色器。</span><span class="sxs-lookup"><span data-stu-id="c2df5-164">Under the material component, switch the shader for the assigned material to use the MRTK TextMeshPro shader.</span></span>

![文本网格Pro深度缓冲区修复](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a><span data-ttu-id="c2df5-166">自定义着色器</span><span class="sxs-lookup"><span data-stu-id="c2df5-166">Custom shader</span></span>

<span data-ttu-id="c2df5-167">如果编写自定义着色器，将 [ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 标志添加到 *Pass* 块定义的顶部，以将着色器配置为写入深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="c2df5-167">If writing a custom shader, add the [ZWrite flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) to the top of the *Pass* block definition to configure the shader to write to the depth buffer.</span></span>

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

##### <a name="opaque-backings"></a><span data-ttu-id="c2df5-168">不透明的后备</span><span class="sxs-lookup"><span data-stu-id="c2df5-168">Opaque backings</span></span>

<span data-ttu-id="c2df5-169">如果上述方法对给定的方案不起作用， (即</span><span class="sxs-lookup"><span data-stu-id="c2df5-169">If the above methods do not work for a given scenario (i.e</span></span> <span data-ttu-id="c2df5-170">使用 Unity UI) ，可能会将另一个对象写入深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="c2df5-170">using Unity UI), it is possible to have another object write to the depth buffer.</span></span> <span data-ttu-id="c2df5-171">常见示例是在场景中的浮动面板上使用 Unity UI 文本。</span><span class="sxs-lookup"><span data-stu-id="c2df5-171">A common example is using Unity UI Text on a floating panel in a scene.</span></span> <span data-ttu-id="c2df5-172">通过使面板不透明或至少写入深度，&面板的文本将被平台稳定，因为它们的 z 值非常接近。</span><span class="sxs-lookup"><span data-stu-id="c2df5-172">By making the panel opaque or at least writing to depth, then both the text & the panel will be stabilized by the platform since their z-values are so close to each other.</span></span>

### <a name="worldanchors-hololens"></a><span data-ttu-id="c2df5-173">WorldAnchors (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="c2df5-173">WorldAnchors (HoloLens)</span></span>

<span data-ttu-id="c2df5-174">除了确保满足正确的配置以确保视觉稳定性外，必须确保全息影像在正确的物理位置保持稳定。</span><span class="sxs-lookup"><span data-stu-id="c2df5-174">Along with ensuring the correct configurations are met to ensure visual stability, it is important to ensure holograms remain stable at their correct physical locations.</span></span> <span data-ttu-id="c2df5-175">若要在物理空间中的重要位置通知平台，开发人员可以利用 GameObject 上需要停留在一个位置的[WorldAnchors。](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)</span><span class="sxs-lookup"><span data-stu-id="c2df5-175">To inform the platform on important locations in a physical space, developers can leverage [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) on GameObjects that need to stay in one place.</span></span> <span data-ttu-id="c2df5-176">[WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是添加到 GameObject 的组件，可绝对控制该对象的转换。</span><span class="sxs-lookup"><span data-stu-id="c2df5-176">A [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) is a component added to a GameObject that takes absolute control over that object's transform.</span></span>

<span data-ttu-id="c2df5-177">设备（HoloLens不断扫描和了解环境。</span><span class="sxs-lookup"><span data-stu-id="c2df5-177">Devices such as HoloLens are constantly scanning and learning about the environment.</span></span> <span data-ttu-id="c2df5-178">因此，随着HoloLens跟踪&位置的移动，其估计值将更新[，Unity 坐标系也会进行调整](/windows/mixed-reality/coordinate-systems-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="c2df5-178">Thus, as the HoloLens tracks movement & position in space, its estimates will be updated and the [Unity coordinate system adjusted](/windows/mixed-reality/coordinate-systems-in-unity).</span></span> <span data-ttu-id="c2df5-179">例如，如果 GameObject 从相机开始放置 1 米，则当 HoloLens 跟踪环境时，它可能会意识到 GameObject 所在的物理点实际距离 1.1 米。</span><span class="sxs-lookup"><span data-stu-id="c2df5-179">For example, if a GameObject is placed 1m from the camera at start, as the HoloLens tracks the environment, it may realize the physical point where the GameObject is located is actually 1.1m away.</span></span> <span data-ttu-id="c2df5-180">这可能会导致全息影像偏移。</span><span class="sxs-lookup"><span data-stu-id="c2df5-180">This would result in the hologram drifting.</span></span> <span data-ttu-id="c2df5-181">将 WorldAnchor 应用于 GameObject 将使定位点能够控制对象的转换，使对象保留在正确的物理位置 (即</span><span class="sxs-lookup"><span data-stu-id="c2df5-181">Applying a WorldAnchor to a GameObject will enable the anchor to control the object's transform so that the object will remain at the correct physical location (i.e</span></span> <span data-ttu-id="c2df5-182">更新到 1.1 米，而不是运行时 1) 。</span><span class="sxs-lookup"><span data-stu-id="c2df5-182">update to 1.1m away instead of 1m at runtime).</span></span> <span data-ttu-id="c2df5-183">若要跨 [应用会话保留 WorldAnchors，](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 开发人员可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) [来保存和加载 WorldAnchors](/windows/mixed-reality/persistence-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="c2df5-183">To persist [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) across app sessions, developers can employ the [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) to [save and load WorldAnchors](/windows/mixed-reality/persistence-in-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="c2df5-184">将 WorldAnchor 组件添加到 GameObject 后，无法修改 GameObject 的转换 (即</span><span class="sxs-lookup"><span data-stu-id="c2df5-184">Once a WorldAnchor component has been added to a GameObject, it is not possible to modify that GameObject's transform (i.e</span></span> <span data-ttu-id="c2df5-185">transform.position = x) 。</span><span class="sxs-lookup"><span data-stu-id="c2df5-185">transform.position = x).</span></span> <span data-ttu-id="c2df5-186">开发人员必须删除 WorldAnchor 以编辑转换。</span><span class="sxs-lookup"><span data-stu-id="c2df5-186">A developer must remove the WorldAnchor to edit the transform.</span></span>

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

<span data-ttu-id="c2df5-187">如果希望使用替代方法来手动使用定位点，请查看 Microsoft World 锁定工具。</span><span class="sxs-lookup"><span data-stu-id="c2df5-187">If you want an alternative to manually working with Anchors, check out the Microsoft World Locking Tools.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2df5-188">使用 MR 功能工具安装</span><span class="sxs-lookup"><span data-stu-id="c2df5-188">Install with the MR Feature Tool</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a><span data-ttu-id="c2df5-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2df5-189">See also</span></span>

- [<span data-ttu-id="c2df5-190">性能</span><span class="sxs-lookup"><span data-stu-id="c2df5-190">Performance</span></span>](../performance/perf-getting-started.md)
- [<span data-ttu-id="c2df5-191">环境注意事项HoloLens</span><span class="sxs-lookup"><span data-stu-id="c2df5-191">Environment Considerations for HoloLens</span></span>](/windows/mixed-reality/environment-considerations-for-hololens)
- [<span data-ttu-id="c2df5-192">全息影像稳定性Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c2df5-192">Hologram Stability Windows Mixed Reality</span></span>](/windows/mixed-reality/hologram-stability)
- [<span data-ttu-id="c2df5-193">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="c2df5-193">Focus point in Unity</span></span>](/windows/mixed-reality/focus-point-in-unity)
- [<span data-ttu-id="c2df5-194">Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="c2df5-194">Coordinate systems in Unity</span></span>](/windows/mixed-reality/coordinate-systems-in-unity)
- [<span data-ttu-id="c2df5-195">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="c2df5-195">Persistence in Unity</span></span>](/windows/mixed-reality/persistence-in-unity)
- [<span data-ttu-id="c2df5-196">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="c2df5-196">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="c2df5-197">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="c2df5-197">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)
