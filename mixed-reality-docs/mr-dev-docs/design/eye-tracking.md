---
title: 眼动跟踪
description: 了解眼动跟踪HoloLens 2在全息体验中提供时，了解人类理解的新水平。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼动跟踪， 混合现实， 输入， 眼睛凝视， 校准， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包， 意向， 操作
ms.openlocfilehash: a4010e5244539909d2b04cdb9e2044672d1decab
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143246"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 中的眼动跟踪

![MRTK 中的眼动跟踪演示](images/mrtk_et_scenemenu.jpg)

HoloLens 2可让开发人员使用有关用户正在查看的内容的信息，从而在全息体验中实现新级别的上下文和人类理解。 本页介绍开发人员如何从各种用例的眼动跟踪中获益，以及设计基于眼睛凝视的用户交互时要查找的内容。 

眼动跟踪 API 在设计时已考虑用户的隐私，避免传递任何可识别信息，尤其是任何生物识别。 对于支持眼动跟踪的应用程序，用户需要授予应用使用眼动跟踪信息的权限。

### <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
</tr>
<tr>
     <td>眼睛凝视</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>头部和眼动跟踪设计概念演示

若要了解头部和眼动跟踪设计概念的运行情况，请查看下面的设计 [全息影像 -]() 头部跟踪和眼动跟踪视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

## <a name="calibration"></a>校准 

若要准确运行眼动跟踪，每个用户都需要进行眼动跟踪用户校准[](/hololens/hololens-calibration)，用户必须查看一组全息目标。 这样，设备可以调整系统，为用户提供更舒适、更高质量的观看体验，并确保同时进行准确的眼动跟踪。 

眼动跟踪应该适用于大多数用户，但在极少数情况下，用户无法成功校准。 校准可能会由于各种原因失败，包括但不限于： 
* 用户以前选择退出校准过程
* 用户发散了注意力，没有遵循校准目标
* 用户具有某些类型的接触镜和眼镜，系统尚不支持这些 
* 用户具有某些眼睛 physiology、目视状况或状态外科，系统尚不支持该系统  
* 外部因素抑制可靠的眼睛跟踪，如在眼睛正面的眼睛上出现污迹，如污迹面板或眼镜、强烈直接阳光和 occlusions

开发人员应确保向用户提供对其视觉跟踪数据可能不可用 (无法成功) 的用户的充分支持。 我们已在本页底部的部分中提供了有关后备解决方案的建议。 

若要了解有关校准的详细信息以及如何确保流畅的体验，请查看我们的 [眼睛跟踪用户校准](/hololens/hololens-calibration) 页面。

<br>

## <a name="available-eye-tracking-data"></a>可用的目视跟踪数据

