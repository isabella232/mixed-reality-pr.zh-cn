---
title: 使用 Unity 包管理器
description: 在 Unity 程序包管理器中使用 MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK 包，
ms.openlocfilehash: fb96a910b86e8ec9f6d73b8239e0ae008ea021c65f2c52edc613d2fe02719e58
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194452"
---
# <a name="using-the-unity-package-manager"></a>使用 Unity 包管理器

从版本2.5.0 开始，使用[混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)，在使用 unity 2019.4 和更高版本时，Microsoft Mixed reality Toolkit 与 unity 程序包管理器 (UPM) 集成。

## <a name="using-the-mixed-reality-feature-tool"></a>使用混合现实功能工具

如欢迎使用 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 中所述，你可以使用 [此链接](https://aka.ms/MRFeatureTool)下载该工具。

> [!IMPORTANT]
> 如果项目的清单 `Microsoft Mixed Reality` 在部分中有一个条目 `scopedRegistries` ，则建议将其删除。
>
> 若要删除已配置的作用域注册表，请使用 `Edit`  >  `Project Settings`  >  `Package Manager` 。
>
> ![删除作用域内注册表](../features/images/packaging/RemoveScopedRegistry.png)

查找功能时，MRTK 包会显示在 `Mixed Reality Toolkit` 标题下方。

![发现功能](../features/images/packaging/DiscoverFeatures.png)

选择功能时，不需要考虑所需的依赖项，该工具会自动下载并将其集成到项目中。

![必需的依赖项](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>通过 Unity 程序包管理器管理混合现实功能

一旦将混合现实 Toolkit 程序包添加到了包清单中，就可以使用 Unity 程序包管理器用户界面对其进行管理。

![MRTK Foundation UPM 包](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> 如果使用 Unity 程序包管理器删除混合现实 Toolkit 包，则必须使用[前面介绍的步骤](#using-the-mixed-reality-feature-tool)重新添加此包。

### <a name="using-mixed-reality-toolkit-examples"></a>使用混合现实 Toolkit 示例

与使用资产包时 () 文件不同， `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` 不会自动导入示例场景和资产。

若要利用一个或多个示例，请使用以下步骤：

1. 在 Unity 编辑器中，导航到 `Window` > `Package Manager`
1. 在包列表中，选择 `Mixed Reality Toolkit Examples`
1. 在列表中找到所需的示例 (s) `Samples`
1. 单击 `Import into Project`

![导入示例](../features/images/packaging/MRTK_ExamplesUpm.png)

更新示例包时，Unity 提供了更新导入的示例的选项。

> [!NOTE]
> 更新导入的示例将覆盖对该示例和关联的资产所做的任何更改。

## <a name="see-also"></a>另请参阅

- [混合现实 Toolkit 包](../packages/mrtk-packages.md)
