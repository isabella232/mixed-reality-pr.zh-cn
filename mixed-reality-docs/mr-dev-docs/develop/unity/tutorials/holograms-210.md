---
title: HoloLens（第一代）输入 210 - 注视
description: 按照以下编码演练操作，使用 Unity，Visual Studio 和 HoloLens 了解注视概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，学院，教程，注视，HoloLens，混合现实院校，unity，混合现实耳机，windows Mixed reality 耳机，虚拟现实耳机，Windows 10
ms.openlocfilehash: e0d761c6292502f381618f8efa1bed9d26f0e6fbac8dbdafa8085e0bb41676ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220965"
---
# <a name="hololens-1st-gen-input-210-gaze"></a>HoloLens 第一代 () 输入210：注视

>[!IMPORTANT]
>混合现实学院教程的设计目的是 HoloLens (一代) 、Unity 2017 和混合现实沉浸式耳机。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新，可能与新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

"[注视](../../../design/gaze-and-commit.md)" 是输入的第一种形式，它显示用户的意图和认知。 MR Input 210 (亦 Project 资源管理器) 深入探讨了 Windows Mixed Reality 的与注视相关的概念。 我们会将上下文感知添加到游标和全息影像，充分利用你的应用程序对用户外观的了解。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

这里有一个友好的 astronaut，可帮助你学习注视的概念。 在 [尊敬的基本知识 101](../../../develop/unity/tutorials/holograms-101.md)中，我们有了一个简单的光标，只需跟随你的注视。 今天，我们要将一个步骤移到简单的游标之外：

* 我们要做的是光标，我们的全息影像看起来很清楚：这两项操作都将根据用户的查找位置或用户 *不* 在查找的位置而变化。 这使它们可以识别其上下文。
* 我们会将反馈添加到游标和全息影像，以便为用户提供更多的目标目标上下文。 这种反馈可以是音频和视觉对象。
* 我们将向你展示用于帮助用户达到更小目标的目标技术。
* 我们将向你展示如何使用定向指示器将用户的注意力吸引到你的全息影像。
* 我们将指导你在世界各地四处移动时，与用户一起使用全息影像。

