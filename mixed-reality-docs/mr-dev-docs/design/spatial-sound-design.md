---
title: 在混合现实应用程序中使用空间音效
description: 空间音效是一个强大的工具，可用于在混合现实应用程序中进行浸入式、可访问性和 UX 设计。
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality，空间音质，设计，样式，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，手势，交互，衰减
ms.openlocfilehash: d51fbdf16d7186c386f124c773f75dacc8c157fd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489207"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>如何在混合现实应用程序中使用声音

您可以使用声音来通知和强化用户应用程序状态的心理模型。 如果合适，请使用 spatialization，将声音置于混合现实世界中。 以这种方式连接听觉和视觉对象时，可以加深交互的直观特性并提高用户信心。
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>何时添加声音

混合现实应用程序通常比2D 应用程序需要更高的声音，因为它们缺乏 tactile 接口。 在通知用户或强化交互时添加声音。

### <a name="inform-and-reinforce"></a>通知和强化

* 对于不是由用户启动的事件（例如通知），请使用声音通知用户发生了更改。
* 交互可能有多个阶段。 使用声音强化过渡过渡。

请参阅下面的交互、事件和建议的声音特征的示例。

### <a name="exercise-restraint"></a>运动挡板

用户无限制音频信息。
* 每个声音应传达特定的有价值信息。
* 当应用播放声音以通知用户时，请暂时减少其他声音的音量。
* 对于按钮悬停声音 (查看以下信息) ，添加时间延迟以防止过多的声音触发。

### <a name="dont-rely-solely-on-sounds"></a>不要仅依赖于声音

使用良好的声音对用户来说十分有价值。 但请确保即使声音关闭，应用程序也可用。
* 用户可能有听力障碍。
* 应用程序可以在一个声音很大的环境中使用。
* 用户可能出于隐私考虑或其他原因禁用设备音频。

## <a name="how-to-sonify-interactions"></a>如何组织交互

混合现实中的交互类型包括手势、直接操作和语音。 使用以下建议的特征为这些交互选择或设计声音。

### <a name="gesture-interactions"></a>手势交互

