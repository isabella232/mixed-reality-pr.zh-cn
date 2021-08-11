---
title: 迁移时限
description: 有关如何在 MRTK 中迁移到更新的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 9e657e0b90f8087670b72c993ab1dcf78ae9e6680873139c6867d7c551a41895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220034"
---
# <a name="migration-window"></a>迁移时限

当 MRTK 发生更改时，某些组件可能会弃用，并引入替换项。
迁移窗口是一种工具，可帮助用户自动将部分已弃用的组件迁移到新的替换项。

![迁移时限](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>使用情况

若要打开该窗口，请选择"**混合现实**  >  **Toolkit**  >  **实用工具**  >  **迁移窗口"。** 打开迁移窗口后，可以通过选择迁移处理程序的组件特定实现来启用选择模式导航选项卡。  

![迁移选择模式](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>对象模式

选择"对象"选项卡可启用对象"字段"，用户可以从当前打开的场景或预制件中拖放要迁移的项目文件夹中的任何 Game 对象。
按 *()* 对象右侧显示的"删除"按钮会从选择列表中删除该对象。

所有所需对象都进入列表中后，按"迁移"按钮将所选迁移处理程序实现所需的更改应用到选择中与实现匹配的所有组件。

![选择迁移](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>场景模式

允许用户拖放包含要迁移的对象的场景资产。

![选择要迁移的场景](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project模式

按 *"迁移* "按钮将更新项目内所有预制件和场景的迁移处理程序实现所面向的组件。

![迁移完整项目](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>另请参阅

- [从早期版本更新](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality Toolkit版本](../../release-notes/mrtk-26-release-notes.md)
- [MRTK 路线图](../../roadmap.md)
