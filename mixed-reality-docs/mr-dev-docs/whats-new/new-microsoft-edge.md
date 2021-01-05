---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 在 Windows Mixed Reality 中准备好新的 Microsoft Edge。 包括对预期的更改、要查找的更新和已知问题。
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: 边缘，新，沉浸式 web，microsoft edge，浏览器，vr，360，360视频，360 viewer，webxr，webvr
ms.openlocfilehash: 341c7e3d53bd7fb0c569a8acffcf56662c8d2c32
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757435"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 和新的 Microsoft Edge

[新的 Microsoft Edge 现在可供下载](https://blogs.windows.com/windowsexperience/?p=173496)，但客户也可以[等待未来的更新使用 Windows 10 进行安装](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)，并遵循下几个月的已测量的推出方法。 

在此新闻中， **我们希望让 Windows Mixed REALITY VR 耳机客户知道从新的 Microsoft Edge 获得的内容，并显示未完成的更新，以改善 Windows Mixed 现实中的浏览体验**。

## <a name="introducing-the-new-microsoft-edge"></a>推出新的 Microsoft Edge

新的 Microsoft Edge [采用桌面上的 Chromium 开源项目](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) ，为客户提供更好的兼容性，并为 web 开发人员提供更少的 web 碎片。 它还支持在启动时 WebXR，这是用于创建用于 VR 耳机的沉浸式 web 体验的新标准，而不是 WebVR。

>[!IMPORTANT]
>当你在最新的 Windows 10 设备上安装 Microsoft Edge 时，它将替换你的电脑上先前 (旧) 版本。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>准备好开始新的 Microsoft Edge

如果 Windows Mixed Reality 需要在混合现实中使用新的 Microsoft Edge，则需要 **升级到 Windows 10 1903 版或更高版本，以便对 Win32 应用程序的本机支持 (如混合现实中的新 Microsoft edge)** 。 请检查 Windows 更新或 [手动安装最新版本的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。

为了在混合现实主页中获得最佳的 Microsoft Edge 体验，我们还建议你等待 windows **10 版本 1903 (或更) 高版本的2020-01 累积更新（年结束时 Windows 更新提供）的 Windows Mixed reality 优化。**

>[!IMPORTANT]
>如果你选择在执行这些更新之前下载新的 Microsoft Edge，则在 Windows Mixed Reality (会出现一些已知问题，你可以在) 了解相关信息。

## <a name="known-issues"></a>已知问题

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>2020-01 (或更高1903版本的 Windows 10 累积更新解决了已知问题) 

- 启动任何 Win32 应用程序（包括新的 Microsoft Edge）都会导致耳机显示暂时冻结。
- Microsoft Edge 磁贴从 Windows Mixed Reality 开始菜单中消失 (你可以在) 的 "经典应用" 文件夹中找到它。
- 以前的 Microsoft Edge 中的 Windows 仍位于混合现实主页，但无法使用。 尝试激活桌面应用程序中的 windows 启动边缘。
- 选择混合现实中的超链接时，将在桌面上而不是混合现实主页上启动 web 浏览器。
- 尽管不再支持 WebVR，但 WebVR 展示应用存在于混合现实主页中。
- 键盘启动和视觉对象的一般改进。

### <a name="monitor-and-input-handling-issues"></a>监视和输入处理问题

为 Windows 10 版本1903（ (或更) 高版本）采用2020-01 累积更新后，在 Windows Mixed Reality 会话期间，虚拟监视器将在 " **设置 > 系统 > 显示** " 中显示为 "一般物理监视器"。 某些客户（尤其是对于多个物理监视器），可能会注意到桌面布局和输入处理的问题。

**为什么会发生这种情况**

Windows [10 2019 更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)中引入了对 Windows Mixed Reality 中经典 Win32 应用程序的支持。 若要启用此支持，必须创建虚拟监视器来托管 Win32 应用程序。 每次启动新的 Win32 应用程序时，都必须创建另一个虚拟监视器。 遗憾的是，创建虚拟监视器是一种密集型任务，可能会导致耳机显示短暂冻结。 客户提供了反馈，指出这是一种令人不安且有中断的体验。 由于反馈和 Win32 应用程序的使用情况，我们决定在 Windows Mixed Reality 启动过程中预分配三个虚拟监视器。 这可以防止中断，并使客户可以启动多达三个并发的 Win32 应用程序，而不会遇到耳机显示冻结。

**解决方法**

由于收到一些客户（尤其是那些具有多个物理监视器的客户），因此将更愿意禁用此虚拟监视器预分配。 为了向客户提供控制，我们已启用了一种解决方法，其中包含更改注册表项值，此值可用于以下 Windows 更新：

- 2020-07 (KB4568831) 的 Windows 2004 10 的累积更新预览
- 2020-10 (KB4580386) 的 Windows 1909 10 的累积更新预览
- 2020-10 (KB4580386) 的 Windows 1903 10 的累积更新预览

>[!NOTE]
>修改注册表项值适用于高级用户。

>[!WARNING]
>如果在 Windows Mixed Reality 中启动 Win32 应用程序 (例如流、新的 Microsoft Edge 或 Google Chrome) ，禁用虚拟监视器预分配可能会导致耳机显示短暂的情况。

若要禁用虚拟监视器预分配：
1. **Windows 更新** 检查以上列出的 Windows 10 累积更新预览版本中的一个，并在可用时安装更新。 你可能会在 "Windows 更新设置" 页上的 " **可选更新** " 或 " **高级选项** " 下找到更新
2. 启动 **注册表编辑器**
3. 导航到 "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. 如果 "PreallocateVirtualMonitors" REG_DWORD 不存在，请通过选择 " **编辑 > 新 > DWORD (32 位) 值** 并输入 PreallocateVirtualMonitors 作为名称来创建它。
5. 如果 "PreallocateVirtualMonitors" REG_DWORD 存在 (或者您刚刚) 创建它，则双击该条目，并将 "值数据" 从 1 (其默认值) 为 0 (零。
    * TRUE-1
    * FALSE-0

当你尝试在 Windows Mixed Reality 而不是预分配中启动 Win32 应用程序时，虚拟监视器现在将进行分配。 若要重置此设置并重新启用虚拟监视器预分配，请将 DWORD "值数据" 返回到 "1"。

### <a name="other-known-issues"></a>其他已知问题

-   当混合现实门户关闭时，在 Windows Mixed Reality 中打开的网站将丢失。 Microsoft Edge 窗口将保留在混合现实中的位置。
- WebXR 体验，包括360查看器扩展，可能无法在具有混合 GPU 设置的电脑上正常启动。 通过在新的 Microsoft Edge 中启用预览功能，可以解决此问题。 导航到 `edge://flags` ，搜索 "多个 gpu" 并启用名为 **WEBXR 多 gpu 支持** 的标志。
-   Microsoft Edge windows 中的音频未 spatialized。
-   **修复了360查看器扩展版本 2.3.8**：在 Windows Mixed Reality 中从 YouTube 打开360视频可能会导致耳机上出现视频失真。 重启边缘应在不可见的情况下更新360查看器扩展以解决此问题。 您可以通过 `edge://system/` 在地址栏中输入，然后选择 "扩展" 旁边的 **展开** 按钮，确认您所拥有的扩展版本。
