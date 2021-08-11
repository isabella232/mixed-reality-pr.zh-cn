---
title: 更新适用于 Windows Mixed Reality 的 2D UWP 应用
description: 本文概述了如何更新现有的2d 通用 Windows 平台应用，以便在 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2d 应用，UWP，平面应用，HoloLens，沉浸式头戴式耳机，应用模型，后退按钮，应用程序栏，dpi，分辨率，缩放，移植，HoloLens 第一代，HoloLens 2，混合现实耳机，windows mixed reality 耳机，迁移，Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195976"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>更新适用于 Windows Mixed Reality 的 2D UWP 应用

Windows Mixed Reality 使你的用户能够像在物理和数字世界中那样直接查看全息影像。 它的核心是将沉浸式耳机配件附加到 Windows 10 设备的 HoloLens 和桌面 pc。 可以在应用商店中几乎所有通用 Windows 平台 (UWP) 应用作为2d 应用运行。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>为混合现实创建 2D UWP 应用

向混合现实耳机引入2D 应用程序的第一步是在桌面监视器上将应用作为标准2D 应用运行。

### <a name="building-a-new-2d-uwp-app"></a>生成新的 2D UWP 应用

若要为混合现实构建新的2d 应用程序，请 (UWP) 应用程序构建标准的2d 通用 Windows 平台。 对于该应用程序，无需进行其他应用程序更改，就能在混合现实中以石板的形式运行。

若要开始生成二维 UWP 应用，请参阅 [创建第一个应用一](/windows/uwp/get-started/your-first-app) 文。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>将现有2D 应用商店应用引入 UWP

如果在存储中已有 2d Windows 应用，请确保它以 (UWP) Windows 10 通用 Windows 平台为目标。 下面是你目前可以使用应用商店应用的所有潜在起点：
<br>

