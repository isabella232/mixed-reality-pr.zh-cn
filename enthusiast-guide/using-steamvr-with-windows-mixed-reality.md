---
title: 将 SteamVR 与 Windows Mixed Reality
description: 了解如何在具有兼容电脑的 Windows Mixed Reality和控制器上设置和播放 SteamVR 游戏。
ms.topic: article
keywords: Windows Mixed Reality、混合现实、虚拟现实、VR、MR、游戏、SteamVR、流、系统要求
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110149"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>将 SteamVR 与 Windows Mixed Reality

Windows Mixed Reality使用 SteamVR，用户可以在沉浸式头戴显示设备Windows Mixed Reality SteamVR 体验。 安装适用于 SteamVR Windows Mixed Reality后，用户可以从桌面或 Steam 库启动其最喜欢的 SteamVR 应用程序，并直接在 Windows 头戴显示设备上播放它们。

## <a name="get-your-pc-ready"></a>准备好电脑

* 确保没有挂起的更新：选择"启动">"设置 **>"&"> Windows 更新"。** 如果更新可用，请选择"**立即安装"。** 如果没有可用的更新，请选择 **"检查更新"，** 然后安装任何新更新。
* Pc 要求因 Steam 上的应用和内容而异。 请参阅每个标题的最低要求。 具有 GTX 1070 图形卡 (或等效) 和 Intel® Core™ i7 处理器的电脑应为各种标题提供良好的体验。
* 设置 [Windows Mixed Reality（](set-up-windows-mixed-reality.md) 如果尚未设置）。 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>为 SteamVR Windows Mixed Reality设置服务

