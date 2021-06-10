---
title: 迁移窗口
description: 有关如何在 MRTK 中迁移到更新的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647126"
---
# <a name="migration-window"></a>迁移时限

当 MRTK 发生变化时，某些组件可能会被弃用，并且会引入替换内容。
"迁移" 窗口是一种工具，可帮助用户自动将这些不推荐使用的部分的子集迁移到新的替换项。

![迁移时限](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>使用情况

若要打开该窗口，请选择 "**混合现实**  >  **工具包**  >  **实用工具**  >  **迁移" 窗口**。 在迁移窗口打开后，可以通过选择迁移处理程序的特定于组件的实现来启用选择模式导航选项卡。  

![迁移选择模式](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>对象模式

选择 "对象" 选项卡后，用户可以在其中将 "对象" 字段拖放到要迁移的项目文件夹中当前打开的场景或 prototyping 中的任何游戏对象。
按所列对象右侧显示的 "删除 *( )* " 按钮将从选择列表中删除该对象。

所有所需的对象都在列表中后，按 " *迁移* " 按钮会将所选迁移处理程序实现所需的更改应用于所选内容中与实现匹配的所有组件。

![选择迁移](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>场景模式

允许用户拖放包含要迁移的对象的场景资产。

![选择用于迁移的场景](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>项目模式

按 " *迁移* " 按钮将为项目中的所有 prototyping 和场景更新迁移处理程序实现的目标组件。

![迁移完整项目](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>另请参阅

- [从早期版本更新](../../updates-deployment/updating.md)
- [Microsoft 混合现实工具包版本](../../release-notes/mrtk-26-release-notes.md)
- [MRTK 路线图](../../roadmap.md)
