---
title: 创建全息远程处理电脑应用程序
description: 完成本课程可以了解如何创建电脑应用程序来远程处理从电脑到 HoloLens 2 的混合现实体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392492"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2.创建全息远程处理电脑应用程序

本教程将介绍如何创建用于全息远程处理的电脑应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。

## <a name="objectives"></a>目标

* 为全息远程处理配置 Unity
* 了解如何通过 Visual Studio 生成和部署应用程序
* 开发全息远程处理应用程序并连接到 HoloLens

## <a name="configuring-the-capabilities"></a>配置功能

在“项目设置”窗口中，展开“发布设置”，向下滚动到“功能”部分，然后选择下面除现有功能外显示的功能复选框 。

* Internet 客户端服务器
* 专用网络客户端服务器

![启用功能](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>在电脑上构建应用程序

全息远程处理应用现可在你的电脑上生成内容。 请按照以下步骤进行这些更改，以在电脑上构建该应用程序。

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>测试“全息远程处理”远程应用程序

若要将电脑应用程序连接到 HoloLens 2，请执行以下过程：

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1.在 HoloLens 2 设备上安装“远程播放器”应用程序

* 在 HoloLens 2 上，访问 Store 应用并搜索“远程播放器”。
* 选择“远程播放器”应用。
* 点击“安装”，下载并安装该应用。

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2.将全息远程处理电脑应用连接到远程播放器

* 在 HoloLens 上启动“远程播放器”。
* 记下 HoloLens IP 地址。 远程播放器启动后，会立即将其显示为全息图。
* 在电脑上打开全息远程处理电脑应用程序。
* 启动该应用程序后，输入 IP 地址，然后单击“连接”按钮进行连接 。

## <a name="congratulations"></a>祝贺

本教程介绍了如何创建全息远程处理远程应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。 将 HoloLens 连接到全息远程处理电脑应用程序后，你应该会看到混合现实体验流式传输到 HoloLens 2 设备。
