---
title: DirectX 中的共享空间定位点
description: 了解如何在 DirectX 应用程序中HoloLens本地定位点和 Azure 空间定位点来同步两个设备。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens、同步、空间定位点、传输、多人游戏、视图、方案、演练、示例代码、Azure、Azure 空间定位点、ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193541"
---
# <a name="shared-experiences-in-directx"></a>DirectX 中的共享体验

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](../native/openxr-getting-started.md)**。

共享体验是一种多用户使用自己的HoloLens iOS 或 Android 设备共同查看同一全息影像并与之交互的体验。 全息影像使用空间定位点共享定位在空间中的固定点。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

可以使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位</a>点创建基于云的持久空间定位点，然后应用可以在多个设备、iOS 和 Android HoloLens定位这些定位点。  通过在多个设备上共享一个公共空间定位点，每个用户可以看到相对于该定位点在同一物理位置呈现的内容。  这可实现实时共享体验。

还可以将<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位</a>点用于跨设备、iOS HoloLens Android 设备的异步全息影像持久性。  通过共享持久云空间定位点，多个设备可以观察一段时间相同的持久全息影像，即使这些设备不同时存在于一起。

若要开始在 HoloLens 应用中构建共享体验，请尝试使用 5 分钟的 Azure 空间定位点HoloLens<a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">快速入门</a>。

使用 Azure 空间定位点启动并运行后，可以在<a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens。</a>  演练还适用于 Android 和 <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS，</a> 使你可以在所有设备上共享相同的定位点。

## <a name="local-anchor-transfers"></a>本地定位点传输

在无法使用 Azure 空间定位点的情况下，本地定位[](../../out-of-scope/local-anchor-transfers-in-directx.md)点传输允许一HoloLens设备导出要由另一台设备导入HoloLens定位点。  与 Azure 空间定位点相比，此方法提供更可靠的定位点召回，此方法不支持 iOS 和 Android 设备。

## <a name="see-also"></a>另请参阅

* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 空间定位点 SDK for HoloLens</a>