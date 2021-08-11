---
title: 多用户功能教程简介
description: 请完成本课堂，了解如何在 HoloLens 2 应用程序中实现共享的多用户体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 3db488cc31d6ef7746aae67b3a84c42dc91985b586e907d2172346fe0952876f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197691"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1.多用户功能教程简介

欢迎学习多用户功能教程！ 通过本系列教程，你将学习有关使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN) 生成多用户体验的基础知识。 混合现实开发人员可使用多个网络选项来创建共享体验，PUN 就是其中的一个。

本系列教程：

* [设置 Photon Unity Networking](mr-learning-sharing-02.md)
* [连接多名用户](mr-learning-sharing-03.md)
* [与多名用户共享对象移动情况](mr-learning-sharing-04.md)
* [将 Azure 空间定位点集成到共享体验中](mr-learning-sharing-05.md)

## <a name="objectives"></a>目标

* 了解如何创建 PUN 应用并将其连接到 Unity 项目
* 了解如何在共享体验中连接多名用户
* 了解如何与其他用户共享对象移动情况
* 了解如何在多台设备之间实现空间对齐

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 计算机，其中已[安装](../../install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020 LTS 并添加了通用 Windows 平台生成支持模块
* 已完成[创建空间定位点资源](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* 已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验
* 已完成 [Azure 空间定位点教程](mr-learning-asa-01.md)系列，或者之前创建 Azure 空间定位点帐户的经验
* 如果打算部署到 Android 和 HoloLens
  * <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020 LTS 且已添加 Android 生成支持模块
* 如果打算部署到 iOS 和 HoloLens
  * 一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020 LTS 且已添加 iOS 生成支持模块

> [!IMPORTANT]
> 建议对本系列教程使用混合现实工具包版本 MRTK 2.7。

> [!IMPORTANT]
> 建议对本系列教程使用 Unity 2020 LTS。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求。

> [!div class="nextstepaction"]
> [下一教程：2.设置 Photon Unity Networking](mr-learning-sharing-02.md)