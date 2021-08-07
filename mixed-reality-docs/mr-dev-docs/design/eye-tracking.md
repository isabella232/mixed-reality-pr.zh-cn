---
title: 眼动跟踪
description: 了解眼动跟踪HoloLens 2在全息体验中提供时，了解人类理解的新水平。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼动跟踪， 混合现实， 输入， 眼睛凝视， 校准， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实 Toolkit， 意向， 操作
ms.openlocfilehash: ce8ffcb6b8b59b6b0484ba4b3db256a8df5810ea2719416bea9e3f4366ad6afe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214134"
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

若要了解头部和眼动跟踪设计概念的运行情况，请查看下面的“设计全息影像 - 头部跟踪和眼动跟踪”视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

此视频来自于“设计全息影像”HoloLens 2 应用。在[此处](https://aka.ms/dhapp)下载并享受完整体验。

## <a name="calibration"></a>校准 

若要准确运行眼动跟踪，每个用户都需要进行眼动跟踪用户校准[](/hololens/hololens-calibration)，用户必须查看一组全息目标。 这样，设备可以调整系统，为用户提供更舒适、更高质量的观看体验，并确保同时进行准确的眼动跟踪。 

眼动跟踪应该适用于大多数用户，但在极少数情况下，用户无法成功校准。 校准可能会由于各种原因失败，包括但不限于： 
* 用户之前选择退出校准过程
* 用户发散了注意力，没有遵循校准目标
* 用户具有某些类型的接触镜和眼镜，系统尚不支持这些 
* 用户有一定的眼部眼部、眼部条件或眼部疾病，系统尚不支持这些  
* 外部因素会阻止可靠的眼动跟踪，例如HoloLens视镜或眼镜上的闪烁、严重直接吸收，以及眼前发造成的遮挡

对于无法成功校准眼动跟踪数据的用户，开发人员 (提供足够的支持) 。 我们在此页底部的 部分中提供了回退解决方案的建议。 

若要详细了解校准以及如何确保顺畅的体验，请查看眼 [动跟踪用户校准](/hololens/hololens-calibration) 页。

<br>

## <a name="available-eye-tracking-data"></a>可用的眼动跟踪数据

在详细介绍眼睛凝视输入的特定用例之前，我们想要简要指出眼动跟踪 API HoloLens 2[的功能](/uwp/api/windows.perception.people.eyespose)。 开发人员可以访问 _30 Hz (约 30 F (PS) 30 Hz_ 的单个眼睛凝视射线和) 。
若要详细了解如何访问眼动跟踪数据，请参阅开发人员指南，了解如何在 [DirectX](../develop/native/gaze-in-directx.md) 中使用眼睛凝视，在 Unity 中 [使用眼睛凝视](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)。

预测眼睛凝视大约位于实际目标周围 1.5 度（可视角度 (，请参阅下图) 。 由于预期会稍有不精确，开发人员应围绕此下限值规划一些边距 (例如，2.0-3.0 度可能会导致更舒适) 。 下面将更详细地讨论如何处理小型目标的选择。 要准确运行眼动跟踪，每个用户需要完成眼动跟踪用户校准。 

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 米距离的最佳目标大小*

<br>

## <a name="use-cases"></a>用例

眼动跟踪可让应用程序实时跟踪用户正在注视的位置。 以下用例描述了在混合现实中通过眼动跟踪HoloLens 2交互。
这些用例尚不是 Holographic Shell 体验的一 (，即启动应用程序时看到的HoloLens 2) 。
可以在混合现实[Toolkit](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)中试用其中一些功能，该示例提供了一些有趣的强大示例，用于使用眼动跟踪，例如快速轻松地选择眼部支持的目标，以及根据用户看到的内容自动滚动文本。 

### <a name="user-intent"></a>用户意图

有关用户查看位置和内容的信息为其他输入（如语音、手和控制器）提供了强大的上下文。
可在各种任务中使用此信息。
例如，通过查看全息影像并说"选择" (还可以看到凝视和提交) 或"放置此 *..."，* 然后查看用户想要 [](gaze-and-commit.md)放置全息影像的位置并说 *"...there"*。 在[混合现实工具包 - 视线支持的目标选择](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection)和[混合现实工具包 - 视线支持的目标定位](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-positioning)中可以找到相关示例。

此外，用户意向的示例可能包括使用有关用户所查看内容的信息来增强与虚拟代理和交互式全息影像的交互。 例如，虚拟代理可能会根据当前查看的内容调整可用选项及其行为。 

### <a name="implicit-actions"></a>隐式操作

隐式操作的类别与用户意图密切相关。
其思路是，全息影像或用户界面元素以一种本能的方式做出反应，甚至不会像用户与系统交互一样，而是让系统和用户保持同步。例如， **基于眼睛凝** 视的自动滚动，用户可以读取长文本，一旦用户进入文本框底部，即可自动开始滚动，使用户保持在阅读流中，而无需举手。  
这一点的关键方面是滚动速度适应用户的阅读速度。
另一个示例 **是支持** 眼睛的缩放和平移，用户可以在其中感觉完全深入到自己所关注的地方。 可以通过语音或手动输入来控制触发和控制缩放速度，这一点对于为用户提供控制感，同时避免被过度控制非常重要。 下面将更详细地讨论这些设计注意事项。 放大后，用户可以顺畅地跟随街道路线，使用眼睛凝视来探索自己附近的区域。
[混合现实工具包 - 视线支持的导航](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation)示例中可以找到此类交互的演示。

隐式操作的其他 _用例_ 可能包括：
- **智能通知：** 是否曾经因为通知弹出而感到麻烦？ 考虑到用户正在关注哪些方面，可以通过从用户当前正在其中接收的通知进行偏移来改善此体验。 这会限制干扰，在用户完成阅读后自动消除这些干扰。 
- **全息影像：全息影像** 时做出小反应的全息影像。 这可以从略微闪烁的 UI 元素、一种缓慢闪烁的花色，到开始回过头看用户并缩小其尾部的虚拟狗。 这种交互可能在应用程序中提供有趣的连接感和满意度。

### <a name="attention-tracking"></a>注意力跟踪

有关用户查看位置或内容的信息可能是一个非常强大的工具。 它可以帮助评估设计的可用性，并确定工作流中的问题，使其更高效。
眼动跟踪可视化和分析是各种应用程序领域的常见做法。 借助HoloLens 2，我们为这种理解提供了一个新维度，因为 3D 全息影像可以放置在实际上下文中并相应地进行评估。 混合[现实Toolkit](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)提供了日志记录和加载眼动跟踪数据以及如何将其可视化的基本示例。
Microsoft 致力于促进创新，同时确保用户在眼动跟踪信息的使用方式方面获得明智的透明体验。  我们将与开发人员和 UX 团队合作，为第三方提供指导，以确保体验以用户为中心。  

此领域的其他应用场景包括： 
-   **远程眼睛凝视可视化：** 远程眼睛凝视可视化效果：可视化远程协作者正在查看的内容，以便提供即时反馈，促进更准确的信息处理。
-   **用户研究：** 关注跟踪可以帮助研究人员深入了解用户如何感知和接触自然环境，而不会干扰，以设计更自然的人机交互。 眼动跟踪可以提供参与者未直接表达的信息，否则研究人员可能很容易错过这些信息。 
-   **训练和性能监视：** 通过更有效地识别执行流中的瓶颈来练习和优化任务的执行。 眼动跟踪可以提供自然、实时和目标信息，以帮助改进工作区中的培训、生产力和安全性。 
-   **设计评估、营销和使用者研究：** 眼动跟踪使商业公司能够在实际环境中执行营销和使用者研究，或分析吸引用户注意以改进产品或空间设计的问题。 

### <a name="other-use-cases"></a>其他用例

- **游戏：** 曾经想要拥有一个？ 机会来了！ 可以通过凝视全息影像来放大全息影像。 从眼睛中发射射线 - 在[RoboRaid 中试用，HoloLens 2。](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
将它们变成块或冻结它们。 使用 X 光透视来扫描建筑物。 没有做不到，只有想不到！
不过，请注意不要使用户占上用场 - 若要了解更多内容，请查看我们基于眼睛凝视的 [输入设计准则](eye-gaze-interaction.md)。

- **表达式头像：** 眼动跟踪通过使用实时眼动跟踪数据对头像眼睛进行动画处理，以指示用户正在查看的内容，帮助获得更具表现力 3D 头像。 

- **文本条目：** 眼动跟踪可以用作低工作量文本输入的替代方法，尤其是在语音或手不方便使用时。 

<br>

## <a name="using-eye-gaze-for-interaction"></a>使用眼睛凝视进行交互

构建利用快速移动眼睛定位的交互可能比较困难。
一方面，眼睛移动得非常快，因此你需要小心如何使用眼睛凝视输入，因为否则用户可能会发现体验令人难以承受或分散注意力。 另一方面，你还可以创建真正的神奇体验，将激发你的用户！ 若要帮助你了解关键优势、挑战和设计建议，了解如何进行 [交互](eye-gaze-interaction.md)。 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>目视跟踪不可用时的回退解决方案

在极少数情况下，目视跟踪数据可能不可用。
这可能是由于下面列出了最常见的原因：
* 系统未能 [校准用户](/hololens/hololens-calibration)。
* 用户跳过了 [校准](/hololens/hololens-calibration)。   
* 用户进行了校准，但决定不向应用程序授予使用其眼睛跟踪数据的权限。    
* 用户具有唯一的眼镜或系统尚不支持的一些目视的情况。 
* 外部因素抑制了一种可靠的眼睛跟踪，如 HoloLens 面板上出现污迹，或眼镜、强烈直接阳光和 occlusions 上，因为眼睛正面有头发。

开发人员应确保为这些用户提供适当的后备支持。 在 " [DirectX 中的目视跟踪](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) " 页上，我们介绍了检测目视跟踪数据是否可用所需的 api。 

尽管某些用户可能已特意决定撤消、访问其眼睛跟踪数据，并且可以在不提供对其眼睛跟踪数据的访问权限的情况下权衡用户体验令人满意的体验，但在某些情况下，这可能是不可能的。 如果你的应用程序使用目视跟踪，并且这是体验的重要部分，我们建议你清楚地将此信息传递给用户。   

请通知用户，目视跟踪对于您的应用程序而言是至关重要的， (甚至可能列出一些增强的功能) 若要充分利用您的应用程序，可以帮助用户更好地了解他们所放弃的内容。 根据上述检查) ，帮助用户确定目视跟踪可能不工作 (的原因，并提供一些建议来快速解决潜在问题。 

例如，如果您可以检测到系统支持目视跟踪，则用户会进行校准，甚至会获得其权限，而不会收到任何眼睛跟踪数据，这可能会导致某些其他问题，如污迹或眼睛封闭像素。 

对于目视跟踪可能不起作用的用户来说，这种情况很罕见。 因此，在应用中启用眼睛跟踪时，可以通过允许消除甚至禁用提醒来过于这种情况。

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>使用红眼作为主要输入指针回退应用

如果你的应用程序使用目视看眼作为指针输入来快速选择场景中的全息影像，但眼睛跟踪数据不可用，则建议回退到打印头并开始显示眼睛良好的光标。 建议使用超时 (例如，500– 1500 ms) 来确定是否要切换。 此操作可防止在系统每次由于快速的目视运动、传情动漫或传情动漫而发生短暂跟踪丢失时，游标都出现。 如果你是一名 Unity 开发人员，则已在混合现实 Toolkit 中处理自动回退到打印头。 如果你是 DirectX 开发人员，则需要自行处理此开关。

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>回退其他特定于跟踪的应用程序

您的应用程序可能会以独特的方式使用视觉眼睛。 例如，对头像的眼睛进行动画处理，或者为了热图，依赖于有关视觉对象的准确信息。 在这种情况下，没有任何明确的回退。 如果目视跟踪不可用，可能需要禁用这些功能。
同样，我们建议你清楚地将其传达给可能未意识到该功能无法正常工作的用户。

<br>

在此页面中，你可以了解如何了解 HoloLens 2 的眼睛跟踪和眼睛眼睛输入的角色。 若要开始开发，请查看我们的信息，了解如何 [与全息影像交互](eye-gaze-interaction.md)、 [在 Unity 中目视](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) 看，以及如何 [在 DirectX 中观看眼](../develop/native/gaze-in-directx.md)。

## <a name="see-also"></a>另请参阅

* [校准](/hololens/hololens-calibration)
* [舒适](comfort.md)
* [基于眼睛凝视的交互](eye-gaze-interaction.md)
* [目视观察 DirectX](../develop/native/gaze-in-directx.md)
* [眼睛 (混合现实 Toolkit) ](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [凝视和提交](gaze-and-commit.md)
* [语音输入](../out-of-scope/voice-design.md)