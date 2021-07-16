---
title: MRTK 中心示例
description: MRTK 中的示例场景概述
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282009"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="1e150-104">MRTK 中心示例</span><span class="sxs-lookup"><span data-stu-id="1e150-104">MRTK Examples Hub</span></span>

![MRTK 中心示例](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="1e150-106">MRTK 示例中心是一个 Unity 场景，可让你轻松地体验多个场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="1e150-107">它使用 MRTK 的场景系统加载 & 卸载场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="1e150-108">**MRTKExamplesHub** 是容器场景，其中包含和的共享组件 ``MixedRealityToolkit`` ``MixedRealityPlayspace`` 。</span><span class="sxs-lookup"><span data-stu-id="1e150-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="1e150-109">**MRTKExamplesHubMainMenu** 场景有多维数据集按钮。</span><span class="sxs-lookup"><span data-stu-id="1e150-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="1e150-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="1e150-110">Prerequisite</span></span>

<span data-ttu-id="1e150-111">MRTK 示例中心使用 [场景转换服务](../extensions/scene-transition-service.md) 和相关脚本。</span><span class="sxs-lookup"><span data-stu-id="1e150-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="1e150-112">如果通过 Unity 包使用 MRTK，请导入 **MixedReality. Toolkit。Unitypackage** 是 [发布包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)的一部分的 Unity. x. x. x. x. x. x. x. x。</span><span class="sxs-lookup"><span data-stu-id="1e150-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="1e150-113">如果通过存储库克隆使用 MRTK，则项目中应该已有 **MRTK/Extensions** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1e150-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="1e150-114">MRTKExamplesHub 场景和场景系统</span><span class="sxs-lookup"><span data-stu-id="1e150-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="1e150-115">打开 **MRTKExamplesHub** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` ，它是 MixedRealityToolkit、MixedRealityPlayspace 和 LoadHubOnStartup 为空的场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="1e150-116">此场景配置为使用 MRTK 的场景系统。</span><span class="sxs-lookup"><span data-stu-id="1e150-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="1e150-117">单击 `MixedRealitySceneSystem` "MixedRealityToolkit" 下。</span><span class="sxs-lookup"><span data-stu-id="1e150-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="1e150-118">它将在 "检查器" 面板中显示场景系统的信息。</span><span class="sxs-lookup"><span data-stu-id="1e150-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="1e150-119">在检查器的底部，它显示在场景系统配置文件中定义的场景的列表。</span><span class="sxs-lookup"><span data-stu-id="1e150-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="1e150-120">您可以单击场景名称来加载/卸载它们。</span><span class="sxs-lookup"><span data-stu-id="1e150-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="1e150-121">通过单击列表中的场景名称加载 _MRTKExamplesHub_ 场景的示例。</span><span class="sxs-lookup"><span data-stu-id="1e150-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="1e150-122">加载 _HandInteractionExamples_ 场景的示例。</span><span class="sxs-lookup"><span data-stu-id="1e150-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="1e150-123">加载多个场景的示例。</span><span class="sxs-lookup"><span data-stu-id="1e150-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="1e150-124">运行场景</span><span class="sxs-lookup"><span data-stu-id="1e150-124">Running the scene</span></span>

<span data-ttu-id="1e150-125">场景在 Unity 的游戏模式和设备上都有效。</span><span class="sxs-lookup"><span data-stu-id="1e150-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="1e150-126">在 Unity 编辑器中运行 **MRTKExamplesHub** 场景，并使用 MRTK 的输入模拟来与场景内容交互。</span><span class="sxs-lookup"><span data-stu-id="1e150-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="1e150-127">若要生成和部署，只需生成包含在场景系统列表中的其他场景的 **MRTKExamplesHub** 场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="1e150-128">该检查器还可以轻松地向生成设置中添加场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="1e150-129">在 "生成设置" 中，确保 **MRTKExamplesHub** 场景位于索引0处列表的顶部。</span><span class="sxs-lookup"><span data-stu-id="1e150-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="1e150-130">MRTKExamplesHub 如何加载场景</span><span class="sxs-lookup"><span data-stu-id="1e150-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="1e150-131">在 **MRTKExamplesHub** 场景中，可以找到 ``ExamplesHubButton`` prefab。</span><span class="sxs-lookup"><span data-stu-id="1e150-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="1e150-132">Prefab 中有一个 **FrontPlate** 对象，其中包含 ``Interactable`` 。</span><span class="sxs-lookup"><span data-stu-id="1e150-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="1e150-133">使用种不可交互的 ``OnClick()`` 和 ``OnTouch()`` 事件，将触发 **LoadContentScene** 脚本的 **LoadContent ()** 函数。</span><span class="sxs-lookup"><span data-stu-id="1e150-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="1e150-134">在 **LoadContentScene** 脚本的检查器中，可以定义要加载的场景名称。</span><span class="sxs-lookup"><span data-stu-id="1e150-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="1e150-135">脚本使用场景系统的 LoadContent () 函数加载场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="1e150-136">有关更多详细信息，请参阅 [场景系统](../scene-system/scene-system-getting-started.md) 页面。</span><span class="sxs-lookup"><span data-stu-id="1e150-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="1e150-137">返回到主菜单场景</span><span class="sxs-lookup"><span data-stu-id="1e150-137">Returning to the main menu scene</span></span>

<span data-ttu-id="1e150-138">若要返回到主菜单场景 (MRTKExamplesHubMainMenu 场景) ，可以使用相同的场景系统 `LoadContent()` 方法。</span><span class="sxs-lookup"><span data-stu-id="1e150-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="1e150-139">**ToggleFeaturesPanelExamplesHub. prefab** 提供了包含 **LoadContentScene** 脚本的 "主页" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1e150-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="1e150-140">使用此 prefab，或在每个场景中提供自定义主页按钮，以允许用户返回到主场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="1e150-141">可以在 **MRTKExamplesHub** 场景中放置 **ToggleFeaturesPanelExamplesHub** ，以使其始终可见，因为 **MRTKExamplesHub** 是共享容器场景。</span><span class="sxs-lookup"><span data-stu-id="1e150-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="1e150-142">请确保在每个示例场景中隐藏/停用 **ToggleFeaturesPanel prefab** 。</span><span class="sxs-lookup"><span data-stu-id="1e150-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="1e150-143">添加其他按钮</span><span class="sxs-lookup"><span data-stu-id="1e150-143">Adding additional buttons</span></span>

<span data-ttu-id="1e150-144">在 **CubeCollection** 对象中，重复 (或添加) _ExampleHubButton_ prototyping，然后单击 " **更新集合** " `GridObjectCollection` 。</span><span class="sxs-lookup"><span data-stu-id="1e150-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="1e150-145">这会基于新的按钮总数更新柱面布局。</span><span class="sxs-lookup"><span data-stu-id="1e150-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="1e150-146">有关更多详细信息，请参阅 [对象集合](../ux-building-blocks/object-collection.md) 页。</span><span class="sxs-lookup"><span data-stu-id="1e150-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="1e150-147">添加按钮后，请更新 **LoadContentScene** 脚本中的场景名称， (以上) 所述。</span><span class="sxs-lookup"><span data-stu-id="1e150-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="1e150-148">将其他场景添加到场景系统配置文件。</span><span class="sxs-lookup"><span data-stu-id="1e150-148">Add additional scenes to the Scene System's profile.</span></span>
