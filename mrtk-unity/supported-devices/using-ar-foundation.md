---
title: 使用 AR Foundation
description: 在 unity 中使用 ARFoundation 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，AR Core，AR 工具包
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143944"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="8ee8d-104">如何配置适用于 iOS 和 Android 的 MRTK [实验]</span><span class="sxs-lookup"><span data-stu-id="8ee8d-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="8ee8d-105">安装所需程序包</span><span class="sxs-lookup"><span data-stu-id="8ee8d-105">Install required packages</span></span>

1. <span data-ttu-id="8ee8d-106">从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [Unity 包管理器](../configuration/usingupm.md)下载并导入 **MixedReality** 包</span><span class="sxs-lookup"><span data-stu-id="8ee8d-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="8ee8d-107">在 Unity 包管理器 (UPM) 中，安装以下包：</span><span class="sxs-lookup"><span data-stu-id="8ee8d-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="8ee8d-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="8ee8d-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-109">**Android**</span></span> | <span data-ttu-id="8ee8d-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-110">**iOS**</span></span> | <span data-ttu-id="8ee8d-111">注释</span><span class="sxs-lookup"><span data-stu-id="8ee8d-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="8ee8d-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-112">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-113">版本： 1.5.0 _ 预览6</span><span class="sxs-lookup"><span data-stu-id="8ee8d-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8ee8d-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-114">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-115">版本： 1.5.0 _ 预览6</span><span class="sxs-lookup"><span data-stu-id="8ee8d-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="8ee8d-116">对于 Unity 2018.4，此包包含为预览版。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="8ee8d-117">查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="8ee8d-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="8ee8d-118">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-119">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="8ee8d-119">Version: 2.1.2</span></span> | <span data-ttu-id="8ee8d-120">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-121">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="8ee8d-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="8ee8d-122">**Unity 2019。4**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="8ee8d-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-123">**Android**</span></span> | <span data-ttu-id="8ee8d-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8ee8d-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-125">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-126">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="8ee8d-126">Version: 2.1.8</span></span> |  <span data-ttu-id="8ee8d-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-127">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-128">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="8ee8d-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="8ee8d-129">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="8ee8d-130">Version: 2.1.11</span></span> | <span data-ttu-id="8ee8d-131">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-132">版本：2.1.9</span><span class="sxs-lookup"><span data-stu-id="8ee8d-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="8ee8d-133">**Unity 2020.1.x (目前不受正式支持，仅出于信息目的包含在)**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="8ee8d-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-134">**Android**</span></span> | <span data-ttu-id="8ee8d-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="8ee8d-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-136">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-137">版本：3.1.3</span><span class="sxs-lookup"><span data-stu-id="8ee8d-137">Version: 3.1.3</span></span> |  <span data-ttu-id="8ee8d-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="8ee8d-138">AR Foundation</span></span>  <br/> <span data-ttu-id="8ee8d-139">版本：3.1.3</span><span class="sxs-lookup"><span data-stu-id="8ee8d-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="8ee8d-140">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-141">版本：3.1.4</span><span class="sxs-lookup"><span data-stu-id="8ee8d-141">Version: 3.1.4</span></span> | <span data-ttu-id="8ee8d-142">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="8ee8d-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="8ee8d-143">版本：3.1.3</span><span class="sxs-lookup"><span data-stu-id="8ee8d-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="8ee8d-144">通过调用菜单项更新 MRTK UnityAR 脚本定义：混合现实工具包 > 实用工具 > **UnityAR >更新脚本定义**</span><span class="sxs-lookup"><span data-stu-id="8ee8d-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="8ee8d-145">启用 Unity AR 相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="8ee8d-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="8ee8d-146">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="8ee8d-147">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="8ee8d-148">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="8ee8d-150">选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="8ee8d-152">选择照相机配置文件旁边的 " **克隆** "。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-152">Select **Clone** next to the Camera Profile.</span></span>

    ![克隆 MRTK 照相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="8ee8d-154">将检查器面板导航到 "照相机系统" 部分，然后展开 " **照相机设置提供程序** " 部分。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="8ee8d-156">单击 " **添加照相机设置提供程序** "，然后展开新添加的 " **相机设置** " 条目。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展开新的设置提供程序](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="8ee8d-158">选择 Unity AR 照相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="8ee8d-158">Select the Unity AR Camera Settings provider</span></span>

    ![选择 Unity AR 设置提供程序](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="8ee8d-160">有关配置 Unity AR 照相机设置提供程序的详细信息： [UNITY ar 照相机设置提供程序](../features/camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ee8d-161">当应用程序启动时，此安装检查 () 如果 AR 基础组件在场景中。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="8ee8d-162">否则，会自动添加它们以使其与 ARCore 和 ARKit 一起使用。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="8ee8d-163">如果需要设置特定行为，你应该自行添加所需的组件。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="8ee8d-164">有关 AR Foundation 组件和安装的详细信息，请查看此 [文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="8ee8d-165">构建适用于 Android 和 iOS 设备的场景</span><span class="sxs-lookup"><span data-stu-id="8ee8d-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="8ee8d-166">请确保已将 UnityAR 照相机设置提供程序添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="8ee8d-167">在 Unity 生成设置中将平台切换到 Android 或 iOS</span><span class="sxs-lookup"><span data-stu-id="8ee8d-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="8ee8d-168">切换平台时，应会看到 "MRTK 项目配置器" 窗口，其中包含所选平台的设置。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="8ee8d-169">单击 "应用" 以启用特定于平台的设置。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="8ee8d-170">iOS 项目配置器设置</span><span class="sxs-lookup"><span data-stu-id="8ee8d-170">iOS Project Configurator Settings</span></span>

    ![iOS 项目配置器](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="8ee8d-172">切换适用于 Android 的平台后，无需执行其他步骤。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="8ee8d-173">如果平台为 iOS，请>">播放器">"其他设置"下，取消选中"条 **带引擎代码** "</span><span class="sxs-lookup"><span data-stu-id="8ee8d-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 设置](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="8ee8d-175">取消选中"带状引擎代码"是 Xcode 中错误的短期[#6646。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)</span><span class="sxs-lookup"><span data-stu-id="8ee8d-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="8ee8d-176">我们正在努力解决长期问题。</span><span class="sxs-lookup"><span data-stu-id="8ee8d-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="8ee8d-177">生成并运行场景</span><span class="sxs-lookup"><span data-stu-id="8ee8d-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="8ee8d-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ee8d-178">See also</span></span>

- [<span data-ttu-id="8ee8d-179">Unity AR 相机设置</span><span class="sxs-lookup"><span data-stu-id="8ee8d-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
