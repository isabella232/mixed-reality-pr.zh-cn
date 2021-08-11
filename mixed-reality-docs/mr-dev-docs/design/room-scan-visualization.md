---
title: 房间扫描可视化
description: 需要空间映射的应用程序使用设备在一段时间和跨会话收集数据。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、应用模式、设计、HoloLens、房间扫描、空间映射、网格、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens
ms.openlocfilehash: 0ebfbd9a1f07ffd0671d36dcc63dbd5303a2cdbceb906839be9736f43de76937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207825"
---
# <a name="room-scan-visualization"></a>房间扫描可视化

需要空间映射的应用程序依赖于设备在一段时间和跨会话收集数据。 地图数据的完整性和质量取决于许多因素，包括用户已完成的探索量、自探索以来经过的时间，以及设备扫描该区域后，是否移动了设备和门等对象。

为了确保有用的空间映射数据，应用程序开发人员提供了多个选项：
* 依赖于可能已收集的 。 此数据最初可能不完整。
* 要求用户使用布满手势进入Windows Mixed Reality，然后浏览想要用于体验的区域。 他们可以使用无线敲击来确认设备知道所有必要的区域。
* 在其自己的应用程序中构建自定义探索体验。

在所有这些情况下，探索期间收集的实际数据都由系统存储，应用程序无需这样做。 若要了解房间扫描可视化效果的运行，请查看下面的设计全息影像 -**空间** 感知视频演示：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

此视频来自于“设计全息影像”HoloLens 2 应用。在[此处](https://aka.ms/dhapp)下载并享受完整体验。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>房间扫描可视化</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>构建自定义扫描体验

应用程序可能在体验开始时分析空间映射数据，以判断他们是否希望用户执行额外的步骤来提高其完整性和质量。 如果分析表明应提高质量，开发人员应提供可视化效果以覆盖世界，以指示：
* 用户邻近区域的总数量需要成为体验的一部分
* 用户应在何处改进数据

用户不知道什么是"好的"扫描。 如果系统要求他们评估扫描（平面度、距离实际墙的距离等）时，需要显示或告知他们要查找什么。 开发人员应实现反馈循环，包括在扫描或探索阶段刷新空间映射数据。

在许多情况下，最好告诉用户需要执行哪些操作才能获得必要的扫描质量。 例如，查看上限、查看装饰后，等等。

## <a name="cached-versus-continuous-spatial-mapping"></a>缓存空间映射与连续空间映射

空间映射数据是应用程序可以使用的最重数据源数据。 若要避免性能问题（如丢弃的帧或断点）问题，应谨慎使用此数据。

在体验期间主动扫描既有利又有害，因此你需要根据体验决定使用哪种方法。

### <a name="cached-spatial-mapping"></a>缓存的空间映射

如果有缓存的空间映射数据，应用程序通常会拍摄空间映射数据的快照，并在此体验期间使用此快照。

**优点**
* 降低运行体验时系统开销，从而显著提升功率、热性能和 CPU 性能。
* 主体验的更简单实现，因为它不会因空间数据更改而中断。
* 空间数据的任何后期处理（用于物理、图形和其他目的）的一次成本。

**缺点**
* 实际对象或人员的移动不会由缓存的数据反映。 例如，应用程序可能会认为门在现在关闭时打开。
* 可能更多的应用程序内存用于维护数据的缓存版本。

此方法的一个好情况是受控环境或表顶级游戏。

### <a name="continuous-spatial-mapping"></a>连续空间映射

某些应用程序可能依赖于继续扫描来刷新空间映射数据。

**优点**
* 无需在应用程序中预先构建单独的扫描或探索体验。
* 虽然有一些延迟，但实际对象的移动可以通过游戏来反映。

**缺点**
* 主要体验的实现复杂性更高。
* 额外的图形和物理处理的潜在开销，因为更改需要由这些系统以增量方式进行。
* 更高的功率、热和 CPU 影响。

此方法的一个好例子是，全息影像预期会与移动的对象交互，例如，在楼层上驾驶的全息汽车可能需要凹入门，具体取决于它是打开还是关闭。

## <a name="see-also"></a>另请参阅

* [空间映射](spatial-mapping.md)
* [坐标系统](coordinate-systems.md)
* [空间音效设计](spatial-sound-design.md)