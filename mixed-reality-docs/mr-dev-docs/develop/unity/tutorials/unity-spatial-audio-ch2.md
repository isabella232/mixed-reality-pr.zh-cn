---
title: 空间音频教程-2。 将按钮交互声音空间化
description: 向项目添加一个按钮，并 spatialize 按钮交互声音。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，prototyping，音量曲线
ms.openlocfilehash: eb550c3127e13926d73428b337abfd7cf9872eb7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678186"
---
# <a name="spatializing-button-interaction-sounds"></a>将按钮交互声音空间化

## <a name="objectives"></a>目标
在 HoloLens 2 教程的 "空间音频" 模块的第二章中，你将：
* 添加按钮
* Spatialize 按钮单击声音

## <a name="add-a-button"></a>添加按钮
在 " **项目** " 窗格中，选择 " **资产** "，并在搜索栏中键入 "PressableButtonHoloLens2"：

![资产中的 prefab 按钮](images/spatial-audio/button-prefab-in-assets.png)

按钮 prefab 是由蓝色图标表示的项，而不是白色图标。 将名为 **PressableButtonHoloLens2** 的 prefab 拖到 " **层次结构** " 窗格中。 在 "新建" 按钮的 " **检查器** " 窗格中，将 " **位置** " 属性设置为 (0，-0.4，2) ，以便在应用程序启动时，它将显示在用户之前。 此按钮的 **转换** 组件如下所示：

![按钮转换](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Spatialize 按钮反馈
在此步骤中，你将 spatialize 按钮的音频反馈。 有关相关设计的建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。 

"**音频混音** 器" 窗格用于定义从 **音频源** 组件播放音频的目标（称为 **混音器组**）。 
* 使用 **> 音频 > 音频混合器** 从菜单栏打开 "**音频混音** 器" 窗格
* 通过单击 **Mixers** 旁边的 "+" 来创建 **混音** 器。 新混音器将包含一个名为 **Master** 的默认 **组**。

**混音** 器窗格现在如下所示：

![带有第一个混音器的混音器面板](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> 在 [第5章](unity-spatial-audio-ch5.md)中启用回响后，混音器的音量指示器不会显示通过 Microsoft Spatializer 播放的声音的活动

单击 "**层次结构**" 窗格中的 **PressableButtonHoloLens2** 。 在 " **检查器** " 窗格中：
1. 查找 **音频源** 组件
2. 对于 " **输出** " 属性，单击选择器并选择混音器
3. 选中 " **Spatialize** " 复选框
4. 将 **空间 Blend** 滑块移动到 3d (1) 。

> [!NOTE]
> 在2019之前的 Unity 版本中，"Spatialize" 复选框位于 **音频源** 的 **检查器** 窗格的底部。

进行这些更改后， **PressableButtonHoloLens2** 的 **音频源** 组件将如下所示：

![按钮音频源](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> 如果将 **空间混合** 移动到 1 (3d) 而不选中 **Spatialize** 复选框，则 Unity 将使用其平移 spatializer，而不是 **Microsoft spatializer** with HRTFs。

## <a name="adjust-the-volume-curve"></a>调整音量曲线
默认情况下，在从侦听器获得更远的距离时，Unity 将衰减 spatialized 声音。 如果此衰减应用于交互反馈声音，则接口可能会变得更难以使用。

若要禁用此衰减，请调整 **音量** 曲线。 在 **PressableButtonHoloLens2** 的 "**检查器**" 窗格的 "**音频源**" 组件中，有一个名为 "**三维声音设置**" 的部分。 在该部分中：
1. 将 **Volume Rolloff** 属性设置为线性
2. 将 **卷** 曲线上的终结点从 y 轴上的 "0")  (红色曲线上，直到 "1"
3. 若要将 **音量** 曲线的形状调整为平面，请拖动 "白色曲线" 形状控件，使其平行于 X 轴

进行这些更改后， **PressableButtonHoloLens2** 的 "**音频源**" 属性的 " **3d 声音设置**" 部分将如下所示：

![按钮三维声音设置](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a>测试 spatialize 音频

可随意测试新的 spatialized 按钮交互声音：

* 在 Unity 编辑器中进入游戏模式，理想情况下，使用场景中的循环音频示例
* 将对象从左到右移动到音频源，并与未启用空间音频的和进行比较。 可以通过以下方式更改用于测试的音频源设置：
    * 将空间 Blend 属性移动到 0-1 (2D 非 spatialized 和 3D spatialized 声音) 
    * 选中和取消选中 Spatialize 属性

## <a name="next-steps"></a>后续步骤

在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。 在应用程序中，可以触摸按钮并听到 spatialized 按钮交互声音。

在 Unity 编辑器中测试时，按空格键并滚动鼠标滚轮以激活手动模拟。 有关详细信息，请参阅 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。

> [!div class="nextstepaction"]
> [第3章](unity-spatial-audio-ch3.md)

