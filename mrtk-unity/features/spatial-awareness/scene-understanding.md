---
title: 场景理解
description: 介绍 MRTK 中的场景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 场景理解
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449746"
---
# <a name="scene-understanding"></a><span data-ttu-id="0242f-104">场景理解</span><span class="sxs-lookup"><span data-stu-id="0242f-104">Scene Understanding</span></span>

<span data-ttu-id="0242f-105">[场景理解](/windows/mixed-reality/scene-understanding)返回场景实体的语义表示形式及其HoloLens 2 (HoloLens  1 Gen 不支持) 。</span><span class="sxs-lookup"><span data-stu-id="0242f-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="0242f-106">此技术的一些预期用例包括：</span><span class="sxs-lookup"><span data-stu-id="0242f-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="0242f-107">将对象放在某种类型的最近表面上 (例如墙和地板) </span><span class="sxs-lookup"><span data-stu-id="0242f-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="0242f-108">为平台样式游戏构造导航网格</span><span class="sxs-lookup"><span data-stu-id="0242f-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="0242f-109">提供物理引擎友好几何图形作为四边形</span><span class="sxs-lookup"><span data-stu-id="0242f-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="0242f-110">通过避免编写类似的算法来加速开发</span><span class="sxs-lookup"><span data-stu-id="0242f-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="0242f-111">场景理解是 MRTK 2.6 中的实验性功能。 </span><span class="sxs-lookup"><span data-stu-id="0242f-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="0242f-112">它作为名为 的空间观察器集成到[](spatial-awareness-getting-started.md#register-observers)MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 中。</span><span class="sxs-lookup"><span data-stu-id="0242f-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="0242f-113">场景理解适用于旧版 XR 管道和 XR SDK 管道 (OpenXR (从 MRTK 2.7) 和 Windows XR 插件) 开始。</span><span class="sxs-lookup"><span data-stu-id="0242f-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="0242f-114">在这两种情况下都 `WindowsSceneUnderstandingObserver` 使用 。</span><span class="sxs-lookup"><span data-stu-id="0242f-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="0242f-115">不支持在远程处理中使用场景理解。</span><span class="sxs-lookup"><span data-stu-id="0242f-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="0242f-116">观察者概述</span><span class="sxs-lookup"><span data-stu-id="0242f-116">Observer overview</span></span>

