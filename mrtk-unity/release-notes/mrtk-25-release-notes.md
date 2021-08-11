---
title: MRTK 2.5 发行说明
description: MRTK 版本2.5 的发行说明
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，
ms.openlocfilehash: 7d3e158bc7e4b0125f264aa9abc8f369a6e825562266891b0528066d8b8b9b71
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198109"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Microsoft Mixed Reality Toolkit 2.5 发行说明

> [!IMPORTANT]
> 存在一个已知的编译器问题，它会影响使用 ARM64 为 Microsoft HoloLens 2 生成的应用程序。 此问题的解决方法是将 Visual Studio 2019 更新为16.8 或更高版本。 如果无法更新 Visual Studio，请导入 `com.microsoft.mixedreality.toolkit.tools` 包以应用解决方法。

## <a name="whats-new-in-254"></a>2.5.4 中的新增功能

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>使用 UPM 修复包含 Oculus 集成的 bug

使用 UPM 时，OculusXRSDKDeviceManagerProfile 在启动时始终将其 [prototyping 设置为 "无](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)"。 此版本将 Device Manager 配置为在启动时指向 prototyping 的工作集。

### <a name="fixes-an-issue-with-openxr-via-upm"></a>解决 OpenXR via UPM 的问题

修复了默认情况下，OpenXR 提供程序未添加到 link.xml 的问题，导致新项目在使用 OpenXR 和 MRTK 通过 Unity 的程序包管理器时无法在设备上运行。 升级的现有项目仍将需要手动添加。

## <a name="whats-new-in-253"></a>2.5.3 中的新增功能

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>修复了2.5.2 中引入的 Oculus 的回归

2.5.2 在 [集成 OCULUS SDK 时引入了生成问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)。 此版本恢复了该问题。

## <a name="whats-new-in-252"></a>2.5.2 中的新增功能

### <a name="add-support-for-openxr"></a>添加对 OpenXR 的支持

添加了对 Unity 的 OpenXR 预览版包和 Microsoft Mixed Reality OpenXR 包的初始支持。 有关详细信息，请参阅 [MRTK/XRSDK 入门页](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的论坛文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的文档](/windows/mixed-reality/develop/unity/openxr-getting-started) 。

> [!IMPORTANT]
> Unity 中的 OpenXR 仅在 Unity 2020.3 和更高版本上受支持。
> 它还仅支持 x64、ARM 和 ARM64 生成。

### <a name="boundary-visualization-errors-fixed"></a>已修复边界可视化错误

现在，边界可视化效果（如地面或墙壁）将正确配置，并根据边界配置文件在运行时可见。

### <a name="msbuild-for-unity-support"></a>MSBuild 支持 Unity

2.5.2 版本已删除对 unity 的 MSBuild 支持，以与[Unity 的新包指南](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)保持一致。

## <a name="whats-new-in-251"></a>2.5.1 的新增功能

### <a name="package-dependency-errors-fixed"></a>已修复包依赖关系错误

此版本修复了不正确的包间文件依赖关系 (ex：标准资产中的文件不再错误地引用 Foundation) 中的文件。 版本2.5.1 还在文本网格 Pro 上添加了显式依赖项。

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>已复制到资产/MRTK/着色器的标准资产包着色器

通过 UPM 安装标准资产包时，着色器将被复制到 "资产/MRTK/着色器" 文件夹中，以使其不再是不可变的。 这解决了在下一次加载项目时 (URP) 还原旧行为而更新的通用呈现管道的着色问题。

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>固定的传送光标粘滞到了手

此版本修复了 "传送目标" 游标可以坚持使用视觉对象的 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 。

## <a name="whats-new-in-250"></a>2.5.0 中的新增功能

### <a name="unity-package-manager-upm-support"></a>Unity 程序包管理器 (UPM) 支持

现在可以使用 Unity 程序包管理器管理混合现实 Toolkit。

![MRTK Foundation UPM 包](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> 导入 MRTK UPM 包需要执行一些手动步骤。 有关详细信息，请查看[混合现实 Toolkit 和 Unity 程序包管理器](../configuration/usingupm.md)。

### <a name="oculus-quest-xr-sdk-support"></a>Oculus 的 XR SDK 支持

MRTK 现在支持使用本机 XR SDK 管道运行 Oculus 寻找耳机和控制器。 [Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)还支持手动跟踪，这归功于[ERIC Provencher](https://twitter.com/prvncher)在 MRTK 上的工作！

有关如何使用新管道在 Oculus 寻找设备上部署设备的说明，请参阅 [Oculus 寻找设置指南](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>滚动对象集合

MRTK UX 组件已从实验功能升级，并为不同大小的布局3D 内容提供更大的自由度，并为未附加 colliders 的对象添加了支持。 此外还添加了用于禁用内容屏蔽的新选项，使原型更容易。

有关详细信息，请参阅 [滚动对象集合](../features/ux-building-blocks/scrolling-object-collection.md) 。

![滚动对象集合](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>传送指针动画、处理和声音改进

现在传送指针改进了动画和音频反馈。 此外，我们还改进了传送指针的处理，使其在从附近表面过渡到远离曲面时处理平滑。

### <a name="input-simulation-cheat-sheet"></a>输入模拟备忘单

HandInteractionExamples 场景现在提供了一个可配置的快捷方式，用于显示输入模拟的帮助页

![输入模拟备忘单](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>带有鼠标的输入模拟眼睛

用户现在可以使用鼠标来模拟眼睛跟踪。 查看 `Eye Simulation Mode` 输入模拟配置文件中的字段，并将其设置为 "鼠标"。 这将替换上一个 `Simulate Eye Position` 字段。

![眼睛眼睛鼠标](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>编辑器播放模式下的输入模拟运动控制器

用户现在可以模拟运动控制器，就像在编辑器播放模式中一样。 当前支持触发器、抓取和菜单按钮。

### <a name="conical-grab-pointer"></a>圆锥抓取指针

现在可以将获取指针配置为使用来自抓取点（而不是球体）的锥形来查询附近的对象。 这与默认 HoloLens 2 接口中的行为更加相似，后者使用圆锥查询附近的对象。 DefaultHoloLens2InputSystemProfile 也已调整为使用新的 `ConicalGrabPointer` 。

![圆锥抓取指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>TestUtilities 包

现在 (MixedReality 包。Toolkit。TestUtilities. 2.5.0. unitypackage) ，其中包含 TESTMODE 用于创建端到端测试的 PlayMode 和 MRTK 测试基础结构。 此基础结构对于 MRTK 团队本身非常有用，因此我们很高兴让使用者将测试覆盖率添加到其自己的项目中。

下面的代码演示如何创建一个测试局，在某个位置显示它，将其移到，然后将其移开。

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

有关如何使用这些 TestUtilities 编写测试的说明，请参阅有关 [编写测试](../contributing/unit-tests.md#writing-tests)的此部分。

有关使用此基础结构的现有测试的示例，请参阅 MRTK 的 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)。

### <a name="support-for-the-leap-motion-451-unity-modules"></a>支持 Leap 运动 4.5.1 Unity 模块

已添加对 Leap 运动 Unity 模块版本4.5.1 的支持，并已删除对4.4.0 资产的支持。 当前支持的 Leap 运动 Unity 模块的版本为4.5.0 和4.5.1。

初始 Leap 运动集成还有一个额外的步骤，有关详细信息，请参阅 [如何在 MRTK 中配置 Leap 运动手跟踪](../supported-devices/leap-motion-mrtk.md) 。

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>空间感知网格观察器更好地处理物料自定义

在此版本中， `Windows Mixed Reality Spatial Mesh Observer` 和 `Generic XR SDK Spatial Mesh Observer` 组件改进了视觉对象处理。 现在，当网格已由观察者更新时（以前，在配置文件中配置的 VisibleMaterial 重置为默认值）时，将保留物料。

这使开发人员可以更改网格材料，而不会意外覆盖更改。

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml 在 MixedRealityToolkit 文件夹中创建

随着 Unity 包管理器的 MRTK，MRTK 现在 `link.xml` 会将文件写入 `Assets/MixedRealityToolkit.Generated` 文件夹（如果没有）。 建议将此文件添加 (，并将 `link.xml.meta`) 添加到源代码管理中。 Link.xml 用于影响 Unity 链接器的 [托管代码去除](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 功能。

可在 [MRTK 和托管代码剥离](../updates-deployment/mrtk-and-managed-code-stripping.md) 一文中找到有关 MRTK link.xml 文件的详细信息。

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 +： MRTK 配置对话框不再尝试启用旧版 XR 支持

为了避免在使用 Unity 的 XR 平台时出现潜在的冲突，已从 MRTK 配置对话框中删除启用旧 XR 支持的选项。 如果需要，可以在 Unity Project 2019 中启用旧的 XR 支持，   >  **设置**  >
 **Player**  >  **XR 设置**  >  **虚拟现实支持**。

### <a name="reduction-in-initializeonload-overhead"></a>降低 InitializeOnLoad 开销

我们一直在努力减少在 InitializeOnLoad 处理程序中运行的工作量，这会使内部循环开发速度得到改进。 InitializeOnLoad 处理程序在脚本每次编译、进入播放模式之前以及在编辑器启动时运行。 现在，这些处理程序在极少的情况下运行，从而使一般的 Unity 响应能力得以改善。

在某些情况下，需要进行权衡：

- 请参阅 [Leap 动作手动跟踪配置](../supported-devices/leap-motion-mrtk.md) ，了解额外的集成步骤。
- 对于使用 ARFoundation 的用户，现已在入门步骤中执行了其他手动步骤。
  有关新步骤，请参阅 [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) 。
- 对于将使用[全息远程处理 HoloLens 2 上的旧版 XR 管道](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions)的用户，现在可以执行[手动步骤](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings)。

### <a name="bounds-control-graduated"></a>边界控制渐变

![边界控制](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[边界控制](../features/ux-building-blocks/bounds-control.md) 以实验性为依据，并附带一组新功能和大量 bug 修复。
下面列出了此更新的要点：

- 属性被拆分为多个配置，以便更轻松地设置边界控件
- 可以通过可编写脚本的对象共享配置
- 每个属性/可脚本属性均可配置运行时
- 不再在属性更改时重新创建边界控制远程测试机组
- 翻译句柄支持
- 通过约束管理器的完全约束支持
- 池中弹性系统集成 (试验性) 

现在已弃用旧的边界框，可以 [使用迁移工具](../features/tools/migration-window.md) 或 [边界框检查器](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)升级使用范围框的现有游戏对象。

### <a name="constraint-manager-component"></a>约束管理器组件

现在，约束控件和对象操控器都可以通过新的 [约束管理器组件](../features/ux-building-blocks/constraint-manager.md)来使用约束。 这两个组件将为每个默认创建一个约束管理器，并自动处理任何附加的约束。

此外，自动行为约束管理器还附带了 "手动" 模式，使用户能够决定应处理哪一个约束。
出于此原因，我们在属性检查器中显示约束的方式已更改。

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

应用于组件的约束现在显示为 "约束管理器" 组件中的一个列表，而使用约束管理器的组件 (" [边界控制](../features/ux-building-blocks/bounds-control.md#constraint-system) " 或 " [对象操控](../features/ux-building-blocks/object-manipulator.md#constraint-manager) 器") 现在将显示选定的约束管理器和模式 (自动或手动) 。
有关详细信息，请参阅文档中的 [约束管理器](../features/ux-building-blocks/constraint-manager.md) 部分。

### <a name="hololens-2-button-material-update"></a>HoloLens 2 按钮材料更新

更新了 HoloLens 2 按钮的前固定架材料，以删除 MRC 中的黑色颜色。

![HoloLens 2 按钮材料更新](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>说明面板更新，可移动示例场景

更新了说明面板。  (prefab) "新设计" 提供了一个 grabbable 顶栏，用户可在其中调整/移动整个场景。

![说明面板更新](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>空间网格可视化-轻按的脉冲

更新了用于匹配 HoloLens 2 shell 行为的空间网格的脉冲着色器示例。

![无线点击脉冲](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>弹性系统 (试验性) 

![弹性 System2](../features/images/elastics/Elastics_Main.gif)

MRTK 现在附带了一个 [弹性模拟系统](../features/experimental/elastic-system.md) ，该系统包含各种可扩展和灵活的子类，为四维四元数弹簧、三维量弹簧和简单线性弹簧系统提供绑定。

目前，支持 [池中弹性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的以下 MRTK 组件可以利用池中弹性功能：

- [边界控制](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [对象操控器](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>游戏杆 (试验) 

可以控制大目标对象的游戏杆界面的示例。

![操纵杆](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a> (试验) 颜色选取器

一个试验性控件，使您可以轻松地在运行时更改任何对象上的材料颜色。

![颜色选取器控件的三个不同方法](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![颜色选取器控件的四种不同方法](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>中断性变更

### <a name="assembly-definition-files-changes"></a>程序集定义文件更改

某些 asmdef 文件已更改，现在仅支持 Unity 2018.4.13 f1 或更高版本。 当在 Unity 的早期版本中更新到 MRTK 2.5 时，将显示编译错误。 若要解决此情况，可以转到 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` "项目" 窗口，并删除检查器中缺少的引用。 用和重复这些 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` 步骤 `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。 请注意，必须使用原始 (替换这三个 asmdef 文件（即，升级到 Unity 2019 时未修改的) ）来还原更改。

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

此接口已更新为具有新函数：

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

如果你的自定义指针转存进程不是子类的子类，则需要实现此新函数。 有关添加此问题的原因的更多背景信息，请参阅 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 。 这样做是为了确保将指针首选项直接传递到转存进程，而不是根据是否存在采用 IPointerPreferences 的构造函数隐式完成此操作。

### <a name="rest--device-portal-api"></a>Rest/设备门户 API

`UseSSL`静态属性已从移动 `Rest` 到 `DevicePortal` 。

如果你之前执行此操作 .。。

```csharp
Rest.UseSSL = true
```

立即执行此操作 .。。

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

如果以前使用 MRTK 的 NuGet 分发应用程序，则该文件已 `link.xml` 从基础包中删除。 若要还原代码保存规则，请在 Unity 中打开项目一次，将在中创建一个默认 `link.xml` 文件 `Assets/MixedRealityToolkit.Generated` 。 建议将此文件 (，并 `link.xml.meta` 将) 添加到源代码管理中。

### <a name="transform-constraint-changes"></a>转换约束更改

TargetTransform 属性已标记为过时，因为它不被约束系统使用。 约束逻辑基于传递到 Initialize 和 Apply 方法中的转换。 依赖于此属性的派生用户约束可以通过存储约束组件的转换来实现相同的行为，从而在其实现中缓存 TargetTransform。

存储的初始世界的 `worldPoseOnManipulationStart` 数据类型已从 MixedRealityPose 更改为 MixedRealityTransform，其中包括操作对象的本地缩放值。 进行此更改后，无需再单独缓存任何初始缩放值。

### <a name="new-property-in-imixedrealitydictationsystem"></a>IMixedRealityDictationSystem 中的新属性

新属性已 `AudioClip` 添加到 IMixedRealityDictationSystem 接口。 `AudioClip`使用属性可以访问与当前听写会话关联的音频剪辑。 用户必须在实现接口的脚本中实现该属性。

### <a name="service-facades-turn-down"></a>服务外观关闭

2.5 中的服务外观正在关闭。 此功能最初是通过创建) MRTK 的每个服务的虚假的场景 Gameobject 来使配置 MRTK 配置文件的配置变得更简单 (。 在长时间运行的情况下，我们希望避免创建虚假的游戏内对象，并尝试使它们保持同步 (因为数据同步和 "真实" 问题是难以缩放和) 正确的。

在2.5 中，服务外观处理程序会保持不变，以确保项目升级顺利进行-服务外观处理程序将删除项目中存在的任何外观，以确保在2.5 中打开的场景自动修复。

未来版本中将删除与服务外观功能关联的剩余代码。

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>向输入模拟服务添加运动控制器

现在，运动控制器模拟以编辑器播放模式提供，沿现有的手动模拟。 若要启用此更改，许多当前函数/字段/属性现已标记为过时， `InputSimulationService.cs` 并 `MixedRealityInputSimulationProfile.cs` 获得最重要的更改。 相关代码的逻辑和行为很大程度上保持不变，大多数过时的函数等都与将对 "手型" 的引用替换为更通用的术语 "controller" (例如从 `DefaultHandSimulationMode` 到 `DefaultControllerSimulationMode`) 。 除了获取新名称外，还会更新某些新函数的返回类型，使其与名称/行为更改相匹配 (例如， `GetControllerDevice` 基于原始源的 `GetHandDevice` 返回 `BaseController` 而不是 `SimulatedHand`) 。

`IInputSimulationService` 现在具有新的属性 `MotionControllerDataLeft` 和 `MotionControllerDataRight` 。 `MixedRealityInputSimulationProfile` 现在包含用于特定运动控制器按钮的键盘映射的新字段。

## <a name="known-issues"></a>已知问题

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>关闭时，CameraCache 可能会创建新的照相机

在某些情况下 (例如，在 Unity 编辑器中使用 LeapMotion 提供程序时) ，CameraCache 可以在关闭时重新创建 MainCamera。 有关详细信息，请参阅 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>通过 Unity 导入示例时的 system.io.filenotfoundexception 程序包管理器

根据项目路径的长度，通过 unity 导入示例程序包管理器可能会在 Unity 控制台中生成 system.io.filenotfoundexception 消息。 导致这种情况的原因是，"丢失" 文件的路径超过了 MAX_PATH (256) 的字符。 若要解决此问题，请缩短项目路径的长度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定 spatializer。 应用程序将不支持空间音效

如果未配置音频 spatializer，将显示 "未指定任何 spatializer" 警告。 如果未安装 XR 包，则可能会发生这种情况，因为 Unity 包含这些包中的 spatializers。

若要解决此问题，请确保：

- **窗口**  > **程序包管理器** 已安装一个或多个 XR 包
- **混合现实Toolkit**  > **实用工具**  > **配置 Unity Project，** 并针对音频空间 **化程序进行选择**

  ![选择"音频空间化程序"](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException：对象引用未设置为实例化 (SceneTransitionService.Ini实例) 

在某些情况下，打开 `EyeTrackingDemo-00-RootScene` 可能会导致 SceneTransitionService 类的 Initialize 方法中出现 NullReferenceException。
此错误是由于未设置场景转换服务的配置文件。 若要解决此问题，请使用以下步骤：

- 导航到 `MixedRealityToolkit` 层次结构中的 对象
- 在"检查器"窗口中，选择 `Extensions`
- 如果未展开，则展开 `Scene Transition Service`
- 将 的值设置为 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile**

![修复场景转换](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

在面向独立平台 时，当前存在将 [Oculus XR 插件与 一起使用的已知问题](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)。 有关更新，请查看 Oculus bug 跟踪器/论坛/发行说明。

此 bug 由以下 3 个错误集表示：

![Oculus XR 插件错误](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

较新版本的 TextMeshPro (1.5.0+ 或 2.1.1+) 存在已知问题，其中下拉列表的默认字号和粗体字体字符间距已更改。

![TMP 映像](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

可以通过降级到早期版本的 TextMeshPro 来这样做。 有关详细信息 [，#8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 问题说明。
