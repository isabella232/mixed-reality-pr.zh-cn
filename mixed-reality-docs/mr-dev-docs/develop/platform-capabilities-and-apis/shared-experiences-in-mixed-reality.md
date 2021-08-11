---
title: 混合现实中的共享体验
description: 全息应用可以共享空间定位点，HoloLens设备之间共享空间定位点，使用户能够在现实世界中的同一位置跨多个设备渲染全息影像。
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 共享体验， 混合现实， 全息影像， 空间定位点， 多用户， 多
ms.openlocfilehash: fe738d07e57bd2f62cab8036a09ca6ab31d6544bdd9b6dacc8dde3445fa58214
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193576"
---
# <a name="shared-experiences-in-mixed-reality"></a>混合现实中的共享体验

全息影像不需要仅对一个用户保持私密。 全息应用可能会将空间[](../../design/spatial-anchors.md)定位点从一台HoloLens、iOS 或 Android 设备共享到另一台设备，使用户能够跨多个设备在现实世界中的同一位置渲染全息影像。

## <a name="six-questions-to-define-shared-scenarios"></a>定义共享方案的六个问题

在开始设计共享体验之前，必须定义目标方案。 这些方案有助于阐明你正在设计什么，并建立一个通用词汇，以帮助比较和对比体验中所需的功能。 了解核心问题以及解决方案的不同途径是发现此新媒体中固有的机会的关键。

通过我们的合作伙伴机构的内部原型HoloLens探索，我们创建了六个问题来帮助你定义共享方案。 这些问题构成了一个框架，不旨在详尽地帮助提取方案的重要属性。

### <a name="1-how-are-they-sharing"></a>1.如何共享？

演示文稿可能由单个虚拟用户引导，而多个用户可以协作，或者教师可能会为使用虚拟材料的虚拟学生提供指导 - 体验的复杂性根据用户在方案中拥有或可以具有的代理级别而增加。

![表上具有全息影像的男性和女性](images/man-and-women-with-holograph-on-table-500px.png)

有很多方法可以共享，但我们发现它们中的大多数分为三个类别：

* **演示**：向多个用户显示相同的内容时。 例如：一位教授使用向每个人呈现的同一全息材料向多个学生做讲座。 但是，教授可能有自己的提示和注释，而其他人可能看不到这些提示和注释。
* **协作**：人们共同实现一些共同目标时。 例如：教授提供了一个项目来了解如何进行心动治疗。 学生配对并创建共享技能实验室体验，使医疗学生能够针对心模型进行协作和学习。
* **指导**：当一个人在一对一样式交互中帮助某人解决问题时。 例如：教授在共享体验中执行心动技能实验室时为学生提供指导。

### <a name="2-what-is-the-group-size"></a>2.组大小是什么？

