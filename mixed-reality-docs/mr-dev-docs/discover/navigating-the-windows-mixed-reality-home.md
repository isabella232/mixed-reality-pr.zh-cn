---
title: 导航 Windows Mixed Reality 主页
description: 了解如何在设备Windows Mixed Reality头戴显示设备HoloLens Windows Mixed Reality导航。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell， os， 平台， 房屋， 家庭， 环境， 开始菜单， 主菜单， 引脚， 应用， 启动应用， 放置应用， 远程端口， 移动， 导航， 混合现实头戴显示设备， 虚拟现实头戴显示设备， 什么是虚拟现实
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190248"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>导航 Windows Mixed Reality 主页

就像Windows电脑体验从桌面开始一样，Windows Mixed Reality从家庭开始。 该Windows Mixed Reality使用我们固有的能力来了解和导航 3D 位置。 借助HoloLens，你的家庭是物理空间，但使用沉浸式头戴显示设备时，你的家庭是一个虚拟位置。

在主页中，你将使用"开始"菜单打开和放置应用和内容。 可以同时使用多个应用，为家庭填充混合现实内容和多任务。 即使重启设备，你放在家中的东西也一直存在。

## <a name="start-menu"></a>“开始”菜单

![菜单上的"开始Microsoft HoloLens](images/start-500px.png)

该"开始"菜单包括：
* 系统信息 (网络状态、电池百分比、当前时间和音量) 
* Cortana (沉浸式头戴显示设备（"开始"磁贴）;"在 HoloLens 上，位于"开始") 
* 固定应用
* "所有应用"按钮 (加号) 
* 用于混合现实捕获 [的照片和视频按钮](/hololens/holographic-photos-and-videos)

选择加号或减号按钮，在固定应用和"所有应用"视图之间切换。 若要在"开始"菜单打开HoloLens，请使用"布满"手势。 在沉浸式头戴显示设备上，Windows控制器上的按钮。

## <a name="launching-apps"></a>启动应用

若要启动应用，请在"启动"中选择它。 应用"开始"菜单消失，应用将在放置模式下打开，作为 2D 窗口或[3D 模型](../distribute/implementing-3d-app-launchers.md)。

若要运行应用，需要将该应用放在主页中：
1. 使用 [凝视](../design/gaze-and-commit.md) 或控制器将应用定位到需要的位置。 它会自动调整 (大小以及位置) 以符合放置空间。
2. 在沉浸式头戴显示设备 (HoloLens) 或"选择"按钮 (应用) 。 若要取消并返回"开始"菜单，请使用"打开手势"或"Windows按钮。

[为桌面、](../develop/porting-apps/building-2d-apps.md)移动或 Xbox 创建的 2D 应用可以修改为使用 [HolographicSpace API](/uwp/api/Windows.Graphics.Holographic.HolographicSpace)作为混合现实沉浸式应用运行。 沉浸式应用将用户带出家庭，进入沉浸式体验。 用户可以使用布满手势 (HoloLens) 或按其控制器上的Windows按钮 (沉浸式头戴显示设备) 。

应用也可通过应用到应用 API 或应用Cortana。

![Windows Mixed Reality 主页中的应用](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移动和调整应用

选择 **应用** 栏上的"调整"以显示移动、缩放和旋转混合现实内容的控件。 完成后，选择"完成 **"。**

![调整模式下的存储板 (蓝色帧) 。 请注意，顶部 (栏) 已更改为包含"完成"和"删除"按钮。](images/adjust-500px.png)

不同的应用可能在应用栏上具有其他选项。 例如，Microsoft Edge"*滚动**"、"拖动*"和"*缩放"* 选项。 

![在 HoloLens 上运行的 2D 应用的应用栏](images/holobar-500px.png)

" **后退** "按钮导航回应用中以前查看的屏幕。 当你到达应用中显示的体验的开头时，它将停止，并且不会导航到其他应用。

## <a name="getting-around-your-home"></a>四处看看家

使用 **HoloLens，** 可以移动物理空间，以在家庭周围移动。

使用 **沉浸式头** 戴显示设备，可以在播放空间中启动并四处移动，以在虚拟世界中的类似区域中移动。 若要跨较长的距离移动，请使用控制器上的滚动块进行几乎"演练"，或者可以使用远程传输立即跳到更长的距离。

![远程传送Windows Mixed Reality主页](images/teleportation-500px.png)

**若要进行远程传送，**
1. 启动远程端口。
   * 使用 [运动控制器](../design/motion-controllers.md)：向前按滚动块，并按住该位置。
   * 使用 Xbox 控制器：向前按左滚动块，并按住该位置。
   * 使用鼠标：按住鼠标右键 (鼠标按钮图标，然后使用滚轮旋转在远程移动时要) 。
2. 将视区放在要远程传送的位置。
   * 使用 [运动控制器](../design/motion-controllers.md)：将 (向前滚动块的控制器) 移动旋转。
   * 使用 Xbox 控制器：使用 [凝视](../design/gaze-and-commit.md) 来移动视点。
   * 使用鼠标：移动鼠标以移动顶点。
3. 释放按钮以将视区置于远程端口。

**几乎"walk："**
* 使用 [运动控制器](../design/motion-controllers.md)：单击滚动块并按住，然后按你想要"步长"的方向移动滚动块。
* 使用 Xbox 控制器：单击左 thumbstick 并按住，然后按你想要"步长"的方向移动滚动块。

## <a name="immersive-headset-input-support"></a>沉浸式头戴显示设备输入支持

[Windows Mixed Reality沉浸式头](immersive-headset-hardware-details.md)戴显示设备支持多种输入类型，以在Windows Mixed Reality导航。 HoloLens不支持用于导航的附件输入，因为你以物理方式四处浏览并查看环境。 但是，HoloLens[支持用于](hardware-accessories.md)与应用交互的输入。

### <a name="motion-controllers"></a>运动控制器

最佳Windows Mixed Reality体验是使用Windows Mixed Reality运动控制器，这些控制器仅支持使用[](../design/motion-controllers.md)头戴显示设备中的传感器进行六度自由跟踪，无需外部相机或标记！

即将推出导航命令。

### <a name="gamepad"></a>游戏板
* **左滚动块：**
  * 按并按住左滚动条，以启动 [远程端口](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 。
  * 点击向左、向右或后退的指纹，以较小的增量向左、向右或后退。
  * 单击左 thumbstick 并按住，然后按你想要几乎"步进" [的方向移动滚动块。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 点击 **右滚动条** 向左或向右旋转 45 度的方向。
* 按 **"A"** 按钮将选择并充当"敲 [击手势](../design/gaze-and-commit.md#composite-gestures) "。
* 按 **"指南**"按钮可打开 ["开始"菜单，其](navigating-the-windows-mixed-reality-home.md#start-menu)行为与布满 [手势](../design/system-gesture.md#bloom)类似。
* 通过 **按左侧和** 右侧触发器，可以放大和缩小要与家庭交互的 2D 桌面应用。

### <a name="keyboard-and-mouse"></a>键盘和鼠标

**注意：** 使用 **Windows键 + Y** 在控制电脑的桌面和家庭Windows Mixed Reality鼠标。

在Windows Mixed Reality中：
* 按 **左键单击** 鼠标按钮将选择并充当点击 [手势](../design/gaze-and-commit.md#composite-gestures) 。
* 按住 **右键单击** 鼠标按钮会打开 [远程传送](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 转网。
* 按 **Windows** 键会打开"开始"[菜单](navigating-the-windows-mixed-reality-home.md#start-menu)，其行为与"打开手势 ["](../design/system-gesture.md#bloom)类似。
* 在 2D 桌面应用中浏览时，可以左键单击以选择，右键单击以打开上下文菜单，然后使用滚动滚轮滚动 (就像在电脑桌面上滚动) 。 [](../design/gaze-and-commit.md)

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana)个人助理，Windows Mixed Reality电脑和手机上一样。 HoloLens内置麦克风，但沉浸式头戴显示设备可能需要额外的硬件。 使用Cortana打开应用、重启设备、联机查找内容等。 开发人员还可以选择[将Cortana](https://dev.windows.com/cortana)集成到其体验中。

也可使用语音命令来离开家。 例如，指向使用凝视 (控制器的按钮，[](../design/gaze-and-commit.md)具体取决于设备) 并说"选择"。 其他语音命令包括"去主页"、"更大"、"较小"、"关闭"和"正面朝我"。

## <a name="store-settings-and-system-apps"></a>应用商店设置和系统应用

Windows Mixed Reality多个内置应用，例如：
* **Microsoft Store** 获取应用和游戏
* **反馈中心** 提交有关系统和系统应用的反馈
* **设置** 配置系统设置 ([包括网络和](/hololens/hololens-network)系统更新) 
* **Microsoft Edge** 浏览网站
* **要查看** 和共享照片和视频的照片
* **校准** (HoloLens) 调整当前HoloLens用户体验
* **了解如何使用****(HoloLens) 了解混合现实 (** 头戴显示设备) 手势
* **3D 查看器** 混合现实内容修饰世界
* **混合现实门户 (** 桌面) ，用于设置和管理沉浸式头戴显示设备，以及流式传输头戴显示设备中的视图实时预览，供其他人查看。
* **用于观看** 360 视频和最新电影和电视的电影和电视
* **Cortana** 虚拟助理的所有需求
* **桌面** (沉浸式头戴显示设备) 在沉浸式头戴显示设备中查看桌面监视器
* **文件资源管理器** 访问设备上的文件和文件夹

## <a name="see-also"></a>另请参阅
* [应用视图](../design/app-views.md)
* [运动控制器](../design/motion-controllers.md)
* [硬件配件](hardware-accessories.md)
* [HoloLens 的环境注意事项](/hololens/hololens-environment-considerations)
* [实现 3D 应用启动器](../distribute/implementing-3d-app-launchers.md)
* [创建 3D 模型以在Windows Mixed Reality使用](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)