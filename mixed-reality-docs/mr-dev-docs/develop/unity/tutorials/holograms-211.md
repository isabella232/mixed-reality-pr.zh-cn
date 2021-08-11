---
title: HoloLens（第一代）输入 211 - 手势
description: 按照此编码演练使用 Unity、Visual Studio和HoloLens来了解手势概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit， mixedrealitytoolkit， mixedrealitytoolkit-unity， academy， 教程， 笔势， HoloLens， 混合现实学院， unity， 混合现实头戴显示设备， windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206415"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (第一代) 输入 211：手势

>[!IMPORTANT]
>混合现实学院教程的设计HoloLens (第一代) Unity 2017 和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不会使用_** 最新工具集或交互进行更新HoloLens 2并且可能与较新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

[手势将](../../../design/gaze-and-commit.md#composite-gestures) 用户意图转变为操作。 用户可以使用手势来与全息影像交互。 本课程将学习如何跟踪用户的手部、响应用户输入，以及根据手部状态和位置向用户提供反馈。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在 [MR 基础知识 101](../../../develop/unity/tutorials/holograms-101.md)中，我们使用了简单的敲击手势来与全息影像交互。 现在，我们将超出敲击手势，并探索新概念，以：

* 检测何时跟踪用户手，并为用户提供反馈。
* 使用导航手势旋转全息影像。
* 当用户的手即将离开视图时提供反馈。
* 使用操作事件允许用户用双手移动全息影像。

在本课程中，我们将重新访问在 MR输入[210](holograms-210.md)中构建的 Unity 项目模型资源管理器。 宇航员朋友回来帮助我们探索这些新手势概念。

>[!IMPORTANT]
>以下每个章节中嵌入的视频都是使用旧版 Unity 和混合现实 Toolkit。 尽管分步说明准确且最新，但你可能会在相应视频中看到过期的脚本和视觉对象。 由于涵盖的概念仍然适用，因此这些视频仍包含在后像中。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入 211：手势</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 配置Windows 10正确工具的[一台电脑](../../../develop/install-the-tools.md)。
* 一些基本的 C# 编程功能。
* 你应已完成[MR 基础知识 101。](../../../develop/unity/tutorials/holograms-101.md)
* 应已完成 MR 输入[210。](holograms-210.md)
* 配置为HoloLens[的设备](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载 [项目](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 所需的文件。 需要 Unity 2017.2 或更高版本。
* 将文件取消存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码，可在[GitHub。](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)

### <a name="errata-and-notes"></a>Errata 和 Notes

* 需要在 Visual Studio 工具->Options->Debugging下禁用"启用 仅我的代码" (未选中的) ，才能在代码中命中断点。

## <a name="chapter-0---unity-setup"></a>第 0 章 - Unity 设置

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择“打开”。
3. 导航到之前未存档的 **"** 笔势"文件夹。
4. 找到并选择"起始 / **模型资源管理器"** 文件夹。
5. 单击" **选择文件夹"** 按钮。
6. 在Project **面板** 中，展开 **"场景"** 文件夹。
7. 双击" **模型""模型""模型场景** "，以在 Unity 中加载它。

### <a name="building"></a>生成

1. 在 Unity 中，选择"**文件>生成设置"。**
2. 如果 **"生成** 中的场景"中未列出"场景/模型""模型""模型"，请单击"**添加打开** 的场景"以添加场景。
3. 如果专门针对设备进行开发HoloLens，将"目标 **设备"****设置为HoloLens"**。 否则，请保留在任何 **设备上**。
4. 确保 **"生成类型**"设置为 **"D3D"，** 并且 **SDK** 设置为"最新安装 (SDK 16299 或更高版本) 。
5. 单击“生成”。
6. 创建名为 **"App"** 的新文件夹。
7. 单击"应用 **"** 文件夹。
8. 按 **"选择文件夹**"，Unity 将开始为项目生成Visual Studio。

Unity 完成后，将显示文件资源管理器窗口。

1. 打开 **"应用"** 文件夹。
2. 打开 **ModelExplorer Visual Studio解决方案**。

如果部署到 HoloLens：

1. 使用中的顶部工具栏Visual Studio，将目标从"调试"更改为"**发布**"，从 ARM 更改为 **x86**。
2. 单击"本地计算机"按钮旁边的下拉箭头，然后选择"**远程计算机"。**
3. 输入 **HoloLens IP 地址，将**"身份验证模式"设置为"通用 (**未加密协议) "**。 单击“选择”。 如果不知道设备 IP 地址，请查找"网络设置 > **Internet &">选项"。**
4. 在顶部菜单栏中，单击"调试 **"->"开始执行而不调试"，或** 按 **Ctrl + F5**。 如果这是首次部署到设备，则需要将其与[Visual Studio。](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)
5. 部署应用后，使用选择手势 关闭 **Fitbox。** 

如果部署到沉浸式头戴显示设备：

1. 使用中的顶部工具栏Visual Studio，将目标从"调试"更改为"发布 **"，从** ARM 更改为 **x64**。
2. 确保部署目标设置为"本地 **计算机"。**
3. 在顶部菜单栏中，单击"调试 **"->"开始执行而不调试"，或** 按 **Ctrl + F5**。
4. 部署应用后，通过拉取运动控制器上的触发器来关闭 **Fitbox。**

>[!NOTE]
>你可能会注意到"错误"面板Visual Studio红色错误。 可以放心地忽略它们。 切换到"输出"面板以查看实际生成进度。 "输出"面板中的错误将要求你修复 (这些错误通常是由脚本错误导致的) 。

## <a name="chapter-1---hand-detected-feedback"></a>第 1 章 - 手动检测到的反馈

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目标

* 订阅手部跟踪事件。
* 使用光标反馈在跟踪手时向用户显示。

>[!NOTE]
>在HoloLens 2，只要手可见，手就会 (，而不只是当手指指向) 。

### <a name="instructions"></a>说明

* 在" **层次结构"面板** 中，展开 **InputManager** 对象。
* 查找并选择 **"GesturesInput"** 对象。

**InteractionInputSource.cs 脚本** 执行以下步骤：

1. 订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 设置 HandDetected 状态。
3. 取消订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。

接下来，我们将光标从 MR 输入 [210](holograms-210.md) 升级到显示反馈的游标，具体取决于用户的操作。

1. 在" **层次结构"面板** 中，选择 **"游标"** 对象并将其删除。
2. 在Project **面板** 中，搜索 **CursorWithFeedback** 并将其拖到"**层次结构"面板** 中。
3. 在"层次结构"面板中单击 **"InputManager"，** 然后将 **CursorWithFeedback** 对象从"层次结构"拖动到检查器底部的 InputManager **的 SimpleSinglePointerSelector** 的"**游标**"**字段中**。 
4. 单击层次结构 **中的 CursorWithFeedback。** 
5. 在" **检查器"** 面板中，展开" **对象游标"脚本** 上的 **"游标状态数据** "。

游标 **状态数据** 的工作方式如下所示：

* " **任何** 观察"状态表示未检测到手部，并且用户只是四处查看。
* " **任何** 交互"状态表示检测到手部或控制器。
* 任何 **悬** 停状态都表示用户正在查看全息影像。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中，使用 **>生成设置** 重新生成应用程序。
* 打开 **"应用"** 文件夹。
* 如果尚未打开，请打开 **ModelExplorer Visual Studio解决方案**。
  *  (如果在设置期间已在 Visual Studio 中生成/部署此项目，则你可以打开该 VS 实例，然后在系统提示时单击"全部重载) 。
* 在Visual Studio中，单击"调试 **"->"启动而不调试"，** 或按 **Ctrl + F5**。
* 应用程序部署到设备后HoloLens，使用敲击手势关闭 fitbox。
* 将手移入视图，将手指指向天上，开始手部跟踪。
* 向左、向右、向上和向下移动手部。
* 观察在检测到手部后从视图中丢失时光标的变化情况。
* 如果位于沉浸式头戴显示设备上，必须连接并断开控制器。 这种反馈在沉浸式设备上变得不太有趣，因为连接的控制器将始终"可用"。

## <a name="chapter-2---navigation"></a>第 2 章 - 导航

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目标

* 使用导航手势事件来旋转宇航员。

### <a name="instructions"></a>说明

若要在应用中使用导航手势，我们将编辑 **GestureAction.cs，** 以在导航手势发生时旋转对象。 此外，我们将向光标添加反馈，以在"导航"可用时显示。

1. 在"**层次结构"面板中**，展开 **"CursorWithFeedback"。**
2. 在 **全息影像** 文件夹中，找到 **ScrollFeedback** 资产。
3. 将 **ScrollFeedback** 预制项拖放到层次结构 中的 **CursorWithFeedback** GameObject **上**。
4. 单击 **"CursorWithFeedback"。**
5. 在" **检查器"** 面板中，单击" **添加组件"** 按钮。
6. 在菜单中，键入搜索框 **CursorFeedback**。 选择搜索结果。
7. 将 **ScrollFeedback** 对象从"层次结构"拖放到检查器 的"游标反馈"组件的"**滚动** 检测到的游戏对象 **"属性上**。
8. 在" **层次结构"面板** 中，选择 **"AstroMan"** 对象。
9. 在" **检查器"** 面板中，单击" **添加组件"** 按钮。
10. 在菜单中，键入搜索框"笔势 **操作"。** 选择搜索结果。

接下来，在 Visual Studio 中打开 **GestureAction.cs。** 在编码练习 2.c 中，编辑脚本以执行以下操作：

1. **每当执行导航手势** 时，都旋转 AstroMan 对象。
2. 计算 **rotationFactor** 以控制应用于对象的旋转量。
3. **当用户向左** 或向右移动手时，围绕 y 轴旋转对象。

在脚本中完成编码练习 2.c，或将代码替换为以下已完成的解决方案：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

你会注意到，其他导航事件已填充了一些信息。 我们将 GameObject 推送到Toolkit的 InputSystem 模式堆栈上，这样用户就不必在旋转开始后将焦点放在宇航员上。 相应地，完成手势后，我们会从堆栈中弹出 GameObject。

### <a name="build-and-deploy"></a>生成和部署

1. 在 Unity 中重新生成应用程序，然后从 Visual Studio 生成和部署，以在 HoloLens。
2. 凝视宇航员，光标两侧应会出现两个箭头。 此新视觉对象指示宇航员可以旋转。
3. 将手放在手部 (指指向天空的位置) 以便手HoloLens开始跟踪手。
4. 若要旋转宇航员，将手指下至收缩位置，然后向左或向右移动手以触发 NavigationX 手势。

## <a name="chapter-3---hand-guidance"></a>第 3 章 - 手部指南

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目标

* 使用 **手部指导** 分数来帮助预测手部跟踪丢失的时间。
* 提供有关 **光标的反馈** ，以在用户手靠近照相机的视图边缘时显示。

### <a name="instructions"></a>说明

1. 在" **层次结构"面板** 中，选择 **CursorWithFeedback** 对象。
2. 在" **检查器"** 面板中，单击" **添加组件"** 按钮。
3. 在菜单中，键入搜索框"手动 **指导"。** 选择搜索结果。
4. 在Project **面板****全息影像，** 找到 **HandGuidanceFeedback** 资产。
5. 将 **HandGuidanceFeedback** 资产拖放到"检查器"面板中的" **手** 部指导指示器 **"** 属性上。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中重新生成应用程序，然后从 Visual Studio 生成和部署，以体验 HoloLens。
* 将手放在视图中，并举手以跟踪。
* 使用导航手势开始旋转宇航员， (手指和拇指合在一起) 。
* 将手向左、向右、向上和向下移动。
* 当手靠近手势框架的边缘时，光标旁边应会出现一个箭头，警告你手部跟踪将丢失。 箭头指示手部移动的方向，以防止跟踪丢失。

## <a name="chapter-4---manipulation"></a>第 4 章 - 操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目标

* 使用操作事件，用手移动宇航员。
* 提供有关游标的反馈，让用户知道何时可以使用操作。

### <a name="instructions"></a>说明

GestureManager.cs 和 AstronautManager.cs 将使我们能够执行以下操作：

1. 使用语音关键字"**移动宇航员**"启用 **操作** 手势，并使用"**旋转宇航员**"来禁用它们。
2. 切换到响应操作 **手势识别器**。

让我们开始吧。

1. 在" **层次结构"面板** 中，创建新的空 GameObject。 将名称命名为 **"AstronautManager"。**
2. 在" **检查器"** 面板中，单击" **添加组件"** 按钮。
3. 在菜单中，键入搜索框"宇航员 **管理器"。** 选择搜索结果。
4. 在" **检查器"** 面板中，单击" **添加组件"** 按钮。
5. 在菜单中，键入搜索框"语音 **输入源"。** 选择搜索结果。

现在，我们将添加控制宇航员交互状态所需的语音命令。

1. 展开 **检查器 中的** "关键字 **"部分**。
2. 单击 **+** 右侧 以添加新关键字。
3. 键入 关键字作为"**移动宇航员"。** 如果需要，可随意添加键快捷方式。
4. 单击 **+** 右侧 以添加新关键字。
5. 键入 关键字作为"**旋转宇航员"。** 如果需要，可随意添加键快捷方式。
6. 可以在 **ISpeechHandler.OnSpeechKeywordRecognized** 处理程序中的 **GestureAction.cs** 中找到相应的处理程序代码。

![如何为第 4 章设置语音输入源](images/holograms211-speech.png)

接下来，我们将设置游标上的操作反馈。

1. 在Project **面板****全息影像，** 找到 **PathingFeedback** 资产。
2. 将 **PathingFeedback** 预制项拖放到层次结构 中的 **CursorWithFeedback** **对象上**。
3. 在"**层次结构&quot;面板** 中，单击 **&quot;CursorWithFeedback&quot;。**
4. 将 **PathingFeedback** 对象从 **层次结构** 中拖放到 **检查器** 的 &quot;**游标反馈**&quot; 组件中的 &quot;**检测到路径&quot; 游戏对象** 属性上。

现在，我们需要将代码添加到 **GestureAction** ，以启用以下内容：

1. 将代码添加到 **IManipulationHandler. OnManipulationUpdated** 函数，该函数将在检测到 **操作** 笔势时移动 astronaut。
2. 计算 **移动向量** ，以根据手头位置确定应将 astronaut 移动到的位置。
3. **将 Astronaut 移动** 到新位置。

完成编码练习 4. 在 **GestureAction** 中，或使用下面的已完成解决方案：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip(&quot;Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中重建，然后从 Visual Studio 生成并部署，以便在 HoloLens 中运行应用。
* 在 HoloLens 的前方移动手，并抬起食指，使其能够被跟踪。
* 将光标放在 astronaut 上。
* 说 "Move Astronaut" 将 Astronaut 与操作手势一起移动。
* 光标两侧应出现四个箭头，指示程序将立即响应操作事件。
* 将索引向下减小到拇指，并使其 pinched 在一起。
* 四处移动手时，astronaut 会 () 操作。
* 抬起索引手指，停止操作 astronaut。
* 注意：如果在移动手前未说 "移动 Astronaut"，则将改用导航手势。
* 说 "旋转 Astronaut" 返回到 rotatable 状态。

## <a name="chapter-5---model-expansion"></a>第5章-模型扩展

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目标

* 将 Astronaut 模型扩展为用户可与之交互的多个较小的部分。
* 使用导航和操作笔势分别移动各个部分。

### <a name="instructions"></a>说明

在本部分中，我们将完成下列任务：

1. 添加新的关键字 "**展开模型**"，展开 astronaut 模型。
2. 添加新的关键字 "**重置模型**"，以将模型返回到其原始形式。

为此，我们将向上一章的语音输入源添加另外两个关键字。 我们还将演示另一种处理识别事件的方法。

1. 在 **检查器** 中单击 " **AstronautManager** "，然后展开 **检查器** 中的 "**关键字**" 部分。
2. 单击右侧的， **+** 添加一个新关键字。
3. 将关键字键入为 **展开 "模型**"。 如果需要，可以随意添加密钥快捷方式。
4. 单击右侧的， **+** 添加一个新关键字。
5. 将关键字键入为 " **重置模型**"。 如果需要，可以随意添加密钥快捷方式。
6. 在 **检查器** 面板中，单击 " **添加组件** " 按钮。
7. 在菜单中，在 "搜索" 框中键入 **语音输入处理程序**。 选择搜索结果。
8. 勾选 **是全局侦听器**，因为我们希望这些命令可以正常运行，而不考虑我们的 GameObject。
9. 单击 "" **+** 按钮，然后从 "关键字" 下拉列表中选择 " **展开模型** "。
10. 单击 " **+** 响应" 下的 "AstronautManager"，并将 "  " 从 **层次结构** 拖到 "**无 (" 对象)** "字段。
11. 现在，单击 " **无函数** " 下拉列表，选择 " **AstronautManager**"，然后选择 " **ExpandModelCommand**"。
12. 单击 "语音输入处理程序" **+** 按钮，然后从 "关键字" 下拉列表中选择 " **重置模型** "。
13. 单击 " **+** 响应" 下的 "AstronautManager"，并将 "  " 从 **层次结构** 拖到 "**无 (" 对象)** "字段。
14. 现在，单击 " **无函数** " 下拉列表，选择 " **AstronautManager**"，然后选择 " **ResetModelCommand**"。

![如何设置第5章的语音输入源和处理程序](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>生成和部署

* 试试看！ 生成应用并将其部署到 HoloLens。
* 说 **展开 "模型** " 以查看扩展的 astronaut 模型。
* 使用 **导航** 旋转 astronaut 花色的各个部分。
* 假设 **移动 Astronaut** ，然后使用 **操作** 来移动 Astronaut 花色的各个部分。
* 说 **旋转 Astronaut** 再次旋转棋子。
* 假设 **Reset Model** 将 astronaut 返回到其原始形式。

## <a name="the-end"></a>结束

恭喜！ 你现在已经完成了 **MR 输入211：手势**。

* 你知道如何检测和响应手动跟踪、导航和操作事件。
* 了解导航和操作笔势之间的差异。
* 你知道如何更改光标以提供有关何时检测到手、即将丢失以及何时对象支持 (导航与操作) 的不同交互的视觉反馈。