---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: c9cf580b1123002e9e8cdfd5c3914c3aa39e2825
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003126"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="8099b-104">2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="8099b-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="8099b-105">在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="8099b-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="8099b-106">你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="8099b-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="8099b-107">将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="8099b-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="8099b-108">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="8099b-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="8099b-110">目标</span><span class="sxs-lookup"><span data-stu-id="8099b-110">Objectives</span></span>

* <span data-ttu-id="8099b-111">了解如何配置用于 HoloLens 开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="8099b-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="8099b-112">了解如何生成应用并将其部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="8099b-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="8099b-113">在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器</span><span class="sxs-lookup"><span data-stu-id="8099b-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="8099b-114">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8099b-114">Creating the Unity project</span></span>

<span data-ttu-id="8099b-115">启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的 **向下箭头**：</span><span class="sxs-lookup"><span data-stu-id="8099b-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![突出显示了“新建”按钮的 Unity 中心](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="8099b-117">在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="8099b-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![具有新版本选择器下拉菜单的 Unity 中心](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="8099b-119">如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。</span><span class="sxs-lookup"><span data-stu-id="8099b-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="8099b-120">在“创建新项目”窗口中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8099b-120">In the Create a new project window:</span></span>

* <span data-ttu-id="8099b-121">确保将“模板”设置为“3D” </span><span class="sxs-lookup"><span data-stu-id="8099b-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="8099b-122">输入合适的“项目名称”，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="8099b-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="8099b-123">选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”</span><span class="sxs-lookup"><span data-stu-id="8099b-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="8099b-124">单击“创建”按钮，创建并启动新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8099b-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity 中心，其中“新建项目窗口”已填写](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="8099b-126">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="8099b-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="8099b-127">因此，应将 Unity 项目保存到驱动器的根目录附近。</span><span class="sxs-lookup"><span data-stu-id="8099b-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="8099b-128">等待 Unity 创建项目：</span><span class="sxs-lookup"><span data-stu-id="8099b-128">Wait for Unity to create the project:</span></span>

![Unity 正在新建项目](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="8099b-130">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="8099b-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="8099b-131">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="8099b-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="8099b-132">在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="8099b-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="8099b-134">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="8099b-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="8099b-136">MRTK 的 UI 元素需要 TextMeshPro 基本资源。</span><span class="sxs-lookup"><span data-stu-id="8099b-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="8099b-137">如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="8099b-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="8099b-138">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="8099b-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="8099b-139">若要将“混合现实工具包”导入 Unity 项目中，需要使用[混合现实功能工具](../welcome-to-mr-feature-tool.md)，开发人员使用该工具能够发现、更新混合现实功能包并将其添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="8099b-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="8099b-140">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="8099b-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="8099b-141">从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载最新版本的混合现实功能工具，下载完成后，解压缩文件并将其保存到桌面。</span><span class="sxs-lookup"><span data-stu-id="8099b-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="8099b-142">需先安装 [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/5.0)，才能运行混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="8099b-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="8099b-143">混合现实功能工具目前仅在 Windows 上运行，对于 MacOS，请按照此[过程](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages)下载混合现实工具包并将其导入 unity 项目。</span><span class="sxs-lookup"><span data-stu-id="8099b-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="8099b-144">从下载的文件夹中打开可执行文件“MixedRealityFeatureTool”，以启动混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="8099b-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![打开 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="8099b-146">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8099b-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="8099b-147">1.应用 MRTK 项目配置器设置</span><span class="sxs-lookup"><span data-stu-id="8099b-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="8099b-148">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="8099b-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="8099b-149">如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：</span><span class="sxs-lookup"><span data-stu-id="8099b-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="8099b-151">在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：</span><span class="sxs-lookup"><span data-stu-id="8099b-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="8099b-153">可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：</span><span class="sxs-lookup"><span data-stu-id="8099b-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="8099b-154">设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。</span><span class="sxs-lookup"><span data-stu-id="8099b-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="8099b-155">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。</span><span class="sxs-lookup"><span data-stu-id="8099b-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="8099b-156">设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。</span><span class="sxs-lookup"><span data-stu-id="8099b-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="8099b-157">若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="8099b-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="8099b-158">2.配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="8099b-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="8099b-159">创建场景并配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="8099b-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="8099b-160">在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：</span><span class="sxs-lookup"><span data-stu-id="8099b-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="8099b-162">在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：</span><span class="sxs-lookup"><span data-stu-id="8099b-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="8099b-164">在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： </span><span class="sxs-lookup"><span data-stu-id="8099b-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="8099b-166">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="8099b-166">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="8099b-167">若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">性能</a>文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="8099b-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8099b-169">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="8099b-169">Importing the tutorial assets</span></span>

<span data-ttu-id="8099b-170">下载以下 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="8099b-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="8099b-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8099b-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="8099b-172">若要导入 Unity 自定义包，在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  </span><span class="sxs-lookup"><span data-stu-id="8099b-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![导入自定义包](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="8099b-174">在“导入包…”窗口中，选择下载的 MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage，然后单击“打开”按钮：</span><span class="sxs-lookup"><span data-stu-id="8099b-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![选择资产包](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="8099b-176">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="8099b-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![选择要导入的所有资产](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="8099b-178">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8099b-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![导入资产后的 Unity 项目窗口](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="8099b-180">配置场景</span><span class="sxs-lookup"><span data-stu-id="8099b-180">Configuring the Scene</span></span>

<span data-ttu-id="8099b-181">在“项目”窗口中，导航到“资产”>“MRTK.Tutorials.GettingStarted”>“预制件”文件夹：</span><span class="sxs-lookup"><span data-stu-id="8099b-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="8099b-182">在“项目”窗口中，单击“立方体”预制件并将其拖动到“层次结构”窗口中，然后在“检查器”窗口中，按如下所示配置“转换”组件 </span><span class="sxs-lookup"><span data-stu-id="8099b-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="8099b-183">**位置**：X = 0, Y = 0, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="8099b-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="8099b-184">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="8099b-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="8099b-185">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="8099b-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![将立方体添加到场景中](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="8099b-187">若要将焦点置于场景中的对象上，可双击“立方体”对象，然后再次放大一些：</span><span class="sxs-lookup"><span data-stu-id="8099b-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="8099b-188">若要使用被跟踪的双手与对象进行交互和抓取对象，对象必须具有碰撞体组件，例如盒碰撞体、Object Manipulator（脚本）组件和 NearInteractionGrabbable（脚本）组件。  </span><span class="sxs-lookup"><span data-stu-id="8099b-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="8099b-189">在“层次结构”窗口中保持选中“立方体”，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“对象操控器”脚本，将对象操控器脚本添加到立方体对象。  </span><span class="sxs-lookup"><span data-stu-id="8099b-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![向立方体添加对象操控器](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="8099b-191">重复相同的操作，以向立方体添加 Near Interaction Grabbable 脚本</span><span class="sxs-lookup"><span data-stu-id="8099b-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![向立方体添加 Near Interaction Grabbable](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="8099b-193">在这种情况下，添加对象操控器（脚本）时，将自动添加约束管理器（脚本），因为对象操控器（脚本）依赖于约束管理器。</span><span class="sxs-lookup"><span data-stu-id="8099b-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="8099b-194">在本教程中，碰撞体已添加到立方体对象中。</span><span class="sxs-lookup"><span data-stu-id="8099b-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="8099b-195">若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。</span><span class="sxs-lookup"><span data-stu-id="8099b-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="8099b-196">若要在 Unity 编辑器中测试此情况，可以进入播放模式并按住左 Shift 或空格键来启用控制器，这样即可通过鼠标移动来移动控制器，还可以使用鼠标滚轮将其移动到距离相机更远或更近的位置。 </span><span class="sxs-lookup"><span data-stu-id="8099b-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="8099b-197">当指针位于立方体上时，按住鼠标右键以移动立方体对象。</span><span class="sxs-lookup"><span data-stu-id="8099b-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![游戏模式](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="8099b-199">将应用程序构建到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8099b-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="8099b-200">1.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8099b-200">1. Build the Unity project</span></span>

<span data-ttu-id="8099b-201">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 </span><span class="sxs-lookup"><span data-stu-id="8099b-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="8099b-202">在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="8099b-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![选中了 UWP 的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="8099b-204">在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：</span><span class="sxs-lookup"><span data-stu-id="8099b-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="8099b-206">等待 Unity 完成生成过程：</span><span class="sxs-lookup"><span data-stu-id="8099b-206">Wait for Unity to finish the build process:</span></span>

![Unity 正在生成进程](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="8099b-208">2.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="8099b-208">2. Build and deploy the application</span></span>

<span data-ttu-id="8099b-209">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="8099b-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="8099b-210">在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="8099b-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![选中了“新建的 Visual Studio 解决方案”的 Windows 资源管理器](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8099b-212">如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="8099b-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="8099b-213">通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：</span><span class="sxs-lookup"><span data-stu-id="8099b-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![配置为部署到 HoloLens 2 的 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="8099b-215">如果要部署到 HoloLens（第一代），请选择 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="8099b-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="8099b-216">对于 HoloLens，通常是针对 ARM 体系结构进行生成。</span><span class="sxs-lookup"><span data-stu-id="8099b-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="8099b-217">但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。</span><span class="sxs-lookup"><span data-stu-id="8099b-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="8099b-218">建议的解决方法是针对 ARM64 进行生成。</span><span class="sxs-lookup"><span data-stu-id="8099b-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="8099b-219">如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。</span><span class="sxs-lookup"><span data-stu-id="8099b-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="8099b-220">如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="8099b-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="8099b-221">在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="8099b-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="8099b-222">将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：</span><span class="sxs-lookup"><span data-stu-id="8099b-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio“启动(不调试)”菜单路径](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="8099b-224">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="8099b-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="8099b-225">这两个步骤都可以按照[这些说明](../../platform-capabilities-and-apis/using-visual-studio.md)来完成。</span><span class="sxs-lookup"><span data-stu-id="8099b-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="8099b-226">你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。</span><span class="sxs-lookup"><span data-stu-id="8099b-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="8099b-227">使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="8099b-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="8099b-228">选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。</span><span class="sxs-lookup"><span data-stu-id="8099b-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="8099b-229">在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。</span><span class="sxs-lookup"><span data-stu-id="8099b-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="8099b-230">我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="8099b-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="8099b-231">例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="8099b-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="8099b-232">祝贺</span><span class="sxs-lookup"><span data-stu-id="8099b-232">Congratulations</span></span>

<span data-ttu-id="8099b-233">现在，你已经部署了第一个 HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="8099b-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="8099b-234">打开应用后，你面前应该会出现一个立方体对象，你应该能够通过移动该对象来与其进行交互；并且当你四处走动时，应该会看到一个空间映射网格，它覆盖了 HoloLens 识别出的表面。</span><span class="sxs-lookup"><span data-stu-id="8099b-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="8099b-235">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="8099b-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="8099b-236">这些只是 MRTK 附带的几个基础功能。</span><span class="sxs-lookup"><span data-stu-id="8099b-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="8099b-237">在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。</span><span class="sxs-lookup"><span data-stu-id="8099b-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8099b-238">下一教程：3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="8099b-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
