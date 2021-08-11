---
title: 在 Windows Mixed Reality 中使用 SteamVR
description: 了解如何在 Windows Mixed Reality 耳机和控制器上安装和玩兼容 pc 的游戏。
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，游戏，SteamVR，流，系统要求
ms.openlocfilehash: 42459f9b8d661bd01ce489460c5293333034612bc59becccf3d35e0ce506fddb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221368"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>在 Windows Mixed Reality 中使用 SteamVR

Windows Mixed Reality for SteamVR 允许用户在 Windows Mixed Reality 沉浸式耳机上运行 SteamVR 体验。 安装适用于 SteamVR 的 Windows Mixed Reality 后，用户可以从其桌面或流库中启动他们最喜爱的 SteamVR 应用程序，并直接在其 Windows 耳机上播放它们。

## <a name="get-your-pc-ready"></a>准备好你的电脑

* 请确保没有挂起的更新：选择 "**开始 > 设置 > 更新 & 安全 > Windows 更新**。 如果有可用更新，请选择 " **立即安装**"。 如果没有可用的更新，请选择 " **检查更新**"，然后安装任何新更新。
* 电脑要求对于流上的应用和内容有所不同。 请参阅每个标题的最低要求。 使用 GTX 1070 图形卡 (或等效) 并且 Intel®内核™ i7 处理器的电脑应为广泛的头衔提供良好的体验。
* 设置[Windows Mixed Reality](set-up-windows-mixed-reality.md) （如果尚未这样做）。 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>设置 SteamVR 的 Windows Mixed Reality

