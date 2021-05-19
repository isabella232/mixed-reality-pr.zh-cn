---
title: 创建设置提供程序
description: MRTK 中相机设置的数据访问接口
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144893"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="92e84-104">创建相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="92e84-104">Creating a camera settings provider</span></span>

<span data-ttu-id="92e84-105">相机系统是一个可扩展的系统，用于为特定于平台的相机配置提供支持。</span><span class="sxs-lookup"><span data-stu-id="92e84-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="92e84-106">若要添加对新相机配置的支持，可能需要自定义设置提供程序。</span><span class="sxs-lookup"><span data-stu-id="92e84-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="92e84-107">可以在 **MRTK/Providers/UnityAR** 文件夹中找到此示例中使用的完整源代码。</span><span class="sxs-lookup"><span data-stu-id="92e84-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="92e84-108">命名空间和文件夹结构</span><span class="sxs-lookup"><span data-stu-id="92e84-108">Namespace and folder structure</span></span>

<span data-ttu-id="92e84-109">可通过两种方式之一分发数据提供程序：</span><span class="sxs-lookup"><span data-stu-id="92e84-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="92e84-110">第三方加载项</span><span class="sxs-lookup"><span data-stu-id="92e84-110">Third party add-ons</span></span>
1. <span data-ttu-id="92e84-111">Microsoft Mixed Reality Toolkit 的一部分</span><span class="sxs-lookup"><span data-stu-id="92e84-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="92e84-112">向 MRTK 提交新数据提供程序的审批过程将因情况而异，将在初始建议时传达。</span><span class="sxs-lookup"><span data-stu-id="92e84-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="92e84-113">可以通过创建新的功能请求类型问题 [*来提交* 建议](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)。</span><span class="sxs-lookup"><span data-stu-id="92e84-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="92e84-114">第三方加载项</span><span class="sxs-lookup"><span data-stu-id="92e84-114">Third party add-ons</span></span>

<span data-ttu-id="92e84-115">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="92e84-115">**Namespace**</span></span>

<span data-ttu-id="92e84-116">数据提供程序需要具有命名空间来缓解潜在的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="92e84-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="92e84-117">建议命名空间包含以下组件。</span><span class="sxs-lookup"><span data-stu-id="92e84-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="92e84-118">生成加载项的公司名称</span><span class="sxs-lookup"><span data-stu-id="92e84-118">Company name producing the add-on</span></span>
- <span data-ttu-id="92e84-119">功能区域</span><span class="sxs-lookup"><span data-stu-id="92e84-119">Feature area</span></span>

<span data-ttu-id="92e84-120">例如，Contoso 公司创建和发货的相机设置提供程序可能是 *"Contoso.MixedReality.Toolkit.Camera"。*</span><span class="sxs-lookup"><span data-stu-id="92e84-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="92e84-121">**文件夹结构**</span><span class="sxs-lookup"><span data-stu-id="92e84-121">**Folder structure**</span></span>

<span data-ttu-id="92e84-122">建议将数据提供程序的源代码布局在文件夹层次结构中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="92e84-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![文件夹结构示例](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="92e84-124">其中 *ContosoCamera* 文件夹包含数据提供程序的实现，Editor文件夹包含检查器 (和任何其他特定于 Unity 编辑器的代码) ，"*配置文件*"文件夹包含一个或多个预生成配置文件可脚本化对象。</span><span class="sxs-lookup"><span data-stu-id="92e84-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="92e84-125">MRTK 提交</span><span class="sxs-lookup"><span data-stu-id="92e84-125">MRTK submission</span></span>

<span data-ttu-id="92e84-126">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="92e84-126">**Namespace**</span></span>

