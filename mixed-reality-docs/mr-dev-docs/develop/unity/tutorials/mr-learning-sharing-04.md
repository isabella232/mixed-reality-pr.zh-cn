---
title: 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中与多个用户共享对象运动。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200773"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.与多个用户共享对象运动

本教程介绍如何共享对象的运动，使共享体验的所有参与者可以展开协作并查看彼此的交互。

## <a name="objectives"></a>目标

* 配置项目以共享对象的运动
* 了解如何生成基本的多用户协作应用

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加教程预制件来准备场景。

在“层次结构”窗口中，展开“MixedRealityPlayspace”对象并选择“主照相机”子对象，然后在“检查器”窗口中，使用“添加组件”按钮将“AR 照相机管理器(脚本)”组件添加到“主照相机”对象    ：

![配置了部分 AR 照相机管理器组件的 Unity](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后将“TableAnchor”预制件拖动到“层次结构”窗口中“SharedPlayground”对象上，以将其作为 SharedPlayground 对象的子项添加到场景    ：

![选中新增的 TableAnchor 预制件的 Unity](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

在“层次结构”窗口中，确保“MixedRealityPlayspace”对象已展开，且已选择“TableAnchor”对象 。 将“主照相机”组件拖入 TableAnchor 的“AR 会话源”组件的“照相机”字段   ：

![配置了 AR 会话源主照相机分配的 Unity](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>配置 PUN 以将对象实例化

在本部分，你将配置项目以使用在[入门教程](mr-learning-base-01.md)中创建的“探测车浏览器”体验，并定义在哪里将其实例化。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  

在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：

* 向“探测车浏览器预制件”字段分配来自“资源”文件夹的“RoverExplorer_Complete_Variant”预制件 

![配置了部分 Photon 房间组件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

在“NetworkRoom”子对象仍处于选中状态的情况下，在“层次结构”窗口中展开“TableAnchor”对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：  

* 向“探测车浏览器位置”字段中分配来自“层次结构”窗口的“TableAnchor”>“Table”子对象 

![配置了 Photon 房间组件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>尝试带有共享对象移动的体验

如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你在 HoloLens 中移动对象时，你将看到对象在 Unity 中移动：

![动画显示了具有联网对象的 Unity](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>祝贺

你已成功将项目配置为同步对象移动，因此用户可以在其他用户移动对象时看到对象移动。 在下一教程中，你将实现协调物理世界体验的功能。 这将确保用户可以看到各自的实际物理位置，让对象在所有用户看来都处于同一物理位置并同步旋转。

> [!div class="nextstepaction"]
> [下一教程：5.将 Azure 空间定位点集成到共享体验中](mr-learning-sharing-05.md)
