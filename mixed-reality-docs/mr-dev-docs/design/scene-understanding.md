---
title: 场景理解
description: 了解如何使用适用于 HoloLens 的场景理解进行开发，其中包括 SDK、功能和常见使用方案。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 场景了解，空间映射，Windows Mixed Reality，Unity，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，封闭，SDK
ms.openlocfilehash: dd54be85ed71c3359408c02914470e97ab42b90e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196392"
---
# <a name="scene-understanding"></a>场景理解

场景理解为混合现实开发人员提供了一种结构化的高级别环境表示形式，旨在简化环保感知应用程序的开发。 场景理解通过组合现有混合现实运行时的强大功能来实现此功能，如高度准确但结构较少的 [空间映射](spatial-mapping.md) 和新的 AI 驱动的运行时。 通过将这些技术相结合，场景理解会生成与你可能已在 Unity 或 ARKit/ARCore 等框架中使用的3D 环境的表示形式。 场景理解入口点从场景观察器开始，该观察程序由应用程序调用以计算新场景。 目前，该技术可以生成3个不同但相关的对象类别：

* 简化的 watertight 环境网格，可推断平面房间结构而不会造成混乱
* 我们调用四边形的放置的平面区域
* 与我们的表面上的四边形/Watertight 数据对齐的 [空间映射](spatial-mapping.md) 网格的快照

![空间映射网格，标签平面表面，watertight 网格](images/SUScenarios.png)

本文档旨在提供方案概述，并阐明场景理解和空间映射共享的关系。 若要查看操作中的场景理解，请查看下面 **的设计全息影像-空间感知** 视频演示：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*此视频取自 "设计全息影像" HoloLens 2 应用。下载并在 [此处](https://aka.ms/dhapp)享受完全体验。*

## <a name="developing-with-scene-understanding"></a>通过场景理解进行开发

本文仅用于介绍运行时和概念的场景。 如果你正在寻找有关如何使用场景理解进行开发的文档，你可能对以下文章感兴趣：

[场景理解 SDK 概述](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

可以从示例 GitHub 站点下载场景理解示例应用：

[场景理解示例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

如果没有设备，并且想要访问示例场景以尝试场景理解，示例资产文件夹中有场景：

[场景理解示例场景](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK 中 IsInRole 中的声明

如果要查找有关使用场景理解进行开发的特定详细信息，请参阅 [场景理解 SDK 概述](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 文档。

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

![常见空间映射使用场景的插图：放置、遮挡、物理和导航](images/sm-concepts-1000px.png)<br>
*常见的空间映射使用方案：放置、遮挡、物理和导航。*

<br>

可以通过空间映射和场景理解解决环境感知应用程序的许多核心方案。 这些核心方案包括放置、遮挡、物理等。 场景理解与空间映射之间的一个核心区别是在最大准确性和延迟与结构和简单性之间权衡。 如果应用程序需要尽可能低的延迟和只有你想要访问的网格三角形，请直接使用空间映射。 如果要执行更高级别的处理，可以考虑切换到场景理解模型，因为它应提供超集功能。 始终可以访问尽可能完整且准确的空间映射数据，因为场景理解在其表示形式中提供了空间映射网格的快照。

以下部分重新访问新场景理解 SDK 上下文中的核心空间映射方案。

### <a name="placement"></a>放置

场景理解提供了旨在简化放置方案的新构造。 场景可以计算名为 SceneQuads 的基元，这些基元描述可以放置全息影像的平面。 SceneQuads 围绕放置而设计，描述了二维图面，并提供了一个用于放置在该表面上的 API。 以前，当使用三角形网格进行放置时，必须扫描四个部分的所有区域，执行孔填充/后处理来识别对象放置的好位置。 对于四边形，这并不总是必需的，因为场景了解运行时可推断哪些故障区域未扫描，并使不属于图面的区域无效。

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

[空间映射封闭](spatial-mapping.md#occlusion) 仍是捕获环境的实时状态的最小延迟方式。 虽然这对于在高度动态的场景中提供封闭可能很有用，但出于多种原因，你可能希望考虑到封闭的场景理解。 如果使用通过场景理解生成的空间映射网格，则可以从空间映射请求数据，这些数据不会存储在本地缓存中，也不能从感知 Api 获得。 将空间映射与水台网格一起用于遮挡可提供额外价值，特别是完成未扫描房间结构。

如果你的要求可以容忍场景理解的延迟增加，应用程序开发人员应考虑使用场景理解 watertight 网格，以及与平面表示形式一致的空间映射网格。 这将提供"两全其美"方案，其中简化的 watertight 遮挡通过更精细的非平面几何图形进行渗透，从而尽可能提供最真实的遮挡贴图。

### <a name="physics"></a>物理

场景理解会生成使用语义分解空间的 watertight 网格，专门用于解决空间映射网格施加的许多物理限制。 Watertight 结构可确保始终命中物理光线投射，语义分解允许更简单地生成用于室内导航的导航网格。 如有关遮挡 [的部分](#occlusion)中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 创建场景将生成尽可能完整的物理网格。 环境网格的 watertight 属性可防止命中测试无法命中表面。 网格数据将确保物理与场景中的所有对象交互，而不只是房间结构。

### <a name="navigation"></a>导航

由语义类分解的平面网格是导航和路径规划的理想构造，可缓解空间映射导航概述 [中所述的许多](spatial-mapping.md#navigation) 问题。 场景中计算的 SceneMesh 对象由表面类型取消组合，确保导航网格生成仅限于可进行演练的图面。 由于地面结构的简单性，3D 引擎（如 Unity）中的动态导航网格生成取决于实时要求。

生成准确的导航网格目前仍然需要后期处理，即应用程序仍必须将遮挡器项目到楼层，以确保导航不会通过混乱/表等。 实现此目的的最准确方法是投影世界网格数据，如果场景是通过 EnableWorldMesh 标志计算的，则会提供此数据。

### <a name="visualization"></a>可视化效果

虽然 [空间映射可视化](spatial-mapping.md#visualization) 可用于环境的实时反馈，但在很多情况下，平面和 watertight 对象的简单性提供了更高的性能或视觉质量。 如果在四边形或平面 watertight 网格提供的平面表面上投影，则使用空间映射描述的阴影投影和接地技术可能更好。 这对于完全预扫描并非最佳的环境/方案特别适用，因为场景将推断并完成环境，而平面假设将最小化项目。

此外，空间映射返回的图面总数受内部空间缓存限制，而场景理解的空间映射网格版本可以访问未缓存的空间映射数据。 因此，场景理解更适合捕获更大空间的网格表示形式 (例如，大于单个房间) 用于可视化或进一步的网格处理。 使用 EnableWorldMesh 返回的世界网格在整个中具有一致的详细级别，这可能会产生更好的可视化效果（如果以线框形式呈现）。

### <a name="see-also"></a>另请参阅

* [场景理解 SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [空间映射](spatial-mapping.md)