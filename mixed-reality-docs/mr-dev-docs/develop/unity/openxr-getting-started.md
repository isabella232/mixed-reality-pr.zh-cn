---
title: 为 Unity 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: cae588acbcddeefae45a555f335f1c74389f1824
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496165"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="a173d-104">为 Unity 使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="a173d-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="a173d-105">从 Unity 版本2020.2 开始，Microsoft 的 Mixed Reality OpenXR 插件包可通过 Unity 包管理器 (UPM) 提供。</span><span class="sxs-lookup"><span data-stu-id="a173d-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a173d-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="a173d-106">Prerequisites</span></span>

* <span data-ttu-id="a173d-107">Unity 2020.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a173d-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="a173d-108">Unity OpenXR 插件0.1.3 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a173d-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="a173d-109">Visual Studio 2019 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a173d-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="a173d-110">在适用于 HoloLens 2 应用的 Unity 中安装 **UWP** 平台支持</span><span class="sxs-lookup"><span data-stu-id="a173d-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="a173d-111">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="a173d-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="a173d-112">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="a173d-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="a173d-113">通过混合现实功能工具安装 OpenXR</span><span class="sxs-lookup"><span data-stu-id="a173d-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="a173d-114">安装具有新的混合现实功能工具应用程序的 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="a173d-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="a173d-115">按照 [安装和使用说明](welcome-to-mr-feature-tool.md) ，在混合现实工具包类别中选择 **混合现实 OpenXR 插件** 包：</span><span class="sxs-lookup"><span data-stu-id="a173d-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="a173d-117">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="a173d-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="a173d-118">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="a173d-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="a173d-119">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="a173d-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="a173d-120">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="a173d-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="a173d-121">选中 " **在启动时初始化 XR"** 和 " **OpenXR (预览")** 框</span><span class="sxs-lookup"><span data-stu-id="a173d-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="a173d-122">如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"</span><span class="sxs-lookup"><span data-stu-id="a173d-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="a173d-124">如果在 OpenXR 插件旁边出现一个红色警告图标 **(预览 ")**，请单击该图标，然后选择" **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="a173d-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="a173d-125">Unity 编辑器可能需要重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="a173d-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="a173d-127">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="a173d-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="a173d-128">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="a173d-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="a173d-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="a173d-129">Optimization</span></span>

<span data-ttu-id="a173d-130">如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="a173d-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="a173d-132">试用 Unity 示例场景</span><span class="sxs-lookup"><span data-stu-id="a173d-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="a173d-133">若要利用一个或多个示例，请从 **包管理器** 安装 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：</span><span class="sxs-lookup"><span data-stu-id="a173d-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了 AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="a173d-135">HoloLens 2 示例</span><span class="sxs-lookup"><span data-stu-id="a173d-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="a173d-136">在 Unity 编辑器中，导航到 "**窗口 >" 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="a173d-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="a173d-137">在包列表中，选择 " **混合现实 OpenXR" 插件**</span><span class="sxs-lookup"><span data-stu-id="a173d-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="a173d-138">在 **示例** 列表中找到示例，然后选择 "**导入**"</span><span class="sxs-lookup"><span data-stu-id="a173d-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![已在 Unity 编辑器中打开 Unity 包管理器的屏幕截图，并选中混合现实 OpenXR 插件，并突出显示示例导入按钮](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="a173d-140">更新包时，Unity 提供更新导入的示例的选项。</span><span class="sxs-lookup"><span data-stu-id="a173d-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="a173d-141">更新导入的示例将覆盖对示例和关联的资产所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="a173d-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="a173d-142">结合使用 MRTK 与 OpenXR 支持</span><span class="sxs-lookup"><span data-stu-id="a173d-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="a173d-143">从2.5.3 版本开始，MRTK Unity 支持混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="a173d-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="a173d-144">再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) ，并在平台支持类别中选择 **混合现实 OpenXR 插件** 包</span><span class="sxs-lookup"><span data-stu-id="a173d-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>
2. <span data-ttu-id="a173d-145">转到检查器中的 MixedReality 工具包组件脚本，并切换到 **DefaultOpenXRConfigurationProfile** 配置文件：</span><span class="sxs-lookup"><span data-stu-id="a173d-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![在检查器的混合现实工具包组件中切换 MRTK 配置的屏幕截图](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="a173d-147">已知问题</span><span class="sxs-lookup"><span data-stu-id="a173d-147">Known issues</span></span> 

<span data-ttu-id="a173d-148">使用手动跟踪功能时，请在 **资产/MixedRealityToolkit/link.xml** 文件中添加以下行：</span><span class="sxs-lookup"><span data-stu-id="a173d-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="a173d-149">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a173d-149">Next steps</span></span>

<span data-ttu-id="a173d-150">现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="a173d-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="a173d-151">是否有反馈？</span><span class="sxs-lookup"><span data-stu-id="a173d-151">Have Feedback?</span></span>

<span data-ttu-id="a173d-152">OpenXR 仍是实验性的，因此我们非常感谢你的反馈，你可以向我们提供更好的帮助。</span><span class="sxs-lookup"><span data-stu-id="a173d-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="a173d-153">你将在 [Unity 论坛](https://aka.ms/unityforums)上查找我们，方法是使用 **Microsoft**  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 标记论坛帖子。</span><span class="sxs-lookup"><span data-stu-id="a173d-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a173d-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="a173d-154">See also</span></span>

* [<span data-ttu-id="a173d-155">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="a173d-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="a173d-156">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="a173d-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="a173d-157">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="a173d-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
