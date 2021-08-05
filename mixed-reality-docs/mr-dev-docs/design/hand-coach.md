---
title: 手部指导
description: 了解当系统检测不到用户手来帮助他们时，如何使用手部指导触发 3D 手部。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、设计、手部指导、沉浸式头戴显示设备、MRTK、手部、帮助手、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: baf1dab7d73f4e5fca9078717b43dab7b71632f4aa7c36dcac280c029b05d58b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208484"
---
# <a name="hand-coach"></a>手部指导

![示例：手部教练](images/HandCoach/MRTK_handCoach.jpg)<br>

当系统检测不到用户的手时，手部教练会触发三维建模手部。 此功能是一个"教学"组件，可帮助在未教授手势时指导用户。 如果用户有一段时间未执行指定的手势，手会以延迟循环。 手部指导可用于表示按下按钮或选取全息影像。  

## <a name="hand-coach-provided"></a>提供手部指导

当前交互模型表示各种手势控件，例如滚动、远点选择和近点击。 下面是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>中提供的现有手势的完整列表：

:::row:::
    :::column:::
       ![Near Select 的示例](images/HandCoach/NearSelect.gif)<br>
       **"近选 - 已用"示例显示如何选择按钮或关闭可交互对象**<br>
    :::column-end:::
    :::column:::
       ![Air Tap 示例](images/HandCoach/AirTap.gif)<br>
        **Air Tap 示例 - 用于显示如何选择远离的对象**<br>
    :::column-end:::
    :::column:::
       ![移动示例](images/HandCoach/Move.gif)<br>
       **在空间中移动对象的示例-用于显示如何在空间中移动全息影像**<br>
    :::column-end:::
    :::column:::
       ![旋转示例](images/HandCoach/Rotate.gif)<br>
       **显示Rotate-Used全息影像或对象的示例**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![缩放示例](images/HandCoach/Scale.gif)<br>
       **缩放示例 - 用于显示如何操作放大或缩小全息影像**<br>
    :::column-end:::
    :::column:::
       ![Palm Up 示例](images/HandCoach/PalmUp.gif)<br>
        **Hand up 示例 - 建议用于显示手部菜单**<br>
    :::column-end:::
    :::column:::
       ![HandFlip 示例](images/HandCoach/HandFlip.gif)<br>
       **手部翻转图 – 显示手部菜单的另一种方法**<br>
    :::column-end:::
    :::column:::
       ![Scroll 示例](images/HandCoach/Scoll.gif)<br>
       **滚动示例 - 用于滚动列表或长文档**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>设计概念

对于 Hololens2，我们基于感觉和自然手势设计出手部交互。 我们认为这些对大多数用户都是直观的，因此我们没有创建专用的手势学习时刻。 相反，我们创建了手部指导，以帮助用户了解这些手势（如果用户停滞或不熟悉全息影像交互）。 如果没有学习时间，我们认为向用户展示如何通过演示操作来执行此操作是最佳选择。 我们发现用户能够找出手势，但需要一些指导。 如果检测到用户在一段时间内未与对象交互，则手部指导将触发演示正确的手部和手指放置。 

### <a name="intuitive"></a>直观

对手进行动画效果时，它应该是明显的，不应引起任何混淆。 手部动画是尝试提示用户理解的手势的表示形式。 

例如，如果希望用户按下按钮，将触发按下按钮的手动操作。

![示例：手部教练近点击](images/HandCoach/NearSelect_unity.gif)<br>
*手部指导演示接近点击 Gem*  

### <a name="hand-scale"></a>手动缩放

我们使用 UI 菜单测试了各种手部大小，并认为如果手的大小正确，则它会提供一种感觉。 如果它们太小，很难看到和理解手势。 

**语音和手部**

不要期望用户可以通过语音呼叫来侦听一组说明，通过手部指导观看不同的说明。 对说明进行排序，以帮助用户专注于减少传感器过载，而不是吸引他们的注意。


## <a name="can-i-create-my-own"></a>我可以创建自己的吗？

是！ 我们鼓励你为游戏创建自己的独特手势，并返回社区！
我们提供了一个可用于应用的"伪造手"Maya 文件，可在此处下载：下载HandCoach_MRTK.zip <a href="files/HandCoach_MRTK.zip"></a>

