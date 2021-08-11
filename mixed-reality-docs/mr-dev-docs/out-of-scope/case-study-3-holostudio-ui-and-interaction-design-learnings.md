---
title: 案例研究 - 3 HoloStudio UI 和交互设计学习
description: HoloStudio UI 和交互设计经验
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195855"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>案例研究 - 3 HoloStudio UI 和交互设计学习

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8)是适用于 HoloLens 的第一个 Microsoft 应用之一。 因此，我们必须为 3D UI 和交互设计创建新的最佳做法。 我们通过大量用户测试、原型制作以及试用和错误来这样做。

我们知道并非每个人都有资源可进行此类研究，因此，我们让 Sr.Holographic Designer， Marcus 一同分享我们在 HoloStudio 开发过程中了解到的三个有关 HoloLens 应用的 UI 和交互设计的知识。

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>问题#1：人们不想移动其创建过程

我们最初在 HoloStudio中将 workbench 设计为一个矩形，就像在现实世界中一样。 问题在于，人们有一生的经验，告诉他们在坐在台前或在计算机前面工作时保持静止，因此他们不会在工作台四处移动，不会从四面八面探索他们的 3D 创建。

![中 workbench 的矩形HoloStudio可让用户从四面四处移动和查看其创建。](images/rectangular-workbench-500px.jpg)

我们已深入了解如何让 workbench 成为圆形工作台，因此没有"front"或 clear 位置，你应位于该位置。 当我们测试这一点时，人们突然开始自行探索其创建。

![圆形 workbench 设计鼓励用户一直进行创建。](images/circular-workbench-500px.jpg)

**我们学到了什么**

请始终考虑用户所习惯的方面。 充分利用其物理空间是一项HoloLens和其他设备无法执行的功能。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>问题#2：模式对话有时会在全息帧外

有时，用户看起来可能不同于应用中需要关注的内容。 在电脑上，只需弹出一个对话框，但如果在 3D 环境中以某人的面执行此操作，则可能会认为对话正在进入其状态。 你需要他们阅读消息，但他们的企图是尝试从消息中消失。 如果你正在玩游戏，这种反应是很好的，但在专为工作而设计的工具中，它并不太理想。

在尝试了一些不同操作后，我们最终决定为对话使用"思考气泡"系统，并添加了一些倾向于，用户可以关注应用程序中需要关注的地方。 我们还进行了"前导"脉冲，这暗示了方向感，以便用户知道要前往何处。

!["思考气泡"系统包括脉冲旋转，这提供了方向感，引导用户了解应用中需要关注的地方。](images/thought-bubble-500px.jpg)

**我们学到了什么**

在 3D 中，提醒用户注意需要关注的问题要困难得多。 使用焦点（如 [空间声音](../design/spatial-sound.md)、光线或思考气泡）可以将用户引导到所需的位置。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>问题#3：有时 UI 可能会被其他全息影像阻止

有时，用户想要与全息影像及其关联的 UI 控件进行交互，但由于另一个全息影像位于其前面，因此被阻止查看。 在开发HoloStudio时，我们使用了试用和错误来找到此解决方案。

![如果与全息影像关联的 UI 控件与用户之间存在另一个全息影像，则可能会HoloLens。](images/ui-blocked-500px.jpg)

我们尝试将 UI 控件移动到更靠近用户，因此它无法被阻止，但发现用户在同时查看远离你的全息影像的同时查看靠近你的控件并不习惯。 但是，如果我们将最靠近用户的全息影像前面的控件移到用户之前，他们看起来就像它与应该影响的全息影像分离。

最后，我们最终虚影 UI 控件，并置于与用户与其关联的全息影像相同的距离，因此两者都感觉已连接。 这样，即使控件被遮盖，用户也能够与之交互。

![解决方案：我们虚影了 UI 控件，该控件允许与控件交互，并使得它感觉已连接到它所影响的全息影像。](images/ghosting-ui-500px.jpg)

**我们学到了什么**

即使被阻止，用户也需要能够轻松访问 UI 控件，因此请找出方法，确保无论全息影像在现实世界中的何处，用户都能完成任务。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus 一维</b><br>Sr.Holographic Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅
* [本能交互](../design/interaction-fundamentals.md)
