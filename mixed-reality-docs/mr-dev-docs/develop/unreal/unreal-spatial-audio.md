---
title: Unreal 中的空间音频
description: 了解适合 HoloLens 设备的 Unreal 混合现实应用程序的空间音频插件的详细信息。
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 空间音频
ms.openlocfilehash: fdb4f401188a813b99884929cd835453dec5aaf0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98580430"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="f53f9-104">Unreal 中的空间音频</span><span class="sxs-lookup"><span data-stu-id="f53f9-104">Spatial Audio in Unreal</span></span>

<span data-ttu-id="f53f9-105">与视觉不同，人类能听到 360 度环绕声。</span><span class="sxs-lookup"><span data-stu-id="f53f9-105">Unlike vision, humans hear in 360-degree surround sound.</span></span> <span data-ttu-id="f53f9-106">空间音效模拟人类听觉的工作方式，从而提供识别世界空间中的声音位置所需的提示。</span><span class="sxs-lookup"><span data-stu-id="f53f9-106">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="f53f9-107">通过在你的混合现实应用程序中添加空间音效，可以提高用户所体验的沉浸感程度。</span><span class="sxs-lookup"><span data-stu-id="f53f9-107">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your user's experience.</span></span>  

<span data-ttu-id="f53f9-108">高质量的空间音效处理比较复杂，因此，HoloLens 2 附带了用于处理这些声音对象的专用硬件。</span><span class="sxs-lookup"><span data-stu-id="f53f9-108">High-quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="f53f9-109">在使用此硬件处理支持之前，需要在 Unreal 项目中安装 MicrosoftSpatialSound 插件。</span><span class="sxs-lookup"><span data-stu-id="f53f9-109">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="f53f9-110">本文将逐步指导你完成该插件的安装和配置，并且将提供更多相关深度资源。</span><span class="sxs-lookup"><span data-stu-id="f53f9-110">This article will walk you through the installation and configuration of the plugin and point you towards more in-depth resources.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="f53f9-111">安装 Microsoft 空间音效插件</span><span class="sxs-lookup"><span data-stu-id="f53f9-111">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="f53f9-112">向项目添加空间音效的第一步是安装 Microsoft 空间音效插件，可通过以下方式找到该插件：</span><span class="sxs-lookup"><span data-stu-id="f53f9-112">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="f53f9-113">单击“编辑”>“插件”，然后在搜索框中搜索“MicrosoftSpatialSound” 。</span><span class="sxs-lookup"><span data-stu-id="f53f9-113">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="f53f9-114">在 MicrosoftSpatialSound 插件中选择“已启用”复选框 。</span><span class="sxs-lookup"><span data-stu-id="f53f9-114">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="f53f9-115">从插件页面选择“立即重启”来重启 Unreal 编辑器。</span><span class="sxs-lookup"><span data-stu-id="f53f9-115">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="f53f9-116">如果尚未安装 Microsoft Windows Mixed Reality 和 HoloLens 插件，需要按照我们 Unreal 教程系列[初始化你的项目](tutorials/unreal-uxt-ch2.md)部分中的说明进行安装  。</span><span class="sxs-lookup"><span data-stu-id="f53f9-116">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal 空间音频插件](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="f53f9-118">待编辑器重启后，你的项目就已就绪了！</span><span class="sxs-lookup"><span data-stu-id="f53f9-118">Once the editor restarts, your project is all set!</span></span>

## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="f53f9-119">设置 HoloLens 2 平台的空间化插件</span><span class="sxs-lookup"><span data-stu-id="f53f9-119">Setting the spatialization plugin for HoloLens 2 platform</span></span>

<span data-ttu-id="f53f9-120">配置空间化插件是以每个平台为基础进行的。</span><span class="sxs-lookup"><span data-stu-id="f53f9-120">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="f53f9-121">可以通过以下方式为 HoloLens 2 启用 Microsoft 空间音效插件：</span><span class="sxs-lookup"><span data-stu-id="f53f9-121">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="f53f9-122">选择“编辑”>“项目设置”，滚动到“平台”，然后单击“HoloLens” 。</span><span class="sxs-lookup"><span data-stu-id="f53f9-122">Selecting **Edit > Project Settings**, scrolling to \*\*Platforms, and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="f53f9-123">展开“音频”属性，并将“空间化插件”字段设置为“Microsoft 空间音效”  。</span><span class="sxs-lookup"><span data-stu-id="f53f9-123">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![HoloLens 平台的空间化插件](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="f53f9-125">如果要在台式电脑上的 Unreal 编辑器中预览应用程序，则需要针对 Windows 平台重复执行上述步骤：</span><span class="sxs-lookup"><span data-stu-id="f53f9-125">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Windows 平台的空间化插件](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="f53f9-127">在工作站上启用空间音频</span><span class="sxs-lookup"><span data-stu-id="f53f9-127">Enabling spatial audio on your workstation</span></span>

<span data-ttu-id="f53f9-128">空间音频在 Windows 桌面版上默认处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="f53f9-128">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="f53f9-129">可以通过以下方式启用它：</span><span class="sxs-lookup"><span data-stu-id="f53f9-129">You can enable it by:</span></span>
* <span data-ttu-id="f53f9-130">右键单击任务栏中的“音量”图标。</span><span class="sxs-lookup"><span data-stu-id="f53f9-130">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="f53f9-131">选择“空间音效”->“用于耳机的 Windows Sonic”以获得在 HoloLens 2 上所听到的声音的最佳呈现效果。</span><span class="sxs-lookup"><span data-stu-id="f53f9-131">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![空间化插件](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="f53f9-133">仅当你计划在 Unreal 编辑器中测试项目时才需要此设置。</span><span class="sxs-lookup"><span data-stu-id="f53f9-133">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="f53f9-134">创建衰减对象</span><span class="sxs-lookup"><span data-stu-id="f53f9-134">Creating Attenuation objects</span></span>

<span data-ttu-id="f53f9-135">安装并配置了必要插件后：</span><span class="sxs-lookup"><span data-stu-id="f53f9-135">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="f53f9-136">在“放置参与者”窗口中搜索“环境声”参与者，并将它拖到“场景”窗口中  。</span><span class="sxs-lookup"><span data-stu-id="f53f9-136">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![添加“环境声”参与者](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="f53f9-138">将“环境声”参与者设置为场景中可视元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="f53f9-138">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="f53f9-139">默认情况下，“环境声”参与者没有任何可视表示形式，因此你只能听到从它在场景中所处的位置传来的声音。</span><span class="sxs-lookup"><span data-stu-id="f53f9-139">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="f53f9-140">将它附加到可视元素后，就可以像对待任何其他资产一样查看和移动此参与者。</span><span class="sxs-lookup"><span data-stu-id="f53f9-140">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="f53f9-141">右键单击“内容浏览器”，然后选择“创建高级资产”->“声音”->“声音衰减” ：</span><span class="sxs-lookup"><span data-stu-id="f53f9-141">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![创建声音衰减资产](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="f53f9-143">右键单击“内容浏览器”窗口中的“声音衰减”资产，然后选择“编辑”选项以打开属性窗口  。</span><span class="sxs-lookup"><span data-stu-id="f53f9-143">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="f53f9-144">将“空间化方法”切换到“双声道” 。</span><span class="sxs-lookup"><span data-stu-id="f53f9-144">Switch the **Spatialization Method** to **Binaural**.</span></span>

![设置空间化方法](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="f53f9-146">选择“环境声”参与者，然后向下滚动到“详细信息”面板中的“衰减”部分  。</span><span class="sxs-lookup"><span data-stu-id="f53f9-146">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="f53f9-147">将“衰减设置”属性设置为你创建的声音衰减资产 。</span><span class="sxs-lookup"><span data-stu-id="f53f9-147">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![设置衰减设置](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="f53f9-149">设置要附加到环境声参与者的“声音资产”：</span><span class="sxs-lookup"><span data-stu-id="f53f9-149">Set the **Sound Asset** you want to attach to the Ambient Sound actor:</span></span>
    * <span data-ttu-id="f53f9-150">更新环境声参与者的“声音”属性，以指定要使用的 SoundAsset 文件。</span><span class="sxs-lookup"><span data-stu-id="f53f9-150">Update the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![设置声音资产](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="f53f9-152">SoundAsset 文件需要为单声道，这样才能使用 Microsoft 空间音效插件对它进行空间化处理。</span><span class="sxs-lookup"><span data-stu-id="f53f9-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="f53f9-153">可以通过将鼠标悬停在“内容浏览器”窗口中的资产上来找到声音文件属性，如以下屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="f53f9-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![新的声音衰减资产](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="f53f9-155">完成声音资产配置后，即可使用 HoloLens 2 上的专用硬件卸载支持对环境声进行空间化处理。</span><span class="sxs-lookup"><span data-stu-id="f53f9-155">When the sound asset is configured, the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="f53f9-156">配置空间化对象</span><span class="sxs-lookup"><span data-stu-id="f53f9-156">Configuring objects for spatialization</span></span>

<span data-ttu-id="f53f9-157">使用空间音频意味着你需要管理声音在虚拟环境中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="f53f9-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="f53f9-158">你的主要目标是创建声音对象，这些对象的特征是当用户靠近时声音会更大，而当用户远离时声音会更小。</span><span class="sxs-lookup"><span data-stu-id="f53f9-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="f53f9-159">这称为声音衰减，使声音听起来就像是被放在一个固定地点一样。</span><span class="sxs-lookup"><span data-stu-id="f53f9-159">This is referred to as sound attenuation, making sounds appear as if they're positioned in a fixed spot.</span></span>

<span data-ttu-id="f53f9-160">所有衰减对象都有针对以下各项的可修改设置：</span><span class="sxs-lookup"><span data-stu-id="f53f9-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="f53f9-161">距离</span><span class="sxs-lookup"><span data-stu-id="f53f9-161">Distance</span></span>
* <span data-ttu-id="f53f9-162">空间化</span><span class="sxs-lookup"><span data-stu-id="f53f9-162">Spatialization</span></span>
* <span data-ttu-id="f53f9-163">空气吸收</span><span class="sxs-lookup"><span data-stu-id="f53f9-163">Air Absorption</span></span>
* <span data-ttu-id="f53f9-164">侦听器聚焦</span><span class="sxs-lookup"><span data-stu-id="f53f9-164">Listener Focus</span></span>
* <span data-ttu-id="f53f9-165">混响发送</span><span class="sxs-lookup"><span data-stu-id="f53f9-165">Reverb Send</span></span>
* <span data-ttu-id="f53f9-166">封闭</span><span class="sxs-lookup"><span data-stu-id="f53f9-166">Occlusion</span></span>

<span data-ttu-id="f53f9-167">[Unreal 中的声音衰减](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)提供了有关这些主题的详细信息和实现细节。</span><span class="sxs-lookup"><span data-stu-id="f53f9-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f53f9-168">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="f53f9-168">Next Development Checkpoint</span></span>

<span data-ttu-id="f53f9-169">如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。</span><span class="sxs-lookup"><span data-stu-id="f53f9-169">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f53f9-170">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="f53f9-170">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f53f9-171">语音输入</span><span class="sxs-lookup"><span data-stu-id="f53f9-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="f53f9-172">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="f53f9-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f53f9-173">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="f53f9-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="f53f9-174">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="f53f9-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="f53f9-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f53f9-175">See also</span></span>
* [<span data-ttu-id="f53f9-176">空间音效</span><span class="sxs-lookup"><span data-stu-id="f53f9-176">Spatial Sound</span></span>](/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="f53f9-177">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="f53f9-177">Spatial Sound Design</span></span>](/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="f53f9-178">MR 空间 220：空间音效</span><span class="sxs-lookup"><span data-stu-id="f53f9-178">MR Spatial 220: Spatial sound</span></span>](/windows/mixed-reality/holograms-220)