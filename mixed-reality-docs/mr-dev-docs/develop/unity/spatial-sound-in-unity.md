---
title: Unity 中的空间音效
description: 从 Unity 场景内的特定3D 点播放空间声音。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包，spatializer，回音
ms.openlocfilehash: db01fe81457d0f46b7f287458b4d48af4a98f2bc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678436"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空间音效

此页链接到 Unity 中的空间音效资源。

## <a name="spatializer-options"></a>Spatializer 选项
混合现实应用程序的 Spatializer 选项包括：
* *MS HRTF Spatializer*。 Unity 将其作为 *Windows Mixed Reality* 可选包的一部分提供。
  * 这会在具有较高成本的 "单一源" 体系结构的 CPU 上运行。
  * 这是为了向后兼容原 HoloLens 应用程序而提供的。
* *Microsoft Spatializer*。 可从 [Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)获取此功能。
  * 这将使用较低成本的 "多源" 体系结构。
  * 在 HoloLens 2 上，这会被下放到硬件加速器。

对于新应用程序，我们建议 *Microsoft Spatializer*。

## <a name="enable-spatialization"></a>启用 spatialization

使用 [NuGet For unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 安装 _SpatialAudio_ ，并在项目的音频设置中选择 **microsoft Spatializer** 。 然后：
* 将 **音频源** 附加到层次结构中的对象
* 选中 " **启用 spatialization** " 复选框
* 将 **空间混合** 滑块移动到 "1"
* 确保已在开发人员工作站上启用空间音频。 右键单击任务栏上的 "音量" 图标，并确保 "空间" "声音" 设置为 "关闭"，以启用它。 若要获取有关在 HoloLens 2 上收到的内容的最佳表示，请选择 " **Windows Sonic" 作为耳机**。

>[!NOTE]
>如果在 Unity 中由于缺少某个依赖项而无法加载 SpatialAudio，请检查你的计算机上是否安装了最新版本的 [Microsoft Visual C++ 可再发行组件](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 。

有关详细信息，请参阅：
* [Microsoft spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft 的 spatializer 教程](tutorials/unity-spatial-audio-ch1.md)
* [Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity 的 spatializer 文档](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>基于距离的衰减
Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。 这些设置可能适用于你的方案，你可能会发现源衰减太快或太慢。 有关详细信息，请参阅：
* [混合现实中的声音设计](../../design/spatial-sound-design.md) 建议的设置。
* [Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) ，了解有关如何设置这些曲线的说明。

## <a name="reverb"></a>混响
默认情况下， _Microsoft Spatializer_ 禁用了 Spatializer 效果。 若要为 spatialized 源启用回响和其他效果：
* 将 " **房间效果发送级别** " 组件附加到每个源
* 调整每个源的发送级别曲线，以控制发送回图形以进行效果处理的音频的增益

有关详细信息，请参阅 [spatializer 教程的第5章](tutorials/unity-spatial-audio-ch5.md) 。

## <a name="unity-spatial-sound-examples"></a>Unity 空间声音示例
有关 Unity 中空间音效的示例，请参阅：
* [MRTK 演示](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。 从这里，你可以进入下一个构建基块：

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>请参阅
* [混合现实中的声音设计](../../design/spatial-sound-design.md)
* [Microsoft 的 spatializer 教程](tutorials/unity-spatial-audio-ch1.md)