<span data-ttu-id="0242f-117">当系统询问时， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 将返回 [SpatialAwarenessSceneObject，](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 其属性对应用程序了解其周围的环境很有用。</span><span class="sxs-lookup"><span data-stu-id="0242f-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="0242f-118">观察频率、返回的对象类型 (例如墙、) 和其他观察者行为取决于通过配置文件对观察者的配置。</span><span class="sxs-lookup"><span data-stu-id="0242f-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="0242f-119">例如，如果需要遮挡掩码，则必须将观察程序配置为生成四边形。</span><span class="sxs-lookup"><span data-stu-id="0242f-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="0242f-120">观察到的场景可以保存为序列化文件，稍后可以加载该文件以在编辑器播放模式下重新创建场景。</span><span class="sxs-lookup"><span data-stu-id="0242f-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="0242f-121">设置</span><span class="sxs-lookup"><span data-stu-id="0242f-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0242f-122">场景理解仅在 HoloLens 2 Unity 2019.4 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="0242f-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="0242f-123">确保在生成设置中将平台设置为 UWP。</span><span class="sxs-lookup"><span data-stu-id="0242f-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="0242f-124">通过混合现实功能工具 [获取场景理解包](https://aka.ms/MRFeatureTool)。</span><span class="sxs-lookup"><span data-stu-id="0242f-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="0242f-125">使用场景理解</span><span class="sxs-lookup"><span data-stu-id="0242f-125">Using Scene Understanding</span></span>

<span data-ttu-id="0242f-126">开始使用场景理解的最快方法就是查看示例场景。</span><span class="sxs-lookup"><span data-stu-id="0242f-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="0242f-127">场景理解示例场景</span><span class="sxs-lookup"><span data-stu-id="0242f-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="0242f-128">在 Unity 中，使用项目资源管理器打开 中的场景文件 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` 并按 play！</span><span class="sxs-lookup"><span data-stu-id="0242f-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="0242f-129">仅适用于 MRTK 2.6.0 - 使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。</span><span class="sxs-lookup"><span data-stu-id="0242f-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="0242f-130">有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。</span><span class="sxs-lookup"><span data-stu-id="0242f-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="0242f-131">场景演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="0242f-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="0242f-132">在应用程序 UI 中通过 可视化观察场景对象来配置观察程序</span><span class="sxs-lookup"><span data-stu-id="0242f-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="0242f-133">演示如何 `DemoSceneUnderstandingController` 更改观察者设置并侦听相关事件的示例脚本</span><span class="sxs-lookup"><span data-stu-id="0242f-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="0242f-134">将场景数据保存至设备进行脱机开发</span><span class="sxs-lookup"><span data-stu-id="0242f-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="0242f-135">将以前保存的场景数据 (.bytes 文件) 以支持编辑器内开发工作流</span><span class="sxs-lookup"><span data-stu-id="0242f-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0242f-136">默认情况下， `ShouldLoadFromFile` 观察者的 属性设置为 false。</span><span class="sxs-lookup"><span data-stu-id="0242f-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="0242f-137">若要查看序列化示例房间的可视化效果，请参阅下面的配置观察程序 [服务](#configuring-the-observer-service) 部分，在编辑器中将 属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="0242f-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="0242f-138">示例场景基于旧版 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="0242f-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="0242f-139">如果使用 XR SDK 管道，应相应地修改配置文件。</span><span class="sxs-lookup"><span data-stu-id="0242f-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="0242f-140">提供的场景理解空间感知系统配置文件 () 和场景理解观察器配置文件 (`DemoSceneUnderstandingSystemProfile` `DefaultSceneUnderstandingObserverProfile` 和) `DemoSceneUnderstandingObserverProfile` 都适用于这两个管道。</span><span class="sxs-lookup"><span data-stu-id="0242f-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="0242f-141">由于初始化/线程执行 `There is no active AsyncCoroutineRunner when an action is posted.` 顺序，示例场景在某些情况下记录警告。</span><span class="sxs-lookup"><span data-stu-id="0242f-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="0242f-142">如果可以确认组件已附加到"演示控制器 `AsyncCoroutineRunner` "GameObject，并且组件/GameObject 在场景中保持启用/活动状态 (默认) ，可以放心忽略警告。</span><span class="sxs-lookup"><span data-stu-id="0242f-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="0242f-143">**但是，使用场景理解创建新场景时，请确保在根目录创建空 GameObject 并将脚本附加到该场景，否则场景理解 `AsyncCoroutineRunner` 可能无法正常运行。**</span><span class="sxs-lookup"><span data-stu-id="0242f-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="0242f-144">配置观察程序服务</span><span class="sxs-lookup"><span data-stu-id="0242f-144">Configuring the observer service</span></span>

<span data-ttu-id="0242f-145">选择"MixedRealityToolkit"游戏对象并检查检查器。</span><span class="sxs-lookup"><span data-stu-id="0242f-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![场景了解层次结构中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![检查器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="0242f-148">这些选项将允许配置 `WindowsSceneUnderstandingObserver` 。</span><span class="sxs-lookup"><span data-stu-id="0242f-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="0242f-149">示例脚本</span><span class="sxs-lookup"><span data-stu-id="0242f-149">Example script</span></span>

<span data-ttu-id="0242f-150">示例脚本 _DemoSceneUnderunderunderController.cs_ 演示了使用场景理解服务时的主要概念。</span><span class="sxs-lookup"><span data-stu-id="0242f-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="0242f-151">订阅场景理解事件</span><span class="sxs-lookup"><span data-stu-id="0242f-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="0242f-152">处理场景理解事件</span><span class="sxs-lookup"><span data-stu-id="0242f-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="0242f-153">在运行时 `WindowsSceneUnderstandingObserver` 配置</span><span class="sxs-lookup"><span data-stu-id="0242f-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="0242f-154">场景中面板上的切换通过调用此示例脚本的公共函数来更改场景理解观察器的行为。</span><span class="sxs-lookup"><span data-stu-id="0242f-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="0242f-155">打开 *实例化预制件*，将演示如何创建大小适合自身以适应所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的对象，这些对象在父对象下完全收集。</span><span class="sxs-lookup"><span data-stu-id="0242f-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![演示控制器选项](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="0242f-157">生成应用说明</span><span class="sxs-lookup"><span data-stu-id="0242f-157">Built app notes</span></span>

<span data-ttu-id="0242f-158">以标准方式生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0242f-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="0242f-159">运行后，应会显示多个按钮以使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="0242f-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="0242f-160">请注意，向观察器进行查询时存在一些问题。</span><span class="sxs-lookup"><span data-stu-id="0242f-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="0242f-161">提取请求配置错误会导致事件有效负载不包含预期数据。</span><span class="sxs-lookup"><span data-stu-id="0242f-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="0242f-162">例如，如果用户不请求四边形，则不存在遮挡掩码纹理。</span><span class="sxs-lookup"><span data-stu-id="0242f-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="0242f-163">与明智一样，如果观察程序未配置为请求网格，则不会出现任何世界网格。</span><span class="sxs-lookup"><span data-stu-id="0242f-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="0242f-164">`DemoSceneUnderstandingController`该脚本负责处理其中一些依赖项，但并非所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="0242f-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="0242f-165">可以通过 设备门户访问保存的 [场景](/windows/mixed-reality/using-the-windows-device-portal) 文件 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。</span><span class="sxs-lookup"><span data-stu-id="0242f-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="0242f-166">可以通过在检查器中的观察程序配置文件中指定这些场景文件，在编辑器中使用这些场景文件。</span><span class="sxs-lookup"><span data-stu-id="0242f-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![设备门户字节文件的位置](../images/spatial-awareness/BytesInDevicePortal.png)

![观察程序中的序列化场景字节数](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="0242f-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0242f-169">See Also</span></span>

* [<span data-ttu-id="0242f-170">场景理解概述</span><span class="sxs-lookup"><span data-stu-id="0242f-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="0242f-171">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="0242f-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)