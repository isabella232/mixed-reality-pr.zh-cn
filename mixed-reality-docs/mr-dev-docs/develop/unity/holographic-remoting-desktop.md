---
title: 桌面应用中的全息远程处理
description: 了解如何在桌面应用程序中通过 OpenXR 使用全息远程处理。
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，增加现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624314"
---
# <a name="holographic-remoting-in-desktop-app"></a>桌面应用中的全息远程处理

> [!NOTE]
> 0.1.3 包版本中添加了 Windows 独立应用远程处理支持。
> 从版本0.1.3 起，此功能不支持 UWP 生成。

1. 按照[全息远程处理设置](openxr-supported-features.md#holographic-remoting-setup)中的步骤操作
2. 打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框。 另外，取消选中 " **启动时初始化 XR"**：

    ![项目设置面板的屏幕截图在 Unity 编辑器中打开，并取消选中 "启动时初始化 XR"](images/openxr-features-img-02-app.png)

3. 展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"
4. 选中 " **全息应用远程处理** " 复选框：

    ![启用了应用远程处理的 Unity 编辑器中打开的项目设置面板的屏幕截图](images/openxr-features-img-03-app.png)

5. 接下来，编写一些代码以设置远程处理配置和触发器 XR 初始化。 使用 [混合现实 OpenXR 插件](openxr-getting-started.md#hololens-2-samples) 分发的示例应用包含 AppRemoting.cs，其中显示了在运行时连接到特定 IP 地址的示例方案。 此时，将示例应用程序部署到本地计算机，将使用 "连接" 按钮显示 IP 地址输入字段。 键入 IP 地址并单击 "连接" 将初始化 XR 并尝试连接到目标设备：

    ![示例应用显示示例应用远程处理 UI 的屏幕截图](images/openxr-sample-app-remoting.png)

6. 若要编写自定义连接代码，请使用已填充的进行调用 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。 该示例应用在检查器中公开此内容，并演示如何在文本字段中填充 IP 地址。 调用 `Connect` 将设置配置并自动初始化 XR，这就是为什么必须将其称为协同程序的原因：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 运行时，可以使用 API 获取当前连接状态 `AppRemoting.TryGetConnectionState` ，还可以选择断开连接，并使用取消初始化 XR `AppRemoting.Disconnect()` 。 这可用于断开连接并重新连接到同一应用会话中的其他设备。 示例应用提供了一个 tappable 多维数据集，该多维数据集会在点击时断开远程处理会话。

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