![Maya 中动画手的示例](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya 中对框进行动画处理的示例*


**推荐的创作工具**

在 3D 艺术家中，许多选择使用 Autodesk 的[Maya，](https://www.youtube.com/watch?v=q0K3n0Gf8mA)这可以使用 HoloLens来转换资产的创建方式。 提供的手部文件是 Maya 二进制文件，因此建议使用 Maya 对手进行动画处理和导出。 如果希望使用另一个 3D 程序，下面是一个<b>。FBX：</b><a href="files/HandCoachMRTK_FBX.zip">下载HandCoachMRTK_FBX.zip</a>以创建自己的控制器设置。 

如果使用提供的可下载 maya 手动文件，建议将 Unity 中的手缩小到 0.6。

![示例：Maya 中的手部教练平台](images/HandCoach/MayaExample.png)<br>
*被操纵的手*

### <a name="technical-specs"></a>技术规范

*   两手文件以 Maya Ascii 格式提供
*    右侧和左侧以 Maya 二进制格式提供
*   将 Maya 文件设置为 24 FPS
*   在 文件中，有一个左右手，可用于两个手势或单手手势。 默认情况下，只有右侧可见。
*   建议在渐变的开头和结尾保留大约 10 帧的缓冲区
*   如果对具有指定目标的对象进行动画处理，最佳做法是动画处理为"默认"框或 Null。
*   如果手对物理对象（如框）进行动画处理，最佳做法是在 Maya 中不对翻译进行动画处理，而是等待在 Unity 或 Code 中对其进行动画处理。
*   可见动画应为 1.5 秒，才能传达任何有意义的信息
*   对动画感到满意时：
    *   选择所有连接和烘焙关键帧
    *   删除控制器，选择连接和网格，并导出为 FBX
    *  如果有多个动画，可以使用 Maya 的内置游戏导出器： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>从 Maya 导出

对动画感到满意后
* 选择所有连接：选择>层次结构

     ![示例：菜单中的层次结构](images/HandCoach/Hierarchy.png)<br>
* 烘焙动画：切换到"动画">">制作动画"

     ![示例：烘培动画菜单位置](images/HandCoach/BakeAnimation.png)<br>
* 删除控制器控制程序：大纲> MainR_Grp或MainL_Grp

     ![示例：控制器设备菜单位置](images/HandCoach/ControllerRig.png)<br>

* 导出为 FBX：选择"JNT + 网格：文件>导出选定内容 (选项框) >导出选择"

     ![示例：导出选择菜单位置](images/HandCoach/OptionBox.png)<br>

     ![示例：菜单位置](images/HandCoach/SelectionExport.png)<br>

     ![示例：导出选项菜单位置](images/HandCoach/FBXSelection.png)<br>


 导出为 FBX 并导入 Unity 时，将手缩小到 0.6。 我们发现，这非常适合用于显示手部。 

![示例：Unity 设置](images/HandCoach/HandHintScale.png)<br>
*在 MRTK 设置中HandCoach_R预制的 Unity HandCoach_R*


## <a name="implementing-hands-into-your-unity-project"></a>将手部实现到 Unity 项目中

### <a name="best-practices"></a>最佳实践

* 建议将 Unity 中的手缩小到 0.6
* 手应播放两次，如果未完成，则持续循环，直到手势完成。 手应循环两次，以确保用户有时间来注册并查看手势。 手应在循环之间淡入和淡出。 
 *  如果用户的手在 HL2 相机中可见，但用户没有执行所需的交互，则手将在 10 秒后出现。
*   如果用户的手在 HL2 相机中不可见，则手将在 5 秒后显示。  
*   如果动画中间的 HL2 相机可明显跟踪用户的手部，则动画将完成并淡出。
*   如果要包括语音呼叫，建议它对应于手部手势。
*   如果你至少已经教授了一次，则只会在其检测到用户停滞时重复手势。
*   如果特定的 finger 位置是关键的，请确保用户可以清楚地查看动画中的这些差异。 尝试右倾，以清楚地显示最重要的部分。 
* 如果你注意到了手上的扭曲，则需要中转到 Unity 的质量设置以增加骨骼数量。 
 中转到 Unity 的编辑 > Project 设置 > 质量 > 其他 > 混合权重。 请确保选择 "4 骨骼" 以查看平滑联接。

   ![示例： Project 设置 "窗口](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>要避免的内容

* 将指针放大太大
* 将指针放在靠近用户的附近
* 只需教授一次。 优于教授会导致混淆和麻烦
* 将它引入 Unity，在此处下载最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity
  * 材料： Teaching_Hand2
  * 脚本：请参阅<a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach">MRTK 手型指导</a>的 MRTK 准则
  * 每项目设置
    * 场景设置为 UWP：说明可在[配置 Unity Project](../develop/unity/Configure-Unity-Project.md)上找到 Windows Mixed Reality

## <a name="see-also"></a>另请参阅

* [交互-基础](interaction-fundamentals.md)
* [资产创建过程](asset-creation-process.md)
* [笔势](./interaction-fundamentals.md)
* [安装工具](../develop/install-the-tools.md)
* [配置 Unity Project](../develop/unity/Configure-Unity-Project.md)
* [Unity 开发概述](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)