>[!IMPORTANT]
>以下各章中嵌入的视频是使用旧版本的 Unity 记录的，混合现实 Toolkit。 虽然分步说明准确且最新，但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。 视频仍包含在 posterity 中，因为涵盖的概念仍适用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入 210：凝视</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 使用安装了正确的[工具](../../../develop/install-the-tools.md)配置的 Windows 10 PC。
* 一些基本 c # 编程能力。
* 应已完成 [尊敬的基本知识 101](../../../develop/unity/tutorials/holograms-101.md)。
* [为开发配置](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的 [文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 。 需要 Unity 2017.2 或更高版本。
* 取消将文件存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)查看。

### <a name="errata-and-notes"></a>勘误表和说明

* 在 Visual Studio 中，需要禁用 "仅我的代码" ("工具->选项" 下的 "未选中) "，以便在代码中命中断点。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 设置

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目标

* 针对 Hololens 开发优化 Unity。
* 导入资产并设置场景。
* 查看 HoloLens 中的 astronaut。

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择 **“新建项目”**。
3. 将项目命名为 **ModelExplorer**。
4. 输入 "位置" 作为先前未存档的 " **注视** " 文件夹。
5. 请确保将项目设置为“3D”。
6. 单击“创建项目”。

### <a name="unity-settings-for-hololens"></a>HoloLens 的 Unity 设置

我们需要让 Unity 知道我们要导出的应用程序应创建 [沉浸式视图](../../../design/app-views.md) 而不是2d 视图。 为此，我们将 HoloLens 添加为虚拟现实设备。

1. 请参阅 **编辑 > Project 设置 > 播放机**。
2. 在播放器设置的 "**检查器" 面板** 中，选择 " **Windows 存储**" 图标。
3. 展开“XR 设置”组。
4. 在“呈现”部分，选中“支持虚拟现实”复选框，添加新“虚拟现实 SDK 的”列表  。
5. 验证列表中是否显示“Windows 混合现实”。 如果没有，请选择 **+** 列表底部的 "" 按钮，然后选择 " **Windows 全息**"。

接下来，我们需要将脚本后端设置为 .NET。

1. 请参阅 **编辑 > Project 设置 > 播放机** (你仍可以从上一步) 来执行此操作。
2. 在播放器设置的 "**检查器" 面板** 中，选择 " **Windows 存储**" 图标。
3. 在 "**其他设置** 配置" 部分中，确保 "**脚本后端**" 设置为 " **.net** "

最后，我们将更新质量设置以实现 HoloLens 的快速性能。

1. 请参阅 **编辑 > Project 设置 > 质量**。
2. 在 "Windows 存储" 图标下，单击 **默认** 行中的向下箭头。
3. 对于 **Windows 应用商店应用**，请选择 "**非常低**"。

### <a name="import-project-assets"></a>导入项目资产

1. 右键单击 " **Project** " 面板中的 "**资产**" 文件夹。
2. 单击 " **导入包 > 自定义包**"。
3. 导航到下载的项目文件，然后单击 " **ModelExplorer. unitypackage**"。
4. 单击“打开”。
5. 加载包后，单击 " **导入** " 按钮。

### <a name="setup-the-scene"></a>设置场景

1. 在层次结构中，删除 **主摄像机**。
2. 在 **HoloToolkit** 文件夹中，打开 " **输入** " 文件夹，然后打开 " **prototyping** " 文件夹。
3. 将 **MixedRealityCameraParent** Prefab 从 **prototyping** 文件夹拖放到 **层次结构** 中。
4. 右键单击层次结构中的 **定向光** ，然后选择 " **删除**"。
5. 在 **全息影像** 文件夹中，将以下资产拖放到 **层次结构** 的根中：
    * **AstroMan**
    * **光线**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 启动 **播放模式** ▶查看 astronaut。
7. 再次单击 **播放模式** ▶ **停止**。
8. 在 **全息影像** 文件夹中，找到 **Fitbox** 资产，并将其拖到 **层次结构** 的根。
9. 在 "**层次结构**" 面板中选择 " **Fitbox** "。
10. 在 "**检查器**" 面板中，将 **AstroMan** 集合从 **层次结构** 中拖到 Fitbox 的 **全息图集合** 属性中。

### <a name="save-the-project"></a>保存项目

1. 保存新场景： **File > 将场景另存为**。
2. 单击 " **新建文件夹** "，然后将文件夹命名为 " **场景**"。
3. 将该文件命名为 "**ModelExplorer**" 并将其保存在 **幕后** 文件夹中。

### <a name="build-the-project"></a>生成项目

1. 在 Unity 中，选择 "**文件 > 生成设置**"。
2. 单击 " **添加打开的场景** " 添加场景。
3. 选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。
4. 如果要为 HoloLens 专门进行开发，请将 "**目标设备**" 设置为 " **HoloLens**"。 否则，请将其留在 **任何设备** 上。
5. 确保将 " **生成类型** " 设置为 " **D3D** "，并将 " **Sdk** " 设置为 " **最新安装** 的 (，这应是 SDK 16299 或更高) 版本
6. 单击“生成”。
7. 创建名为 "App" 的 **新文件夹** 。
8. 单击 **应用** 文件夹。
9. 按 " **选择文件夹**"。

当 Unity 完成后，将显示文件资源管理器窗口。

1. 打开 **应用程序** 文件夹。
2. 打开 **ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens：

1. 使用 Visual Studio 中的顶部工具栏将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x86**"。
2. 单击 "本地计算机" 按钮旁的下拉箭头，然后选择 " **远程计算机**"。
3. 输入 **HoloLens 设备 IP 地址**，并将身份验证模式设置为 **通用 (未加密的协议)**。 单击“选择”。 如果你不知道设备 IP 地址，请查看 **设置 > 网络 & Internet > 高级选项**。
4. 在顶部菜单栏中，单击 " **调试-> 启动而不调试** " 或按 **Ctrl + F5**。 如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。
5. 当应用程序已部署后，使用 **选择手势** 关闭 **Fitbox** 。

如果要部署到沉浸式耳机：

1. 使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，并将 "从 ARM 更改为 **x64**"。
2. 确保将部署目标设置为 " **本地计算机**"。
3. 在顶部菜单栏中，单击 " **调试-> 启动而不调试** " 或按 **Ctrl + F5**。
4. 当应用程序已部署后，通过将触发器拖到运动控制器上来关闭 **Fitbox** 。

## <a name="chapter-2---cursor-and-target-feedback"></a>第2章-游标和目标反馈

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目标

* 游标视觉对象设计和行为。
* 基于注视的光标反馈。
* 基于注视的全息影像反馈。

我们将使用一些游标设计原则，即：

* 游标始终存在。
* 不要让光标变得太小或太大。
* 避免阻碍内容。

### <a name="instructions"></a>说明

1. 在 **HoloToolkit\Input\Prefabs** 文件夹中，找到 " **InputManager** " 资产。
2. 将 **InputManager** 拖放到 **层次结构** 中。
3. 在 **HoloToolkit\Input\Prefabs** 文件夹中，找到 **光标** 资产。
4. 将 **光标** 拖放到 **层次结构** 中。
5. 选择 **层次结构** 中的 **InputManager** 对象。
6. 将 **光标** 对象从 **层次结构** 中拖放到 **检查器** 底部的 InputManager 的 **SimpleSinglePointerSelector** 的 **游标** 字段。

![简单的单指针选择器设置](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>生成和部署

1. **> Build 设置从文件** 重新生成应用。
2. 打开 **应用程序文件夹**。
3. 打开 **ModelExplorer Visual Studio 解决方案**。
4. 单击 " **调试-> 启动但不调试** " 或按 **Ctrl + F5**。
5. 观察如何绘制光标，以及如何在触摸全息图时更改其外观。

### <a name="instructions"></a>说明

1. 在 "**层次结构**" 面板中，展开 " **AstroMan** -> **GEO_G** -> **Back_Center** " 对象。
2. 双击 " **Interactible** " 以 Visual Studio 中打开它。
3. 取消注释 IFocusable 中的行 **OnFocusEnter ()** 和 IFocusable **中的** **()** 回调。 当焦点 (时，混合现实 Toolkit 的 InputManager 会调用这些类，) 进入和退出特定 GameObject 的碰撞器。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>我们使用 `EnableKeyword` 和 `DisableKeyword` 更高版本。 若要使用 Toolkit 的标准着色器在自己的应用程序中使用这些应用程序，需要遵循[Unity 指导原则，通过脚本访问材料](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 在这种情况下，我们已在 "资源" 文件夹中包含了所需的 [突出显示材料的三个变体](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) (查找姓名) 中突出显示的三个材料。

### <a name="build-and-deploy"></a>生成和部署

1. 与之前一样，生成项目并部署到 HoloLens。
2. 观察注视的目标是对象时，发生的情况。

## <a name="chapter-3---targeting-techniques"></a>第3章-目标技术

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目标

* 更轻松地定位全息影像。
* 稳定的自然头运动。

### <a name="instructions"></a>说明

1. 在 " **层次结构** " 面板中，选择 " **InputManager** " 对象。
2. 在 " **检查器** " 面板中，找到 " **注视" 稳定** 的脚本。 单击它可在 Visual Studio 中打开（如果想要查看）。
    * 此脚本将循环访问 Raycast 数据的示例，并帮助使用户看得更稳定，以实现精确定位。
3. 在 **检查器** 中，可以编辑 **存储的稳定性示例** 值。 此值表示稳定程序为计算稳定值而迭代的样本数。

## <a name="chapter-4---directional-indicator"></a>第4章-方向指示器

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目标

* 在光标处添加方向指示器以帮助查找全息影像。

### <a name="instructions"></a>说明

我们将使用 **DirectionIndicator** 文件，该文件将：

1. 如果用户不 gazing 在全息影像上，则显示方向指示器。
2. 如果用户在全息影像上 gazing，则隐藏方向指示器。
3. 更新方向指示器以指向全息影像。

让我们开始吧。

1. 单击 "**层次结构**" 面板中的 **AstroMan** 对象，然后 **单击箭头** 将其展开。
2. 在 "**层次结构**" 面板中，选择 " **AstroMan**" 下的 **DirectionalIndicator** 对象。
3. 在 **检查器** 面板中，单击 " **添加组件** " 按钮。
4. 在菜单中，键入 "搜索框 **方向" 指示器**。 选择搜索结果。
5. 在 "**层次结构**" 面板中，将 **cursor** 对象拖放到 **检查器** 的 **cursor** 属性上。
6. 在 **Project** 面板的 **全息影像** 文件夹中，将 **DirectionalIndicator** 资产拖放到 **检查器** 的 "**方向指示器**" 属性上。
7. 构建并部署应用。
8. 观看方向指示器对象如何帮助您找到 astronaut。

## <a name="chapter-5---billboarding"></a>第5章-Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目标

* 使用 billboarding，让全息影像始终面向你。

我们将使用 **GameObject 文件来** 保持面向用户的面向用户，使其始终面向用户。

1. 在 " **层次结构** " 面板中，选择 " **AstroMan** " 对象。
2. 在 **检查器** 面板中，单击 " **添加组件** " 按钮。
3. 在菜单中，在 "搜索" 框中键入 " **布告栏**"。 选择搜索结果。
4. 在 **检查器** 中，将 **透视轴** 设置为 **Y**。
5. 试试看！ 像以前一样构建并部署应用程序。
6. 了解布告栏对象如何面对您如何更改视点。
7. 立即从 **AstroMan** 中删除脚本。

## <a name="chapter-6---tag-along"></a>第6章-Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目标

* 使用 Tag-Along 让我们的全息影像围绕空间。

当我们处理此问题时，我们将通过以下设计约束指导：

* 内容应始终一目了然。
* 内容不应采用的方式。
* 打印头锁定内容不舒服。

此处使用的解决方案是使用 "标记式" 方法。

标记靠对象从不完全离开用户的视图。 可以将标记作为附加到用户 head 的对象（通过橡胶带）。 随着用户的移动，内容将一直滑入视图边缘，无需完全离开。 当用户 gazes 沿标记的对象时，它会更全面地进入视图。

我们将使用 **SimpleTagalong** 文件，该文件将：

1. 确定 Tag-Along 对象是否处于相机边界内。
2. 如果不在视图的 "被" Tag-Along 截
3. 否则，将 Tag-Along 定位到用户的默认距离。

为此，必须首先更改 **Interactible** 脚本，以便调用 **TagalongAction**。

1. 完成编码练习6，编辑 **Interactible** 。 (取消注释行84到 87) 。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

当点击全息影像时，与 **Interactible** 配对的 **InteractibleAction** 脚本将执行自定义操作。 在这种情况下，我们将专门用于标记。

* 在 "**脚本**" 文件夹中，单击要在 Visual Studio 中打开的 **TagalongAction** 资产。
* 完成编码练习，或将其更改为：
  * 在 **层次结构** 的顶部，在搜索栏中键入 " **ChestButton_Center** "，然后选择结果。
  * 在 **检查器** 面板中，单击 " **添加组件** " 按钮。
  * 在菜单中，在 "搜索" 框中键入 " **Tagalong" 操作**。 选择搜索结果。
  * 在 **全息影像** 文件夹中，查找 **Tagalong** 资产。
  * 选择 **层次结构** 中的 **ChestButton_Center** 对象。 将 **TagAlong** 对象从 **Project** 面板拖放到 "**检查器**" 中的 " **TagAlong** " 属性。
  * 将 **Tagalong 操作** 对象从 **检查器** 拖到 **Interactible** 脚本的 " **Interactible 操作**" 字段。
* 双击 " **TagalongAction** " 脚本，在 Visual Studio 中打开它。

![Interactible 设置](images/holograms210-interactible.png)

我们需要添加以下内容：

* 将功能添加到 TagalongAction 脚本中的 PerformAction 函数 (从 InteractibleAction) 继承。
* 将 billboarding 添加到 gazed 对象，并将透视轴设置为 XY。
* 然后，将简单的 Tag-Along 添加到对象。

下面是 **TagalongAction** 的解决方案：

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* 试试看！ 构建并部署应用。
* 观察内容如何沿着注视点的中心，但不会不断地进行阻止。