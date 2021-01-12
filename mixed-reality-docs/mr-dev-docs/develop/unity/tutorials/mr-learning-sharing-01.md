---
title: 多用户功能教程简介
description: 请完成本课堂，了解如何在 HoloLens 2 应用程序中实现共享的多用户体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 1000b4d2637e3a0f3bbc79df9866577427674767
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007217"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="3f562-104">1.多用户功能教程简介</span><span class="sxs-lookup"><span data-stu-id="3f562-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="3f562-105">欢迎学习多用户功能教程！</span><span class="sxs-lookup"><span data-stu-id="3f562-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="3f562-106">通过本系列教程，你将学习有关使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN) 生成多用户体验的基础知识。</span><span class="sxs-lookup"><span data-stu-id="3f562-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="3f562-107">混合现实开发人员可使用多个网络选项来创建共享体验，PUN 就是其中的一个。</span><span class="sxs-lookup"><span data-stu-id="3f562-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="3f562-108">本系列教程：</span><span class="sxs-lookup"><span data-stu-id="3f562-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="3f562-109">设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="3f562-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="3f562-110">连接多名用户</span><span class="sxs-lookup"><span data-stu-id="3f562-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="3f562-111">与多名用户共享对象移动情况</span><span class="sxs-lookup"><span data-stu-id="3f562-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="3f562-112">将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="3f562-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="3f562-113">目标</span><span class="sxs-lookup"><span data-stu-id="3f562-113">Objectives</span></span>

* <span data-ttu-id="3f562-114">了解如何创建 PUN 应用并将其连接到 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3f562-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="3f562-115">了解如何在共享体验中连接多名用户</span><span class="sxs-lookup"><span data-stu-id="3f562-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="3f562-116">了解如何与其他用户共享对象移动情况</span><span class="sxs-lookup"><span data-stu-id="3f562-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="3f562-117">了解如何在多台设备之间实现空间对齐</span><span class="sxs-lookup"><span data-stu-id="3f562-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f562-118">必备条件</span><span class="sxs-lookup"><span data-stu-id="3f562-118">Prerequisites</span></span>

* <span data-ttu-id="3f562-119">一台 Windows 10 计算机，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="3f562-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="3f562-120">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3f562-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="3f562-121">一台[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="3f562-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="3f562-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="3f562-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="3f562-123">已完成[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="3f562-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="3f562-124">已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验</span><span class="sxs-lookup"><span data-stu-id="3f562-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="3f562-125">已完成 [Azure 空间定位点教程](mr-learning-asa-01.md)系列，或者之前创建 Azure 空间定位点帐户的经验</span><span class="sxs-lookup"><span data-stu-id="3f562-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="3f562-126">如果打算部署到 Android 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3f562-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="3f562-127"><a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接</span><span class="sxs-lookup"><span data-stu-id="3f562-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="3f562-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 Android 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="3f562-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="3f562-129">如果打算部署到 iOS 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3f562-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="3f562-130">一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机</span><span class="sxs-lookup"><span data-stu-id="3f562-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="3f562-131"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="3f562-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="3f562-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 iOS 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="3f562-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="3f562-133">建议对本系列教程使用混合现实工具包版本 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="3f562-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="3f562-134">建议对本系列教程使用 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="3f562-134">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="3f562-135">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="3f562-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f562-136">下一教程：2.设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="3f562-136">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
