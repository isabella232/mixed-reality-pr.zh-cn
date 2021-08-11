---
title: Unreal 中的流式传输
description: 了解如何将 Unreal 应用流式传输到 HoloLens 2，包括流式传输限制和命令行选项。
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 流式传输, 电脑, 全息应用远程处理, 全息远程处理播放器, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 4b3be99f699c7c1d40d3ea98aacecde6f60e4d2db759448f84c820a43d89bb0a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218850"
---
# <a name="streaming-in-unreal"></a>Unreal 中的流式传输

从电脑流式传输到 HoloLens 提供了两大优势： 
* 它使混合现实应用可以利用电脑的计算能力。 
* 它有助于加快开发迭代的时间。 

首先，需要将[全息远程处理播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)下载到 HoloLens 设备。 通过全息远程处理播放器，应用可以从以下来源直接流式传输到 HoloLens 上的远程处理播放器：

* Unreal Engine 编辑器
* 打包的 Windows 可执行文件 

进行流式传输时，你可以访问几乎所有相同的 HoloLens 功能，就像你在设备上运行应用程序时一样。 这包括[手关节跟踪](unreal-hand-tracking.md)（如果使用的是 HoloLens 2）、[空间映射](unreal-spatial-mapping.md)和[空间定位点](unreal-spatial-anchors.md)，但此[列表](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)上的功能除外。 

> [!NOTE]
> * 流式传输的质量严重依赖于 wifi 网络的强度。
> * 自动为全息远程处理播放器启用所有功能。 如果你发现有一项功能需要用户授权（例如眼动跟踪）才能用于流媒体，但在设备上运行时确不需要它，请检查确保已在项目设置下启用适当的功能。

### <a name="streaming-limitations"></a>流式传输限制

不能通过流式传输使用手部网格、HoloLens 摄像头和系统键盘。 请注意，可通过要作为流式传输源的电脑的麦克风获取流应用的语音输入。

#### <a name="openxr"></a>OpenXR

在 OpenXR 上运行的 Unreal 4.26 支持流式传输到全息远程播放器版本 2.4.0+。 2\.4.0 中的 OpenXR 流式传输缺少对空间映射和空间定位点的支持。 

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>源</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>沉浸式头戴显示设备</strong></td>
    </tr>
     <tr>
        <td>Unreal 编辑器</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Windows 包</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>从 Unreal 编辑器进行流式传输

作为开发人员，你会发现从 Unreal 编辑器流式传输到 HoloLens 设备在测试时会提供很大的好处，也就是说，你无需再等待应用生成和部署完成后才尝试更新。

教程系列中提供了[从 Unreal 编辑器流式传输](tutorials/unreal-uxt-ch6.md#device-only-streaming)的详细说明。

## <a name="streaming-from-a-packaged-windows-executable"></a>从打包的 Windows 可执行文件进行流式传输

在 Unreal 4.25.1 及更高版本中，可以将应用从打包的 Windows 可执行文件流式传输到 HoloLens 2 设备： 

1. 转到编辑器菜单中的“文件”>“包项目”>“Windows”。 
    * 选择要保存包的位置，然后选择“选择文件夹”。

2. 包生成完成后，请打开 HoloLens 2 上的“全息远程处理播放器”，并记下 IP 地址。 
3. 使“全息远程处理播放器”保持打开状态，然后使用命令行提示符执行以下操作： 
    * 将 cd 插入到保存包的本地目录。
    * 输入以下命令：`<App Name>.exe -vr -HoloLensRemoting=<IP Address>`

> [!NOTE]
> 项目设置中的应用程序名称应自动用于创建 Windows 包。 如果名称因某些原因而有所不同，请在命令提示符下使用 Windows 可执行文件名称。

按 Enter 键，随即将看到应用程序开始进行流式传输了！

### <a name="command-line-options"></a>命令行选项

可在下表中找到 Unreal 引擎 4.26+ 中用于从每个平台进行流式传输的其他命令行选项。 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a>另请参阅

* [全息远程处理版本历史记录](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [编写自定义全息远程处理播放器应用](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [使用全息远程处理建立安全连接](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)