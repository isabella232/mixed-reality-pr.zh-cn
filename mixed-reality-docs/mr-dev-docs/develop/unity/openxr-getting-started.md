---
title: 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547055"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="2b331-104">使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="2b331-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="2b331-105">对于面向 Unity 2020 的开发人员构建 HoloLens 2 或混合现实应用程序，可以使用 OpenXR 插件代替 WindowsXR 插件，以实现更好的跨平台兼容性。</span><span class="sxs-lookup"><span data-stu-id="2b331-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="2b331-106">混合现实 OpenXR 插件还适用于最新的 [混合现实工具包 2.7](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="2b331-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b331-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="2b331-107">Prerequisites</span></span>

* <span data-ttu-id="2b331-108">最新 Unity 2020.3 LTS， (建议 2020.3.8 f1 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="2b331-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="2b331-109">最新 Unity OpenXR 插件 (建议1.2 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="2b331-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="2b331-110">[适用于 HoloLens 2 开发的](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="2b331-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="2b331-111">最新的 MRTK (可选) ， (建议2.7 版或更高版本) </span><span class="sxs-lookup"><span data-stu-id="2b331-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="2b331-112">最新混合现实 OpenXR 插件， (建议1.0.0 版-预览版或更高版本) </span><span class="sxs-lookup"><span data-stu-id="2b331-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![在 HoloLens 上运行的开放 xr unity 基本示例的屏幕截图](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="2b331-114">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="2b331-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="2b331-115">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="2b331-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="2b331-116">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="2b331-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="2b331-117">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="2b331-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="2b331-118">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="2b331-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="2b331-119">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="2b331-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b331-120">使用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="2b331-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="2b331-121">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="2b331-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="2b331-122">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="2b331-122">Manual setup without MRTK</span></span>

<span data-ttu-id="2b331-123">安装具有新的混合现实功能工具应用程序的 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="2b331-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="2b331-124">按照 [安装和使用说明](welcome-to-mr-feature-tool.md) ，在混合现实工具包类别中选择 **混合现实 OpenXR 插件** 包：</span><span class="sxs-lookup"><span data-stu-id="2b331-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="2b331-126">设置生成目标</span><span class="sxs-lookup"><span data-stu-id="2b331-126">Setting your build target</span></span>

<span data-ttu-id="2b331-127">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="2b331-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="2b331-129">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="2b331-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="2b331-130">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="2b331-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="2b331-131">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="2b331-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="2b331-132">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="2b331-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="2b331-133">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="2b331-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="2b331-134">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="2b331-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="2b331-135">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="2b331-135">Set **UWP SDK** to **Latest installed**</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="2b331-137">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="2b331-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="2b331-138">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="2b331-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="2b331-139">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="2b331-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="2b331-140">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="2b331-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="2b331-141">选中 " **在启动时初始化 XR"** 和 " **OpenXR** " 框</span><span class="sxs-lookup"><span data-stu-id="2b331-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="2b331-142">如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"</span><span class="sxs-lookup"><span data-stu-id="2b331-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="2b331-144">优化</span><span class="sxs-lookup"><span data-stu-id="2b331-144">Optimization</span></span>

<span data-ttu-id="2b331-145">如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="2b331-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="2b331-147">如果在 " **OpenXR" 插件** 旁出现一个红色警告图标，请单击该图标，然后选择 " **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="2b331-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="2b331-148">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="2b331-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="2b331-150">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="2b331-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="2b331-151">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="2b331-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="2b331-152">适用于 OpenXR 和 HoloLens 2 的 Unity 示例项目</span><span class="sxs-lookup"><span data-stu-id="2b331-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="2b331-153">查看示例 unity 项目的 [OpenXR 混合现实示例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存储库展示如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实耳机构建 unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2b331-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="2b331-154">结合使用 MRTK 与 OpenXR 支持</span><span class="sxs-lookup"><span data-stu-id="2b331-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="2b331-155">MRTK for Unity 版本2.7 现已正式支持混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="2b331-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="2b331-156">再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="2b331-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="2b331-157">OpenXR 支持在 **基础** 包中提供。</span><span class="sxs-lookup"><span data-stu-id="2b331-157">OpenXR support is in the **Foundation** package.</span></span>

![混合现实功能工具 "发现功能" 窗口，其中突出显示了标准资产](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="2b331-159">从 MRTK 的早期版本进行升级时，请确保以下行位于 **资产/MixedRealityToolkit/link.xml** 文件中：</span><span class="sxs-lookup"><span data-stu-id="2b331-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="2b331-160">如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。</span><span class="sxs-lookup"><span data-stu-id="2b331-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2b331-161">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2b331-161">Next steps</span></span>

<span data-ttu-id="2b331-162">现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="2b331-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="2b331-163">是否有反馈？</span><span class="sxs-lookup"><span data-stu-id="2b331-163">Have Feedback?</span></span>

<span data-ttu-id="2b331-164">OpenXR 仍是实验性的，因此我们非常感谢你的反馈，你可以向我们提供更好的帮助。</span><span class="sxs-lookup"><span data-stu-id="2b331-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="2b331-165">你将在 [Unity 论坛](https://aka.ms/unityforums)上查找我们，方法是使用 **Microsoft**  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 标记论坛帖子。</span><span class="sxs-lookup"><span data-stu-id="2b331-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b331-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b331-166">See also</span></span>

* [<span data-ttu-id="2b331-167">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="2b331-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="2b331-168">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="2b331-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="2b331-169">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="2b331-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
