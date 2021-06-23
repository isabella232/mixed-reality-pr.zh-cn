---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2021
ms.locfileid: "112536046"
---
# <a name="openxr"></a>[<span data-ttu-id="6e972-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="6e972-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6e972-102">安装具有新的混合现实功能工具应用程序的 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="6e972-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="6e972-103">按照 [安装和使用说明](../../welcome-to-mr-feature-tool.md)进行操作，并在 **平台支持** 类别中选择 **混合现实 OpenXR 插件** 包：</span><span class="sxs-lookup"><span data-stu-id="6e972-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="6e972-105">设置生成目标</span><span class="sxs-lookup"><span data-stu-id="6e972-105">Setting your build target</span></span>

<span data-ttu-id="6e972-106">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

<span data-ttu-id="6e972-108">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="6e972-109">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="6e972-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="6e972-110">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="6e972-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="6e972-111">将“体系结构”设置为“ARM64”</span><span class="sxs-lookup"><span data-stu-id="6e972-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="6e972-112">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="6e972-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="6e972-113">将“生成类型”设置为“D3D 项目”</span><span class="sxs-lookup"><span data-stu-id="6e972-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="6e972-114">将 **目标 SDK 版本** 设置为 **已安装的最新** 版本</span><span class="sxs-lookup"><span data-stu-id="6e972-114">Set **Target SDK Version** to **Latest installed**</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="6e972-116">为 OpenXR 配置 XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="6e972-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="6e972-117">若要将 OpenXR 设置为 Unity 中的运行时：</span><span class="sxs-lookup"><span data-stu-id="6e972-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="6e972-118">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"</span><span class="sxs-lookup"><span data-stu-id="6e972-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="6e972-119">在设置列表中，选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="6e972-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="6e972-120">选择 " **安装 XR 插件管理** " （如果它出现 ![ 在 unity 编辑器中打开的 "项目设置" 窗口屏幕截图，并突出显示 XR 插件管理](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="6e972-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="6e972-121&quot;>选中 &quot; **在启动时初始化 XR** &quot; 框</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;6e972-121&quot;>Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id=&quot;6e972-122&quot;>如果面向的是 Desktop VR，请在 &quot;监视器")  ("计算机" "独立" 选项卡，然后选中 **OpenXR** 和 **Windows Mixed Reality 功能集** 框</span><span class="sxs-lookup"><span data-stu-id="6e972-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="6e972-123">如果面向 HoloLens 2，请切换到 "通用 Windows 平台" 选项卡 (Windows 徽标) 并选择 **OpenXR** 和 **Microsoft HoloLens 功能集** 框</span><span class="sxs-lookup"><span data-stu-id="6e972-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="6e972-125">如果在 " **OpenXR" 插件** 旁出现黄色警告图标，请单击该图标，然后选择 " **全部修复** "，然后继续。</span><span class="sxs-lookup"><span data-stu-id="6e972-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="6e972-126">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="6e972-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 项目验证窗口的屏幕截图](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="6e972-128">优化</span><span class="sxs-lookup"><span data-stu-id="6e972-128">Optimization</span></span>

<span data-ttu-id="6e972-129">如果正在开发 HoloLens 2，请选择 " **混合现实" > 项目 > "为 HoloLens 2 菜单项应用推荐的项目设置** "，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="6e972-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](../../images/openxr-img-08.png)

<span data-ttu-id="6e972-131">你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！</span><span class="sxs-lookup"><span data-stu-id="6e972-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="6e972-132">继续阅读下一节，了解如何使用 OpenXR 示例。</span><span class="sxs-lookup"><span data-stu-id="6e972-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="6e972-133">适用于 OpenXR 和 HoloLens 2 的 Unity 示例项目</span><span class="sxs-lookup"><span data-stu-id="6e972-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="6e972-134">查看示例 unity 项目的 [OpenXR 混合现实示例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存储库展示如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实耳机构建 unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="6e972-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="6e972-135">或者，如果你已准备好开始使用空白项目，请转到 [相机设置](../../camera-in-unity.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="6e972-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="6e972-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="6e972-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="6e972-137">Windows XR 插件在 Unity 2021.1 中已弃用，并将在 Unity 2021.2 中被删除。</span><span class="sxs-lookup"><span data-stu-id="6e972-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="6e972-138">对于 Unity 2020 开发，Microsoft 建议改用 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="6e972-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="6e972-139">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

<span data-ttu-id="6e972-141">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="6e972-142">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="6e972-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="6e972-143">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="6e972-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="6e972-144">将“体系结构”设置为“ARM64”</span><span class="sxs-lookup"><span data-stu-id="6e972-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="6e972-145">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="6e972-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="6e972-146">将“生成类型”设置为“D3D 项目”</span><span class="sxs-lookup"><span data-stu-id="6e972-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="6e972-147">将 **目标 SDK 版本** 设置为 **已安装的最新** 版本</span><span class="sxs-lookup"><span data-stu-id="6e972-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="6e972-148">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="6e972-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

<span data-ttu-id="6e972-150">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../../../design/app-views.md) 而不是2d 视图：</span><span class="sxs-lookup"><span data-stu-id="6e972-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="6e972-151">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"，然后选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="6e972-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="6e972-152">如果出现，请选择 " **安装 XR 插件管理** "</span><span class="sxs-lookup"><span data-stu-id="6e972-152">Select **Install XR Plugin Management** if it appears</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="6e972-154">选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality** "</span><span class="sxs-lookup"><span data-stu-id="6e972-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="6e972-156">选择 " **XR 插件管理**  >  " "**Windows Mixed Reality** " 部分，选中所有框并将 **深度缓冲区格式** 设置为 **深度缓冲区16位**</span><span class="sxs-lookup"><span data-stu-id="6e972-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![突出显示了 Windows Mixed Reality 部分的 "项目设置" 窗口的屏幕截图已在 unity 编辑器中打开](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="6e972-158">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="6e972-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="6e972-159">旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。</span><span class="sxs-lookup"><span data-stu-id="6e972-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="6e972-160">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

<span data-ttu-id="6e972-162">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="6e972-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="6e972-163">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="6e972-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="6e972-164">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="6e972-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="6e972-165">将“体系结构”设置为“ARM64”</span><span class="sxs-lookup"><span data-stu-id="6e972-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="6e972-166">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="6e972-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="6e972-167">将“生成类型”设置为“D3D 项目”</span><span class="sxs-lookup"><span data-stu-id="6e972-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="6e972-168">将 **目标 SDK 版本** 设置为 **已安装的最新** 版本</span><span class="sxs-lookup"><span data-stu-id="6e972-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="6e972-169">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="6e972-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

<span data-ttu-id="6e972-171">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../../../design/app-views.md) 而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="6e972-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="6e972-172">从生成设置中打开 **播放机设置** ... **窗口** 并展开 **XR 设置** 组</span><span class="sxs-lookup"><span data-stu-id="6e972-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="6e972-173">在 " **XR 设置** " 部分中，选择 " **支持的虚拟现实** " 以添加虚拟现实设备列表</span><span class="sxs-lookup"><span data-stu-id="6e972-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="6e972-174">将 **深度格式** 设置为 **16 位深度**，并选中 "**启用深度缓冲区共享**"</span><span class="sxs-lookup"><span data-stu-id="6e972-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="6e972-175">将“立体渲染模式”设置为“单通道实例化”</span><span class="sxs-lookup"><span data-stu-id="6e972-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="6e972-176">如果要使用全息播放模式远程处理，请选择 " **支持 WSA 全息远程处理** "</span><span class="sxs-lookup"><span data-stu-id="6e972-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![突出显示了 "播放机设置" 部分的 "项目设置" 窗口的屏幕截图](../../images/wmr-config-img-9.png)
