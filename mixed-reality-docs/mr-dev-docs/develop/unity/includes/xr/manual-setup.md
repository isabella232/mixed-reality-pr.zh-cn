---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394581"
---
# <a name="openxr"></a>[<span data-ttu-id="313f9-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="313f9-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="313f9-102">使用新的混合现实功能工具应用程序安装 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="313f9-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="313f9-103">按照安装和 [使用说明操作，](../../welcome-to-mr-feature-tool.md) 在"混合现实工具包"类别中选择"混合现实 **OpenXR** 插件"包：</span><span class="sxs-lookup"><span data-stu-id="313f9-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![混合现实功能工具包窗口，突出显示了打开的 xr 插件](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="313f9-105">设置生成目标</span><span class="sxs-lookup"><span data-stu-id="313f9-105">Setting your build target</span></span>

<span data-ttu-id="313f9-106">如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

<span data-ttu-id="313f9-108">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="313f9-109">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="313f9-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="313f9-110">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="313f9-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="313f9-111">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="313f9-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="313f9-112">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="313f9-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="313f9-113">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="313f9-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="313f9-114">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="313f9-114">Set **UWP SDK** to **Latest installed**</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="313f9-116">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="313f9-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="313f9-117">若要在 Unity 中将 OpenXR 设置为运行时，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="313f9-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="313f9-118">在 Unity 编辑器中，导航到 **"编辑>项目设置"**</span><span class="sxs-lookup"><span data-stu-id="313f9-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="313f9-119">在"设置"列表中，选择 **"XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="313f9-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="313f9-120">选中"**启动时初始化 XR"和\*\*\*\*"OpenXR"** 框</span><span class="sxs-lookup"><span data-stu-id="313f9-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="313f9-121">如果以HoloLens 2为目标，请确保你位于 UWP 平台上，然后选择"Microsoft HoloLens **功能集"**</span><span class="sxs-lookup"><span data-stu-id="313f9-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="313f9-123">优化</span><span class="sxs-lookup"><span data-stu-id="313f9-123">Optimization</span></span>

<span data-ttu-id="313f9-124">如果要针对 HoloLens 2 进行开发，请导航到"混合现实> **OpenXR >应用** 针对 HoloLens 2 的建议项目设置，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="313f9-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已选中 OpenXR 的混合现实菜单项的屏幕截图](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="313f9-126">如果在 **OpenXR** 插件旁边看到黄色警告图标，请单击该图标并选择" **全部修复** "，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="313f9-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="313f9-127">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="313f9-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](../../images/openxr-img-06.png)

<span data-ttu-id="313f9-129">现在，你已准备好在 Unity 中开始使用 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="313f9-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="313f9-130">继续学习下一部分，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="313f9-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="313f9-131">OpenXR 和 HoloLens 2 的 Unity 示例项目</span><span class="sxs-lookup"><span data-stu-id="313f9-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="313f9-132">请查看 [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 示例存储库，了解示例 Unity 项目，了解如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实头戴显示设备生成 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="313f9-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="313f9-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="313f9-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="313f9-134">如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

<span data-ttu-id="313f9-136">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="313f9-137">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="313f9-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="313f9-138">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="313f9-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="313f9-139">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="313f9-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="313f9-140">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="313f9-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="313f9-141">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="313f9-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="313f9-142">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="313f9-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="313f9-143">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="313f9-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

<span data-ttu-id="313f9-145">设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图：</span><span class="sxs-lookup"><span data-stu-id="313f9-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="313f9-146">在 Unity 编辑器中，导航到"编辑 **>项目设置"，然后选择\*\*\*\*"XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="313f9-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="313f9-147">选择 **"安装 XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="313f9-147">Select **Install XR Plugin Management**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="313f9-149">选择 **"启动时初始化 XR"，\*\*\*\*然后选择Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="313f9-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="313f9-151">展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows 平台设置"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="313f9-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="313f9-152">如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。**</span><span class="sxs-lookup"><span data-stu-id="313f9-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="313f9-153">可以选择任一运行时。</span><span class="sxs-lookup"><span data-stu-id="313f9-153">You can choose either runtime.</span></span>  <span data-ttu-id="313f9-154">如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，查看使用适用于 Unity 的混合现实 [OpenXR](../../openxr-getting-started.md) 插件指南，在返回到本教程之前，请正确设置这些设备</span><span class="sxs-lookup"><span data-stu-id="313f9-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="313f9-155">从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。</span><span class="sxs-lookup"><span data-stu-id="313f9-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="313f9-156">迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。</span><span class="sxs-lookup"><span data-stu-id="313f9-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="313f9-157">有关详细信息，请参阅 [使用混合现实 OpenXR 插件](../../openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="313f9-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="313f9-158">如果决定选择"深度提交 **Windows Mixed Reality，** 请选中所有框，将"深度提交模式"设置为"深度 **16 位"**</span><span class="sxs-lookup"><span data-stu-id="313f9-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中Windows Mixed Reality部分](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="313f9-160">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="313f9-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="313f9-161">如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

<span data-ttu-id="313f9-163">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="313f9-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="313f9-164">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="313f9-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="313f9-165">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="313f9-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="313f9-166">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="313f9-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="313f9-167">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="313f9-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="313f9-168">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="313f9-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="313f9-169">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="313f9-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="313f9-170">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="313f9-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

<span data-ttu-id="313f9-172">设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图。</span><span class="sxs-lookup"><span data-stu-id="313f9-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="313f9-173">旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。</span><span class="sxs-lookup"><span data-stu-id="313f9-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="313f9-174">从 **"生成设置..."** 打开" **播放器设置..."。窗口** 并展开 **"XR 设置"** 组</span><span class="sxs-lookup"><span data-stu-id="313f9-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="313f9-175">在 **"XR 设置"** 部分中 **，选择"** 支持的虚拟现实"以添加"虚拟现实设备"列表</span><span class="sxs-lookup"><span data-stu-id="313f9-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="313f9-176">将 **深度格式设置为** **16 位深度** 并启用 **深度缓冲区共享**</span><span class="sxs-lookup"><span data-stu-id="313f9-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="313f9-177">将 **立体声渲染模式设置为\*\*\*\*单通道实例**</span><span class="sxs-lookup"><span data-stu-id="313f9-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="313f9-178">如果要 **使用全息远程处理** ，请选择"支持的 WSA 全息远程处理"</span><span class="sxs-lookup"><span data-stu-id="313f9-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了"播放器设置"部分](../../images/wmr-config-img-9.png)