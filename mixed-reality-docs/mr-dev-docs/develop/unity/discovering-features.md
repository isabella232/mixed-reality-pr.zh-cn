---
title: 发现并获取功能
description: 发现并下载混合现实功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731993"
---
# <a name="discovering-and-acquiring-features"></a>发现并获取功能

本文中的各部分概述了如何在混合现实功能工具中查找功能包。 如果需要有关对给定部分的参考，请参阅下面的屏幕截图：

![发现功能](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>可用功能

### <a name="category"></a>类别

混合现实功能工具可显示功能类别集合，便于查找所需内容。 展开任何类别都可显示其可用功能的集合。

> [!NOTE]
> 如果找不到要查找的功能，请检查“其他功能”。

![功能类别](images/FeatureCategory.png)

上面的屏幕截图中的类别标头包含以下属性（从左到右）：

- 展开和折叠按钮
- 类别名称（例如：混合现实工具包）
- 选定的功能计数
- 可用功能计数
- 分区按钮

> [!NOTE]
> 选择按钮与上下文相关。 根据类别中功能选择的状态，将显示一个或多个`Select All`和`Select None`按钮。

### <a name="feature"></a>功能

![功能条目](images/FeatureEntry.png)

功能按适当的类别列出。 在上面的屏幕截图中，功能条目从左到右包含：

- 选择复选框
- 功能名称（例如：Mixed Reality Toolkit Foundation）
- 可用版本列表
- 指向[功能包详细信息](viewing-package-details.md)的链接

> [!NOTE]
> 如果某功能是由抢先访问功能提供的（也称为个人预览版），则将显示一个指示器图标 ![抢先访问](images/EarlyAccess.png)。

## <a name="refresh-the-feature-catalog"></a>刷新功能目录

若要检查有无新功能和更新的功能，请单击“刷新” ![“刷新”按钮](images/RefreshButton.png) 按钮。 随即会连接到目录站点并检索最新信息。 读取目录后，将显示上次更新的日期和时间。

## <a name="select-features"></a>选择特征

功能的选择方法是：展开类别，选择版本，然后单击复选框：

![所选功能](images/SelectedFeatures.png)

若要选择某类别中的每个包，可使用`Select All`按钮。 `Select None`将取消选择所有已选定的包。 

具有一个或多个选定功能的每个类别都将更新以显示计数。

## <a name="acquiring-features"></a>获取功能

选择功能后，选择“获取功能”，开始下载选定的功能包文件。

> [!NOTE]
> 默认情况下，不会重新下载以前获取的功能包文件。 若要更改此行为，请参阅[配置功能工具](configuring-feature-tool.md)。

下载完成后，混合现实功能工具将移动到[导入功能](importing-features.md)步骤。

## <a name="going-back-to-the-previous-step"></a>返回到上一步骤

在“发现功能”中，混合现实功能工具允许返回到项目选择。 选择“返回”重新开始。

## <a name="see-also"></a>另请参阅

- [欢迎使用混合现实功能工具](welcome-to-mr-feature-tool.md)
- [配置功能工具](configuring-feature-tool.md)
- [查看功能包详细信息](viewing-package-details.md)
- [导入选定包](importing-features.md)
