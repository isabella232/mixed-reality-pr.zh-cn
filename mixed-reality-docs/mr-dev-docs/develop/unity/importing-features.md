---
title: 导入功能
description: 了解如何从面向 HoloLens 和 VR 开发的混合现实功能工具导入并安装功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230803"
---
# <a name="importing-features"></a>导入功能

下载功能后，可以查看这些功能并将其导入到 Unity 项目。 在此步骤中，你的应用程序窗口应如下图所示：

![导入功能](images/FeatureToolImport.png)

## <a name="features-list"></a>特征列表

“功能”列表包含在发现过程中选择的包的集合。 在导入之前，可以选择或取消选择每个功能。 可使用下面所示的“详细信息”链接查看包详细信息

![特征列表](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>必需的依赖项列表

“必需的依赖项”列表包含运行一个或多个所选功能所需的包。 此列表还将包含依赖项的依赖项。 在导入之前，可以选择或取消选择每个依赖项。 可使用下面所示的“详细信息”链接查看包详细信息

![依赖项列表](images/RequiredDependencyList.png)

> [!NOTE]
> 如果取消选择所需的依赖项，则会导致在 Unity 中加载项目时出现一个或多个依赖项缺失的错误。 这些功能在项目中不可用。

## <a name="validating-selections"></a>验证选定内容

强烈建议在导入前验证所选功能。 此步骤引发的任何问题都可能会妨碍项目成功开发。

![验证问题](images/ValidationIssues.png)

混合现实功能工具提供了两个自行解决问题的方法（如后面部分所述）以及手动取消和解决问题的选项。

### <a name="enable-dependencies"></a>启用依赖项

“启用依赖项”按钮将自动重新选择缺少的依赖项。 此选项适用于显式选择的依赖项（显示在“功能”列表中）和根据所选功能的要求隐式选择的依赖项。

### <a name="disable-features"></a>禁用功能

选择“禁用功能”会自动取消选择依赖于一个或多个未选中的依赖项的功能。 此选项适用于隐式选择的依赖项包和显式选择的功能。

## <a name="importing"></a>导入

选择“导入”添加所选功能，并在更新目标项目之前提供[最终审批](reviewing-changes.md)。

> [!IMPORTANT]
> 如果导入时仍然存在验证问题，则将显示一条警告消息。 建议选择“否”，单击“验证”并解决所显示的任何问题。
>
> ![继续验证问题](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>返回到上一步骤

在“导入功能”中，混合现实功能工具允许返回到[发现](discovering-features.md)。 选择“返回”下载其他功能包。

## <a name="see-also"></a>另请参阅

- [欢迎使用混合现实功能工具](welcome-to-mr-feature-tool.md)
- [发现和获取](discovering-features.md)
- [查看功能包详细信息](viewing-package-details.md)
- [查看和批准项目修改](reviewing-changes.md)