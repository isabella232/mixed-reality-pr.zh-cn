---
title: 全息远程播放器
description: 了解全息远程处理播放机，并从 PC 实时将全息内容流式传输到 HoloLens。
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/27/2021
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，诊断，性能
ms.openlocfilehash: 1e286612035a34c1bac174a620c350a91eb2b0fd59c3e808fe3a99368e03f43c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217135"
---
# <a name="holographic-remoting-player"></a>全息远程播放器

[了解全息远程处理的基础知识。](platform-capabilities-and-apis/holographic-remoting-overview.md)

>[!IMPORTANT]
>HoloLens 2 的全息远程处理是一种主要版本更改。 [适用于 **HoloLens (1 代)** 的远程应用程序](add-holographic-remoting.md)必须使用 **NuGet 包版本 1.x** 和 [ **HoloLens 2** 的远程应用程序](holographic-remoting-create-remote-wmr.md)**必须使用1.x。** 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens (第一代) ，反之亦然。

[全息远程处理播放器](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40)是一种附属应用，用于连接到支持全息远程处理的 PC 应用和游戏。 播放机适用于 HoloLens (第一代) 和 HoloLens 2。  支持全息远程远程处理 HoloLens 的 PC 应用需要更新为支持 HoloLens 2 的全息远程处理。 如果对支持的版本有任何疑问，请与应用提供商联系。

>[!TIP]
>从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始，全息远程处理播放机也可用于运行[Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)Windows pc。

>[!TIP]
>从版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 开始，可以创建使用 [OpenXR API](../native/openxr.md) 的远程应用。 若要开始，请参阅 [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)。

## <a name="connecting-to-the-holographic-remoting-player"></a>连接到全息远程处理播放器

按照应用的说明连接到全息远程处理播放器。 需要输入 HoloLens 设备的 IP 地址，你可以在远程处理播放机的主屏幕上看到该地址，如下所示：

![全息远程播放器](images/holographicremotingplayer.png)

看到主屏幕时，你会知道未连接应用。

全息远程处理连接 **未加密**。 你应始终通过你信任的安全 Wi-Fi 连接使用全息远程处理。

## <a name="quality-and-performance"></a>质量和性能

经验的质量和性能会因三个因素而异：
* **正在运行的全息体验** -呈现高分辨率或高度详细内容的应用可能需要更快的 PC 或更快的无线连接。
* **你的电脑硬件** -你的电脑需要能够以60帧/秒的速度运行和编码全息体验。 对于图形卡，我们通常建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高。 同样，你的特定体验可能需要更高或更低端的卡。
* **Wi-Fi 连接** -你的全息体验通过 wi-fi 进行流式处理。 使用具有低拥塞的快速网络来最大程度地提高质量。 使用通过以太网电缆而不是 Wi-fi 连接的 PC，还可以提高质量。

## <a name="diagnostics"></a>诊断

若要测量连接的质量，请在全息远程处理播放机的主屏幕上说 **"启用诊断"** 。 启用诊断后，请在 **HoloLens (第一代)** ，应用将向你显示：

* **FPS** -远程处理播放机每秒接收和呈现的呈现帧的平均数目。 理想为 60 FPS。
* **延迟**-帧从 PC 到 HoloLens 所需的平均时间量。 越低越好。 这在很大程度上取决于 Wi-Fi 网络。

**HoloLens 2** 应用将显示：

![全息远程处理播放器诊断](images/holographicremotingplayer-diag.png)

* **Render** -远程处理播放机在上一秒内呈现的帧数。 请注意，这与通过网络到达的帧数量无关 (请参阅 **视频帧**) 。 显示呈现的帧间最后一秒的平均/最大呈现增量时间（以毫秒为单位）。

* **视频帧** -将跳过显示的第一个数字视频帧，第二个显示的是视频帧，第三个是接收视频帧。 所有数字表示上一秒的计数。
    * ```Received frames``` 是在上一秒钟到达的视频帧的数目。 正常情况下，这应为60，但如果不是，则指示由于网络问题而导致的帧被丢弃，或者远程/远程端不产生具有预期速率的帧。
    * ```Reused frames``` 是在上一秒钟内多次使用的视频帧的计数。 例如，如果视频帧晚到达，播放机的呈现循环仍将呈现一个帧，但需要 *重复* 使用它已用于前一帧的视频帧。
    * ```Skipped frames``` 视频帧的计数，播放机的呈现循环尚未使用该计数。 例如，网络抖动可能会造成视频帧无法均匀地分布。 例如，如果有一些延迟，而另一些时间到达时，则在 60 Hz 运行时，它们不会再出现16.66 毫秒的增量。 在播放机的呈现循环的两个刻度之间，可能会有多个帧到达。 在这种情况下，播放机将 *跳过* 一个或多个帧，因为应该始终显示最近收到的视频帧。

    >[!NOTE]
    >当网络抖动时，跳过和重复使用的帧通常是相同的。 相反，如果您只看到跳过的帧，则表明播放机不会达到其目标帧速率。 在这种情况下，应注意诊断问题时的最大渲染增量时间。

* **视频帧增量** -上一秒收到的视频帧之间的最小/最大增量。 当网络抖动导致的问题时，此数字通常与跳过/重复使用帧关联。
* **延迟** -上一秒的平均周转时间（以毫秒为单位）。 在此上下文中，"周转时间" 指的是将姿势/传感器数据从 HoloLens 发送到远程/远程端，直到显示 HoloLens 显示的该姿势/遥测数据的视频帧。
* **丢弃的视频帧** -上一秒内丢弃的视频帧的数量，自建立连接后被丢弃的视频帧的数目。 被丢弃的视频帧的主要原因是，视频帧未按顺序到达，出于此原因，需要将其丢弃，因为已经有一个新的。 这类似于 *丢弃的帧* ，但原因是远程堆栈中的较低级别。 仅在出现错误的网络条件下，才需要弃用的视频帧。

在主屏幕上，可以说 **"禁用诊断"** 以关闭诊断。

## <a name="pc-system-requirements"></a>PC 系统要求
* 你的电脑 **必须** 运行 Windows 10 周年更新或更新版本。
* 建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。
* 建议你通过以太网将电脑连接到网络，以减少无线跃点的数量。

## <a name="see-also"></a>另请参阅
* [第一代)  (HoloLens：添加全息远程处理](add-holographic-remoting.md)
* [使用 Windows Mixed Reality api 编写全息远程处理远程应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)