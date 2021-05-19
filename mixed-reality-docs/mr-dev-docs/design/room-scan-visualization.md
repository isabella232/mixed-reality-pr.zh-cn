---
title: 房间扫描可视化
description: 需要空间映射的应用程序使用设备跨时间和跨会话收集数据。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，应用模式，设计，HoloLens，房间扫描，空间映射，网格，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143613"
---
# <a name="room-scan-visualization"></a>房间扫描可视化

需要空间映射的应用程序依赖于设备跨时间和跨会话收集数据。 映射数据的完整性和质量取决于许多因素，包括用户的探索量、自浏览以来经过的时间，以及设备和门等对象是否在设备扫描区域后移动。

为了确保有用的空间映射数据，应用程序开发人员有多种选择：
* 依赖于可能已收集的内容。 此数据最初可能是不完整的。
* 要求用户使用布隆手势进入 Windows Mixed Reality 主页，并浏览他们希望用于体验的领域。 他们可以使用分流来确认设备是否知道所有必要的区域。
* 在自己的应用程序中生成自定义浏览体验。

在所有这些情况下，系统会存储浏览过程中收集的实际数据，而应用程序无需执行此操作。 若要查看房间扫描视觉对象的运行情况，请查看下面 [的设计全息影像-空间感知]() 视频演示：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

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

应用程序可以在体验开始时分析空间映射数据，判断他们是否希望用户执行额外的步骤来提高其完整性和质量。 如果分析表明质量应该提高，开发人员应提供一种可视化对象，使其在世界上叠加以指示：
* 用户附近的用户总数需要成为体验的一部分
* 用户应在何处着手改善数据

用户不知道什么是 "良好" 扫描。 如果系统要求他们评估扫描（平面度、距离实际墙的距离等）时，需要显示或告知他们要查找什么。 开发人员应实现反馈循环，包括在扫描或探索阶段刷新空间映射数据。

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
* 无需在应用程序中提前构建单独的扫描或浏览体验。
* 尽管有一些延迟，但现实世界对象的移动可能会反映出来。

**弊端**
* 实现主要体验的复杂性更高。
* 额外的图形和物理学处理可能产生的开销，因为需要对这些系统进行增量引入。
* 高功率、热量和 CPU 影响。

此方法的一种很好的情况是，全息影像应与移动对象进行交互，例如，地面驱动器上的一只是处于打开或关闭状态的全息汽车。

## <a name="see-also"></a>另请参阅

* [空间映射](spatial-mapping.md)
* [坐标系统](coordinate-systems.md)
* [空间音效设计](spatial-sound-design.md)