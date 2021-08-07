---
title: 资产创建过程
description: 了解如何为混合现实体验创建、购买和端口资产。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 资产，创建，处理，预算，多边形，纹理，着色器，性能，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实 Toolkit，资产
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214102"
---
# <a name="asset-creation-process"></a>资产创建过程

Windows Mixed Reality 在 Microsoft 投入了大量投资。 开发人员构建三维图形的所有经验和技能都将继续对 HoloLens 有价值。

你为项目创建的资产分为多个形状和窗体。 它们可由一系列纹理/图像、音频、视频、3D 模型和动画组成。 我们无法开始涵盖可用于创建项目中使用的不同类型资产的所有工具。 对于本文，我们将重点介绍3D 资产创建方法。

![概念、创建、集成和迭代流](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*概念、创建、集成和迭代流*

## <a name="things-to-consider"></a>注意事项

在观看经验时，您要尝试创建，将其视为可用于尝试创建最佳体验的 **预算** 。 对于可以在资产中使用的 **多边形** 数量或 **材料类型** ，不一定有任何硬性限制。 将其视为一组预算的折衷。

下面是你的体验的示例预算。 性能不是单一故障点，而是通过几千次切削停止。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>资产</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 内存</th>
</tr><tr>
<td> Polygon（多边形）</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 纹理</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 着色器</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 实时照明</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Media (音频/视频) </td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 脚本/逻辑</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 一般开销</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>总计</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**资产总数**
* 场景中有多少资产处于活动状态？

**资产复杂性**
* 三角形/多边形有多少？
* 着色器的复杂程度如何？ 使用混合现实 Toolkit 时，建议使用[混合现实 Toolkit 标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)来降低着色器的复杂性。

开发人员和艺术家都必须考虑设备和图形引擎的功能。 Microsoft HoloLens 包含内置于设备中的所有计算和图形。 它共享开发人员在移动平台上所能找到的功能。

无论你的体验面向的是 [全息设备还是沉浸式设备](../discover/mixed-reality.md#the-mixed-reality-spectrum)，资产创建过程都是相同的。 需要注意的主要事项是设备功能和规模。 您可以在混合现实中看到现实世界，因此您需要根据经验来维护正确的规模。

## <a name="authoring-assets"></a>创作资产

首先，我们将介绍如何获取项目的资产：
1. 创建资产 (创作工具和对象捕获) 
2. 采购资产 (在线购买资产) 
3. 迁移资产 (获取现有资产) 
4. 外包资产 (从第三方导入资产) 

### <a name="creating-assets"></a>创建资产

**创作工具**<br>
首先，你可以通过几种不同的方式创建自己的资产。 3D 艺术家使用各种应用程序和工具来创建模型，其中包括 **网格**、 **纹理** 和 **材料**。 然后以文件格式保存该文件，应用程序使用的图形引擎可以导入或使用该格式，如 **。FBX** 或 **。OBJ**。 生成所选图形引擎支持的模型的任何工具将在 **HoloLens** 上工作。 在三维音乐家之间，很多选择使用[Autodesk 的 Maya，因为它可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)来转换资产的创建方式。 如果你想要快速获得一些东西，还可以使用 Windows 附带的[3d Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)进行导出。要在应用程序中使用的 OBJ。

**对象捕获**<br>
还可以选择以三维方式捕获对象。 在三维中捕获 inanimate 对象并通过数字内容创建软件对其进行编辑时，三维打印增加了。 使用 **Kinect 2** 传感器和 [3d 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)，可以使用捕获功能从真实世界对象创建资产。 这也是一 [套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ，用于通过处理多个要装订在一起和网格和纹理的图像来对 **photogrammetry** 执行相同的操作。

### <a name="purchasing-assets"></a>采购资产

另一种极佳的选择是购买资产以获得经验。 有大量的资产可通过 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 或 [TurboSquid](https://www.turbosquid.com/) 等服务获得。

从第三方购买资产时，始终需要检查以下属性：
* **什么是 poly 计数？**
  * 它是否适用于预算内？
* **模型是否有 (LODs) 的详细信息级别？**
  * 利用模型级别的详细信息，您可以缩放模型的详细信息以提高性能。
* **源文件可用吗？**
  * 不包含在 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 中，但始终包含在 [TurboSquid](https://www.turbosquid.com/)等服务中。
  * 如果没有源文件，则无法修改资产。
  * 确保提供的源文件可通过 3D 工具导入。
* **了解你获得什么**
  * 是否提供动画？
  * 请务必检查要购买的资产的内容列表。

### <a name="porting-assets"></a>移植资产

在某些情况下，需要将最初为其他设备和不同应用构建的现有资产移交给你。 在大多数情况下，这些资产可以转换为与应用使用的图形引擎兼容的格式。

移植资产以在 HoloLens 应用程序中使用时，需要提出以下问题：
* **可以直接导入还是需要转换为其他格式？** 使用使用的图形引擎检查要导入的格式。
* **如果转换为兼容格式，是否丢失了任何内容？** 有时，详细信息可能会丢失，或者导入可能会导致需要在 3D 创作工具中清理的项目。
* **资产的三角形/多边形计数是什么？** 根据应用程序的预算，可以使用 [Simplygon](https://www.simplygon.com/) 或类似工具按过程 (或手动减少原始资产中的) 计数，以适应应用程序预算。

### <a name="outsourcing-assets"></a>外包资产

对于需要比团队能够创建的资产更多的大型项目，另一种选择是外包资产创建。 外包过程涉及查找专门处理外包资产的合适工作室或机构。 这可以是开销最大的选项，但也是最灵活的选项。
* **清楚地定义要请求什么**
  * 提供尽可能多的详细信息
  * Front、side 和 back 概念图像
  * 在上下文中显示资产的参考图
  * 对象刻度 (通常以厘米为单位) 
* **提供预算**
  * Poly 计数范围
  * 纹理数
  * 对于 Unity 和 (着色器类型HoloLens应始终默认为移动着色器) 
* **了解成本**
  * 更改请求的外包策略是什么？

根据项目时间线，外包可以很好地工作，但需要更多的监督，以确保你第一次获得所需的正确资产。
