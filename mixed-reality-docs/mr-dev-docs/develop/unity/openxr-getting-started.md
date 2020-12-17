---
title: 为 Unity 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: adb678d168d86dc2376ac46caa690e5db036099c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622907"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="3dd8d-104">为 Unity 使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="3dd8d-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="3dd8d-105">从 Unity 版本2020.2 开始，Microsoft 的 Mixed Reality OpenXR 插件包可通过 Unity 包管理器 (UPM) 提供。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3dd8d-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="3dd8d-106">Prerequisites</span></span>

*   <span data-ttu-id="3dd8d-107">Unity 2020.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3dd8d-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="3dd8d-108">Unity OpenXR 插件0.1.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3dd8d-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="3dd8d-109">Visual Studio 2019 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3dd8d-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="3dd8d-110">在适用于 HoloLens 2 应用的 Unity 中安装 **UWP** 平台支持</span><span class="sxs-lookup"><span data-stu-id="3dd8d-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="3dd8d-111">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="3dd8d-112">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="3dd8d-113">安装混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="3dd8d-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="3dd8d-114">使用 Mixed Reality OpenXR 插件之前，需要安装 Unity 的 **OpenXR 插件** 和 **XR 插件管理** 包：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-114">Before using the Mixed Reality OpenXR Plugin, you need to install Unity’s **OpenXR Plugin** and **XR Plugin Management** packages:</span></span>

1. <span data-ttu-id="3dd8d-115">在 Unity 编辑器中，导航到 "**编辑" > 项目设置 > 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-115">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="3dd8d-116">展开 " **限定作用域** " 部分，输入以下信息，然后选择 " **保存**"：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-116">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="3dd8d-117">将 **名称** 设置为 **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="3dd8d-117">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="3dd8d-118">将 **URL** 设置为 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="3dd8d-118">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="3dd8d-119">将 **范围 (s)** 设置为 **mixedreality**</span><span class="sxs-lookup"><span data-stu-id="3dd8d-119">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="3dd8d-120">在 "**高级设置**" 下，选择 "**启用预览包**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-120">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![在项目设置中打开的 "Unity 包管理器" 窗口的屏幕截图](images/openxr-img-01.png)

<span data-ttu-id="3dd8d-122">Unity 包管理器使用名为 *manifest.js* 的清单文件来确定要安装的包以及可以从中安装这些包的注册表。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-122">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3dd8d-123">OpenXR 仍在 Unity 中试验，此过程可能会随时间而改变，因为我们将努力优化开发人员体验。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-123">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="3dd8d-124">注册混合现实依赖项</span><span class="sxs-lookup"><span data-stu-id="3dd8d-124">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="3dd8d-125">将 Microsoft 混合现实范围内的注册表添加到清单后，可以指定 OpenXR 包。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-125">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="3dd8d-126">添加 OpenXR 包：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-126">To add the OpenXR package:</span></span>

1. <span data-ttu-id="3dd8d-127">在文本编辑器中打开 **<projectRoot> /Packages/manifest.js** ，如 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3dd8d-127">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="3dd8d-128">按如下所示修改文件 *中包/manifest.js* 的依赖项部分：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-128">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3dd8d-129">清单文件中的依赖关系可能比此处显示的更多。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-129">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="3dd8d-130">请勿删除任何文件，只需将 "OpenXR" 依赖项添加到列表。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-130">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="3dd8d-131">保存该文件，切换回 Unity 编辑器，打开 **包管理器** 以确认已安装插件：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-131">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了混合现实 OpenXR 插件](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="3dd8d-133">如果使用 Unity 包管理器删除 OpenXR 包，则必须使用前面介绍的步骤重新添加它。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-133">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="3dd8d-134">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="3dd8d-134">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="3dd8d-135">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-135">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="3dd8d-136">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-136">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="3dd8d-137">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-137">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="3dd8d-138">选中 " **在启动时初始化 XR"** 和 " **OpenXR (预览")** 框</span><span class="sxs-lookup"><span data-stu-id="3dd8d-138">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="3dd8d-139">如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-139">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="3dd8d-141">如果在 OpenXR 插件旁边出现一个红色警告图标 **(预览 ")**，请单击该图标，然后选择" **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-141">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="3dd8d-142">Unity 编辑器可能需要重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-142">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="3dd8d-144">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="3dd8d-144">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="3dd8d-145">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-145">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="3dd8d-146">Optimization</span><span class="sxs-lookup"><span data-stu-id="3dd8d-146">Optimization</span></span>

<span data-ttu-id="3dd8d-147">如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-147">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="3dd8d-149">试用 Unity 示例场景</span><span class="sxs-lookup"><span data-stu-id="3dd8d-149">Try out the Unity sample scenes</span></span>

<span data-ttu-id="3dd8d-150">若要利用一个或多个示例，请从 **程序包 Manager** 安装 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：</span><span class="sxs-lookup"><span data-stu-id="3dd8d-150">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了 AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="3dd8d-152">HoloLens 2 示例</span><span class="sxs-lookup"><span data-stu-id="3dd8d-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="3dd8d-153">在 Unity 编辑器中，导航到 "**窗口 >" 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="3dd8d-154">在包列表中，选择 " **混合现实 OpenXR" 插件**</span><span class="sxs-lookup"><span data-stu-id="3dd8d-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="3dd8d-155">在 **示例** 列表中找到示例，然后选择 "**导入**"</span><span class="sxs-lookup"><span data-stu-id="3dd8d-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![已在 Unity 编辑器中打开 Unity 包管理器的屏幕截图，并选中混合现实 OpenXR 插件，并突出显示示例导入按钮](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="3dd8d-157">更新包时，Unity 提供更新导入的示例的选项。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="3dd8d-158">更新导入的示例将覆盖对示例和关联的资产所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3dd8d-159">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3dd8d-159">Next steps</span></span> 

<span data-ttu-id="3dd8d-160">现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="3dd8d-160">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dd8d-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dd8d-161">See also</span></span>
* [<span data-ttu-id="3dd8d-162">不 MRTK 配置你的项目</span><span class="sxs-lookup"><span data-stu-id="3dd8d-162">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="3dd8d-163">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="3dd8d-163">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="3dd8d-164">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="3dd8d-164">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)