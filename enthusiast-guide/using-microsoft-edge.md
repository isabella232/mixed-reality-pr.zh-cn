---
title: 使用 Windows Mixed Reality 中的 Microsoft Edge
description: 准备好 Windows Mixed Reality 中的新 Microsoft Edge。 包括对预期的更改、要查找的更新和已知问题。
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，Home，导航，接收，，应用，游戏，Microsoft Edge，chromium，边缘，360，360视频，360查看器
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436692"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 和新的 Microsoft Edge

[新 Microsoft Edge](https://www.microsoft.com/edge)可供下载，并已开始通过 Windows 更新自动向客户推出。 

新 Microsoft Edge[采用桌面上的 Chromium 开源项目](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)。 这为客户提供更好的兼容性，并且为 web 开发人员提供的碎片更少。 它还支持 WebXR，这是用于创建适用于 VR 耳机的沉浸式 web 体验的新标准，替代 WebVR。

>[!IMPORTANT]
>在最新的 Windows 10 或 Windows 11 设备上安装 Microsoft Edge 时，它将替换你的电脑上以前的 (旧) 版本。

## <a name="installing-the-new-microsoft-edge"></a>安装新 Microsoft Edge 

安装新 Microsoft Edge 之前，请 **升级到 Windows 10 版本1903或更高版本，或升级到 Windows Mixed Reality 中的新 Microsoft Edge 等本机 Win32 应用程序支持的 Windows 11** 。 检查 Windows 更新或[手动安装最新版本的 Windows 10](https://www.microsoft.com/software-download/windows10)或 Windows 11。

Windows 10 版本1903或更高版本或 Windows 11 之后，就可以开始使用新的 Microsoft Edge！ 新 Microsoft Edge 通过 Windows 更新推出，但你可以根据需要在[Microsoft Edge 网站](https://www.microsoft.com/edge)上手动安装新的 Microsoft Edge。

>[!IMPORTANT]
>新的 Microsoft Edge 启动时支持 WebXR，这是为 VR 耳机创建沉浸式 web 体验的新标准。 当你安装新的 Microsoft Edge 时，你将无法再在 Microsoft Edge 中播放 WebVR 体验。 

## <a name="known-issues"></a>已知问题

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>2020-01 Windows 10 1903 (或更高版本的累积更新解决了已知问题) 

- 启动任何 Win32 应用程序（包括新 Microsoft Edge）都会导致耳机显示暂时冻结。
- "Microsoft Edge" 磁贴从 Windows Mixed Reality "开始"菜单中消失 (你可以在 "经典应用" 文件夹中找到它) 。
- 之前 Microsoft Edge Windows 仍位于混合现实主页，但不能使用。 尝试激活桌面应用程序中的 windows 启动边缘。
- 选择混合现实中的超链接时，将在桌面上而不是混合现实主页上启动 web 浏览器。
- 尽管不再支持 WebVR，但 WebVR 展示应用存在于混合现实主页中。
- 键盘启动和视觉对象的一般改进。

### <a name="monitor-and-input-handling-issues"></a>监视和输入处理问题

为 Windows 10 版本1903或更高版本获取2020-01 累积更新后，虚拟监视器将在 Windows Mixed Reality 会话期间显示为 **设置 > 系统 > 显示** 的通用物理监视器。 有些客户（尤其是那些具有多个物理监视器的客户）可能会注意到桌面布局和输入处理的问题。

**为什么会发生这种情况**

[Windows 10 2019 年5月更新](/windows/mixed-reality/release-notes-may-2019)中引入了对 Windows Mixed Reality 中经典 Win32 应用程序的支持。 若要启用此支持，必须创建虚拟监视器来托管 Win32 应用程序。 每次启动新的 Win32 应用程序时，都必须创建另一个虚拟监视器。 遗憾的是，创建虚拟监视器是一种密集型任务，可能会导致耳机显示短暂冻结。 客户向用户提供了丰富体验的反馈，并具有破坏性。 由于此反馈，增加了 Win32 应用程序的使用情况，因此我们决定在 Windows Mixed Reality 启动过程中预先分配三个虚拟监视器以防止这种中断，并使客户可以启动多达三个并发的 Win32 应用程序，而不会遇到耳机显示冻结。

**解决方法**

由于收到一些客户（尤其是那些具有多个物理监视器的客户），因此将更愿意禁用此虚拟监视器预分配。 为了向客户提供更多控制措施，我们已启用了一种解决方法，其中包含更改注册表项值，并提供以下 Windows 更新：

- 2020-07 Windows 10 版本2004的累积更新预览 (KB4568831) 
- 2020-10 Windows 10 版本1909的累积更新预览 (KB4580386) 
- 2020-10 Windows 10 版本1903的累积更新预览 (KB4580386) 

>[!NOTE]
>修改注册表项值适用于高级用户。

>[!WARNING]
>禁用虚拟监视器预分配可能会导致头戴显示在启动 Win32 应用程序 (例如流、新 Microsoft Edge 或) Windows Mixed Reality 中的 Google Chrome 时。

若要禁用虚拟监视器预分配：
1. 检查以上列出的 Windows 10 累积更新预览版本之一 **Windows 更新**，并在可用时安装更新。 你可能会在 "Windows 更新设置" 页上的 "**可选更新**" 或 "**高级选项**" 下找到更新
2. 启动 **注册表编辑器**
3. 导航到 "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. 如果 "PreallocateVirtualMonitors" REG_DWORD 不存在，请通过选择 " **编辑 > 新 > DWORD (32 位) 值** 并输入 PreallocateVirtualMonitors 作为名称来创建它。
5. 如果 "PreallocateVirtualMonitors" REG_DWORD 存在 (或者您刚刚) 创建它，则双击该条目，并将 "值数据" 从 1 (其默认值) 为 0 (零。
    * TRUE-1
    * FALSE-0

当你尝试在 Windows Mixed Reality 中启动 Win32 应用程序（而不是预先分配）时，虚拟监视器现在会分配。 若要重置此设置并重新启用虚拟监视器预分配，请将 DWORD "值数据" 返回到 "1"。

### <a name="other-known-issues"></a>其他已知问题

-   当混合现实门户关闭时，Windows Mixed Reality 中打开的网站将会丢失，但 Microsoft Edge 的窗口将保留在混合现实中的位置。
- WebXR 体验，包括360查看器扩展，可能无法在具有混合 GPU 设置的电脑上正常启动。 若要解决此问题，可以在新的 Microsoft Edge 中启用预览功能。 导航到 `edge://flags` ，搜索 "多个 gpu" 并启用名为 **WEBXR 多 gpu 支持** 的标志。
-   Microsoft Edge windows 中的音频不 spatialized。
-   **修复了360查看器扩展版本 2.3.8**：在 Windows Mixed Reality 中从 YouTube 打开360视频可能会导致耳机上出现视频失真。 重启边缘应在不可见的情况下更新360查看器扩展以解决此问题。 您可以通过 `edge://system/` 在地址栏中输入，然后选择 "扩展" 旁边的 **展开** 按钮，确认您所拥有的扩展版本。