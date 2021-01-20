---
title: Unity 中的共享体验
description: 了解如何使用 Azure 空间锚点在 Unity 应用程序的多个用户之间共享相同的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共享、定位、WorldAnchor、MR 共享250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空间锚，ASA，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583366"
---
# <a name="shared-experiences-in-unity"></a>Unity 中的共享体验

共享体验允许多个用户，每个用户都有自己的 HoloLens、iOS 或 Android 设备，共同查看同一个全息影像，并与之交互。 全息影像通过空间锚点共享定位在空间的固定点上。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 创建支持云的持久空间锚，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。  通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。 

你还可以将 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 用于每个 HoloLens、IOS 和 Android 设备上的异步全息影像。  通过共享持久云空间锚点，多个设备可以在一段时间内观察到相同的持久全息图，即使这些设备同时不存在。

若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

设置 Azure 空间锚定后，可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。

## <a name="local-anchor-transfers"></a>本地定位点传输

在不能使用 Azure 空间锚点的情况下， [本地定位点传输](../../out-of-scope/local-anchor-transfers-in-unity.md) 允许一个 hololens 设备导出一个定位点，以便另一个 hololens 可以导入它。  IOS 和 Android 设备不支持此方法，提供比 Azure 空间定位点更少的定位回调。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。 从这里，你可以继续学习下一部分：

> [!div class="nextstepaction"]
> [可定位相机](locatable-camera-in-unity.md)

或直接跳到在设备或模拟器上部署应用：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机](../platform-capabilities-and-apis/using-visual-studio.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另请参阅
* [混合现实中的共享体验](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>