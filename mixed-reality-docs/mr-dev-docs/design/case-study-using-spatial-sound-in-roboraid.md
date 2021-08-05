---
title: 案例研究 - 在 RoboRaid 中使用空间声音
description: 空间音效是视觉中最令人Microsoft HoloLens的功能之一，让用户在对象不见时感知周围发生什么。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、RoboRaid、空间音效、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实 Toolkit、cpu
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208989"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究 - 在 RoboRaid 中使用空间声音

本文介绍体验Microsoft HoloLens[为 RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)混合现实第一人称机创建音频时面临的难题。

## <a name="the-tech"></a>技术

[空间](spatial-sound.md)音效是视觉中最令人Microsoft HoloLens的功能之一，让用户在对象不在视线中时感知周围发生什么。

在 RoboRaid 中，空间声音最明显且最有效的使用是提醒播放器注意其外围视觉之外发生的情况。 例如，违规者可以从房间中扫描的任何墙进入。 如果未面向其输入的位置，可能会错过它。 为了提醒你注意此漏洞，你将听到来自"破坏者"进入位置的一些不同音频，这让你知道需要快速采取行动来阻止它。

## <a name="behind-the-scenes"></a>幕后

为应用创建HoloLens声音非常新且独一无二，因此问题可能难以解决，因为没有任何过去的项目需要引用。 希望这些示例说明我们在创建 RoboRaid 时面临的音频挑战，有助于为你自己的应用创建音频。

### <a name="be-mindful-of-taxing-the-cpu"></a>请注意对 CPU 进行税

空间声音在 CPU 上可能要求很高。 对于 RoboRaid 等繁忙体验，在任何给定时间将空间声音实例数保持在 8 以下至关重要。 通常，设置不同音频事件的实例限制一样简单。 达到限制后发生的任何实例均会被击。 例如，当无人机生成时，其飞行物在任何给定时间都限制为三个实例。 考虑到一次只能生成四架无人机，有三只无人机非常多，因为大脑无法跟踪许多类似声音的音频事件。 这释放了其他空间声音事件的资源，例如准备发射的死难或事故。

### <a name="rewarding-a-successful-dodge"></a>奖励成功的失败者

Dodginging 是 RoboRaid 中最重要的游戏机制之一，也是我们认为真正独特的游戏体验HoloLens机制。 因此，我们希望让成功的球员对球员非常有成就感。 我们在开发早期让 Doppler"whizz-by"听起来相当具有吸引力。 最初，我的计划是使用循环，并使用音量、间距和筛选器实时操作它。 此的实现将非常详细。 在提交资源以生成此模型之前，我们创建了一个价格不贵的原型，该原型使用中烘焙的 Doppler 效果的资产来了解其感觉。 我们的有才能的开发人员进行了此操作，使此 whizz by 资产正好在 0.7 秒后，才将球通过玩家的眼部传递，结果令人赞叹！ 不用说，我们构建了更复杂的解决方案并实现了原型。

