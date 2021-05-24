---
title: 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333439"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="be403-104">使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="be403-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="be403-105">对于面向 Unity 2020 的开发人员构建 HoloLens 2 或混合现实应用程序，可以使用 OpenXR 插件代替 WindowsXR 插件，以实现更好的跨平台兼容性。</span><span class="sxs-lookup"><span data-stu-id="be403-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="be403-106">混合现实 OpenXR 插件还适用于最新的 [混合现实功能工具](welcome-to-mr-feature-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="be403-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be403-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="be403-107">Prerequisites</span></span>

* <span data-ttu-id="be403-108">最新 Unity 2020.3 LTS，建议 2020.3.6 f1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="be403-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="be403-109">最新 Unity OpenXR 插件，建议1.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="be403-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="be403-110">[适用于 HoloLens 2 开发的](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="be403-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="be403-111">最新 MRTK (可选) ，建议版本2.6 或更高版本</span><span class="sxs-lookup"><span data-stu-id="be403-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="be403-112">最新混合现实 OpenXR 插件，建议版本0.9.5 或更高版本</span><span class="sxs-lookup"><span data-stu-id="be403-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="be403-113">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="be403-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="be403-114">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="be403-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="be403-115">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="be403-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="be403-116">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="be403-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="be403-117">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="be403-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="be403-118">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="be403-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be403-119">使用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="be403-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="be403-120">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="be403-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="be403-121">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="be403-121">Manual setup without MRTK</span></span>

<span data-ttu-id="be403-122">安装具有新的混合现实功能工具应用程序的 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="be403-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="be403-123">按照 [安装和使用说明](welcome-to-mr-feature-tool.md) ，在混合现实工具包类别中选择 **混合现实 OpenXR 插件** 包：</span><span class="sxs-lookup"><span data-stu-id="be403-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="be403-125">设置生成目标</span><span class="sxs-lookup"><span data-stu-id="be403-125">Setting your build target</span></span>

<span data-ttu-id="be403-126">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="be403-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="be403-128">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="be403-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="be403-129">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="be403-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="be403-130">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="be403-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="be403-131">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="be403-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="be403-132">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="be403-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="be403-133">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="be403-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="be403-134">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="be403-134">Set **UWP SDK** to **Latest installed**</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="be403-136">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="be403-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="be403-137">若要在 Unity 中将 OpenXR 设置为运行时，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="be403-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="be403-138">在 Unity 编辑器中，导航到 **"编辑>项目设置"**</span><span class="sxs-lookup"><span data-stu-id="be403-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="be403-139">在"设置"列表中，选择 **"XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="be403-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="be403-140">选中"**启动时初始化 XR"和\*\*\*\*"OpenXR"** 框</span><span class="sxs-lookup"><span data-stu-id="be403-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="be403-141">如果以HoloLens 2为目标，请确保你位于 UWP 平台上，然后选择"Microsoft HoloLens **功能集"**</span><span class="sxs-lookup"><span data-stu-id="be403-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="be403-143">优化</span><span class="sxs-lookup"><span data-stu-id="be403-143">Optimization</span></span>

<span data-ttu-id="be403-144">如果要针对 HoloLens 2 进行开发，请导航到"混合现实> **OpenXR >应用** 针对 HoloLens 2 的建议项目设置，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="be403-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已选中 OpenXR 的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="be403-146">如果在 **OpenXR** 插件旁边看到红色警告图标，请单击该图标并选择" **全部修复** "，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="be403-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="be403-147">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="be403-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="be403-149">现在，你已准备好在 Unity 中开始使用 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="be403-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="be403-150">继续学习下一部分，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="be403-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="be403-151">OpenXR 和 HoloLens 2 的 Unity 示例项目</span><span class="sxs-lookup"><span data-stu-id="be403-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="be403-152">请查看 [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 示例存储库，了解示例 Unity 项目，了解如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实头戴显示设备生成 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="be403-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="be403-153">使用具有 OpenXR 支持的 MRTK</span><span class="sxs-lookup"><span data-stu-id="be403-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="be403-154">MRTK-Unity 2.5.3 版开始，支持混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="be403-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="be403-155">再次 [打开混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="be403-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="be403-156">OpenXR 支持位于 **Foundation 包** 中。</span><span class="sxs-lookup"><span data-stu-id="be403-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="be403-157">转到检查器中的 MixedReality Toolkit 组件脚本，并切换到 **DefaultOpenXRConfigurationProfile** 配置文件：</span><span class="sxs-lookup"><span data-stu-id="be403-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![在检查器中切换混合现实工具包组件中的 MRTK 配置的屏幕截图](images/openxr-img-11.png)

    1. <span data-ttu-id="be403-159">有关迁移到 OpenXR 的更深入的信息，请参阅 [MRTK 文档](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)。</span><span class="sxs-lookup"><span data-stu-id="be403-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="be403-160">从以前版本的 MRTK 升级时，请确保以下行位于 **Assets/MixedRealityToolkit.Generated/link.xml** 文件中：</span><span class="sxs-lookup"><span data-stu-id="be403-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="be403-161">如果从 MRTK 2.5.4 或更高版本开始，则默认情况下将添加此行。</span><span class="sxs-lookup"><span data-stu-id="be403-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="be403-162">后续步骤</span><span class="sxs-lookup"><span data-stu-id="be403-162">Next steps</span></span>

<span data-ttu-id="be403-163">为 OpenXR 配置项目并有权访问示例后，请查看 OpenXR 插件中[](openxr-supported-features.md)当前支持的功能。</span><span class="sxs-lookup"><span data-stu-id="be403-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="be403-164">有反馈？</span><span class="sxs-lookup"><span data-stu-id="be403-164">Have Feedback?</span></span>

<span data-ttu-id="be403-165">OpenXR 仍处于试验阶段，因此，我们感谢你提供的任何反馈来帮助改进它。</span><span class="sxs-lookup"><span data-stu-id="be403-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="be403-166">使用 [](https://aka.ms/unityforums)**Microsoft**  +  **OpenXR** 标记你的论坛帖子，并HoloLens 2或 Windows Mixed Reality。 </span><span class="sxs-lookup"><span data-stu-id="be403-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="be403-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be403-167">See also</span></span>

* [<span data-ttu-id="be403-168">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="be403-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="be403-169">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="be403-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="be403-170">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="be403-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