**一对一** 共享体验可以提供强大的基线，理想情况下，可以在此级别创建概念证明。 但请注意，与 (6 人) 的大型组共享可能会导致技术 (数据和网络) 以及社交 (与多个头像一起在房间中) 。 [](https://vimeo.com/160704056) 从小组到大型组 时，复杂性 **呈指数级增长**。

我们发现，组的需求可以分为三种大小类别：
* 1:1
* Small < 7
* 大型>= 7

组大小是一个重要的问题，因为它会影响：

* 全息空间中人员表示形式
* 对象规模
* 环境规模

### <a name="3-where-is-everyone"></a>3.每个人在哪里？

当共享体验可以在同一位置进行时，混合现实的优势将发挥作用。 我们称之为 **共分配**。 相反，当组分布并且至少有一个参与者不在同一物理空间中时 (与 VR) 通常一样，我们称之为远程 **体验**。 通常，组同时有并分配和远程参与者，例如 (会议室中的两个组) 。

![三个人在表上带全息影像](images/three-people-with-holograph-on-table-500px.png)

以下类别有助于传达用户所在的位置：

* **共分配**：所有用户将位于同一物理空间中。
* **远程**：所有用户都将在单独的物理空间中。
* **两** 者：用户将混合使用共分配空间和远程空间。

此问题至关重要，因为它会影响：

* 人们如何通信？
    * 例如：它们是否应该有头像？
* 他们看到的对象。 所有对象是否共享？
* 我们是否需要适应其环境？

### <a name="4-when-are-they-sharing"></a>4.何时共享？

当我们想到共享 **体验时** ，我们通常会考虑同步体验：我们都在一起操作。 但如果包含其他人添加的单个虚拟元素，则有一个 **异步** 方案。 Imagine虚拟环境中留下便笺或语音备注。 如何处理设计上留下 100 个虚拟备注？ 如果他们来自具有不同隐私级别的数十个人，那该做什么？

将体验视为以下时间类别之一：

* **同步**：同时共享全息体验。 例如：两名学生同时进行技能实验室。
* **异步：** 在不同时间共享全息体验。 例如：两名学生进行技能实验室，但在不同的时间处理不同的部分。
* **两** 者：用户有时会同步共享，但其他时间以异步方式共享。 例如：一位教授在以后对学生完成的任务进行评分，并给学生留下第二天的笔记。

此问题很重要，因为它会影响：

* 对象和环境持久性。 例如：存储状态以便可以检索这些状态。
* 用户视角。 例如：也许记住用户在留下笔记时正在查看的内容。

### <a name="5-how-similar-are-their-physical-environments"></a>5.其物理环境有多相似？

在共分配体验之外，两个相同的实际环境的可能性很小，除非这些环境设计为相同。 你更有可能 **拥有类似的环境** 。 例如，会议室类似 ，它们通常有一个中央位置的表，周围有一个四周都由。 另一方面，房间不同，可以在无限布局数组中包括任意数目的装饰。

![表上的 Hol分](images/holograph-on-table-500px.png)

请考虑适合以下两个类别之一的共享体验：

* **类似**：环境往往具有相似的房间、环境光线和声音、物理房间大小。 例如：教授在讲座场 A 中，学生位于讲座会场 B 中。讲座场 A 的台子可能比 B 少，但两人可能都有一个可放置全息影像的物理台。
* **不同：在** 房间设置、房间大小、光线和声音注意事项方面不同的环境。 例如：教授位于焦点房间，但学生位于一个大型讲座场中，由学生和教师填充。

考虑环境很重要 [，](/hololens/hololens-environment-considerations)因为它会影响：

* 人们如何体验这些对象。 例如：如果你的体验对表最有效，而用户没有表？ 或者，在平面图面上，但用户的空间杂乱。
* 对象的规模。 例如：在表上放置六英尺人类模型可能很有挑战性，但心模型会非常成功。

### <a name="6-what-devices-are-they-using"></a>6.它们使用哪些设备？

目前，你通常可能会看到两个沉浸式设备之间的共享 [**体验 (这些设备**](../../discover/immersive-headset-hardware-details.md)对于按钮和相对功能可能略有不同，但考虑到针对这些设备的解决方案，) 或两个全息设备可能略有不同。  但请考虑 **2D** 设备 (/桌面参与者或观察者) 是否是必需的注意事项，尤其是在混合 **使用 2D 和 3D** 设备的情况下。 了解参与者将使用的设备类型非常重要，不仅因为它们具有不同的保真度、数据约束和机会，还因为用户对于每个平台都有独特的期望。

## <a name="exploring-the-potential-of-shared-experiences"></a>探索共享体验的潜力

可以结合上述问题的答案来更好地了解你的共享方案，在扩展体验时克服挑战。 对于 Microsoft 团队来说，这有助于制定路线图来改进我们目前使用的体验，了解这些复杂问题的细微差别，以及如何在混合现实中利用共享体验。

例如，假设Skype发射HoloLens场景之一：用户通过远程定位专家的帮助来修复损坏的光线开关。 [](https://www.youtube.com/watch?v=iBfzs3G8BEA)

![通过 Skype 修复光开关HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*专家从 **2D** 桌面计算机到 3D 混合现实设备的用户提供 **1：1** 指导。 指导 **是****同步的**，物理环境 **不同**。*

这种体验是我们当前体验的一个逐步变化，即将视频和语音范例应用于新媒体。 但是，当我们面向未来时，我们必须更好地定义方案的机会，并构建反映混合现实强度的体验。

考虑一下由 NASA 的 Jet 一体机实验室开发的 [OnSight](https://www.youtube.com/watch?v=XtUyUJAVQ6w)协作工具。 使用 Mars 火星任务中数据的科学家可在 Martian 横向的数据内实时与同事进行协作。

![在以远程方式分开的同事之间进行协作，为 Mars 火星计划工作](images/onsight-nasa-jpl.gif)

*科研人员 **使用三维****和二维** 设备，通过一组较 **小** 的 **远程** 同事来浏览环境。**协作** (**同步**，但可以异步方式进行) 并且物理环境 (虚拟) **类似**。*

像 OnSight 这样的体验会带来新的合作机会。 从物理上指出虚拟环境中的元素，并在其解释其观点时共享其外观。 OnSight 使用浸入式和状态的镜头来重新考虑混合现实中的共享体验。

直观的协作是会话的成为，合作并了解我们如何将此直觉应用到混合现实的复杂性至关重要。 如果我们不仅可以在混合现实中重新创建共享体验，还可以提升它们，但对于未来的工作来说，这是一项转变。 在混合现实中设计共享体验是一项新的令人兴奋的空间-我们只是一开始。

## <a name="get-started-building-shared-experiences"></a>开始构建共享体验

根据您的应用程序和方案，将有各种要求来实现您所需的体验。 其中包括：

* **Match**：创建会话、播发会话、发现和邀请特定人员，同时在本地和远程加入会话。
* **定位点共享**：能够在一个公共的本地空间内对齐多个设备上的坐标，因此对于所有用户，全息影像都显示在同一位置。
* **网络**：能够在所有参与者之间实时同步用户和全息影像的位置、交互和移动。
* **状态存储**：能够在空间中存储全息图的特性和位置，以便进行中型会话加入，稍后重新调用，并抵御网络问题。

共享体验的关键是，多个用户在自己的设备上看到同一个全息影像，这通常通过共享锚点来跨设备对齐坐标来完成。

若要共享锚，请使用 [Azure 空间锚点](/azure/spatial-anchors)：

* 首先，用户放置全息影像。
* 应用创建 [空间锚](../../design/spatial-anchors.md)，以便在世界上准确固定该全息图。
* 可以通过[Azure 空间锚点](/azure/spatial-anchors/)将定位点共享到 HoloLens、iOS 和 Android 设备。

使用共享空间定位点，每个设备上的应用现在都有一个可放置内容的 [通用坐标系统](../../design/coordinate-systems.md) 。 现在，应用可以确保在同一位置定位和定位全息影像。

在 HoloLens 设备上，还可以从一个设备脱机共享锚点。  使用以下链接来确定最适合你的应用程序。

## <a name="evaluating-tech-options"></a>评估技术选项

有各种服务和技术选项可用于帮助构建多用户混合现实体验。  选择路径可能比较困难，因此，要采用以方案为中心的角度，下面详细介绍了一些选项。

## <a name="shared-static-holograms-no-interactions"></a>共享静态全息影像 (无交互) 

在应用中利用 [Azure 空间锚](/azure/spatial-anchors/) 。  通过跨设备启用并共享空间锚，你可以创建一个应用程序，让用户同时查看同一位置的全息影像。  需要跨设备进行额外的同步，以使用户能够与全息影像交互，并查看影像的移动或状态更新。

## <a name="share-first-person-perspective"></a>共享第一人称视角

如果你有受支持的 Miracast 接收方（如电脑或电视），请利用内置 Miracast 支持（对于本地用户），无需其他应用代码。

在应用中利用[MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) ，对于远程用户，或在你要共享的非 Miracast 设备上使用。  启用 WebRTC 连接将在用户之间启用1:1 音频/视频流，并使用数据通道跨设备进行消息传送。  混合现实实现通过向其他人提供 HoloLens 用户的视图的混合现实视频流，来优化 HoloLens。  如果要将视频流扩展到多个远程客户端，则通常使用一个 [MCU 服务提供程序](https://webrtcglossary.com/mcu/) (Multipoint 会议单位) ，如 [SignalWire](https://signalwire.com/)。  可通过 [Freeswitch](https://github.com/andywolk/azure-freeswitch-gpu-windows)获取对 Azure 的一键式 SignalWire 部署。

> [!NOTE]
> 请注意，SignalWire 是付费服务，不属于 Microsoft。

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator 应用程序和演示

利用 [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) 将 [spectator view 功能](spectator-view.md) 引入应用。  启用 (HL、Android、iOS 和摄像机) 的其他设备，查看 HoloLens 在同一位置的不同透视中看到的内容，并接收有关主机的交互的更新 HoloLens 用户与全息影像交互。  使用同一个应用的 spectator 伴随空间，观看、拍摄照片并记录主机对应用程序中的全息影像执行的操作的视频。

**注意：** 图片是通过 iOS/Android 设备上的屏幕截图拍摄的。

## <a name="multi-user-collaborative-experience"></a>多用户协作体验

首先介绍[多用户学习教程](../unity/tutorials/mr-learning-sharing-02.md)，该教程利用了用于本地用户和[Photon SDK](https://www.photonengine.com/PUN)的[Azure 空间锚点](/azure/spatial-anchors/)来同步场景中的内容/状态。 创建本地协作应用程序，其中每个用户在场景中的全息影像上都有自己的观点，每个用户都可以完全与全息影像交互。  所有设备都提供更新，交互冲突管理由 Photon 处理。

> [!NOTE]
> 请注意， [Photon](https://www.photonengine.com/) 是一种非 Microsoft 产品，因此，可能需要使用 Photon 进行计费关系，以实现更高的使用量。

## <a name="future-work"></a>未来工作

组件功能和接口将帮助提供跨各种方案和基础技术的常见一致性和可靠支持。  在此之前，请选择与你要在应用程序中尝试实现的方案相符的最佳路径。

不同的方案或希望使用不同的技术/服务？ 在此页底部的相应存储库中提供 GitHub 问题的反馈，或与[HoloDevelopers 的时差](https://holodevelopers.slack.com/)联系。

## <a name="see-also"></a>另请参阅

* [Azure 空间定位点](/azure/spatial-anchors)
* [DirectX 中的共享空间定位点](shared-spatial-anchors-in-directx.md)
* [Unity 中的共享体验](../unity/shared-experiences-in-unity.md)
* [旁观视图](spectator-view.md)