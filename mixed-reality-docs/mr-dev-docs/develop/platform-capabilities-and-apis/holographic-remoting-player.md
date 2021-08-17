---
title: 全息远程播放器
description: 了解全息远程处理播放器，以及通过 Wi-Fi 将全息内容从电脑HoloLens实时流式传输到你的视频。
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/30/2021
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、诊断、性能
ms.openlocfilehash: c5574017c33379248f4bf412cb5b046fdf309d72
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184658"
---
# <a name="holographic-remoting-player"></a>全息远程播放器

>[!TIP]
>[了解全息远程处理的基础知识。](holographic-remoting-overview.md)

>[!IMPORTANT]
>适用于 HoloLens 2全息远程处理是主要版本更改。 [第一代 **HoloLens (**](add-holographic-remoting.md)的远程) 必须使用 NuGet 包版本 **1.x.x，** 而 HoloLens 2 的远程应用程序 [**必须使用**](holographic-remoting-create-remote-wmr.md) **2.x.x**。 这意味着为应用程序编写的远程应用程序HoloLens 2第一代HoloLens (兼容，反之亦然) 第一代应用程序。

[全息远程处理播放器](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40)是一个配套应用，可连接到支持全息远程处理的电脑应用和游戏。 Player 可用于第一代HoloLens () HoloLens 2。  需要更新支持使用 HoloLens 进行全息远程处理的电脑应用，以支持使用 HoloLens 2。 如果对支持哪些版本有疑问，请与应用提供商联系。

>[!TIP]
>从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始，全息远程处理播放器还可用于Windows运行[Windows Mixed Reality。](../../discover/navigating-the-windows-mixed-reality-home.md)

>[!TIP]
>从版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 开始，可以使用 [OpenXR API](../native/openxr.md) 创建远程应用。 若要开始，请查看 [使用 OpenXR](holographic-remoting-create-remote-openxr.md)API 编写全息远程处理远程应用。

## <a name="connecting-to-the-holographic-remoting-player"></a>连接到全息远程处理播放器

按照应用说明连接到全息远程处理播放器。 需要输入远程处理HoloLens IP 地址，可在远程处理播放器主屏幕上看到该地址，如下所示：

![全息远程播放器](images/holographicremotingplayer.png)

每当看到主屏幕时，都会知道没有连接应用。

全息远程处理连接 **未加密**。 应始终通过你信任的安全Wi-Fi远程处理。

## <a name="quality-and-performance"></a>质量和性能

体验的质量和性能因以下三个因素而异：
* **正在运行的全息体验** - 呈现高分辨率或高度详细内容的应用可能需要更快的电脑或更快的无线连接。
* **电脑的硬件 -** 电脑需要能够以每秒 60 帧的速度运行和编码全息体验。 对于图形卡，我们通常建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更优。 同样，你的特定体验可能需要更高或更低的卡。
* **你的Wi-Fi** 连接 - 全息体验通过 Wi-Fi 进行流式传输。 使用具有低拥塞的快速网络，以最大程度地提高质量。 使用通过以太网电缆（而不是 Wi-Fi）连接的电脑也可以提高质量。

## <a name="diagnostics"></a>诊断

若要度量连接的质量 **，在全息** 远程处理播放器的主屏幕上说"启用诊断"。 启用诊断后，HoloLens (第一 **代**) 应用会显示：

* **FPS** - 远程处理播放器每秒接收和呈现的平均渲染帧数。 理想的是 60 FPS。
* **延迟**- 帧从电脑转到设备的平均HoloLens。 越低越好。 这主要取决于你的Wi-Fi网络。

在 **HoloLens 2** 应用会显示：

![全息远程播放器诊断](images/holographicremotingplayer-diag.png)

* **Render** - 远程处理播放器在上一秒呈现的帧数。 请注意，这独立于通过网络到达的帧数， (**视频帧) 。** 显示呈现帧之间最后一秒的平均/最大呈现增量时间（以毫秒为单位）。

* **视频帧** - 显示的第一个数字是跳过的视频帧，第二个数字是重复使用的视频帧，第三个数字是接收的视频帧。 所有数字都表示过去一秒钟的计数。
    * ```Received frames``` 是最后一秒到达的视频帧数。 在正常情况下，这应为 60，但如果不是，则表明任一帧由于网络问题而被删除，或者远程/远程端不会生成具有预期速率的帧。
    * ```Reused frames``` 是在过去一秒中多次使用的视频帧计数。 例如，如果视频帧延迟到达，播放器的呈现循环仍呈现帧，但需要重用已用于上一帧的视频帧。
    * ```Skipped frames``` 是播放器的呈现循环尚未使用的视频帧计数。 例如，网络抖动可能会影响到达的视频帧不再均匀分布。 例如，如果有些延迟，而另一些则及时到达，导致它们在 60 Hz 上运行时不再有 16.66 毫秒的增量。 播放器呈现循环的两个刻度之间可能会到达多个帧。 在这种情况下，播放器 *会跳过* 一个或多个帧，因为它应始终显示最新接收的视频帧。

    >[!NOTE]
    >当面临网络抖动时，跳过的帧和重复使用的帧通常相同。 相反，如果只看到跳过的帧，则表明播放器未达到其目标帧速率。 在这种情况下，在诊断问题时，应关注最长呈现增量时间。

* **视频帧增量** - 过去一秒接收的视频帧之间的最小/最大增量。 如果网络抖动导致问题，此数字通常与跳过/重复使用的帧相关联。
* **延迟** - 过去一秒的平均周转时间（以毫秒为单位）。 此上下文中的恢复是指从 HoloLens 向远程/远程端发送姿势/传感器数据到在显示器上显示该姿势/遥测数据的视频帧HoloLens的时间。
* **丢弃的视频帧** 数 - 过去一秒和建立连接后丢弃的视频帧数。 丢弃的视频帧的主要原因是视频帧未按顺序排列，因此需要丢弃，因为已有较新的视频帧。 这类似于 *丢弃的帧* ，但原因在远程处理堆栈中较低级别。 丢弃的视频帧仅在网络状况不佳的情况下才应被丢弃。

在主屏幕上，可以说 **"禁用诊断"** 以关闭诊断。

## <a name="pc-system-requirements"></a>电脑系统要求
* 电脑 **必须运行** Windows 10 周年更新或更高版本。
* 建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。
* 建议通过以太网将电脑连接到网络，以减少无线跃点的数量。

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [HoloLens (第一代) ：添加全息远程处理](add-holographic-remoting.md)
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)