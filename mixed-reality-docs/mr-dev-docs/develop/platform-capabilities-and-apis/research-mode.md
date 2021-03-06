---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流 (深度、环境跟踪和反射率) 。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens，HoloLens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237128"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

在 HoloLens (第一代) 设备上引入了研究模式，以提供对关键传感器的访问权限，特别是针对不打算部署的研究应用程序。  HoloLens 2 的研究模式保留了 HoloLens 1 的功能，但添加了对以下流的访问权限：

* **可见的轻型环境跟踪相机** -系统用于 head 跟踪和地图构建的灰色缩放相机。
* **深度相机** –在两种模式下运行：  
    + AHAT，高频 (45 FPS) 用于手动跟踪的近深度感应。 不同于第一个版本的短整型模式，AHAT 提供了超出1米的相位覆盖的伪深度。 
    + 长整型引发、低频率 (1-5 FPS) [空间映射](../../design/spatial-mapping.md)使用的深度感应

* **反射率的两个版本** ： HoloLens 用于计算深度。 这些图像通过红外，并不受环境可见光的影响。

如果使用的是 HoloLens 2，还可以访问下面的其他输入：

* **加速感应** 程序–由系统用来确定沿 X、Y 和 Z 轴和重心的线性加速度。
* **Gyro** –系统用来确定旋转。
* **磁力仪** –系统用于估计绝对方向。

> [!IMPORTANT]
> 研究模式目前为公共预览版。 

![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)<br>
*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*

## <a name="usage"></a>使用情况

研究模式旨在使学术和工业研究人员了解计算机视觉和机器人的字段中的新想法。  它不适合企业环境中部署的应用程序，也不能通过 Microsoft Store 或其他分发渠道提供。

此外，Microsoft 不保证在未来的硬件或操作系统更新中将支持研究模式或等效的功能。 不过，请不要让你使用它来开发和测试新创意！

## <a name="security-and-performance"></a>安全性和性能

即使使用 "调研模式" 功能的应用程序未运行，启用研究模式也比在正常情况下使用 HoloLens 2 的电池电量更多。  启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。  您可以在 [HoloLens 安全常见问题](/hololens/hololens-faq-security)中找到有关设备安全的详细信息。  

## <a name="device-support"></a>设备支持
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>标题跟踪相机</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>IR 相机 & 深度</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>加速计</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>陀螺仪</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>磁力计</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>启用研究模式 (HoloLens 第一代和 HoloLens 2) 

研究模式是开发人员模式的扩展。 在开始之前，需要启用设备的开发人员功能才能访问 "研究模式" 设置： 

* 打开 " **开始" 菜单 > 设置** "，然后选择" **更新**"。
* **为开发人员** 选择并启用 **开发人员模式**。
* **向下滚动** 并启用“设备门户”。

启用开发人员功能后， [连接到设备门户](/windows/uwp/debug-test-perf/device-portal-hololens) 以启用研究模式功能：

* 在 **设备门户** 中转到 "**系统 > 研究模式**"。
* 选择 " **允许访问传感器流**"。
* 从页面顶部的 **Power** menu 项重新启动设备。

重新启动设备后，通过 **设备门户** 加载的应用程序可以访问研究模式流。

![HoloLens 设备门户的研究模式选项卡](images/ResearchModeDevPortal.png)<br>
*HoloLens 设备门户中的研究模式窗口*

> [!IMPORTANT]
> HoloLens 2 的研究模式从版本19041.1364 开始提供。 如果在早期版本中需要访问权限，请注册我们的预览 [体验](/hololens/hololens-insider) 计划。 可以在 " [研究模式 GitHub 存储库](https://github.com/microsoft/HoloLens2ForCV)" 中找到更多详细信息。

### <a name="using-sensor-data-in-your-apps"></a>在应用中使用传感器数据

应用程序可以访问传感器流数据，其方式与 [媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk) 访问照片和视频摄像机流的方式相同。 

适用于 HoloLens 开发的所有 Api 在研究模式下也可用。 具体而言，应用程序在每个传感器帧捕获时间确切地了解 HoloLens 在6DoF 空间的位置。

我们有使用 [内部和 extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)和记录流的示例应用程序，显示研究模式流访问：
* [HoloLens (第一代) ](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>支持

对于 HoloLens (第一代) ，请使用 HoloLensForCV 存储库中的 [问题跟踪](https://github.com/Microsoft/HololensForCV/issues) 器发布反馈并跟踪已知问题。

对于 HoloLens 2，请使用 HoloLens2ForCV 存储库中的 [问题跟踪](https://github.com/microsoft/HoloLens2ForCV/issues) 程序发布反馈并跟踪已知问题。

## <a name="see-also"></a>请参阅

* [Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub 存储库](https://github.com/microsoft/HoloLens2ForCV)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)