1. [下载并安装 SteamVR。](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. 准备就绪后，启动 SteamVR。 SteamVR 教程应该会自动启动。

> **注意：** 若要对 SteamVR 设置进行高级故障排除，请确保已安装以下软件组件：
> 1. 安装 [流](http://store.steampowered.com/about/) 并 **登录** ，或 **创建新帐户。**
> 2. 安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)。 戴上耳机后，启动流，你会看到一个对话框，提示你安装 SteamVR。 按照对话框中的提示安装该对话框。
    * 如果看不到弹出窗口，请通过导航到 *库* 的 "*工具*" 部分来安装 SteamVR。 在列表中找到 "SteamVR"，然后右键单击并选择 " *安装游戏*"。
> 3. 安装[SteamVR Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)。

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>在无 internet 访问权限的环境中为 SteamVR 设置 Windows Mixed Reality

**在便携式存储设备上存储所需的媒体**
1. 使用具有完全 internet 访问权限的 PC 上的[流](http://store.steampowered.com/about/)，为 SteamVR 安装[SteamVR](https://store.steampowered.com/app/250820/SteamVR/)和[Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 。
2. 在 "流" 中，打开 "库" 部分，并找到标签为 "工具" 的部件。
3. 安装 SteamVR 后，右键单击 "SteamVR" 条目，然后在生成的弹出菜单中单击 "属性" 条目。
4. 将打开一个具有多个选项卡的新窗口。 选择选项卡 "本地文件"，然后单击标记为 "浏览本地文件" 的按钮。
5. 将打开包含 SteamVR 运行时的目录。 将名为 SteamVR)  (的整个目录复制到所选的便携式介质上 (例如，USB 拇指驱动器) 。
6. 对 SteamVR Windows Mixed Reality，以及要在目标电脑上安装的任何与 SteamVR 兼容的应用程序执行相同的操作。

**在目标电脑上运行 SteamVR**
1. 将便携式存储设备插入目标 PC 后，将 SteamVR、MixedRealityVRDriver 和其他文件夹移动到目标 PC 上的一个便利位置。
![目标电脑上安装的 SteamVR 的 SteamVR 和 Windows Mixed Reality](images/steamvr-install-files.png)

2. 确保 SteamVR 和 MixedRealityVRDriver 位于同一个文件夹中，并打开命令提示符。 就此示例来说，我们假设包含文件夹位于 *C:\SteamVRInstall*。 在这种情况下，应在命令提示符下运行：
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
 (请注意，如果运行的是32位版本的 Windows，则 `win64` 应改为上述路径的部分 `win32` 。 ) 

这将允许运行时在自定义安装中查找 SteamVR 驱动程序的 Windows Mixed Reality。

4. 若要运行 SteamVR，应双击位于 *SteamVR\bin\win64\vrstartup.exe* 的文件 "vrstartup.exe"，或者在目标 PC 运行32位版本的 Windows 的情况下，双击该文件 *SteamVR\bin\win32\vrstartup.exe* 。

[有关详细信息和故障排除，请参阅 Steamworks 文档页](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)。

## <a name="play-steamvr-games"></a>玩 SteamVR 游戏

1. 将耳机连接到电脑上，并打开运动控制器。
2. 加载 Windows Mixed Reality home 并显示控制器后，请在桌面上打开流应用。
3. 使用流应用从您的流库中启动 SteamVR 游戏。

**提示**：若要在不停用耳机的情况下启动 SteamVR 游戏，请使用桌面应用 (**启动 > 桌面**) ，在 Windows Mixed Reality 内查看 PC 桌面并与其交互。

## <a name="using-motion-controllers-with-steamvr"></a>将运动控制器用于 SteamVR

不同游戏中的运动控制器使用方式有所不同。 下面是一些可帮助你入门的基础知识：

* 若要打开 "流" 仪表板，请在左或右操纵杆上按向下。
* 若要退出 SteamVR 游戏并返回 Windows Mixed Reality 主页，请按 "Windows" 按钮。

## <a name="changing-the-resolution"></a>更改分辨率

如果你想要以更高的分辨率玩游戏，可以随时在 > SteamVR 设置 > 应用程序窗口中调整应用程序分辨率滑块。 * * 当使用较高的分辨率乘数时，您会希望游戏对您的 PC 造成更大的压力。 如果增加乘数并查看性能下降，请将滑块重新调整为默认级别，并重新启动游戏以确保更改生效。![调整应用程序分辨率](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>使用多个耳机

如果你是一位 VR 发烧，你可能会定期在同一台电脑上使用多个 VR 耳机。 如果是这样，请注意，当 Windows Mixed Reality 耳机接通电源时，SteamVR 游戏将始终启动到 Windows Mixed Reality 耳机。 如果要在另一个耳机上启动 SteamVR 游戏，请确保先拔出 Windows Mixed Reality 耳机，然后再继续。

## <a name="preview-programs"></a>预览计划

我们发布定期更新，以提高在 Windows Mixed Reality 沉浸式耳机上使用 SteamVR 的性能、可靠性和总体体验。 尽管这些预览程序都不是必需的，但如果想要更快地 (更新，并向我们提供有关这些更新的反馈，则建议你加入这些程序！ ) 。

### <a name="windows-mixed-reality-for-steamvr-beta"></a>SteamVR Beta 的 Windows Mixed Reality

SteamVR 的 Windows Mixed Reality 是从流应用商店中安装的组件，可使 SteamVR 与 Windows Mixed Reality 耳机一起工作。  我们会定期将更新发布到此 "桥"，然后自动将其安装。

如果您想要更频繁地获取更新，我们鼓励您加入我们的公共 Beta。  更新首先会转向我们的测试人员，并在将更新发布给所有用户之前，使用他们的反馈来确保更新质量高。  如果你不在我们的 Beta 版计划中，你最终会获得所有相同的修补程序和功能，但在我们的 Beta 用户进行测试后即可。

加入：

  1. 在 "流" 中，使用 " **库** " 菜单下的下拉箭头来筛选 **软件**。
  2. 在列表中，右键单击 " **Windows Mixed Reality" SteamVR** "，然后选择"**属性**"。
  3. 选择 " **测试** 版" 选项卡。
  4. 选择 **"beta-公共 beta"** 并选择 " **关闭** " 以确认。 "Beta 访问代码" 字段应留空。
  
### <a name="steamvr-beta"></a>SteamVR Beta

SteamVR 是由阀门构建和发布的，在所有 SteamVR 耳机上都是通用的。  它遵循在发布到所有用户之前发布 Beta 成员更新的类似模型。

加入：

  1. 在 "流" 中，使用 " **库** " 菜单下的下拉箭头来筛选 **工具**。
  2. 在列表中，右键单击 **SteamVR** ，然后选择 " **属性**"。
  3. 选择 " **测试** 版" 选项卡。
  4. 选择 **"beta-公共 beta"** 并选择 " **关闭** " 以确认。  "Beta 访问代码" 字段应留空。 ![切换到 SteamVR 的 "属性" 对话框中的 "SteamVR beta"。](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Windows 预览体验计划

Windows Mixed Reality 是 Windows 10 的一部分。  影响 SteamVR 用户的许多修补程序和功能都带有 Windows 操作系统。  如果要尝试最新的 Windows 10 预览版，我们建议加入[Windows 有问必答计划](https://insider.windows.com)。

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>为 SteamVR 应用启用运动 reprojection

SteamVR 的 Windows Mixed Reality 具有试验性运动 reprojection 功能，使 90 FPS reprojection 更平稳。

启用动作 reprojection 后，所有流的 VR 游戏将以1/2 帧速率呈现通常 (45 fps，而不是 90 fps) ，而 Windows Mixed Reality for SteamVR 使用 GPU 生成的运动向量来推断下一帧。 对于在给定的 PC 上可靠地命中 60 FPS + 的 SteamVR 游戏，这应该会在保持舒适的体验的同时，偶尔产生稳定的 90 FPS 体验。

可用的运动 reprojection 模式如下所示：

* **SteamVR 每个应用的设置**：允许通过 SteamVR 设置 UI 控制运动 reprojection。 然后，可以打开 "SteamVR 设置"，> Per-Application 视频 "设置中选择" 视频 "，然后选择" 运动平滑处理 "选项。
* **自动**：当游戏呈现速度太慢而无法维护 90 FPS 时，使运动 reprojection 自动打开。 当游戏开始维护 90 FPS 或在小于 45 FPS 时开始呈现时，运动 reprojection 将关闭。 异步旋转 reprojection 始终处于启用状态。
* **运动向量**：强制应用程序始终以半帧速率和运动矢量 reprojection 运行。
* **None**：禁用运动 reprojection。

**应为 Visual Artifacts** 

1. 如果使用的应用程序分辨率大于150%，则可能会遇到模糊效果。 使用运动 reprojection 时，我们建议使用小于150% 的值。
2. 清晰对比度边缘或文本（特别是在游戏中的 HUDs 或菜单上）可能会因为 disocclusion 而暂时歪曲或失真。
3. 在您的 PC 上，SteamVR 家庭和很多其他不可靠地碰到 50-60 FPS 的游戏将继续在此模式下出现不佳的体验。
4. 某些游戏已报告为以50% 速度运行，或延迟延迟 (lag) 。 通过以下[Windows 反馈中心](filing-feedback.md)说明报告这些游戏。

最初，我们对最近的一代 NVidia Gpu 进行了实验性支持。 我们将继续循环访问更多 Gpu 上的 reprojection 支持，并积极倾听你的反馈。

**支持的 gpu：** 安装了 Windows Mixed Reality 兼容图形驱动程序的 Nvidia GeForce GTX1060、AMD RX470 或更高。

若要启用运动 reprojection：

1. 请确保已使用上述说明选择加入 **SteamVR Beta 的 Windows Mixed Reality** 。
2. 打开 SteamVR 仪表板。
3. 选择左侧带有 Windows Mixed Reality 徽标的按钮以打开 SteamVR 设置的 **Windows Mixed Reality** 。
4. 在弹出的 UI 中，选择 "图形" 选项卡。
5. 选择 "自动" 作为 "默认 SteamVR 应用动作 reprojection 模式" 以启用自动运动 reprojection。

![启用 SettingsUX 的 LSR & LSR 指示器](images/settingsux-enable-lsr.gif)

**运动 Reprojection 指示器**

运动 reprojection 指示器有助于诊断试验性自动运动 reprojection 功能的问题。 如果设置为 true，则会在自动运动 reprojection 过程中的耳机显示的左上角看到指示器。 此指示器的颜色和位置与当前运动 reprojection 模式相对应-有关示例，请参阅下图。

![mvLSR 指示器](images/mvLSRIndicator.png)

绿色 = 运动 reprojection 是关闭的，因为应用程序可以以完整的帧速率呈现。

蓝绿色 = 运动 reprojection 为 on，因为应用程序是 cpu 界限。

Blue = 运动 reprojection 为 on，因为应用程序是 gpu 界限。

Red = 运动 reprojection 为 off，因为应用程序的运行时间不到半帧率;如果启用，请尝试减少超采样。

绿色 + 青色 + 蓝色 = 运动 reprojection 为半帧速率模式，或应用程序请求运动 reprojection。

## <a name="sharing-feedback-on-steamvr"></a>在 SteamVR 上共享反馈

如果要改善 Windows Mixed Reality SteamVR 体验，你的反馈非常有用。 通过[Windows 反馈中心](filing-feedback.md)提交所有反馈和 bug。 请遵循这些建议，帮助我们充分利用您的反馈意见：

1. 在 "反馈中心" 中，指出你要在 "哪种类型的反馈" 中报告新问题。 部分。
2. 选择 " **混合现实** " 类别和 " **应用** " 子类别。
3. 在问题摘要中放入 "SteamVR" 一词。 这可以帮助我们找到你的反馈。
4. 描述遇到问题时使用的 SteamVR 游戏或应用程序。
5. 考虑将 SteamVR 系统报表附加到你的反馈。 这提供了更多的日志，可帮助我们诊断你的问题。
    1. 在 "SteamVR" 窗口中 (显示控制器状态的小窗口) 选择标题以打开菜单。
    2. 选择 "创建系统报表"。
    3. 保存到文件。
    4. 直接将生成的文件附加到反馈中心条目。
6. 如果你的反馈与 SteamVR 性能有关，请收集混合现实性能跟踪： 
    1. 选择 " **重新创建我的问题** " 按钮。
    2. 在 "包含有关的数据" 旁边的下拉菜单中，选择 " **混合现实性能**"。
    3. 请确保游戏正在运行，然后选择 " **开始捕获**"。
    4. 花费几秒钟时间来捕获跟踪。 请勿捕获超过10-15 秒的跟踪，或者将过大，无法提交。
    5. 选择 " **停止捕获**"。
7. 完成剩余字段后，选择 " **提交** "。

如果你有任何疑问或意见要分享，你也可以通过我们的 [流论坛](http://steamcommunity.com/app/719950/discussions/)联系我们。

## <a name="see-also"></a>另请参阅

* [SteamVR 与 Windows Mixed Reality 疑难解答](steamvr-questions.md)
* [在 Windows Mixed Reality 中使用游戏和应用](using-games-and-apps-in-windows-mixed-reality.md)
* [在 Unity 中使用 HP 控制器](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [在 Unreal 中使用 HP 控制器](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [提交 bug 和反馈](filing-feedback.md)