|  起点  |  AppX 清单平台目标  |  如何实现此通用？ | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 应用程序清单 |  [迁移到 WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 通用  |  8.1 AppX 清单，不包括平台目标  |  [将应用迁移到通用 Windows 平台](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows商店8  |  8个不包括平台目标的 AppX 清单  |  [将应用迁移到通用 Windows 平台](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows应用商店8.1 通用  |  8.1 AppX 清单，不包括平台目标  |  [将应用迁移到通用 Windows 平台](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

如果当前在电脑上构建为 Win32 应用的 2d Unity 应用 **，Mac & Linux 独立** 生成目标，请切换到混合现实 **通用 Windows 平台** 生成目标。

我们将讨论如何使用 Windows 专门限制应用程序 HoloLens。[下面](#publish-and-maintain-your-universal-app)的全息设备系列。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>在 Windows Mixed Reality 沉浸式耳机中运行2d 应用

如果已将2D 应用部署到桌面计算机并在监视器上尝试使用，则可以在沉浸式桌面耳机上试用！

只需在混合现实耳机中中转到 "开始"菜单，即可从此处启动应用。 桌面 shell 和全息 shell 共享同一组 UWP 应用，因此，从 Visual Studio 部署后，应用应该已经存在。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>面向沉浸式耳机和 HoloLens

恭喜！ 应用现在正在使用通用 Windows 平台 (UWP) 的 Windows 10。

现在，你的应用程序能够在当前的 Windows 设备上运行，例如桌面、移动、Xbox、Windows Mixed Reality 沉浸式耳机、HoloLens，以及未来的 Windows 设备。 但是，若要实际定位所有这些设备，需要确保应用面向 Windows。 通用设备系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>将设备系列更改为 Windows。全局

现在，让我们跳转到 AppX 清单，确保 Windows 10 UWP 应用可以在 HoloLens 上运行：
* 用 **Visual Studio** 打开应用的解决方案文件，并导航到应用程序包清单
* 右键单击解决方案中的 **appxmanifest.xml** 文件，然后单击 "**查看代码**"<br>
  ![解决方案资源管理器中的 appxmanifest.xml](images/openappxmanifest-500px.png)<br>
* 确保 Windows 目标平台。 "依赖关系" 部分中的通用
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 把!

如果不使用 Visual Studio 开发环境，则可以在所选的文本编辑器中打开 **AppXManifest.xml** ，以确保以 Windows 为目标 **。通用** *y*。

### <a name="run-in-the-hololens-emulator"></a>在 HoloLens 中运行 Emulator

现在，UWP 应用面向 "Windows。通用 "，让我们生成您的应用程序，并在[HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md)中运行该应用程序。
* 请确保[已安装 HoloLens Emulator](../install-the-tools.md)。
* 在 Visual Studio 中，选择应用的 **x86** 生成配置

  ![Visual Studio 中的 x86 生成配置](../platform-capabilities-and-apis/images/x86setting.png)<br>
* 在部署目标下拉菜单中选择“HoloLens 仿真器” 

  ![部署目标列表中的 HoloLens Emulator](images/deployemulator-500px.png)<br>
* 选择 " **调试" > "开始调试** " 以部署应用并启动调试。
* 模拟器将启动并运行您的应用程序。
* 使用键盘、鼠标和 Xbox 控制器，将您的应用程序置于世界中以启动它。

  ![使用 UWP 示例加载 HoloLens Emulator](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>后续步骤

此时，可能会出现以下两种情况之一：
1. 应用将显示其初始，并在将其置于 Emulator 中后开始运行！ 太棒了！
2. 或者，在看到2D 全息图的加载动画后，加载将停止，您将在其初始屏幕上看到您的应用程序。 这意味着出现了问题，并将进行更多调查，以了解如何在混合现实中实现应用程序的生活。

需要进行调试，以获取停止 UWP 应用从 HoloLens 开始的可能问题的根源。

### <a name="running-your-uwp-app-in-the-debugger"></a>在调试器中运行 UWP 应用

这些步骤将指导你使用 Visual Studio 调试程序调试 UWP 应用。
* 如果尚未这样做，请在 Visual Studio 中打开解决方案。 将目标更改为 " **HoloLens Emulator** "，并将 "生成配置" 更改为 " **x86**"。
* 选择 " **调试" > "开始调试** " 以部署应用并启动调试。
* 在世界上，用鼠标、键盘或 Xbox 控制器放置应用程序。
* Visual Studio 现在应在应用代码中的某处中断。
  - 如果应用由于未处理的错误而不会立即崩溃或进入调试器，请完成应用的核心功能测试，以确保一切正常运行且正常运行。 你可能会看到如下所示的错误， (正在处理) 的内部异常。 若要确保不会错过影响应用体验的内部错误，请运行自动测试和单元测试，以确保一切都按预期方式运行。

![使用显示系统异常的 UWP 示例加载了 HoloLens Emulator](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新用户界面

现在，UWP 应用运行在沉浸式耳机上，并 HoloLens 为2d 全息图，接下来我们要确保它看起来很漂亮。 以下是一些需要考虑的事项：
* Windows Mixed Reality 将按固定分辨率和 DPI （等同于853x480 有效像素）运行所有2d 应用。 考虑设计是否需要优化此规模，并查看下面的设计指南，以改善 HoloLens 和沉浸式耳机上的体验。
* Windows Mixed Reality[不支持](../../design/app-model.md)2d 动态磁贴。 如果你的核心功能显示了有关动态磁贴的信息，请考虑将该信息移回你的应用程序或浏览 [3d 应用程序启动器](../../distribute/3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 应用视图分辨率和缩放比例

![从响应式设计](images/scale-500px.png)

Windows 10 将所有视觉对象设计从真实屏幕像素变为 **有效像素**。 这意味着，开发人员会按照 Windows 10 的用户界面准则为有效像素设计用户界面，Windows 缩放可确保这些有效像素的大小适用于跨设备、分辨率、DPI 等的可用性。 有关详细信息，请参阅 MSDN 上的这一 [精彩阅读](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) 和此 [生成演示](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx) 。

即使有独特的功能可以将应用放在世界上的距离范围内，也建议使用类似于电视的观看距离，以获得最佳的可读性，并与注视/手势交互。 因此，混合现实中的虚拟石板会在以下位置显示平面 UWP 视图：

**1280x720，150% DPI** (853x480 有效像素) 

此分辨率具有几个优点：
* 这一有效的像素布局将与 tablet 或小型桌面具有相同的信息密度。
* 它匹配 Xbox One 上运行的 UWP 应用的固定 DPI 和有效像素，实现跨设备的无缝体验。
* 当在世界各地的应用范围内扩展时，此大小看起来很好。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 应用视图界面设计最佳做法

**执行：**
* 对于样式Windows 10字号 (按钮) [HIG，](https://dev.windows.com/design)请遵循人机界面指南。 HoloLens将执行相关工作，确保应用具有兼容的应用模式、可读文本大小和适当的命中目标大小。
* 确保 UI 遵循响应式设计[](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)最佳做法，HoloLens独特的分辨率和 DPI。
* 使用来自"浅色"的颜色主题Windows。

**不要：**
* 在混合现实中过于彻底地更改 UI，以确保用户在头戴显示设备中和在头戴显示设备外拥有熟悉的体验。

### <a name="understand-the-app-model"></a>了解应用模型

混合 [现实的应用](../../design/app-model.md) 模型旨在使用混合现实主页，许多应用都位于其中。 这可视为桌面的混合现实等效项，一次运行多个 2D 应用。 这影响应用生命周期、磁贴以及应用的其他关键功能。

### <a name="app-bar-and-back-button"></a>应用栏和后退按钮

2D 视图使用内容上方的应用栏进行修饰。 应用栏有两个特定于应用的个性化设置点：

**标题** ： *显示与* 应用实例关联的磁贴的显示名称

**后退按钮：** 按下时引发 *[BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* 事件。 后退按钮可见性由 *[SystemNavigationManager.AppViewBackButtonVisibility 控制](/uwp/api/Windows.UI.Core.SystemNavigationManager)*。

![2D 应用视图中的应用栏 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 应用视图中的应用栏 UI*

### <a name="test-your-2d-apps-design"></a>测试 2D 应用的设计

请务必测试应用，确保文本可读、按钮是可定向的，并且整个应用看起来正确。 可以在[分辨率设置为](../platform-capabilities-and-apis/testing-your-app-on-hololens.md)1280x720 % 的桌面头戴显示设备、HoloLens、仿真器或触摸设备上 @150 进行测试。

## <a name="new-input-possibilities"></a>新的输入可能性

HoloLens高级深度传感器来查看世界并查看用户。 这将启用高级手势，例如["开"和](../../design/system-gesture.md#bloom)["空敲击"。](../../design/gaze-and-commit.md#composite-gestures) 功能强大的麦克风还支持 [语音体验](../../design/voice-input.md)。

使用桌面头戴显示设备，用户可以使用运动控制器指向应用并采取措施。 他们还可使用游戏板，将对象作为凝视目标。

Windows UWP 应用处理所有这些复杂性，将凝视、手势、语音和[](../../design/gaze-and-commit.md)运动控制器输入转换为抽象掉输入机制的指针事件。 [](/windows/uwp/design/input/handle-pointer-input#pointer_events) 例如，用户可能已用手进行无线点击或拉取了运动控制器上的"选择"触发器，但 2D 应用程序不需要知道输入来自何处 - 他们只需看到 2D 触控按下，就像在触摸屏上一样。

以下是在将 UWP 应用引入应用时，应了解用于输入的HoloLens：
* [凝](../../design/gaze-and-commit.md) 视会变为悬停事件，这些事件可能会意外触发菜单、浮出控件或其他用户界面元素，只需在应用周围四处移动，就会弹出。
* 凝视与鼠标输入的精确性不一样。 将适当大小的命中目标用于HoloLens，类似于触摸友好的移动应用程序。 靠近应用边缘的小元素特别难以交互。
* 用户必须将输入模式从滚动切换为拖动到双指平移。 如果应用专为触摸输入设计，请考虑确保没有主要功能锁定在双指平移后面。 如果是这样，请考虑使用备用输入机制，例如可以启动双指平移的按钮。 例如，地图应用可以使用双指平移进行缩放，但具有加号、减号和旋转按钮，以通过单击来模拟相同的缩放交互。

[语音输入](../../design/voice-input.md) 是混合现实体验的关键部分。 使用头戴显示设备时，我们Windows 10所有Cortana语音 API。

## <a name="publish-and-maintain-your-universal-app"></a>发布和维护通用应用

应用启动并运行后，打包应用以[将其提交到 Microsoft Store。](../../distribute/submitting-an-app-to-the-microsoft-store.md)

## <a name="see-also"></a>另请参阅
* [应用模型](../../design/app-model.md)
* [头部凝视并提交](../../design/gaze-and-commit.md)
* [运动控制器](../../design/motion-controllers.md)
* [语音输入](../../design/voice-input.md)
* [将应用提交到 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)