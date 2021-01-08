---
title: MRTK 教程 - 2. 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859526"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="3f388-105">2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="3f388-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="3f388-106">概述</span><span class="sxs-lookup"><span data-stu-id="3f388-106">Overview</span></span>

<span data-ttu-id="3f388-107">在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="3f388-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="3f388-108">你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="3f388-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="3f388-109">将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="3f388-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="3f388-110">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="3f388-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="3f388-111">目标</span><span class="sxs-lookup"><span data-stu-id="3f388-111">Objectives</span></span>

* <span data-ttu-id="3f388-112">了解如何配置用于 HoloLens 开发的 Unity。</span><span class="sxs-lookup"><span data-stu-id="3f388-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="3f388-113">了解如何生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="3f388-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="3f388-114">在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器。</span><span class="sxs-lookup"><span data-stu-id="3f388-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="3f388-115">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3f388-115">Creating the Unity project</span></span>

1. <span data-ttu-id="3f388-116">启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的向下箭头：   </span><span class="sxs-lookup"><span data-stu-id="3f388-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![突出显示“新建”按钮的向下箭头的 Unity 中心](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="3f388-118">在下拉菜单中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="3f388-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![选择 Unity 版本](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="3f388-120">如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。</span><span class="sxs-lookup"><span data-stu-id="3f388-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="3f388-121">在“创建新项目”窗口中，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3f388-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="3f388-122">确保将“模板”设置为“3D” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="3f388-123">在“项目名称”框中，为项目输入一个合适的名称（例如“MRTK 教程”）。</span><span class="sxs-lookup"><span data-stu-id="3f388-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="3f388-124">单击“位置”旁边的三点按钮，然后导航到要在其中保存项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f388-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="3f388-125">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="3f388-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="3f388-126">因此，应将 Unity 项目保存到驱动器的根目录附近。</span><span class="sxs-lookup"><span data-stu-id="3f388-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="3f388-127">单击“创建”  按钮。</span><span class="sxs-lookup"><span data-stu-id="3f388-127">Click the **Create** button.</span></span> <span data-ttu-id="3f388-128">这将创建并启动新的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="3f388-128">This creates and launches your new Unity project.</span></span>

![Unity 中心，已填写其中的“创建新项目”窗口](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="3f388-130">状态栏可让你了解最新进度。</span><span class="sxs-lookup"><span data-stu-id="3f388-130">The status bar keeps you updated on your progress.</span></span>

![Unity 进度栏可让你了解“创建项目”的最新状态](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="3f388-132">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="3f388-132">Switching the build platform</span></span>

1. <span data-ttu-id="3f388-133">在菜单栏上，选择“文件” > “生成设置…” </span><span class="sxs-lookup"><span data-stu-id="3f388-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="3f388-135">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮：  </span><span class="sxs-lookup"><span data-stu-id="3f388-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="3f388-137">等待 Unity 完成平台切换，然后关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="3f388-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="3f388-138">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="3f388-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="3f388-139">MRTK 的 UI 元素需要 TextMeshPro 基本资源。</span><span class="sxs-lookup"><span data-stu-id="3f388-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="3f388-140">如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="3f388-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="3f388-141">在菜单栏上，选择“窗口” > “TextMeshPro” > “导入 TMP Pro 基本资源”  。</span><span class="sxs-lookup"><span data-stu-id="3f388-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="3f388-143">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产  ：</span><span class="sxs-lookup"><span data-stu-id="3f388-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="3f388-145">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="3f388-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="3f388-146">下载 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="3f388-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="3f388-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="3f388-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="3f388-148">在菜单栏上，选择“资产” > “导入包” > “自定义包…”  。</span><span class="sxs-lookup"><span data-stu-id="3f388-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="3f388-149">在“导入包…”对话框中，导航到刚才下载的包所在的位置，选择该包，然后单击“打开”按钮 。</span><span class="sxs-lookup"><span data-stu-id="3f388-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="3f388-150">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产  。</span><span class="sxs-lookup"><span data-stu-id="3f388-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="3f388-151">选择 MRTK 和项目设置</span><span class="sxs-lookup"><span data-stu-id="3f388-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="3f388-152">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3f388-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="3f388-153">如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：</span><span class="sxs-lookup"><span data-stu-id="3f388-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="3f388-155">在“MRTK 项目配置器”窗口中，展开“修改配置”部分（如果需要），确保选中所有选项 。</span><span class="sxs-lookup"><span data-stu-id="3f388-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![显示了“修改配置”的 Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="3f388-157">要应用设置，请单击“应用”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f388-157">To apply the settings, click the **Apply** button.</span></span>

![MRTK 中的“应用”按钮](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="3f388-159">你使用的是 Unity 的内置旧版 XR 而不是新的 XR 插件系统，因为新系统与本系列教程中[推荐的 Unity 和 MRTK 版本](mr-learning-base-01.md#prerequisites)不完全兼容。</span><span class="sxs-lookup"><span data-stu-id="3f388-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="3f388-160">如果你看到任何关于即将弃用内置 XR 的警告，可以忽略它们。</span><span class="sxs-lookup"><span data-stu-id="3f388-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="3f388-161">可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：</span><span class="sxs-lookup"><span data-stu-id="3f388-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="3f388-162">启用旧版 XR：为项目启用 VR。</span><span class="sxs-lookup"><span data-stu-id="3f388-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="3f388-163">设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。</span><span class="sxs-lookup"><span data-stu-id="3f388-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="3f388-164">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[单通道实例化渲染](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)部分。</span><span class="sxs-lookup"><span data-stu-id="3f388-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="3f388-165">设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。</span><span class="sxs-lookup"><span data-stu-id="3f388-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="3f388-166">若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="3f388-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="3f388-167">在菜单栏上，选择“编辑” > “项目设置…” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="3f388-168">在“项目设置”窗口中，选择“播放器”，单击“XR 设置”下拉列表，然后选中“支持的虚拟现实”旁边的框   ：</span><span class="sxs-lookup"><span data-stu-id="3f388-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![显示了“支持虚拟现实”的 Unity“XR 设置”](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="3f388-170">这会导入 Windows Mixed Reality SDK：</span><span class="sxs-lookup"><span data-stu-id="3f388-170">This imports the Windows Mixed Reality SDK:</span></span>

![显示了“Virtual Reality SDK”的 Unity“XR 设置”](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="3f388-172">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3f388-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="3f388-173">如果未显示该窗口，请选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，以将其打开  。</span><span class="sxs-lookup"><span data-stu-id="3f388-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="3f388-174">在“MRTK 项目配置器”窗口中，单击“音频空间定位器”下拉列表，然后选择“MS HRTF 空间定位器”  。</span><span class="sxs-lookup"><span data-stu-id="3f388-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![显示了“音频空间定位器”选项的“项目设置”](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="3f388-176">单击“应用”  按钮。</span><span class="sxs-lookup"><span data-stu-id="3f388-176">Click the **Apply** button.</span></span> <span data-ttu-id="3f388-177">这将关闭“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3f388-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="3f388-178">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="3f388-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="3f388-179">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="3f388-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="3f388-180">若要了解有关本主题的详细信息，请参阅空间音频教程。</span><span class="sxs-lookup"><span data-stu-id="3f388-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="3f388-181">在“项目设置”窗口中，单击“深度格式”下拉列表，然后选择“16 位深度”：  </span><span class="sxs-lookup"><span data-stu-id="3f388-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="选中了“16 位深度”的 Unity“XR 设置”。":::

    > [!TIP]
    > <span data-ttu-id="3f388-183">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="3f388-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="3f388-184">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[深度缓冲区共享 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) 部分。</span><span class="sxs-lookup"><span data-stu-id="3f388-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="3f388-185">单击“发布设置”下拉列表，然后在“包名称”框中输入合适的名称（例如“MRTK-Tutorials-Getting-Started”） 。</span><span class="sxs-lookup"><span data-stu-id="3f388-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="配置了“包名称”的 Unity“发布设置”。":::

    <span data-ttu-id="3f388-187">**包名称和产品名称**</span><span class="sxs-lookup"><span data-stu-id="3f388-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="3f388-188">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="3f388-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="3f388-189">应在部署应用之前创建此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="3f388-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="3f388-190">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="3f388-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="3f388-191">为了更轻松地在开发期间查找应用，可以在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="3f388-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="已配置“产品名称”的 Unity“项目设置”。":::

9. <span data-ttu-id="3f388-193">关闭“项目设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="3f388-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="3f388-194">创建和配置场景</span><span class="sxs-lookup"><span data-stu-id="3f388-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="3f388-195">在菜单栏中，选择“文件” > “新场景” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="3f388-196">要将 MRTK 添加到场景，请在菜单栏上选择“混合现实工具包” > “添加到场景并配置…” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity“添加到场景并配置...”菜单路径。":::

3. <span data-ttu-id="3f388-198">在“层次结构”窗口中，确保选中了“MixedRealityToolkit” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="确保已选中“MixedRealityTookit”。":::

4. <span data-ttu-id="3f388-200">在“检查器”窗口的“MixedRealityToolkit”部分中，验证配置文件是否设置为“DefaultMixedRealityToolkitConfigurationProfile”  ：</span><span class="sxs-lookup"><span data-stu-id="3f388-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="选中了“DefaultMixedRealityTookitConfigurationProfile”的 Unity MixedRealityToolkit 组件。":::

    > [!IMPORTANT]
    > <span data-ttu-id="3f388-202">通常，在针对 HoloLens 进行开发时会使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3f388-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="3f388-203">但对于本教程，将使用 DefaultMixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3f388-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="3f388-204">在下一个教程（[配置 MRTK 配置文件](mr-learning-base-03.md)）中，将改用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3f388-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="3f388-205">在菜单栏上，选择“文件” > “另存为…” </span><span class="sxs-lookup"><span data-stu-id="3f388-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="3f388-206">在“保存场景”对话框中，导航到项目的“场景”文件夹 。</span><span class="sxs-lookup"><span data-stu-id="3f388-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="3f388-207">在“文件名”框中，为场景指定一个合适的名称（例如“\_GettingStarted\_”），然后单击“保存”按钮 。</span><span class="sxs-lookup"><span data-stu-id="3f388-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity“保存场景”的“保存”提示窗口。":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="3f388-209">生成并部署到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f388-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="3f388-210">在生成到设备之前，请确认以下事项：</span><span class="sxs-lookup"><span data-stu-id="3f388-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="3f388-211">设备处于开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="3f388-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="3f388-212">设备已与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="3f388-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="3f388-213">如果没有，则在生成过程中，Visual Studio 中会出现以下对话框：</span><span class="sxs-lookup"><span data-stu-id="3f388-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![输入 PIN 以实现设备配对](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="3f388-215">要了解有关这两个步骤的详细信息，请参阅[使用 Visual Studio 进行部署和调试](../../platform-capabilities-and-apis/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="3f388-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="3f388-216">在菜单栏上，选择“文件” > “生成设置…” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="3f388-217">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中  。</span><span class="sxs-lookup"><span data-stu-id="3f388-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![将当前场景添加“生成中的场景”列表](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="3f388-219">单击“**生成**”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f388-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="单击“生成”按钮。":::

4. <span data-ttu-id="3f388-221">在“生成通用 Windows 平台”对话框中，选择一个合适的位置来存储生成（例如，你可能希望在“MRTK 教程”文件夹中创建一个“生成”文件夹）。</span><span class="sxs-lookup"><span data-stu-id="3f388-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="3f388-222">创建一个新文件夹并为其提供一个合适的名称（例如“GettingStarted”），选择该文件夹，然后单击“选择文件夹”按钮启动生成过程。</span><span class="sxs-lookup"><span data-stu-id="3f388-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="显示生成文件夹的 Unity 生成窗口。":::

    <span data-ttu-id="3f388-224">此时会显示一个状态栏，可让你了解最新生成进度。</span><span class="sxs-lookup"><span data-stu-id="3f388-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity 生成过程正在进行中。":::

    > [!TIP]
    > <span data-ttu-id="3f388-226">你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。</span><span class="sxs-lookup"><span data-stu-id="3f388-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="3f388-227">生成过程完成后，在文件资源管理器中导航到存储生成的位置，然后双击解决方案文件以在 Visual Studio 中打开它：</span><span class="sxs-lookup"><span data-stu-id="3f388-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="选中了新建的 Visual Studio 解决方案文件的 Windows 资源管理器。":::

    > [!NOTE]
    > <span data-ttu-id="3f388-229">如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="3f388-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="3f388-230">通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   。</span><span class="sxs-lookup"><span data-stu-id="3f388-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="3f388-231">如果要部署到 HoloLens（第一代），请选择 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="3f388-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="配置为部署到 HoloLens 2 的 Visual Studio。":::

    > [!NOTE]
    > <span data-ttu-id="3f388-233">对于 HoloLens，通常是针对 ARM 体系结构进行生成。</span><span class="sxs-lookup"><span data-stu-id="3f388-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="3f388-234">但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。</span><span class="sxs-lookup"><span data-stu-id="3f388-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="3f388-235">建议的解决方法是针对 ARM64 进行生成。</span><span class="sxs-lookup"><span data-stu-id="3f388-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="3f388-236">如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f388-237">如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="3f388-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="3f388-238">为此，请在“解决方案资源管理器”中右键单击“YourProjectName (通用 Windows)”，然后选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="3f388-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="3f388-239">将 HoloLens 连接到计算机，然后执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="3f388-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="3f388-240">要生成应用，请将其部署到 HoloLens，并在不附加 Visual Studio 调试器的情况下自动启动它，在菜单栏上，选择“调试” > “启动但不调试” 。</span><span class="sxs-lookup"><span data-stu-id="3f388-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio“启动但不调试”的菜单路径。":::

- <span data-ttu-id="3f388-242">要生成应用并将其部署到 HoloLens，但不自动启动该应用，请在菜单栏上选择“生成”>“部署解决方案”。</span><span class="sxs-lookup"><span data-stu-id="3f388-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="3f388-243">在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。</span><span class="sxs-lookup"><span data-stu-id="3f388-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="3f388-244">我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="3f388-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="3f388-245">例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="3f388-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="3f388-246">祝贺</span><span class="sxs-lookup"><span data-stu-id="3f388-246">Congratulations</span></span>

<span data-ttu-id="3f388-247">现在，你已经部署了第一个 HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="3f388-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="3f388-248">四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="3f388-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="3f388-249">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="3f388-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="3f388-250">这些只是 MRTK 附带的几个基础功能。</span><span class="sxs-lookup"><span data-stu-id="3f388-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="3f388-251">在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。</span><span class="sxs-lookup"><span data-stu-id="3f388-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f388-252">下一教程：3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="3f388-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