在深入了解有关目视输入的特定用例的详细信息之前，我们想要简要指出 HoloLens 2 [目视跟踪 API](/uwp/api/windows.perception.people.eyespose) 提供的功能。 开发人员可在大约 _30 FPS (30) Hz_ 的情况上，通过一种眼睛 (眼睛和方向) 访问。
有关如何访问目视跟踪数据的详细信息，请参阅我们的开发人员指南，了解如何使用 [DirectX 中的眼睛](../develop/native/gaze-in-directx.md) ，并看看 [Unity](https://aka.ms/mrtk-eyes)。

围绕实际目标 (的视觉角度看，眼睛的眼睛约为1.5 度，请参阅下图) 。 由于预期的轻微 imprecisions，开发人员应围绕这一下限值来规划一些利润率 (例如，2.0-3.0 度可能会导致更舒适的体验) 。 下面将详细介绍如何处理小目标的选择。 要准确运行眼动跟踪，每个用户需要完成眼动跟踪用户校准。 

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*以2米距离为目标的最佳目标大小*

<br>

## <a name="use-cases"></a>用例

眼动跟踪可让应用程序实时跟踪用户正在注视的位置。 以下用例描述了在混合现实中，在 HoloLens 2 上使用目视跟踪可能会发生的一些交互。
这些用例不是全息 Shell 体验的一部分 (即，启动 HoloLens 2) 时显示的接口。
你可以在 [混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)中试用其中一些功能，这为使用目视跟踪提供了几个有趣且功能强大的示例，例如，快速轻松地支持目视的目标选择，并根据用户所查看的内容自动滚动查看文本。 

### <a name="user-intent"></a>用户意图

有关用户所在位置和内容的信息 **为其他输入** 提供了强大的上下文，如语音、双手和控制器。
可在各种任务中使用此信息。
例如，这可以通过查看全息图并口述 *"选择"* (，在场景中快速轻松地 **定位**，同时查看 "[注视" 和 "提交](gaze-and-commit.md)") 或 *"put ..."*，然后查找用户要放置全息影像的位置，并显示 *".。。出现 "*。 在[混合现实工具包 - 视线支持的目标选择](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合现实工具包 - 视线支持的目标定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中可以找到相关示例。

此外，用户意向的示例可能包括使用用户查看的信息来增强使用所介绍的虚拟代理和交互式全息影像。 例如，根据当前查看的内容，虚拟代理可能会调整可用选项及其行为。 

### <a name="implicit-actions"></a>隐式操作

隐式操作的类别与用户意图密切相关。
其思路是，全息影像或用户界面元素会以 instinctual 的方式做出反应，甚至可能不会像用户同时与系统交互，而是让系统和用户保持同步。例如， **基于目视的自动滚动** ，用户可以在其中读取长文本，在用户进入文本框底部时自动开始滚动，以使用户处于阅读流中，而不会抬起手指。  
这种情况的一个关键方面是，滚动速度可适应用户的读取速度。
另一个例子就是 **受支持的目视缩放和平移** ，用户可以感觉到他或她所关注的内容完全接近。 触发和控制缩放速度可以通过语音或手写输入来控制，这对于向用户提供控制感受，同时避免被淹没非常重要。 下面将更详细地讨论这些设计注意事项。 放大后，用户可以通过使用眼睛来平稳地关注街道的学习过程，以浏览其邻居。
[混合现实工具包 - 视线支持的导航](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)示例中可以找到此类交互的演示。

_隐式操作_ 的其他用例可能包括：
- **智能通知：** 在你要查找的位置，厌恶的通知会出现问题？ 考虑到用户正在关注的内容，你可以通过从当前 gazing 用户的位置偏移通知来更好地进行此体验。 这会限制干扰，并在用户完成读取后自动将其关闭。 
- **留心全息影像：** 在 gazed 时，会对影像进行细微反应。 这可能包括稍微光亮的 UI 元素，这是一种对虚拟狗的缓慢百花齐放花，开始回顾用户并 wagging 其尾部。 这种交互可能会在应用程序中提供更有趣的连接和满意度。

### <a name="attention-tracking"></a>注意力跟踪

有关用户所在位置或位置的信息可以是非常强大的工具。 它可帮助评估设计的可用性并识别工作流中的问题，使其更高效。
目视跟踪可视化和分析是各种应用程序领域的常见做法。 在 HoloLens 2 中，我们提供了一种新的维度来理解，因为3D 全息图可以放置在真实的上下文中并进行相应的评估。 [混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)提供了用于记录和加载目视跟踪数据的基本示例，以及如何对其进行可视化。
Microsoft 致力于推动创新，同时确保用户对其眼睛跟踪信息的使用方式有了经验和透明性。  我们将与我们的开发人员和 UX 团队合作，为第三方提供指导，以确保在用户的中心获得经验。  

此领域的其他应用场景包括： 
-   **远程目视视觉视觉对象：** 远程目视目视可视化：直观显示远程协作者正在查看的内容，以便能够提供即时反馈并加速更准确的信息处理。
-   **用户研究：** 关注跟踪可以帮助研究人员深入了解用户如何感知和接触自然环境，而不会干扰，以设计更自然的人机交互。 眼动跟踪可以提供参与者未直接表达的信息，否则研究人员可能很容易错过这些信息。 
-   **训练和性能监视：** 通过更有效地识别执行流中的瓶颈来练习和优化任务的执行。 眼动跟踪可以提供自然、实时和目标信息，以帮助改进工作区中的培训、生产力和安全性。 
-   **设计评估、营销和使用者研究：** 眼动跟踪使商业公司能够在实际环境中执行营销和使用者研究，或分析吸引用户注意以改进产品或空间设计的问题。 

### <a name="other-use-cases"></a>其他用例

- **Gaming:** Ever wanted to have superpowers? 机会来了！ 可以通过凝视全息影像来放大全息影像。 从眼睛中发射射线 - 在[RoboRaid 中试用，HoloLens 2。](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
将它们变成块或冻结它们。 使用 X 光透视来扫描建筑物。 没有做不到，只有想不到！
不过，请注意不要使用户占上用场 - 若要了解更多内容，请查看我们基于眼睛凝视的 [输入设计准则](eye-gaze-interaction.md)。

- **表达式头像：** 眼动跟踪通过使用实时眼动跟踪数据对头像眼睛进行动画处理，以指示用户正在查看的内容，帮助获得更具表现力 3D 头像。 

- **文本条目：** 眼动跟踪可以用作低工作量文本输入的替代方法，尤其是在语音或手不方便使用时。 

<br>

## <a name="using-eye-gaze-for-interaction"></a>使用眼睛凝视进行交互

构建利用快速移动眼睛定位的交互可能比较困难。
一方面，眼睛移动得非常快，因此你需要小心如何使用眼睛凝视输入，因为否则用户可能会发现体验令人难以承受或分散注意力。 另一方面，还可以创建真正激发用户体验的体验！ 若要帮助你了解关键优势、挑战和设计建议，了解如何进行 [交互](eye-gaze-interaction.md)。 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>目视跟踪不可用时的回退解决方案

在极少数情况下，目视跟踪数据可能不可用。
这可能是由于下面列出了最常见的原因：
* 系统未能 [校准用户](/hololens/hololens-calibration)。
* 用户跳过了 [校准](/hololens/hololens-calibration)。   
* 用户进行了校准，但决定不向应用程序授予使用其眼睛跟踪数据的权限。    
* 用户具有唯一的眼镜或系统尚不支持的一些目视的情况。 
* 外部因素抑制了一种可靠的眼睛跟踪，如在眼睛前面的头发的情况下，在 HoloLens 面板上出现污迹、眼镜、强烈直接阳光和 occlusions。

开发人员应确保为这些用户提供适当的后备支持。 在 " [DirectX 中的目视跟踪](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) " 页上，我们介绍了检测目视跟踪数据是否可用所需的 api。 

尽管某些用户可能已特意决定撤消、访问其眼睛跟踪数据，并且可以在不提供对其眼睛跟踪数据的访问权限的情况下权衡用户体验令人满意的体验，但在某些情况下，这可能是不可能的。 如果你的应用程序使用目视跟踪，并且这是体验的重要部分，我们建议你清楚地将此信息传递给用户。   

请通知用户，目视跟踪对于您的应用程序而言是至关重要的， (甚至可能列出一些增强的功能) 若要充分利用您的应用程序，可以帮助用户更好地了解他们所放弃的内容。 根据上述检查) ，帮助用户确定目视跟踪可能不工作 (的原因，并提供一些建议来快速解决潜在问题。 

例如，如果检测到系统支持眼动跟踪，则用户已校准，甚至已授予其权限，但尚未收到任何眼动跟踪数据，则这可能指向一些其他问题，例如闪烁或眼睛被遮挡。 

在极少数情况下，眼动跟踪可能无法工作的用户。 因此，请通过允许关闭甚至禁用在应用中启用眼动跟踪的提醒来消除这一点。

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>回退使用眼睛凝视作为主要输入指针的应用

如果应用使用眼睛凝视作为指针输入，以快速选择场景中的全息影像，但眼动跟踪数据不可用，我们建议返回到头部凝视并开始显示头部凝视光标。 建议使用超时值 (例如 500–1500 毫秒) 确定是否切换。 此操作可防止每次系统由于快速眼睛运动或闪烁而短暂丢失跟踪时出现光标。 如果你是 Unity 开发人员，混合现实工具包中已处理了头部凝视的自动回退。 如果你是 DirectX 开发人员，则需要自己处理此开关。

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>回退到其他特定于眼动跟踪的应用程序

应用可能会以专门针对眼睛定制的独特方式使用眼睛凝视。 例如，对头像眼睛进行动画处理，或对基于眼睛的注意热度地图进行动画处理，这依赖于有关视觉注意的精确信息。 在这种情况下，没有明确的回退。 如果眼动跟踪不可用，可能需要禁用这些功能。
同样，建议向可能不知道该功能不工作的用户明确传达此信息。

<br>

本页希望能够提供一个很好的概述，让你开始了解眼动跟踪和眼睛凝视输入HoloLens 2。 若要开始开发，请查看有关眼睛凝视与全息影像交互[](eye-gaze-interaction.md)[、Unity](https://aka.ms/mrtk-eyes)中眼睛凝视和 DirectX 中眼睛[凝视的作用的信息](../develop/native/gaze-in-directx.md)。

## <a name="see-also"></a>另请参阅

* [校准](/hololens/hololens-calibration)
* [舒适](comfort.md)
* [基于眼睛凝视的交互](eye-gaze-interaction.md)
* [DirectX 中的眼睛凝视](../develop/native/gaze-in-directx.md)
* [眼睛 (混合现实工具包) ](https://aka.ms/mrtk-eyes)
* [凝视和提交](gaze-and-commit.md)
* [语音输入](../out-of-scope/voice-design.md)
