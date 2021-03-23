---
title: 适用于 Android 和 iOS 的 Azure 空间定位点
description: 完成本课程可以了解如何将使用混合现实工具包 (MRTK) 和 Azure 空间定位点的 Unity 项目部署到 Android 和 iOS 上。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, android, ios, MRTK, 混合现实工具包, UWP, Azure 空间定位点, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 699c7689fcd23543f4d4b0e86f64cdbf98debc1f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590709"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="ac469-104">5.适用于 Android 和 iOS 的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="ac469-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="ac469-105">在本教程中，你将学习如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="ac469-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="ac469-106">目标</span><span class="sxs-lookup"><span data-stu-id="ac469-106">Objectives</span></span>

* <span data-ttu-id="ac469-107">学习如何使用 Unity 的 AR Foundation 和 ARCore XR 插件对 Android 设备生成项目</span><span class="sxs-lookup"><span data-stu-id="ac469-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="ac469-108">学习如何使用 Unity 的 AR Foundation 和 ARKit XR 插件对 iOS 设备生成项目</span><span class="sxs-lookup"><span data-stu-id="ac469-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="ac469-109">安装内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="ac469-109">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="ac469-110">在本部分中，你将升级并安装以下内置包：</span><span class="sxs-lookup"><span data-stu-id="ac469-110">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="ac469-111">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="ac469-111">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="ac469-112">XR 旧版 Input Helpers 2.1.6</span><span class="sxs-lookup"><span data-stu-id="ac469-112">XR Legacy Input Helpers 2.1.6</span></span>
* <span data-ttu-id="ac469-113">适用于 Android 的 ARCore XR 插件 3.1.3 支持</span><span class="sxs-lookup"><span data-stu-id="ac469-113">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="ac469-114">适用于 iOS 的 ARKit XR 插件 3.1.3 支持</span><span class="sxs-lookup"><span data-stu-id="ac469-114">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="ac469-115">并非所有版本都与 MRTK 兼容，只有某些版本可协同工作，因此请确保安装的是上述版本。</span><span class="sxs-lookup"><span data-stu-id="ac469-115">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="ac469-116">在 Unity 菜单中，选择“窗口” > “包管理器”来打开“包管理器”窗口，然后选择“AR Foundation” > “3.1.3”，再单击“更新到 3.1.3”按钮来更新包    ：</span><span class="sxs-lookup"><span data-stu-id="ac469-116">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![选中了“AR Foundation”的 Unity 包管理器](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="ac469-118">根据需要按照相同的过程导入其余的包。</span><span class="sxs-lookup"><span data-stu-id="ac469-118">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="ac469-119">如果你要为 Android 开发此项目，则无需安装 ARKit XR 插件包。</span><span class="sxs-lookup"><span data-stu-id="ac469-119">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="ac469-120">同样，如果你要为 iOS 开发此项目，则无需安装 ARCore XR 插件。</span><span class="sxs-lookup"><span data-stu-id="ac469-120">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="ac469-121">为 AR Foundation 摄像头配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="ac469-121">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="ac469-122">在本部分，你将学习如何配置 MRTK 以部署到移动设备。</span><span class="sxs-lookup"><span data-stu-id="ac469-122">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="ac469-123">在“层次结构”窗口中，选择 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="ac469-123">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="ac469-124">然后，在检查器窗口中，选择“摄像头”选项卡，克隆摄像头配置文件，并为其指定一个适当的名称，例如 AzureSpatialAnchors_ARCameraProfile ：</span><span class="sxs-lookup"><span data-stu-id="ac469-124">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![选中了新创建的 ARCameraProfile 的 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ac469-126">要通过提示了解如何克隆 MRTK 配置文件的提示，可参阅[配置混合现实工具包配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="ac469-126">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="ac469-127">在检查器窗口中仍选中“摄像头”选项卡的情况下，展开“摄像头设置提供程序”，单击“+添加摄像头设置提供程序”按钮，然后展开新添加的“新数据提供程序 1”   ：</span><span class="sxs-lookup"><span data-stu-id="ac469-127">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![添加了新数据提供程序的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="ac469-129">使用“类型”下拉列表将类型更改为“Microsoft.MixedReality.Toolkit.Experimental.UnityAR” > “UnityARCameraSettings”  ：</span><span class="sxs-lookup"><span data-stu-id="ac469-129">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![具有指向数据提供程序类型选择的路径的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="ac469-131">在“层次结构”窗口中仍选中 MixedRealityToolkit 对象的情况下，使用检查器窗口中的“添加组件”按钮添加以下组件 ：</span><span class="sxs-lookup"><span data-stu-id="ac469-131">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="ac469-132">AR 空间点管理器(脚本)</span><span class="sxs-lookup"><span data-stu-id="ac469-132">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="ac469-133">DisableDiagnosticsSystem (脚本)</span><span class="sxs-lookup"><span data-stu-id="ac469-133">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="ac469-134">添加了 AR 定位点管理器和 DisableDiagnosticsSystem 组件的 Unity MixedRealityToolkit 对象</span><span class="sxs-lookup"><span data-stu-id="ac469-134">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="ac469-135">添加“AR 引用点管理器(脚本)”组件时，会自动添加“AR 会话来源(脚本)”组件，因为它是“AR 引用点管理器(脚本)”组件所必需的。</span><span class="sxs-lookup"><span data-stu-id="ac469-135">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>



<span data-ttu-id="ac469-136">通过调用菜单项来更新 MRTK UnityAR 脚本定义：“混合现实工具包” > “实用工具” > “UnityAR”>“更新脚本定义”  </span><span class="sxs-lookup"><span data-stu-id="ac469-136">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="ac469-137">将应用程序生成到 Android 设备</span><span class="sxs-lookup"><span data-stu-id="ac469-137">Building your application to your Android device</span></span>

<span data-ttu-id="ac469-138">在本部分，你将学习如何配置项目来生成它并将其部署到 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="ac469-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="ac469-139">在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，然后将平台切换到 Android ：</span><span class="sxs-lookup"><span data-stu-id="ac469-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![选中了 Android 平台的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="ac469-141">有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。</span><span class="sxs-lookup"><span data-stu-id="ac469-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ac469-142">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-142">Close the Build Settings window.</span></span>

<span data-ttu-id="ac469-143">在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置    ：</span><span class="sxs-lookup"><span data-stu-id="ac469-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity“MRTK 项目配置器”窗口 Android](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="ac469-145">在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，选择“Vulkan”，然后单击“-”符号将其删除：     </span><span class="sxs-lookup"><span data-stu-id="ac469-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![选中了 Vulcan 的 Unity“其他设置”](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="ac469-147">在 Unity 菜单中，选择“编辑” > “项目设置...” >“播放器”> “XR 设置”，确保使用的是 Android 平台，勾选“支持的虚拟现实”复选框，然后单击“+”图标并选择“无”     ：</span><span class="sxs-lookup"><span data-stu-id="ac469-147">In the Unity menu, select **Edit** > **Project Settings...** >**Player**> **XR Setting**, make sure you are in **Android** platform and check the **Virtual Reality Supported** checkbox then click the + icon, and select None:</span></span>

![Unity“MRTK 项目配置器”窗口 Android](images/mr-learning-asa/asa-05-section3-step1-2-1.png)

<span data-ttu-id="ac469-149">关闭“播放器设置”窗口，再次打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-149">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="ac469-150">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 。</span><span class="sxs-lookup"><span data-stu-id="ac469-150">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="ac469-151">然后，使用 USB 线缆将 Android 设备连接到计算机，再从“运行设备”下拉列表中将它选中：</span><span class="sxs-lookup"><span data-stu-id="ac469-151">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![添加了场景并选中了“运行设备”的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="ac469-153">如果“运行设备”下拉列表中未显示你的设备，则可能需要按下拉列表旁边的“刷新”按钮。</span><span class="sxs-lookup"><span data-stu-id="ac469-153">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="ac469-154">在“生成设置”窗口中，单击“生成并运行”按钮打开“生成 Android”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-154">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="ac469-155">选择一个合适的位置来存储生成（例如 D:\MixedRealityLearning\Builds），然后为 apk 提供一个合适的名称（例如 MRTKTutorials-AzureSpatialAnchors），再单击“保存”按钮，开始生成过程 ：</span><span class="sxs-lookup"><span data-stu-id="ac469-155">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![具有“保存”提示窗口 Android 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="ac469-157">如果在 Unity 控制台窗口中收到任何与 Android SDK、NDK 或 JDK 模块相关的错误，则需要打开 Unity Hub 并安装相关的 Android 生成支持模块。</span><span class="sxs-lookup"><span data-stu-id="ac469-157">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="ac469-158">生成过程完成后，应用应会在 Android 设备上自动加载。</span><span class="sxs-lookup"><span data-stu-id="ac469-158">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="ac469-159">将应用程序生成到 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="ac469-159">Building your application to your iOS device</span></span>

<span data-ttu-id="ac469-160">在本部分，你将学习如何配置项目来生成它并将其部署到 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="ac469-160">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="ac469-161">在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，并将平台切换到 iOS ：</span><span class="sxs-lookup"><span data-stu-id="ac469-161">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![选中了 iOS 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="ac469-163">有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。</span><span class="sxs-lookup"><span data-stu-id="ac469-163">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ac469-164">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-164">Close the Build Settings window.</span></span>

<span data-ttu-id="ac469-165">在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置    ：</span><span class="sxs-lookup"><span data-stu-id="ac469-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity“MRTK 项目配置器”窗口 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="ac469-167">在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，取消选中“剪裁引擎代码”复选框来禁用它    ：</span><span class="sxs-lookup"><span data-stu-id="ac469-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![禁用了“剪裁引擎代码”的 Unity“其他设置”](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="ac469-169">关闭“播放器设置”窗口，再次打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-169">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="ac469-170">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 ：</span><span class="sxs-lookup"><span data-stu-id="ac469-170">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![添加了场景的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="ac469-172">在“生成设置”窗口中，单击“生成”按钮打开“生成 iOS”窗口。</span><span class="sxs-lookup"><span data-stu-id="ac469-172">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="ac469-173">选择一个合适的位置来存储 Xcode 项目（例如 D:\MixedRealityLearning\Builds），创建一个新文件夹并为其指定适当的名称（例如 MRTKTutorials-AzureSpatialAnchors），然后单击“选择文件夹”按钮，启动生成过程 ：</span><span class="sxs-lookup"><span data-stu-id="ac469-173">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![具有“保存”提示窗口 iOS 的 Unity“生成设置”窗口](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="ac469-175">生成过程完成后，按照[导出 Xcode 项目](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)中的说明了解如何将 Xcode 项目部署到 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="ac469-175">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ac469-176">祝贺</span><span class="sxs-lookup"><span data-stu-id="ac469-176">Congratulations</span></span>

<span data-ttu-id="ac469-177">在本教程中，你学习了如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="ac469-177">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>