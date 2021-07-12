---
title: 适用于 Android 和 iOS 的 Azure 空间定位点
description: 完成本课程可以了解如何将使用混合现实工具包 (MRTK) 和 Azure 空间定位点的 Unity 项目部署到 Android 和 iOS 上。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, android, ios, MRTK, 混合现实工具包, UWP, Azure 空间定位点, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403405"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="390f0-104">5.适用于 Android 和 iOS 的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="390f0-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="390f0-105">在本教程中，你将学习如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="390f0-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="390f0-106">目标</span><span class="sxs-lookup"><span data-stu-id="390f0-106">Objectives</span></span>

* <span data-ttu-id="390f0-107">学习如何使用 Unity 的 AR Foundation 和 ARCore XR 插件对 Android 设备生成项目</span><span class="sxs-lookup"><span data-stu-id="390f0-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="390f0-108">学习如何使用 Unity 的 AR Foundation 和 ARKit XR 插件对 iOS 设备生成项目</span><span class="sxs-lookup"><span data-stu-id="390f0-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="390f0-109">安装内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="390f0-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="390f0-110">为 AR Foundation 摄像头配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="390f0-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="390f0-111">在本部分，你将学习如何配置 MRTK 以部署到移动设备。</span><span class="sxs-lookup"><span data-stu-id="390f0-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="390f0-112">在“层次结构”窗口中，选择 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="390f0-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="390f0-113">然后，在检查器窗口中，选择“摄像头”选项卡，克隆摄像头配置文件，并为其指定一个适当的名称，例如 AzureSpatialAnchors_ARCameraProfile ：</span><span class="sxs-lookup"><span data-stu-id="390f0-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![选中了新创建的 ARCameraProfile 的 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="390f0-115">要通过提示了解如何克隆 MRTK 配置文件的提示，可参阅[配置混合现实工具包配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="390f0-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="390f0-116">在“检查器”窗口中仍选中“相机”选项卡的情况下，展开“相机设置提供程序”，然后单击“-”以删除“Windows Mixed Reality相机设置”或“XR SDK Windows Mixed Reality 相机设置”：   </span><span class="sxs-lookup"><span data-stu-id="390f0-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="390f0-117">添加了新数据提供程序的 Unity ARCameraProfile</span><span class="sxs-lookup"><span data-stu-id="390f0-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="390f0-118">然后单击“+ 添加相机设置提供程序”按钮，然后展开新添加的“新数据提供程序”： </span><span class="sxs-lookup"><span data-stu-id="390f0-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![为 Android 添加了 AR 相机](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="390f0-120">使用“类型”下拉列表将类型更改为“Microsoft.MixedReality.Toolkit.Experimental.UnityAR” > “UnityARCameraSettings”  ：</span><span class="sxs-lookup"><span data-stu-id="390f0-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![具有指向数据提供程序类型选择的路径的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="390f0-122">通过调用以下菜单项来更新 MRTK UnityAR 脚本定义：“混合现实” > “工具包” > “实用工具” > “UnityAR”>“更新脚本定义”</span><span class="sxs-lookup"><span data-stu-id="390f0-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="390f0-123">将应用程序生成到 Android 设备</span><span class="sxs-lookup"><span data-stu-id="390f0-123">Building your application to your Android device</span></span>

<span data-ttu-id="390f0-124">在本部分，你将学习如何配置项目来生成它并将其部署到 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="390f0-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="390f0-125">在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，然后将平台切换到 Android ：</span><span class="sxs-lookup"><span data-stu-id="390f0-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![选中了 Android 平台的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="390f0-127">有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。</span><span class="sxs-lookup"><span data-stu-id="390f0-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="390f0-128">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="390f0-128">Close the Build Settings window.</span></span>

<span data-ttu-id="390f0-129">在 Unity 菜单中，选择“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置     ：</span><span class="sxs-lookup"><span data-stu-id="390f0-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity MRTK 项目配置器 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="390f0-131">在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，选择“Vulkan”，然后单击“-”符号将其删除：     </span><span class="sxs-lookup"><span data-stu-id="390f0-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![选中了 Vulcan 的 Unity“其他设置”](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="390f0-133">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 。</span><span class="sxs-lookup"><span data-stu-id="390f0-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="390f0-134">然后，使用 USB 线缆将 Android 设备连接到计算机，再从“运行设备”下拉列表中将它选中：</span><span class="sxs-lookup"><span data-stu-id="390f0-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![添加了场景并选中了“运行设备”的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="390f0-136">如果“运行设备”下拉列表中未显示你的设备，则可能需要按下拉列表旁边的“刷新”按钮。</span><span class="sxs-lookup"><span data-stu-id="390f0-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="390f0-137">在“生成设置”窗口中，单击“生成并运行”按钮打开“生成 Android”窗口。</span><span class="sxs-lookup"><span data-stu-id="390f0-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="390f0-138">选择一个合适的位置来存储生成（例如 D:\MixedRealityLearning\Builds），然后为 apk 提供一个合适的名称（例如 MRTKTutorials-AzureSpatialAnchors），再单击“保存”按钮，开始生成过程 ：</span><span class="sxs-lookup"><span data-stu-id="390f0-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![具有“保存”提示窗口 Android 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="390f0-140">如果在 Unity 控制台窗口中收到任何与 Android SDK、NDK 或 JDK 模块相关的错误，则需要打开 Unity Hub 并安装相关的 Android 生成支持模块。</span><span class="sxs-lookup"><span data-stu-id="390f0-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="390f0-141">生成过程完成后，应用应会在 Android 设备上自动加载。</span><span class="sxs-lookup"><span data-stu-id="390f0-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="390f0-142">将应用程序生成到 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="390f0-142">Building your application to your iOS device</span></span>

<span data-ttu-id="390f0-143">在本部分，你将学习如何配置项目来生成它并将其部署到 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="390f0-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="390f0-144">在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，并将平台切换到 iOS ：</span><span class="sxs-lookup"><span data-stu-id="390f0-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![选中了 iOS 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="390f0-146">有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。</span><span class="sxs-lookup"><span data-stu-id="390f0-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="390f0-147">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="390f0-147">Close the Build Settings window.</span></span>

<span data-ttu-id="390f0-148">在 Unity 菜单中，选择“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置     ：</span><span class="sxs-lookup"><span data-stu-id="390f0-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity“MRTK 项目配置器”窗口 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="390f0-150">在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，取消选中“剪裁引擎代码”复选框来禁用它    ：</span><span class="sxs-lookup"><span data-stu-id="390f0-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![禁用了“剪裁引擎代码”的 Unity“其他设置”](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="390f0-152">关闭“播放器设置”窗口，再次打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="390f0-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="390f0-153">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 ：</span><span class="sxs-lookup"><span data-stu-id="390f0-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![添加了场景的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="390f0-155">在“生成设置”窗口中，单击“生成”按钮打开“生成 iOS”窗口。</span><span class="sxs-lookup"><span data-stu-id="390f0-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="390f0-156">选择一个合适的位置来存储 Xcode 项目（例如 D:\MixedRealityLearning\Builds），创建一个新文件夹并为其指定适当的名称（例如 MRTKTutorials-AzureSpatialAnchors），然后单击“选择文件夹”按钮，启动生成过程 ：</span><span class="sxs-lookup"><span data-stu-id="390f0-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![具有“保存”提示窗口 iOS 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="390f0-158">生成过程完成后，按照[导出 Xcode 项目](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)中的说明了解如何将 Xcode 项目部署到 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="390f0-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="390f0-159">祝贺</span><span class="sxs-lookup"><span data-stu-id="390f0-159">Congratulations</span></span>

<span data-ttu-id="390f0-160">在本教程中，你学习了如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="390f0-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
