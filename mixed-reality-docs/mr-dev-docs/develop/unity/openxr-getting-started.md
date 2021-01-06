---
title: 为 Unity 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 7d28dd50e111da4b010bcae699b7451d967e8f35
ms.sourcegitcommit: 653ddcae6d7a1617c89da1153fa8e7b482ef6818
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905289"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="1bd34-104">为 Unity 使用混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="1bd34-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="1bd34-105">从 Unity 版本2020.2 开始，Microsoft 的 Mixed Reality OpenXR 插件包可通过 Unity 包管理器 (UPM) 提供。</span><span class="sxs-lookup"><span data-stu-id="1bd34-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bd34-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="1bd34-106">Prerequisites</span></span>

* <span data-ttu-id="1bd34-107">Unity 2020.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="1bd34-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="1bd34-108">Unity OpenXR 插件0.1.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="1bd34-108">Unity OpenXR plugin 0.1.1 or later</span></span>
* <span data-ttu-id="1bd34-109">Visual Studio 2019 或更高版本</span><span class="sxs-lookup"><span data-stu-id="1bd34-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="1bd34-110">在适用于 HoloLens 2 应用的 Unity 中安装 **UWP** 平台支持</span><span class="sxs-lookup"><span data-stu-id="1bd34-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="1bd34-111">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="1bd34-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="1bd34-112">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="1bd34-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="1bd34-113">安装混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="1bd34-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="1bd34-114">你的项目需要在使用混合现实 OpenXR 插件之前安装 **OpenXR 插件** 和 **XR 插件管理** 包。</span><span class="sxs-lookup"><span data-stu-id="1bd34-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="1bd34-115">如果已安装了这些文件，很好！</span><span class="sxs-lookup"><span data-stu-id="1bd34-115">If you've already installed them, great!</span></span> <span data-ttu-id="1bd34-116">否则，安装混合现实 OpenXR 插件会自动将它们作为依赖项进行安装：</span><span class="sxs-lookup"><span data-stu-id="1bd34-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="1bd34-117">在 Unity 编辑器中，导航到 "**编辑" > 项目设置 > 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="1bd34-118">展开 " **限定作用域** " 部分，输入以下信息，然后选择 " **保存**"：</span><span class="sxs-lookup"><span data-stu-id="1bd34-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="1bd34-119">将 **名称** 设置为 **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="1bd34-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="1bd34-120">将 **URL** 设置为 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="1bd34-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="1bd34-121">将 **范围 (s)** 设置为 **mixedreality**</span><span class="sxs-lookup"><span data-stu-id="1bd34-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="1bd34-122">在 "**高级设置**" 下，选择 "**启用预览包**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![在项目设置中打开的 "Unity 包管理器" 窗口的屏幕截图](images/openxr-img-01.png)

