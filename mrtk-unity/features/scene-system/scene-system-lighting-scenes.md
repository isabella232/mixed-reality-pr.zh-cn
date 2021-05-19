---
title: 场景系统照明场景
description: 有关场景中的照明的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144412"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="18e55-104">光照场景操作</span><span class="sxs-lookup"><span data-stu-id="18e55-104">Lighting scene operations</span></span>

<span data-ttu-id="18e55-105">在启动时加载配置文件中定义的默认照明场景。</span><span class="sxs-lookup"><span data-stu-id="18e55-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="18e55-106">在调用之前，该照明场景将保持加载状态 `SetLightingScene` 。</span><span class="sxs-lookup"><span data-stu-id="18e55-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="18e55-107">照明设置转换</span><span class="sxs-lookup"><span data-stu-id="18e55-107">Lighting setting transitions</span></span>

<span data-ttu-id="18e55-108">`transitionType` 控制过渡到新光源场景的样式。</span><span class="sxs-lookup"><span data-stu-id="18e55-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="18e55-109">可用样式包括：</span><span class="sxs-lookup"><span data-stu-id="18e55-109">The available styles are:</span></span>

<span data-ttu-id="18e55-110">类型</span><span class="sxs-lookup"><span data-stu-id="18e55-110">Type</span></span> | <span data-ttu-id="18e55-111">说明</span><span class="sxs-lookup"><span data-stu-id="18e55-111">Description</span></span> | <span data-ttu-id="18e55-112">持续时间</span><span class="sxs-lookup"><span data-stu-id="18e55-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="18e55-113">无</span><span class="sxs-lookup"><span data-stu-id="18e55-113">None</span></span> | <span data-ttu-id="18e55-114">上一个光照场景已卸载，将加载新的照明场景。</span><span class="sxs-lookup"><span data-stu-id="18e55-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="18e55-115">无转换。</span><span class="sxs-lookup"><span data-stu-id="18e55-115">No transition.</span></span> | <span data-ttu-id="18e55-116">忽略</span><span class="sxs-lookup"><span data-stu-id="18e55-116">Ignored</span></span>
<span data-ttu-id="18e55-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="18e55-117">FadeToBlack</span></span> | <span data-ttu-id="18e55-118">上一个光照场景淡出为黑色。</span><span class="sxs-lookup"><span data-stu-id="18e55-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="18e55-119">加载新的照明场景，然后从黑色上褪色。</span><span class="sxs-lookup"><span data-stu-id="18e55-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="18e55-120">适用于位置间的平滑转换。</span><span class="sxs-lookup"><span data-stu-id="18e55-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="18e55-121">已使用</span><span class="sxs-lookup"><span data-stu-id="18e55-121">Used</span></span>
<span data-ttu-id="18e55-122">CrossFade</span><span class="sxs-lookup"><span data-stu-id="18e55-122">CrossFade</span></span> | <span data-ttu-id="18e55-123">当新的照明场景淡入时，上一个光照场景将淡出。</span><span class="sxs-lookup"><span data-stu-id="18e55-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="18e55-124">对于同一位置的照明设置之间的平滑转换很有用。</span><span class="sxs-lookup"><span data-stu-id="18e55-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="18e55-125">已使用</span><span class="sxs-lookup"><span data-stu-id="18e55-125">Used</span></span>

<span data-ttu-id="18e55-126">请注意，在转换过程中不能插值某些照明设置。</span><span class="sxs-lookup"><span data-stu-id="18e55-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="18e55-127">如果希望平滑视觉对象的转换，这些设置必须保持一致。</span><span class="sxs-lookup"><span data-stu-id="18e55-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="18e55-128">设置</span><span class="sxs-lookup"><span data-stu-id="18e55-128">Setting</span></span> | <span data-ttu-id="18e55-129">平滑 FadeToBlack 转换</span><span class="sxs-lookup"><span data-stu-id="18e55-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="18e55-130">平滑 CrossFade 转换</span><span class="sxs-lookup"><span data-stu-id="18e55-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="18e55-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="18e55-131">Skybox</span></span> | <span data-ttu-id="18e55-132">否</span><span class="sxs-lookup"><span data-stu-id="18e55-132">No</span></span> | <span data-ttu-id="18e55-133">否</span><span class="sxs-lookup"><span data-stu-id="18e55-133">No</span></span>
<span data-ttu-id="18e55-134">自定义反射</span><span class="sxs-lookup"><span data-stu-id="18e55-134">Custom Reflections</span></span> | <span data-ttu-id="18e55-135">否</span><span class="sxs-lookup"><span data-stu-id="18e55-135">No</span></span> | <span data-ttu-id="18e55-136">否</span><span class="sxs-lookup"><span data-stu-id="18e55-136">No</span></span>
<span data-ttu-id="18e55-137">浅色实时阴影</span><span class="sxs-lookup"><span data-stu-id="18e55-137">Sun light realtime shadows</span></span> | <span data-ttu-id="18e55-138">是</span><span class="sxs-lookup"><span data-stu-id="18e55-138">Yes</span></span> | <span data-ttu-id="18e55-139">否</span><span class="sxs-lookup"><span data-stu-id="18e55-139">No</span></span>
