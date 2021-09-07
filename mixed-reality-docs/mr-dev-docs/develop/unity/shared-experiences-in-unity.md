---
title: Unity 中的共享体验
description: 了解如何使用 Azure 空间定位点在 Unity 应用程序中的多个用户之间共享相同的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共享、定位点、WorldAnchor、MR 共享 250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空间定位点、ASA、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244188"
---
# <a name="shared-experiences-in-unity"></a>Unity 中的共享体验

共享体验允许多个用户（每个用户都有自己的HoloLens iOS 或 Android 设备）共同查看同一全息影像并与之交互。 全息影像空间定位点共享将定位在空间的固定点。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

### <a name="automated-with-world-locking-tools"></a>使用世界锁定工具自动执行

与本地定位点一样，世界锁定工具可以使用一组 Azure 空间定位点来锁定相对于物理世界的整个坐标空间，而不是使用单个定位点锁定单个对象。 世界锁定整个空间不仅提供更有利于精确布局的环境，而且在开发人员时间和运行时资源方面效率更高。

有关利用 Azure 空间定位点跨 HoloLens、Android 和 iOS 设备共享坐标系以及跨会话保留空间的更多信息和示例，请参阅世界锁定[工具文档](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html)。

### <a name="manual-configuration-of-azure-spatial-anchors"></a>手动配置 Azure 空间定位点

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>创建持久云支持的空间定位点，应用可以在多个 HoloLens、iOS 和 Android 设备上找到这些定位点。  通过在多个设备上共享一个公共空间定位点，每个用户可以看到相对于该定位点在同一物理位置呈现的内容。

还可以将<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>用于跨设备、iOS HoloLens Android 设备的异步全息影像持久性。  通过共享持久云空间定位点，多个设备可以观察一段时间相同的持久全息影像，即使这些设备不同时存在于一起。

若要开始在 Unity 中构建共享体验，请尝试 5 分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间定位点 Unity 快速入门</a>。

设置 Azure 空间定位点后，可以在 Unity 中创建 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">和查找定位点</a>。

## <a name="local-anchor-transfers"></a>本地定位点传输

在无法使用 Azure 空间定位点的情况下，本地定位[](../../out-of-scope/local-anchor-transfers-in-unity.md)点传输允许一HoloLens设备导出定位点，以便第二HoloLens导入定位点。  此方法在 iOS 和 Android 设备上不受支持，并且提供比 Azure 空间定位点更可靠的定位点召回。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索混合现实平台功能和 API。 在这里，可以继续学习下一部分：

> [!div class="nextstepaction"]
> [可定位相机](locatable-camera-in-unity.md)

或直接跳到在设备或模拟器上部署应用：

> [!div class="nextstepaction"]
> [部署到HoloLens或Windows Mixed Reality头戴显示设备](../platform-capabilities-and-apis/using-visual-studio.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另请参阅
* [混合现实中的共享体验](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">适用于 Unity 的 Azure 空间定位点 SDK</a>