---
title: 空间音频教程-1。 向项目添加空间音频
description: 将 Microsoft Spatializer 插件添加到 Unity 项目以访问 HoloLens 2 HRTF 硬件卸载。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: 9ddfd1644a20ac063551b8140f9f8950ae172196
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678596"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="08091-105">将空间音频添加到 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="08091-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="08091-106">欢迎使用 HoloLens2 上 Unity 的空间音频教程。</span><span class="sxs-lookup"><span data-stu-id="08091-106">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="08091-107">本教程序列显示：</span><span class="sxs-lookup"><span data-stu-id="08091-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="08091-108">如何在 Unity 中使用与头相关的传输函数 (HRTF) 在 HoloLens 2 上卸载</span><span class="sxs-lookup"><span data-stu-id="08091-108">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="08091-109">如何在使用 HRTF 卸载时启用回响</span><span class="sxs-lookup"><span data-stu-id="08091-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="08091-110">[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)包含此教程序列的已完成 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="08091-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="08091-111">若要了解如何使用基于 HRTF 的 spatialization 技术来 spatialize 声音，并提供有关其有用情况的建议，请参阅 [空间音效设计](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="08091-111">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="08091-112">什么是 HRTF 卸载？</span><span class="sxs-lookup"><span data-stu-id="08091-112">What is HRTF offload?</span></span>
<span data-ttu-id="08091-113">使用基于 HRTF 的算法处理音频需要大量的专用计算。</span><span class="sxs-lookup"><span data-stu-id="08091-113">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="08091-114">HoloLens 2 包括专用硬件，可以利用这些硬件来避免应用程序处理器的负担，从而将处理基于 HRTF 的算法。</span><span class="sxs-lookup"><span data-stu-id="08091-114">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="08091-115">Microsoft spatializer 插件为应用程序提供了一种简单的方法，使应用程序能够利用专用的 HRTF 硬件，使应用程序可以将更多应用程序处理器用于除了空间音频以外的其他操作。</span><span class="sxs-lookup"><span data-stu-id="08091-115">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="08091-116">目标</span><span class="sxs-lookup"><span data-stu-id="08091-116">Objectives</span></span>
<span data-ttu-id="08091-117">在第一章中，你将：</span><span class="sxs-lookup"><span data-stu-id="08091-117">In this first chapter, you'll:</span></span>
* <span data-ttu-id="08091-118">创建 Unity 项目并导入 MRTK</span><span class="sxs-lookup"><span data-stu-id="08091-118">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="08091-119">导入 Microsoft spatializer 插件</span><span class="sxs-lookup"><span data-stu-id="08091-119">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="08091-120">启用 Microsoft spatializer 插件</span><span class="sxs-lookup"><span data-stu-id="08091-120">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="08091-121">启用开发人员工作站上的空间音频</span><span class="sxs-lookup"><span data-stu-id="08091-121">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="08091-122">创建项目并为 Unity 添加 NuGet</span><span class="sxs-lookup"><span data-stu-id="08091-122">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="08091-123">从空 Unity 项目开始，为 Unity 添加并配置 NuGet：</span><span class="sxs-lookup"><span data-stu-id="08091-123">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="08091-124">下载最新的 [NuGetForUnity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="08091-124">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="08091-125">在 Unity 菜单栏中，单击 " **资产-> 导入包-> 自定义包 ...** " 并安装 NuGetForUnity 包：</span><span class="sxs-lookup"><span data-stu-id="08091-125">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![导入自定义包](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="08091-127">添加 Windows Mixed Reality 包</span><span class="sxs-lookup"><span data-stu-id="08091-127">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="08091-128">Unity 2019 和更高版本中的 Windows Mixed Reality 支持包含在一个可选的包中。</span><span class="sxs-lookup"><span data-stu-id="08091-128">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="08091-129">若要将其添加到项目，请从 Unity 菜单栏中打开 " **> 包管理器** "：</span><span class="sxs-lookup"><span data-stu-id="08091-129">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![程序包管理器菜单](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="08091-131">然后查找并安装 **Windows Mixed Reality** 包：</span><span class="sxs-lookup"><span data-stu-id="08091-131">Then find and install the **Windows Mixed Reality** package:</span></span>

!["程序包管理器" 窗口](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="08091-133">安装 MRTK 和 Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="08091-133">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="08091-134">使用 NuGet for Unity，安装 MRTK 和 Microsoft Spatializer 插件：</span><span class="sxs-lookup"><span data-stu-id="08091-134">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="08091-135">在 Unity 菜单栏中，单击 " **nuget-> 管理 Nuget 包** "。</span><span class="sxs-lookup"><span data-stu-id="08091-135">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages** .</span></span>

![管理 NuGet 包](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="08091-137">在 " **搜索** " 框中，输入 "MixedReality" 并安装 MRTK 核心包： **MixedReality**</span><span class="sxs-lookup"><span data-stu-id="08091-137">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet 包](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="08091-139">[MRTK NuGet 包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) 具有其他上下文和详细信息。</span><span class="sxs-lookup"><span data-stu-id="08091-139">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="08091-140">在 **搜索** 框中，输入 "SpatialAudio"，并安装 microsoft Spatializer Package： **SpatialAudio. Spatializer**</span><span class="sxs-lookup"><span data-stu-id="08091-140">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer 插件 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="08091-142">在项目中设置 MRTK</span><span class="sxs-lookup"><span data-stu-id="08091-142">Set up MRTK in your project</span></span>

1. <span data-ttu-id="08091-143">转到 " **文件 > 生成设置** "，打开 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="08091-143">Open the Build Settings window by going to **File -> Build Settings** .</span></span>

2. <span data-ttu-id="08091-144">选择 " _通用 Windows 平台_ "，然后单击 " **切换平台** "。</span><span class="sxs-lookup"><span data-stu-id="08091-144">Select the _Universal Windows Platform_ and click **Switch Platform** .</span></span>

3. <span data-ttu-id="08091-145">单击 " **生成" 窗口** 中的 " **播放机设置** "，在 " **检查器** " 窗格中打开 **播放机设置** 属性。</span><span class="sxs-lookup"><span data-stu-id="08091-145">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="08091-146">在 " **XR 设置** " 下，选中 " **支持虚拟现实** " 复选框</span><span class="sxs-lookup"><span data-stu-id="08091-146">Under **XR Settings** , check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="08091-147">在 " **XR 设置** " 下，将 **立体声渲染模式** 更改为 **单步实例** 。</span><span class="sxs-lookup"><span data-stu-id="08091-147">Under **XR Settings** , change the **Stereo Rendering Mode** to **Single Pass Instanced** .</span></span>
    * <span data-ttu-id="08091-148">在 " **发布设置** " 下的 " **功能** " 部分中，选中 " **空间感知** " 复选框</span><span class="sxs-lookup"><span data-stu-id="08091-148">Under **Publishing Settings** , check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="08091-149">在菜单栏上，单击 " **混合现实工具包-> 添加到场景并配置 ...** "。</span><span class="sxs-lookup"><span data-stu-id="08091-149">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="08091-150">将 MRTK 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="08091-150">to add MRTK to your scene.</span></span>

<span data-ttu-id="08091-151">有关其他指南，包括如何生成应用并将其部署到 HoloLens 2，请参阅 [尊敬的学习基础模块第1章](../../../mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="08091-151">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="08091-152">启用 Microsoft Spatializer 插件</span><span class="sxs-lookup"><span data-stu-id="08091-152">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="08091-153">启用 **Microsoft Spatializer** 插件。</span><span class="sxs-lookup"><span data-stu-id="08091-153">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="08091-154">打开 **> 项目设置-> 音频** "，然后将 **Spatializer 插件** 更改为" Microsoft Spatializer "。</span><span class="sxs-lookup"><span data-stu-id="08091-154">Open **Edit -> Project Settings -> Audio** , and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="08091-155">**项目设置** 的 " **音频** " 部分现在将如下所示：</span><span class="sxs-lookup"><span data-stu-id="08091-155">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![显示 spatializer 插件的项目设置](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="08091-157">启用工作站上的空间音频</span><span class="sxs-lookup"><span data-stu-id="08091-157">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="08091-158">在桌面版本的 Windows 上，默认情况下禁用空间音频。</span><span class="sxs-lookup"><span data-stu-id="08091-158">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="08091-159">右键单击任务栏中的音量图标即可启用此项。</span><span class="sxs-lookup"><span data-stu-id="08091-159">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="08091-160">若要获得有关在 HoloLens 2 上收到的内容的最佳表示，请选择 " **空间音效-> Windows Sonic 用于耳机** "。</span><span class="sxs-lookup"><span data-stu-id="08091-160">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones** .</span></span>

![桌面空间音频设置](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="08091-162">仅当计划在 Unity 编辑器中测试项目时，才需要此设置。</span><span class="sxs-lookup"><span data-stu-id="08091-162">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="08091-163">后续步骤</span><span class="sxs-lookup"><span data-stu-id="08091-163">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="08091-164">Unity 空间音频第2章</span><span class="sxs-lookup"><span data-stu-id="08091-164">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

