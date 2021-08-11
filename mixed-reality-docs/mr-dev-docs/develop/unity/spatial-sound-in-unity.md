---
title: Unity 中的空间音效
description: 通过示例了解如何从 Unity 场景中的特定 3D 点播放和衰减空间声音。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity， 空间音效， HRTF， 房间大小， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， MRTK， 混合现实设备， 空间Toolkit， 混响
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228223"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空间音效

此页链接到 Unity 中空间声音的资源。

## <a name="spatializer-options"></a>空间化程序选项

混合现实应用程序的空间化程序选项包括：
* Unity 提供 *MS HRTF 空间化程序* 作为可选 *Windows Mixed Reality的一* 部分。
  * 在成本较高的"单一源"体系结构的 CPU 上运行。
  * 提供，用于向后兼容原始HoloLens应用程序。
* *Microsoft 空间化程序* 可从 Microsoft 空间化程序 [存储库 GitHub提供](https://github.com/microsoft/spatialaudio-unity)。
  * 使用成本较低的"多源"体系结构。
  * 卸载到硬件加速器上的 HoloLens 2。 

对于新应用程序，我们建议使用 *Microsoft Spatializer*。

## <a name="enable-spatialization"></a>启用空间化

使用 [NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)安装 _Microsoft.SpatialAudio.Spatializer.Unity，_ 并选择项目音频设置中的 **Microsoft Spatializer。** 然后：
* 将 **音频源** 附加到层次结构中的对象
* 选中" **启用空间化"** 复选框
* 将" **空间混合"** 滑块移动到"1"
* 确保在开发人员工作站上启用空间音频。 
    * 右键单击任务栏中的音量图标，确保"空间音效"设置为"关闭"外的其他内容。 
    * 选择 **用于耳机的 Windows Sonic"，** 以获得最佳表示形式，以表达你在HoloLens 2。

>[!NOTE]
>如果在 Unity 中收到由于缺少插件 Microsoft.SpatialAudio.Spatializer.Unity 的一个依赖项而无法加载插件的错误[，请检查电脑上是否](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)安装了最新版本的 Microsoft Visual C++ Redistributable。

有关更多信息，请参阅：
* [Microsoft 空间化GitHub存储库](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft 的空间化程序教程](tutorials/unity-spatial-audio-ch1.md)
* [Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity 的空间化程序文档](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>基于距离的衰减

Unity 的默认基于距离的衰减最小距离为 1 米，最大距离为 500 米，具有对数回退。 这些设置可能适用于你的方案，或者你可能会发现源衰减过快或过慢。 有关更多信息，请参阅：
* [混合现实中的建议设置](../../design/spatial-sound-design.md) 声音设计。
* [有关设置这些曲线的说明](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) ，请参阅 Unity 的音频源文档。

## <a name="reverb"></a>混响

_默认情况下，Microsoft 空间_ 化程序禁用后空间化程序效果。 为空间化源启用混响和其他效果：
* 将房间 **效果发送级别** 组件附加到每个源
* 调整每个源的发送级别曲线，以控制发回图以处理效果的音频的增益

有关详细信息 [，请参阅空间化程序教程的第 5](tutorials/unity-spatial-audio-ch5.md) 章。

## <a name="unity-spatial-sound-examples"></a>Unity 空间声音示例

有关 Unity 中空间声音的示例，请参阅：
* [MRTK 演示](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索混合现实核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [混合现实中的声音设计](../../design/spatial-sound-design.md)
* [Microsoft 的空间化程序教程](tutorials/unity-spatial-audio-ch1.md)
