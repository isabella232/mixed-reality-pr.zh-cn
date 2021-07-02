---
title: 场景系统入门
description: 具有 MRTK 的场景系统的登陆页面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177568"
---
# <a name="scene-system-getting-started"></a><span data-ttu-id="2acf4-104">场景系统入门</span><span class="sxs-lookup"><span data-stu-id="2acf4-104">Scene system getting started</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="2acf4-105">何时使用场景系统</span><span class="sxs-lookup"><span data-stu-id="2acf4-105">When to use the scene system</span></span>

<span data-ttu-id="2acf4-106">如果你的项目包含单个场景，则场景系统可能不是必需的。</span><span class="sxs-lookup"><span data-stu-id="2acf4-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="2acf4-107">如果满足下列一项或多项条件，它最有用：</span><span class="sxs-lookup"><span data-stu-id="2acf4-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="2acf4-108">你的项目具有多个场景。</span><span class="sxs-lookup"><span data-stu-id="2acf4-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="2acf4-109">使用单个场景加载，但不喜欢销毁 MixedRealityToolkit 实例的方式。</span><span class="sxs-lookup"><span data-stu-id="2acf4-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="2acf4-110">你需要一种简单的方法来添加性地加载多个场景以构建你的体验。</span><span class="sxs-lookup"><span data-stu-id="2acf4-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="2acf4-111">你需要一种简单的方法来跟踪正在进行的负载操作，或使用一种简单的方法来控制同时加载的多个场景的场景激活。</span><span class="sxs-lookup"><span data-stu-id="2acf4-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="2acf4-112">希望在所有场景中保持一致且可预测。</span><span class="sxs-lookup"><span data-stu-id="2acf4-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="2acf4-113">场景系统资源</span><span class="sxs-lookup"><span data-stu-id="2acf4-113">Scene System Resources</span></span>

<span data-ttu-id="2acf4-114">默认情况下，场景系统利用一对场景对象)  (DefaultManagerScene 和 DefaultLighting 场景。</span><span class="sxs-lookup"><span data-stu-id="2acf4-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="2acf4-115">如果无法找到其中的任何一种情况，则会在场景系统配置检查器中出现一条消息。</span><span class="sxs-lookup"><span data-stu-id="2acf4-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![默认资源消息](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="2acf4-117">!纪录如果项目使用的是自定义管理器和照明场景，则可以安全地忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="2acf4-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="2acf4-118">以下部分介绍了如何根据使用哪种方法导入混合现实 Toolkit 来解决此消息。</span><span class="sxs-lookup"><span data-stu-id="2acf4-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="2acf4-119">Unity 程序包管理器 (UPM) </span><span class="sxs-lookup"><span data-stu-id="2acf4-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="2acf4-120">在混合现实 Toolkit UPM 包中，场景系统资源打包为示例。</span><span class="sxs-lookup"><span data-stu-id="2acf4-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="2acf4-121">由于 UPM 包是不可变的，因此 Unity 无法打开必要的场景文件，除非显式将其导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="2acf4-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="2acf4-122">若要导入，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2acf4-122">To import use the following steps:</span></span>

- <span data-ttu-id="2acf4-123">选择 **窗口**  >  **程序包管理器**</span><span class="sxs-lookup"><span data-stu-id="2acf4-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="2acf4-124">选择 **混合现实 Toolkit 基础**</span><span class="sxs-lookup"><span data-stu-id="2acf4-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="2acf4-125">在 "**示例**" 部分找到 **场景系统资源**</span><span class="sxs-lookup"><span data-stu-id="2acf4-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![导入场景系统资源](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="2acf4-127">选择 **导入**</span><span class="sxs-lookup"><span data-stu-id="2acf4-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="2acf4-128">资产 ( unitypackage) 文件</span><span class="sxs-lookup"><span data-stu-id="2acf4-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="2acf4-129">如果 SceneSystemResources 文件夹已删除，或在导入过程中被取消选择，则可以使用以下步骤进行恢复：</span><span class="sxs-lookup"><span data-stu-id="2acf4-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="2acf4-130">选择 **资产**  >  **导入包**  >  **自定义包**</span><span class="sxs-lookup"><span data-stu-id="2acf4-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="2acf4-131">打开 **MixedReality。 Toolkit。Foundation** 包</span><span class="sxs-lookup"><span data-stu-id="2acf4-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="2acf4-132">确保已选择 " **服务/SceneSystem/SceneSystemResources** " 和 "所有子选项"</span><span class="sxs-lookup"><span data-stu-id="2acf4-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![重新导入场景系统资源](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="2acf4-134">选择 **导入**</span><span class="sxs-lookup"><span data-stu-id="2acf4-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="2acf4-135">如何使用场景系统</span><span class="sxs-lookup"><span data-stu-id="2acf4-135">How to use the scene system</span></span>

- [<span data-ttu-id="2acf4-136">场景类型</span><span class="sxs-lookup"><span data-stu-id="2acf4-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="2acf4-137">内容场景加载</span><span class="sxs-lookup"><span data-stu-id="2acf4-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="2acf4-138">监视内容加载</span><span class="sxs-lookup"><span data-stu-id="2acf4-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="2acf4-139">照明场景加载</span><span class="sxs-lookup"><span data-stu-id="2acf4-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="2acf4-140">编辑器设置</span><span class="sxs-lookup"><span data-stu-id="2acf4-140">Editor settings</span></span>

<span data-ttu-id="2acf4-141">默认情况下，场景系统在 Unity 编辑器中强制执行多个行为。</span><span class="sxs-lookup"><span data-stu-id="2acf4-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="2acf4-142">如果你发现这些行为中的任何一种，可以在场景系统配置文件的 "**编辑器设置**" 部分中禁用。</span><span class="sxs-lookup"><span data-stu-id="2acf4-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="2acf4-143">`Editor Manage Build Settings:` 如果为 true，则服务将自动更新生成设置，确保添加所有管理器、照明和内容场景。</span><span class="sxs-lookup"><span data-stu-id="2acf4-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="2acf4-144">如果希望完全控制生成设置，请禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="2acf4-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="2acf4-145">`Editor Enforce Scene Order:` 如果为 true，则服务将确保管理器场景首先显示在场景层次结构中，后跟光照和内容。</span><span class="sxs-lookup"><span data-stu-id="2acf4-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="2acf4-146">如果需要对场景层次结构进行总体控制，请禁用此选择。</span><span class="sxs-lookup"><span data-stu-id="2acf4-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="2acf4-147">`Editor Manage Loaded Scenes:` 如果为 true，则服务将确保始终加载管理器、内容和照明场景。</span><span class="sxs-lookup"><span data-stu-id="2acf4-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="2acf4-148">如果希望在编辑器中加载哪些场景的总体控制，请禁用。</span><span class="sxs-lookup"><span data-stu-id="2acf4-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="2acf4-149">`Editor Enforce Lighting Scene Types:` 如果为 true，则该服务将确保在 `PermittedLightingSceneComponentTypes` 光照场景中只允许使用在中定义的照明相关组件。</span><span class="sxs-lookup"><span data-stu-id="2acf4-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="2acf4-150">如果希望完全控制照明场景的内容，请禁用。</span><span class="sxs-lookup"><span data-stu-id="2acf4-150">Disable if you want total control over the content of lighting scenes.</span></span>

![场景系统编辑器设置](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
