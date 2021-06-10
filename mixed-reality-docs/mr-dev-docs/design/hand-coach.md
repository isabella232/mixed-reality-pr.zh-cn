---
title: 手部指导
description: 了解当系统未检测到要帮助帮助的用户时，如何使用手型指导触发3D 手势。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，手型指导，沉浸式耳机，MRTK，双手，帮助双手，混合现实耳机，windows Mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600426"
---
# <a name="hand-coach"></a>手部指导

![示例：手型指导](images/HandCoach/MRTK_handCoach.jpg)<br>

当系统未检测到用户的手时，手动指导会触发3D 建模。 此功能是一个 "教学" 组件，可帮助用户在未教授手势时引导用户。 如果用户没有在某个时间段完成指定的手势，则会循环一段时间。 手型指导可用于表示按下按钮或选取全息图标。  

## <a name="hand-coach-provided"></a>手写指导

当前交互模型表示各种手势控件，例如滚动、远选和点击显示。 下面是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>中提供的现有手型手势的完整列表：

:::row:::
    :::column:::
       ![接近选择的示例](images/HandCoach/NearSelect.gif)<br>
       **接近选择使用的示例显示如何选择按钮或关闭种不可交互对象**<br>
    :::column-end:::
    :::column:::
       ![空中点击的示例](images/HandCoach/AirTap.gif)<br>
        **空中点击的示例-用于显示如何选择远距离的对象**<br>
    :::column-end:::
    :::column:::
       ![移动示例](images/HandCoach/Move.gif)<br>
       **将对象移动到空间的示例-用于显示如何在空间中移动全息图**<br>
    :::column-end:::
    :::column:::
       ![旋转示例](images/HandCoach/Rotate.gif)<br>
       **演示如何旋转全息影像或对象的 Rotate-Used 示例**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![缩放示例](images/HandCoach/Scale.gif)<br>
       **缩放示例-用于显示如何操作更大或更小的全息影像**<br>
    :::column-end:::
    :::column:::
       ![手掌的示例](images/HandCoach/PalmUp.gif)<br>
        **掌上-建议使用的示例，用于引入手菜单**<br>
    :::column-end:::
    :::column:::
       ![HandFlip 的示例](images/HandCoach/HandFlip.gif)<br>
       **示例-用于打开手形菜单的另一种方式**<br>
    :::column-end:::
    :::column:::
       ![滚动示例](images/HandCoach/Scoll.gif)<br>
       **滚动示例–用于滚动列表或长文档**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>设计概念

对于 Hololens2，我们基于 instinctual 和自然手势设计出了手动交互。 我们认为这对于大多数用户来说是直观的，因此我们不会创建专用的手势学习时间。 相反，我们创建了手形指导，帮助用户了解有关这些手势的问题，或者不熟悉全息图交互。 如果没有学习，我们认为向用户展示如何执行操作，这是最佳选择。 我们发现用户能够找出手势，但需要一些指导。 如果检测到用户不能在某个时间段内与对象交互，则会触发一则手指导，演示正确的抓手和 finger 位置。 

### <a name="intuitive"></a>直观

动画处理时，应该很明显，不会造成任何混淆。 手型动画是尝试提示用户理解的手势的表示形式。 

例如，如果希望用户按下某个按钮，则会触发按下按钮的一只手。

![示例：点击点击](images/HandCoach/NearSelect_unity.gif)<br>
*演示附近点击 Gem 的指导*  

### <a name="hand-scale"></a>手动缩放

我们使用 UI 菜单测试了各种手大小，并感觉到，如果想要调整规模，就会 menacing。 如果它们太小，则很难查看和理解手势。 

**语音和手**

不要指望用户可以通过语音来侦听一组说明，并通过手动指导观看不同说明。 序列化说明，帮助用户专注于争用，从而减少传感器的过载。


## <a name="can-i-create-my-own"></a>我能创建自己的吗？

会！ 我们鼓励你为游戏创建自己的独特手势，并向社区提供反馈！
我们提供了一个可用于你的应用的 Rigged 的 Maya 文件，可在此处下载 <a href="files/HandCoach_MRTK.zip"> HandCoach_MRTK.zip </a>

