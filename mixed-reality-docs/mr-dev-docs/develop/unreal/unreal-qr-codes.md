---
title: Unreal 中的 QR 码
description: 了解如何在 Unreal 混合现实应用程序中设置、使用和跟踪 QR 码。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, qr 码, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 689ebe9b904b269c00078245b137bc21f2e56df2b441150c7c6b18c179ac51f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205112"
---
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 码

HoloLens 2 可以使用网络摄像头查看世界空间中的 QR 码，这会在每个代码的实际位置将其呈现为全息影像。 HoloLens 2 还可以在多个设备上的同一位置呈现全息影像，以打造共享体验。 请确保遵循将 QR 码添加到应用程序的最佳做法：

- 安静区域
- 照明和背景
- 大小、距离和角度位置

将 QR 码置于应用中时，请特别注意[环境注意事项](/hololens/hololens-environment-considerations)。 有关每个主题的详细信息以及下载所需 NuGet 包的说明，请参阅主 [QR 码跟踪](../platform-capabilities-and-apis/qr-code-tracking.md)文档。

> [!CAUTION]
> HoloLens 当前只能跟踪 QR 码这种图像类型，HoloLens 上尚不支持 Unreal 的 UARTrackedImage 模块。 如需跟踪自定义图像，可访问设备的[网络摄像头](unreal-hololens-camera.md)，并使用第三方图像识别库来处理图像。 

## <a name="enabling-qr-detection"></a>启用 QR 检测

由于 HoloLens 2 需要使用网络摄像头来查看 QR 码，因此需要在项目设置中将其启用：
- 打开“编辑”>“项目设置”，滚动到“平台”部分，然后选择“HoloLens”。
    + 展开“功能”部分，选中“网络摄像头”。  
- 还需要通过[添加 ARSessionConfig 资产](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)来选择使用 QR 码跟踪。

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>设置已跟踪的 QR 码

QR 码通过 Unreal 的 AR 跟踪几何系统显示为跟踪图像。 若要实现此操作，需执行以下操作：
1. 创建 Actor 蓝图，并添加 ARTrackableNotify 组件：

![QR AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 选择“ARTrackableNotify”，然后在“详细信息”面板中展开“事件”部分  ：

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. 单击“关于添加跟踪几何”旁的 +，将节点添加到事件图中。
    - 可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。

![向“关于添加跟踪几何”添加节点](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>使用已跟踪的 QR 码

下图中的事件图显示了 OnUpdateTrackedImage 事件，该事件用于呈现 QR 码中心的一个点并输出其数据。

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

以下是具体过程：
1. 首先，将跟踪图像转换为 ARTrackedQRCode，以检查当前更新的图像是否为 QR 码。  
2. 编码数据是从 QRCode 变量中检索的。 可以从 GetLocalToWorldTransform 位置获取左上方的 QR 码，并在 GetEstimateSize 中获取维度。

还可以在代码中[获取 QR 码的坐标系统](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。

## <a name="finding-the-unique-id"></a>查找唯一 ID

每个 QR 码都具有一个唯一的 GUID ID，可以通过以下方式查找：
- 拖放“作为 ARTracked QRCode”引脚并搜索“获取唯一 ID”。

![QR GUID](images/unreal-qr-guid.PNG)

QR 码幕后还有很多内容等待挖掘，因此体验之旅并没有就此结束。 请务必查看下面的链接，以了解更多详细信息。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索混合现实平台功能和 API 的过程之中。 从这里，你可以进入下一主题：

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

或直接跳到在设备或模拟器上部署应用：

> [!div class="nextstepaction"]
> [部署到设备](unreal-deploying.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另请参阅
* [空间映射](../../design/spatial-mapping.md)
* [全息影像](../../discover/hologram.md)
* [坐标系统](../../design/coordinate-systems.md)