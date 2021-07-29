---
title: Kippy 的转义
description: 请与我们探讨，因为我们在 Unreal Engine 中探讨了 Kippy 的转义混合现实应用程序 HoloLens 2。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，混合现实，部署到设备，PC，文档，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757106"
---
# <a name="the-making-of-kippys-escape"></a>Kippy 的转义
![Kippy 的转义英雄图像](images/KippysEscape_1920.jpg)

自动唤醒机器人，使其 Kippy。 你需要放在你的问题解决 hat 上，以帮助它找到返回到其火箭的途径！ 带到 HoloLens 2 并从 Microsoft Store[下载应用](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd)，或者从 GitHub 克隆[存储库](https://github.com/microsoft/MixedReality-Unreal-KippysEscape)，并获得 Kippy 主页安全！  

> [!IMPORTANT]
> 如果要从 GitHub 存储库构建 Kippy 的转义，请确保使用的是 **Unreal Engine 4.25 或更高版本**。

Kippy 的转义是使用 Unreal 引擎4和[混合现实 UX 工具（用于 Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)）生成的开源[HoloLens 2](/hololens/hololens2-hardware)示例应用。 在此文章中，我们将指导你完成从第一个原则和视觉设计到实现和优化体验的过程。 在 [Unreal 开发概述](unreal-development-overview.md)中，可以找到有关通过 MRTK UX 工具开发混合现实应用程序的详细信息。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 HoloLens 2 中的 Microsoft Store 下载应用
如果有 HoloLens 2 设备，则可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>首要原则 

在设置为创建 Kippy 的转义的过程中，我们的目标是创建一个可突出显示[Unreal 引擎 HoloLens 2 支持](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、HoloLens 2 功能和混合现实 Toolkit 的体验。 我们想让开发人员想象一下他们可以通过 Unreal 和 HoloLens 2 创建的内容。  

我们提出了三个针对体验的指导原则：这是一项有趣的交互式工作，并面临进入的障碍。 我们希望经验非常直观，甚至首次混合现实用户都不需要教程。  

## <a name="designing-the-game"></a>设计游戏 

HoloLens 2 可以访问当前在游戏中的其他地方。 对象可以使用您的手直接推送或操作，也可以使用目视跟踪来进行操作。 这些关键功能在 Kippy 的转义中构建了一些有趣的时刻。  

使用独特的 HoloLens 2 功能作为游戏设计的指导，我们只是确定了几种小环境方案。 孤岛非常有用，因为它们可以针对不同的播放机高度进行调整，并提供一些有趣的 bridge 创意。 我们着陆主题古文明与科幻技术相结合，这种想法表明有人通过刻录构建了一种奇怪的能源。 每个孤岛都具有自己的外观，这是一项有助于创建视觉对象的详细信息。 建模和纹理间的良好平衡会使绘图调用对呈现性能的消耗降低，因此，设计风格的外观就是用这一理念设计的。 

![早期游戏设计 ](images/kippys-escape/kippys-escape-img-01.png)
 *将一些更早的草图作为经验*

![第二个 ](images/kippys-escape/kippys-escape-img-02.png)
 *岛呈现* 的呈现

为了保持较短的生产计划，我们同意在没有严格的动画周期的情况下，可以捕获意向和情感。 那么 Kippy 是不是的。 它通过眼睛和简单沉默声音效果 emotes 几个不同的表达式，以帮助指导玩家体验。 

![Kippy 通过其眼睛显示不同的表达式](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy 通过其眼睛显示不同的表达式*

![如果用户需要花费很长时间来解决测验题，Kippy 会向用户提示](images/kippys-escape/kippys-escape-img-04.gif)

*如果用户需要花费很长时间来解决测验题，Kippy 会向用户提示*

除了字符和环境设计外，我们还进行了 concerted 的工作，让游戏变得有趣。 目视跟踪允许我们激发材料和声音属性，其中突出显示了游戏的关键部分。 空间音频有助于使这些级别在播放机的周围处于家里。 能够抓住对象、推送按钮和操作滑杆推动创新的播放器的合作。 务必要确保这些连接点感觉自然。 

![桥接电缆结束时，用户将对其进行接近](images/kippys-escape/kippys-escape-img-05.gif)

*桥接电缆结束时，用户将对其进行接近*

## <a name="building-the-game-mechanics"></a>构建游戏机制 

Kippy 的转义很大程度上依赖于混合现实 UX 工具组件，以使游戏成为交互的（即手交互参与者、边界控件、操控器、滑杆和按钮）。   

[手动交互执行组件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)允许直接和远端操作全息影像。 在 Kippy 的转义开始时，用户有机会设置游戏的位置。 手动光标从用户的掌中进行扩展，可以轻松地操作距离较远的大全息影像，如以下 gif 所示。  

![手动交互执行组件 gif](images/kippys-escape/kippys-escape-img-06.gif)

占位符场景本身可使用 UX 工具的 [边界控件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) 组件进行拖动和旋转。  

在第二个岛上，用户必须选择宝物，并将其放入匹配的插槽中。 这些 gem 附加了操控器，这些 [操控](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) 器允许用户选取它们并将其放置。 

![操控器示例 gif](images/kippys-escape/kippys-escape-img-07.gif)

[Pressable 按钮](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html)是在第三个岛上使用炸弹的关键所在。  

![Pressable 按钮示例 gif](images/kippys-escape/kippys-escape-img-08.gif)

第四个岛上会出现一个 [滑块](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) 组件，触发要引发的最终桥。  

![滑块组件示例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>优化 HoloLens 2 

对于在移动设备上运行的任何体验，请务必关注性能。 Unreal 4.25 包括一个用于支持移动多视图的主要更新，这大大减少了渲染开销并提升了帧速率。 建议在 HoloLens 2 进行优化时，使用 Unreal 查看我们的其他[建议性能设置](performance-recommendations-for-unreal.md)。  

物理学对象在性能方面仍会成本高昂，因此使用了一些巧妙的解决方法。 例如，第三个 "桥" 需要吹一些阻止方法的碎片。 炸弹引爆不会将石子影响为物理学对象，而是通过切换静态石子来实现分解粒子效果。 

![HoloLens 2 gif 的优化示例](images/kippys-escape/kippys-escape-img-10.gif) 

我们还将我们的绘图调用从400减少到 ~ 260： 
* 降低网格复杂性
* 组合网格
* 删除某些初始动态照明元素

虽然我们可能还有更多的操作，但我们认为这是性能和视觉质量之间的良好平衡。  

## <a name="try-it-out"></a>试试看！ 

启动 HoloLens 2 并从 Microsoft Store[下载](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd)应用，或者从 GitHub 克隆[存储库](https://github.com/microsoft/MixedReality-Unreal-KippysEscape)，并自行生成应用！  

## <a name="about-the-team"></a>关于团队

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>插孔抑符</b><br><i>线索游戏设计器</i><br>插孔当前适用于 Microsoft 的混合现实体验，包括 HoloLens 2 项目和 AltspaceVR，以前是 HoloLens 平台团队的设计器。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>夏季 Wu</b><br><i>创建器</i><br>夏季适用于混合现实开发人员平台，并领导团队与 Unreal 引擎相关的工作。</td>
</tr>
</table>

特别感谢我们在 [Framestore](https://www.framestore.com/) 中的朋友，帮助我们将 Kippy 带入生活。 从字符开发到资产设计，再到游戏编程，对此项目的协作是 pivotal 的。