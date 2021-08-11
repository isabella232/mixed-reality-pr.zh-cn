---
title: 案例研究 - 我在设计团队的第一HoloLens年
description: 2016 年 1 月加入 2D 平面HoloLens 3D 世界时，我从此旅程开始。
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、设计、编辑、个人
ms.openlocfilehash: 2defa24b8e53b28f90a8eb613afcbae7d1b9b1f2d12caaf885e405593df01ffe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192862"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>案例研究 - 我在设计团队的第一HoloLens年

2016 年 1 月加入 2D 平面HoloLens 3D 世界时，我从此旅程开始。 加入团队之前，我在 3D 设计方面经验很少。 这就像中国国家/地名一样，从一个步骤开始的千英里之旅，但在我的案例中，第一步是一个闰年！

![将 Leap 从 2D 到 3D](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*从 2D 到 3D 的跨越*

> *"我就像在不知道如何驾驶汽车的情况下跳到司机的席位一样。我感到十分专注，但非常专注。"*<br>
> — Hae Jin Lee

在过去一年中，我尽可能快地学习了技能和知识，但仍有很多需要学习的知识。 在这里，我撰写了 4 个观察结果，视频教程记录了从 2D 到 3D 交互设计器的转换。 我希望我的经验将激励其他设计人员实现 3D 的跨越。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>"好的 Bye"帧。 Hello spatial /diegetic UI

每当我设计海报、杂志、网站或应用屏幕时，一个定义的框架 (通常是一个矩形) 每个问题的常量。 除非在设备或其他 VR HoloLens阅读此帖子，否则你将从外部到 2D 屏幕在帧中安全保护。  内容是外部内容。 但是，混合 *现实头戴* 显示设备消除了帧 ，因此你位于内容空间中，从内到外浏览内容。

我在概念上理解这一点，但一开始我错误地只是将 2D 思维转移到 3D 空间。 这显然并不起作用，因为 3D 空间具有其自己的独特属性，例如视图更改 (基于用户的头部运动) 以及基于设备属性和使用用户) 的用户 [舒适感](https://www.youtube.com/watch?v=-606oZKLa_s/) (的不同要求。 例如，在 2D UI 设计空间中，将 UI 元素锁定到屏幕的一角是一种很常见的模式，但此 HUD (向上显示) 样式 UI 在 MR/VR 体验中并不自然;它会妨碍用户沉浸到空间中，并让用户感到不便。 这就像在眼镜上有一个令人难看的粒子一样，你正想去除它。 随着时间的推移，我了解到在 3D 空间中定位内容并添加人体锁定行为会更加自然，使内容在相对固定的距离内跟随用户。

![正文锁定](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*正文锁定*

<br>

![已锁定世界](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*已锁定世界*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>片段：出色的模具 UI 的示例

[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)[（Asobo Studio](https://www.asobostudio.com/)为HoloLens开发的第一人称犯罪受害者）演示了一个出色的"死人"UI。 在此游戏中，用户成为一个主角色，一个尝试解决小问题的人。 解决此问题的关键线索会嵌入到用户的物理房间中，并且通常嵌入在虚构对象中，而不是自行存在。 与锁定人体的 UI 相比，这种死锁 UI 往往不太可发现，因此 Asobo 团队特地使用了许多提示，包括虚拟字符的凝视方向、声音、光线和引导符 (例如，指向线索) 位置的箭头，以吸引用户的注意。

![片段 - 模具 UI 示例](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*片段 - 模具 UI 示例*

### <a name="observations-about-diegetic-ui"></a>有关模具 UI 的观察结果

空间 UI (锁定和世界锁定的 ui 和) UI 都有自己的优点和缺点。 我鼓励设计人员尝试尽可能多的 MR/VR 应用，并针对各种 UI 定位方法培养自己的理解和敏感度。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>skeuomorphism and interaction interaction 的返回

Skeuomorphism，一种模拟现实世界对象形状的数字界面，过去 5-7 年在设计行业中一直"不冷"。 当 Apple 最终在 iOS 7 中放弃平面设计时，它看起来就像作为接口设计方法的 Skeuomorphism 最终已死一样。 但随后，新的媒体 MR/VR 头戴显示设备到达市场，似乎再次返回了 Skeuomorphism。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作业模拟器：skeuomorphic VR 设计示例

[作业模拟器](https://jobsimulatorgame.com/)是一款由 [Chemy Labs](https://owlchemylabs.com/) 开发的奇特游戏，是最常见的 Skeuomorphic VR 设计示例之一。 在此游戏中，玩家将经历未来，机器人将取代人类和人类访问一个博物馆，体验在四个不同工作之一上执行一般任务的体验：Auto Chef、Chef、Store Clerk 或 Office Worker。

Skeuomorphism 的好处很明显。 此游戏中熟悉的环境和对象可帮助新 VR 用户感觉更舒适，并存在于虚拟空间中。 它还通过将熟悉的知识和行为与对象及其相应的物理反应相关联，让他们感觉自己受控制。 例如，若要咖啡，人们只需步至咖啡机，按一个按钮，抓取咖啡柄，然后向自己的手部倾斜它，就像在现实世界中一样。

![作业模拟器](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*作业模拟器*

由于 MR/VR 仍是一种开发介质，因此，使用一定程度的旋转态性来解构 MR/VR 技术并向世界各地的更多受众介绍它是必需的。 此外，使用 skeuomorphism 或真实表示形式可能有利于特定类型的应用程序，例如飞行或飞行模拟。 由于这些应用的目标是开发和优化可在现实世界中直接应用的特定技能，因此模拟越接近现实世界，知识越可转移。

请记住，单一性只是一种方法。 MR/VR 世界的潜力远大于这一点，设计人员应努力创建独特的超自然交互 - 在 MR/VR 世界中唯一可能的新体验。 首先，请考虑向普通对象添加超能力，使用户能够满足其基本需求，包括远程传送和全能。

![Doraemon 的守护门 (左侧) Ruby (右侧) ](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon 的 (门) 和 ruby (右侧)*

### <a name="observations-about-skeuomorphism-in-vr"></a>有关 VR 中 skeuomorphism 的观察结果

从 Doraemon 中的"Anywhere door"，到"Ruby 的向导"中的"Ruby Objectss"到"Maurader's map"中的"Maurader's map"（在热门的虚构中，普通对象具有无限功能的示例）。 这些出色的对象可帮助我们直观呈现现实世界与真正者之间的连接，以及什么是和可能的关系。 请记住，在设计幻或超现实对象时，需要在功能与娱乐之间取得平衡。 请注意，出于新奇的原因，创建一些纯奇的创作。

## <a name="understanding-different-input-methods"></a>了解不同的输入方法

当我针对 2D 媒体进行设计时，必须专注于输入的触摸、鼠标和键盘交互。 在 MR/VR 设计空间中，我们的人体成为界面，用户可以使用更广泛的输入方法：包括语音、凝视、手势 [、6-dof](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)控制器，以及提供与虚拟对象的更直观直接连接。

![可用输入HoloLens](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*可用输入HoloLens*

> *"所有内容都最适合某些内容，对于其他内容则最差。"*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

例如，在 HMD 设备上使用裸手和相机传感器的手势输入可释放用户手部，避免手部持有控制器或手部不雅的手套，但频繁使用可能会导致 (（即 gorilla arm) ）。 此外，用户还必须将手放在视线范围内;如果相机看不到手，则不能使用手。

语音输入非常能够遍历复杂的任务，因为它允许用户通过一个命令来 (例如"向我展示 Laika Studio 制作的电影"。)  (其他形式（例如，"正面朝我"命令）将用户正在查看的全息影像定位到用户) 。 但是，语音输入可能无法在干扰环境中正常工作，也可能不适合在非常静默的环境中使用。

除了手势和语音之外，手部跟踪控制器 (例如 Oculus 触控、Vive 等 ) ）是非常流行的输入方法，因为它们易于使用、准确、利用人们属性感知，并提供被动的视觉提示。 [](https://en.wikipedia.org/wiki/Proprioception)但是，这些好处的代价是无法无手操作和使用全指跟踪。

![Senso (Left) 和 Manus VR (Right) ](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (Left) 和 Manus VR (Right)*

虽然不及控制器那么受欢迎，但由于 MR/VR 波次，手套再次获得支持。 最近，通过将 EEG 或 EMG 传感器集成到头戴显示设备（例如 [MindMaze VR](https://www.mindmaze.com/) (）来开始成为虚拟环境界面的智能输入) 。

### <a name="observations-about-input-methods"></a>有关输入方法的观察结果

这些只是 MR/VR 市场中提供的输入设备示例。 在行业成熟并同意最佳做法之前，它们将继续激增。 在此之前，设计人员应始终了解新的输入设备，并熟悉其特定项目的特定输入方法。 设计者需要在限制内寻找创意解决方案，同时发挥设备的优势。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>绘制场景并测试头戴显示设备

当我使用 2D 时，我主要只是绘制内容。 但是，在混合现实空间中，这是不够的。 我必须绘制整个场景，以更好地想象用户和虚拟对象之间的关系。 为了帮助我的空间思维，我开始在 ["第 4D](https://www.maxon.net/en/products/cinema-4d/overview/) 年"中绘制场景，有时在 [Maya](https://www.autodesk.com/products/maya/overview/)中为原型制作创建简单的资产。 我在加入 HoloLens 团队之前从未使用过任何一个程序，但使用这些 3D 程序肯定有助于我熟悉新术语，例如着色器以及[IK (反](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)运动) 。 [](https://en.wikipedia.org/wiki/Shader)

**"无论在 3D 中绘制场景有多接近，头戴显示设备的实际体验几乎与草图几乎不一样。这就是在目标头戴显示设备中测试场景很重要的原因。" — Hae Jin Lee**

对于HoloLens原型制作，我尝试了混合现实教程[中开始的所有](../develop/unity/tutorials.md)教程。 然后，我开始使用 Microsoft 为开发人员提供的 [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) 来加速全息应用程序的开发。 遇到问题时，我向问答论坛 HoloLens[问题&了问题](https://forums.hololens.com/categories/questions-and-answers/)。

在基本了解HoloLens原型制作后，我想让其他非编码人员自行制作原型。 因此，我学习了一个视频教程，介绍如何使用 HoloLens。 我简要介绍了基本概念，因此，即使你在开发方面没有经验HoloLens，也应该能够继续学习。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我为非程序员（如自己）学习了这个简单的教程。*

对于 VR 原型制作，我学习 [了 VR Dev School](https://learn.vrdev.school/) 的课程，还学习了 [3D Content Creation for Virtual Reality](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) at Lynda.com。 VR Dev School 为我提供了更深入的编码知识，Lynda 课程提供了为 VR 创建资产的简短简介。

## <a name="take-the-leap"></a>跨越

一年前，我认为这一切有点有点难以承受。 现在，我可以告诉你，这是 100% 值得努力。 MR/VR 仍是一种非常少的媒体，有许多有趣的可能性需要等待实现。 我在设计未来时能够发挥一小部分的灵感和灵感。 希望你将加入我进入 3D 空间之旅！

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

 
