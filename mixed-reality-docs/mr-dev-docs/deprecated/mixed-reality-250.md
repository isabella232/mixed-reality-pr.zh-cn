---
title: MR 250-HoloLens 和沉浸式耳机
description: 按照以下编码演练操作，使用 Unity、Visual Studio、HoloLens 和 Windows Mixed Reality 耳机，了解在混合现实设备之间共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、运动控制器、共享、xbox 控制器、网络、跨设备
ms.openlocfilehash: 9f1b136193feefece3235d853503c05c69dbd451f9c2916fb178f1bcac0e3972
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208307"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 共享 250：HoloLens 和沉浸式头戴显示设备

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](../develop/unity/tutorials/mr-learning-base-01.md)。

利用通用 Windows 平台 (UWP) 的灵活性，可以轻松创建跨多个设备的应用程序。 通过这种灵活性，我们可以创建利用每个设备的优势的体验。 本教程将介绍在 HoloLens 和 Windows Mixed Reality 沉浸式耳机上都运行的基本共享体验。 此内容最初在华盛顿州西雅图的 Microsoft Build 2017 大会上交付。

**在本教程中，我们将：**

* 使用 UNET 设置网络。
* 跨混合现实设备共享全息影像。
* 根据正在使用的混合现实设备，建立不同的应用程序视图。
* 通过一些简单的测验题，创建 HoloLens 用户指导沉浸式耳机用户的共享体验。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 共享 250：HoloLens 和沉浸式头戴显示设备</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 使用[必要的开发工具](../develop/install-the-tools.md)并将其[配置为支持 Windows Mixed Reality 沉浸式耳机](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 Windows 10 PC。
* 适用于你的电脑的 Xbox 控制器。
* 至少一个 HoloLens 设备和一个沉浸式耳机。
* 允许 UDP 广播进行发现的网络。

### <a name="project-files"></a>项目文件

* 下载项目所需的 [文件](https://github.com/Microsoft/MixedReality250/archive/master.zip) 。 将文件提取到易于记忆的位置。
* 此项目需要[Windows Mixed Reality 支持的 Unity 推荐版本](../develop/install-the-tools.md)。

>[!NOTE]
>如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/MixedReality250)查看。

## <a name="chapter-1---holo-world"></a>第1章-Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目标

请确保开发环境已准备好使用简单项目。

### <a name="what-we-will-build"></a>要生成的内容

在 HoloLens 或 Windows Mixed Reality 沉浸式耳机上显示全息图的应用程序。

### <a name="steps"></a>步骤

* 打开 Unity。
    * 选择“打开”。
    * 导航到在其中提取项目文件的位置。
    * 单击“选择文件夹”。
    * *Unity 第一次处理项目需要一些时间。*
* 检查 Unity 中是否已启用混合现实。
    * 打开 "生成设置" 对话框 (**Control + Shift + B** 或 **文件 > "生成设置 ...** ") 。
    * 选择 **通用 Windows 平台** 然后单击 "**切换平台**"。
    * 选择 "**编辑>播放器" 设置**。
    * 在右侧的 **检查器** 面板中，展开 " **XR 设置**"。
    * 选中 " **支持虚拟现实** " 框。
    * *Windows Mixed Reality 应为虚拟现实 SDK。*
* 创建场景。
    * 在 **层次结构** 中右键单击 " **主相机** "，然后选择 " **删除**"。
    * 从 **HoloToolkit > 输入 > prototyping** 将 **MixedRealityCameraParent** 拖到 **层次结构** 中。
* 将全息影像添加到场景
    * From **AppPrefabs** 将 **Skybox** 拖到 **场景视图**。
    * From **AppPrefabs** 将 **经理** 拖到 **层次结构** 中。
    * From **AppPrefabs** 将 **岛** 拖到 **层次结构** 中。
* 保存并生成
    * 保存 (**Control + S** 或 **File > save 场景**) 
    * 由于这是新场景，因此需要将其命名为。 名称并不重要，但我们使用的是 SharedMixedReality。
* 导出到 Visual Studio
    * 打开 "生成" 菜单 (**Control + Shift + B** 或 **File > build 设置**) 
    * 单击 " **添加打开的场景"。**
    * 检查 **Unity c # 项目**
    * 单击“生成”。
    * 在出现的 "文件资源管理器" 窗口中，创建一个名为 " **应用**" 的新文件夹。
    * 单击 **应用** 文件夹。
    * 按 " **选择文件夹"。**
    * **等待生成完成**
    * 在出现的 "文件资源管理器" 窗口中，导航到 " **应用** " 文件夹。
    * 双击 " **SharedMixedReality** " 以启动 Visual Studio
* 从 Visual Studio 生成
    * 使用顶部工具栏将目标更改为 " **发布** " 和 " **x86**"。
    * 单击 "**本地计算机**" 旁边的箭头，然后选择要部署到的 **设备** HoloLens
    * 单击 " **设备** " 旁边的箭头，并选择 "要为混合现实耳机部署的 **本地计算机** "。
    * 单击 " **调试"->"无调试开始** " 或按 **F5** 启动应用程序。

### <a name="digging-into-the-code"></a>深入到代码中

在 "项目" 面板中，导航到 " **Assets\HoloToolkit\Input\Scripts\Utilities** "，然后双击 " **MixedRealityCameraManager** " 以将其打开。

**概述：** MixedRealityCameraManager 是一个简单的脚本，可根据设备调整质量级别和背景设置。 此处的项是 HolographicSettings。 IsDisplayOpaque，它允许脚本检测设备是否为 HoloLens (IsDisplayOpaque 返回 false) 或沉浸式耳机 (IsDisplayOpaque 返回 true) 。

### <a name="enjoy-your-progress"></a>欣赏你的进度

此时，应用程序将只呈现一个全息图。 稍后我们将向全息图添加交互。 这两个设备会将两个全息图呈现相同的。 沉浸式耳机还会呈现蓝天和云背景。

## <a name="chapter-2---interaction"></a>第2章-交互

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目标

演示如何处理 Windows Mixed Reality 应用程序的输入。

### <a name="what-we-will-build"></a>要生成的内容

基于第1章中的应用程序，我们将添加功能，使用户能够选择全息影像，并将其放在 HoloLens 或沉浸式头戴式耳机上的虚拟表中的实际表面。

**输入刷新器：** 在 HoloLens **单击 "选择手势"。** 在沉浸式耳机上，我们将使用 Xbox 控制器上 **的按钮。** 有关详细信息，请查看 [交互模型概述](../design/interaction-fundamentals.md)。

### <a name="steps"></a>步骤

* 添加输入管理器
    * 从 **HoloToolkit >输入>预制** 将 **InputManager** 拖动到 **Hierarchy** 作为 Managers 的 **子级**。
    * 从 **HoloToolkit >输入>"** 预制>光标 **拖动** 到 **"层次结构"。**
* 添加空间映射
    * 从 **HoloToolkit > SpatialMapping >预制将** **SpatialMapping** 拖动到 **"层次结构"。**
* 添加虚拟 Playspace
    * 在 **"层次结构"中** 展开 **"MixedRealityCameraParent"，选择****"边界"**
    * 在 **"检查** 器"面板中，选中复选框以启用 **"边界"**
    * 从 **AppPrefabs 将** **VRRoom** 拖动 **到"层次结构"。**
* 添加 WorldAnchorManager
    * 在 **"层次结构"中**，选择"**管理器"。**
    * 在 **检查器** 中，单击 **"添加组件"。**
    * 键入 **World Anchor Manager**。
    * 选择 **"世界定位点管理器** "以添加它。
* 将 TapToPlace 添加到岛
    * 在 **"层次结构"中**，展开"**岛"。**
    * 选择 **"MixedRealityLand"。**
    * 在 **检查器** 中，单击 **"添加组件"。**
    * 键入 **"点击放置"** 并选择它。
    * 选中 **"在点击 时放置父级"。**
    * 将 **"放置偏移** (**设置为 0、0.1、0) 。**
* 像以前一样保存和生成

### <a name="digging-into-the-code"></a>深入了解代码

**脚本 1 - GamepadInput.cs**

在项目面板中，导航到 **Assets\HoloToolkit\Input\Scripts\InputSources，** 然后双击 **GamepadInput.cs** 打开它。 在项目面板中的同一路径中，也双击 **"InteractionSourceInputSource.cs"。**

请注意，这两个脚本都有一个公共基类 BaseInputSource。

BaseInputSource 保留对 InputManager 的引用，该引用允许脚本触发事件。 在这种情况下，InputClicked 事件是相关的。 当我们进入脚本 2 TapToPlace 时，必须记住这一点。 对于 GamePadInput，我们轮询控制器上的 A 按钮以按下，然后引发 InputClicked 事件。 对于 InteractionSourceInputSource，我们引发 InputClicked 事件以响应 TappedEvent。

**脚本 2 - TapToPlace.cs**

在项目面板中，导航到 **Assets\HoloToolkit\SpatialMapping\Scripts，** 然后双击 **TapToPlace.cs** 打开它。

创建全息应用程序时，许多开发人员想要实现的第一件事是全息影像手势输入。 因此，我们努力对此脚本进行彻底注释。 本教程需要重点介绍一些内容。

首先，请注意 TapToPlace 实现 IInputClickHandler。 IInputClickHandler 公开处理 GamePadInput.cs 或 InteractionSourceInputSource.cs 引发 InputClicked 事件的函数。 当具有 TapToPlace 的对象聚焦时，当 BaseInputSource 检测到单击时，将调用 OnInputClicked。 在 Xbox 控制器上HoloLens或按 A 按钮将触发事件。

第二个是在更新中执行代码，以查看是否正在查看图面，以便我们可以将游戏对象放在图面上，就像表一样。 沉浸式头戴显示设备没有真实表面的概念，因此表示表顶部 (Vroom > TableThingy > Cube) 的对象已标记为 SpatialMapping 物理层，因此 Update 中的光线投射会与虚拟表顶部发生冲突。

### <a name="enjoy-your-progress"></a>享受进度

这次可以选择要移动的岛。 在HoloLens可以将岛移动到实际表面。 在沉浸式头戴显示设备中，可以将岛移动到我们添加的虚拟表。

## <a name="chapter-3---sharing"></a>第 3 章 - 共享

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目标

确保正确配置网络，并详细说明如何在设备之间共享空间定位点。

### <a name="what-we-will-build"></a>我们将生成什么

我们将项目转换为多人游戏项目。 我们将添加 UI 和逻辑来托管或加入会话。 HoloLens用户将在与云的会话中看到彼此的头部，沉浸式头戴显示设备用户具有靠近定位点位置的云。 沉浸式头戴显示设备中的用户将看到HoloLens相对于场景原点的用户。 HoloLens用户将在同一位置看到岛全息影像。 必须注意，在本章中，沉浸式头戴显示设备中的用户不会在岛中，但行为与 HoloLens 非常类似，具有岛群的眼睛视图。

### <a name="steps"></a>步骤

* 删除岛和 VRRoom
    * 在 **"层次结构"中** ，右键单击 **"岛"，选择** " **删除"**
    * 在 **"层次结构"中** ，右键单击 **"VRRoom"，选择** " **删除"**
* 添加 Usland
    * 从 **AppPrefabs** 拖动 **Usland** 到 **Hierarchy**。
* 从 **AppPrefabs** 将以下各项拖动到 **"层次结构"：**
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 像以前一样保存和生成

### <a name="digging-into-the-code"></a>深入了解代码

在项目面板中，导航到 **Assets\AppPrefabs\Support\SharingWithUnet\Scripts，** 然后双击 **UnetAnchorManager.cs**。 一个设备HoloLens另一个设备共享跟踪HoloLens使两个设备可以共享同一空间这一功能几乎不小。 当两个或多个人员可以使用同一数字数据进行协作时，混合现实功能将处于活动状态。

在此脚本中需要指出的一些要点：

在 start 函数中，请注意 **IsDisplayOpaque 的检查**。 在这种情况下，我们假设已建立定位点。 这是因为沉浸式头戴显示设备不会公开导入或导出定位点的方法。 但是，如果我们在设备HoloLens，此脚本将实现设备之间的共享定位点。 启动会话的设备将创建用于导出的定位点。 加入会话的设备会从启动会话的设备请求定位点。

**出口：**

当用户创建会话时，NetworkDiscoveryWithAnchors 将调用 UNETAnchorManagers CreateAnchor 函数。 让我们遵循 CreateAnchor 流。

我们首先执行一些管理，清除为以前的定位点收集的任何数据。 然后，检查是否有要加载的缓存定位点。 定位点数据往往介于 5 到 20 MB 之间，因此，重新使用缓存的定位点可以节省我们需要通过网络传输的数据量。 稍后我们将了解此操作的工作原理。 即使我们要重新使用定位点，也需要准备好定位点数据，以防没有定位点的新客户端联接。

在准备定位点数据时，WorldAnchorTransferBatch 类公开了准备定位点数据以发送到其他设备或应用程序的功能，以及用于导入定位点数据的功能。 由于我们位于导出路径上，因此我们将定位点添加到 WorldAnchorTransferBatch 并调用 ExportAsync 函数。 然后，ExportAsync 将在生成要导出的数据时调用 WriteBuffer 回调。 导出所有数据后，将调用 ExportComplete。 在 WriteBuffer 中，我们将数据块添加到保留用于导出的列表中。 在 ExportComplete 中，我们将列表转换为数组。 此外，还设置了 AnchorName 变量，这将触发其他设备请求定位点（如果它们没有定位点）。

在某些情况下，定位点不会导出或会创建很少的数据，因此我们将重试。 在这里，我们只需再次调用 CreateAnchor。

导出路径中的最后一个函数是 AnchorFoundRemotely。 当另一个设备找到定位点时，该设备将告知主机，主机将使用该定位点作为信号，指示定位点是"良好定位点"并可以缓存。

**进口：**

当HoloLens会话时，它需要导入定位点。 在 UNETAnchorManager 的 Update 函数中，将对 AnchorName 进行轮询。 定位点名称更改时，导入过程开始。 首先，我们尝试从本地定位点存储中加载具有指定名称的定位点。 如果已有该数据，则可以使用它，而无需再次下载数据。 如果没有，请调用 WaitForAnchor，这将启动下载。

下载完成后，将调用 NetworkTransmitter_dataReadyEvent。 这会向更新循环发出信号，以便对下载的数据调用 ImportAsync。 导入过程完成后，ImportAsync 将调用 ImportComplete。 如果导入成功，定位点将保存在本地播放机存储区中。 PlayerController 实际上会调用 AnchorFoundRemotely，以让主机知道已经建立好锚。

### <a name="enjoy-your-progress"></a>欣赏你的进度

这次，具有 HoloLens 的用户将使用用户界面中的 "**启动会话**" 按钮来托管会话。 HoloLens 或沉浸式耳机上的其他用户将选择该会话，然后在 UI 中选择 "**加入会话**" 按钮。 如果有多个用户使用 HoloLens 设备，则它们将具有红色的云。 对于每个沉浸式耳机，还会有一个蓝色的云，但蓝色云不会位于耳机上方，因为耳机不会尝试查找与 HoloLens 设备相同的世界坐标空间。

项目中的这一点是包含共享应用程序;这并不是很多，而且可以充当基线。 在接下来的章节中，我们将开始为用户带来体验。 若要获取有关共享体验设计的更多指导，请转到此处。

## <a name="chapter-4---immersion-and-teleporting"></a>第4章-浸入式和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目标

为每种类型的混合现实设备满足经验。

### <a name="what-we-will-build"></a>要生成的内容

我们将更新应用程序，以通过沉浸式视图将沉浸式头戴式耳机用户置于岛中。 HoloLens 用户仍将获得岛的鸟瞰视图。 每种设备类型的用户可以看到其他用户出现在世界中。 例如，沉浸式耳机用户可以查看岛上其他路径上的其他头像，并在岛上方看到 HoloLens 用户作为巨大的云。 如果 HoloLens 用户正在查看岛，沉浸式耳机用户也会看到 HoloLens 用户的 "注视" 的光标。 HoloLens 用户将看到岛上的头像来表示每个沉浸式耳机用户。

**已更新沉浸式设备的输入：**

* Xbox 控制器上的左缓冲器和右缓冲器按钮将旋转播放机
* 按住 Xbox 控制器上的 Y 按钮将启用 [传送](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 光标。 如果在释放 Y 按钮时光标有旋转箭头指示器，则会 teleported 光标所在的位置。

### <a name="steps"></a>步骤

* 将 MixedRealityTeleport 添加到 MixedRealityCameraParent
    * 在 **层次结构** 中，选择 **Usland**。
    * 在 **检查器** 中，启用 **级别控制**。
    * 在 **层次结构** 中，选择 **MixedRealityCameraParent**。
    * 在 **检查器** 中，单击 " **添加组件**"。
    * 键入 **混合现实传送** 并将其选中。

### <a name="digging-into-the-code"></a>深入到代码中

沉浸式耳机用户将通过电缆受限到其电脑上，但岛比电缆长。 若要进行补偿，我们需要能够独立于用户的动作移动相机。 有关设计混合现实应用 ([程序的详细](../design/comfort.md) 信息，请参阅 locomotion) 。

若要描述此过程，请定义两个术语。 首先， **dolly** 将是独立于用户移动相机的对象。 **Dolly** 的子游戏对象将是 **主摄像机**。 将相机连接到用户的头。

在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **MixedRealityTeleport**"。

MixedRealityTeleport 有两个作业。 首先，它使用缓冲器处理旋转。 在更新函数中，我们轮询 LeftBumper 和 RightBumper 上的 "ButtonUp"。 GetButtonUp 仅在第一帧上返回 true，按钮在关闭后就会正常运行。 如果引发了任一按钮，则我们知道用户需要旋转。

旋转时，我们使用名为 "淡化 control" 的简单脚本，进行淡出并淡出。 这样做是为了防止用户看到可能导致 discomfort 的非自然移动。 淡入和淡出效果非常简单。 在 **摄像机** 前面有一个黑色的故障诊断。 淡出时，将从0到1转换 alpha 值。 这会逐渐导致四个黑色像素渲染和遮蔽。 当淡化后，转换后的 alpha 值将返回零。

计算旋转时，请注意，我们要旋转 **dolly** ，但计算出 **摄像机** 周围的旋转。 这一点很重要，因为在 **摄像机** 远离0，0，0时，dolly 的旋转就会从用户的角度来看。 事实上，如果不围绕相机位置旋转，用户将在 **dolly** 上移动，而不是旋转。

MixedRealityTeleport 的第二个作业是处理移动 **dolly**。 这是在 SetWorldPosition 中完成的。 SetWorldPosition 采用所需的世界位置，该位置是用户想要 percieve 具有的位置。 我们需要将 **dolly** 置于该位置，而不是 **主摄像机** 的本地位置，因为每帧都会添加该偏移量。

第二个脚本调用 SetWorldPosition。 让我们看看该脚本。 在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **TeleportScript**"。

此脚本比 MixedRealityTeleport 更复杂一些。 脚本正在检查 Xbox 控制器上的 Y 按钮是否已关闭。 当按钮被按下时，将呈现一个传送光标，并且该脚本将从用户的注视位置转换一条射线。 如果该射线与更多或更少地指向的图面冲突，则会将该图面视为传送到的一个好图面，并将启用传送光标上的动画。 如果该射线不会与某个面上更多或更少的向上箭头发生冲突，则将禁用游标上的动画。 当 "Y" 按钮被释放并且射线的计算点为有效位置时，该脚本将使用与该射线相交的位置来调用 SetWorldPosition。

### <a name="enjoy-your-progress"></a>欣赏你的进度

这次您需要查找朋友。

同样，具有 HoloLens 的用户将托管一个会话。 其他用户将加入会话。 应用程序将把前三名用户加入到岛上三个路径之一上的沉浸式耳机上。 请随时浏览本部分中的岛。

要注意的详细信息：

1. 你可以在云中看到人脸，这有助于沉浸用户查看 HoloLens 用户正在查找的方向。
2. 岛上的头像具有旋转 necks。 它们不会遵循用户正在执行的操作， (我们没有) 的信息，而是为了获得良好的体验。
3. 如果 HoloLens 用户正在查看岛，沉浸用户会看到其光标。
4. 表示用户投影 HoloLens 的云。

## <a name="chapter-5---finale"></a>第5章-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目标

在这两种设备类型之间创建协作式交互式体验。

### <a name="what-we-will-build"></a>要生成的内容

在第4章，当具有沉浸式耳机的用户在岛上出现谜题附近时，HoloLens 用户将收到一条工具提示，其中包含对测验题的线索。 所有沉浸式耳机用户都在火箭房间内进入了测验题后，就会启动火箭。

### <a name="steps"></a>步骤

* 在 **层次结构** 中，选择 **Usland**。
* 在 **检查器** 的 " **级别控制**" 中，选中 " **启用协作**"。

### <a name="digging-into-the-code"></a>深入到代码中

现在让我们看看 LevelControl。 此脚本是游戏逻辑的核心，并且保持游戏状态。 由于这是一个使用 UNET 的多玩家游戏，我们需要了解数据的流动方式，至少足以修改本教程。 有关 UNET 的更完整概述，请参阅 Unity 的文档。

在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **LevelControl**"。

让我们了解沉浸式耳机如何指示它们已准备好进行火箭启动。 通过在与岛上的三个路径相对应的布尔列表中设置三个布尔之一，可以传达火箭的启动准备情况。 当分配到路径的用户在火箭房间内的棕色垫的顶部时，将设置路径的 bool。 好了，现在来了解详细信息。

我们将从更新 () 函数开始。 你会注意到有一个 "使用" 函数。 我们在开发过程中使用这种测试火箭启动和重置顺序。 它在多用户体验中不起作用。 但愿您内在化以下信息可以使其正常工作。 检查是否应该是，我们会检查是否已沉浸本地播放器。 我们想要重点介绍我们的目标。 在 if (沉浸) 检查的情况下，调用 CheckGoal 隐藏在 **EnableCollaboration** bool 后面。 这对应于完成本章中的步骤时选中的复选框。 在 EnableCollaboration 内部，我们看到对 CheckGoal () 的调用。

CheckGoal 进行一些数学计算，看看是否有更多或更少的时间。 当我们进行调试时，我们将进行调试。记录 "到达目标"，然后调用 "SendAtGoalMessage () "。 在 SendAtGoalMessage 中，我们调用 playerController. SendAtGoal。 为节省时间，请参阅以下代码：

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

请注意，SendAtGoalMessage 调用 CmdSendAtGoal，后者调用 levelState 中的 SetGoalIndex。 乍一看，这似乎很奇怪。 为什么不只调用 SetGoalIndex 而不是通过播放机控制器进行这种奇怪的路由？ 原因是我们符合数据模型，UNET 使用该数据来使数据保持同步。若要防止作弊和抖动，UNET 要求每个对象都有一个有权更改同步变量的用户。 此外，只有启动会话) 用户 (的主机可以直接更改数据。 如果用户不是宿主但具有权限，则需要将 "command" 发送到将更改变量的主机。 默认情况下，主机拥有所有对象的权限，但生成的对象除外表示用户。 在本例中，此对象具有 playercontroller 脚本。 有一种方法可以为对象请求授权，然后进行更改，但我们选择利用这一事实：播放机控制器具有己方授权，并通过播放机控制器路由命令。

另一种方法是，当我们以我们的目标找到自己时，玩家需要告诉主机，主机会告诉所有其他人。

返回 LevelControl，查看 SetGoalIndex。 这里，我们要在 synclist (AtGoal) 中设置值的值。 请记住，在执行此操作时，我们处于主机的上下文中。 与命令相似，RPC 是指主机可以发出的，这会导致所有客户端运行一些代码。 这里我们称之为 "RpcCheckAllGoals"。 每个客户端将分别检查是否设置了所有三个 AtGoals，如果已设置，则启动火箭。

### <a name="enjoy-your-progress"></a>欣赏你的进度

在上一章中生成，我们将像以前一样启动会话。 当沉浸式耳机中的用户到达其路径上的 "门" 时，将显示一个工具提示，只显示 HoloLens 用户可以看到的工具提示。 HoloLens 用户负责将此线索传达给沉浸式耳机中的用户。 一旦每个虚拟形象在火山内的相应的棕色垫上火箭，就会启动空间。 场景将在60秒后重置，因此你可以重新执行此操作。

## <a name="see-also"></a>另请参阅

* [MR 输入 213：运动控制器](mixed-reality-213.md)