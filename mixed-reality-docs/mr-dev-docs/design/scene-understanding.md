---
title: 场景理解
description: 了解如何使用 HoloLens 的场景理解进行开发，包括 SDK、功能和常见使用方案。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 场景理解、空间映射、Windows Mixed Reality、Unity、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、遮挡、SDK
ms.openlocfilehash: 06a4fdb6f3ad777c47151950acbd4ccdec9935ca
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143597"
---
# <a name="scene-understanding"></a>场景理解

场景理解为混合现实开发人员提供了结构化的高级别环境表示形式，旨在直观地为环境感知型应用程序进行开发。 场景理解通过组合现有混合现实运行时（如高度准确但结构不太结构化的空间映射和新的 AI[](spatial-mapping.md)驱动运行时）的能力来实现此点。 通过组合这些技术，场景理解可生成类似于 Unity 或 ARKit/ARCore 等框架中使用的三维环境的表示形式。 场景理解入口点从场景观察程序开始，应用程序调用它来计算新场景。 目前，该技术可以生成 3 个不同但相关的对象类别：

* 简化的 watertight 环境网格，可推断平面房间结构，且无杂乱
* 用于放置的平面区域，我们称之为四边形
* 与 [所显示](spatial-mapping.md) Quads/Watertight 数据对齐的空间映射网格的快照

![空间映射网格、带标签的平面图面、watertight 网格](images/SUScenarios.png)

本文档旨在提供方案概述，并阐明场景理解和空间映射共享的关系。 若要了解场景理解的运行情况，请查看下面的设计 [全息影像 - 空间]() 感知视频演示：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="developing-with-scene-understanding"></a>使用场景理解进行开发

本文仅介绍场景理解运行时和概念。 如果你正在寻找有关如何使用场景理解进行开发的文档，你可能对以下文章感兴趣：

