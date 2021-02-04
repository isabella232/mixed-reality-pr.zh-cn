---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ff479df81316ab5ceeabf045ad1bbae007190ed4
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238151"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="9020d-104">2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="9020d-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="9020d-105">在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="9020d-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="9020d-106">你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="9020d-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="9020d-107">将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="9020d-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9020d-108">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="9020d-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="9020d-109">目标</span><span class="sxs-lookup"><span data-stu-id="9020d-109">Objectives</span></span>

* <span data-ttu-id="9020d-110">了解如何配置用于 HoloLens 开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="9020d-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="9020d-111">了解如何生成应用并将其部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="9020d-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="9020d-112">在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器</span><span class="sxs-lookup"><span data-stu-id="9020d-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9020d-113">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9020d-113">Creating the Unity project</span></span>

<span data-ttu-id="9020d-114">启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的 **向下箭头**：</span><span class="sxs-lookup"><span data-stu-id="9020d-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![突出显示了“新建”按钮的 Unity 中心](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="9020d-116">在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="9020d-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![具有新版本选择器下拉菜单的 Unity 中心](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="9020d-118">如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。</span><span class="sxs-lookup"><span data-stu-id="9020d-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="9020d-119">在“创建新项目”窗口中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9020d-119">In the Create a new project window:</span></span>

* <span data-ttu-id="9020d-120">确保将“模板”设置为“3D” </span><span class="sxs-lookup"><span data-stu-id="9020d-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="9020d-121">输入合适的“项目名称”，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="9020d-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="9020d-122">选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”</span><span class="sxs-lookup"><span data-stu-id="9020d-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="9020d-123">单击“创建”按钮，创建并启动新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9020d-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity 中心，其中“新建项目窗口”已填写](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9020d-125">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="9020d-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="9020d-126">因此，应将 Unity 项目保存到驱动器的根目录附近。</span><span class="sxs-lookup"><span data-stu-id="9020d-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="9020d-127">等待 Unity 创建项目：</span><span class="sxs-lookup"><span data-stu-id="9020d-127">Wait for Unity to create the project:</span></span>

![Unity 正在新建项目](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="9020d-129">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="9020d-129">Switching the build platform</span></span>

<span data-ttu-id="9020d-130">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="9020d-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="9020d-132">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： </span><span class="sxs-lookup"><span data-stu-id="9020d-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="9020d-134">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="9020d-134">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切换平台](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="9020d-136">当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：</span><span class="sxs-lookup"><span data-stu-id="9020d-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![突出显示了“关闭”图标的 Unity 生成窗口](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="9020d-138">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="9020d-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="9020d-139">在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="9020d-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="9020d-141">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="9020d-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="9020d-143">MRTK 的 UI 元素需要 TextMeshPro 基本资源。</span><span class="sxs-lookup"><span data-stu-id="9020d-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="9020d-144">如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="9020d-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="9020d-145">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="9020d-145">Importing the Mixed Reality Toolkit</span></span>

### <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="9020d-146">使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="9020d-146">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="9020d-147">若要使用全新的混合现实功能工具应用程序安装 MRTK，请遵循我们的[安装和使用说明](../welcome-to-mr-feature-tool.md)并在“混合现实工具包”类别中选择“Mixed Reality Toolkit Foundation”包。</span><span class="sxs-lookup"><span data-stu-id="9020d-147">To install MRTK with our new Mixed Reality Feature Tool application, follow our [installation and usage instructions](../welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

### <a name="using-unity-packages"></a><span data-ttu-id="9020d-148">使用 Unity 包</span><span class="sxs-lookup"><span data-stu-id="9020d-148">Using Unity Packages</span></span>

<span data-ttu-id="9020d-149">使用自定义包安装 MRTK：</span><span class="sxs-lookup"><span data-stu-id="9020d-149">To install MRTK with a custom package:</span></span>

* [<span data-ttu-id="9020d-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9020d-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="9020d-151">在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  </span><span class="sxs-lookup"><span data-stu-id="9020d-151">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Unity“导入自定义包...”菜单路径](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="9020d-153">在“导入包…”窗口中，选择下载的 Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage，然后单击“打开”按钮 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-153">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![具有“打开”提示窗口的 Unity“导入自定义包”](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="9020d-155">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="9020d-155">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity MRTK Foundation 导入窗口](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="9020d-157">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9020d-157">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="9020d-158">1.应用 MRTK 项目配置器设置</span><span class="sxs-lookup"><span data-stu-id="9020d-158">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="9020d-159">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="9020d-159">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="9020d-160">如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：</span><span class="sxs-lookup"><span data-stu-id="9020d-160">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="9020d-162">在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-162">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="9020d-164">可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：</span><span class="sxs-lookup"><span data-stu-id="9020d-164">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="9020d-165">设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。</span><span class="sxs-lookup"><span data-stu-id="9020d-165">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="9020d-166">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[单通道实例化渲染](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)部分。</span><span class="sxs-lookup"><span data-stu-id="9020d-166">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="9020d-167">设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。</span><span class="sxs-lookup"><span data-stu-id="9020d-167">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="9020d-168">若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="9020d-168">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="9020d-169">2.配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="9020d-169">2. Configure additional project settings</span></span>

<span data-ttu-id="9020d-170">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="9020d-170">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity“项目设置...”菜单路径](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="9020d-172">在“项目设置”窗口中，选择“XR 插件管理” > “安装 XR 插件管理”，安装 XR 插件管理 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-172">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![选择了 XR 插件管理的项目设置](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="9020d-174">Unity 安装完 XR 插件管理后。</span><span class="sxs-lookup"><span data-stu-id="9020d-174">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="9020d-175">确保转到“通用 Windows 平台”设置，然后选中“在启动时初始化 XR”。</span><span class="sxs-lookup"><span data-stu-id="9020d-175">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Unity 配置 XR 插件管理](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="9020d-177">在“项目设置”窗口中，选择“播放器” > “XR 设置”，单击 + 图标，然后选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK  ：</span><span class="sxs-lookup"><span data-stu-id="9020d-177">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![选中了“添加 Windows Mixed Reality SDK”的 Unity XR 设置](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="9020d-179">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="9020d-179">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="9020d-180">如果未显示，请使用 Unity 菜单打开它。</span><span class="sxs-lookup"><span data-stu-id="9020d-180">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="9020d-181">在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="9020d-181">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![突出显示音频空间定位器属性的 MRTK 项目配置器窗口](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="9020d-183">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="9020d-183">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="9020d-184">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="9020d-184">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="9020d-185">若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="9020d-185">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="9020d-186">在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：</span><span class="sxs-lookup"><span data-stu-id="9020d-186">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 启用 16 深度](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="9020d-188">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="9020d-188">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="9020d-189">若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">性能</a>文档的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="9020d-189">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="9020d-190">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="9020d-190">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![配置了包名称的 Unity 发布设置](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="9020d-192">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="9020d-192">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="9020d-193">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="9020d-193">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="9020d-194">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="9020d-194">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="9020d-195">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="9020d-195">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="9020d-196">创建和配置场景</span><span class="sxs-lookup"><span data-stu-id="9020d-196">Creating and configuring the scene</span></span>

<span data-ttu-id="9020d-197">在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-197">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="9020d-199">在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-199">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="9020d-201">仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：</span><span class="sxs-lookup"><span data-stu-id="9020d-201">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![选中了 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="9020d-203">在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： </span><span class="sxs-lookup"><span data-stu-id="9020d-203">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="9020d-205">在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“GettingStarted”），然后单击“保存”按钮以保存场景：</span><span class="sxs-lookup"><span data-stu-id="9020d-205">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="9020d-207">将应用程序构建到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9020d-207">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="9020d-208">1.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9020d-208">1. Build the Unity project</span></span>

<span data-ttu-id="9020d-209">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 </span><span class="sxs-lookup"><span data-stu-id="9020d-209">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="9020d-210">在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="9020d-210">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![选中了 UWP 的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="9020d-212">在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：</span><span class="sxs-lookup"><span data-stu-id="9020d-212">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="9020d-214">等待 Unity 完成生成过程：</span><span class="sxs-lookup"><span data-stu-id="9020d-214">Wait for Unity to finish the build process:</span></span>

![Unity 正在生成进程](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="9020d-216">2.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="9020d-216">2. Build and deploy the application</span></span>

<span data-ttu-id="9020d-217">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="9020d-217">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="9020d-218">在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="9020d-218">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![选中了“新建的 Visual Studio 解决方案”的 Windows 资源管理器](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9020d-220">如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="9020d-220">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="9020d-221">通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：</span><span class="sxs-lookup"><span data-stu-id="9020d-221">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![配置为部署到 HoloLens 2 的 Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="9020d-223">如果要部署到 HoloLens（第一代），请选择 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="9020d-223">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="9020d-224">对于 HoloLens，通常是针对 ARM 体系结构进行生成。</span><span class="sxs-lookup"><span data-stu-id="9020d-224">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="9020d-225">但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。</span><span class="sxs-lookup"><span data-stu-id="9020d-225">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="9020d-226">建议的解决方法是针对 ARM64 进行生成。</span><span class="sxs-lookup"><span data-stu-id="9020d-226">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="9020d-227">如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。</span><span class="sxs-lookup"><span data-stu-id="9020d-227">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="9020d-228">如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="9020d-228">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="9020d-229">在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="9020d-229">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="9020d-230">将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：</span><span class="sxs-lookup"><span data-stu-id="9020d-230">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio“启动(不调试)”菜单路径](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="9020d-232">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="9020d-232">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="9020d-233">这两个步骤都可以按照[这些说明](../../platform-capabilities-and-apis/using-visual-studio.md)来完成。</span><span class="sxs-lookup"><span data-stu-id="9020d-233">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="9020d-234">你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。</span><span class="sxs-lookup"><span data-stu-id="9020d-234">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="9020d-235">使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="9020d-235">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="9020d-236">选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。</span><span class="sxs-lookup"><span data-stu-id="9020d-236">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="9020d-237">在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。</span><span class="sxs-lookup"><span data-stu-id="9020d-237">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="9020d-238">我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="9020d-238">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="9020d-239">例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="9020d-239">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9020d-240">祝贺</span><span class="sxs-lookup"><span data-stu-id="9020d-240">Congratulations</span></span>

<span data-ttu-id="9020d-241">现在，你已经部署了第一个 HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="9020d-241">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="9020d-242">四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="9020d-242">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9020d-243">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="9020d-243">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="9020d-244">这些只是 MRTK 附带的几个基础功能。</span><span class="sxs-lookup"><span data-stu-id="9020d-244">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="9020d-245">在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。</span><span class="sxs-lookup"><span data-stu-id="9020d-245">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9020d-246">下一教程：3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="9020d-246">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)