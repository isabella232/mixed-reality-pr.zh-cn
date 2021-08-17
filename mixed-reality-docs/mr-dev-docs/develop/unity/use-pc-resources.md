---
title: 使用 PC 资源通过全息远程处理为应用程序提供支持
description: 使用 PC 资源，而不是依靠 HoloLens 的板上处理能力，使用全息远程处理为应用程序提供支持
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实 Toolkit，增加的现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面，预览，调试
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203833"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>使用 PC 资源通过全息远程处理为应用程序提供支持

本文介绍了全息远程处理的以下用例：

-  **你希望电脑的资源可以为应用程序提供支持，而不是依赖于 HoloLens 的板资源**：可以创建和构建包含全息远程处理功能的应用程序。 用户遇到 HoloLens 上的应用程序，但应用程序实际在 pc 上运行，这使应用程序能够利用电脑更强大的资源。 如果你的应用程序具有高分辨率资产或型号，并且你不希望帧速率受到影响，这会特别有用。 我们称之为全息远程 _处理远程应用_。 HoloLens 中的输入（"注视"、"手势"、"语音" 和 "空间映射"）将发送到 PC，其中的内容在虚拟沉浸式视图中呈现。 然后，将呈现的帧发送到 HoloLens。

此类全息远程处理还适用于 Windows Mixed Reality (WMR) 沉浸式耳机。 例如，如果你的 WMR 耳机连接到背包 PC，并且你想要将应用从功能更强大的电脑流式传输到背包 PC，这可能很有用。

若要了解有关全息远程处理的详细信息，请参阅 [全息远程处理概述](../platform-capabilities-and-apis/holographic-remoting-overview.md)

请注意，如果 [想要在开发过程中预览和调试应用，](preview-and-debug-your-app.md)还可以使用全息远程处理。

## <a name="set-up-holographic-remoting"></a>设置全息远程处理

若要使用全息远程处理，需要从 HoloLens 2 上的 Microsoft Store 安装[全息远程处理播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)应用。 如下所述，下载并运行应用后，你将看到要连接到的版本号和 IP 地址。 **你将需要2.4 或更高版本才能使用 OpenXR 插件**。

全息远程处理需要快速的 PC 和 Wi-Fi 的连接。 可以在上面链接的 "全息远程处理播放机" 文章中找到更多详细信息。

![在 HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

1. 在菜单栏上，选择 "**编辑 > Project 设置**"。
1. 在左侧列中，选择 " **XR 插件管理**"。
1. 在 " **XR 插件管理**" 部分中，选择 **Microsoft HoloLens 功能组**"和"**全息远程处理远程应用功能组**"。
1. 取消选中 **"启动时初始化 XR"**：

    ![项目设置面板的屏幕截图在 Unity 编辑器中打开，并取消选中 "启动时初始化 XR"](images/001-openxr-features.png)

1. 编写一些代码以设置远程处理配置和触发器 XR 初始化。 使用 [混合现实 OpenXR 插件](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) 分发的示例应用包含 AppRemoting，其中显示了在运行时连接到特定 IP 地址的示例方案。 此时，将示例应用程序部署到本地计算机，将使用 "连接" 按钮显示 IP 地址输入字段。 键入 IP 地址，然后单击 "连接" 将初始化 XR 并尝试连接到目标设备：

    ![示例应用显示示例应用远程处理 UI 的屏幕截图](images/openxr-sample-app-remoting.png)

1. 若要编写自定义连接代码，请使用已填充的进行调用 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。 该示例应用在检查器中公开此内容，并演示如何在文本字段中填充 IP 地址。 调用 `Connect` 将设置配置并自动初始化 XR，这就是为什么必须将其称为协同程序的原因：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. 运行时，可以使用 API 获取当前连接状态 `AppRemoting.TryGetConnectionState` ，还可以选择断开连接，并使用取消初始化 XR `AppRemoting.Disconnect()` 。 这可用于断开连接并重新连接到同一应用会话中的其他设备。 示例应用提供了一个 tappable 多维数据集，该多维数据集会在点击时断开远程处理会话。

## <a name="migrate-from-previous-holographic-remoting-apis"></a>从以前的全息远程处理 Api 迁移

若要了解有关全息远程处理的详细信息，请参阅 [全息远程处理概述](../platform-capabilities-and-apis/holographic-remoting-overview.md)

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. HolographicRemoting

在 [Unity 文档](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)的示例代码中：

| XR.WSA.HolographicRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A：调用时自动发生 `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR.WindowsMR.WindowsMRRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | `AppRemoting.Connect`通过 `RemotingConfiguration` 结构传入 |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>另请参阅

* [全息远程播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [通过全息远程处理和播放模式预览和调试应用程序](preview-and-debug-your-app.md)
* [教程： PC 全息远程处理入门](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程电脑应用程序](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
