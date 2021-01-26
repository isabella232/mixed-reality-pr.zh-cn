---
title: 教程概述和目标
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581168"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="96ef1-104">1.概述和目标</span><span class="sxs-lookup"><span data-stu-id="96ef1-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="96ef1-105">设备支持</span><span class="sxs-lookup"><span data-stu-id="96ef1-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="96ef1-106"><strong>课程</strong></span><span class="sxs-lookup"><span data-stu-id="96ef1-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="96ef1-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="96ef1-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="96ef1-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="96ef1-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="96ef1-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="96ef1-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="96ef1-110">✔️</span><span class="sxs-lookup"><span data-stu-id="96ef1-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="96ef1-111">准备工作</span><span class="sxs-lookup"><span data-stu-id="96ef1-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="96ef1-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="96ef1-112">Prerequisites</span></span>

* <span data-ttu-id="96ef1-113">一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="96ef1-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="96ef1-114">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="96ef1-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="96ef1-115">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="96ef1-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="96ef1-116">一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="96ef1-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="96ef1-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="96ef1-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96ef1-118">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="96ef1-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="96ef1-119">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="96ef1-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="96ef1-120">下一课：2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="96ef1-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)