<span data-ttu-id="92e84-127">如果将照相机设置提供程序提交到 [混合现实工具包存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，命名空间 **必须** 以 MixedReality 开头 (例如： *CameraSystem*) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="92e84-128">**文件夹结构**</span><span class="sxs-lookup"><span data-stu-id="92e84-128">**Folder structure**</span></span>

<span data-ttu-id="92e84-129">所有代码都必须位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/UnityAR) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="92e84-130">定义相机设置对象</span><span class="sxs-lookup"><span data-stu-id="92e84-130">Define the camera settings object</span></span>

<span data-ttu-id="92e84-131">创建照相机设置提供程序的第一步是确定数据类型 (例如：网格或平面将提供给应用程序) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="92e84-132">所有空间数据对象必须实现 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 接口。</span><span class="sxs-lookup"><span data-stu-id="92e84-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="92e84-133">实现设置提供程序</span><span class="sxs-lookup"><span data-stu-id="92e84-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="92e84-134">指定接口和/或基类继承</span><span class="sxs-lookup"><span data-stu-id="92e84-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="92e84-135">所有照相机设置提供程序必须实现 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 接口，该接口指定了照相机系统所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="92e84-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="92e84-136">MRTK foundation 包含类， [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 该类提供所需功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="92e84-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="92e84-137">应用 MixedRealityDataProvider 特性</span><span class="sxs-lookup"><span data-stu-id="92e84-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="92e84-138">创建照相机设置提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。</span><span class="sxs-lookup"><span data-stu-id="92e84-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="92e84-139">此步骤允许在照相机系统配置文件中选择默认配置文件和平台 () ，并在名称、文件夹路径等中进行选择。</span><span class="sxs-lookup"><span data-stu-id="92e84-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="92e84-140">实现 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="92e84-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="92e84-141">一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="92e84-142">[`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)类通过 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 类为方法提供空实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="92e84-143">这些方法的详细信息通常是特定于数据访问接口的。</span><span class="sxs-lookup"><span data-stu-id="92e84-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="92e84-144">应由数据提供程序实现的方法如下：</span><span class="sxs-lookup"><span data-stu-id="92e84-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="92e84-145">并非所有的设置提供程序都需要所有这些方法的实现。</span><span class="sxs-lookup"><span data-stu-id="92e84-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="92e84-146">强烈建议 `Destroy()` `Initialize()` 至少实现和。</span><span class="sxs-lookup"><span data-stu-id="92e84-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="92e84-147">实现数据访问接口逻辑</span><span class="sxs-lookup"><span data-stu-id="92e84-147">Implement the data provider logic</span></span>

<span data-ttu-id="92e84-148">下一步是通过实现 添加设置提供程序的逻辑 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 。</span><span class="sxs-lookup"><span data-stu-id="92e84-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="92e84-149">数据提供程序的这一部分通常特定于相机配置。</span><span class="sxs-lookup"><span data-stu-id="92e84-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="92e84-150">创建配置文件和检查器</span><span class="sxs-lookup"><span data-stu-id="92e84-150">Create the profile and inspector</span></span>

<span data-ttu-id="92e84-151">在混合现实工具包中，数据提供程序是使用配置文件 [配置的](../profiles/profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="92e84-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="92e84-152">定义配置文件</span><span class="sxs-lookup"><span data-stu-id="92e84-152">Define the profile</span></span>

<span data-ttu-id="92e84-153">配置文件内容应镜像开发人员可选择的配置选项。</span><span class="sxs-lookup"><span data-stu-id="92e84-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="92e84-154">每个接口中定义的任何用户可配置属性也应包含在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="92e84-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="92e84-155">属性可应用于配置文件类，使客户能够使用"创建资产混合现实工具包配置文件"菜单 `CreateAssetMenu`   >    >  **创建**  >  **配置文件** 实例。</span><span class="sxs-lookup"><span data-stu-id="92e84-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="92e84-156">实现检查器</span><span class="sxs-lookup"><span data-stu-id="92e84-156">Implement the inspector</span></span>

<span data-ttu-id="92e84-157">配置文件检查器是配置和查看配置文件内容的用户界面。</span><span class="sxs-lookup"><span data-stu-id="92e84-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="92e84-158">每个配置文件检查器都应扩展 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。</span><span class="sxs-lookup"><span data-stu-id="92e84-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="92e84-159">`CustomEditor`属性通知 Unity 检查器应用到的资产类型。</span><span class="sxs-lookup"><span data-stu-id="92e84-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="92e84-160">创建程序集 () </span><span class="sxs-lookup"><span data-stu-id="92e84-160">Create assembly definition(s)</span></span>

<span data-ttu-id="92e84-161">混合现实工具包使用程序集定义 ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 文件来指定组件之间的依赖关系，以及帮助 Unity 减少编译时间。</span><span class="sxs-lookup"><span data-stu-id="92e84-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="92e84-162">建议为所有数据提供程序及其编辑器组件创建程序集定义文件。</span><span class="sxs-lookup"><span data-stu-id="92e84-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="92e84-163">使用 [前面示例中](#namespace-and-folder-structure) 的文件夹结构，ContosoCamera 数据提供程序有两个 .asmdef 文件。</span><span class="sxs-lookup"><span data-stu-id="92e84-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="92e84-164">第一个程序集定义用于数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="92e84-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="92e84-165">对于此示例，它将称为 ContosoCamera，并位于示例的 *ContosoCamera* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="92e84-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="92e84-166">此程序集定义必须指定对 Microsoft.MixedReality.Toolkit 及其依赖的其他任何程序集的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="92e84-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="92e84-167">ContosoCameraEditor 程序集定义将指定配置文件检查器以及任何特定于编辑器的代码。</span><span class="sxs-lookup"><span data-stu-id="92e84-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="92e84-168">此文件必须位于编辑器代码的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="92e84-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="92e84-169">在此示例中，该文件将位于 *ContosoCamera\Editor* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="92e84-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="92e84-170">此程序集定义将包含对 ContosoCamera 程序集的引用以及：</span><span class="sxs-lookup"><span data-stu-id="92e84-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="92e84-171">MixedReality 工具包</span><span class="sxs-lookup"><span data-stu-id="92e84-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="92e84-172">MixedReality。检查器</span><span class="sxs-lookup"><span data-stu-id="92e84-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="92e84-173">MixedReality 实用程序。</span><span class="sxs-lookup"><span data-stu-id="92e84-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="92e84-174">注册数据提供程序</span><span class="sxs-lookup"><span data-stu-id="92e84-174">Register the data provider</span></span>

<span data-ttu-id="92e84-175">创建后，可以向照相机系统注册数据提供程序，以便在应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="92e84-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![选择相机设置提供程序](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="92e84-177">打包和分发</span><span class="sxs-lookup"><span data-stu-id="92e84-177">Packaging and distribution</span></span>

<span data-ttu-id="92e84-178">作为第三方组件分发的数据提供程序具有与开发人员首选项一起打包和分发的特定详细信息。</span><span class="sxs-lookup"><span data-stu-id="92e84-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="92e84-179">最常见的解决方案是生成 unitypackage，并通过 Unity 资产存储进行分发。</span><span class="sxs-lookup"><span data-stu-id="92e84-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="92e84-180">如果将数据访问接口作为 Microsoft Mixed Reality 工具包的一部分进行提交和接受，Microsoft MRTK 团队会将其打包并分发为 MRTK 服务的一部分。</span><span class="sxs-lookup"><span data-stu-id="92e84-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="92e84-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92e84-181">See also</span></span>

- [<span data-ttu-id="92e84-182">照相机系统概述</span><span class="sxs-lookup"><span data-stu-id="92e84-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="92e84-183">`BaseCameraSettingsProvider` 类</span><span class="sxs-lookup"><span data-stu-id="92e84-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="92e84-184">`IMixedRealityCameraSettingsProvider` 交互</span><span class="sxs-lookup"><span data-stu-id="92e84-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="92e84-185">`IMixedRealityDataProvider` 交互</span><span class="sxs-lookup"><span data-stu-id="92e84-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
