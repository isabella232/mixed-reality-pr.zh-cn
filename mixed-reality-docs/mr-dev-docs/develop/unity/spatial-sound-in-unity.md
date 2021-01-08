---
title: Unity 中的空间音效
description: 了解如何使用示例从 Unity 场景内的特定3D 点播放和衰减空间声音。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包，spatializer，回音
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009267"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="6456b-104">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="6456b-104">Spatial sound in Unity</span></span>

<span data-ttu-id="6456b-105">此页链接到 Unity 中的空间音效资源。</span><span class="sxs-lookup"><span data-stu-id="6456b-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="6456b-106">Spatializer 选项</span><span class="sxs-lookup"><span data-stu-id="6456b-106">Spatializer options</span></span>

<span data-ttu-id="6456b-107">混合现实应用程序的 Spatializer 选项包括：</span><span class="sxs-lookup"><span data-stu-id="6456b-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="6456b-108">Unity 将 *MS HRTF Spatializer* 作为 *Windows Mixed Reality* 可选包的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="6456b-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="6456b-109">在较高成本的 "单一源" 体系结构中的 CPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="6456b-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="6456b-110">提供用于与原始 HoloLens 应用程序的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="6456b-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="6456b-111">Microsoft *Spatializer* 在 [microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)中提供。</span><span class="sxs-lookup"><span data-stu-id="6456b-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="6456b-112">使用较低成本的 "多源" 体系结构。</span><span class="sxs-lookup"><span data-stu-id="6456b-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="6456b-113">已卸载到 HoloLens 2 上的硬件加速器。</span><span class="sxs-lookup"><span data-stu-id="6456b-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="6456b-114">对于新应用程序，我们建议 *Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="6456b-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="6456b-115">启用 spatialization</span><span class="sxs-lookup"><span data-stu-id="6456b-115">Enable spatialization</span></span>

<span data-ttu-id="6456b-116">使用 [NuGet For unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 安装 _SpatialAudio_ ，并在项目的音频设置中选择 **microsoft Spatializer** 。</span><span class="sxs-lookup"><span data-stu-id="6456b-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="6456b-117">然后：</span><span class="sxs-lookup"><span data-stu-id="6456b-117">Then:</span></span>
* <span data-ttu-id="6456b-118">将 **音频源** 附加到层次结构中的对象</span><span class="sxs-lookup"><span data-stu-id="6456b-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="6456b-119">选中 " **启用 spatialization** " 复选框</span><span class="sxs-lookup"><span data-stu-id="6456b-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="6456b-120">将 **空间混合** 滑块移动到 "1"</span><span class="sxs-lookup"><span data-stu-id="6456b-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="6456b-121">确保已在开发人员工作站上启用空间音频。</span><span class="sxs-lookup"><span data-stu-id="6456b-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="6456b-122">右键单击任务栏上的 "音量" 图标，并确保 "空间音效" 设置为 "关闭"。</span><span class="sxs-lookup"><span data-stu-id="6456b-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="6456b-123">选择 **Windows Sonic For 耳机** ，以获得您在 HoloLens 2 上听到的最佳表现。</span><span class="sxs-lookup"><span data-stu-id="6456b-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="6456b-124">如果在 Unity 中由于缺少某个依赖项而无法加载 SpatialAudio，请检查你的计算机上是否安装了最新版本的 [Microsoft Visual C++ 可再发行组件](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 。</span><span class="sxs-lookup"><span data-stu-id="6456b-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="6456b-125">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6456b-125">For more information, see:</span></span>
* [<span data-ttu-id="6456b-126">Microsoft spatializer GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="6456b-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="6456b-127">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="6456b-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="6456b-128">Unity 的音频源文档</span><span class="sxs-lookup"><span data-stu-id="6456b-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="6456b-129">Unity 的 spatializer 文档</span><span class="sxs-lookup"><span data-stu-id="6456b-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="6456b-130">基于距离的衰减</span><span class="sxs-lookup"><span data-stu-id="6456b-130">Distance-based attenuation</span></span>

<span data-ttu-id="6456b-131">Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。</span><span class="sxs-lookup"><span data-stu-id="6456b-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="6456b-132">这些设置可能适用于你的方案，你可能会发现源衰减太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="6456b-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="6456b-133">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6456b-133">For more information, see:</span></span>
* <span data-ttu-id="6456b-134">[混合现实中的声音设计](../../design/spatial-sound-design.md) 建议的设置。</span><span class="sxs-lookup"><span data-stu-id="6456b-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="6456b-135">[Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) ，了解有关如何设置这些曲线的说明。</span><span class="sxs-lookup"><span data-stu-id="6456b-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="6456b-136">混响</span><span class="sxs-lookup"><span data-stu-id="6456b-136">Reverb</span></span>

<span data-ttu-id="6456b-137">默认情况下， _Microsoft Spatializer_ 禁用了 Spatializer 效果。</span><span class="sxs-lookup"><span data-stu-id="6456b-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="6456b-138">若要为 spatialized 源启用回响和其他效果：</span><span class="sxs-lookup"><span data-stu-id="6456b-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="6456b-139">将 " **房间效果发送级别** " 组件附加到每个源</span><span class="sxs-lookup"><span data-stu-id="6456b-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="6456b-140">调整每个源的发送级别曲线，以控制发送回图形以进行效果处理的音频的增益</span><span class="sxs-lookup"><span data-stu-id="6456b-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="6456b-141">有关详细信息，请参阅 [spatializer 教程的第5章](tutorials/unity-spatial-audio-ch5.md) 。</span><span class="sxs-lookup"><span data-stu-id="6456b-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="6456b-142">Unity 空间声音示例</span><span class="sxs-lookup"><span data-stu-id="6456b-142">Unity spatial sound examples</span></span>

<span data-ttu-id="6456b-143">有关 Unity 中空间音效的示例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6456b-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="6456b-144">MRTK 演示</span><span class="sxs-lookup"><span data-stu-id="6456b-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="6456b-145">[Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="6456b-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6456b-146">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="6456b-146">Next Development Checkpoint</span></span>

<span data-ttu-id="6456b-147">如果遵循我们所说的 Unity 开发旅程，就是探索混合现实核心构建基块的过程。</span><span class="sxs-lookup"><span data-stu-id="6456b-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="6456b-148">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="6456b-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6456b-149">文本</span><span class="sxs-lookup"><span data-stu-id="6456b-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="6456b-150">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="6456b-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6456b-151">共享体验</span><span class="sxs-lookup"><span data-stu-id="6456b-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="6456b-152">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="6456b-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6456b-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6456b-153">See also</span></span>

* [<span data-ttu-id="6456b-154">混合现实中的声音设计</span><span class="sxs-lookup"><span data-stu-id="6456b-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="6456b-155">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="6456b-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
