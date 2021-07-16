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
# <a name="mrtk-examples-hub"></a>MRTK 中心示例

![MRTK 中心示例](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK 示例中心是一个 Unity 场景，可让你轻松地体验多个场景。 它使用 MRTK 的场景系统加载 & 卸载场景。

**MRTKExamplesHub** 是容器场景，其中包含和的共享组件 ``MixedRealityToolkit`` ``MixedRealityPlayspace`` 。 **MRTKExamplesHubMainMenu** 场景有多维数据集按钮。

## <a name="prerequisite"></a>先决条件

MRTK 示例中心使用 [场景转换服务](../extensions/scene-transition-service.md) 和相关脚本。 如果通过 Unity 包使用 MRTK，请导入 **MixedReality. Toolkit。Unitypackage** 是 [发布包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)的一部分的 Unity. x. x. x. x. x. x. x. x。 如果通过存储库克隆使用 MRTK，则项目中应该已有 **MRTK/Extensions** 文件夹。

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub 场景和场景系统

打开 **MRTKExamplesHub** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` ，它是 MixedRealityToolkit、MixedRealityPlayspace 和 LoadHubOnStartup 为空的场景。 此场景配置为使用 MRTK 的场景系统。 单击 `MixedRealitySceneSystem` "MixedRealityToolkit" 下。 它将在 "检查器" 面板中显示场景系统的信息。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

在检查器的底部，它显示在场景系统配置文件中定义的场景的列表。 您可以单击场景名称来加载/卸载它们。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">通过单击列表中的场景名称加载 _MRTKExamplesHub_ 场景的示例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">加载 _HandInteractionExamples_ 场景的示例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
加载多个场景的示例。

## <a name="running-the-scene"></a>运行场景

场景在 Unity 的游戏模式和设备上都有效。 在 Unity 编辑器中运行 **MRTKExamplesHub** 场景，并使用 MRTK 的输入模拟来与场景内容交互。 若要生成和部署，只需生成包含在场景系统列表中的其他场景的 **MRTKExamplesHub** 场景。 该检查器还可以轻松地向生成设置中添加场景。 在 "生成设置" 中，确保 **MRTKExamplesHub** 场景位于索引0处列表的顶部。

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>MRTKExamplesHub 如何加载场景

在 **MRTKExamplesHub** 场景中，可以找到 ``ExamplesHubButton`` prefab。
Prefab 中有一个 **FrontPlate** 对象，其中包含 ``Interactable`` 。
使用种不可交互的 ``OnClick()`` 和 ``OnTouch()`` 事件，将触发 **LoadContentScene** 脚本的 **LoadContent ()** 函数。
在 **LoadContentScene** 脚本的检查器中，可以定义要加载的场景名称。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

脚本使用场景系统的 LoadContent () 函数加载场景。
有关更多详细信息，请参阅 [场景系统](../scene-system/scene-system-getting-started.md) 页面。

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>返回到主菜单场景

若要返回到主菜单场景 (MRTKExamplesHubMainMenu 场景) ，可以使用相同的场景系统 `LoadContent()` 方法。 **ToggleFeaturesPanelExamplesHub. prefab** 提供了包含 **LoadContentScene** 脚本的 "主页" 按钮。 使用此 prefab，或在每个场景中提供自定义主页按钮，以允许用户返回到主场景。 可以在 **MRTKExamplesHub** 场景中放置 **ToggleFeaturesPanelExamplesHub** ，以使其始终可见，因为 **MRTKExamplesHub** 是共享容器场景。 请确保在每个示例场景中隐藏/停用 **ToggleFeaturesPanel prefab** 。

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>添加其他按钮

在 **CubeCollection** 对象中，重复 (或添加) _ExampleHubButton_ prototyping，然后单击 " **更新集合** " `GridObjectCollection` 。
这会基于新的按钮总数更新柱面布局。
有关更多详细信息，请参阅 [对象集合](../ux-building-blocks/object-collection.md) 页。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

添加按钮后，请更新 **LoadContentScene** 脚本中的场景名称， (以上) 所述。
将其他场景添加到场景系统配置文件。