在混合现实中，用户可以使用鼠标与按钮进行交互。 按钮操作通常在用户释放时发生，而不是按按钮来让用户有机会取消交互。 使用声音来强化这些阶段。 若要帮助用户定位远距按钮，还请考虑使用指针悬停声音。
* 按钮按下声音应该是一个简短的、触感为"单击"的声音。<br/>示例 [：MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按钮-"解压缩"声音应具有类似的触感。 高于按下声音的音高可增强完成感。<br/>示例 [：MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 对于悬停声音，请考虑使用细微且无威胁的声音，例如低频率四下或凹凸。

### <a name="direct-manipulation"></a>直接操作

在 HoloLens 2 上，已表述的手动跟踪支持直接操作用户界面元素。 当没有其他物理反馈时，声音非常重要。

*按钮按下* 声音非常重要，因为当用户到达关键笔画的底部时，用户不会收到任何其他指示。 关键旅行的声音指示器可以是小型、微妙和封闭像素。 与手势交互一样，按钮按下会显示短暂的 tactile 声音，如单击。 Unpresses 应该具有类似的单击声音，但具有凸起的音调。
* 示例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 示例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

难以直观地确认获取或释放操作。 用户的手常常会受到任何视觉效果的影响，而 expression-bodied 对象却缺乏现实世界的 "抓取" 视觉模拟。 声音可以有效地传达成功的获取和释放交互。
* 抓取操作应该具有一个 muffled 的简短 tactile 声音，该声音将提示围绕对象的抓手指。 有时还会有一个 "whoosh" 声音，该声音会导致抓住声音传达手的运动。<br/>示例： [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Release 操作应该获得类似的简短和 tactile 的声音。 它通常比抓住声音和反向顺序下的音调更小，但影响，然后使用 "whoosh" 传达对象正在进行的结算。<br/>示例： [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*绘图* 交互应会获得持久的循环声音，并使用由用户的移动决定的音量。 当用户的手仍在 loudest 时，它应为无提示。

### <a name="voice-interactions"></a>语音交互

语音交互通常具有细微的视觉元素。 使用声音强化交互阶段。 你可能想要使用更音调的声音来区分它们与手势和直接操作声音。

* 使用正面声音进行语音命令 *确认*。 音调和主要音调间隔有效。
* 对语音命令失败使用更短、不太正面的 *语调*。 避免负面声音。 请改为使用更具可自定义性的中性声音来传达应用程序正在从交互中继续。
* 如果应用程序有唤醒词，则当设备开始侦听 时，请使用简短的 *音调*。 在应用程序侦听时，使用 *细微的循环* 声音。

### <a name="notifications"></a>通知

通知指示用户未启动的应用程序状态更改和其他事件。 状态更改可能包括进程完成、消息和电话呼叫。

在混合现实中，对象有时会从用户的视野中移开。 将移动 *的动画* 对象与空间化声音配对，具体取决于对象类型和运动速度。
* 它有助于在动画末尾播放空间化的声音，以通知用户对象的新位置。
* 对于逐步移动，移动过程中发出"whoosh"声音有助于用户跟踪对象。

*消息通知* 声音可能会重复出现，有时是快速连续的。 重要的是它们不突出或声音不小。 中范围正调音有效。

* 传入呼叫声音应具有与手机音素类似的质量。 这些声音会循环播放音乐短语，直到用户应答呼叫。
* 语音通信连接和断开连接应具有短暂的色调声音。 连接声音应为正片，指示连接成功。 断开连接声音应该是一种中性声音，指示调用完成。

## <a name="handle-spatialization"></a>处理 spatialization

Spatialization 使用立体声耳机或扬声器将声音置于混合现实世界中。

### <a name="which-sounds-to-spatialize"></a>哪些声音 spatialize

当声音与具有空间位置的事件关联时，应 spatialized。 这包括 UI、包含的 AI 声音和视觉指示器。

Spatialize *用户界面* 元素，可通过限制他们听到的立体声声音数量来帮助整理用户的 sonic "space"。 在 spatialized 音频反馈时，处理触摸、抓取和释放感觉更自然的交互。 请考虑以下有关这些元素的距离衰减的信息。

Spatialize *直观的指示器* 和三应的 *AI 声音* ，以直观地通知用户这些东西超出了视图的范围。
    
与此相反，应避免 spatialization 用于 *FACELESS AI 声音* ，还应避免缺少定义良好的空间位置的其他元素。 如果没有相关的视觉元素，Spatialization 可能会分散用户以为其无法找到的可视元素。

Spatialization 有一定的 CPU 开销。 许多应用程序最多可以同时播放两个声音。 在这种情况下，spatialization 的成本可能会忽略不计。 可以使用 MRTK 帧速率监视器来判断添加 spatialization 的影响。

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>何时以及如何应用基于距离的衰减

在物理世界，距离较远的声音更静。 音频引擎可以基于源距离对此衰减进行建模。 在传达相关信息时，请使用基于距离的衰减。

与视觉 *指示器、**动画全息* 影像和其他信息性声音之间的距离与用户相关。 使用基于距离的衰减直观地提供提示。

调整每个源的衰减曲线，以适应混合现实世界空间的大小。 音频引擎的默认曲线通常适用于高达 (半公里) 空间。

强化按钮 *操作和其他交互* 的渐进阶段的声音不应应用衰减。 这些声音的增强效果比将距离与按钮通信更重要。 当连续听到许多按钮单击时，变体可能会分散注意力，尤其是在键盘上。

### <a name="which-spatialization-technology-to-use"></a>要使用哪种空间化技术

对于耳机或 HoloLens 扬声器，使用基于 HRTF (的) 相关传输函数。 这些技术为物理世界中的头部周围的声音传播建模。 即使声源位于头部远端，声音也传播到远端的声音，并出现一些衰减和延迟。 说话人平移仅依赖于衰减，当声音位于右侧时，在左声中应用总衰减，而从另一种方式进行平移。 对于"正常听声"侦听器，此方法可能会感到障碍，并且对于有一只听力障碍的侦听器不可访问。

## <a name="next-steps"></a>后续步骤

* [在 Unity 中使用空间声音](../develop/unity/spatial-sound-in-unity.md)
* [Robor表示法的案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 案例研究](case-study-spatial-sound-design-for-holotour.md)
