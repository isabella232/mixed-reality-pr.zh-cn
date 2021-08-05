---
title: MR 输入 213
description: 按照此编码教程操作，Visual Studio和沉浸式头戴显示设备了解运动控制器的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit， mixedrealitytoolkit， mixedrealitytoolkit-unity， 沉浸式， 运动控制器， 学院， 教程
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210106"
---
# <a name="mr-input-213-motion-controllers"></a>MR 输入 213：运动控制器

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](../develop/unity/tutorials/mr-learning-base-01.md)。

混合现实中的运动控制器增加了另一级别的交互性。 借助 [运动控制器](../design/motion-controllers.md)，我们可以以更自然的方式直接与对象交互，这类似于在现实生活中的物理交互，从而增加沉浸感，并让你更享受应用体验。

在 MR 输入 213 中，我们将通过创建简单的空间绘制体验来探索运动控制器的输入事件。 通过此应用，用户可以使用各种类型的画笔和颜色在三维空间中绘制。

## <a name="topics-covered-in-this-tutorial"></a>本教程中涵盖的主题

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器可视化效果**|**控制器输入事件**|**自定义控制器和 UI**|
|了解如何在 Unity 的游戏模式和运行时中呈现运动控制器模型。|了解不同类型的按钮事件及其应用程序。|了解如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。|

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入 213：运动控制器</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

请参阅此页上的沉浸式头戴显示设备 [安装清单](../develop/install-the-tools.md)。

