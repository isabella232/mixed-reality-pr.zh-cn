---
title: “生成”窗口
description: 有关在适用于 Unity 的 MRTK 中使用生成窗口的文档。
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 生成， 生成窗口， 工具
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176154"
---
# <a name="build-window"></a>“生成”窗口
![生成&部署流](images/MRTK_BuildWindow0.png)

使用 MRTK 的生成窗口可以轻松生成&部署MRTK-Unity项目。 单击单个按钮即可生成 Unity 项目，并生成Visual Studio解决方案 (。SLN) ，UWP 应用包 (。APPX) ，在设备上安装应用包。 


## <a name="unity-build-options"></a>Unity 生成选项
![生成窗口 - Unity 生成选项 1](images/MRTK_BuildWindow1.png)

这些场景来自 Unity 生成设置。 可以使用下拉菜单更改目标设备类型。

## <a name="appx-build-options"></a>Appx 生成选项
![生成窗口 - Appx 生成选项 2](images/MRTK_BuildWindow2.png)

此选项卡显示解决方案Visual Studio配置。 若要启用HoloLens 2眼动跟踪输入功能，请检查"**凝视输入功能"** 选项。 

可以在自定义 3D 应用启动器图标的 **"3D** 应用Launcher模型"字段中分配 .glb 文件。 有关详细信息 [，请参阅 3D 应用启动器](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 设计准则。

默认情况下 **，"版本控制** 选项"中会选中"自动递增"。 AppX 版本将自动递增。


## <a name="deploy-options"></a>部署选项
![生成窗口 - 部署选项 3](images/MRTK_BuildWindow3.png)

在此选项卡中，可以通过为设备输入用户名和密码来连接到设备门户。 

在页面底部，可以找到已创建的应用包的列表。 

