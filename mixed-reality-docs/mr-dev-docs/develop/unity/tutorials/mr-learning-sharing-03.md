---
title: 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 混合现实应用程序中连接多名用户。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 207c451ee616ee4065e948ca78c17ad59f7dd190
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702472"
---
# <a name="3-connecting-multiple-users"></a>3.连接多个用户

本教程介绍如何将多个用户连接为实时共享体验的一部分。 在本教程结束时，你将能够在多台设备上运行应用，并让每位用户都能实时看到其他用户的头像移动。

## <a name="objectives"></a>目标

* 了解如何在共享体验中连接多个用户

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：

* NetworkLobby 预制件
* SharedPlayground 预制件

![选中了新增的 NetworkLobby 和 SharedPlayground 预制件的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：

* DebugWindow 预制件

![选中了新增的 DebugWindow 预制件的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>配置 PUN 以将用户预制件实例化

在本部分中，配置项目以使用 PhotonUser 预制件。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  

在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在检查器窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：

* 向“Photon 用户预制件”字段中分配来自“资源”文件夹的“PhotonUser”预制件

![配置了部分 Photon 房间组件的 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>尝试包含多个用户的体验

如果现在生成 Unity 项目并将其部署到 HoloLens，然后回到 Unity，并在应用运行于 HoloLens 上时进入“游戏”模式，那么当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：

![动画显示了具有联网用户的 Unity](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

> [!CAUTION]
> 应用需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。 在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。

> [!div class="nextstepaction"]
> [下一教程：4.与多个用户共享对象移动](mr-learning-sharing-04.md)