*(有关使用内置 Doppler 效果创建音频资产的信息，请参阅 [100 Whooshes in 2](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)minutes .)* 
<br>
![成功推导一个死机的球后，玩家会以一种令人满足的声音来奖励玩家。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>丢弃无效声音

最初，我们希望在玩家成功击球后在玩家后面播放一个爆炸声，但出于多种原因，我们决定放弃这一点。 首先，它并没有像我们用于开店的 SFX 一样有效。 当球面命中你后面的墙时，游戏中也会发生其他会屏蔽该声音的情况。 其次，我们在楼层上没有碰撞，因此当球面命中地而不是墙时，无法播放爆炸。 最后，空间音效的 CPU 成本。 可抓取 (墙中的一个) Scorpion 内部有一次特殊攻击，该攻击可发射大约 8 个投篮。 这不仅在混合中造成巨大混乱，还引入了破解，因为它对 CPU 的命中过于困难。

### <a name="communicating-a-hit"></a>传达命中

我们遇到了一个有趣的问题HoloLens是有效传达球员被命中的难度。 使混合现实体验成功的是故事发生在你身上。 这意味着，你必须确信自己正在自己的房间中与一位机器人相冲突。

显然，球员在被命中时不会感觉任何内容，因此我们必须找到一种方法来让玩家确信他们发生了一些错误。 在传统游戏中，你可能会看到一个动画，让你知道你的字符已命中，或者屏幕可能会闪烁红色，并且你的字符可能会有点发声。 由于这些类型的提示在混合现实体验中不起作用，因此我们决定将视觉提示与一种放大的声音组合在一起，指示你已损坏。 我创建了一个大声音，在组合中非常突出，因此它使一切关闭。 然后，为了使其更加突出，我们添加了一个简短的警告声音，就像一个空子正在接收器一样。 
<br>
![当玩家在 RoboRaid 中命中时，他们会看到视觉提示，但也会获得一个放大的音频提示，告知他们已受损。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>从小扬声器获取大声音

HoloLens扬声器较小且轻量，以满足设备的需求，因此不能期望听到太多低端声音。 与针对智能手机或游戏设备进行开发类似，声音设计者和作者必须注意其音频的频率内容。 我始终设计声音或编写全频率范围音乐，因为不戴耳机是用户的一个选项。 但是，为了确保与HoloLens兼容，我偶尔会运行一个测试，即将 EQ 放在我碰巧要处理的任何一个的 MASTER 中。 EQ 设置包括大约 600 Hz 到 700 Hz 的高通筛选器 (不太) 且低通筛选器在大约 10K () 。 这应该让你大致了解声音在设备上播放。

如果你依赖于音乐中的和弦变化感，你可能会发现，应用此 EQ 设置时，音乐完全失去根感。 为了解决此问题，我向具有一些丰富 (且具有丰富) 并混合起来以获得根后退感的凹凸层添加了另一个层。 有时，使用扭曲来调高音流会提供较高范围中足够的频率内容，让我们的大脑认为其下有一些内容。 这适用于 SFX，例如影响、爆炸或特殊时刻的声音，例如一个头头的超级攻击。 你确实不能依赖低端来让玩家获得影响或重量感。 与音乐一样，使用扭曲来给一些扭曲肯定有帮助。

### <a name="making-your-audio-cues-stand-out"></a>使音频提示突出

当然，团队中每个人都希望音乐音乐、响声和巨大的爆炸;但他们还希望能够听到语音播放或其他任何游戏关键音频提示。

在具有全范围频率的控制台游戏上，你有更多的选项根据声音的重要性划分频率。 对于 RoboRaid，我受频率范围限制，我可以从声音中退出。 如果使用低通筛选器，并且从色谱的较高端开始曲线过长，则声音上不会留下任何内容，因为没有太多低端。

若要使 RoboRaid 声音在设备上尽可能大，我们必须降低整个体验的动态范围，并且通过为不同类型的声音创建清晰的重要性层次结构来广泛使用创作。 根据重要性，我将值从 -2 dB 设置为 -6 dB。 我个人不喜欢在游戏中明显减少，因此我花费了大量时间来优化淡入/淡出计时和音量衰减量。 我们针对空间声音、非空间声音、VO 和干总线设置了单独的总线，而不对音乐进行混响。 然后，我们创建了高优先级、关键和非关键总线，因此资产已设置为转到相应的总线。

我希望音频专业人员能够像在 RoboRaid 上一样，在他们自己的应用上工作， 我等不及看到 (听到！) Microsoft 外部的有才人员将针对这些工作HoloLens。

## <a name="do-it-yourself"></a>自制

发现某些事件 (例如) 声音"更大"（就像填满房间一样）的一个技巧是，为空间声音创建单声道资产，并混合使用 2D 立体声资产，以在 3D 中播放。 这确实需要一些优化，因为立体声内容中信息过多会降低单声道资产的方向性。 但是，获得平衡将带来巨大的声音，使玩家能够朝正确的方向旋转头部。

可以使用下面的音频资产自己试用大声音：

**方案 1**
1. 下载 [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) 并将其设置为播放空间声音，并将其分配给事件。
2. 下载 [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) 并将 设置为在 2D 立体声中播放，并分配与上述相同的事件。 由于这些资产规范化为 Unity，因此会减少这两个资产的量，以便不会进行剪裁。
3. 同时播放这两种声音。 四处移动头部，感觉空间有多大。

**方案 2**
1. 下载 [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) 并将 设置为通过空间声音播放并分配给事件。
2. 自行播放此资产，并将其与方案 1 中的事件进行比较。
3. 尝试对单声道和立体声文件进行不同的平衡。

## <a name="see-also"></a>另请参阅

* [空间音效](spatial-sound.md)
* [RoboRaid for Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
