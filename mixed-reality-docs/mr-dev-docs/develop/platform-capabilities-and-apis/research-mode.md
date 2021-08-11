---
title: HoloLens 研究模式
description: 使用研究模式HoloLens，应用程序可以访问关键设备传感器流 (深度、环境跟踪和 IR 反射率) 。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式， cv， rs4， 计算机视觉， 研究， HoloLens， HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193675"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

第一代HoloLens (设备上引入了) 模式，以授予对关键传感器的访问权限，特别是用于不适合部署的研究应用程序。  HoloLens 2研究模式保留 HoloLens 1 的功能，但添加了对以下流的访问：

* **可见光环境跟踪相机** - 系统用于头部跟踪和地图构建的灰度相机。
* **深度相机** – 在两种模式下运行：  
    + AHAT，高频率 (45 FPS) 用于手部跟踪的近深度运动。 与第一个版本的短引发模式不同，AHAT 提供伪深度，其相位包装超过 1 米。 
    + 空间映射使用的长 (1-5 FPS) 远深度 [探测](../../design/spatial-mapping.md)

* **IR 反射流的两** 个版本 - 由HoloLens计算深度。 这些图像受光线影响，不受环境可见光的影响。

如果使用的是 HoloLens 2，则还可以访问以下其他输入：

* **加速** 计 – 由系统用来确定沿 X、Y 和 Z 轴的线性加速度和加速度。
* **Gyro** – 由系统用于确定旋转。
* **磁力** 计 – 由系统用来估计绝对方向。

> [!IMPORTANT]
> 研究模式目前为公共预览版。 

![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)<br>
*测试应用程序的混合现实捕获，其中显示了研究模式下提供的八个传感器流*

## <a name="usage"></a>使用情况

研究模式专为学术和行业研究人员设计，这些研究人员在机器人和机器人领域计算机视觉新想法。  它不适用于部署在企业环境中的应用程序，或者通过 Microsoft Store或其他分发渠道提供的应用程序。

此外，Microsoft 不保证研究模式或等效功能将在未来硬件或 OS 更新中受支持。 但是，请不要阻止你使用它来开发和测试新想法！

## <a name="security-and-performance"></a>安全性和性能

启用研究模式比在正常情况下使用HoloLens 2，即使使用研究模式功能的应用程序未运行，也使用更多电池电源。  启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。  可以在安全常见问题解答 中找到有关设备HoloLens[详细信息](/hololens/hololens-faq-security)。  

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
        <td>头部跟踪相机</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>深度& IR 相机</td>
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

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>启用第一代 (HoloLens研究模式HoloLens 2) 

研究模式是开发人员模式的扩展。 在启动之前，需要启用设备的开发人员功能才能访问研究模式设置： 

* 打开 **"开始菜单> 设置** 并选择"更新 **"。**
* 选择 **"开发人员"** 并启用 **"开发人员模式"。**
* **向下滚动** 并启用“设备门户”。

启用开发人员功能后， [连接到设备门户以](/windows/uwp/debug-test-perf/device-portal-hololens) 启用研究模式功能：

* 在中 **> System 设备门户****研究模式**。
* 选择 **"允许访问传感器流"。**
* 从页面顶部的 **"电源** "菜单项重启设备。

重启设备后，通过 设备门户加载的应用程序 **可以访问研究** 模式流。

!["研究模式"选项卡HoloLens 设备门户](images/ResearchModeDevPortal.png)<br>
*"研究模式"窗口HoloLens 设备门户*

> [!IMPORTANT]
> 从内部版本 19041.1364 开始HoloLens 2研究模式。 如果需要在早期版本中访问，请注册 Insider [Preview](/hololens/hololens-insider) 计划。 可以在研究模式和存储库 找到[GitHub的详细信息](https://github.com/microsoft/HoloLens2ForCV)。

### <a name="using-sensor-data-in-your-apps"></a>在应用中使用传感器数据

应用程序可以像访问照片和视频相机流 [媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk) 访问传感器流数据。 

所有适用于开发HoloLens API 也以研究模式提供。 具体而言，应用程序知道每个传感器帧捕获HoloLens 6DoF 空间的 6DoF 空间。

我们的示例应用程序显示了研究模式流访问，使用内部函数 [和外部](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)函数 ，并记录流：
* [HoloLens (第一代) ](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>支持

对于HoloLens (第一代) ，请使用 HoloLensForCV 存储库中的问题跟踪器发布反馈并跟踪已知问题。 [](https://github.com/Microsoft/HololensForCV/issues)

对于HoloLens 2，请使用 HoloLens2ForCV 存储库中的问题跟踪器发布反馈并跟踪已知问题。 [](https://github.com/microsoft/HoloLens2ForCV/issues)

## <a name="see-also"></a>另请参阅

* [Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV GitHub存储库](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub存储库](https://github.com/microsoft/HoloLens2ForCV)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)