![在 Maya 中进行动画处理的示例](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya 中闲逛的动画手形的示例*


**推荐的创作工具**

在三维音乐家之间，很多选择使用 [Autodesk 的 Maya，它可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 来转换资产的创建方式。 提供的免提文件是一个 Maya 二进制文件，因此建议使用 Maya 来动画和导出手。 如果希望使用其他三维程序，请参阅 <b>。FBX</b>： <a href="files/HandCoachMRTK_FBX.zip"> 下载 HandCoachMRTK_FBX.zip </a> 来创建自己的控制器设置。 

如果使用提供的可下载 maya 手型文件，则建议将 unity 向下扩展到0.6。

![示例： Maya 中的手型指导远程测试机组](images/HandCoach/MayaExample.png)<br>
*Rigged*

### <a name="technical-specs"></a>技术规格

*   Maya Ascii 格式提供两个文件
*    Right 和左手提供 Maya 二进制格式
*   将 Maya 文件设置为 24 FPS
*   在该文件中，有一个左手的右手，可用于两个右手或单面手势。 仅在默认情况下，才会显示右手。
*   建议在开始和结束时留出大约10帧的缓冲区来淡化
*   如果对具有指定目标的对象进行动画处理，则其最佳方案为动态到默认框或 Null。
*   如果要对物理对象（例如 box）进行动画处理，最佳做法是不在 Maya 中对转换进行动画处理，而是等待在 Unity 中或代码中对其进行动画处理。
*   对于要传达的任何有意义的信息，可见动画应为1.5 秒
*   如果你对动画感到满意：
    *   选择所有接头和制作关键帧
    *   删除控制器，选择接头和网格，并将其导出为 FBX
    *  如果有多个动画，可以使用 Maya 的内置游戏导出程序： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>从 Maya 导出

对动画满意后
* 选择所有接头：选择 > 层次结构

     ![示例：菜单中的层次结构](images/HandCoach/Hierarchy.png)<br>
* 制作动画：切换到动画 > 键 > 制作动画

     ![示例：制作动画菜单位置](images/HandCoach/BakeAnimation.png)<br>
* 删除控制器远程测试机组： Outliner > MainR_Grp 或 MainL_Grp

     ![示例：控制器 Rig 菜单位置](images/HandCoach/ControllerRig.png)<br>

* 导出为 FBX：选择 .JNT + 网格： File > 导出所选内容 (选项框) > 导出选定内容

     ![示例：导出选择菜单位置](images/HandCoach/OptionBox.png)<br>

     ![示例：菜单位置](images/HandCoach/SelectionExport.png)<br>

     ![示例：导出选项菜单位置](images/HandCoach/FBXSelection.png)<br>


 导出为 FBX 并将其放入 Unity 时，将指针向下缩放到0.6。 我们发现这非常适合显示手。 

![示例： Unity 设置](images/HandCoach/HandHintScale.png)<br>
*在 MRTK 中找到 HandCoach_R prefab 的 Unity 设置*


## <a name="implementing-hands-into-your-unity-project"></a>实现对 Unity 项目的动手

### <a name="best-practices"></a>最佳实践

* 建议将 unity 向下扩展到0。6
* 应播放两次，如果未完成，则连续循环，直到手势完成。 应循环访问两次，以确保用户有时间注册并查看手势。 指针应在循环之间淡入和淡出。 
 *  如果用户的手在 HL2 摄像头中可见，但用户不会进行所需的交互，则会在10秒后出现。
*   如果 HL2 照相机看不到用户的手，则会在5秒后出现指针。  
*   如果动画中间的 HL2 相机明显跟踪用户的手，动画将完成并淡出。
*   如果要包括语音，则建议将其对应于手的手势。
*   如果已教手至少一次，则仅在检测到用户卡住时重复手势。
*   如果特定手指/手部位置至关重要，请确保用户可以清楚地了解动画中的这些细微差别。 尝试将手放在一起，使最重要的部分清晰可见。 
* 如果发现手部扭曲，则需要转到 Unity 的"质量"设置，增加双手的数量。 
 转到 Unity 的"编辑">项目设置>"质量>其他>"混合权重"。 确保已选择"4 个关节"，以查看平滑联合。

   ![示例："项目设置"窗口](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>要避免的内容

* 缩放手部太大
* 将手放在离用户太近
* 手只应教授一次。 过度教学可能会导致混淆和混乱
* 将 MRTK 引入 Unity，请在此处下载最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity
  * 材料：Teaching_Hand2
  * 脚本：请参阅 MRTK 手 <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> 部指导的 MRTK 指南 </a>
  * 每项目设置
    * 场景设置为 UWP：可以在配置 [Unity Project for](../develop/unity/Configure-Unity-Project.md) Windows Mixed Reality

## <a name="see-also"></a>另请参阅

* [交互基础](interaction-fundamentals.md)
* [资产创建过程](asset-creation-process.md)
* [笔势](./interaction-fundamentals.md)
* [安装工具](../develop/install-the-tools.md)
* [配置 Unity 项目](../develop/unity/Configure-Unity-Project.md)
* [Unity 开发概述](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)