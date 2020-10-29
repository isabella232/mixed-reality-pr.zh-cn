---
title: 设置常见问题
description: 高级 Windows Mixed Reality 排查超出了标准使用者支持文档的设置问题。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，安装，Windows Mixed Reality 主页，Windows Mixed Reality 门户
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677579"
---
# <a name="setup-faqs"></a>设置常见问题 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>当我插入耳机时，混合现实门户不会打开。

混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。 如果未打开，请在 "搜索" 框中输入 "混合现实门户" 以打开应用。 如果找不到混合现实门户，这可能意味着你需要 [更新到最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何实现在 "固定" 和 "所有体验" 之间进行选择吗？

如果在头戴式耳机设置期间或更高版本中选择 "固定和放置"，则将使用头戴式耳机而不使用边界。 您可以坐在那里，但您需要停留在一个地方，因为您没有边界来帮助您避免物理障碍。 某些应用程序可能会设计为使用边界，因此你可能无法使用这些应用程序，或者如果你在没有边界的情况下使用它们，则可能没有相同的体验。 请参阅 ["什么是边界，为什么要创建一个？"](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one)。

如果你选择 "所有体验"，你将设置一个边界，你可以使用适用于边界以及不需要的应用和体验。 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>了解混合现实首次启动时未运行，并已直接进入 Windows Mixed Reality 主页。

可以按照 [重新运行步骤](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)重新运行学习体验。 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>我的控制器未显示在我的 Windows Mixed Reality 主页中。

请确保控制器具有完全电池并且使用蓝牙正确配对。 尝试使用 Windows 按钮关闭和打开控制器。 如果仍然看不到控制器，请尝试取消配对并重新配对每个控制器： 
* 如果你的耳机有内置收音机，请使用耳机附带的随附应用来取消配对，然后再次配对控制器 (混合现实门户可以帮助你找到正确的配套应用) 。 
* 如果控制器已配对到电脑，请在 " **设备" > "蓝牙 >" 设置** "取消配对并再次配对控制器。 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>我的 Windows Mixed Reality 主页的底层看起来不是正确的高度。

选择 **开始 > 楼层调整** ，一旦将应用放入世界，就会启动，以便在戴上耳机时进行更改。 在此应用中，你将被定向到使用触摸板 (运动控制器) 或方向板 (游戏板) 调整地面高度。 如果地面正确，请使用 Windows 按钮返回到你的主页。

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>我无法在我的桌面上显示我在我的耳机上看到的内容的预览。

Windows Mixed Reality 门户在屏幕底部有一个 " **播放** " 按钮，可让你在桌面屏幕上预览你在手机上看到的内容。 出于性能方面的考虑，此功能仅适用于在 Windows Mixed Reality 上运行的 Pc，超 (90Hz) 。

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到 "出现错误" 错误消息，或在混合现实门户中遇到问题
若要获取有关特定错误代码的详细信息，请查看 [此处](error-codes.md)。 你还可以尝试：

重启 Windows Mixed Reality：
1. 从电脑拔下耳机电缆。
2. 重启你的电脑。
3. 重新连接耳机。

确保你的电脑能识别你的耳机：
1. 选择“启动”。
2. 在搜索框中键入 "设备管理器"，并在列表中选择它。 
3. 展开 "Mixed reality 设备"，并查看是否列出了你的耳机。 

如果未列出：
1. 将耳机插入电脑上的不同端口（如果可用）。
2. 查看 Windows 更新中的最新软件更新。
3. 卸载并重新安装 Windows Mixed Reality：
    1. 从电脑拔下耳机电缆。
    2. 选择 " **设置" > 混合现实 > 卸载** "。
    3. 如果运动控制器与电脑配对，请选择 " **设置" > 设备 > 蓝牙 & 其他设备** 进行取消配对。 选择每个控制器，然后选择 "删除设备"。 如果控制器与耳机配对，则可以跳过此步骤。
    4. 将您的耳机插回您的 PC 上，重新安装 Windows Mixed Reality。

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>我无法将输入 (控制器、游戏板、鼠标/键盘) 连接到 Windows Mixed Reality。

在戴戴戴显示设备上时，输入应通过耳机的状态传感器自动切换到混合现实体验。 桌面上应显示一个蓝色栏：

![向耳机定向输入的 Windows 桌面](images/1050px-windowsy.png)

如果输入未自动切换，则可能已禁用 "设置" 中的 "自动输入切换" **> 混合现实 > 耳机显示 > 输入切换** 。 你始终可以在键盘上键入 **Windows Key + Y** ，手动将输入切换到你的耳机或返回桌面。

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合现实启动过程中，我停滞在一侧，然后在一层中。

此步骤允许耳机识别空间，并还原任何现有的虚拟楼层和边界。 当你放在你的耳机上时，此扫描过程可能需要长达10秒的时间。 完成后，你将处于 Windows Mixed Reality 主页，否则系统将提示你重新设置边界。

如果扫描过程所用时间超过10秒，则耳机中的邻近感应传感器可能出现问题：
1. 检查是否已从邻近感应传感器中删除不干胶标签。 邻近感应感应器位于耳机内，大致位于 forehead 的中心。
2. 检查邻近感应传感器是否正在将输入切换到你的耳机：使用手指覆盖并抽出几次近程传感器，验证输入是否正在切换到耳机。 你应在电脑顶部看到 " **Windows 键 + Y** " 横幅。 您可以通过在键盘上键入 **Windows Key + Y** ，随时手动切换到耳机的输入。

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>我的 Xbox 控制器不能与 Windows Mixed Reality 一起使用。

* 确保控制器已打开、完全充电并连接到 PC。
* 更换控制器的电池。
* 如果使用的是蓝牙控制器，请在计算机上的 " **设置" > 设备 "> 蓝牙 & 其他设备** ，并确保其配对 (应在页面) 上列出。
