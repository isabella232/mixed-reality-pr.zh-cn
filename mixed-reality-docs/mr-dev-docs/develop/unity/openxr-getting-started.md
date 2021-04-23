---
title: 为 Unity 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 97169507e2b61110d2d16580ba957feff3755258
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894009"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="8cb01-104">为 Unity 使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="8cb01-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="8cb01-105">从 Unity 版本2020.2 开始，Microsoft 的 Mixed Reality OpenXR 插件包可通过 Unity 包管理器 (UPM) 提供。</span><span class="sxs-lookup"><span data-stu-id="8cb01-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8cb01-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="8cb01-106">Prerequisites</span></span>

* <span data-ttu-id="8cb01-107">Unity 2020.3 LTS 或更高版本</span><span class="sxs-lookup"><span data-stu-id="8cb01-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="8cb01-108">Unity OpenXR 插件1.1.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="8cb01-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="8cb01-109">Visual Studio 2019 或更高版本</span><span class="sxs-lookup"><span data-stu-id="8cb01-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="8cb01-110">在适用于 HoloLens 2 应用的 Unity 中安装 **UWP** 平台支持</span><span class="sxs-lookup"><span data-stu-id="8cb01-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="8cb01-111">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="8cb01-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="8cb01-112">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="8cb01-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="8cb01-113">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="8cb01-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="8cb01-114">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="8cb01-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8cb01-115">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="8cb01-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="8cb01-116">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="8cb01-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8cb01-117">使用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="8cb01-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="8cb01-118">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="8cb01-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="8cb01-119">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="8cb01-119">Manual setup without MRTK</span></span>

<span data-ttu-id="8cb01-120">安装具有新的混合现实功能工具应用程序的 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="8cb01-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="8cb01-121">按照 [安装和使用说明](welcome-to-mr-feature-tool.md) ，在混合现实工具包类别中选择 **混合现实 OpenXR 插件** 包：</span><span class="sxs-lookup"><span data-stu-id="8cb01-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="8cb01-123">设置生成目标</span><span class="sxs-lookup"><span data-stu-id="8cb01-123">Setting your build target</span></span>

<span data-ttu-id="8cb01-124">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="8cb01-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="8cb01-126">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="8cb01-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="8cb01-127">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="8cb01-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8cb01-128">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="8cb01-129">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="8cb01-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="8cb01-130">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="8cb01-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="8cb01-131">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="8cb01-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="8cb01-132">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="8cb01-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="8cb01-133">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="8cb01-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="8cb01-135">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="8cb01-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="8cb01-136">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="8cb01-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="8cb01-137">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="8cb01-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="8cb01-138">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="8cb01-139">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="8cb01-140">选中 " **在启动时初始化 XR"** 和 " **OpenXR** " 框</span><span class="sxs-lookup"><span data-stu-id="8cb01-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="8cb01-141">如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="8cb01-143">优化</span><span class="sxs-lookup"><span data-stu-id="8cb01-143">Optimization</span></span>

<span data-ttu-id="8cb01-144">如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="8cb01-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="8cb01-146">如果在 " **OpenXR" 插件** 旁出现一个红色警告图标，请单击该图标，然后选择 " **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="8cb01-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="8cb01-147">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="8cb01-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="8cb01-149">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="8cb01-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="8cb01-150">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="8cb01-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="8cb01-151">试用 Unity 示例场景</span><span class="sxs-lookup"><span data-stu-id="8cb01-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="8cb01-152">HoloLens 2 示例</span><span class="sxs-lookup"><span data-stu-id="8cb01-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="8cb01-153">在 Unity 编辑器中，导航到 "**窗口 >" 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="8cb01-154">在包列表中，选择 " **混合现实 OpenXR" 插件**</span><span class="sxs-lookup"><span data-stu-id="8cb01-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="8cb01-155">在 **示例** 列表中找到示例，然后选择 "**导入**"</span><span class="sxs-lookup"><span data-stu-id="8cb01-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![已在 Unity 编辑器中打开 Unity 包管理器的屏幕截图，并选中混合现实 OpenXR 插件，并突出显示示例导入按钮](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="8cb01-157">更新包时，Unity 提供更新导入的示例的选项。</span><span class="sxs-lookup"><span data-stu-id="8cb01-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="8cb01-158">更新导入的示例将覆盖对示例和关联的资产所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="8cb01-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="8cb01-159">结合使用 MRTK 与 OpenXR 支持</span><span class="sxs-lookup"><span data-stu-id="8cb01-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="8cb01-160">从2.5.3 版本开始，MRTK-Unity 支持混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="8cb01-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="8cb01-161">再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="8cb01-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="8cb01-162">OpenXR 支持在 **基础** 包中提供。</span><span class="sxs-lookup"><span data-stu-id="8cb01-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="8cb01-163">转到检查器中的 MixedReality 工具包组件脚本，并切换到 **DefaultOpenXRConfigurationProfile** 配置文件：</span><span class="sxs-lookup"><span data-stu-id="8cb01-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![在检查器的混合现实工具包组件中切换 MRTK 配置的屏幕截图](images/openxr-img-11.png)

    1. <span data-ttu-id="8cb01-165">有关 [迁移到 OpenXR 的更深入信息](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，请参阅 MRTK 文档。</span><span class="sxs-lookup"><span data-stu-id="8cb01-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="8cb01-166">从 MRTK 的早期版本进行升级时，请确保以下行位于 **资产/MixedRealityToolkit/link.xml** 文件中：</span><span class="sxs-lookup"><span data-stu-id="8cb01-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="8cb01-167">如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。</span><span class="sxs-lookup"><span data-stu-id="8cb01-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8cb01-168">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8cb01-168">Next steps</span></span>

<span data-ttu-id="8cb01-169">现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="8cb01-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="8cb01-170">是否有反馈？</span><span class="sxs-lookup"><span data-stu-id="8cb01-170">Have Feedback?</span></span>

<span data-ttu-id="8cb01-171">OpenXR 仍是实验性的，因此我们非常感谢你的反馈，你可以向我们提供更好的帮助。</span><span class="sxs-lookup"><span data-stu-id="8cb01-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="8cb01-172">你将在 [Unity 论坛](https://aka.ms/unityforums)上查找我们，方法是使用 **Microsoft**  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 标记论坛帖子。</span><span class="sxs-lookup"><span data-stu-id="8cb01-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cb01-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cb01-173">See also</span></span>

* [<span data-ttu-id="8cb01-174">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="8cb01-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="8cb01-175">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="8cb01-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="8cb01-176">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="8cb01-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
