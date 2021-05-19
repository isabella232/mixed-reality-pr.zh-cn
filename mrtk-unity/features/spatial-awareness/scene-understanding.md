---
title: 场景理解
description: 介绍 MRTK 中的场景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，场景理解
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143887"
---
# <a name="scene-understanding"></a><span data-ttu-id="e2677-104">场景理解</span><span class="sxs-lookup"><span data-stu-id="e2677-104">Scene Understanding</span></span>

<span data-ttu-id="e2677-105">[场景理解](/windows/mixed-reality/scene-understanding) 返回场景实体的语义表示形式，并在 __HoloLens 2__ (hololens 第一代上，不支持) 。</span><span class="sxs-lookup"><span data-stu-id="e2677-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="e2677-106">此技术的一些预期用例如下：</span><span class="sxs-lookup"><span data-stu-id="e2677-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="e2677-107">将对象置于特定类型的最近图面上 (例如墙壁和地面) </span><span class="sxs-lookup"><span data-stu-id="e2677-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="e2677-108">构造平台样式游戏的导航网格</span><span class="sxs-lookup"><span data-stu-id="e2677-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="e2677-109">提供物理引擎友好几何作为四边形</span><span class="sxs-lookup"><span data-stu-id="e2677-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="e2677-110">通过避免编写类似的算法来加速开发</span><span class="sxs-lookup"><span data-stu-id="e2677-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="e2677-111">从 MRTK 2.6 开始，场景理解作为 __实验__ 性功能提供。</span><span class="sxs-lookup"><span data-stu-id="e2677-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="e2677-112">它集成到 MRTK 中，作为名为的 [空间观察](spatial-awareness-getting-started.md#register-observers) 程序 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。</span><span class="sxs-lookup"><span data-stu-id="e2677-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="e2677-113">场景理解既适用于旧的 XR 管道，也适用于 XR SDK 管道。</span><span class="sxs-lookup"><span data-stu-id="e2677-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="e2677-114">在这两种情况下， `WindowsSceneUnderstandingObserver` 都使用。</span><span class="sxs-lookup"><span data-stu-id="e2677-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="e2677-115">观察程序概述</span><span class="sxs-lookup"><span data-stu-id="e2677-115">Observer overview</span></span>

