---
title: Unity 播放模式
description: 了解如何在 Unity 编辑器中使用播放模式在不部署应用的情况下预览设备上的应用程序更改。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，远程处理，全息远程处理，全息远程处理播放器，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity 播放模式
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333393"
---
# <a name="unity-play-mode"></a>Unity 播放模式

处理 Unity 项目的一种快速方法是使用 "播放模式"，该模式在计算机上的 Unity 编辑器中本地运行你的应用程序。 Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。 播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。

## <a name="holographic-remoting-setup"></a>全息远程处理安装

1. 首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址
    * 你需要使用版本2.4 或更高版本才能使用 OpenXR 插件

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 编辑器播放模式下的全息远程处理

在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。 一种解决方案是启用全息编辑器远程处理功能，该功能使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备。 此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。

1. 按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作
2. 打开 **Windows > XR > OpenXR 编辑器远程处理**：

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. 输入从全息远程处理应用获取的 IP 地址，然后选择 "**启用编辑器远程处理**"

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。 还可以将 [脚本Visual Studio Unity，](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 以在播放模式下调试 C# 脚本。

> [!NOTE]
> 从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。  此功能将在未来版本中推出。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全息远程处理的 Unity 播放模式

使用全息远程处理，可以在 HoloLens 上体验应用，同时该应用在电脑上的 Unity 编辑器中运行。 凝视、手势、语音和空间映射输入从 HoloLens 发送到电脑。 然后，渲染的帧将发送回 HoloLens。 这是在不生成和部署完整项目的情况下快速调试应用的一种好方法。
1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
2. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
3. 在 Unity 中，转到 **"窗口"** 菜单，展开 **XR** 子菜单，然后选择"**全息仿真"。**
4. 将 **仿真模式设置为****"远程"到"设备"。**
5. 对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。
6. 选择“**连接**”。 应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。
7. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。

全息远程处理需要快速的电脑和Wi-Fi连接。 可以在全息远程处理播放器 [文档中找到](../platform-capabilities-and-apis/holographic-remoting-player.md) 更多详细信息。

为获得最佳结果，请确保应用正确设置 [焦点](focus-point-in-unity.md)。 这有助于全息远程处理以最佳方式使场景适应无线连接的延迟。

## <a name="see-also"></a>另请参阅
* [全息远程播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)
