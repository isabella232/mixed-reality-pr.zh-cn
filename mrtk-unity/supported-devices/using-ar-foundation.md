---
title: 部署到 Android 和 iOS (AR Foundation) [实验]
description: 在 unity 中配置适用于 Android 和 iOS 的 MRTK (ARFoundation) 文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， AR Core， AR Kit， iOS， IOS， Android， AR Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281947"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a><span data-ttu-id="e4b8d-104">部署到 Android 和 iOS (AR Foundation) [实验]</span><span class="sxs-lookup"><span data-stu-id="e4b8d-104">Deploying to Android and iOS (AR Foundation) [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="e4b8d-105">安装所需程序包</span><span class="sxs-lookup"><span data-stu-id="e4b8d-105">Install required packages</span></span>

1. <span data-ttu-id="e4b8d-106">下载并导入 **Microsoft.MixedReality.Toolkit。Unity.Foundation** 包 [，GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)或 Unity [程序包管理器](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="e4b8d-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="e4b8d-107">在 Unity 程序包管理器 (UPM) 中，安装以下包：</span><span class="sxs-lookup"><span data-stu-id="e4b8d-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="e4b8d-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="e4b8d-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-109">**Android**</span></span> | <span data-ttu-id="e4b8d-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-110">**iOS**</span></span> | <span data-ttu-id="e4b8d-111">注释</span><span class="sxs-lookup"><span data-stu-id="e4b8d-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="e4b8d-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-112">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-113">版本：1.5.0 - 预览版 6</span><span class="sxs-lookup"><span data-stu-id="e4b8d-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e4b8d-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-114">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-115">版本：1.5.0 - 预览版 6</span><span class="sxs-lookup"><span data-stu-id="e4b8d-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e4b8d-116">对于 Unity 2018.4，此包以预览版提供。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="e4b8d-117">查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="e4b8d-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="e4b8d-118">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-119">版本：2.1.2</span><span class="sxs-lookup"><span data-stu-id="e4b8d-119">Version: 2.1.2</span></span> | <span data-ttu-id="e4b8d-120">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-121">版本：2.1.2</span><span class="sxs-lookup"><span data-stu-id="e4b8d-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="e4b8d-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="e4b8d-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-123">**Android**</span></span> | <span data-ttu-id="e4b8d-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e4b8d-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-125">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-126">版本：2.1.8</span><span class="sxs-lookup"><span data-stu-id="e4b8d-126">Version: 2.1.8</span></span> |  <span data-ttu-id="e4b8d-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-127">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-128">版本：2.1.8</span><span class="sxs-lookup"><span data-stu-id="e4b8d-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="e4b8d-129">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="e4b8d-130">Version: 2.1.11</span></span> | <span data-ttu-id="e4b8d-131">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-132">版本：2.1.9</span><span class="sxs-lookup"><span data-stu-id="e4b8d-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="e4b8d-133">**Unity 2020.3.x**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="e4b8d-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-134">**Android**</span></span> | <span data-ttu-id="e4b8d-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e4b8d-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-136">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-137">版本：3.1.3</span><span class="sxs-lookup"><span data-stu-id="e4b8d-137">Version: 3.1.3</span></span> |  <span data-ttu-id="e4b8d-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="e4b8d-138">AR Foundation</span></span>  <br/> <span data-ttu-id="e4b8d-139">版本：4.0.12</span><span class="sxs-lookup"><span data-stu-id="e4b8d-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="e4b8d-140">ARCore XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-141">版本：3.1.4</span><span class="sxs-lookup"><span data-stu-id="e4b8d-141">Version: 3.1.4</span></span> | <span data-ttu-id="e4b8d-142">ARKit XR 插件</span><span class="sxs-lookup"><span data-stu-id="e4b8d-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e4b8d-143">版本：4.1.7</span><span class="sxs-lookup"><span data-stu-id="e4b8d-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="e4b8d-144">通过调用菜单项更新 MRTK UnityAR 脚本定义：UnityAR > Toolkit >实用工具> **UnityAR >脚本定义**</span><span class="sxs-lookup"><span data-stu-id="e4b8d-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![更新脚本定义](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="e4b8d-146">启用 Unity AR 相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="e4b8d-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="e4b8d-147">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e4b8d-148">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e4b8d-149">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="e4b8d-151">选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="e4b8d-153">选择 **"相机** 配置文件"旁边的"克隆"。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-153">Select **Clone** next to the Camera Profile.</span></span>

    ![克隆 MRTK 相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="e4b8d-155">将"检查器"面板导航到"相机系统"部分，然后展开"相机 **设置提供程序"** 部分。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="e4b8d-157">单击 **"添加设置** 提供程序"，然后展开新 **添加的"新建相机设置"** 条目。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展开新设置提供程序](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="e4b8d-159">选择 Unity AR 相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="e4b8d-159">Select the Unity AR Camera Settings provider</span></span>

    ![选择 Unity AR 设置提供程序](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="e4b8d-161">有关配置 Unity AR 相机设置提供程序的信息，请参阅 [Unity AR 相机设置提供程序](../features/camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e4b8d-162">当应用程序 (AR Foundation 组件) 时，此安装会检查其运行状况。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="e4b8d-163">如果没有，则会自动添加它们，使其与 ARCore 和 ARKit 一同使用。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="e4b8d-164">如果需要设置特定行为，应自己添加所需的组件。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="e4b8d-165">有关 AR Foundation 组件和安装的信息，请查看 [此文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="e4b8d-166">生成适用于 Android 和 iOS 设备的场景</span><span class="sxs-lookup"><span data-stu-id="e4b8d-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="e4b8d-167">确保已将 UnityAR 相机设置提供程序添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="e4b8d-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="e4b8d-168">在 Unity 生成工具中将平台切换到 Android 或 iOS 设置</span><span class="sxs-lookup"><span data-stu-id="e4b8d-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="e4b8d-169">确保已启用关联的 XR 插件管理提供程序</span><span class="sxs-lookup"><span data-stu-id="e4b8d-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="e4b8d-170">iOS XR 插件管理  ![ ：XR 插件管理 iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="e4b8d-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="e4b8d-171">生成并运行场景</span><span class="sxs-lookup"><span data-stu-id="e4b8d-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="e4b8d-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4b8d-172">See also</span></span>

- [<span data-ttu-id="e4b8d-173">Unity AR 相机设置</span><span class="sxs-lookup"><span data-stu-id="e4b8d-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
