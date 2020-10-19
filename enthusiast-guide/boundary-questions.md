---
title: 边界常见问题解答
description: 高级 Windows Mixed Reality 排查超出了标准使用者支持文档的边界问题。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，边界
appliesto:
- Windows 10
ms.openlocfilehash: 9ddf9c7f7c5f36567e6968f619dabead9107731d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174396"
---
# <a name="boundary-faqs"></a>边界常见问题解答

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>什么是边界，为何要创建它？

边界定义了在戴上 Windows Mixed Reality 耳机的同时，您可以四处移动的区域。 务必创建一个边界，以帮助避免在耳机中无法看到的障碍。 边界看起来就像混合现实中的白色轮廓，并在接近它时出现。 当你看到此情况时，会减慢移动速度，并避免超出边界或扩展粗枝。

边界内的区域应该无家具、低悬挂光装置、天花板风扇等，因此不会出现任何东西。 [了解 Windows Mixed Reality 中的运行状况和安全性](wmr-health-safety-comfort.md)。

## <a name="how-do-i-create-a-boundary"></a>如何实现创建边界？

首次设置耳机时，安装应用 (混合现实门户) 会指导你完成创建边界的步骤。 但你可以随时创建一个：

1. 在桌面上选择 " **启动 > 混合现实门户** "。
2. 打开 "菜单"。
3. 选择 "设置空间边界" 以创建新边界。

如果其他人使用你的耳机，请确保它们了解边界以及如何使用它。 如果将耳机移动到新位置，则需要设置一个适用于该空间的新边界。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>尝试创建边界时收到错误消息

* 创建边界时，请勿接近墙壁或其他障碍。
* 请确保在跟踪边界时，将耳机置于 waist 高度，并面对计算机。
* 请确保传感器未被阻止且有足够的光线。
* 正在跟踪的空间应大于三个平方米。
* 空间不应太大或太复杂。 坚持使用简单的几何形状，无需太多的旋转。
* 请不要在跟踪时返回到自己的路径。
* 如果你的角落停滞，请重新开始。

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>系统找不到边界，并显示了安装程序 UI

这意味着跟踪系统无法识别您的环境。 如果你在新的环境中，则必须设置 [边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary)。
如果以前在此环境中使用了该设备，并设置了边界：

* 请确保空间充足。
* 请确保已使设备磨损，并看看房间。 设备必须观察您的环境，以了解它的位置。 如果你的边界位于办公桌或表上，则它将找不到边界。
* 拔出设备，关闭 Windows Mixed Reality，并再次将其插入。
* 如果环境中的某些内容已更改，则设备可能不再识别它。 设置新边界。

如果这些步骤不能解决问题，请删除环境数据并再次设置边界。

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>系统向我提供 UI，要求我为所有体验或已安装/所有体验选择设置，并看到我的边界

设备查找界限所用的时间太长。 你可以通过选择使用边界的选项来绕过此消息，并且你将在你的边界存在的情况下进入 Windows Mixed Reality 主页。

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>我经常会看到一条消息，指出 "我已经失去界限"

跟踪系统正在跟踪并识别您的环境。 在此状态下，设备将不再显示你的边界，并且头戴式耳机切换到3DOF，使你能够在实际定位边界之前碰撞到现实世界中的东西。 解决方法：

1. 请确保房间具有足够的光线。
2. 如果最近 redecorated 或重新建模房间，请重新运行安装程序。
3. 拔出设备，关闭 Windows Mixed Reality，并再次将其插入。
4. 清除环境数据并再次设置设备。
5. 如果消息仍然存在，请与客户支持联系。

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>出现一条消息，表明找不到边界。   应采取何种操作？

Windows Mixed Reality 在识别现有边界时可能会遇到问题。 你可以创建新边界，也可以在 "已安装" 和 "运行" 模式下使用你的设备。

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>消息显示 "跟踪丢失" 或 "我们没有此空间的边界"

您必须创建一个新边界。 为此，请按以下步骤操作：

1. 选择 " **开始 > 混合现实门户**。
2. 打开 "菜单"。
3. 选择 "设置空间边界"。

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>边界始终可见。 如何使其消失？

当你接近它时，会出现边界。 如果边界包含的任何部分都具有较窄或不规则的形状，则您可能最终会接近它并导致其出现，而不像您所希望的那样。 若要解决此问题，请尝试使用更大、更普通的形状再次创建边界。 为此，请按以下步骤操作：

1. 选择 " **开始 > 混合现实门户**。
2. 打开 "菜单"。
3. 选择 "设置空间边界"。

## <a name="can-i-turn-off-the-boundary-temporarily"></a>能否暂时关闭边界？

* 选择 " **开始 > 混合现实门户**。
* 打开 "菜单"。
* 将 "边界" 转换为 "关"。 请确保在边界关闭时保持在一个位置。

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何实现在 "固定" 和 "所有体验" 之间进行选择吗？

如果在头戴显示设备设置期间或更高版本中选择 "固定"，则将使用头戴式耳机而不使用边界。 这意味着，在使用耳机时，您需要停留在一个位置，这样就可以避免出现物理障碍和危害。 您可以坐在下，但不能四处移动。 请记住，障碍可能会造成开销和您的影响。

某些应用程序可能会设计为使用边界，因此，如果你在没有边界的情况下使用它们，则可能无法使用这些应用，也不能具有相同的体验。

如果你选择 "所有体验"，则会设置边界，并将能够使用与边界以及不需要的应用程序和体验。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)