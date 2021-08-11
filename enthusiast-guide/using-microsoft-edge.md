---
title: 在 Microsoft Edge Windows Mixed Reality
description: 准备好在 Windows Mixed Reality 中Microsoft Edge新Windows Mixed Reality。 包括预期更改、要查找的更新和已知问题。
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 主页， 导航， 四处浏览， 应用， 游戏， Microsoft Edge， chromium， Edge， 360， 360 video， 360 viewer
ms.openlocfilehash: 3cdb051e9925338a5f0145e106e2213712eb611e575b9f5d7dd29342a52ff38d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199483"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality和新的Microsoft Edge

[新Microsoft Edge](https://www.microsoft.com/edge)可供下载，并开始通过 Windows 更新自动推出。 

新Microsoft Edge[在桌面上Chromium开源](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)项目。 这可为客户提供更好的兼容性，减少 Web 开发人员的碎片。 它还会在发布时支持 WebXR，这是用于为 VR 头戴显示设备创建沉浸式 Web 体验的新标准，用于代理 WebVR。

>[!IMPORTANT]
>在最新的 Microsoft Edge 设备上安装 Windows 10 时，它将替换电脑上 (旧版) 旧版。

## <a name="installing-the-new-microsoft-edge"></a>安装新Microsoft Edge 

在安装新 Microsoft Edge 之前，请升级到 Windows 10 版本 **1903** 或更高版本，以支持本机 Win32 应用程序，如 Windows Mixed Reality 中的新 Microsoft Edge。 检查Windows更新[或手动安装最新版本Windows 10。](https://www.microsoft.com/software-download/windows10)

使用版本Windows 10 1903 或更高版本后，即可使用新的Microsoft Edge！ 新的Microsoft Edge通过 Windows Update 推出，但如果需要，可以Microsoft Edge从 Microsoft Edge[网站](https://www.microsoft.com/edge)手动安装新应用。

>[!IMPORTANT]
>新Microsoft Edge WebXR（为 VR 头戴显示设备创建沉浸式 Web 体验的新标准）启动。 安装新 Microsoft Edge 时，你将无法再在 Microsoft Edge 中播放 WebVR 体验。 

## <a name="known-issues"></a>已知问题

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>版本 1903 或更高版本的 2020-01 Windows 10 累积更新解决的已知 (问题) 

- 启动任何 Win32 应用（包括Microsoft Edge）会导致头戴显示短暂冻结。
- "Microsoft Edge磁贴从"Windows Mixed Reality "开始"菜单 ("文件夹中消失，可在"经典应用"文件夹中找到) 。
- Windows上一个Microsoft Edge仍放置在混合现实主页周围，但不能使用。 尝试激活这些窗口会启动桌面应用中的 Edge。
- 选择窗口中的超链接混合现实主页在桌面上启动 Web 浏览器，而不是混合现实主页。
- WebVR 展示应用存在于 混合现实主页，尽管不再支持 WebVR。
- 对键盘启动和视觉对象的常规改进。

### <a name="monitor-and-input-handling-issues"></a>监视和输入处理问题

对 Windows 10 版本 1903 或更高版本进行 2020-01 累积更新后，虚拟监视器将在 Windows Mixed Reality 会话期间在 **设置 > System > Display** 中显示为通用物理监视器。 某些客户（尤其是具有多个物理监视器的客户）可能会注意到桌面布局和输入处理的问题。

**发生这种情况的原因**

在 中引入了对 Windows Mixed Reality 经典 Win32 应用程序[Windows 10 2019 年 5 月更新。](/windows/mixed-reality/release-notes-may-2019) 若要启用此支持，必须创建虚拟监视器来托管 Win32 应用程序。 每次启动新的 Win32 应用程序时，必须创建另一个虚拟监视器。 遗憾的是，创建虚拟监视器是一项密集型任务，可能会导致头戴显示短暂冻结。 客户提供了反馈，指出体验是混乱和中断性的。 由于这种反馈，以及 Win32 应用程序的使用量增加，我们决定在 Windows Mixed Reality 启动期间预分配三个虚拟监视器，以防止这种中断，使客户能够启动最多三个并发 Win32 应用程序，而不会遇到头戴显示冻结。

**解决方法**

此后，我们收到了反馈，指出某些客户（尤其是具有多个物理监视器的客户）希望禁用此虚拟监视器预分配。 为了为客户提供更多控制，我们启用了一种解决方法，该解决方法涉及更改注册表项值，Windows更新：

- 版本 2004 Windows 10 KB4568831 (2020-07 累积更新预览) 
- 2020-10 Windows 10 版本 1909 (KB4580386) 
- 2020-10 Windows 10 版本 1903 (KB4580386) 

>[!NOTE]
>修改注册表项值适用于高级用户。

>[!WARNING]
>在 Windows Mixed Reality 中启动 Win32 应用程序 (如 Steam、新的 Microsoft Edge 或 Google Chrome) 时，禁用虚拟监视器预分配可能会导致头戴显示短暂冻结。

禁用虚拟监视器预分配：
1. 查看 **Windows累积** 更新预览Windows 10之一的更新，并安装更新（如果可用）。 更新设置页上的"可选更新 **"** 或 **"高级Windows** 更新
2. 启动 **注册表编辑器**
3. 导航到"HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. 如果"PreallocateVirtualMonitors"REG_DWORD 不存在，请通过选择"编辑 > 新建 **> DWORD (32** 位) 值"并输入 PreallocateVirtualMonitors 作为名称来创建它
5. 如果存在"PreallocateVirtualMonitors"REG_DWORD (，或者你刚刚创建了它) ，请双击该条目，将"值数据"从 1 (其默认值) 更改为 0 (零) 
    * TRUE - 1
    * FALSE - 0

现在，当你尝试在虚拟机中启动 Win32 Windows Mixed Reality而不是预先分配时，虚拟监视器将进行分配。 若要重置此配置并重新启用虚拟监视器预分配，请返回 DWORD"值数据"到 1。

### <a name="other-known-issues"></a>其他已知问题

-   在 Windows Mixed Reality 中打开的网站将在关闭混合现实门户丢失，尽管Microsoft Edge窗口将保留它们放置在混合现实主页。
- WebXR 体验（包括 360 查看器扩展）可能无法在具有混合 GPU 设置的 PC 上正确启动。 可以通过在新功能中启用预览功能来解决此问题Microsoft Edge。 导航到 `edge://flags` ，搜索"多 gpu"并启用名为 **"WebXR 多 GPU 支持"的标志**。
-   来自Microsoft Edge的音频未进行空间化。
-   在 **360 查看器扩展版本 2.3.8** 中修复：在 Windows Mixed Reality 中打开 YouTube 中的 360 视频可能会导致视频在头戴显示设备中扭曲。 重启 Edge 时，应以不公开方式更新 360 查看器扩展来解决此问题。 可以通过在地址栏中输入 并选择"扩展"旁边的"展开"按钮来确认扩展 `edge://system/` 的版本。