[场景理解 SDK 概述](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

可以从示例 GitHub 站点下载场景理解示例应用：

[场景理解示例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

如果你没有设备，并且想要访问示例场景来尝试了解场景，示例资产文件夹中有一些场景：

[场景了解示例场景](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK 中 IsInRole 中的声明

如果正在寻找有关通过场景理解进行开发的特定详细信息，请参阅 [场景了解 SDK 概述](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 文档。

### <a name="sample"></a>示例

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>场景理解</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>常见使用方案

![常见空间映射使用方案的插图：放置、封闭、物理学和导航](images/sm-concepts-1000px.png)<br>
*常见的空间映射使用方案：放置、封闭、物理学和导航。*

<br>

环境感知应用程序的许多核心方案可通过空间映射和场景理解进行寻址。 这些核心方案包括放置、封闭、物理学等。 场景理解和空间映射之间的核心差异是对结构和简易性的最大准确性和延迟的折衷。 如果你的应用程序需要可能的最低延迟时间和只需要访问的网格三角形，请直接使用空间映射。 如果要执行更高级的处理，则可以考虑切换到场景理解模型，因为它应提供功能的超集。 您始终可以访问最完整且准确的空间映射数据，因为场景理解会提供空间映射网格的快照作为其表示形式的一部分。

以下部分将在新的场景理解 SDK 的上下文中重新访问核心空间映射方案。

### <a name="placement"></a>放置

场景理解提供旨在简化放置方案的新构造。 场景可以计算称为 SceneQuads 的基元，它们描述了可放置全息影像的平面面。 SceneQuads 围绕放置而设计，描述了二维图面，并提供了一个用于放置在该表面上的 API。 以前，当使用三角形网格进行放置时，必须扫描四个部分的所有区域，执行孔填充/后处理来识别对象放置的好位置。 对于四边形，这并不总是必需的，因为场景了解运行时可推断哪些故障区域未扫描，并使不属于图面的区域无效。

:::row:::
    :::column:::
       ![已禁用推理，并捕获扫描区域的放置区域 SceneQuads。](images/SUQuads.png)<br>
       已禁用 SceneQuads 的 **图像 #1** ，并捕获扫描区域的放置区。
    :::column-end:::
        :::column:::
       ![四边形启用了推理后，放置不再局限于扫描区域。](images/SUWatertight.png)<br>
        **图像 #2** -启用了推理的四边形，放置不再局限于扫描区域。
    :::column-end:::
:::row-end:::

<br>


如果你的应用程序想要将二维或3D 全息图放置在环境的严格结构上，最好是从 [空间映射](spatial-mapping.md) 网格计算此信息。 有关此主题的详细信息，请参阅 [场景了解 SDK 参考](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**注意** 对于依赖于空间映射网格的传统放置代码，可以通过设置 EnableWorldMesh 设置与 SceneQuads 一起计算空间映射网格。 如果场景理解 API 不满足应用程序的延迟要求，我们建议继续使用 [空间映射 API](spatial-mapping.md#placement)。

### <a name="occlusion"></a>封闭

[空间映射封闭](spatial-mapping.md#occlusion) 仍是捕获环境的实时状态的最小延迟方式。 虽然这对于在高度动态的场景中提供封闭可能很有用，但出于多种原因，你可能希望考虑到封闭的场景理解。 如果使用通过场景理解生成的空间映射网格，则可以从空间映射请求数据，这些数据不会存储在本地缓存中，也不能从感知 Api 获得。 使用封闭和 watertight 网格的空间映射将提供额外的价值，特别是完成了未扫描的空间结构。

如果你的要求可以容忍场景理解的延迟增加，应用程序开发人员应考虑使用场景理解 watertight 网格，以及与平面表示形式一致的空间映射网格。 这将提供"两全其美"方案，其中简化的 watertight 遮挡通过更精细的非平面几何图形进行渗透，从而尽可能提供最真实的遮挡贴图。

### <a name="physics"></a>物理

场景理解会生成使用语义分解空间的 watertight 网格，专门用于解决空间映射网格施加的许多物理限制。 Watertight 结构可确保始终命中物理光线投射，语义分解允许更简单地生成用于室内导航的导航网格。 如有关遮挡 [的部分](#occlusion)中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 创建场景将生成尽可能完整的物理网格。 环境网格的 watertight 属性可防止命中测试无法命中表面。 网格数据将确保物理与场景中的所有对象交互，而不只是房间结构。

### <a name="navigation"></a>导航

由语义类分解的平面网格是导航和路径规划的理想构造，可缓解空间映射导航概述 [中所述的许多](spatial-mapping.md#navigation) 问题。 场景中计算的 SceneMesh 对象由表面类型取消组合，确保导航网格生成仅限于可进行演练的图面。 由于地面结构的简单性，3D 引擎（如 Unity）中的动态导航网格生成取决于实时要求。

生成准确的导航网格目前仍然需要后期处理，即应用程序仍必须将遮挡器项目到楼层，以确保导航不会通过混乱/表等。 实现此目的的最准确方法就是预测世界网格数据，如果场景是使用 EnableWorldMesh 标志计算的，则提供该数据。

### <a name="visualization"></a>可视化效果

虽然 [空间](spatial-mapping.md#visualization) 映射可视化可用于环境实时反馈，但在许多情况下，平面对象和 watertight 对象的简单性提供了更多的性能或视觉质量。 如果投影在四边形网格或平面水台网格提供的平面图面上，则使用空间映射描述的阴影投影和地面技术可能更美观。 对于环境/方案尤其如此，因为场景将推断出全面预扫描，而完整的环境和平面假设将最大程度地减少项目。

此外，空间映射返回的图面总数受内部空间缓存限制，而场景理解的空间映射网格版本可以访问未缓存的空间映射数据。 因此，场景理解更适用于捕获较大空间的网格表示形式 (例如，大于单个房间) 可视化或进一步网格处理。 使用 EnableWorldMesh 返回世界网格将始终具有一致的详细级别，如果呈现为线框，则可能会生成更美观的可视化效果。

### <a name="see-also"></a>另请参阅

* [场景理解 SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [空间映射](spatial-mapping.md)