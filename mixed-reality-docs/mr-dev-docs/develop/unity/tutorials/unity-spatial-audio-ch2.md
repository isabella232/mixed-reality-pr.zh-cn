---
title: 空间音频教程 - 2. 将按钮交互声音空间化
description: 向项目添加一个按钮，并空间化按钮交互声音。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 与头部相关的传输函数， 混响， Microsoft Spatializer， 预制器， 音量曲线
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712792"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2.将按钮交互声音空间化

## <a name="overview"></a>概述

本教程介绍如何将按钮交互声音空间化，并了解如何使用音频剪辑来测试空间化按钮交互。  

## <a name="objectives"></a>目标

* 添加按钮单击声音并将其空间化

## <a name="add-a-button"></a>添加按钮

若要添加按钮预制件，请在"项目"窗口中选择"包"，在搜索栏中键入"PressableButtonHoloLens2"。

![资产中的按钮预制](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

按钮预制项是由蓝色图标表示的项。 单击 **PressableButtonHoloLens2** 预制项并将其拖动到"层次结构"中。 在 **"PressableButtonHoloLens2"** 对象仍处于选中状态后，在"检查器"窗口中配置 **"转换** "组件，如下所示：

* **位置**：X = 0，Y = -0.4，Z = 2
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![按钮转换](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

若要专注于场景中的对象，可以双击 **PressableButtonHoloLens2** 对象，然后再次稍微放大：

## <a name="spatialize-button-feedback"></a>空间化按钮反馈

在此步骤中，将按钮的音频反馈空间化。 有关相关设计建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。

在" **音频调音器** "窗口中，你将定义名为 **"调音** 器组"的目标，用于从音频源 **组件播放** 音频。

若要打开音频 **调音器** 窗口，请在 Unity 菜单中选择"**窗口**  >  **音频**  >  **音频调** 音器： ![ 打开音频调音器窗口"](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 通过单击 **"调** 音器"旁边的"+"创建一个调音器，然后向"调音器"输入合适的名称，例如空间 _音频调音器_。 新的混合器将包含名为 **Master 的默认****组**。

![具有第一个调音器的调音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> 直到第 [5](unity-spatial-audio-ch5.md)章：使用混响向空间音频添加距离中启用混响之前，调音器音量计不会显示通过 Microsoft Spatializer 播放的声音的活动

在"层次结构"窗口中，选择 **PressableButtonHoloLens2，** 然后在"检查器"窗口中找到"音频源"组件，并按如下所示配置"音频源"组件：

1. 对于" **输出** "属性，单击选择器并选择 **创建的"调** 音器"。
2. 选中" **空间化"** 复选框。
3. 将" **空间混合"** 滑块移动到 1 (3D) 。

![按钮音频源](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> 如果将 **空间混合** 移动到 1 (3D) 而不选中"空间化"复选框，Unity 将使用其平移空间化程序，而不是 **将 Microsoft Spatializer** 与 HRTF 一起使用。

## <a name="adjust-the-volume-curve"></a>调整音量曲线

默认情况下，当空间化声音距离侦听器较远时，Unity 会衰减这些声音。 当此衰减应用于交互反馈声音时，界面可能变得更加难以使用。

若要禁用此衰减，需要在音频源 **组件中调整****音量曲线。**

在"层次结构"窗口中，选择 **"PressableButtonHoloLens2"，** 然后在"检查器"窗口中导航到"音频 **源**  >  **3D 声音** 设置"，并按如下所示进行配置：

1. 将" **卷回滚"属性** 设置为"线性回滚"
2. 将"卷"曲线上的终结点 (红色曲线) 从 y 轴上的"0"拖动到"1"
3. 若要将 **音量曲线的形状** 调整为平面，请将白色曲线形状控件拖动到 X 轴

![按钮 3D 声音设置](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>测试空间化音频

若要在 Unity 编辑器中测试空间化音频，你必须在 **PressableButtonHoloLens2** 对象上选中"循环"选项的"音频源"组件中添加音频剪辑。  

在播放模式下，将 **PressableButtonHoloLens2** 对象从左向右移动，并比较工作站上启用的空间音频和未启用空间音频的对象。 还可通过以下方法更改用于测试的音频源设置：

* 将 **空间混合属性** 移动到 0 到 1 之间 (2D 非空间化以及 3D 空间化声音) 
* 检查和取消选中 **Spatialize** 属性

在应用程序上试用HoloLens 2。 在应用中，可以单击按钮并听到空间化按钮交互声音。

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解将按钮交互声音空间化，并使用音频剪辑来测试空间化按钮交互。 下一教程将介绍如何从视频源对音频进行空间化。

> [!div class="nextstepaction"]
> [下一教程：3.对视频中的音频进行空间化](unity-spatial-audio-ch3.md)