<span data-ttu-id="e2677-116">当系统询问时， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 将返回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其属性对应用程序有用，以了解其环境。</span><span class="sxs-lookup"><span data-stu-id="e2677-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="e2677-117">观察频率、返回的对象类型 (例如墙壁、楼层) 和其他观察者行为取决于观察者通过配置文件的配置。</span><span class="sxs-lookup"><span data-stu-id="e2677-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="e2677-118">例如，如果需要封闭掩码，则必须将观察程序配置为生成四边形。</span><span class="sxs-lookup"><span data-stu-id="e2677-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="e2677-119">观察到的场景可以保存为序列化文件，稍后可以将其加载以便在编辑器播放模式下重新创建场景。</span><span class="sxs-lookup"><span data-stu-id="e2677-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="e2677-120">设置</span><span class="sxs-lookup"><span data-stu-id="e2677-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2677-121">仅在 HoloLens 2 和 Unity 2019.4 及更高版本上支持场景理解。</span><span class="sxs-lookup"><span data-stu-id="e2677-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="e2677-122">确保在生成设置中将平台设置为 UWP。</span><span class="sxs-lookup"><span data-stu-id="e2677-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="e2677-123">通过混合现实功能工具 [获取场景理解包](https://aka.ms/MRFeatureTool)。</span><span class="sxs-lookup"><span data-stu-id="e2677-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="e2677-124">使用场景理解</span><span class="sxs-lookup"><span data-stu-id="e2677-124">Using Scene Understanding</span></span>

<span data-ttu-id="e2677-125">开始使用场景理解的最快方法就是查看示例场景。</span><span class="sxs-lookup"><span data-stu-id="e2677-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="e2677-126">场景理解示例场景</span><span class="sxs-lookup"><span data-stu-id="e2677-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="e2677-127">在 Unity 中，使用项目资源管理器打开 中的场景文件 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` 并按 play！</span><span class="sxs-lookup"><span data-stu-id="e2677-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2677-128">使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。</span><span class="sxs-lookup"><span data-stu-id="e2677-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="e2677-129">有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。</span><span class="sxs-lookup"><span data-stu-id="e2677-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="e2677-130">场景演示了以下内容：</span><span class="sxs-lookup"><span data-stu-id="e2677-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="e2677-131">在应用程序 UI 中通过 可视化观察场景对象来配置观察程序</span><span class="sxs-lookup"><span data-stu-id="e2677-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="e2677-132">演示如何 `DemoSceneUnderstandingController` 更改观察者设置并侦听相关事件的示例脚本</span><span class="sxs-lookup"><span data-stu-id="e2677-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="e2677-133">将场景数据保存至设备进行脱机开发</span><span class="sxs-lookup"><span data-stu-id="e2677-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="e2677-134">将以前保存的场景数据 (.bytes 文件) 以支持编辑器内开发工作流</span><span class="sxs-lookup"><span data-stu-id="e2677-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="e2677-135">示例场景基于旧版 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="e2677-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="e2677-136">如果使用 XR SDK 管道，应相应地修改配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2677-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="e2677-137">提供的场景理解空间感知系统配置文件 () 和场景理解观察器配置文件 (`DemoSceneUnderstandingSystemProfile` `DefaultSceneUnderstandingObserverProfile` 和) `DemoSceneUnderstandingObserverProfile` 都适用于这两个管道。</span><span class="sxs-lookup"><span data-stu-id="e2677-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="e2677-138">配置观察程序服务</span><span class="sxs-lookup"><span data-stu-id="e2677-138">Configuring the observer service</span></span>

<span data-ttu-id="e2677-139">选择"MixedRealityToolkit"游戏对象并检查检查器。</span><span class="sxs-lookup"><span data-stu-id="e2677-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![场景了解层次结构中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![检查器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="e2677-142">这些选项允许配置 `WindowsSceneUnderstandingObserver` 。</span><span class="sxs-lookup"><span data-stu-id="e2677-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="e2677-143">示例脚本</span><span class="sxs-lookup"><span data-stu-id="e2677-143">Example script</span></span>

<span data-ttu-id="e2677-144">示例脚本 _DemoSceneUnderstandingController_ 演示了使用场景理解服务的主要概念。</span><span class="sxs-lookup"><span data-stu-id="e2677-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="e2677-145">订阅场景理解事件</span><span class="sxs-lookup"><span data-stu-id="e2677-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="e2677-146">处理场景理解事件</span><span class="sxs-lookup"><span data-stu-id="e2677-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="e2677-147">`WindowsSceneUnderstandingObserver`在运行时配置</span><span class="sxs-lookup"><span data-stu-id="e2677-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="e2677-148">屏幕上面板上的切换通过调用此示例脚本的公共函数，更改场景理解观察程序的行为。</span><span class="sxs-lookup"><span data-stu-id="e2677-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="e2677-149">打开 *实例化 prototyping*，将演示如何创建适合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小的对象，并在父对象下进行整齐收集。</span><span class="sxs-lookup"><span data-stu-id="e2677-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![演示控制器选项](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="e2677-151">生成的应用说明</span><span class="sxs-lookup"><span data-stu-id="e2677-151">Built app notes</span></span>

<span data-ttu-id="e2677-152">采用标准方式生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e2677-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="e2677-153">运行后，将出现一些按钮，这些按钮可用于功能。</span><span class="sxs-lookup"><span data-stu-id="e2677-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="e2677-154">请注意，有一些 pit 正在向观察者发出查询。</span><span class="sxs-lookup"><span data-stu-id="e2677-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="e2677-155">错误配置请求导致事件负载中不包含预期数据。</span><span class="sxs-lookup"><span data-stu-id="e2677-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="e2677-156">例如，如果一个没有请求四边形，则不会显示任何封闭掩码纹理。</span><span class="sxs-lookup"><span data-stu-id="e2677-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="e2677-157">类似地，如果未将观察者配置为请求网格，则不会显示世界网格。</span><span class="sxs-lookup"><span data-stu-id="e2677-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="e2677-158">此 `DemoSceneUnderstandingController` 脚本负责处理其中的某些依赖项，但并非全部。</span><span class="sxs-lookup"><span data-stu-id="e2677-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="e2677-159">可以通过中的 [设备门户](/windows/mixed-reality/using-the-windows-device-portal) 访问已保存的场景文件 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。</span><span class="sxs-lookup"><span data-stu-id="e2677-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="e2677-160">可以通过在 "检查器" 中找到的观察程序配置文件中指定这些场景文件，在编辑器中使用这些文件。</span><span class="sxs-lookup"><span data-stu-id="e2677-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![字节文件的设备门户位置](../images/spatial-awareness/BytesInDevicePortal.png)

![观察程序中的序列化场景字节](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="e2677-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2677-163">See Also</span></span>

* [<span data-ttu-id="e2677-164">空间映射概述 WMR</span><span class="sxs-lookup"><span data-stu-id="e2677-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="e2677-165">空间映射概述 WMR</span><span class="sxs-lookup"><span data-stu-id="e2677-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)