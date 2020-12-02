---
ms.openlocfilehash: 487118403c2a8af1a6b54bc9aa9245fbe9d0568a
ms.sourcegitcommit: bec6029b2780c54cc04a45ef7ae5df3f5b4727c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477534"
---
# <a name="project-settings"></a>[项目设置](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. 查看上面列出的常见移植步骤

查看上面列出的常见步骤，确保正确设置开发环境。 在步骤 #3 中，如果使用的是 Visual Studio，则应选择 " **使用 Unity 的游戏开发** " 工作负荷。 由于将在下一步中安装较新版本的 Unity，因此可以取消选中 "Unity 编辑器可选" 组件。

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. 升级到具有 Windows MR 支持的 Unity 的最新公共版本
1. 下载最新建议的具有混合现实支持 [的 Unity 公共内部版本](../../install-the-tools.md) 。
2. 在开始之前保存项目的副本
3. 如果你的项目是基于早期版本的 Unity 生成的，请查看 Unity 上提供的 [文档](https://docs.unity3d.com/Manual/UpgradeGuides.html) 。
4. 按照 Unity 站点上的 [说明](https://docs.unity3d.com/Manual/APIUpdater.html) 使用其自动 API 更新程序
5. 检查并查看你是否需要进行其他更改以使你的项目运行，并处理剩余的错误和警告。 

> [!Note] 
> 如果你有依赖的中间件，请检查你是否正在使用最新版本， () 下面的步骤3中的更多详细信息。

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. 将中间件升级到最新版本

对于任何 Unity 更新，都有可能需要更新游戏或应用程序所依赖的一个或多个中间件包。 此外，最新的中间件是最新的，最新的中间件会在整个移植过程中增加成功的可能性。

### <a name="4-target-your-application-to-run-on-win32"></a>4. 将应用程序定位到在 Win32 上运行

从 Unity 应用程序内部：

* 导航到 "文件-> 生成设置"
* 选择 "PC、Mac、Linux 独立版"
* 将目标平台设置为 "Windows"
* 将体系结构设置为 "x86" 选择 "切换平台"

> [!NOTE] 
> 如果你的应用程序在特定于设备的服务上有任何依赖关系，例如，从流中进行匹配，则需要在此步骤中禁用它们。 你可以挂钩到 Windows 稍后提供的等效服务。

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. 设置 Windows Mixed Reality 硬件
1. 查看[沉浸式耳机安装程序](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)中的步骤
2. 了解如何 [使用 Windows Mixed reality 模拟器](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 并 [导航 windows mixed reality 主页](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. 将应用程序设定为在 Windows Mixed Reality 上运行
1. 首先，必须将特定于特定的 VR SDK 的任何其他库支持删除或有条件地编译掉。 这些资产经常以与其他 VR Sdk （如 Windows Mixed Reality）不兼容的方式更改项目的设置和属性。
    * 例如，如果你的项目引用 SteamVR SDK，则需要将你的项目更新为，以改用支持 Windows Mixed Reality 和 SteamVR 的 Unity 公共 VR Api。
    * 即将推出其他用于有条件地排除其他 VR Sdk 的特定步骤。
2. 在 Unity 项目中， [面向 Windows 10 SDK](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. 对于每个场景， [设置照相机](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. 使用舞台将内容放到地面上

您可以在各种 [经验](../../../design/coordinate-systems.md)范围内构建混合现实体验。

如果要移植 **固定规模的体验**，必须确保将 Unity 设置为 **静止** 跟踪空间类型：

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上述代码将设置 Unity 的世界坐标系统，以跟踪 [固定的引用框架](../../../design/coordinate-systems.md#spatial-coordinate-systems)。 在静止跟踪模式下，在应用程序启动时，位于该编辑器中的内容仅在照相机默认位置的前面 ("向前" 为-Z) 出现在用户的前面。 若要 recenter 用户的固定来源，可以调用 Unity 的 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法。

如果迁移的是 **大规模体验** 或 **房间规模体验**，将会相对于地面放置内容。 使用 **[空间阶段](../../../design/coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。 对于这些体验，必须确保将 Unity 设置为 **RoomScale** 跟踪空间类型。 尽管 RoomScale 是默认值，但你需要对其进行显式设置，并确保返回 true，以便捕获用户将其计算机从其校准的房间离开的情况：

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。 位于 (0，0，0) 的原点将是用户在房间设置期间考验的特定位置，并以-Z 表示在安装过程中所面临的正向方向。

在脚本代码中，您可以对 UnityEngine 调用 TryGetGeometry 方法来获取边界多边形，并指定 "TrackedArea" 的边界类型。 如果用户定义了边界 (你获取了) 的顶点列表，则可以安全地向用户提供一个 **会议室规模的体验** ，用户可在其中浏览你创建的场景。

当用户接近边界时，系统将自动渲染边界。 您的应用程序不需要使用此多边形来呈现边界本身。

有关详细信息，请参阅 [Unity 页中的坐标系统](../../unity/coordinate-systems-in-unity.md) 。

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

结果示例：

![结果示例](../../porting-apps/images/largestrectangle-400px.jpg)

算法基于 Daniel Smilkov：[多边形中的最大矩形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)的博客

### <a name="8-work-through-your-input-model"></a>8. 通过输入模型工作

每个面向现有 HMD 的游戏或应用程序都将具有一组可处理的输入，其所需的输入类型和体验所需的特定 Api 以及用于获取这些输入的特定 Api。 我们已经投入了大量努力，尽可能简单直接地利用 Windows Mixed Reality 中提供的输入。

有关 Windows Mixed Reality 如何公开输入的详细信息以及如何映射到你的应用程序可以执行的操作的详细信息，请参阅相邻选项卡中的 [Unity 的输入移植指南](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input) 。

### <a name="9-performance-testing-and-tuning"></a>9. 性能测试和优化

Windows Mixed Reality 将在各种设备上可用，范围从高端游戏电脑到广泛市场主流 Pc。 根据你的目标市场，你的应用程序的可用计算和图形预算有很大的差异。 在此迁移过程中，你可能会利用高级 PC，并为应用提供大量的计算和图形预算。 如果你希望将应用程序提供给更广泛的受众，则应在 [你想要面向的代表硬件](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)上测试和分析你的应用程序。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)和[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)都包含性能探查器， [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)和[Intel](https://software.intel.com/articles/vr-content-developer-guide)发布有关性能分析和优化的指导原则。 在 [了解混合现实的性能](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)方面，提供了有关性能的广泛讨论。 此外，针对 [unity 的性能建议](../../unity/performance-recommendations-for-unity.md)下的 unity 有特定的详细信息。

# <a name="input-mapping"></a>[输入映射](#tab/input)

你可以使用以下两种方法之一将输入逻辑移植到 Windows Mixed Reality： Unity 的一般输入. GetButton/GetAxis Api，跨越多个平台或特定于 Windows 的 XR。WSA.输入 Api，专门为运动控制器和 HoloLens 提供更丰富的数据。

> [!IMPORTANT]
> 如果你使用的是 HP 回音 G2 控制器，请参阅 [此文](../../unity/unity-reverb-g2-controllers.md) ，了解更多输入映射说明。

## <a name="unity-xr-input-apis"></a>Unity XR 输入 Api

对于新项目，建议从头开始使用新的 XR 输入 Api。 

可在此处找到有关 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。

## <a name="inputgetbuttongetaxis-apis"></a>GetButton/GetAxis Api

Unity 目前使用其常规输入. GetButton/GetAxis Api 来公开 [OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的输入。 如果你的应用程序已在使用这些 Api 进行输入，则这是在 Windows Mixed Reality 中支持运动控制器的最简单途径：只需重新映射输入管理器中的按钮和轴即可。

有关详细信息，请参阅 [Unity 按钮/轴映射表](../../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和 [常见 Unity api 的概述](../../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 特定的 XR。WSA.输入 Api

> [!CAUTION]
> 如果你的项目使用的是任何 XR。WSA Api 在未来的 Unity 版本中，这些 Api 将在 XR SDK 的后面逐步推出。 对于新项目，建议从头开始使用 XR SDK。 可在此处找到有关 [XR 输入系统和 api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。

如果应用已为每个平台构建自定义输入逻辑，则可以选择在 **UnityEngine** 命名空间下使用特定于 Windows 的空间输入 api。 这样，你就可以访问其他信息（如位置准确性或源类型），从而让你能够在 HoloLens 上区分双手和控制器。

> [!NOTE]
> 如果你使用的是 HP 回音 G2 控制器，则除 **InteractionSource** 以外的所有输入 api 都将继续工作，这将返回 false，而不会返回任何触摸板数据。

有关详细信息，请参阅 [UNITYENGINE XR api 概述](../../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持各种外形规格的运动控制器，其中每个控制器的设计在用户的手位置与应用程序在呈现控制器时应使用的自然 "前进" 方向不同。

为了更好地表示这些控制器，可以针对每个交互源调查以下两种类型：

* **手柄姿势**，表示由 HoloLens 检测到的掌托的位置，或包含运动控制器的掌托的位置。
    * 在沉浸式耳机上，这种姿势最适合用于呈现 **用户的手** 或 **持有用户的对象**，例如剑或机枪。
    * **手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。
    * **手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，与你的掌上的光线 (从右手掌向后) 
    * **手柄方向的正向轴**：当您关闭手中的部分 (时，就如同按住控制器) 一样，通过您的非拇指形来表示 "转发" 的射线。
    * **手柄方向的上轴**：向右和向后定义隐含的上轴。
    * 可以通过 Unity 的跨供应商输入 API (XR 来访问抓握姿势 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/旋转**) 或通过特定于 Windows 的 API (**sourcePose TryGetPosition/旋转**，) 请求手柄姿势。
* **指针姿势**，表示控制器的末端。
    * 这种姿势最适用于在呈现控制器模型本身时 **指向 UI** 时进行 raycast。
    * 目前，指针姿势仅可通过特定于 Windows 的 API (**TryGetPosition/旋转**，请求指针) 。

这些姿势坐标全部用 Unity 世界坐标表示。
