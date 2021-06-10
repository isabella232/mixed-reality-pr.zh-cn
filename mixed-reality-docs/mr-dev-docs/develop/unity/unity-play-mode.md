---
title: Unity 播放模式
description: 了解如何在 Unity 编辑器中使用播放模式在设备上预览应用程序更改，而无需部署应用。
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity， 远程处理， 全息远程处理， 全息远程处理播放器， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity 播放模式
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547095"
---
# <a name="unity-play-mode"></a>Unity 播放模式

处理 Unity 项目的一种快速方法就是使用"播放模式"，该模式在电脑上的 Unity 编辑器中本地运行应用。 Unity 使用全息远程处理提供在真实 HoloLens 设备上预览内容的快速方法。 播放模式还可以与连接到开发电脑Windows Mixed Reality头戴显示设备一起使用。

## <a name="holographic-remoting-setup"></a>全息远程处理设置

1. 首先，需要 [从](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 应用程序上的应用程序安装全息远程Microsoft Store应用HoloLens 2
2. 在 HoloLens 2 运行 Holographic Remoting Player 应用，你将看到要连接到的版本号和 IP 地址
    * 需要 v2.4 或更高版本来使用 OpenXR 插件

    ![在 HoloLens 中运行的全息远程处理播放器的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 编辑器播放模式下的全息远程处理

在项目中生成 UWP Unity Visual Studio，然后打包并部署到 HoloLens 2 设备可能需要一些时间。 一种解决方案是启用全息编辑器远程处理功能，该功能允许使用"播放"模式将 C# 脚本直接调试到HoloLens 2设备。 此方案可避免生成 UWP 包以及将其部署到远程设备的开销。

1. 按照全息远程 [处理设置中的步骤操作](#holographic-remoting-setup)
2. 打开 **Windows > XR > OpenXR 编辑器远程处理**：

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. 输入从全息远程处理应用获取的 IP 地址，然后选择" **启用编辑器远程处理"**

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了"功能"](images/openxr-features-img-03.png)

现在，可以单击"播放"按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用中。 还可以将 [脚本Visual Studio Unity，](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 以在播放模式下调试 C# 脚本。

> [!NOTE]
> 从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。  此功能将在未来版本中推出。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全息远程处理的 Unity 播放模式

使用全息远程处理，可以在 HoloLens 上体验应用，同时该应用在电脑上的 Unity 编辑器中运行。 凝视、手势、语音和空间映射输入从 HoloLens 发送到电脑。 然后，渲染的帧将发送回 HoloLens。 这是在不生成和部署完整项目的情况下快速调试应用的一种好方法。

[!INCLUDE[](includes/unity-play-mode.md)]

全息远程处理需要快速的电脑和Wi-Fi连接。 可以在全息远程处理播放器 [文档中找到](../platform-capabilities-and-apis/holographic-remoting-player.md) 更多详细信息。

为获得最佳结果，请确保应用正确设置 [焦点](focus-point-in-unity.md)。 这有助于全息远程处理以最佳方式使场景适应无线连接的延迟。

## <a name="see-also"></a>另请参阅

* [全息远程播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)
