---
title: 配置混合现实功能工具
description: 了解如何从面向 HoloLens 和 VR 开发的混合现实功能工具中下载并安装混合现实工具包 Unity。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731934"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>配置混合现实功能工具

使用混合现实功能工具时，你可以访问三个不同的设置类别并可随意自定义这些类别：

* [下载设置](#download-settings)
* [功能设置](#feature-settings)
* [导入设置](#import-settings)

## <a name="download-settings"></a>下载设置

![下载设置](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>覆盖现有包文件

如果启用此设置，则每次获取包文件时都会下载包文件。 

* **建议将此选项保留为禁用状态以减少网络带宽使用量**
* 默认情况下，不会重新下载以前获取的包文件

### <a name="package-cache"></a>包缓存

更改此设置可更新下载功能包的位置。

> [!NOTE]
> 该设置在此版本中是只读的。 将来的版本允许配置此设置。

## <a name="feature-settings"></a>功能设置

![功能设置](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>显示预览版本

启用此设置可获取预览版本。
* 默认情况下，不会在混合现实功能工具中显示预览版本 

> [!NOTE]
> 预览版本定义为在包版本中包含“-preview”指定。

### <a name="show-early-access-program-features"></a>显示抢先访问计划功能

启用此设置可从注册的抢先访问计划版本中获取功能。

* 默认情况下，不会在混合现实功能工具中显示抢先访问功能 

> [!NOTE]
> 如果在没有`Show preview releases`的情况下启用`Show early access program features`，可能导致发现中不显示抢先访问包。

## <a name="import-settings"></a>导入设置

![导入设置](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>替换现有包文件

默认情况下，混合现实功能工具会删除正在导入的包的以前副本，以减少文件大小和不必要的计算。 

* 取消选中此设置可保留所有版本

### <a name="project-relative-import-path"></a>项目的相对导入路径

更改此设置可更新导入时复制功能包的项目文件夹路径。 

* 例如，如果项目文件夹是 C:\GalaxyExplorer，则完全限定的导入路径将为 C:\GalaxyExplorer\Packages\MixedReality 。

> [!NOTE]
> 该设置在此版本中是只读的。 将来的版本允许配置此设置。

## <a name="early-access-settings"></a>抢先访问设置

![抢先访问设置](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>在删除抢先访问计划之前要求确认

此设置确定在每次删除抢先访问计划时是否显示提示。

### <a name="my-previews"></a>我的预览

已注册的抢先访问计划的列表。 使用`Add`、`Edit`和`Remove`来管理已注册的计划的集合。

## <a name="diagnostic-settings"></a>诊断设置

![诊断设置](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>日志文件

显示诊断日志文件的路径。

## <a name="see-also"></a>另请参阅

- [欢迎使用混合现实功能工具](welcome-to-mr-feature-tool.md)