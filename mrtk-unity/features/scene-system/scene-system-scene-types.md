---
title: 场景系统场景类型
description: 有关 MRTK 中不同场景类型的文档
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: be34110c693c749535f6bfcd0411ecbd0bafc3bb48ab2392b3635c2e86a4dfb1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203305"
---
# <a name="scene-types"></a>场景类型

场景分为三种类型，每种类型具有不同的函数。

![层次结构中的场景系统](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>内容场景

这些是用于处理的场景。 任何类型的内容都可以存储在其中，并且可以任意组合进行加载或卸载。

默认启用内容场景。 服务可以加载/卸载配置文件数组 `Content Scenes` 中包含的任何场景。

___

## <a name="manager-scenes"></a>管理器场景

具有所需 MixedRealityToolkit 实例的单个场景。 此场景将在启动时首先加载，在应用生存期内将保持加载状态。 管理器场景还可以托管不应销毁的其他对象。 这是 DontDestroyOnLoad 的首选替代方法。

若要启用此功能， `Use Manager Scene` 请检查配置文件并将场景对象拖动到 `Manager Scene` 字段中。

___

## <a name="lighting-scenes"></a>照明场景

一组场景，用于存储照明信息和照明对象。 一次只能加载一个，其设置可以在负载期间混合，实现平滑照明转换。

Unity 的照明设置（环境光、天盒等）在使用加法加载时可能难以管理，因为它们与单个场景关联，重写行为并不简单。 在实践中，当资产在无法在运行时获取的照明条件下创作时，这可能会导致混淆。

![场景系统照明设置](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

场景系统使用照明场景来确保无论在编辑模式和播放模式下加载或激活哪些场景，这些设置都保持一致。

若要启用此功能， `Use Lighting Scene` 请检查配置文件并填充 `Lighting Scenes` 数组。

### <a name="cached-lighting-settings"></a>缓存照明设置

配置文件存储照明场景中保留的照明设置的缓存副本。 如果这些设置在照明场景中发生变化，则需要更新缓存，以确保照明在播放模式下如预期显示。 如果配置文件怀疑缓存的设置已过期，则会显示警告。 单击 `Update Cached Lighting Settings` 将加载每个照明场景，提取其设置，然后将这些设置存储在配置文件中。

![场景系统缓存照明设置](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>编辑器行为

使用照明场景的一个好处是知道内容在编辑时正确亮起。 为此，场景服务将始终加载照明场景，并且将场景的照明设置复制到当前活动场景。\*

可以通过打开场景系统的服务检查器来更改加载的照明 [场景。](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 在编辑模式下，可以在照明场景之间即时转换。 在播放模式下，可以预览转换。

![场景系统检查器](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**注意：通常，活动场景确定编辑器中的照明设置。但是，我们选择不使用此功能来强制实施照明设置，因为活动场景也默认放置新创建的对象，并且只允许照明场景包含照明组件。相反，当前照明场景的设置会自动复制到活动场景的设置。请记住，这将导致内容场景的照明设置被过度写入。*
