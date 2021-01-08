---
title: DirectX 中的共享空间定位点
description: 了解如何通过在 DirectX 应用程序中共享本地和 Azure 空间锚点来同步两个 HoloLens 设备。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens，同步，空间定位，传输，多人，查看，方案，演练，示例代码，Azure，Azure 空间锚，ASA
ms.openlocfilehash: 46fe6be5d81a8fc68502500e318eb8e63d223089
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008527"
---
# <a name="shared-experiences-in-directx"></a>DirectX 中的共享体验

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](../native/openxr-getting-started.md)**。

共享体验是指多个用户使用其自己的 HoloLens、iOS 或 Android 设备，共同查看相同的全息影像并与之进行交互。 全息图使用空间锚点共享定位在空间的固定点上。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

你可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 来创建支持云的持久空间锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。  通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。  这可实现实时共享体验。

你还可以将 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 用于每个 HoloLens、IOS 和 Android 设备上的异步全息影像。  通过共享持久云空间锚点，多个设备可以在一段时间内观察到相同的持久全息图，即使这些设备同时不存在。

若要开始在 HoloLens 应用中构建共享体验，请尝试5分钟的 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空间锚快速入门</a>。

启动并运行 Azure 空间锚点后，可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上创建和查找锚</a>。  演练也适用于 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，使你能够在所有设备上共享相同的定位标记。

## <a name="local-anchor-transfers"></a>本地定位点传输

在不能使用 Azure 空间锚点的情况下， [本地定位点传输](../../out-of-scope/local-anchor-transfers-in-directx.md) 允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。  此方法提供的定位回调不如 Azure 空间锚，而且不支持 iOS 和 Android 设备。

## <a name="see-also"></a>另请参阅

* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">用于 HoloLens 的 Azure 空间锚点 SDK</a>