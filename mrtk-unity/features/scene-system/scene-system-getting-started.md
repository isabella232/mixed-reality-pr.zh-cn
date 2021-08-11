---
title: 场景系统入门
description: 使用 MRTK 的场景系统的登陆页
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 5b4f1c3b0f069d320feca8ccecacc6c66576b50339ea7b7733f34525005dd842
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191545"
---
# <a name="scene-system-getting-started"></a>场景系统入门

## <a name="when-to-use-the-scene-system"></a>何时使用场景系统

如果项目由单个场景组成，则场景系统可能不需要。 当以下一个或多个情况成立时，它最有用：

- 项目有多个场景。
- 你习惯单场景加载，但不喜欢它破坏 MixedRealityToolkit 实例的方式。
- 你需要一种简单的方式来附加加载多个场景来构造体验。
- 你需要一种简单的方式来跟踪正在进行中的加载操作，或者一种控制同时加载多个场景的场景激活的简单方法。
- 你想要在所有场景中保持照明一致且可预测。

## <a name="scene-system-resources"></a>场景系统资源

默认情况下，场景系统使用 DefaultManagerScene 和 DefaultLighting 场景 (一对场景) 。 如果找不到其中任一场景，则"场景系统配置文件检查器"中将显示一条消息。

![默认资源消息](../images/scene-system/DefaultResourcesMessage.png)

>![注意]如果项目使用自定义管理器和照明场景，可以放心忽略此消息。

以下各节现在介绍了如何根据用于导入混合现实应用的方法来Toolkit。

### <a name="unity-package-manager-upm"></a>Unity 程序包管理器 (UPM) 

在混合现实Toolkit UPM 包中，场景系统资源打包为示例。 由于 UPM 包不可变，Unity 无法打开必要的场景文件，除非将其显式导入项目中。

若要导入，请使用以下步骤：

- 选择 **"窗口**  >  **程序包管理器**
- 选择 **混合现实 Toolkit Foundation**
- 在 **"示例"部分** 找到"场景 **系统资源** "

  ![导入场景系统资源](../images/scene-system/UpmImportSceneSystemResources.png)

- 选择" **导入"**

### <a name="asset-unitypackage-files"></a>资产 (.unitypackage) 文件

如果 SceneSystemResources 文件夹已删除，或在导入过程中已取消选中，可以使用以下步骤恢复该文件夹：

- 选择 **资产**  >  **导入包**  >  **自定义包**
- 打开 **Microsoft.MixedReality.Toolkit。基础** 包
- 确保 **已选择"服务/场景""系统/场景""** 系统""资源"以及所有子选项

  ![重新导入场景系统资源](../images/scene-system/ReimportSceneSystemResources.png)

- 选择" **导入"**

## <a name="how-to-use-the-scene-system"></a>如何使用场景系统

- [场景类型](scene-system-scene-types.md)
- [内容场景加载](scene-system-content-loading.md)
- [监视内容加载](scene-system-load-progress.md)
- [照明场景加载](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>编辑器设置

默认情况下，场景系统在 Unity 编辑器中强制执行多个行为。 如果发现其中任一行为是繁重的，可以在场景系统配置文件的"编辑器 **"设置** 禁用它们。

- `Editor Manage Build Settings:` 如果为 true，服务将自动更新生成设置，确保添加所有管理器、照明和内容场景。 如果希望完全控制生成设置，请禁用此选项。

- `Editor Enforce Scene Order:` 如果为 true，服务将确保首先在场景层次结构中显示管理器场景，然后显示照明和内容。 如果希望完全控制场景层次结构，请禁用此选项。

- `Editor Manage Loaded Scenes:` 如果为 true，服务将确保始终加载管理器、内容和照明场景。 如果希望完全控制编辑器中加载的场景，请禁用 。

- `Editor Enforce Lighting Scene Types:` 如果为 true，则服务将确保只允许在照明场景中使用 中定义的照明 `PermittedLightingSceneComponentTypes` 相关组件。 如果希望完全控制照明场景的内容，请禁用 。

![场景系统编辑器设置](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
