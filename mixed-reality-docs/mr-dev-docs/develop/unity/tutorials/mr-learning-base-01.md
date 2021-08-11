---
title: MRTK 教程简介
description: 本课程从零开始介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, 求解器, 眼动跟踪, 语音命令
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224783"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1.MRTK 教程简介

欢迎使用入门教程系列！ 这些教程将介绍混合现实工具包 (MRTK) 及其提供的一些功能。 此外，还将构建一个混合现实体验，让用户可在其中浏览按 NASA 的“好奇号”火星探测车建模的全息图。 本系列结束后，你将牢牢把握 MRTK 及其如何加速开发过程。

本系列教程的设计遵循一定的顺序，因此请按正确的顺序学习：

1. [简介](mr-learning-base-01.md)（你已经位于这里）
2. [初始化项目并部署第一个应用程序](mr-learning-base-02.md)
3. [配置 MRTK 配置文件](mr-learning-base-03.md)
4. [定位场景中的对象](mr-learning-base-04.md)
5. [使用求解器创建动态内容](mr-learning-base-05.md)
6. [创建用户界面](mr-learning-base-06.md)
7. [与 3D 对象交互](mr-learning-base-07.md)
8. [使用眼动跟踪](mr-learning-base-08.md)
9. [使用语音命令](mr-learning-base-09.md)

## <a name="objectives"></a>目标

* 了解如何针对 MRTK 配置 Unity
* 了解如何生成和部署到设备
* 了解如何使用 MRTK 的一些主要功能
* 创建完整的混合现实体验

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更高版本
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备

* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> 并装有 Unity 2020.3 LTS 或 Unity 2019.4 LTS（OpenXR 要求使用 2020.3.8 或更高版本以防发生错误）

安装 Unity 时，请务必在“平台”下检查以下组件。

* **通用 Windows 平台生成支持**
* **Windows 生成支持 (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

如果安装 Unity 时未使用这些选项，可以通过 Unity Hub 中的“添加模块”菜单添加它们。

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> 建议用于本系列教程的 MRTK 版本是 MRTK 2.7.2

> [!Important]
> 本系列教程支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR 或 Windows XR 插件）以及 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA 或 Windows XR 插件）。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求。

> [!div class="nextstepaction"]
> [下一教程：2.初始化项目并部署第一个应用程序](mr-learning-base-02.md)