1. [下载并安装 SteamVR。](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. 准备就绪后，启动 SteamVR。 SteamVR 教程应会自动启动。

> **注意：** 对于 SteamVR 设置的高级故障排除，请确保已安装以下软件组件：
> 1. 安装 [Steam](http://store.steampowered.com/about/) **并登录****或创建新帐户。**
> 2. 安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)。 插入头戴显示设备后，启动"Steam"，应会看到一个提示你安装 SteamVR 的对话框。 按照对话框中的提示进行安装。
    * 如果看不到弹出窗口，请导航到库 的"工具"部分来安装 *SteamVR。* 在列表中找到"SteamVR"，然后右键单击并选择"*安装游戏"。*
> 3. 安装[Windows Mixed Reality适用于 SteamVR 的 。](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>在Windows Mixed Reality Internet 访问的环境中为 SteamVR 设置连接

**在可移植存储设备上存储必要的介质**
1. 按照 [上述Windows Mixed Reality](https://store.steampowered.com/app/250820/SteamVR/) 在具有完全 Internet 访问权限的电脑上使用 SteamVR 安装 [SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 和适用于 [SteamVR](http://store.steampowered.com/about/) 的客户端。
2. 在"Steam"中，打开"库"部分，找到标记为"工具"的部分。
3. 安装 SteamVR 后，右键单击条目"SteamVR"，在生成的弹出菜单中，单击条目"属性"。
4. 将打开包含多个选项卡的新窗口。 选择选项卡"本地文件"，然后单击标记为"浏览本地文件"的按钮。
5. 将打开包含 SteamVR 运行时的目录。 将名为"SteamVR ("的整个) 复制到你选择的可移植介质上 (例如 USB u 盘) 。
6. 对于 SteamVR Windows Mixed Reality，以及要安装在目标电脑上的任何与 SteamVR 兼容的应用，请执行相同的操作。

**在目标电脑上运行 SteamVR**
1. 将便携式存储设备插入目标电脑后，将 SteamVR、MixedRealityVRDriver 和其他文件夹移到目标电脑上的方便位置。
![在目标电脑上Windows Mixed Reality的 SteamVR 和适用于 SteamVR 的流](images/steamvr-install-files.png)

2. 确保 SteamVR 和 MixedRealityVRDriver 在同一文件夹中，打开命令提示符。 对于此示例，我们假设包含文件夹位于 *C：\SteamVRInstall*。 在这种情况下，应在命令提示符下运行：
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
 (请注意，如果运行的是 32 位版本的 Windows，则上述路径的部分 `win64` `win32` 应为 。) 

这将允许运行时在自定义Windows Mixed Reality中查找适用于 SteamVR 驱动程序的驱动程序。

4. 若要运行 SteamVR，应双击位于SteamVR\bin\win64\vrstartup.exe的文件 *"vrstartup.exe";* 如果目标电脑运行的是 32 位版本的 *Windows，* 则双击SteamVR\bin\win32\vrstartup.exe。

有关详细信息 [和故障排除，请参阅 Steamworks 文档页](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)。

## <a name="play-steamvr-games"></a>播放 SteamVR 游戏

1. 将头戴显示设备连接到电脑并打开运动控制器。
2. 加载Windows Mixed Reality控制器后，在桌面上打开 Steam 应用。
3. 使用 Steam 应用从 Steam 库启动 SteamVR 游戏。

**提示**：若要在不关闭头戴显示设备的情况下启动 SteamVR 游戏，请使用桌面应用 (**启动 > Desktop**) 在 Windows Mixed Reality 中查看电脑桌面并与之Windows Mixed Reality。

## <a name="using-motion-controllers-with-steamvr"></a>将运动控制器与 SteamVR 一起使用

你将在不同的游戏中以不同方式使用运动控制器。 下面是一些可帮助你入门的基础知识：

* 若要打开"流"仪表板，请直接按下左侧或右侧滚动块。
* 若要退出 SteamVR 游戏并返回到Windows Mixed Reality，请按 Windows 按钮。

## <a name="changing-the-resolution"></a>更改分辨率

如果希望以更高的分辨率播放游戏，随时可以在"SteamVR"->"设置"->"应用程序"窗口中调整"应用程序解析"滑块。 **使用分辨率更高的乘数时，可以预期游戏对电脑造成更大压力。 如果增加乘数并看到性能下降，请重新将滑块调整为默认级别，然后重启游戏以确保更改生效。![调整应用程序分辨率](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>使用多个头戴显示设备

如果你是 VR 运动家，可以定期在同一电脑上使用多个 VR 头戴显示设备。 如果是这种情况，请注意，当插入 Windows Mixed Reality头戴显示设备时，SteamVR 游戏将始终启动到 Windows Mixed Reality头戴显示设备。 如果要在另一个头戴显示设备上启动 SteamVR 游戏，请确保在继续操作Windows Mixed Reality头戴显示设备。

## <a name="preview-programs"></a>预览程序

我们发布定期更新，以提高在沉浸式头戴显示设备上使用 SteamVR Windows Mixed Reality可靠性和整体体验。 尽管这些预览计划都不需要，但如果希望更快、更频繁地获取更新，我们建议你加入它们 (并提供有关这些更新的反馈！) 。

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality SteamVR Beta 版本

Windows Mixed Reality适用于 SteamVR 的组件是从 Steam Store 安装的组件，使 SteamVR 能够与 Windows Mixed Reality头戴显示设备一起工作。  我们会定期发布对此"网桥"的更新，而 Steam 会自动安装更新。

如果希望更频繁地获取更新，我们建议你加入我们的公共 Beta 版本。  更新首先会转到 Beta 受众，我们会使用他们的反馈确保更新是高质量的，然后再将其发布到所有用户。  如果你不在我们的 Beta 计划中，最终会获得所有相同的修补程序和功能，但在 Beta 用户测试它们之后。

若要联接：：

  1. 在"流"中，使用"库"菜单 **下的** 下拉列表筛选为"**软件"。**
  2. 在列表中，右键单击 **"Windows Mixed Reality"，然后选择**"属性 **"。**
  3. 选择 **"Betas"** 选项卡。
  4. 选择加入 **"beta - 公共 beta 版本"，然后选择** " **关闭"** 以确认。 beta 访问代码字段应留空。
  
### <a name="steamvr-beta"></a>SteamVR Beta

SteamVR 由"流"生成和释放，在所有 SteamVR 头戴显示设备中很常见。  它遵循类似的模型，在向所有用户发布 Beta 成员之前发布更新。

若要联接：：

  1. 在"流"中，使用"库"菜单 **下的** 下拉列表筛选为"**工具"。**
  2. 在列表中，右键单击 **"SteamVR"，** 然后选择"属性 **"。**
  3. 选择 **"Betas"** 选项卡。
  4. 选择加入 **"beta - 公共 beta 版本"，然后选择** " **关闭"** 以确认。  beta 访问代码字段应留空。 ![在 SteamVR 的属性对话框中切换到 SteamVR beta 版本](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Windows 预览体验计划

Windows Mixed Reality是 Windows 10 的一Windows 10。  影响 SteamVR 用户的许多修补程序和功能都随 Windows OS 一起提供。  若要试用最新的预览Windows 10版本，建议加入[Windows 预览体验计划。](https://insider.windows.com)

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>为 SteamVR 应用启用运动重新项目

Windows Mixed Reality的流式处理具有实验性运动重现功能，使 90 FPS 重新保护更流畅。

启用运动重新项目时，所有 Steam VR 游戏在名义上以 1/2 帧速率呈现 (45 fps 而不是 90 FPS) ，而 Windows Mixed Reality for SteamVR 使用 GPU 生成的运动矢量来推断下一帧。 对于在给定电脑上可靠地达到 60 FPS+ 的 SteamVR 游戏，这应该可以带来可靠的 90 FPS 体验，偶尔出现项目，同时保持舒适体验。

可用的运动重现模式如下所示：

* **SteamVR 每应用设置**：允许通过"SteamVR 设置"UI 控制运动重新项目。 然后，可以打开"SteamVR 设置"，转到"视频> Per-Application视频设置"，然后选择"运动平滑处理"选项。
* **自动**：使运动重现能够在游戏呈现速度过慢而维持 90 FPS 时自动打开。 当游戏开始保持 90 FPS 或以小于 45 FPS 开始渲染时，运动重新保护将关闭。 始终启用异步旋转重新项目。
* **运动向量**：强制应用程序始终以半帧速率运行，并重排运动矢量。
* **无**：禁用运动重新项目。

**预期的视觉对象项目** 

1. 使用大于 150% 的应用程序分辨率时，可能会遇到模糊处理。 使用运动重现时，建议使用小于 150% 的值。
2. 清晰对比度的边缘或文本（尤其是在游戏内 HUD 或菜单上）可能会由于分离而暂时出现扭曲或扭曲。
3. 在此模式下，SteamVR Home 和电脑上无法可靠地达到 50-60 FPS 的其他许多游戏将继续体验不佳。
4. 某些游戏已报告以 50% 的速度运行，或者延迟增加 (延迟) 。 通过下面的说明报告 [Windows 反馈中心](filing-feedback.md) 游戏。

最初，我们针对最新一代 NVidia GPU 提供实验性支持。 我们将继续在更多 GPU 上循环访问和改进运动重现支持，并且我们期待收到你的反馈。

**支持的 GPU：** Nvidia GeForce GTX1060、AMD RX470 或更好，Windows Mixed Reality兼容的图形驱动程序。

启用运动重新项目：

1. 确保已按照上述说明选择Windows Mixed Reality **SteamVR Beta** 版本。
2. 打开 SteamVR 仪表板。
3. 选择左侧具有"流"徽标的按钮Windows Mixed Reality打开 **"Windows Mixed Reality"设置"。**
4. 在弹出的 UI 中，选择"图形"选项卡。
5. 选择"自动"作为"默认 SteamVR 应用运动重现模式"，以启用自动运动重现。

![使用 SettingsUX & LSR 指示器启用 LSR](images/settingsux-enable-lsr.gif)

**运动重现指示器**

运动重现指示器有助于诊断实验性自动运动重新项目功能的问题。 设置为 true 时，在自动运动重新保护期间，头戴显示设备左上方会显示一个指示器。 此指示器的颜色和位置对应于当前运动重现模式 - 有关示例，请参阅下图。

![mvLSR 指示器](images/mvLSRIndicator.png)

绿色 = 运动重现处于关闭状态，因为应用程序可以以全帧速率呈现。

由于应用程序占用了 CPU，因此，"青色 = 运动重新项目"为"打开"状态。

蓝色 = 运动重新项目已打开，因为应用程序已绑定 gpu。

红色 = 运动重新重现处于关闭状态，因为应用程序以小于一半帧速率运行;如果已启用，请尝试减少超级采样。

绿色 + 青色 + 蓝色 = 运动重排为半帧速率模式，或应用程序请求的重排运动。

## <a name="sharing-feedback-on-steamvr"></a>共享有关 SteamVR 的反馈

在改进 SteamVR 体验方面，你的Windows Mixed Reality非常有用。 通过 提交所有反馈和 bug [Windows 反馈中心。](filing-feedback.md) 请遵循以下建议，帮助我们从你的反馈中获得最大帮助：

1. 在反馈中心中，指示你在"什么是反馈？"中报告新问题。 部分位于顶部。
2. 选择" **混合现实"** 类别和 **"应用** "子类别。
3. 将单词"SteamVR"放在问题摘要中。 这有助于我们找到你的反馈。
4. 描述遇到问题时使用的 SteamVR 游戏或应用程序。
5. 请考虑将 SteamVR 系统报告附加到反馈。 这提供了更多日志，可帮助我们诊断问题。
    1. 在"SteamVR 窗口 (显示控制器状态的小窗口) 在标题上选择以打开菜单。
    2. 选择"创建系统报表"。
    3. 保存到文件。
    4. 将生成的文件直接附加到反馈中心条目。
6. 如果你的反馈与 SteamVR 性能有关，请收集混合现实性能跟踪： 
    1. 选择" **重新创建我的问题"** 按钮。
    2. 在"包含关于的数据"旁边的下拉列表中，选择"**混合现实性能"。**
    3. 确保游戏正在运行，然后选择"开始 **捕获"。**
    4. 在游戏上花费几秒钟来捕获跟踪。 不要捕获跟踪超过 10-15 秒，否则它太大，无法提交。
    5. 选择"**停止捕获"。**
7. 完成 **其余** 字段后，选择"提交"。

如果你有要分享的问题或意见，还可以在我们的 Steam 论坛上 [与我们联系](http://steamcommunity.com/app/719950/discussions/)。

## <a name="see-also"></a>另请参阅

* [使用 Windows Mixed Reality 对 SteamVR 进行故障排除](steamvr-questions.md)
* [在应用程序中使用Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [在 Unity 中使用 HP 控制器](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [在 Unreal 中使用 HP 控制器](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [提交 bug 和反馈](filing-feedback.md)
