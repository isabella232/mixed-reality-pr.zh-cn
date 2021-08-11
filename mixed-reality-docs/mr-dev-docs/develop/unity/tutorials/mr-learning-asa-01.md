---
title: Azure 空间定位点教程简介
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, ios, android, Windows 10, ARCore, macOS, Android 生成支持, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 4d753546fd8fd0779e7614ca11e4668e359d8f9dcdc8db9d62e95267747471db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197357"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1.Azure 空间定位点教程简介

欢迎学习 Azure 空间定位点教程！ 通过本系列教程，你将了解 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure 空间定位点</a>的基础知识，学习如何在真实世界中创建定位空间的混合现实体验。 你还将了解如何将项目部署到 Android 和 iOS。

本系列教程：

1. [简介](mr-learning-asa-01.md)（你已经位于这里）
2. [Azure 空间定位点入门](mr-learning-asa-02.md)
3. [保存、检索和共享 Azure 空间定位点](mr-learning-asa-03.md)
4. [显示 Azure 空间定位点反馈](mr-learning-asa-04.md)
5. [适用于 Android 和 iOS 的 Azure 空间定位点](mr-learning-asa-05.md)

## <a name="objectives"></a>目标

* 了解如何创建空间定位点并从 Azure 中获取它们
* 了解如何在应用会话之间实现空间对齐
* 了解如何在多台设备之间实现空间对齐
* 了解如何准备、生成项目并将其部署到 Android 和 iOS 上

## <a name="prerequisites"></a>先决条件

* 一台 Windows 10 计算机，其中已[安装](../../install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020/2019 LTS 并添加了通用 Windows 平台生成支持模块
* 已完成[创建空间定位点资源](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中）
* 已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验
* 如果打算部署到 Android 和 HoloLens
  * <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020/2019 LTS 且已添加 Android 生成支持模块
* 如果打算部署到 iOS 和 HoloLens
  * 一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020/2019 LTS 且已添加 iOS 生成支持模块

> [!Important]
> 本系列教程支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR 或 Windows XR 插件）以及 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA）。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求。

> [!div class="nextstepaction"]
> [下一教程：2.开始使用 Azure 空间定位点](mr-learning-asa-02.md)
