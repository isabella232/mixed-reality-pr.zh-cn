---
layout: LandingPage
title: Azure 混合现实云服务概述
description: 混合现实云服务资源。
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合现实, 开发, 开发, HoloLens, 云服务, Azure, 远程渲染, 空间定位点, 认知服务, 认知, unity, 机器学习, 语音翻译, 计算机视觉 Microsoft Graph
ms.openlocfilehash: e660556810cdea86321b7826217268e6c8d0850a
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865402"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Azure 混合现实云服务概述

![ Azure 空间定位点图像](../design/images/AzureSpatialAnchors.jpg)

使用 Azure 混合现实服务，解锁每个人都熟悉的世界 - 我们周围的三维物理世界。 通过在工作和世界的上下文中捕获和显示数字信息，帮助用户更有效地创建、学习和协作。 将 3D 引入移动设备、头戴显示设备和其他不受限制的设备上。 使用 Azure 有助于确保最敏感的信息受到保护。

## <a name="mixed-reality-services"></a>混合现实服务

混合现实云服务（例如 Azure 远程渲染和 Azure 空间定位点）可帮助开发人员在各种平台上构建引人注目的沉浸式体验 。 借助这些服务，当你创建应用程序来进行 3D 训练、预测性设备维护和设计审查时，可在项目中集成空间感知 - 所有操作均在用户环境的上下文中进行。

### <a name="azure-remote-rendering"></a>Azure 远程渲染
Azure 远程渲染（也称为 ARR）是一项服务，可用于实时渲染高度复杂的 3D 模型并将其流式传输到设备。 ARR 目前为公共预览版，可将其添加到面向 HoloLens 2 或 Windows 桌面电脑的 Unity 或 Native C++ 项目中。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR 是在不受限制的设备上运行的任何混合现实应用程序的重要组成部分，因为它们的计算渲染能力较小。 以下面的并排引擎模型比较为例：左侧的高保真模型具有超过 1800 万个三角形，而右侧的简化模型仅具有大约 20 万个三角形。 在每个细节都很重要的场景中（工业工厂管理、卡车发动机等资产的设计审查、术前手术规划等），3D 可视化将这些细节变为现实。 这有助于设计人员、工程师、医生和学生更好地理解复杂信息并做出正确的选择。 但是，这种简化可能会导致关键业务和设计决策所需的重要细节丢失。

![Unity 展示应用中的 Azure 远程渲染示例](images/arr-engine.png)

ARR 通过将渲染工作负载移至云中的高端 GPU 来解决此问题。 然后，云托管的图形引擎接管并渲染图像，将其编码为视频流，并将模型直接流式传输到目标设备。 

* 对于高端 GPU 无法处理的复杂模型，ARR 将工作负载分配给多个 GPU，并将结果合并为一个图像，从而使该过程对用户完全透明。 

ARR 不会限制可在应用中使用的用户界面类型，这是一个额外的好处。 在某个帧的结尾，本地渲染的内容将自动与远程图像合并，如下图所示：

![Unity 展示应用中的 Azure 远程渲染示例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure 空间定位点
Azure 空间定位点（又称为 ASA）是一项跨平台服务，可用于生成空间感知的混合现实应用程序。 借助 Azure 空间定位点，你可按真实世界的规模跨多台设备映射、保存和共享全息内容。 

ASA 是针对混合现实中常见用例特别定制的解决方案，其中包括：
* 导视：可以连接两个或多个空间定位点以创建用户必须与之交互的任务列表或关注点。
* 多用户体验：通过与同一虚拟空间中的对象进行交互，用户可以来回传递动作。
* 在现实世界中保留虚拟内容：用户可以在现实世界中放置虚拟对象，这些虚拟对象可以从其他受支持的设备查看。

![Azure 空间定位点示例](images/persistence.gif)

可在多种环境中开发该服务，并将其部署到大量设备和平台上。 这样的话，它们自带列表上的可用平台不用进行这些操作：
* Unity for HoloLens
* Unity for iOS
* Unity for Android
* 本机 iOS
* 本机 Android
* 用于 HoloLens 的 C++/WinRT 和 DirectX
* Xamarin for iOS
* Xamarin for Android

## <a name="cognitive-services"></a>认知服务

:::row:::
    :::column:::
       [![语音](../whats-new/images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[语音](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
        了解语音服务如何支持将语音处理功能集成到任何应用或服务中。 使用标准的（或可自定义的）语音字体将口语转换为文本或基于文本产生自然发音。 免费试用所有服务，并使用以下功能快速生成启用了语音服务的应用和服务。
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![影像](../whats-new/images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[影像](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
        识别、标识、说明、索引和调整你的图片、视频和数字墨迹内容。了解视觉服务如何使应用和服务能够准确地识别和分析图像、视频和数字墨迹中的内容。
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>独立 Unity 服务

下面列出的独立服务不适用于混合现实，但在各种开发上下文中都很有用。 如果要在 Unity 中开发，其中的每项服务都可集成到你的新项目或现有项目中。

### <a name="device-support"></a>设备支持
<table>
    <tr>
        <td><strong>Azure 云服务</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens 第 1 代</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">语言翻译</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">计算机视觉</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">自定义视觉</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">跨设备通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">人脸识别</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Functions 和存储</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">流式传输视频</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">机器学习</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Functions 和存储</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">对象检测</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">机器人集成</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>请参阅

* 适用于 HoloLens 2 的 Azure 空间定位点教程 - [Azure 空间定位点入门第 1 部分（共 3 部分）](../mrlearning-asa-ch1.md)
* 适用于 HoloLens 2 的 Azure 语音服务教程 - [集成和使用语音识别与听录第 1 部分（共 4 部分）](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
