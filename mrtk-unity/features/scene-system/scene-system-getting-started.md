---
title: 场景系统入门
description: 使用 MRTK 的场景系统的登陆页
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144301"
---
# <a name="scene-system-overview"></a><span data-ttu-id="1577b-104">场景系统概述</span><span class="sxs-lookup"><span data-stu-id="1577b-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="1577b-105">何时使用场景系统</span><span class="sxs-lookup"><span data-stu-id="1577b-105">When to use the scene system</span></span>

<span data-ttu-id="1577b-106">如果项目由单个场景组成，则场景系统可能不需要。</span><span class="sxs-lookup"><span data-stu-id="1577b-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="1577b-107">当以下一个或多个情况成立时，它最有用：</span><span class="sxs-lookup"><span data-stu-id="1577b-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="1577b-108">项目有多个场景。</span><span class="sxs-lookup"><span data-stu-id="1577b-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="1577b-109">你习惯单场景加载，但不喜欢它破坏 MixedRealityToolkit 实例的方式。</span><span class="sxs-lookup"><span data-stu-id="1577b-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="1577b-110">你需要一种简单的方式来附加加载多个场景来构造体验。</span><span class="sxs-lookup"><span data-stu-id="1577b-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="1577b-111">你需要一种简单的方式来跟踪正在进行中的加载操作，或者一种控制同时加载多个场景的场景激活的简单方法。</span><span class="sxs-lookup"><span data-stu-id="1577b-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="1577b-112">你想要在所有场景中保持照明一致且可预测。</span><span class="sxs-lookup"><span data-stu-id="1577b-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="1577b-113">场景系统资源</span><span class="sxs-lookup"><span data-stu-id="1577b-113">Scene System Resources</span></span>

<span data-ttu-id="1577b-114">默认情况下，场景系统使用 DefaultManagerScene 和 DefaultLighting 场景 (一对场景) 。</span><span class="sxs-lookup"><span data-stu-id="1577b-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="1577b-115">如果找不到其中任一场景，则"场景系统配置文件检查器"中将显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="1577b-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![默认资源消息](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="1577b-117">![注意]如果项目使用自定义管理器和照明场景，可以放心忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="1577b-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="1577b-118">以下各节现在介绍了如何根据用于导入混合现实工具包的方法来解析此消息。</span><span class="sxs-lookup"><span data-stu-id="1577b-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="1577b-119">Unity 程序包管理器 (UPM) </span><span class="sxs-lookup"><span data-stu-id="1577b-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="1577b-120">在混合现实工具包 UPM 包中，场景系统资源打包为示例。</span><span class="sxs-lookup"><span data-stu-id="1577b-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="1577b-121">由于 UPM 包不可变，Unity 无法打开必要的场景文件，除非将其显式导入项目中。</span><span class="sxs-lookup"><span data-stu-id="1577b-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="1577b-122">若要导入，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1577b-122">To import use the following steps:</span></span>

- <span data-ttu-id="1577b-123">选择 **窗口**  >  **包管理器**</span><span class="sxs-lookup"><span data-stu-id="1577b-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="1577b-124">选择 **混合现实工具包 Foundation**</span><span class="sxs-lookup"><span data-stu-id="1577b-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="1577b-125">在 "**示例**" 部分找到 **场景系统资源**</span><span class="sxs-lookup"><span data-stu-id="1577b-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![导入场景系统资源](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="1577b-127">选择 **导入**</span><span class="sxs-lookup"><span data-stu-id="1577b-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="1577b-128">资产 ( unitypackage) 文件</span><span class="sxs-lookup"><span data-stu-id="1577b-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="1577b-129">如果 SceneSystemResources 文件夹已删除，或在导入过程中被取消选择，则可以使用以下步骤进行恢复：</span><span class="sxs-lookup"><span data-stu-id="1577b-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="1577b-130">选择 **资产**  >  **导入包**  >  **自定义包**</span><span class="sxs-lookup"><span data-stu-id="1577b-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="1577b-131">打开 **MixedReality 包。**</span><span class="sxs-lookup"><span data-stu-id="1577b-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="1577b-132">确保已选择 " **服务/SceneSystem/SceneSystemResources** " 和 "所有子选项"</span><span class="sxs-lookup"><span data-stu-id="1577b-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![重新导入场景系统资源](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="1577b-134">选择 **导入**</span><span class="sxs-lookup"><span data-stu-id="1577b-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="1577b-135">如何使用场景系统</span><span class="sxs-lookup"><span data-stu-id="1577b-135">How to use the scene system</span></span>

- [<span data-ttu-id="1577b-136">场景类型</span><span class="sxs-lookup"><span data-stu-id="1577b-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="1577b-137">内容场景加载</span><span class="sxs-lookup"><span data-stu-id="1577b-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="1577b-138">监视内容加载</span><span class="sxs-lookup"><span data-stu-id="1577b-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="1577b-139">照明场景加载</span><span class="sxs-lookup"><span data-stu-id="1577b-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="1577b-140">编辑器设置</span><span class="sxs-lookup"><span data-stu-id="1577b-140">Editor settings</span></span>

<span data-ttu-id="1577b-141">默认情况下，场景系统在 Unity 编辑器中强制执行多个行为。</span><span class="sxs-lookup"><span data-stu-id="1577b-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="1577b-142">如果你发现这些行为中的任何一种，可以在场景系统配置文件的 " **编辑器设置** " 部分中禁用。</span><span class="sxs-lookup"><span data-stu-id="1577b-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="1577b-143">`Editor Manage Build Settings:` 如果为 true，则服务将自动更新生成设置，确保添加所有管理器、照明和内容场景。</span><span class="sxs-lookup"><span data-stu-id="1577b-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="1577b-144">如果希望完全控制生成设置，请禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="1577b-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="1577b-145">`Editor Enforce Scene Order:` 如果为 true，则服务将确保管理器场景首先显示在场景层次结构中，后跟光照和内容。</span><span class="sxs-lookup"><span data-stu-id="1577b-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="1577b-146">如果需要对场景层次结构进行总体控制，请禁用此选择。</span><span class="sxs-lookup"><span data-stu-id="1577b-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="1577b-147">`Editor Manage Loaded Scenes:` 如果为 true，则服务将确保始终加载管理器、内容和照明场景。</span><span class="sxs-lookup"><span data-stu-id="1577b-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="1577b-148">如果希望在编辑器中加载哪些场景的总体控制，请禁用。</span><span class="sxs-lookup"><span data-stu-id="1577b-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="1577b-149">`Editor Enforce Lighting Scene Types:` 如果为 true，则该服务将确保在 `PermittedLightingSceneComponentTypes` 光照场景中只允许使用在中定义的照明相关组件。</span><span class="sxs-lookup"><span data-stu-id="1577b-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="1577b-150">如果希望完全控制照明场景的内容，请禁用。</span><span class="sxs-lookup"><span data-stu-id="1577b-150">Disable if you want total control over the content of lighting scenes.</span></span>

![场景系统编辑器设置](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
