---
title: HP 回音 G2 常见问题解答
description: 有关使用 HP 回音 G2 耳机的常见问题
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，性能
appliesto:
- Windows 10
ms.openlocfilehash: 77d1d7273d1e73af4655ef45bd102220e15d2355
ms.sourcegitcommit: af1e5c9003fc3b7dd0a2f67531f91f954b6a9ea3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2020
ms.locfileid: "94498282"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>HP 回音

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>将耳机电缆连接到电脑时，是否应遵循特定顺序

HP 建议：

- 在连接到电脑或电源之前，先将6米电缆连接到耳机。
- 初始安装后，使6米缆线连接到耳机。
- 当耳机未在使用时，将电源适配器从6米电缆断开连接。

## <a name="what-should-i-do-to-get-a-crisper-image"></a>我应该怎么做才能获得更锐利的图像

如果你认为你的显示看起来有点模糊，可以尝试以下几项：

- 请确保您的耳机正确地位于您的头上，以便您的眼睛与重用功能区有关。
- 尝试调整 IPD (interpupillary 距离) 。 请注意，回音 G2 使用硬件 IPD。 若要进行更改，请在耳机上查找 IPD 调整。
- 如果需要眼镜或联系方式，它们仍是必需的。
- 如果需要清洁重用功能区，请检查你的（如果需要清洁） (仅 microfiber 抹布–无流体) 。
- 由于头戴式耳机的高级设计，在启动设备时，可能会在一段很短的时间内启动设备，直到 Lcd 有机会预热。

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>我接到耳机时出现 7-14 "出现错误" 错误

如果看到 7-14 "出现错误" 错误，请尝试执行以下步骤：

- 请确保已安装最新的驱动程序。
- 尝试将电缆插入到其他 USB-3.0 端口。
- 请使用 USB C 通过包含的适配器来尝试不同的端口。

尝试将电缆插到不同的 USB 集线器。  

> [!NOTE]
> HP 建议仅使用内置于带有回音 G2 设备的主板的 USB 控制器。
> 如果无法连接到设备，请联系[HP 支持](https://support.hp.com/us-en)部门

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>我的电脑从休眠状态 () S4 恢复时出现 13-14 "出现错误" 错误

有时，在恢复过程中，视频卡不能建立连接，因此，从电脑中拔出 USB 类型 C 并重新插入，可能有助于建立连接。

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>混合现实门户显示 "无法在此耳机上运行 Mixed Reality"，但这对于我以前的 WMR 耳机工作正常

出现这种情况的原因可能是 HP 回音 G2 需要更强大的 PC，以确保获得最佳体验。 有关详细信息，请查看最低 [计算机要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>它看起来像是我的左显示内容，右侧显示的是离线和半黑

如果头戴显示设备未运行，则可能会发生这种情况。 由于 HP 回音 G2 HMD 中的高分辨率显示性质，并非所有系统都能呈现本机分辨率。 将来的 Windows 更新会出现一个修补程序，当耳机不是本机分辨率时，将解决呈现问题。

系统无法以本机分辨率呈现的原因有以下几个：

- 系统上的 DisplayPort 可能不兼容1.3，或它可能不支持所有4个车道。
- 如果你使用的是适配器，则它可能不支持 HBR3 兼容，或它可能不支持所有4个车道。
- 如果系统具有混合 GPU，则可能会限制可用于 DisplayPort 的带宽。

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>为什么 HP 运动控制器型号在游戏中显示不正确

虽然大多数游戏不显示控制器或使用驱动程序安装的模型，但某些游戏使用其自己的控制器模型版本来对它们进行自定义或显示有关可用输入的上下文帮助。 通常，这不会阻止游戏的任何功能，但可能会导致混乱甚至视觉对象。 这只能在游戏本身的更新中修复。

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>我的 SteamVR 游戏似乎无法与我的 HP 运动控制器一起正常工作

虽然开发人员正在努力更新其游戏以实现 HP 运动控制器的兼容性，但我们为流上的许多最流行的游戏提供了自定义控制器绑定。 对于 "SteamVR 的 Windows Mixed Reality" 已完全更新到版本1.2.444，当游戏运行时，应自动选取这些绑定。 但是，如果你目前没有注册操作，你可以使用 "SteamVR 设置" 菜单手动搜索自定义绑定配置文件。
任务

- 按下右运动控制器的菜单按钮打开 SteamVR 菜单
- 选择 SteamVR 菜单右下角的 "设置" 图标
- 选择 "控制器" 选项卡
- 选择 "管理控制器绑定" 选项

在此处，你可以将活动控制器绑定更改为 "自定义"，这将打开用于尝试社区共享游戏绑定的选项。
如果尚未为此游戏共享自定义游戏绑定 (或者你对) 尝试过的内容不完全满意，则还可以创建你自己的自定义游戏绑定，甚至还可以通过在几个游戏会话后共享他们来帮助其他人。