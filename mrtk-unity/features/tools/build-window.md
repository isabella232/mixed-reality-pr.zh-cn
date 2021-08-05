---
title: “生成”窗口
description: 有关使用 MRTK for Unity 中的 "生成" 窗口的文档。
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，生成，生成窗口，工具
ms.openlocfilehash: d01fefd09337e2639388a43d94bd8beb93716e3ef7f12a9c924b5755fb594447
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211373"
---
# <a name="build-window"></a>“生成”窗口
![生成 & 部署流](images/MRTK_BuildWindow0.png)

通过 MRTK 的生成窗口，可以轻松生成 & 部署 MRTK-Unity 项目。 通过单击一次按钮，您可以生成 Unity 项目并生成 Visual Studio 解决方案 (。.SLN) ，UWP 应用包 (。APPX) ，并在设备上安装应用程序包。 


## <a name="unity-build-options"></a>Unity 生成选项
![生成窗口-Unity 生成选项1](images/MRTK_BuildWindow1.png)

这些场景来自 Unity 生成设置。 你可以使用下拉菜单更改目标设备类型。

## <a name="appx-build-options"></a>Appx 生成选项
!["生成" 窗口-Appx 生成选项2](images/MRTK_BuildWindow2.png)

此选项卡显示 Visual Studio 解决方案的配置。 若要启用 HoloLens 2 的眼睛跟踪输入功能，请检查 "**注视输入功能**" 选项。 

可以在 " **3d 应用 Launcher 模型**" 字段中为自定义3d 应用启动器图标指定 glb 文件。 有关详细信息，请参阅 [3d 应用启动器设计指南](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 。

默认情况下，"版本控制" 选项中已选中 " **自动增量** "。 AppX 版本将自动递增。


## <a name="deploy-options"></a>部署选项
![生成窗口-部署选项3](images/MRTK_BuildWindow3.png)

在此选项卡中，可以通过输入设备门户的用户名和密码来连接到设备。 

在页面的底部，可以找到已创建的应用包的列表。 