<span data-ttu-id="1bd34-124">Unity 包管理器使用名为 *manifest.js* 的清单文件来确定要安装的包以及可以从中安装这些包的注册表。</span><span class="sxs-lookup"><span data-stu-id="1bd34-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bd34-125">OpenXR 仍在 Unity 中试验，此过程可能会随时间而改变，因为我们将努力优化开发人员体验。</span><span class="sxs-lookup"><span data-stu-id="1bd34-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="1bd34-126">注册混合现实依赖项</span><span class="sxs-lookup"><span data-stu-id="1bd34-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="1bd34-127">将 Microsoft 混合现实范围内的注册表添加到清单后，可以指定 OpenXR 包。</span><span class="sxs-lookup"><span data-stu-id="1bd34-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="1bd34-128">添加 OpenXR 包：</span><span class="sxs-lookup"><span data-stu-id="1bd34-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="1bd34-129">在文本编辑器中打开 **[projectRoot]/Packages/manifest.js** ，如 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1bd34-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="1bd34-130">为此，请在项目窗口的左面板中右键单击 " **包** "。</span><span class="sxs-lookup"><span data-stu-id="1bd34-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="1bd34-131">然后单击 " **在资源管理器中显示**"。</span><span class="sxs-lookup"><span data-stu-id="1bd34-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="1bd34-132">![项目窗口中列出的包的屏幕截图](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="1bd34-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="1bd34-133">按如下所示修改文件 *中包/manifest.js* 的依赖项部分：</span><span class="sxs-lookup"><span data-stu-id="1bd34-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1bd34-134">清单文件中的依赖关系可能比此处显示的更多。</span><span class="sxs-lookup"><span data-stu-id="1bd34-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="1bd34-135">请勿删除任何文件，只需将 "OpenXR" 依赖项添加到列表。</span><span class="sxs-lookup"><span data-stu-id="1bd34-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. <span data-ttu-id="1bd34-136">保存该文件，切换回 Unity 编辑器，打开 **包管理器** 以确认已安装插件：</span><span class="sxs-lookup"><span data-stu-id="1bd34-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了混合现实 OpenXR 插件](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="1bd34-138">如果使用 Unity 包管理器删除 OpenXR 包，则必须使用前面介绍的步骤重新添加它。</span><span class="sxs-lookup"><span data-stu-id="1bd34-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="1bd34-139">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="1bd34-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="1bd34-140">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="1bd34-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="1bd34-141">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="1bd34-142">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="1bd34-143">选中 " **在启动时初始化 XR"** 和 " **OpenXR (预览")** 框</span><span class="sxs-lookup"><span data-stu-id="1bd34-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="1bd34-144">如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="1bd34-146">如果在 OpenXR 插件旁边出现一个红色警告图标 **(预览 ")**，请单击该图标，然后选择" **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="1bd34-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="1bd34-147">Unity 编辑器可能需要重新启动才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="1bd34-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

<span data-ttu-id="1bd34-149">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="1bd34-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="1bd34-150">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="1bd34-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="1bd34-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="1bd34-151">Optimization</span></span>

<span data-ttu-id="1bd34-152">如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="1bd34-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="1bd34-154">试用 Unity 示例场景</span><span class="sxs-lookup"><span data-stu-id="1bd34-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="1bd34-155">若要利用一个或多个示例，请从 **包管理器** 安装 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：</span><span class="sxs-lookup"><span data-stu-id="1bd34-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了 AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="1bd34-157">HoloLens 2 示例</span><span class="sxs-lookup"><span data-stu-id="1bd34-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="1bd34-158">在 Unity 编辑器中，导航到 "**窗口 >" 包管理器**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="1bd34-159">在包列表中，选择 " **混合现实 OpenXR" 插件**</span><span class="sxs-lookup"><span data-stu-id="1bd34-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="1bd34-160">在 **示例** 列表中找到示例，然后选择 "**导入**"</span><span class="sxs-lookup"><span data-stu-id="1bd34-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![已在 Unity 编辑器中打开 Unity 包管理器的屏幕截图，并选中混合现实 OpenXR 插件，并突出显示示例导入按钮](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="1bd34-162">更新包时，Unity 提供更新导入的示例的选项。</span><span class="sxs-lookup"><span data-stu-id="1bd34-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="1bd34-163">更新导入的示例将覆盖对示例和关联的资产所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="1bd34-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bd34-164">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1bd34-164">Next steps</span></span>

<span data-ttu-id="1bd34-165">现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="1bd34-165">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="1bd34-166">是否有反馈？</span><span class="sxs-lookup"><span data-stu-id="1bd34-166">Have Feedback?</span></span>

<span data-ttu-id="1bd34-167">OpenXR 仍是实验性的，因此我们非常感谢你的反馈，你可以向我们提供更好的帮助。</span><span class="sxs-lookup"><span data-stu-id="1bd34-167">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="1bd34-168">你将在 [Unity 论坛](https://aka.ms/unityforums)上查找我们，方法是使用 **Microsoft**  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 标记论坛帖子。</span><span class="sxs-lookup"><span data-stu-id="1bd34-168">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd34-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="1bd34-169">See also</span></span>

* [<span data-ttu-id="1bd34-170">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="1bd34-170">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="1bd34-171">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="1bd34-171">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="1bd34-172">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="1bd34-172">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
