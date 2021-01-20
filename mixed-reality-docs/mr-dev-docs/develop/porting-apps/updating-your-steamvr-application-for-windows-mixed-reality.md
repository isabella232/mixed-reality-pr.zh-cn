---
title: 更新适用于 Windows Mixed Reality 的 SteamVR 应用
description: 更新 SteamVR 应用程序以最大程度地兼容 Windows Mixed Reality 耳机的最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，兼容性，移植，HoloLens 第一代，混合现实耳机，windows mixed reality 耳机，迁移，Windows 10，流，运动控制器，haptics
ms.openlocfilehash: b6d92d558218f71af0e8c7693f64a50a44524c63
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583821"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>更新适用于 Windows Mixed Reality 的 SteamVR 应用

我们鼓励开发人员测试并优化其 SteamVR 体验，以便在 Windows Mixed Reality 耳机上运行。 本文档介绍了在 Windows Mixed Reality 上体验出色运行的常见改进。

## <a name="initial-setup-instructions"></a>初始设置说明

若要在 Windows Mixed Reality 上开始测试您的游戏或应用程序，请确保先遵循我们的 [入门指南。](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

## <a name="controller-models"></a>控制器型号

1. 如果应用呈现控制器模型：
    * 使用 [Windows Mixed Reality 运动控制器模型](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * 使用 IVRRenderModel：： GetComponentState 获取对组件部分的本地转换 (例如，指针姿势) 
2. 具有左右手使用习惯概念的经验应从输入 Api 获取提示，以区分控制器 [ (Unity 示例) ](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>控制

设计或调整控件布局时，请记住以下保留命令集：
1. 在 **左侧和右侧的模拟操纵杆** 中，会保留在 " **流" 仪表板** 中。

> [!NOTE]
> 如果使用的是 HP 回音 G2 控制器，请单击 " **流" 仪表板** 的 "向右菜单按钮"。

2. **Windows 按钮** 将始终向 Windows Mixed Reality 主页返回用户。

如果可能，则默认为基于操纵杆的 teleportation，以匹配 [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行为

## <a name="tooltips-and-ui"></a>工具提示和 UI

许多 VR 游戏都利用运动控制器工具提示和覆盖来向用户的应用程序或游戏讲解最重要的命令。 为 Windows Mixed reality 优化应用程序时，我们建议查看此部分体验，确保工具提示映射到 Windows 控制器模型。

此外，如果你在其中显示了控制器图像的任何点，请确保使用 Windows Mixed Reality 运动控制器提供更新的图像。

## <a name="haptics"></a>Haptics

从 [windows 10 2018 年4月的更新](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)开始，现在支持 Haptics 在 Windows Mixed Reality 上的 SteamVR 体验。 如果你的 SteamVR 应用或游戏已包含对 haptics 的支持，则它现在应 (，而不会) 使用 [Windows Mixed Reality 运动控制器](../../design/motion-controllers.md)的其他工作。

Windows Mixed Reality 运动控制器使用标准的 haptics 马达，而不是在其他 SteamVR 运动控制器中找到的线性传动装置。 这可能会导致用户体验略有不同。 因此，建议通过 Windows Mixed Reality 运动控制器来测试和优化 haptics 设计。 例如，有时短 haptic 脉冲 (5-10 ms) 在 Windows Mixed Reality 运动控制器上不太明显。 若要生成更明显的脉冲，请尝试发送更长的 "单击" (40-70 ms) ，以使该马达更长时间启动，然后再次将其关闭。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>从 Windows Mixed Reality 开始菜单启动 SteamVR 应用

对于通过流分发的 VR 体验，我们已 [更新 SteamVR 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 以及最新的 [windows 版本](https://insider.windows.com)。 SteamVR 标题现在会自动显示在 "所有应用" 列表的 "Windows Mixed Reality 开始" 菜单中。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 徽标

若要为标题显示 Windows Mixed Reality 支持，请转到应用登录页上的 "编辑存储页" 链接，选择 "基本信息" 选项卡，然后向下滚动到 "虚拟现实"。 取消选中 "隐藏 Windows Mixed Reality"，然后发布到应用商店。

## <a name="bugs-and-feedback"></a>Bug 和反馈

如果要改善 Windows Mixed Reality SteamVR 体验，你的反馈非常有用。 通过 [Windows 反馈中心](/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有反馈和 bug。 下面是 [有关如何使你的 SteamVR 反馈尽可能有用](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)的一些提示。

如果你有任何疑问或意见要分享，你也可以通过我们的 [流论坛](https://steamcommunity.com/app/719950/discussions/)联系我们。

## <a name="faqs-and-troubleshooting"></a>常见问题和疑难解答

如果正在运行设置或播放体验的一般问题，请 [查看最新的故障排除步骤](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。

## <a name="see-also"></a>另请参阅

* [安装工具](../install-the-tools.md)
* [耳机和运动控制器驱动程序历史记录](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最小电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)