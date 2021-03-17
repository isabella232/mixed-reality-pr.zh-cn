---
title: Unity 中的空间锚
description: 了解如何在 Unity 混合现实应用程序中创建、存储和提取空间锚。
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity，空间锚，定位存储，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623617"
---
# <a name="spatial-anchors-in-unity"></a>Unity 中的空间锚

空间锚点在应用程序会话之间将全息区保存在实际空间内。 保存到 HoloLens 的锚定存储中后，可以在不同的会话中找到并加载它们，在没有 internet 连接的情况下是理想的备选方案。

> [!IMPORTANT]
> 本地定位点存储在设备上，而 Azure 空间定位点存储在云中。 如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](../mixed-reality-cloud-services.md#azure-spatial-anchors)。 请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。

## <a name="understanding-anchors"></a>了解定位点

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>使用 AnchorStore

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [空间映射](spatial-mapping-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [空间锚点持久性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>
* [体验规模](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的失跟](tracking-loss-in-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)