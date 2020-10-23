---
title: 由内而外跟踪的工作原理
description: 有关在 Windows Mixed Reality 耳机中使用的基于照相机的内部跟踪系统的信息。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，从内到外，内幕，跟踪，照相机
ms.openlocfilehash: eda1b323915788f72ae6f4a2efcf51850734eac9
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434606"
---
# <a name="inside-out-tracking"></a>内部跟踪

## <a name="how-does-inside-out-tracking-work"></a>内部跟踪如何工作？

**快速解答：** 跟踪系统使用两个可见的低分辨率相机来观察您的环境中的功能，并将此信息与 IMU 数据融合，以确定设备在您的环境中的确切位置。

**更多详细信息：** 跟踪系统使用两个低分辨率黑色和白色的照相机来识别您的环境中的特征。 系统会根据观察到的功能三角化其位置，并通过融合高比特率 IMU 数据来对此信息进行补充，从而为你的环境中的 HMD 生成连续的姿势估算。 这两个应用程序都使用姿势信息呈现场景和系统，以便针对时间和位置的任何错误预测更正此呈现。 有关您的环境的信息存储在您的 PC 上，以便跟踪系统可以召回特定于环境的数据，例如空间中边界的物理位置。 如果您在多个房间内使用您的设备，则可以在每个房间内设置不同的边界，并且跟踪系统将能够撤回特定房间的特定边界。

由于在 Windows Mixed Reality 沉浸式耳机上进行跟踪的工作方式类似于在 [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens)上进行跟踪，你可能会发现此视频非常有用：

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>要使跟踪工作良好，需要执行哪些操作？

要解决这两个问题，以确保跟踪非常适合你：
1. 确保你的电脑满足运行 Windows Mixed Reality 的要求。 如果你的电脑满足 Windows Mixed Reality 的最低要求，则跟踪将有足够的资源可在你的电脑上正常运行。
2. 确保你的环境适合于设备使用的视觉对象跟踪类型。 你应在具有足够光线的环境中使用该设备。 因为设备的工作原理是观察您的环境中的可见性，所以必须有足够的光线，才能观察到该环境。 还必须有足够的视觉功能 () ，使跟踪系统能够正常运行，。

## <a name="how-much-light-is-enough-light"></a>光源有多少？

一种很好的经验法则是，如果您能够在环境中轻松地四处移动，而且您可以在房间内观察其他人的功能，那么跟踪系统可能具有足够的光线。

## <a name="what-is-the-recommended-amount-of-environmental-features"></a>建议的环境功能量是多少？

此产品设计为在正常环境中工作。 请考虑以下思考试验-如果你处于完全空白的房间 (白名单、白色天花板、白底) ，则跟踪系统将找不到任何要跟踪的功能，并且会失败。 如果你位于作品和装饰作品所涵盖的空间中，则跟踪系统会发现许多功能要进行跟踪，而且效果会很好。 在大多数情况下，我们已经演示了装饰的家庭和办公室，足以更好地跟踪功能。

## <a name="how-fast-can-i-move-with-the-device"></a>在设备上移动的速度有多快？

该设备旨在支持运动，使其超出了人类头运动通常经历的体验。 可以随意移动。 请记住，在沉浸式头戴显示设备时，您对物理周围环境的认知度已经降低，因此，请确保在您的环境中安全地移动。

## <a name="where-will-tracking-not-work"></a>跟踪不起作用？

在较低的房间内，如果相机不能看到充足的功能，则跟踪将不起作用。 通常情况下，跟踪不会执行良好 (或有时在移动汽车（例如飞机、客车、火车、汽车或电梯）的所有) 中工作。

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>3DOF 和6DOF 之间的区别是什么？

首先，DOF 是 "自由度" 的简短。 讨论跟踪系统时，这意味着可检测到的移动的程度或类型。 这些变动分为两大类： "旋转" 和 "带转换的旋转"。 3DOF 指的是3度的自由度，表示每个轴的旋转。 简单地说，3DOF 跟踪使你可以向左或向右、向上/向下或向下倾斜 (滚) 方。 无法在3DOF 中转换或向前/向后进行转换。 6DOF 的长度为6度。 它基于3DOF 的旋转，并添加到 it 翻译。 这意味着，可以向前/向后、strafe 向下、向下和 crouch。 3 DOF 跟踪是你通常在手机或移动版的 VR 产品上发现的跟踪类型，而6DOF 将在更强大的 VR 平台上找到。 一些经验定制为3DOF，只允许3DOF 运动 (旋转) ，即使设备支持6DOF 跟踪。 例如，在 Windows Mixed Reality 中观看360视频。 视频允许您进行查找，但不允许您在您的环境中进行浏览。

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>我的耳机中 jittering 或断断续续。 我的跟踪是否不起作用？

此类错误有几个源。 必须能够将观察到的内容确定为正确的原因，以便解决问题。 请参阅 [故障排除](tracking.md) 部分，以帮助了解发生此问题的原因。

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>我能否将我自己的跟踪技术引入 Windows Mixed Reality？

暂不支持。

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>为什么会看到显示 "找不到边界" 的 UI？

由于安全边界特定于一个物理位置，因此，如果在不同的位置使用该设备，系统将无法找到该边界。 此外，如果您设置了边界，系统将始终查找该边界，即使您在不同的物理位置使用该设备也是如此。 只要在不同的位置使用设备，并且尚未在该位置设置边界，就会看到此 UI。 你可以在每个使用设备的位置设置边界，设备将重新调用特定位置的边界。

如果你使用的是之前设置边界的位置中的设备，但设备仍找不到它，则可以设置新的界限，或清除所有环境数据以从设备中删除所有边界。 请参阅 [故障排除](tracking.md) 部分，了解系统为何找不到你的边界和更正此问题的步骤。

## <a name="how-do-i-set-up-tracking"></a>如何实现设置跟踪？

Windows Mixed Reality 中的跟踪非常易于使用。 不需要任何基础结构或设置，设备将开箱即用。 如果选择了，则可以设置一个虚拟边界以供使用。 有关详细信息，请参阅 [设置边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 部分。

## <a name="how-do-i-clear-tracking-and-environment-data"></a>如何实现清除跟踪和环境数据？

跟踪系统存储某些环境数据，以使其能够回忆到实际的物理位置（如安全界限）。 此信息（包括安全边界）可随时删除。 如果删除此信息，系统将无法再识别你的空间或重新调用安全边界。 如果要在清除环境数据后使用安全边界，则必须重新设置它。 若要设置新边界，请参阅 [设置边界](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 部分。 若要删除所有这些数据，请打开 "设置"，导航到 "Mixed Reality"，然后选择左侧菜单的 "环境" 部分。 单击标记为 "清除环境数据" 的按钮以删除所有环境和跟踪数据。

## <a name="see-also"></a>另请参阅
* [跟踪系统疑难解答](tracking.md)
* [运动控制器](controller-in-wmr.md)
* [Windows Mixed Reality 主页](your-mixed-reality-home.md)
* [在 Windows Mixed Reality 中使用游戏和应用](using-games-and-apps-in-windows-mixed-reality.md)