* 本教程需要 [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>项目文件

* [下载项目](https://github.com/Microsoft/MixedReality213/archive/master.zip) 所需的文件，将文件提取到桌面。

>[!NOTE]
>如果要在下载之前查看源代码，可在[GitHub。](https://github.com/Microsoft/MixedReality213)

## <a name="unity-setup"></a>Unity 设置

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目标

* 优化 Unity 以Windows Mixed Reality开发
* 安装程序混合现实相机
* 设置环境

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择“打开”。
* 导航到桌面并找到之前未搜索的 **MixedReality213-master** 文件夹。
* 单击“选择文件夹”。
* Unity 完成项目文件的加载后，将能够看到 Unity 编辑器。
* 在 Unity 中，选择"**文件>生成设置"。**

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* 在 **"Windows"** 列表中选择"通用平台 **"，** 然后单击"**切换平台"** 按钮。
* 将"目标设备" **设置为"任何设备"**
* 将"生成类型"设置为 **"D3D"**
* 将 SDK 设置为 **"最新安装"**
* 检查 **Unity C# 项目**
    * 这样，无需重新生成 Unity 项目即可修改Visual Studio项目中的脚本文件。
* 单击 **"播放器设置"。**
* 在" **检查器** "面板中，向下滚动到底部
* 在 XR 设置中，选中 **"支持的虚拟现实"**
* 在"虚拟现实 SDK"下，选择 **"Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* 关闭 **"生成设置** 窗口。

### <a name="project-structure"></a>项目结构

本教程使用 **[混合现实Toolkit - Unity。](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 可在此页上找到 [版本](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**已完成的场景供参考**

* 你将在"场景"文件夹下找到两个 **已完成的** Unity 场景。
    * **MixedReality213：** 使用单个画笔完成场景
    * **MixedReality213高级**：已完成场景，用于使用多个画笔进行高级设计

**教程的新场景设置**

* 在 Unity 中，单击 **">"新建场景"**
* 删除 **主相机** 和 **定向光**
* 从Project **面板** 中，搜索以下预制项并将其拖动到"**层次结构"** 面板中：
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/Environment

    ![相机和环境](images/mr213-cameraenvironment-300px.jpg)

* 混合现实服务有两个相机预制Toolkit：
    * **MixedRealityCamera.prefab：** 仅相机
    * **MixedRealityCameraParent.prefab：** 相机 + 远程传送 + 边界
    * 在本教程中，我们将使用 **MixedRealityCamera** 而不使用远程传送功能。 因此，我们添加了简单的 **环境** 预制项，其中包含基本楼层，让用户感到不自在。
    * 若要详细了解使用 **MixedRealityCameraParent** 进行远程传送，请参阅 [高级设计 - 远程传送和定位](#advanced-design---teleportation-and-locomotion)

**Skybox 设置**

* 单击 **"窗口>照明> 设置**
* 单击 **"Skybox** 材料"字段右侧圆圈
* 键入"gray"，然后选择 **"SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat) 

    ![设置 skybox](images/mr123-skyboxsetting-400px.jpg)

* 选中 **"Skybox"** 选项，以查看分配的灰色渐变 skybox

    ![切换 skybox 选项](images/mr213-skyboxcheck-400px.jpg)

* 具有 MixedRealityCamera、环境和灰色天空框的场景将如下所示。

    ![MixedReality213 环境](images/mr213-environment-600px.jpg)

* 单击 **"文件>将场景另存为 "**
* **使用** 任意名称将场景保存在"场景"文件夹下

## <a name="chapter-1---controller-visualization"></a>第 1 章 - 控制器可视化效果

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目标

* 了解如何在 Unity 的游戏模式和运行时呈现运动控制器模型。

Windows Mixed Reality提供用于控制器可视化效果的动画控制器模型。 可通过多种方法在应用中实现控制器可视化：

* 默认 - 在不修改的情况下使用默认控制器
* 混合 - 使用默认控制器，但自定义其某些元素或覆盖 UI 组件
* 替换 - 对控制器使用自己的自定义 3D 模型

在本章中，我们将了解这些控制器自定义的示例。

### <a name="instructions"></a>说明

* 在Project **面板** 中，在搜索 **框中键入"MotionControllers"。** 还可以在 Assets/HoloToolkit/Input/Prefabs/ 下找到它。
* 将 **MotionControllers** 预制块拖到" **层次结构"面板** 中。
* 在"层次结构 **"面板中单击"MotionControllers"****预制** 块。

**MotionControllers 预制**

**MotionControllers** 预制有一个 **MotionControllerVisualizer** 脚本，该脚本为备用控制器模型提供槽。 如果分配自己的自定义 3D 模型（如手或手）并选中"始终使用备用左/右模型"，则会看到它们而不是默认模型。 我们将在第 4 章中使用此槽将控制器模型替换为画笔。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**说明**

* 在"**检查器**"面板中，双击 **"MotionControllerVisualizer 脚本**"，查看Visual Studio

**MotionControllerVisualizer 脚本**

**MotionControllerVisualizer** 和 **MotionControllerInfo** 类提供了访问 &修改默认控制器模型的方式。 **MotionControllerVisualizer** 订阅 Unity **的 InteractionSourceDetected** 事件，并会在找到控制器模型时自动实例化它们。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

控制器模型根据 [glTF](https://github.com/KhronosGroup/glTF)规范交付。 创建此格式以提供通用格式，同时改进传输和解压缩 3D 资产背后的过程。 在这种情况下，我们需要在运行时检索和加载控制器模型，因为我们希望尽可能无缝地提供用户体验，并且无法保证用户可能使用哪个运动控制器版本。 本课程通过混合现实Toolkit，使用 Khronos 组的[UnityGLTF 项目 的版本](https://github.com/KhronosGroup/UnityGLTF)。

传递控制器后，脚本可以使用 **MotionControllerInfo** 查找特定控制器元素的转换，以便它们能够正确定位自身。

在稍后的一章中，我们将了解如何使用这些脚本将 UI 元素附加到控制器。

*在某些脚本中，你会发现代码块 **#if！UNITY_EDITOR** 或 **UNITY_WSA**。这些代码块仅在部署到 UWP 运行时时在 UWP Windows。这是因为 Unity 编辑器和 UWP 应用运行时使用的 API 集不同。*

* **保存** 场景并 **单击播放按钮** 。

你将能够在头戴显示设备中查看具有运动控制器的场景。 可以看到按钮单击、指纹移动和触摸板触控突出显示的详细动画。

![MR213_Controller可视化效果默认值](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第 2 章 - 将 UI 元素附加到控制器

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目标

* 了解运动控制器的元素
* 了解如何将对象附加到控制器的特定部分

在本章中，你将了解如何将用户界面元素添加到控制器，用户可以随时轻松访问和操作这些元素。 你还将了解如何使用触摸板输入添加简单的颜色选取器 UI。

### <a name="instructions"></a>说明

* 在 **"Project"** 面板中，搜索 **"MotionControllerInfo 脚本**"。
* 在搜索结果中，双击 **"MotionControllerInfo 脚本**"，查看Visual Studio。

**MotionControllerInfo 脚本**

第一步是选择要将 UI 附加到的控制器元素。 这些元素在 **MotionControllerInfo.cs** 中的 **ControllerElementEnum** 中定义。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Home**
* **菜单**
* **把握**
* **Thumbstick**
* **Select**
* **触摸板**
* **指向姿势** – 此元素表示指向向前的控制器的提示。

**说明**

* 在 **"Project"** 面板中，搜索 **"AttachToController 脚本**"。
* 在搜索结果中，双击 **AttachToController** 脚本以查看Visual Studio。

**AttachToController 脚本**

**AttachToController** 脚本提供了一种将任何对象附加到指定控制器手部和元素的简单方法。

在 **AttachElementToController ()** 中，

* 使用 **MotionControllerInfo.Handedness 检查手部**
* 使用 **MotionControllerInfo.TryGetElement** () 
* 从控制器模型检索元素的转换后，将其下的对象作为父级，将对象的本地位置&旋转为零。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

使用 **AttachToController** 脚本的最简单方法就是从该脚本继承，就像在 **ColorPickerWheel 中所做的那样。** 只需重写 **OnAttachToController** 和 **OnDetachFromController** 函数，以在检测到/断开连接控制器时执行设置/细分。

**说明**

* 在Project **面板** 中，键入搜索框 **ColorPickerWheel**。 还可以在 Assets/AppPrefabs/ 下找到它。
* 将 **ColorPickerWheel** 预制块拖到 **"层次结构"** 面板中。
* 单击" **层次结构"面板中的 ColorPickerWheel** **预制** 块。
* 在"**检查器**"面板中，双击 **"ColorPickerWheel** 脚本"，查看Visual Studio。

![ColorPickerWheel 预制](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 脚本**

由于 **ColorPickerWheel** 继承 **了 AttachToController，** 因此它在检查器面板中显示 **"手部**"和 **"元素**"。 我们将 UI 附加到左侧控制器上的 Touchpad 元素。

![ColorPickerWheel 脚本](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** 重写 **OnAttachToController** 和 **OnDetachFromController，** 以订阅输入事件，下一章将用触摸板输入来选择颜色。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **保存** 场景并 **单击播放按钮** 。

**用于将对象附加到控制器的替代方法**

建议脚本继承自 **AttachToController 并** 重写 **OnAttachToController**。 但是，这可能并非始终可行。 另一种替代方法是使用它作为独立组件。 当你想要在不重构脚本的情况下将现有预制项附加到控制器时，这非常有用。 只需让类等待 IsAttached 设置为 true，然后再执行任何设置。 最简单的方法就是使用"Start"的协同例程。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第 3 章 - 使用触摸板输入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目标

* 了解如何获取触摸板输入数据事件
* 了解如何将触摸板轴位置信息用于应用体验

### <a name="instructions"></a>说明

* 在" **层次结构"面板中** ，单击 **"ColorPickerWheel"**
* 在检查 **器面板** 中的 **"动画器"下**，双击 **"ColorPickerWheelController"**
* 你将能够看到"动画 **器"选项卡** 已打开

**使用 Unity 的动画控制器显示/隐藏 UI**

为了通过动画显示和隐藏 **ColorPickerWheel** UI，我们使用的是 [Unity 的动画系统](https://docs.unity3d.com/Manual/AnimationOverview.html)。 将 **ColorPickerWheel** 的 **Visible** 属性设置为 true 或 false 可触发 **显示****和隐藏** 动画触发器。 **显示****和隐藏** 参数在 **ColorPickerWheelController** 动画控制器中定义。

![Unity 动画控制器](images/mr123-animationcontroller-550px.jpg)

**说明**

* 在" **层次结构"面板中** ，选择 **"ColorPickerWheel** 预制"
* 在"**检查器**"面板中，双击 **ColorPickerWheel** 脚本以查看Visual Studio

**ColorPickerWheel 脚本**

**ColorPickerWheel** 订阅 Unity **的 InteractionSourceUpdated** 事件，以侦听触摸板事件。

在 **InteractionSourceUpdated ()** 中，脚本首先进行检查以确保它：

* 实际上是 obj.state (触摸板事件。**touchpadTouched**) 
* 源自左侧控制器 (obj.state.source。**手部**) 

如果两者均为 true，则触摸板位置 (obj.state。**touchpadPosition**) 分配给 **selectorPosition**。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

在 **" () "** 中，它基于 **可见** 属性触发颜色选取器的动画器组件中的"显示和隐藏动画触发器"

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

在 **Update ()** 中 **，selectorPosition** 用于在色轮的网格碰撞体上投射射线，从而返回 UV 位置。 然后，可以使用此位置查找色轮纹理的像素坐标和颜色值。 其他脚本可通过 **SelectedColor** 属性访问此值。

![颜色选择器 Wheel Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>第 4 章 - 重写控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目标

* 了解如何使用自定义 3D 模型替代控制器模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>说明

* 在 **"层次结构"面板中单击"MotionControllers"。** 
* 单击"备用右控制器"字段 **右侧圆圈** 。
* 键入 **"BrushController"，** 然后从结果中选择预制。 可以在 Assets/AppPrefabs/**BrushController 下找到它**。
* 选中 **"始终使用备用右侧模型"**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** 预制块无需包含在"层次结构 **"面板** 中。 但是，若要签出其子组件，请执行：

* 在 **"Project** 面板中，键入 **BrushController，** 然后将 **BrushController** 预制块拖动到"**层次结构"** 面板中。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

你将在 **BrushController** 中查找 Tip 组件。  我们将使用其转换来开始/停止绘制线条。

* 从"**层次结构"面板中删除 BrushController。**
* **保存** 场景并 **单击播放按钮** 。 你将能够看到画笔模型替换了右侧运动控制器。

## <a name="chapter-5---painting-with-select-input"></a>第 5 章 - 使用选择输入进行绘制

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目标

* 了解如何使用"选择"按钮事件启动和停止线条绘制

### <a name="instructions"></a>说明

* 在 **仪表板面板中搜索 BrushController** **Project** 预制。
* 在"**检查器**"面板中，双击 **BrushController** 脚本以查看Visual Studio

**BrushController 脚本**

**BrushController** 订阅 InteractionManager 的 **InteractionSourcePressed** 和 **InteractionSourceReleased** 事件。 触发 **InteractionSourcePressed** 事件时，画笔的 **Draw** 属性设置为 true;触发 **InteractionSourceReleased** 事件时，画笔的 **Draw** 属性设置为 false。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

当 **Draw** 设置为 true 时，画笔将在实例化 Unity **LineRenderer 中生成点**。 对此预制名的引用保留在画笔的"笔 **划预制"字段中** 。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

若要使用颜色选取器 wheel UI 中当前选定的颜色 **，BrushController** 需要具有对 **ColorPickerWheel** 对象的引用。 由于 **BrushController** 预制件在运行时作为替换控制器实例化，因此必须在运行时设置对场景中对象的任何引用。 在这种情况下，我们使用 **GameObject.FindObjectOfType** 查找 **ColorPickerWheel**：

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **保存** 场景并 **单击播放按钮** 。 你将能够使用右侧控制器上的"选择"按钮绘制线条和绘制。

## <a name="chapter-6---object-spawning-with-select-input"></a>第 6 章 - 使用选择输入生成对象

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目标

* 了解如何使用"选择"和"抓取"按钮输入事件
* 了解如何实例化对象

### <a name="instructions"></a>说明

* 在Project **面板** 中，在搜索框中 **键入 ObjectSpawner。** 还可以在 Assets/AppPrefabs/ 下找到它
* 将 **ObjectSpawner** 预制块拖到 **"层次结构"面板** 中。
* 在 **"层次结构"面板中单击"ObjectSpawner"。** 
* **ObjectSpawner** 有一个名为"颜色源 **"的字段**。
* 从" **层次结构"面板** 中，将 **ColorPickerWheel** 引用拖到此字段中。

    ![对象生成器检查器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* 单击" **层次结构"面板中的 ObjectSpawner** **预制** 。
* 在"**检查器**"面板中，双击 **"ObjectSpawner** 脚本"，查看Visual Studio。

**ObjectSpawner 脚本**

**ObjectSpawner** 将基元网格的副本实例化 (立方体、球体、柱面) 到空间中。 检测到 **InteractionSourcePressed** 时，它会检查手部，以及它是 **InteractionSourcePressType.Grasp** 还是 **InteractionSourcePressType.Select** 事件。

对于 **"抓取** "事件，它会递增当前网格类型的索引 (球体、立方体、柱面) 

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

对于 **Select** 事件，在 **SpawnObject** () 中，新对象将实例化、无父级并释放到世界。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** 使用 **ColorPickerWheel** 设置显示对象材料的颜色。 为生成的对象提供此材料的实例，以便它们保留其颜色。

* **保存** 场景并 **单击播放按钮** 。

可以使用"抓取"按钮更改对象，并生成具有"选择"按钮的对象。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>生成应用并部署到混合现实门户

* 在 Unity 中，选择"**文件>生成设置"。**
* 单击 **"添加打开的** 场景"，将当前场景 **添加到生成 中的场景**。
* 单击“生成”。
* 创建名为 **"App"** 的新文件夹。
* 单击"应用 **"** 文件夹。
* 单击“选择文件夹”。
* Unity 完成后，将显示文件资源管理器窗口。
* 打开 **"应用"** 文件夹。
* 双击 **"YourSceneName.sln"Visual Studio** 解决方案文件。
* 使用中的顶部工具栏Visual Studio，将目标从"调试"更改为"发布 **"，从** ARM 更改为 **X64**。
* 单击"设备"按钮旁边的下拉箭头，然后选择"本地 **计算机"。**
* 单击 **菜单中的"调试>** "启动而不调试"，或按 **Ctrl + F5**。

现在，应用已生成并安装在 混合现实门户。 可以通过在 混合现实门户 中"开始"菜单它。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>高级设计 - 具有径向布局的画笔工具

![MixedReality213 Main](images/mr213-main-600px.jpg)

在本章中，你将了解如何将默认运动控制器模型替换为自定义画笔工具集合。 在"场景"文件夹下可以找到已完成的场景 **MixedReality213Advanced 供****参考。**

### <a name="instructions"></a>说明

* 在Project **面板** 中，在搜索框中键入 **BrushSelector。** 还可以在 Assets/AppPrefabs/ 下找到它
* 将 **BrushSelector** 预制块拖到 **"层次结构"面板** 中。
* 对于组织，创建名为画笔 **的空** GameObject
* 将以下预制项从 **"Project"拖动** 到 **"画笔"**
    * Assets/AppPrefabs/BrushFat
    * Assets/AppPrefabs/BrushThin
    * Assets/AppPrefabs/Eraser
    * Assets/AppPrefabs/MarkerFat
    * Assets/AppPrefabs/MarkerThin
    * Assets/AppPrefabs/**铅笔**

    ![画笔](images/mixedreality213-brushes-250px.png)

* 在 **"层次结构"面板中单击"MotionControllers** **预制"。**
* 在" **检查器"** 面板中，取消 **选中"运动控制器** 可视化工具"上的"始终使用备用 **右模型"**
* 在" **层次结构"面板中** ，单击 **"BrushSelector"**
* **BrushSelector** 有一个名为 **ColorPicker** 的字段
* 从 "**层次结构**" 面板中，将 " **ColorPickerWheel** " 拖动到 **检查器** 面板中的 " **ColorPicker** " 字段。

    ![将 ColorPickerWheel 分配给画笔选择器](images/mr213-brushselector-500px.jpg)

* 在 " **层次结构** " 面板中的 " **BrushSelector** prefab" 下，选择 " **Menu** " 对象。
* 在 " **检查器** " 面板中的 **LineObjectCollection** 组件下，打开 " **对象** 数组" 下拉列表。 你将看到6个空槽。
* 从 " **层次结构** " 面板中，将 " **画笔** " 下的每个 prototyping 父级以任意顺序拖动到这些槽。  (确保从场景中拖动 prototyping，而不是从项目文件夹中的 prototyping 中拖动。 ) 

![画笔选择器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

由于 **BrushSelector** 继承了 **AttachToController**，它将在 "**检查器**" 面板中显示 **左右手使用习惯** 和 **元素** 选项。 我们选择了 " **向右** " 并将画笔工具 **连接到右侧** 的右控制器。

**BrushSelector** 利用了两个实用工具：

* **椭圆形**：用于沿椭圆形状生成空间中的点。
* **LineObjectCollection**：使用任意 Line 类生成的点（ (例如) 的椭圆形）来分发对象。 这就是我们用来沿椭圆形状放置画笔的内容。

结合使用时，可以使用这些实用程序创建放射状菜单。

**LineObjectCollection 脚本**

**LineObjectCollection** 具有控件沿行分布的对象的大小、位置和旋转。 这对于创建径向菜单（如画笔选择器）很有用。 若要创建画笔的外观，使其在接近中心选定位置的情况下进行缩放， **ObjectScale** 曲线会在中心处峰值，并在边缘处关闭 tapers。

**BrushSelector 脚本**

对于 **BrushSelector**，我们选择了使用过程动画。 首先，画笔模型由 **LineObjectCollection** 脚本分布在一个椭圆中。 然后，每个画笔负责根据其 **DisplayMode** 值来维护其在用户的手边，这会根据所选内容进行更改。 我们选择了过程方法，因为当用户选择画笔时，画笔位置转换的概率很高。 Mecanim 动画可以合理地处理中断，但比简单的 Lerp 操作要复杂得多。

**BrushSelector** 结合使用这两种方法。 检测到触摸板输入后，画笔选项将变为可见，并沿径向菜单向上缩放。 超时时间段之后 (表示用户选择了) 画笔选项再次缩小，只留下所选的画笔。

**可视化触摸板输入**

即使在完全替换控制器模型的情况下，显示原始模型输入的输入也可能会很有帮助。 这有助于使用户的操作成为现实。 对于 **BrushSelector** ，我们选择了在收到输入时使触摸板短暂可见。 这是通过从控制器检索触摸板元素，将其材料替换为自定义材料，然后根据收到的触摸板输入的最后时间向该材料的颜色应用渐变来完成的。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**带有触摸板输入的画笔工具选择**

当画笔选择器检测到触摸板的按下输入时，它将检查输入的位置以确定其是否在左侧或右侧。

**笔划粗细与 selectPressedAmount**

可以通过 **selectPressedAmount** 获取按下量的模拟值，而不是 **InteractionSourcePressed ()** 中的 **InteractionSourcePressType 事件。** 可以在 **InteractionSourceUpdated ()** 中检索此值。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**橡皮擦脚本**

**橡皮擦** 是一种特殊类型的画笔，用于重写基 **画笔** 的 **DrawOverTime ()** 函数。 绘图为 true 时，橡皮擦检查其刀尖是否与任何现有画笔笔划相交。 如果已添加到队列中，则会将它们添加到要缩减和删除的队列中。

## <a name="advanced-design---teleportation-and-locomotion"></a>高级设计-Teleportation 和 locomotion

如果要允许用户使用 teleportation 在场景周围移动，请使用 **MixedRealityCameraParent** 而不是 **MixedRealityCamera**。 还需要添加 **InputManager** 和 **DefaultCursor**。 由于 **MixedRealityCameraParent** 已将 **MotionControllers** 和 **边界** 包含为子组件，因此应该删除现有的 **MotionControllers** 和 **环境** prefab。

### <a name="instructions"></a>说明

* 在 **层次结构** 面板中删除 **"MixedRealityCamera**"、"**环境**" 和 " **MotionControllers** "
* 从 " **Project" 面板** 中，搜索并将以下 prototyping 拖到 "**层次结构**" 面板中：
    * 资产/AppPrefabs/Input/Prototyping/**MixedRealityCameraParent**
    * 资产/AppPrefabs/Input/Prototyping/**InputManager**
    * 资产/AppPrefabs/Input/Prototyping/Cursor/**DefaultCursor**

    ![混合现实相机父项](images/mr213-cameraparent-300px.png)

* 在 **层次结构** 面板中，单击 "**输入管理器**"
* 在 " **检查器** " 面板中，向下滚动到 **简单的单指针选择器** 部分
* 从 " **层次结构** " 面板中，将 **DefaultCursor** 拖到 **Cursor** 字段

    ![分配 DefaultCursor](images/mr213-defaultcursor-500px.png)

* **保存** 场景并单击 " **播放** " 按钮。 你将能够使用操纵杆向左或向右旋转。

## <a name="the-end"></a>结束

这就是本教程的结尾！ 你已了解：

* 如何使用 Unity 的游戏模式和运行时中的运动控制器模型。
* 如何使用不同类型的按钮事件及其应用程序。
* 如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。

现在，你可以开始创建自己的具有运动控制器的沉浸式体验！

## <a name="completed-scenes"></a>已完成场景

* 在 Unity 的 **Project** 面板中，单击 "**场景**" 文件夹。
* 你将发现两个 Unity 场景 **MixedReality213** 和 **MixedReality213Advanced**。
    * **MixedReality213**：通过单画笔完成场景
    * **MixedReality213Advanced**：具有多个画笔并带有 "选择按钮的按量" 示例的已完成场景

## <a name="see-also"></a>另请参阅

* [MR 输入213项目文件](https://github.com/Microsoft/MixedReality213)
* [混合现实 Toolkit 运动控制器测试场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合现实 Toolkit 获取机制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [运动控制器开发指南](../design/motion-controllers.md)