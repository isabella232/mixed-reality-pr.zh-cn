---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496128"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>混合现实 OpenXR 支持 Unity 中的功能

**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。 继续之前，请确保已安装 **Unity 2020.2** 或更高版本， **OpenXR 插件版本 0.1.3** 或更高版本，并且 Unity 项目已 [配置为 OpenXR](openxr-getting-started.md)。

## <a name="whats-supported"></a>支持的操作

目前支持以下功能：

* 支持 HoloLens 2 的 UWP 应用程序，并针对 HoloLens 2 应用程序模型进行优化。
* 支持适用于 Windows Mixed Reality 耳机的 Win32 VR 应用程序，包含最新控制器配置文件和全息应用远程处理。
* 使用定位点和无限空间进行世界规模跟踪。
* [用于将定位点保存](#anchors-and-anchor-persistence) 到 HoloLens 2 本地存储的定位存储 API。
* [运动控制器和手动交互](#motion-controller-and-hand-interactions)，包括新的 HP 回音 G2 控制器。
* 使用26个接合和接点输入的有向右跟踪。
* HoloLens 2 上的目视注视交互。
* 在 HoloLens 2 上查找 (PV) 相机的照片/视频。
* 混合现实通过 PV 相机使用第三种目视渲染来捕获。
* 支持 [通过全息远程处理应用 "播放" 到 HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)，使开发人员无需生成并部署到设备即可调试脚本。
* 与 MRTK Unity 2.5.3 和更高版本通过 [MRTK OpenXR 提供程序支持](openxr-getting-started.md#using-mrtk-with-openxr-support)兼容。
* 与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。
*  (在 0.1.3) 中添加的功能支持从生成和部署的 Windows 独立应用进行 [桌面应用全息远程处理](#holographic-remoting-in-desktop-app) 。

## <a name="holographic-remoting-setup"></a>全息远程处理安装

1. 首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址
    * 你需要使用版本2.4 或更高版本才能使用 OpenXR 插件

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 编辑器播放模式下的全息远程处理

在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。 一种解决方案是启用全息编辑器远程处理功能，该功能使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备。 此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。

1. 按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作
2. 打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框：

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. 展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"
4. 选中 " **全息编辑器远程处理** " 复选框并输入从全息远程处理应用获取的 IP 地址：

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。 还可以 [将 Visual Studio 连接到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以便在播放模式下调试 c # 脚本。

> [!NOTE]
> 从版本0.1.0 起，全息远程处理运行时不支持定位点，并且 ARAnchorManager 功能将无法通过远程处理。  此功能即将推出。

## <a name="holographic-remoting-in-desktop-app"></a>桌面应用中的全息远程处理

> [!NOTE]
> 0.1.3 包版本中添加了 Windows 独立应用远程处理支持。
> 从版本0.1.3 起，此功能不支持 UWP 生成。

1. 按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作
2. 打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框。 另外，取消选中 " **启动时初始化 XR"**：

    ![项目设置面板的屏幕截图在 Unity 编辑器中打开，并取消选中 "启动时初始化 XR"](images/openxr-features-img-02-app.png)

3. 展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"
4. 选中 " **全息应用远程处理** " 复选框：

    ![启用了应用远程处理的 Unity 编辑器中打开的项目设置面板的屏幕截图](images/openxr-features-img-03-app.png)

5. 接下来，编写一些代码以设置远程处理配置和触发器 XR 初始化。 使用 [混合现实 OpenXR 插件](openxr-getting-started.md#hololens-2-samples) 分发的示例应用包含 AppRemoting.cs，其中显示了在运行时连接到特定 IP 地址的示例方案。 此时，将示例应用程序部署到本地计算机，将使用 "连接" 按钮显示 IP 地址输入字段。 键入 IP 地址并单击 "连接" 将初始化 XR 并尝试连接到目标设备：

    ![示例应用显示示例应用远程处理 UI 的屏幕截图](images/openxr-sample-app-remoting.png)

6. 若要编写自定义连接代码，请使用已填充的进行调用 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。 该示例应用在检查器中公开此内容，并演示如何在文本字段中填充 IP 地址。 调用 `Connect` 将设置配置并自动初始化 XR，这就是为什么必须将其称为协同程序的原因：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 运行时，可以使用 API 获取当前连接状态 `AppRemoting.TryGetConnectionState` ，还可以选择断开连接，并使用取消初始化 XR `AppRemoting.Disconnect()` 。 这可用于断开连接并重新连接到同一应用会话中的其他设备。 示例应用提供了一个 tappable 多维数据集，该多维数据集会在点击时断开远程处理会话。

### <a name="migration-from-previous-apis"></a>从以前的 Api 迁移

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. HolographicRemoting

在 [Unity 文档](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)的示例代码中：

| XR.WSA.HolographicRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A：调用时自动发生 `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR.WindowsMR.WindowsMRRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | `AppRemoting.Connect`通过 `RemotingConfiguration` 结构传入 |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a>定位点和定位点持久性

Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。 若要了解有关 ARFoundation 中 **ARAnchor** 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。 从版本0.1.0，此插件支持除创建附加到某一平面的定位点之外的所有 ARAnchorManager 功能，后者将在将来的版本中推出。

### <a name="anchor-persistence-and-the-xranchorstore"></a>定位点持久性和 XRAnchorStore

另外一个名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。 XRAnchorStore 是设备上保存的定位点的表示形式。 定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。

> [!NOTE]
> 这些定位点将保存并加载到同一设备上。 未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

若要加载 XRAnchorStore，该插件会在 XRAnchorSubsystem （ARAnchorManager 的子系统）上提供扩展方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用此扩展方法，请按如下所示从 ARAnchorManager 的子系统访问它：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](openxr-getting-started.md#hololens-2-samples)中的定位点 > 锚样品 GameObject 和 AnchorsSample.cs 脚本：

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>运动控制器和手动交互

若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。 此 Unity 文档介绍了从特定于控制器的输入到更可归纳的 **InputFeatureUsage** 的映射，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。

Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准 **InputFeatureUsage**，如下所述：

| InputFeatureUsage | HP 回音 G2 控制器 (OpenXR)  | HoloLens 手型 (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操纵杆 | |
| primary2DAxisClick | 游戏杆-单击 | |
| 触发器 | 触发器  | |
| 调整 | 调整 | 空中分流或挤压 |
| primaryButton | [X/A]-按 | 隔空敲击 |
| secondaryButton | [Y/B]-按 | |
| gripButton | 手柄-按 | |
| triggerButton | 触发器-按 | |
| menuButton | 菜单 | |

### <a name="aim-and-grip-poses"></a>瞄准并抓住姿势

通过 OpenXR 输入交互可以访问两组姿势：

* 用于呈现对象的手柄姿势
* 目标是指进入世界。

有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。 与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。

InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。 这些 InputFeatureUsages 未在包含的任何 c # 文件中定义，因此你需要定义自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 unity [XR 输入-haptics 的 Unity 手册](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的文档。

## <a name="whats-coming-soon"></a>即将推出的内容

以下问题和缺少的功能是通过混合现实 OpenXR 插件 **版本 0.1.0** 知道的。 我们正在处理这些问题，将在即将发布的版本中发布修补程序和新功能。

* 尚不支持 **ARPlaneSubsystem** 。 HoloLens 2 上还不支持 **ARPlaneManager**、 **ARRAYCASTMANAGER** 和相关 API，如 **ARAnchorManager。**
* 全息远程处理尚不支持 **定位点**，但不久后会推出。
* 目前尚不支持 **手写** 跟踪、 **QR 码** 和 **XRMeshSubsystem** 。
* 未来版本中将提供 **Azure 空间锚点** 支持。
* **ARM64** 是仅适用于 HoloLens 2 应用的受支持平台。 **ARM** 平台即将发布。

## <a name="troubleshooting"></a>疑难解答

当你在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这将导致在 HoloLens 视图中显示4个旋转点。

* 将 OpenXR 项目设置中的 " **深度提交模式** " 设置为 " **无** " 作为一种解决方法
