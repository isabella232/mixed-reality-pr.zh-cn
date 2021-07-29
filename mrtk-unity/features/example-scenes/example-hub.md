---
title: MRTK 中心示例
description: MRTK 中的示例场景概述
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 2b7e1234ed79a99e826184e42c319f84582ff23a
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757046"
---
# <a name="mrtk-examples-hub"></a>MRTK 中心示例

![MRTK 中心示例](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK 示例中心是一个 Unity 场景，可轻松体验多个场景。 它使用 MRTK 的场景系统加载&场景。

**MRTKExamplesHub.unity** 是包含共享组件的容器场景，包括 ``MixedRealityToolkit`` 和 ``MixedRealityPlayspace`` 。 **MRTKExamplesHubMainMenu.unity** 场景具有立方体按钮。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 Microsoft Store HoloLens 2
如果有HoloLens 2，可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>先决条件

MRTK 示例中心使用 [场景转换服务](../extensions/scene-transition-service.md) 和相关脚本。 如果通过 Unity 包使用 MRTK，请导入 **Microsoft.MixedReality.Toolkit。Unity.Extensions.x.x.x.unitypackage，** 它是发布包 [的一部分](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)。 如果通过存储库克隆使用 MRTK，则项目中应已有 **MRTK/Extensions** 文件夹。

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub 场景和场景系统

打开 **MRTKExamplesHub.unity，** 位于它是一个空场景，具有 `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit、MixedRealityPlayspace 和 LoadHubOnStartup。 此场景配置为使用 MRTK 的场景系统。 单击 `MixedRealitySceneSystem` "MixedRealityToolkit"下。 它将在"检查器"面板中显示场景系统的信息。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

在检查器的底部，它显示"场景系统配置文件"中定义的场景列表。 可以单击场景名称来加载/卸载它们。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">通过单击列表中的场景名称加载 _MRTKExamplesHub_ 场景的示例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">加载 _HandInteractionExamples 场景_ 的示例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
加载多个场景的示例。

## <a name="running-the-scene"></a>运行场景

场景在 Unity 的游戏模式和设备上均有效。 在 Unity **编辑器中运行 MRTKExamplesHub** 场景，并使用 MRTK 的输入模拟与场景内容进行交互。 若要生成和部署，只需使用场景系统列表中包含的其他场景生成 **MRTKExamplesHub** 场景。 检查器还可轻松将场景添加到"生成"设置。 在"设置"中，确保 **MRTKExamplesHub** 场景位于列表顶部索引 0。

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>MRTKExamplesHub 如何加载场景

在 **MRTKExamplesHub** 场景中，可以找到 ``ExamplesHubButton`` 预制。
预制 **条中包含 FrontPlate** 对象 ``Interactable`` 。
使用 Interactable 的 和 事件，它会 ``OnClick()`` ``OnTouch()`` 触发 **LoadContentScene** 脚本的 **LoadContent ()** 函数。
在 **LoadContentScene** 脚本的检查器中，可以定义要加载的场景名称。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

该脚本使用场景系统的 LoadContent () 函数来加载场景。
有关更多详细信息，请参阅 [场景](../scene-system/scene-system-getting-started.md) 系统页。

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>返回到主菜单场景

若要返回到 MRTKExamplesHubMainMenu (主菜单场景) ，可以使用同一场景系统 `LoadContent()` 方法。 **ToggleFeaturesPanelExamplesHub.prefab** 提供包含 **LoadContentScene** 脚本的"主页"按钮。 使用此预制组件或在每个场景中提供自定义主页按钮，允许用户返回到主场景。 可以将 **ToggleFeaturesPanelExamplesHub.prefab** 放在 **MRTKExamplesHub** 场景中，使其始终可见，因为 **MRTKExamplesHub** 是共享容器场景。 请确保在每个示例场景中隐藏/停用 **ToggleFeaturesPanel.prefab。**

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>添加其他按钮

在 **CubeCollection** 对象中，重复 (或) _ExampleHubButton_ 预制件，然后单击 中的" **更新** 集合 `GridObjectCollection` "。
这将基于新的按钮总数更新柱面布局。
有关更多详细信息，请参阅 [对象](../ux-building-blocks/object-collection.md) 集合页。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

添加按钮后，更新 **LoadContentScene** 脚本中的场景名称 (上述) 。
向场景系统的配置文件添加其他场景。
