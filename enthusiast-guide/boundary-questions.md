---
title: 边界常见问题解答
description: 高级 Windows Mixed Reality 排查超出了标准使用者支持文档的边界问题。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，故障排除，错误，帮助，支持，边界
appliesto:
- Windows 10
ms.openlocfilehash: c1d6a10ae6ed50f7b9088b26c78cde4ccf8386ea0603c39e107ed23910db9308
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187967"
---
# <a name="boundary-faqs"></a>边界常见问题解答

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>什么是边界，为何要创建它？

边界定义了在戴 Windows Mixed Reality 耳机时可以在中四处移动的区域。 务必创建一个边界，以帮助避免在耳机中无法看到的障碍。 边界看起来就像混合现实中的白色轮廓，并在接近它时出现。 当你看到此情况时，会减慢移动速度，并避免超出边界或扩展粗枝。

边界内的区域应该无家具、低悬挂光装置、天花板风扇等，因此不会出现任何东西。 [了解 Windows Mixed Reality 中的运行状况和安全性](wmr-health-safety-comfort.md)。

## <a name="how-do-i-create-a-boundary"></a>如何实现创建边界？

首次设置耳机时，安装应用 (混合现实门户) 会指导你完成创建边界的步骤。 但你可以随时创建一个：

1. 在桌面上选择 " **启动 > 混合现实门户** "。
2. 打开 "菜单"。
3. 选择 "设置空间边界" 以创建新边界。

如果其他人使用你的耳机，请确保它们了解边界以及如何使用它。 如果将耳机移动到新位置，则需要为空间设置新边界。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>尝试创建边界时收到错误消息

* 创建边界时，请勿接近墙壁或其他障碍。
* 请确保在跟踪边界时，将耳机置于 waist 高度，并面对计算机。
* 请确保传感器未被阻止且有足够的光线。
* 跟踪的空间应大于3个平方米。
* 空间不应太大或太复杂。 使用旋转并转到简单的几何形状。
* 请不要在跟踪时返回到自己的路径。
* 如果你的角落停滞，请重新开始。

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>系统找不到边界，并显示了安装程序 UI

这意味着跟踪系统无法识别您的环境。 如果你在新的环境中，则必须设置 [边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary)。
如果以前在此环境中使用了该设备，并设置了边界：

* 请确保空间充足。
* 请确保已使设备磨损，并看看房间。 设备必须观察您的环境，以了解它的位置。 如果你的边界位于办公桌或表上，则它不会找到你的界限。
* 拔出设备，关闭 Windows Mixed Reality，并再次将其插入。
* 如果环境中的某些内容已更改，则设备可能不再识别它。 设置新边界。

如果这些步骤不能解决问题，请删除环境数据并再次设置边界。

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>系统向我提供 UI，要求我为所有体验或已安装/所有体验选择设置，并看到我的边界

设备查找界限所用的时间太长。 你可以通过选择 "使用边界" 选项跳过此消息，并且你将转到你的边界存在的 Windows Mixed Reality home。

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>我经常会看到一条消息，指出 "我已经失去界限"

跟踪系统正在跟踪并识别您的环境。 在此状态下，设备不能再显示你的边界。 头戴式耳机切换到3DOF，使你能够在现实世界中碰撞。 请尝试执行以下步骤来解决此问题：

1. 请确保房间具有足够的光线。
2. 如果最近 redecorated 或重新建模房间，请重新运行安装程序。
3. 拔出设备，关闭 Windows Mixed Reality，并再次将其插入。
4. 清除环境数据并再次设置设备。
5. 如果消息仍然存在，请与客户支持联系。

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>出现一条消息，表明找不到边界。 应采取何种操作？

Windows Mixed Reality 在识别现有边界时可能会遇到问题。 你可以创建新边界，也可以在 "已安装" 和 "运行" 模式下使用你的设备。

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>消息显示 "跟踪丢失" 或 "我们没有此空间的边界"

创建新边界：

1. 选择 " **开始 > 混合现实门户**。
2. 打开 "菜单"。
3. 选择 "设置空间边界"。

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>边界始终可见。 如何使其消失？

当你接近它时，将显示边界。 如果边界包含带有窄或不规则形状的任何部分，则可能最终会接近它。 边界显示的频率可能比你喜欢的更多。 尝试使用更大、更普通的形状再次创建边界，以解决此问题：

1. 选择 " **开始 > 混合现实门户**。
2. 打开 "菜单"。
3. 选择 "设置空间边界"。

## <a name="can-i-turn-off-the-boundary-temporarily"></a>能否暂时关闭边界？

* 选择 " **开始 > 混合现实门户**。
* 打开 "菜单"。
* 将 "边界" 转换为 "关"。 请确保在边界关闭时保持在一个位置。

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何实现在 "固定" 和 "所有体验" 之间进行选择吗？

如果在头戴显示设备设置期间或更高版本中选择 "固定"，则将使用头戴式耳机而不使用边界。 使用耳机时，需要保持在一个位置，以避免物理障碍和抵御危险。 您可以坐在下，但不能四处移动。 请记住，障碍可能会造成开销和影响。

某些应用程序可能设计为使用边界。 如果在没有边界的情况下使用这些方法，则可能无法正常工作或提供相同的体验。

如果你选择 "所有体验"，则会设置边界，并可以使用在没有边界的情况下使用和使用的应用程序和体验。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)