---
title: 场景系统场景类型
description: MRTK 中不同场景类型的文档
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144574"
---
# <a name="scene-types"></a><span data-ttu-id="b80af-104">场景类型</span><span class="sxs-lookup"><span data-stu-id="b80af-104">Scene types</span></span>

<span data-ttu-id="b80af-105">幕后分为三种类型，每种类型都具有不同的函数。</span><span class="sxs-lookup"><span data-stu-id="b80af-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![层次结构中的场景系统](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="b80af-107">内容场景</span><span class="sxs-lookup"><span data-stu-id="b80af-107">Content scenes</span></span>

<span data-ttu-id="b80af-108">这是你用来处理的场景。</span><span class="sxs-lookup"><span data-stu-id="b80af-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="b80af-109">可以在这些内容中存储任何类型的内容，也可以通过任何组合加载或卸载这些内容。</span><span class="sxs-lookup"><span data-stu-id="b80af-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="b80af-110">默认情况下，启用内容场景。</span><span class="sxs-lookup"><span data-stu-id="b80af-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="b80af-111">服务可以加载或卸载配置文件的数组中包含的任何场景 `Content Scenes` 。</span><span class="sxs-lookup"><span data-stu-id="b80af-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="b80af-112">管理器场景</span><span class="sxs-lookup"><span data-stu-id="b80af-112">Manager scenes</span></span>

<span data-ttu-id="b80af-113">一个场景，其中包含所需的 MixedRealityToolkit 实例。</span><span class="sxs-lookup"><span data-stu-id="b80af-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="b80af-114">此场景将首先在启动时加载，并将在应用程序的生存期内保持加载。</span><span class="sxs-lookup"><span data-stu-id="b80af-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="b80af-115">管理器场景还可以托管不应销毁的其他对象。</span><span class="sxs-lookup"><span data-stu-id="b80af-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="b80af-116">这是 DontDestroyOnLoad 的首选替代方法。</span><span class="sxs-lookup"><span data-stu-id="b80af-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="b80af-117">若要启用此功能，请签 `Use Manager Scene` 入您的配置文件，然后将场景对象拖入该 `Manager Scene` 字段。</span><span class="sxs-lookup"><span data-stu-id="b80af-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="b80af-118">照明场景</span><span class="sxs-lookup"><span data-stu-id="b80af-118">Lighting scenes</span></span>

<span data-ttu-id="b80af-119">一组用于存储光照信息和照明对象的场景。</span><span class="sxs-lookup"><span data-stu-id="b80af-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="b80af-120">一次只能加载一个，在平滑照明过渡期间，可以混合使用其设置。</span><span class="sxs-lookup"><span data-stu-id="b80af-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="b80af-121">使用加法加载时，Unity 的照明设置（环境光线、skyboxes 等）可能会很难管理，因为它们与单个场景相关，替代行为并不是很简单。</span><span class="sxs-lookup"><span data-stu-id="b80af-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="b80af-122">在实践中，如果在运行时未获得的照明条件中创作资产，这可能会导致混淆。</span><span class="sxs-lookup"><span data-stu-id="b80af-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![场景系统照明设置](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="b80af-124">场景系统使用照明场景来确保无论在编辑模式和播放模式下加载或激活哪些场景，这些设置都保持一致。</span><span class="sxs-lookup"><span data-stu-id="b80af-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="b80af-125">若要启用此功能， `Use Lighting Scene` 请检查配置文件并填充 `Lighting Scenes` 数组。</span><span class="sxs-lookup"><span data-stu-id="b80af-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="b80af-126">缓存照明设置</span><span class="sxs-lookup"><span data-stu-id="b80af-126">Cached lighting settings</span></span>

<span data-ttu-id="b80af-127">配置文件存储照明场景中保留的照明设置的缓存副本。</span><span class="sxs-lookup"><span data-stu-id="b80af-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="b80af-128">如果这些设置在照明场景中发生变化，则需要更新缓存，以确保照明在播放模式下如预期显示。</span><span class="sxs-lookup"><span data-stu-id="b80af-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="b80af-129">如果配置文件怀疑缓存的设置已过期，则会显示警告。</span><span class="sxs-lookup"><span data-stu-id="b80af-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="b80af-130">单击 `Update Cached Lighting Settings` 将加载每个照明场景，提取其设置，然后将这些设置存储在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="b80af-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![场景系统缓存照明设置](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="b80af-132">编辑器行为</span><span class="sxs-lookup"><span data-stu-id="b80af-132">Editor behavior</span></span>

<span data-ttu-id="b80af-133">使用照明场景的一个好处是知道内容在编辑时正确亮起。</span><span class="sxs-lookup"><span data-stu-id="b80af-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="b80af-134">为此，场景服务将始终加载照明场景，并且将场景的照明设置复制到当前活动场景。\*</span><span class="sxs-lookup"><span data-stu-id="b80af-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="b80af-135">可以通过打开场景系统的服务检查器来更改加载的照明 [场景。](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="b80af-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="b80af-136">在编辑模式下，可以在照明场景之间即时转换。</span><span class="sxs-lookup"><span data-stu-id="b80af-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="b80af-137">在播放模式下，可以预览转换。</span><span class="sxs-lookup"><span data-stu-id="b80af-137">In play mode, you can preview transitions.</span></span>

![场景系统检查器](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="b80af-139">\**注意：通常，活动场景确定编辑器中的照明设置。但是，我们选择不使用此功能来强制实施照明设置，因为活动场景也默认放置新创建的对象，并且只允许照明场景包含照明组件。相反，当前照明场景的设置会自动复制到活动场景的设置。请记住，这将导致内容场景的照明设置被过度写入。*</span><span class="sxs-lookup"><span data-stu-id="b80af-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
