---
title: Unity 中的全息远程处理
description: 了解如何在桌面应用中使用全息远程处理，以及如何在 Unity 播放模式下使用 OpenXR。
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实 Toolkit，增加的现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面
ms.openlocfilehash: 0b18bf4a187190da3ef9d17fd87f2c42feaa271210345330887ce618b49a0442
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192168"
---
# <a name="holographic-remoting-in-unity"></a>Unity 中的全息远程处理

> [!NOTE]
> Windows0.1.3 包版本中添加了独立应用远程处理支持。
> 从版本0.1.3 起，此功能不支持 UWP 生成。

[了解全息远程处理的基础知识。](../platform-capabilities-and-apis/holographic-remoting-overview.md)

可以使用全息远程处理实时将全息内容流式传输到 HoloLens 2。 这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。 

在开始之前，请务必了解 Unity 中的两个主要选项：
* **Unity 播放模式下的全息远程处理**：在计算机上以播放模式在 unity 编辑器中本地运行你的应用，以便在 HoloLens 2 上快速预览你的内容。 播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。
* **来自 unity 生成文件的全息远程处理**：从已导出到桌面的 unity 全息远程处理远程应用程序运行你的应用程序到你的 HoloLens 2。 如果你的应用程序具有高分辨率资产或型号，这会很有帮助。桌面 GPU 在获取到 HoloLens 2 之前处理渲染。

## <a name="holographic-remoting-setup"></a>全息远程处理安装

无论采用哪种方式进行全息远程处理，都需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用](https://www.microsoft.com/store/productId/9NBLGGH4SV40)。

下载后，在您的 HoloLens 2 上运行全息远程处理播放器应用程序，您将看到要连接到的版本号和 IP 地址。 **你将需要2.4 或更高版本才能使用 OpenXR 插件**。

![在 HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>采用全息远程处理的 Unity 播放模式

[!INCLUDE[](includes/unity-play-mode.md)]

全息远程处理需要快速的 PC 和 Wi-Fi 的连接。 可以在 [全息远程处理播放机](../platform-capabilities-and-apis/holographic-remoting-player.md) 文档中找到更多详细信息。

为了获得最佳结果，请确保应用正确设置了 [焦点](focus-point-in-unity.md)。 这有助于全息远程处理将场景调整到无线连接的延迟。

## <a name="holographic-remoting-from-a-remote-application"></a>从远程应用程序进行全息远程处理

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

### <a name="migration-from-previous-apis"></a>从以前的 Api 迁移

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
* [教程： PC 全息远程处理入门](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程电脑应用程序](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
