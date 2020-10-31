---
title: SteamVR 常见问题
description: SteamVR Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，SteamVR
ms.openlocfilehash: f1eafa303d0f2ee4c289f9acf337d8c512a7915c
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132131"
---
# <a name="steamvr-faqs"></a>SteamVR 常见问题

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>如何在 Windows Mixed Reality 耳机上播放 SteamVR 游戏

1. [下载并安装 SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)。 启动 SteamVR 时，SteamVR 教程应该会自动启动。
2. 将耳机连接到电脑，并打开运动控制器。
3. 加载 Windows Mixed Reality 主页并显示控制器后，请在桌面上打开流应用。
4. 使用流应用从您的流库中启动 SteamVR 游戏。 若要在不停用耳机的情况下启动 SteamVR 游戏，请在 Windows Mixed Reality **> 所有应用** 中找到并启动它们。

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>出现一条消息，指出 "在 Windows Mixed Reality 中使用 SteamVR，需要安装最新的 Windows 更新" 或 "需要 Windows 开发人员模式"

1. 确保你的计算机运行的是最新版本的 Windows 10。 请参阅 " **设置" > 系统 > 关于** "，然后在" Windows 规范 "下，确保" OS Build "为16299.64 或更高版本。
2. 请确保没有任何等待下载或安装的更新。 请参阅 " **设置" > 更新 & 安全 > Windows 更新** ，然后选择 "检查更新"。 你可能需要检查多次，直到没有可用的更新，然后重新启动你的电脑。

## <a name="steamvr-is-crashing-after-updating-windows"></a>更新 Windows 后 SteamVR 崩溃

SteamVR 的某些较旧版本的 Windows Mixed Reality 不再与 Windows 兼容。 确保 SteamVR 的 Windows Mixed Reality 版本是最新版本：

1. 在您的流库中，请参阅 **软件 > Windows Mixed Reality For SteamVR** 。
2. 右键单击它，并跳到 "属性"。
3. 选择 "更新" 选项卡和 "始终保持此应用程序最新"。
4. 转到 "本地文件" 选项卡，然后选择 "验证应用程序文件的完整性" 来强制更新。
5. 重新启动流和 SteamVR。

如果在更新后 SteamVR 仍崩溃，则可能会在计算机上为 SteamVR 安装两个 Windows Mixed Reality。 若要确认是否属于这种情况：

1. ```%localappdata%\openvr\openvrpaths.vrpath```在记事本中查找并打开它。
2. 在 "外部驱动程序" 部分，查找 "MixedRealityVRDriver" 的多个条目
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 如果看到多个条目，请删除这两个条目中较早的条目。 只有一个条目后，行尾不应再有一个逗号。 例如：
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. 保存文件并将其关闭。
5. 重新启动流和 SteamVR。

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>我的控制器在 SteamVR 中未按预期方式工作。

1. 关闭 SteamVR。
2. 返回到 Windows Mixed Reality home，确认控制器正在运行。
3. 再次启动 SteamVR 体验，控制器应恢复正常。
4. 如果问题仍然存在，请使用混合现实类别下的 [Windows 反馈中心](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) 提供文件反馈，并在摘要中包括 SteamVR。

请注意，在不同的游戏中，你将以不同的方式使用移动控制器。 下面是一些可帮助你入门的基础知识：
* 若要打开 "流" 仪表板，请在左侧操纵杆上按 "向下"。
* 若要退出 SteamVR 游戏并返回到 Windows Mixed Reality 主页，请按 Windows 按钮。 然后选择屏幕上显示的混合现实主页按钮。

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>我的左控制器和右控制器在 SteamVR

先关闭控制器，然后再打开，然后打开左控制器和右控制器。

## <a name="my-games-are-running-slowly"></a>游戏运行缓慢

1. 确保你的电脑满足 Windows Mixed Reality 中 SteamVR 的规范，以及你正在玩的 SteamVR 游戏的规范。
2. 在桌面上的混合现实门户中，选择 "暂停" 停止桌面预览。
3. 请参阅 " **设置" > 系统 >** "Windows 规范" 下的 "设置"，确保 "OS Build" 为16299.64 或更高版本。
4. 确保你的电脑具有最新的图形驱动程序， ( "Windows 更新) 中的" 检查更新 "。
5. 选中 "任务管理器" 以查看在您的 PC 上可能会消耗资源的其他进程。
6. 检查流是否正在后台下载游戏。 这可能会消耗资源并使游戏运行不佳。
7. 如果一小类应用没有可见的窗口 (例如 SteamVR Home) ，则会有一个已知的性能问题。 大多数应用不属于此类别，并且在将来的更新中会提供修补程序。

如果仍遇到意外性能问题，请使用 [Windows 反馈中心](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)向我们发送反馈。 请确保按照说明操作以 [包含 SteamVR 性能跟踪](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)。

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR 显示了一个组合器错误 (例如，"Shared IPC 合成器 Connect Failed (400) " ) 。

如果头戴显示在两个不同的视频适配器上，则可能会发生这种情况。 将监视器连接到与耳机相同的适配器，并将该监视器配置为 "设置" 应用中的主监视器 **> 系统 > 显示** 。

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR 内容显示在错误的位置，例如

重置位置：

1. 单击左侧控制器的操纵杆，打开 "SteamVR 仪表板"。
2. 选择 "设置" 按钮。
3. 选择 "重置固定位置"。

## <a name="my-steam-app-closed-unexpectedly"></a>我的流应用意外关闭

如果你锁定电脑屏幕、删除头戴显示设备、切换用户或电脑进入睡眠状态，则流应用将关闭。
