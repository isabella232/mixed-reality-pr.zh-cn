---
title: 由内而外跟踪的工作原理
description: 有关在 Windows Mixed Reality 耳机中使用的基于照相机的内部跟踪系统的信息。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，从内到外，内幕，跟踪，照相机
ms.openlocfilehash: af7553b27bec63c2ae83bed390c17e1fcf006954
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725868"
---
# <a name="inside-out-tracking"></a>由内而外跟踪

## <a name="how-does-inside-out-tracking-work"></a>内部跟踪如何工作？

**快速答案：** 跟踪系统使用两个可见的低分辨率相机来观察您的环境中的功能。 然后，照相机会附带 IMU 数据的信息，以确定设备在您的环境中的准确位置。

**更多详细信息：** 跟踪系统使用两个低分辨率黑色和白色的照相机来识别您的环境中的特征。 系统会根据观察到的功能三角化其位置，然后将高比特率 IMU 的数据融合在一起，为环境中的 HMD 生成连续的姿势估算。 这两个应用程序都使用姿势信息呈现场景和系统，以便针对时间和位置的任何错误预测更正此呈现。 你的电脑存储环境信息，因此跟踪系统可以召回特定于环境的数据，如房间边界物理位置。 如果在多个房间内使用您的设备，则可以在每个空间中设置不同的边界，并且跟踪系统可以召回特定房间的特定边界。

由于在 Windows Mixed Reality 沉浸式耳机上进行跟踪的工作方式类似于在 [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens)上进行跟踪，你可能会发现此视频非常有用：

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>要使跟踪工作良好，需要执行哪些操作？

要解决这两个问题，以确保跟踪非常适合你：
1. 确保你的电脑满足运行 Windows Mixed Reality 的要求。 如果你的电脑满足 Windows Mixed Reality 的最低要求，则跟踪将有足够的资源可在你的电脑上正常运行。
2. 确保你的环境适合于设备使用的视觉对象跟踪类型。 你应在具有足够光线的环境中使用该设备。 因为设备的工作原理是观察您的环境中的可见性，所以必须有足够的光线，才能观察到该环境。 还必须有足够的视觉功能 (换言之、装饰、对比度等) ，以便跟踪系统正常运行。

## <a name="how-much-light-is-enough-light"></a>光源有多少？

如果您可以轻松地在环境中四处移动，而感觉它太暗，并且如果您能够在房间内观察其他人的功能，那么跟踪系统可能具有足够的光线。 请记住，这种情况太多了，例如，如果你正在查看 sun，照相机可能会变得饱和，无法可靠地跟踪。 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>建议的环境功能数是多少？

此产品设计为在正常环境中工作。 请考虑以下思考试验-如果你在空白房间内使用白名单、白色天花板和白色地面，则跟踪系统将找不到任何要跟踪的功能，并且会失败。 如果你位于作品和装饰作品所涵盖的空间中，则跟踪系统会发现许多功能要进行跟踪，而且效果会很好。 通常，我们已经演示了装饰的家庭和办公室，足以更好地跟踪功能。

## <a name="how-fast-can-i-move-with-the-device"></a>在设备上移动的速度有多快？

该设备旨在支持运动，使其超出了人类头运动通常经历的体验。 可以随意移动。 请记住，在沉浸式头戴显示设备时，您对物理周围环境的认知度已经降低，因此请确保在您的环境中安全移动。

## <a name="where-will-tracking-not-work"></a>跟踪不起作用？

跟踪不能在较暗的空间中工作，因为相机的光线不足，无法看到足够的功能。 跟踪不会做得很好 (或有时在移动汽车（例如飞机、客车、火车、汽车或电梯）的所有) 中工作。 如果有太多的光线或极小的差异，则跟踪也可能会失败。 例如，如果有直接的直射流到房间，照相机可能会降低饱和度，并不会看到常规自然特征。 建议你坚持使用相对照明，如果你必须重合或发现 uncomfortably 鲜的东西，则跟踪系统可能无法正常工作。 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>3DOF 和6DOF 之间的区别是什么？

首先，DOF 是 "自由度" 的简短。 讨论跟踪系统时，这意味着可检测到的移动的程度或类型。 这些变动分为两大类： "旋转" 和 "带转换的旋转"。 3DOF 指的是3度的自由度，表示每个轴的旋转。 简单地说，3DOF 跟踪使你可以向左或向右、向下或向下倾斜 (滚) 侧边。 无法在3DOF 中转换或向前/向后转换。 6DOF 的长度为6度。 它基于3DOF 的旋转，并添加到 it 翻译。 这意味着，可以向前/向后、向下 strafe 左/右和 crouch 并将其关闭。 三个 DOF 跟踪是你通常会在手机或移动版的 VR 产品上发现的跟踪类型，而6DOF 将在更强大的 VR 平台上找到。 一些经验定制为3DOF，只允许3DOF 运动 (旋转) ，即使设备支持6DOF 跟踪。 例如，在 Windows Mixed Reality 中观看360视频。 视频将允许你查看，但不允许你在你的环境中进行演练。

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>我的耳机中 jittering 或断断续续。 我的跟踪是否不起作用？

此类错误有几个源。 请务必将观察到的内容定义为正确的原因，以便解决问题。 请参阅 [故障排除](tracking.md) 部分，以帮助了解发生此问题的原因。

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>我能否将我自己的跟踪技术引入 Windows Mixed Reality？

当前不支持此功能。

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>为什么会看到显示 "找不到边界" 的 UI？

由于安全边界特定于一个物理位置，因此，如果在不同的位置使用该设备，系统就无法找到该边界。 此外，如果您设置了边界，系统将始终查找该边界，即使您在不同的物理位置使用该设备也是如此。 只要在不同的位置使用设备，并且尚未在该位置设置边界，就会看到此 UI。 你可以在每个使用设备的位置设置边界，设备将重新调用特定位置的边界。

如果你在以前设置了边界的位置中使用设备，但设备仍找不到它，则可以设置新的界限，或清除所有环境数据以从设备中删除所有边界。 请参阅 [故障排除](tracking.md) 部分，了解系统为何找不到你的边界和更正此问题的步骤。

## <a name="how-do-i-set-up-tracking"></a>如何实现设置跟踪？

Windows Mixed Reality 中的跟踪很容易使用，无需基础结构或设置。 如果选择了，则可以设置一个虚拟边界以供使用。 有关详细信息，请参阅 [设置边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 部分。

## <a name="how-do-i-clear-tracking-and-environment-data"></a>如何实现清除跟踪和环境数据？

跟踪系统存储某些环境数据，以使其能够回忆到实际的物理位置（如安全界限）。 此信息（包括安全边界）可随时删除。 如果删除此信息，系统将不再识别你的空间或撤回安全边界。 如果要在清除环境数据后使用安全边界，则必须重新设置它。 若要设置新边界，请参阅 [设置边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 部分。 若要删除所有这些数据，请打开 "设置"，导航到 "Mixed Reality"，然后选择左侧菜单的 "环境" 部分。 选择标记为 "清除环境数据" 的按钮以删除所有环境和跟踪数据。

## <a name="see-also"></a>另请参阅
* [跟踪系统疑难解答](tracking.md)
* [运动控制器](controllers-in-wmr.md)
* [Windows Mixed Reality 主页](your-mixed-reality-home.md)
* [在 Windows Mixed Reality 中使用游戏和应用](using-games-and-apps-in-windows-mixed-reality.md)
