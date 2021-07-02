---
title: 场景理解观察程序
description: 介绍 MRTK 中的场景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，场景理解
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176230"
---
# <a name="scene-understanding-observer"></a><span data-ttu-id="6fad6-104">场景理解观察程序</span><span class="sxs-lookup"><span data-stu-id="6fad6-104">Scene understanding observer</span></span>

<span data-ttu-id="6fad6-105">[场景理解](/windows/mixed-reality/scene-understanding)返回场景实体的语义表示形式，并在 __HoloLens 2__ (不支持 HoloLens 第一代中的几何窗体) 。</span><span class="sxs-lookup"><span data-stu-id="6fad6-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="6fad6-106">此技术的一些预期用例如下：</span><span class="sxs-lookup"><span data-stu-id="6fad6-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="6fad6-107">将对象置于特定类型的最近图面上 (例如墙壁和地面) </span><span class="sxs-lookup"><span data-stu-id="6fad6-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="6fad6-108">构造平台样式游戏的导航网格</span><span class="sxs-lookup"><span data-stu-id="6fad6-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="6fad6-109">提供物理引擎友好几何作为四边形</span><span class="sxs-lookup"><span data-stu-id="6fad6-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="6fad6-110">通过避免编写类似的算法来加速开发</span><span class="sxs-lookup"><span data-stu-id="6fad6-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="6fad6-111">在 MRTK 2.6 中引入了场景理解作为 __实验__ 性功能。</span><span class="sxs-lookup"><span data-stu-id="6fad6-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="6fad6-112">它集成到 MRTK 中，作为名为的 [空间观察](spatial-awareness-getting-started.md#register-observers) 程序 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。</span><span class="sxs-lookup"><span data-stu-id="6fad6-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="6fad6-113">场景理解既适用于旧的 XR 管道，也适用于 XR SDK 管道 (从 MRTK 2.7) 和 Windows XR 插件) 开始的 OpenXR (。</span><span class="sxs-lookup"><span data-stu-id="6fad6-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="6fad6-114">在这两种情况下， `WindowsSceneUnderstandingObserver` 都使用。</span><span class="sxs-lookup"><span data-stu-id="6fad6-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="6fad6-115">不支持在远程处理中使用场景理解。</span><span class="sxs-lookup"><span data-stu-id="6fad6-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="6fad6-116">观察程序概述</span><span class="sxs-lookup"><span data-stu-id="6fad6-116">Observer overview</span></span>

<span data-ttu-id="6fad6-117">当系统询问时， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 将返回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其属性对应用程序有用，以了解其环境。</span><span class="sxs-lookup"><span data-stu-id="6fad6-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="6fad6-118">观察频率、返回的对象类型 (例如墙壁、楼层) 和其他观察者行为取决于观察者通过配置文件的配置。</span><span class="sxs-lookup"><span data-stu-id="6fad6-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="6fad6-119">例如，如果需要封闭掩码，则必须将观察程序配置为生成四边形。</span><span class="sxs-lookup"><span data-stu-id="6fad6-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="6fad6-120">观察到的场景可以保存为序列化文件，稍后可以将其加载以便在编辑器播放模式下重新创建场景。</span><span class="sxs-lookup"><span data-stu-id="6fad6-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="6fad6-121">设置</span><span class="sxs-lookup"><span data-stu-id="6fad6-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fad6-122">仅 HoloLens 2 和 Unity 2019.4 及更高版本支持场景理解。</span><span class="sxs-lookup"><span data-stu-id="6fad6-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="6fad6-123">确保在 "生成设置" 中将平台设置为 UWP。</span><span class="sxs-lookup"><span data-stu-id="6fad6-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="6fad6-124">通过 [混合现实功能工具](https://aka.ms/MRFeatureTool)获取场景理解包。</span><span class="sxs-lookup"><span data-stu-id="6fad6-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="6fad6-125">使用场景理解</span><span class="sxs-lookup"><span data-stu-id="6fad6-125">Using Scene Understanding</span></span>

<span data-ttu-id="6fad6-126">了解场景理解的最快捷方法是查看示例场景。</span><span class="sxs-lookup"><span data-stu-id="6fad6-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="6fad6-127">场景了解示例场景</span><span class="sxs-lookup"><span data-stu-id="6fad6-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="6fad6-128">在 Unity 中，使用 "Project 资源管理器" 打开场景文件 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` ，然后按 "播放"！</span><span class="sxs-lookup"><span data-stu-id="6fad6-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="6fad6-129">仅适用于 MRTK 2.6.0-如果使用混合现实功能工具或通过 UPM 导入，请在导入 SpatialAwareness 示例之前导入示例，因为存在依赖关系问题。</span><span class="sxs-lookup"><span data-stu-id="6fad6-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="6fad6-130">有关详细信息，请参阅[此 GitHub 问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)。</span><span class="sxs-lookup"><span data-stu-id="6fad6-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="6fad6-131">场景演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="6fad6-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="6fad6-132">在应用程序 UI 中用来配置观察程序的观察场景对象的可视化</span><span class="sxs-lookup"><span data-stu-id="6fad6-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="6fad6-133">示例 `DemoSceneUnderstandingController` 脚本，演示如何更改观察程序设置和侦听相关事件</span><span class="sxs-lookup"><span data-stu-id="6fad6-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="6fad6-134">将场景数据保存到设备以进行离线开发</span><span class="sxs-lookup"><span data-stu-id="6fad6-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="6fad6-135">加载以前保存的场景数据 ( 字节文件) 以支持编辑器内开发工作流</span><span class="sxs-lookup"><span data-stu-id="6fad6-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fad6-136">默认情况下，观察者的 `ShouldLoadFromFile` 属性设置为 false。</span><span class="sxs-lookup"><span data-stu-id="6fad6-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="6fad6-137">若要查看序列化示例文件的可视化效果，请参阅下面的 [配置观察程序服务](#configuring-the-observer-service) 部分，并在编辑器中将属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="6fad6-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="6fad6-138">示例场景基于旧的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="6fad6-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="6fad6-139">如果使用 XR SDK 管道，则应相应地修改配置文件。</span><span class="sxs-lookup"><span data-stu-id="6fad6-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="6fad6-140">提供的场景了解空间感知系统配置文件 (`DemoSceneUnderstandingSystemProfile`) 和场景了解观察程序配置文件 (`DefaultSceneUnderstandingObserverProfile` 和 `DemoSceneUnderstandingObserverProfile`) 适用于这两个管道。</span><span class="sxs-lookup"><span data-stu-id="6fad6-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="6fad6-141">在某些情况下，示例场景会记录一个 `There is no active AsyncCoroutineRunner when an action is posted.` 警告，因为初始化/线程执行顺序。</span><span class="sxs-lookup"><span data-stu-id="6fad6-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="6fad6-142">如果可以确认 `AsyncCoroutineRunner` 组件已附加到 "Demo 控制器" GameObject，并 (在) 默认情况下，组件/GameObject 保持启用/活动状态，则可以安全地忽略该警告。</span><span class="sxs-lookup"><span data-stu-id="6fad6-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="6fad6-143">**但是，在使用场景理解创建新场景时，请确保在根上创建一个空的 GameObject 并将 `AsyncCoroutineRunner` 其附加到该位置，否则场景理解可能无法正常工作。**</span><span class="sxs-lookup"><span data-stu-id="6fad6-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="6fad6-144">配置观察程序服务</span><span class="sxs-lookup"><span data-stu-id="6fad6-144">Configuring the observer service</span></span>

<span data-ttu-id="6fad6-145">选择 "MixedRealityToolkit" 游戏对象并检查检查器。</span><span class="sxs-lookup"><span data-stu-id="6fad6-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![在层次结构中了解位置的场景](../images/spatial-awareness/MRTKHierarchy.png)

![检查器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="6fad6-148">这些选项允许配置 `WindowsSceneUnderstandingObserver` 。</span><span class="sxs-lookup"><span data-stu-id="6fad6-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="6fad6-149">示例脚本</span><span class="sxs-lookup"><span data-stu-id="6fad6-149">Example script</span></span>

<span data-ttu-id="6fad6-150">示例脚本 _DemoSceneUnderstandingController_ 演示了使用场景理解服务的主要概念。</span><span class="sxs-lookup"><span data-stu-id="6fad6-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="6fad6-151">订阅场景理解事件</span><span class="sxs-lookup"><span data-stu-id="6fad6-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="6fad6-152">处理场景理解事件</span><span class="sxs-lookup"><span data-stu-id="6fad6-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="6fad6-153">`WindowsSceneUnderstandingObserver`在运行时配置</span><span class="sxs-lookup"><span data-stu-id="6fad6-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="6fad6-154">屏幕上面板上的切换通过调用此示例脚本的公共函数，更改场景理解观察程序的行为。</span><span class="sxs-lookup"><span data-stu-id="6fad6-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="6fad6-155">打开 *实例化 prototyping*，将演示如何创建适合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小的对象，并在父对象下进行整齐收集。</span><span class="sxs-lookup"><span data-stu-id="6fad6-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![演示控制器选项](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="6fad6-157">生成的应用说明</span><span class="sxs-lookup"><span data-stu-id="6fad6-157">Built app notes</span></span>

<span data-ttu-id="6fad6-158">以标准方式生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6fad6-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="6fad6-159">运行后，将出现一些按钮，这些按钮可用于功能。</span><span class="sxs-lookup"><span data-stu-id="6fad6-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="6fad6-160">请注意，有一些 pit 正在向观察者发出查询。</span><span class="sxs-lookup"><span data-stu-id="6fad6-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="6fad6-161">错误配置请求导致事件负载中不包含预期数据。</span><span class="sxs-lookup"><span data-stu-id="6fad6-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="6fad6-162">例如，如果一个没有请求四边形，则不会显示任何封闭掩码纹理。</span><span class="sxs-lookup"><span data-stu-id="6fad6-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="6fad6-163">类似地，如果未将观察者配置为请求网格，则不会显示世界网格。</span><span class="sxs-lookup"><span data-stu-id="6fad6-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="6fad6-164">此 `DemoSceneUnderstandingController` 脚本负责处理其中的某些依赖项，但并非全部。</span><span class="sxs-lookup"><span data-stu-id="6fad6-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="6fad6-165">可以通过中的 [设备门户](/windows/mixed-reality/using-the-windows-device-portal) 访问已保存的场景文件 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。</span><span class="sxs-lookup"><span data-stu-id="6fad6-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="6fad6-166">可以通过在 "检查器" 中找到的观察程序配置文件中指定这些场景文件，在编辑器中使用这些文件。</span><span class="sxs-lookup"><span data-stu-id="6fad6-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![字节文件的设备门户位置](../images/spatial-awareness/BytesInDevicePortal.png)

![观察程序中的序列化场景字节](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="6fad6-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fad6-169">See Also</span></span>

* [<span data-ttu-id="6fad6-170">场景理解概述</span><span class="sxs-lookup"><span data-stu-id="6fad6-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="6fad6-171">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="6fad6-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)
