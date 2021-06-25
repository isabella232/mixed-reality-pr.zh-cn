---
title: 桌面应用中的全息远程处理
description: 了解如何通过 OpenXR 在桌面应用中使用全息远程处理。
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr， unity， hololens， hololens 2， 混合现实， MRTK， 混合现实工具包， 增强现实， 虚拟现实， 混合现实头戴显示设备， 学习， 教程， 入门， 全息远程处理， 桌面
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906723"
---
# <a name="holographic-remoting-in-desktop-app"></a>桌面应用中的全息远程处理

> [!NOTE]
> 0.1.3 包版本中添加了 Windows 独立应用远程处理支持。
> 从版本 0.1.3 开始，此功能不支持 UWP 生成。

1. 按照全息远程 [处理设置中的步骤操作](unity-play-mode.md#holographic-remoting-setup)
2. 打开 **"编辑>项目** 设置"，导航到 **"XR****插件管理"，并** 选中"Windows Mixed Reality功能集"框。 此外，取消 **选中"启动时初始化 XR"：**

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中未选中"启动时初始化 XR"](images/openxr-features-img-02-app.png)

3. 展开 **"OpenXR"下的"功能"部分**，然后选择"**全部显示"** 
4. 选中" **全息应用远程处理"** 复选框：

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中启用了应用远程处理](images/openxr-features-img-03-app.png)

5. 接下来，编写一些代码来设置远程处理配置并触发 XR 初始化。 使用混合现实 [OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) 插件分发的示例应用包含 AppRemoting.cs，其中显示了在运行时连接到特定 IP 地址的示例方案。 此时，将示例应用部署到本地计算机将显示 IP 地址输入字段和连接按钮。 键入 IP 地址并单击"连接"将初始化 XR 并尝试连接到目标设备：

    ![显示示例应用远程处理 UI 的示例应用的屏幕截图](images/openxr-sample-app-remoting.png)

6. 若要编写自定义连接代码，请 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` 用填充的 调用 `RemotingConfiguration` 。 示例应用在检查器中公开这一点，并演示如何从文本字段填充 IP 地址。 调用 `Connect` 将设置配置并自动初始化 XR，这就是必须调用为协同例程的原因：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 运行时，可以使用 API 获取当前连接状态，并可以选择使用 断开连接 `AppRemoting.TryGetConnectionState` 和取消初始化 `AppRemoting.Disconnect()` XR。 这可用于断开连接并重新连接到同一应用会话中的不同设备。 示例应用提供了一个可点击的多维数据集，该多维数据集将在点击时断开远程处理会话。

### <a name="migration-from-previous-apis"></a>从以前的 API 迁移

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

从 Unity 文档[的示例代码中：](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

| XR。Wsa。HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A：调用 时自动 `AppRemoting.Connect` 发生]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine.XR.WindowsMR.WindowsMRRemoting

| XR。WindowsMR.WindowsMRRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | 通过 `AppRemoting.Connect` 结构 `RemotingConfiguration` 传入 |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`