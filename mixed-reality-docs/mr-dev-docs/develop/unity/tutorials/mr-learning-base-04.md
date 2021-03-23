---
title: MRTK 教程 - 4. 定位场景中的对象
description: 本课程介绍如何定位场景中的对象，以及如何使用混合现实工具包 (MRTK) 来组织网格中的对象。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 求解器, 网格对象集合
ms.localizationpriority: high
ms.openlocfilehash: 9087800eca3536704ed4ef01a5d8178720b6a875
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590493"
---
# <a name="4-positioning-objects-in-the-scene"></a>4.定位场景中的对象

## <a name="overview"></a>概述

在本教程中，你将导入教程资产，并定位场景中提供的对象。

## <a name="objectives"></a>目标

* 了解如何定位场景中的对象
* 了解如何使用 MRTK 的网格对象集合功能

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

若要导入 Unity 自定义包，在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](images/mr-learning-base/base-04-section1-step1-1.png)

在“导入包…”窗口中，选择下载的 MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage，然后单击“打开”按钮：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](images/mr-learning-base/base-04-section1-step1-2.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](images/mr-learning-base/base-04-section1-step1-3.png)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](images/mr-learning-base/base-04-section1-step1-4.png)

## <a name="creating-the-parent-object"></a>创建父对象

在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中：

![Unity“创建空上下文弹出菜单”](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> 若要按上图所示并排显示“场景”和“游戏”窗口，请将“游戏”窗口拖放到“场景”窗口的右侧。 若要详细了解如何自定义工作区，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。

右键单击新创建的对象，选择“重命名”，然后将名称更改为“RoverExplorer” ：

![Unity“重命名上下文弹出菜单”](images/mr-learning-base/base-04-section2-step1-2.png)

在仍选中 RoverExplorer 对象的情况下，在“检查器”窗口中，按如下所示配置“转换”组件：

* **位置**：X = 0, Y = -0.6, Z = 2
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![选中并定位了 RoverExplorer 对象的 Unity](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> 摄像头表示用户头部，位于原点，即 X = 0，Y = 0，Z = 0。 一般情况下，Unity 中的 1 个单位大致对应现实生活中的 1 米。 但也存在例外情况，例如，当对象是缩放对象的子级时。 在上述场景中，RoverExplorer 位于用户头部前方 2 米、下方 0.6 米处。

## <a name="adding-the-tutorial-prefabs"></a>添加教程预制件

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹  ：

![选中了预制件文件夹的 Unity 项目窗口](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">预制件</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。

在“项目”窗口中，单击“Table”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：

* **位置**：X = 0, Y = -0.005, Z = 0
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 1.2，Y = 0.01，Z = 1.2

![选中并定位了新增的“表”预制件的 Unity](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> 若要按下图所示显示场景，请使用“场景”窗口右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景 Gizmo</a>，将视角调整为沿正向 Z 轴，双击 MixedRealityPlayspace 对象以将焦点对准摄像头，然后根据需要放大。

在“项目”窗口中，单击“RoverAssembly”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：

* **位置**：X = -0.1, Y = 0, Z = 0
* **旋转**：X = 0, Y = -135, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![选中并定位了新增的 RoverAssembly 预制件的 Unity](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>组织集合中的对象

在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“RoverParts”，并按如下所示配置“转换”组件   ：

* **位置**：X = 0, Y = 0.06, Z = 0
* **旋转**：X = 0, Y = 90, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![选中并定位了新创建的 RoverParts 对象的 Unity](images/mr-learning-base/base-04-section4-step1-1.png)

在“层次结构”窗口中，选择所有“RoverExplorer”>“RoverAssembly”>“RoverModel”>“Parts”子对象，右键单击它们，然后选择“复制”，创建每个部件的副本 ：

![选中了所有部件且具有“复制上下文弹出菜单”的 Unity](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> 若要选择多个相邻的对象，请按住 SHIFT 键，并同时使用鼠标选择第一个和最后一个对象。

在仍选中新复制的 Parts 子对象的情况下，单击它们并将其拖动到 RoverParts 对象上，使其成为 RoverParts 对象的子对象：

![将新复制的部件作为 RoverParts 对象的子类的 Unity](images/mr-learning-base/base-04-section4-step1-3.png)

为了更轻松地在场景中操作，请在“层次结构”窗口中，单击“RoverAssembly”对象左侧的眼睛图标，将此对象的“场景可见性”切换为关闭  。 这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性：

![RoverAssembly 场景可见性为关闭的 Unity](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> 若要详细了解“场景可见性”控件以及如何使用它们来优化场景视图和工作流，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。

在“层次结构”窗口中，将后缀“(1)”替换为“_Part”以整理 RoverParts 子对象的名称 ：

![清除了复制的部件名称的 Unity](images/mr-learning-base/base-04-section4-step1-5.png)

在“层次结构”窗口中，选择“RoverParts”对象，然后在“检查器”窗口中单击“添加组件”按钮，搜索并选择“GridObjectCollection”，以将“GridObjectCollection”组件添加到“RoverParts”对象  ：

![正在“添加组件网格对象集合”的 Unity RoverParts 对象](images/mr-learning-base/base-04-section4-step1-6.png)

按如下所示配置“GridObjectCollection”组件值：

* **排序类型**：按字母顺序
* **布局**：水平
* **单元格宽度**：0.25
* **到父项的距离**：0.38

![配置了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section4-step1-7.png)

然后单击“更新集合”按钮以更新 RoverParts 子对象的位置：

![应用了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>祝贺

本教程介绍了如何在场景中相对于用户定位对象，以及如何使用 MRTK 的网格对象集合功能来组织集合中的对象。

> [!div class="nextstepaction"]
>[下一教程：5.使用求解器创建动态内容](mr-learning-base-05.md)
