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
# <a name="scene-system-getting-started"></a>场景系统入门

## <a name="when-to-use-the-scene-system"></a>何时使用场景系统

如果你的项目包含单个场景，则场景系统可能不是必需的。 如果满足下列一项或多项条件，它最有用：

- 你的项目具有多个场景。
- 使用单个场景加载，但不喜欢销毁 MixedRealityToolkit 实例的方式。
- 你需要一种简单的方法来添加性地加载多个场景以构建你的体验。
- 你需要一种简单的方法来跟踪正在进行的负载操作，或使用一种简单的方法来控制同时加载的多个场景的场景激活。
- 希望在所有场景中保持一致且可预测。

## <a name="scene-system-resources"></a>场景系统资源

默认情况下，场景系统利用一对场景对象)  (DefaultManagerScene 和 DefaultLighting 场景。 如果无法找到其中的任何一种情况，则会在场景系统配置检查器中出现一条消息。

![默认资源消息](../images/scene-system/DefaultResourcesMessage.png)

>!纪录如果项目使用的是自定义管理器和照明场景，则可以安全地忽略此消息。

以下部分介绍了如何根据使用哪种方法导入混合现实 Toolkit 来解决此消息。

### <a name="unity-package-manager-upm"></a>Unity 程序包管理器 (UPM) 

在混合现实 Toolkit UPM 包中，场景系统资源打包为示例。 由于 UPM 包是不可变的，因此 Unity 无法打开必要的场景文件，除非显式将其导入到项目中。

若要导入，请使用以下步骤：

- 选择 **窗口**  >  **程序包管理器**
- 选择 **混合现实 Toolkit 基础**
- 在 "**示例**" 部分找到 **场景系统资源**

  ![导入场景系统资源](../images/scene-system/UpmImportSceneSystemResources.png)

- 选择 **导入**

### <a name="asset-unitypackage-files"></a>资产 ( unitypackage) 文件

如果 SceneSystemResources 文件夹已删除，或在导入过程中被取消选择，则可以使用以下步骤进行恢复：

- 选择 **资产**  >  **导入包**  >  **自定义包**
- 打开 **MixedReality。 Toolkit。Foundation** 包
- 确保已选择 " **服务/SceneSystem/SceneSystemResources** " 和 "所有子选项"

  ![重新导入场景系统资源](../images/scene-system/ReimportSceneSystemResources.png)

- 选择 **导入**

## <a name="how-to-use-the-scene-system"></a>如何使用场景系统

- [场景类型](scene-system-scene-types.md)
- [内容场景加载](scene-system-content-loading.md)
- [监视内容加载](scene-system-load-progress.md)
- [照明场景加载](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>编辑器设置

默认情况下，场景系统在 Unity 编辑器中强制执行多个行为。 如果你发现这些行为中的任何一种，可以在场景系统配置文件的 "**编辑器设置**" 部分中禁用。

- `Editor Manage Build Settings:` 如果为 true，则服务将自动更新生成设置，确保添加所有管理器、照明和内容场景。 如果希望完全控制生成设置，请禁用此设置。

- `Editor Enforce Scene Order:` 如果为 true，则服务将确保管理器场景首先显示在场景层次结构中，后跟光照和内容。 如果需要对场景层次结构进行总体控制，请禁用此选择。

- `Editor Manage Loaded Scenes:` 如果为 true，则服务将确保始终加载管理器、内容和照明场景。 如果希望在编辑器中加载哪些场景的总体控制，请禁用。

- `Editor Enforce Lighting Scene Types:` 如果为 true，则该服务将确保在 `PermittedLightingSceneComponentTypes` 光照场景中只允许使用在中定义的照明相关组件。 如果希望完全控制照明场景的内容，请禁用。

![场景系统编辑器设置](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
