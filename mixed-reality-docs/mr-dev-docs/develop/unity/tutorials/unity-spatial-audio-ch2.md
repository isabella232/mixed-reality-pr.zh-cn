---
title: 空间音频教程-2。 将按钮交互声音空间化
description: 向项目添加一个按钮，并 spatialize 按钮交互声音。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，prototyping，音量曲线
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578472"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2.将按钮交互声音空间化

## <a name="overview"></a>概述

在本教程中，你将学习如何 spatialize 按钮交互声音，还可以了解如何使用音频剪辑测试 spatialized 按钮交互。  

## <a name="objectives"></a>目标

* 添加并 Spatialize 按钮单击声音

## <a name="add-a-button"></a>添加按钮

若要添加按钮 prefab，请在 " **项目** " 窗口中选择 " **资产** "，并在搜索栏中键入 "PressableButtonHoloLens2"。

![资产中的 prefab 按钮](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

按钮 prefab 是由蓝色图标表示的条目。 单击并将 **PressableButtonHoloLens2** prefab 拖到层次结构中。 在 **PressableButtonHoloLens2** 对象仍处于选中状态的情况下，在 "检查器" 窗口中，按如下所示配置 **转换** 组件：

* **Position**： X = 0，Y =-0.4，Z = 2
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![按钮转换](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

若要重点关注场景中的对象，可以双击 **PressableButtonHoloLens2** 对象，然后再次缩小：

## <a name="spatialize-button-feedback"></a>Spatialize 按钮反馈

在此步骤中，你将 spatialize 按钮的音频反馈。 有关相关设计的建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。

在 " **音频混音** 器" 窗口中，你将定义名为 " **混音器组**" 的目标，以便从 **音频源** 组件播放音频。

若要打开 "**音频混音** 器" 窗口，请在 Unity 菜单中选择 "**窗口**  >  **音频**  >  **混音** 器： ![ 打开音频混音器" 窗口](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 单击 " **Mixers** " 旁边的 "+" 并向混音器输入合适的名称（例如，_空间音频混合器_），创建 **混音** 器。 新混音器将包含一个名为 **Master** 的默认 **组**。

![带有第一个混音器的混音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> 在5章节中启用回响后 [：使用回音向空间音频添加距离](unity-spatial-audio-ch5.md)，混音器的音量指示器不显示通过 Microsoft Spatializer 播放的声音的活动

在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2** "，然后在 "检查器" 窗口中找到 " **音频源** " 组件，并按如下所示配置音频源组件：

1. 对于 " **输出** " 属性，单击选择器并选择已创建的 **混音** 器。
2. 选中 " **Spatialize** " 复选框。
3. 将 **空间 Blend** 滑块移动到 3d (1) 。

![按钮音频源](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> 如果将 **空间混合** 移动到 1 (3d) 而不选中 **Spatialize** 复选框，则 Unity 将使用其平移 spatializer，而不是 **Microsoft spatializer** with HRTFs。

## <a name="adjust-the-volume-curve"></a>调整音量曲线

默认情况下，在从侦听器获得更远的距离时，Unity 将衰减 spatialized 声音。 如果此衰减应用于交互反馈声音，则接口可能会变得更难以使用。

若要禁用此衰减，需调整 **音频源** 组件中的 **音量** 曲线。

在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2** "，然后在 "检查器" 窗口中，导航到 "**音频源**  >  **3d 声音设置**"，并按如下

1. 将 **Volume Rolloff** 属性设置为线性 Rolloff
2. 将 **卷** 曲线上的终结点从 y 轴上的 "0")  (红色曲线上，直到 "1"
3. 若要将 **音量** 曲线的形状调整为平面，请拖动 "白色曲线" 形状控件，使其平行于 X 轴

![按钮三维声音设置](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>测试 spatialize 音频

若要在 unity 编辑器中测试 spatialize 音频，必须在 **PressableButtonHoloLens2** 对象上 **的 "已签入"** "**循环**" 选项中添加音频剪辑。

在播放模式下，将 **PressableButtonHoloLens2** 对象从左到右移动，并在工作站上比较和不启用空间音频。 还可以通过以下方式更改用于测试的音频源设置：

* 将 **空间 Blend** 属性移动到 0-1 (2d 非 Spatialized 和 3d spatialized 声音) 
* 选中和取消选中 **Spatialize** 属性

试用 HoloLens 2 上的应用。 在应用程序中，可以单击按钮并听到 spatialized 按钮交互声音。

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解到 spatialize 按钮交互声音，并使用音频剪辑测试 spatialized 按钮交互。 在下一教程中，你将学习如何从视频源 spatialize 音频。

> [!div class="nextstepaction"]
> [下一教程： Spatializing 音频视频](unity-spatial-audio-ch3.md)
