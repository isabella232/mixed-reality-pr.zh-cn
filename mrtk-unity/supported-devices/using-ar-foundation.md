---
title: UsingARFoundation
description: 在 unity 中使用 ARFoundation 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， AR Core， AR 工具包
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852333"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="e5fdd-104">如何为 iOS 和 Android 配置 MRTK [实验]</span><span class="sxs-lookup"><span data-stu-id="e5fdd-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="e5fdd-105">安装所需程序包</span><span class="sxs-lookup"><span data-stu-id="e5fdd-105">Install required packages</span></span>

1. <span data-ttu-id="e5fdd-106">从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 Unity 页面下载并导入 **Microsoft.MixedReality.Toolkit.Unity.Foundation** [程序包管理器](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="e5fdd-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="e5fdd-107">在 Unity 程序包管理器 (UPM) 中，安装以下包：</span><span class="sxs-lookup"><span data-stu-id="e5fdd-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="e5fdd-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="e5fdd-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-109">**Android**</span></span> | <span data-ttu-id="e5fdd-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-110">**iOS**</span></span> | <span data-ttu-id="e5fdd-111">注释</span><span class="sxs-lookup"><span data-stu-id="e5fdd-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="e5fdd-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-112">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-113">版本：1.5.0 - 预览版 6</span><span class="sxs-lookup"><span data-stu-id="e5fdd-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e5fdd-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-114">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-115">版本：1.5.0 - 预览版 6</span><span class="sxs-lookup"><span data-stu-id="e5fdd-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e5fdd-116">对于 Unity 2018.4，此包以预览版提供。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="e5fdd-117">查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="e5fdd-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="e5fdd-118">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-119">版本：2.1.2</span><span class="sxs-lookup"><span data-stu-id="e5fdd-119">Version: 2.1.2</span></span> | <span data-ttu-id="e5fdd-120">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-121">版本：2.1.2</span><span class="sxs-lookup"><span data-stu-id="e5fdd-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="e5fdd-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="e5fdd-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-123">**Android**</span></span> | <span data-ttu-id="e5fdd-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e5fdd-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-125">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-126">版本：2.1.8</span><span class="sxs-lookup"><span data-stu-id="e5fdd-126">Version: 2.1.8</span></span> |  <span data-ttu-id="e5fdd-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-127">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-128">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="e5fdd-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="e5fdd-129">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="e5fdd-130">Version: 2.1.11</span></span> | <span data-ttu-id="e5fdd-131">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-132">版本：2.1。9</span><span class="sxs-lookup"><span data-stu-id="e5fdd-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="e5fdd-133">**目前尚不支持 Unity 2020.1 (，仅包含在信息中)**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="e5fdd-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-134">**Android**</span></span> | <span data-ttu-id="e5fdd-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e5fdd-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-136">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-137">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="e5fdd-137">Version: 3.1.3</span></span> |  <span data-ttu-id="e5fdd-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e5fdd-138">AR Foundation</span></span>  <br/> <span data-ttu-id="e5fdd-139">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="e5fdd-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="e5fdd-140">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-141">版本：3.1。4</span><span class="sxs-lookup"><span data-stu-id="e5fdd-141">Version: 3.1.4</span></span> | <span data-ttu-id="e5fdd-142">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e5fdd-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e5fdd-143">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="e5fdd-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="e5fdd-144">通过调用菜单项来更新 MRTK UnityAR 脚本定义： **混合现实工具包 > 实用程序 > UnityAR > 更新脚本定义**</span><span class="sxs-lookup"><span data-stu-id="e5fdd-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="e5fdd-145">启用 Unity AR 照相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="e5fdd-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="e5fdd-146">以下步骤假定使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e5fdd-147">其他服务注册机构所需的步骤可能不同。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e5fdd-148">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="e5fdd-150">选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="e5fdd-152">选择 **"相机** 配置文件"旁边的"克隆"。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-152">Select **Clone** next to the Camera Profile.</span></span>

    ![克隆 MRTK 相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="e5fdd-154">将"检查器"面板导航到"相机系统"部分，然后展开" **相机设置提供程序"** 部分。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="e5fdd-156">单击 **"添加相机设置提供程序"，** 然后展开新 **添加的"新建相机设置"** 条目。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展开新设置提供程序](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="e5fdd-158">选择 Unity AR 相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="e5fdd-158">Select the Unity AR Camera Settings provider</span></span>

    ![选择 Unity AR 设置提供程序](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="e5fdd-160">有关配置 Unity AR 相机设置提供程序的信息，请参阅 [Unity AR 相机设置提供程序](../features/camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e5fdd-161">当应用程序 (AR Foundation 组件) 时，此安装会检查其运行状况。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="e5fdd-162">如果没有，则会自动添加它们，使其与 ARCore 和 ARKit 一同使用。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="e5fdd-163">如果需要设置特定行为，应自己添加所需的组件。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="e5fdd-164">有关 AR Foundation 组件和安装的信息，请查看 [此文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="e5fdd-165">生成适用于 Android 和 iOS 设备的场景</span><span class="sxs-lookup"><span data-stu-id="e5fdd-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="e5fdd-166">确保已将 UnityAR 相机设置提供程序添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="e5fdd-167">在 Unity 生成设置中将平台切换到 Android 或 iOS</span><span class="sxs-lookup"><span data-stu-id="e5fdd-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="e5fdd-168">切换平台时，应会看到具有所选平台设置的 MRTK 项目配置器窗口。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="e5fdd-169">单击"应用"以启用特定于平台的设置。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="e5fdd-170">iOS 项目配置器设置</span><span class="sxs-lookup"><span data-stu-id="e5fdd-170">iOS Project Configurator Settings</span></span>

    ![iOS 项目配置器](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="e5fdd-172">切换适用于 Android 的平台后，不需要执行其他步骤。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="e5fdd-173">如果该平台为 iOS，请在 "优化" 标头下编辑 > 项目设置 > Player > 其他设置 "，然后 **取消选中** " 剥离引擎代码 "</span><span class="sxs-lookup"><span data-stu-id="e5fdd-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 设置](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="e5fdd-175">取消选中块代码是 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)中错误的短期解决方案。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="e5fdd-176">我们正在致力于长期解决方案。</span><span class="sxs-lookup"><span data-stu-id="e5fdd-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="e5fdd-177">生成和运行场景</span><span class="sxs-lookup"><span data-stu-id="e5fdd-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="e5fdd-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5fdd-178">See also</span></span>

- [<span data-ttu-id="e5fdd-179">Unity AR 照相机设置</span><span class="sxs-lookup"><span data-stu-id="e5fdd-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
