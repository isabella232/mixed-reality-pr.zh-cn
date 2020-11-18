---
title: 针对 Unreal 的性能建议
description: Unreal 中混合现实应用获得最佳性能的建议
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 性能, 优化, 设置, 文档
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549121"
---
# <a name="performance-recommendations-for-unreal"></a>针对 Unreal 的性能建议

## <a name="overview"></a>概述

本文是在[针对混合现实的性能建议](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unreal Engine 的功能。 建议在继续操作之前，先了解应用程序瓶颈和一般性能修复，以及有关分析和剖析混合现实应用的信息。

## <a name="recommended-unreal-project-settings"></a>建议的 Unreal 项目设置
可以在“编辑”>“项目设置”中找到以下每个设置。

1. 使用移动 VR 呈现器：
    * 滚动到“项目”部分，选择“目标硬件”，并将目标平台设置为“移动/平板电脑”

![移动目标设置](images/unreal/performance-recommendations-img-01.png)

2. 使用前向呈现器： 
    * 对于混合现实，此功能比默认的延迟呈现管道要好得多。 这主要是由于可以单独关闭的功能数量众多。 
    * 可以在 [Unreal 文档](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)中找到详细信息。

![前向呈现](images/unreal/performance-recommendations-img-04.png)

3. 使用移动多视图：
    * 滚动到“引擎”部分，选择“呈现”，展开“VR”部分，同时启用“实例立体声”和“移动多视图”。 应取消选中移动端 HDR。

![VR 渲染设置](images/unreal/performance-recommendations-img-03.png)

4. 使用 OpenXR 时，请确保为“默认 RHI”选择了“默认值”或“D3D12”  。
    * 由于平台执行额外的渲染通道，因此选择 D3D11 将对性能产生负面影响。 D3D12 会改进渲染性能，同时避免额外的渲染通道。

![默认 RHI](images/unreal/performance-recommendations-img-09.png)

5. 禁用顶点雾化： 
    * 顶点雾化在多边形中的每个顶点上应用雾化计算，然后将结果插入到多边形的整个面上。 如果游戏不使用雾化，则应选择此设置以禁用雾化，从而提高着色性能。

![顶点雾化选项​​](images/unreal/performance-recommendations-img-05.png)

6. 禁用遮挡剔除：
    * 滚动到“引擎”部分，选择“呈现”，展开“剔除”部分，取消选中“遮挡剔除”。
        + 如果需要对呈现的详细场景进行遮挡剔除，建议在“引擎”>“呈现”中启用“支持软件遮挡剔除” 。 这使得 Unreal 可以在 CPU 上执行此操作，并避免 GPU 遮挡查询，后者在 HoloLens 2 上的执行效果不佳。
    * 移动设备上 GPU 上的遮挡剔除速度缓慢。 通常，你希望 GPU 主要关注呈现。 如果你认为遮挡将有助于提高性能，请尝试改为启用软件遮挡。 请注意，如果你已受到大量绘图调用的 CPU 限制，则启用软件遮挡可能会使性能更差。

![禁用遮挡剔除](images/unreal/performance-recommendations-img-02.png)

7. 禁用自定义深度模具通道：
    * 此功能需要额外的通道，这意味着它的速度缓慢。 在 Unreal 上，半透明度功能也很慢。 可以在 [Unreal 文档](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)中找到详细信息。

![深度模板](images/unreal/performance-recommendations-img-06.png)

8. 减少级联阴影映射： 
    * 减少阴影映射的数量将提高性能。 通常，除非存在明显的质量损失，否则应将其设置为 1。 

![级联阴影映射](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>可选设置

> [!NOTE]
> 以下设置可能会提高性能，但会以禁用某些功能为代价。 仅当你确定不需要使用这些功能时才使用这些设置。

1. 移动着色器置换减少
    * 如果光源不独立于相机移动，则可以安全地将此值设置为 0。 主要优点是它将允许 Unreal 剔除多个着色器置换，从而加快着色器的编译速度。

![移动着色器置换减少](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>请参阅
* [Unreal 引擎移动性能准则]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)