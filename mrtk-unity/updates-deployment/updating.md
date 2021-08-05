---
title: 从早期版本更新
description: 从较低版本的 MRTK 进行迁移的文档。
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: a5d1e914fcbc44572e06c1fc3cbaba7ea0363287b9e670a423a4e63b17cb20a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210610"
---
# <a name="updating-from-earlier-versions"></a>从早期版本更新

- [升级到新版本的 MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 到2.4。0](#updating-230-to-240)
- [2.2.0 到2.3。0](#updating-220-to-230)
- [2.1.0 到2.2。0](#updating-210-to-220)
- [2.0.0 到2.1。0](#updating-200-to-210)
- [RC2 到2.0。0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>查找当前版本 

按照以下说明来确定当前正在使用的 MRTK 版本：

1. 在 Unity 中打开 MRTK 项目
2. 在 Project 窗口中导航到 "MixedRealityToolkit" 文件夹
3. 打开名为 "Version" 的文件

如果上面的文件和文件夹不存在，则是 MRTK 的较新版本。 在这种情况下，请尝试以下操作：

1. 导航到 "Mixed Reality Toolkit Foundation" 文件夹
2. 单击 "package.js打开" 以查看 Unity 中的预览或使用文本编辑器打开该预览版
3. 查找包含单词 "version：" 的行 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>升级到新版本的 MRTK

*强烈建议在获取 MRTK 更新后运行 [迁移工具](../features/tools/migration-window.md)* ，以自动修复并从弃用的组件升级，并调整为重大更改。 迁移工具是 **工具包** 的一部分。

以下说明介绍了 2.4.0 to 2.5.0 upgrade path。 如果项目在2.3.0 或更早版本上，请阅读 [版本间](#updating-230-to-240) 的更改以了解升级路径，或阅读以前 [版本的说明](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) ，以进行版本升级。

### <a name="mixed-reality-feature-tool"></a>混合现实功能工具
将 MRTK 升级到较新版本 MRTK 的最简单方法是使用 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 下载最新的包并将它们直接加载到 Unity 项目。

如果项目以前使用了 Unity 资产)  (，请参阅 [这些说明](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)。 

### <a name="unity-asset-unitypackage-files"></a>Unity 资产 ( unitypackage) 文件

另一种升级途径是手动下载 MRTK Unity 包并将其应用于你的项目。 请参阅以下步骤，

1. 保存当前项目的副本，以防在升级步骤中的任何点点击任何障碍。
1. 关闭 Unity
1. 在 " *资产* " 文件夹中，删除以下 **MRTK** 文件夹及其元文件 (项目可能没有所有列出的文件夹) 
    - MRTK/Core
    - MRTK/示例
    - MRTK/Extensions
    - MRTK/提供程序
    - MRTK/SDK
    - MRTK/服务
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > 如果对 MRTK 着色器进行了修改，请在删除 MRTK/StandardAssets 文件夹之前创建本地备份
    - MRTK/Tools
    > [!IMPORTANT]
    > 请勿删除 **MixedRealityToolkit** 文件夹或其元文件。
1. 删除 **库** 文件夹
    > [!IMPORTANT]
    > 某些 Unity 工具（如 Unity Collab）将配置信息保存到库文件夹。 如果使用这样的工具，请首先从库中复制该工具的数据文件夹，然后再删除，然后在库重新生成后将其还原。
1. 重新打开 Unity 中的项目
1. 导入新的 unity 包
    - Foundation- _首先导入此包_
    - 工具
    -  (可选) 扩展
    > [!NOTE]
    > 如果已安装其他扩展，则可能需要重新导入它们。
    -  (可选) 示例
1. 关闭 Unity 并删除 **库** 文件夹 (请先阅读下面的说明！ ) 。 此步骤是强制 Unity 刷新其资产数据库和协调现有自定义配置文件所必需的。
1. 为项目中的每个场景启动 Unity 和
    - 从层次结构中删除 **MixedRealityToolkit** 和 **MixedRealityPlayspace**（如果存在）。 这将删除主摄像机，但会在下一步中重新创建它。 如果已手动更改了主相机的任何属性，则在创建新相机后，必须手动重新应用这些属性。
    - 选择 **MixedRealityToolkit-> 添加到场景并配置**
    - 选择 **MixedRealityToolkit-> 公用事业-> Update-> 控制器映射配置文件** (仅需执行一次) -这将用更新的轴和数据更新任何自定义控制器映射配置文件，同时使自定义分配的输入操作保持不变
1. 运行 [迁移工具](../features/tools/migration-window.md)并在 *完整 Project* 上运行该工具，以确保将所有代码更新到最新版本。
   迁移窗口包含多个不同的迁移处理程序，这些处理程序必须各自运行。 此步骤涉及：
   - 从 " **迁移处理程序选择** " 下拉列表中选择第一个迁移处理程序。
   - 单击 "完全 Project" 按钮。
   - 单击 "添加用于迁移的完整项目" 按钮 (这将扫描要迁移的对象的整个项目) 。
   - 单击 "迁移" 按钮，如果找到任何 migrateable 对象，应启用该按钮。
   - 为下拉列表中的每个迁移处理程序重复前面三个步骤。
      (查看 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) ，其中包含可在未来版本中用于简化此迁移过程的工作) 

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>从 Unity 资产文件切换到混合现实功能工具

从 Unity 资产文件切换到混合现实功能包带来了很多好处：

- 更容易更新
- 更快的编译时间
- Visual Studio 解决方案中的项目较少

更改为使用混合现实功能工具需要一组一次性的手动步骤。

1. 保存当前项目的副本。
1. 关闭 Unity
1. 在 " *资产* " 文件夹中，删除以下 **MRTK** 文件夹及其元文件 (项目可能没有所有列出的文件夹) 
    - MRTK/Core
    - MRTK/示例
    - MRTK/Extensions
    - MRTK/提供程序
    - MRTK/SDK
    - MRTK/服务
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > 如果对 MRTK 着色器进行了修改，请在删除 MRTK/StandardAssets 文件夹之前创建本地备份
    - MRTK/Tools
    > [!IMPORTANT]
    > 请勿删除 **MixedRealityToolkit** 文件夹或其元文件。
1. 删除 **库** 文件夹
    > [!IMPORTANT]
    > 某些 Unity 工具（如 Unity Collab）将配置信息保存到库文件夹。 如果使用这样的工具，请首先从库中复制该工具的数据文件夹，然后再删除，然后在库重新生成后将其还原。
1. 重新打开 Unity 中的项目

执行前面的步骤后，运行[混合现实功能工具](#mixed-reality-feature-tool)，并导入所需的混合现实 Toolkit 版本。

## <a name="updating-230-to-240"></a>将2.3.0 更新为2.4。0

[文件夹重命名](#folder-renames-in-240) 
[API 更改](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>在2.4.0 中重命名文件夹

已重命名 MixedRealityToolkit 文件夹，并将其移入版本2.4 中的公共层次结构。 如果应用程序使用硬编码路径来 MRTK 资源，则需要按照下表对这些资源进行更新。

| 上一个文件夹 | 新建文件夹 |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit 示例 | MRTK/示例 |
| MixedRealityToolkit 扩展 | MRTK/Extensions |
| MixedRealityToolkit 提供程序 | MRTK/提供程序 |
| MixedRealityToolkit | MRTK/SDK |
| MixedRealityToolkit | MRTK/服务 |
| MixedRealityToolkit | MRTK/测试 |
| MixedRealityToolkit | MRTK/Tools |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`包含客户生成的文件，并且保持不变。

### <a name="eye-gaze-setup-in-240"></a>2.4.0 中的眼睛设置

此版本的 MRTK 修改目视注视设置所需的步骤。 在输入指针配置文件的 "注视" 设置中可以找到 _"IsEyeTrackingEnabled"_ 复选框。 选中此框将启用基于眼睛的眼睛，而不是默认的基于头的注视。

有关这些更改和跟踪设置的完整说明的详细信息，请参阅 [目视跟踪](../features/input/eye-tracking/eye-tracking-basic-setup.md) 文章。

### <a name="eye-gaze-pointer-behavior-in-240"></a>2.4.0 中的眼睛指针行为

已对眼睛默认指针行为进行了修改，使其与头眼睛默认指针行为匹配。 检测到手后，会自动抑制眼睛指示器。 "选择" 后，眼睛眼睛指针将再次变为可见。

可在 [眼睛和实习](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 文章中找到有关注视和手动设置的详细信息。

### <a name="api-changes-in-240"></a>2.4.0 中的 API 更改

**自定义控制器类**

自定义控制器类之前必须定义 `SetupDefaultInteractions(Handedness)` 。 此方法在2.4 中已过时，因为左右手使用习惯参数对于控制器类 "自有左右手使用习惯" 是冗余的。 新方法没有参数。 此外，许多控制器类定义了这种 () 的相同方式 `AssignControllerMappings(DefaultInteractions);` ，因此完全调用已重构为 `BaseController` ，并进行了可选替代，而不是必需的。

**眼睛属性**

的 `UseEyeTracking` 实现中的属性 `GazeProvider` `IMixedRealityEyeGazeProvider` 已重命名为 `IsEyeTrackingEnabled` 。

如果你之前执行此操作 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

立即执行此操作 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**WindowsApiChecker 属性**

以下 WindowsApiChecker 属性已标记为过时。 请使用 `IsMethodAvailable` 、 `IsPropertyAvailable` 或 `IsTypeAvailable` 。

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

无计划为将来的 API 协定版本向 WindowsApiChecker 添加属性。

**GltfMeshPrimitiveAttributes 只读**

用于可设置的 gltf 网状基元属性现在为只读。 反序列化时，将设置一次其值。

### <a name="custom-button-icon-migration"></a>自定义按钮图标迁移

以前的自定义按钮图标需要将新材料分配给按钮的四个呈现器。 这不再是必需的，我们建议将自定义图标纹理移到 IconSet。 保留现有的自定义材料和图标。 但在升级之前，它们将不太好。
若要将项目中所有按钮上的资产升级为新建议的格式，请使用 ButtonConfigHelperMigrationHandler。
 (混合现实 Toolkit-> 实用工具-> 迁移窗口-> 迁移处理程序选择-> MixedReality。Toolkit。ButtonConfigHelperMigrationHandler) 

![升级窗口对话框](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

如果在迁移过程中在默认图标集中找不到图标，将在 MixedRealityToolkit/CustomIconSets 中创建自定义图标集。 此时将显示一个对话框，指示已发生此情况。

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>将2.2.0 更新为2.3。0

- [API 更改](#api-changes-in-230)

### <a name="api-changes-in-230"></a>2.3.0 中的 API 更改

**ControllerPoseSynchronizer**

Private ControllerPoseSynchronizer. 左右手使用习惯字段已标记为过时。 这对应用程序的影响最小，因为字段在其类的外部不可见。

已 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)) 中删除 Public ControllerPoseSynchronizer 左右手使用习惯属性的 setter。

**Unity 的 MSBuild**

此版本的 MRTK 使用比以前版本更高的 Unity MSBuild 版本。 在项目加载期间，如果 "Unity 包管理器" 清单中列出了较旧的版本，则会出现 "配置" 对话框，并选中 "启用 MSBuild for Unity" 选项。 应用将执行升级。

**ScriptingUtilities**

ScriptingUtilities 类已标记为过时，并已被 ScriptUtilities 替换为 MixedReality。Toolkit。编辑器实用工具程序集。 新类将改进以前的行为并添加对删除脚本定义的支持。

尽管现有代码将继续在版本2.3.0 中运行，但建议将更新为新类。

**ShellHandRayPointer**

ShellHandRayPointer 类的 lineRendererSelected 和 lineRendererNoTarget 成员分别 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)) 替换。

请将 lineRendererSelected 替换为 lineMaterialSelected 和/或 lineRendererNoTarget with lineMaterialNoTarget，以解决编译错误。

**空间观察程序 Microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior**

基于类构建的空间观察器 `BaseSpatialObserver` 现在可在重新启用 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) 时遵循 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior 的值。

无需进行任何更改即可利用此修补程序。

**UX 控件 prototyping 已更新为使用 PressableButton**

以下 prototyping 现在正在使用 PressableButton 组件而不是 TouchHandler 进行近交互 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)) 

- AnimationButton
- Button
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

由于此更改，应用程序代码可能需要更新。

**WindowsMixedRealityUtilities 命名空间**

WindowsMixedRealityUtilities 的命名空间已更改为 MixedReality。Toolkit。WindowsMixedReality MixedReality。Toolkit。WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)) 。

请更新 #using 语句以解决编译错误。

## <a name="updating-210-to-220"></a>将2.1.0 更新为2.2。0

- [API 更改](#api-changes-in-220)

### <a name="api-changes-in-220"></a>2.2.0 中的 API 更改

**IMixedRealityBoundarySystem。包含**

之前，此方法采用特定的 Unity 定义试验性枚举。 它现在采用与 Unity 枚举相同的 MRTK 定义枚举。 此更改有助于为 Unity 未来的边界 Api 准备 MRTK。

**MixedRealityServiceProfileAttribute**

为了更好地描述支持配置文件的要求，MixedRealityServiceProfileAttribute 已更新为添加可选的排除类型集合。 作为此更改的一部分，ServiceType 属性已从类型更改为类型 []，并已重命名为 RequiredTypes。

还添加了另一个属性 ExcludedTypes。

## <a name="updating-200-to-210"></a>将2.0.0 更新为2.1。0

- [API 更改](#api-changes-in-210)
- [配置文件更改](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>2.1.0 中的 API 更改

**BaseNearInteractionTouchable**

已将 `BaseNearInteractionTouchable` 修改为将方法标记 `OnValidate` 为虚拟。 扩展 `BaseNearInteractionTouchable` (ex：) 的类已 `NearInteractionTouchableUnityUI` 更新，以反映此更改。

**ColliderNearInteractionTouchable**

`ColliderNearInteractionTouchable` 类已弃用。 请更新要使用的代码引用 `BaseNearInteractionTouchable` 。

**IMixedRealityMouseDeviceManager**

**_已_**

`IMixedRealityMouseDeviceManager` 添加了 `CursorSpeed` 和 `WheelSpeed` 属性。 这些属性允许应用程序指定一个乘数值，通过该值，可分别缩放光标和滚轮的速度。

这是一项重大更改，需要修改现有的鼠标设备管理器实现。

>[!NOTE]
>此更改与版本2.0.0 不向后兼容。

**_弃用_**

该 `MouseInputProfile` 属性已标记为过时，并将从 Microsoft Mixed Reality Toolkit 的未来版本中删除。 建议应用程序代码不再使用此属性。

**可交互**

以下方法和属性已弃用，并将从 Microsoft Mixed Reality Toolkit 的未来版本中删除。 建议按过时属性中包含的指南更新应用程序代码，并将其显示在控制台中。

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

`NearInteractionTouchableSurface`类已添加，现在用作和的基类 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 。

### <a name="profile-changes-in-210"></a>2.1.0 中的配置文件更改

**手动跟踪配置文件**

手写网格和联合可视化效果现在具有单独的编辑器和播放机设置。 手动跟踪配置文件已更新为允许将这些可视化效果设置为;所有内容、编辑器或播放机。

![手动可视化模式](../release-notes/images/HandTrackingVisualizationModes.png)

自定义手动跟踪配置文件可能需要更新才能在版本2.1.0 中正常工作。

>[!NOTE]
>此更改与版本2.0.0 不向后兼容。

**输入模拟配置文件**

已升级输入模拟系统，这将更改输入模拟配置文件中的几个设置。 某些更改不能自动迁移，用户可能会发现配置文件正在使用默认值。

1. 配置文件中的所有 KeyCode 和鼠标按钮绑定都已替换为泛型 `KeyBinding` 结构，该结构存储 (键或鼠标) 的绑定类型，以及分别)  (KeyCode 或鼠标按钮号的实际绑定代码。 结构具有自己的检查器，它允许统一显示，并提供 "自动绑定" 工具，通过按相应的键来快速设置键绑定，而不是从大下拉列表中进行选择。

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` 先前作为枚举包含在中 `MouseLookButton` `InputSimulationMouseButton.Focused` ，它现在是一个单独的选项。 启用后，照相机会在松开按钮后一直旋转鼠标，直到按下 esc 键。
1. `HandDepthMultiplier` 从0.1 到0.03 的默认值已降低，可适应对输入模拟进行的某些更改。 如果在滚动时相机移动速度太快，请尝试降低此值。
1. 旋转的键已被移除，手动旋转现在也由鼠标控制。 按住 `HandRotateButton` (Ctrl) ，同时 (LShift/Space) 将启用手写旋转。
1. 已将新的 "UpDown" 轴引入到输入轴列表。 这会控制垂直方向的相机运动，默认值为 Q/E 键以及控制器触发器按钮。

有关这些更改的详细信息，请参阅 [输入模拟服务](../features/input-simulation/input-simulation-service.md) 一文。

**鼠标数据提供程序配置文件**

已更新鼠标数据提供程序配置文件，以公开新的 `CursorSpeed` 和 `WheelSpeed` 属性。 现有的自定义配置文件将自动提供默认值。 保存配置文件时，将保留这些新值。

**控制器映射配置文件**

某些轴和输入类型在2.1.0 中进行了更新，尤其是围绕 OpenVR 平台。 请确保在升级时选择 **MixedRealityToolkit-> 公用事业-> 更新 > 控制器映射配置文件** 。 这会更新包含更新的轴和数据的任何自定义控制器映射配置文件，同时使自定义分配的输入操作保持不变。

## <a name="updating-rc2-to-200"></a>将 RC2 更新到2.0。0

Microsoft Mixed Reality Toolkit 的 RC2 版本和2.0.0 版本之间发生了更改，可能会影响现有项目。 本文档介绍这些更改，以及如何将项目更新到2.0.0 版本。

- [API 更改](#api-changes-in-200)
- [程序集名称更改](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>2.0.0 中的 API 更改

从版本 RC2 开始，有许多 API 更改，其中一些可能会破坏现有项目。 以下各节介绍了 RC2 和2.0.0 版本之间发生的更改。

**MixedRealityToolkit**

MixedRealityToolkit 对象上的以下公共属性已弃用。

- `RegisteredMixedRealityServices` 不再包含注册的扩展服务和数据提供程序的集合。

若要访问扩展服务，请使用 `MixedRealityServiceRegistry.TryGetService<T>` 。 若要访问数据访问接口，请将服务实例强制转换为 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 并使用 `GetDataProvider<T>` 。

使用 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 或 [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 而不是已弃用的以下属性

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)类是在对象中找到的静态系统访问器 (例如： BoundarySystem) 的替换 `MixedRealityToolkit` 。

>[!IMPORTANT]
>`MixedRealityToolkit`版本2.0.0 中已弃用系统访问器，将在 MRTK 的未来版本中将其删除。

下面的代码示例演示了旧模式和新模式。

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

如果将应用程序更改为使用不同的服务注册机构 (例如：某个试验性服务经理) ，则使用 new CoreSystem 类将确保应用程序代码不需要更新。

**IMixedRealityRaycastProvider**

如果添加了 IMixedRealityRaycastProvider，则会更改输入系统配置文件。 如果有自定义配置文件，则在运行应用程序时，可能会收到下图中的错误。

![选择 Raycast 提供程序1](../release-notes/images/UnableToRegisterRaycastProvider.png)

若要解决这些问题，请将 IMixedRealityRaycastProvider 实例添加到输入系统配置文件。

![选择 Raycast provider 2](../release-notes/images/SelectRaycastProvider.png)

**事件系统**

- `IMixedRealityEventSystem`旧的 API 方法 `Register` 和已 `Unregister` 标记为过时。 保留它们是为了向后兼容。
- `InputSystemGlobalListener` 已标记为过时。 其功能未发生更改。
- `BaseInputHandler` 基类已从更改 `InputSystemGlobalListener` 为 `InputSystemGlobalHandlerListener` 。 这是的任何后代的重大更改 `BaseInputHandler` 。

**_变化背后的动机_**

旧的事件系统 API `Register` 可能 `Unregister` 会导致运行时出现多个问题，主要是：

- 如果组件注册全局事件，则它将接收 *所有* 类型的全局输入事件。
- 如果对象上的组件之一注册全局输入事件，则此对象上的所有组件都将接收 *所有* 类型的全局输入事件。
- 如果同一对象上的两个组件注册到全局事件，然后在运行时中有一个处于禁用状态，则第二个组件将停止接收全局事件。

新 `RegisterHandler` 的 API 和 `UnregisterHandler` ：

- 提供对应全局侦听哪些输入事件以及哪些应基于焦点的输入事件进行显式和精细的控制。
- 允许同一对象上的多个组件彼此独立地侦听全局事件。

**_如何迁移_**

- 如果你以前直接调用了 `Register` / `Unregister` API，请将这些调用替换为对的调用 `RegisterHandler` / `UnregisterHandler` 。 使用实现为泛型参数的处理程序接口。 如果实现多个接口，并且其中几个接口侦听全局输入事件，则调用多次 `RegisterHandler` 。
- 如果已从继承 `InputSystemGlobalListener` ，请将继承更改为 `InputSystemGlobalHandlerListener` 。 实现 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法。 在实现调用中 `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) 在要侦听其全局事件的所有处理程序接口上进行注册。
- 如果已从继承，则 `BaseInputHandler` 实现 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法 (与 `InputSystemGlobalListener`) 相同。

**_迁移示例_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**空间感知**

IMixedRealitySpatialAwarenessSystem 和 IMixedRealitySpatialAwarenessObserver 接口发生了多个重大更改，如下所述。

**_更改_**

已重命名了以下方法 () ，以更好地描述其使用情况。

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 已将重命名为， `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 以明确其用法。

**_新增内容_**

根据客户反馈，增加了对以前观察到的空间意识数据的轻松删除的支持。

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**求解器**

某些规划求解组件和 SolverHandler manager 类已更改，可修复各种 bug，并获得更直观的用法。

**_SolverHandler_**

- 类不再从扩展 `ControllerFinder`
- `TrackedObjectToReference` 公共属性已弃用，已重命名为 `TrackedTargetType`
- `TrackedObjectType` 弃用左 & 右控制器值。 改为使用 `MotionController` 或 `HandJoint` 值，并更新新 `TrackedHandedness` 属性以将跟踪限制为左或右控制器

**_InBetween_**

- `TrackedObjectForSecondTransform` 公共属性已弃用，已重命名为 `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` 已删除。 若要更新规划求解，请修改公共属性 (即 `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` 公共属性已弃用，已重命名为 `MaxRaycastDistance`
- `CloseDistance` 公共属性已弃用，已重命名为 `ClosestDistance`
- 的默认值 `RaycastDirectionMode` 现在 `TrackedTargetForward` raycasts 跟踪的目标转换的方向
- `OrientationMode` 枚举值 `Vertical` 和 `Full` ，分别重命名为 `TrackedTarget` 和 `SurfaceNormal` 。
- `KeepOrientationVertical` 添加了公共属性，用于控制是否将相关 GameObject 的方向保持垂直

**按钮**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 现在已 `DistanceSpaceMode` 将属性设置为 `Local` 默认值。 这允许在仍 pressable 的情况下缩放按钮

**剪切球**

ClippingSphere 接口已更改为镜像在 ClippingBox 和 ClippingPlane 中找到的 Api。

现在，ClippingSphere 的 Radius 属性基于转换比例进行隐式计算。 开发人员必须在检查器中指定 ClippingSphere 的半径。 如果要更改 radius，只需像往常一样更新转换的转换比例。

**NearInteractionTouchable 和 PokePointer**

- NearInteractionTouchable 不会再处理 Unity UI 画布。 NearInteractionTouchableUnityUI 类必须立即用于 Unity UI touchables。
- ColliderNearInteractionTouchable 是基于 colliders 的 touchables （即每个可触摸除外）的新基类。
- BaseNearInteractionTouchable 已移动，并已重命名为 PokePointer。 TouchableDistance 这是 PokePointer 可以与 touchables 交互的距离。 之前，每个可触摸都有其自己的最大交互距离，但现在这是在 PokePointer 中定义的，它可以更好地进行优化。
- BaseNearInteractionTouchable 已将 DistBack 重命名为 PokeThreshold，这使得 PokeThreshold 是 DebounceThreshold 的对应项。 当超过 PokeThreshold 时，将激活可触摸，并在超过 DebounceThreshold 后释放。

**ReadOnlyAttribute**

`Microsoft.MixedReality.Toolkit`命名空间已添加到 `ReadOnlyAttribute` 、 `BeginReadOnlyGroupAttribute` 和 `EndReadOnlyGroupAttribute` 。

**PointerClickHandler**

`PointerClickHandler` 类已弃用。 `PointerHandler`应改用，它提供相同的功能。

**HoloLens clicker 支持**

HoloLens clicker 的控制器映射已从 unhanded 更改 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) 为 unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 。 为此，将在首次打开 ControllerMapping 配置文件时运行自动更新程序。 升级到2.0.0 后，请至少打开一次自定义配置文件，以便触发此一次性迁移步骤。

**InteractableHighlight**

`InteractableHighlight` 类已弃用。 `InteractableOnFocus` `FocusInteractableStates` 应改用类和资产。 若要为创建新 `Theme` 资产 `InteractableOnFocus` ，请在项目窗口中右键单击，然后选择 "*创建*  >  *混合现实 Toolkit*  >  *种不可交互*"  >  *主题*。

**HandInteractionPanZoom**

`HandInteractionPanZoom` 已移至 UI 命名空间，因为它不是输入组件。 `HandPanEventData` 已移动到此命名空间中，并进行了简化以与其他 UI 事件数据相对应。

### <a name="assembly-name-changes-in-200"></a>2.0.0 中的程序集名称更改

在2.0.0 版本中，所有官方混合现实 Toolkit 程序集名称及其关联的程序集定义 () 文件已更新为适合以下模式。

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

在某些情况下，已合并多个程序集，以创建更好的内容。 如果项目使用 asmdef 文件，可能需要更新。

下表描述了 RC2 asmdef 文件名如何映射到2.0.0 版本。 所有程序集名称均与 asmdef 文件名匹配。

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | MixedReality。Toolkit. asmdef |
| MixedRealityToolkit. BuildAndDeploy. asmdef | MixedReality。Toolkit。BuildAndDeploy. asmdef |
| MixedRealityToolkit. asmdef。 | 删除，请使用 MixedReality。Toolkit。Asmdef |
| MixedRealityToolkit. EditorClassExtensions. asmdef | MixedReality。Toolkit。ClassExtensions. asmdef
| MixedRealityToolkit. asmdef | MixedReality。Toolkit。Asmdef |
| MixedRealityToolkit. ServiceInspectors. asmdef | MixedReality。Toolkit。ServiceInspectors. asmdef |
| MixedRealityToolkit. UtilitiesAsync. asmdef | MixedReality。Toolkit。Asmdef |
| MixedRealityToolkit. asmdef。 | MixedReality。Toolkit。Asmdef |
| MixedRealityToolkit. Gltf. asmdef | MixedReality。Toolkit。Gltf.asmdef |
| MixedRealityToolkit. Gltf. asmdef | MixedReality。Toolkit。Gltf. asmdef |

**MixedRealityToolkit 提供程序**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. OpenVR. asmdef | MixedReality。Toolkit。OpenVR. asmdef |
| MixedRealityToolkit. WindowsMixedReality. asmdef | MixedReality。Toolkit。WindowsMixedReality. asmdef |
| MixedRealityToolkit. WindowsVoiceInput. asmdef | MixedReality。Toolkit。WindowsVoiceInput. asmdef |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. BoundarySystem. asmdef | MixedReality。Toolkit。BoundarySystem. asmdef |
| MixedRealityToolkit. CameraSystem. asmdef | MixedReality。Toolkit。CameraSystem. asmdef |
| MixedRealityToolkit. DiagnosticsSystem. asmdef | MixedReality。Toolkit。DiagnosticsSystem. asmdef |
| MixedRealityToolkit. InputSimulation. asmdef | MixedReality。Toolkit。InputSimulation. asmdef |
| MixedRealityToolkit. InputSimulation. asmdef | MixedReality。Toolkit。InputSimulation. asmdef |
| MixedRealityToolkit. InputSystem. asmdef | MixedReality。Toolkit。InputSystem. asmdef |
| MixedRealityToolkit. asmdef | MixedReality。Toolkit。InputSystem. asmdef |
| MixedRealityToolkit. SceneSystem. asmdef | MixedReality。Toolkit。SceneSystem. asmdef |
| MixedRealityToolkit. SpatialAwarenessSystem. asmdef | MixedReality。Toolkit。SpatialAwarenessSystem. asmdef |
| MixedRealityToolkit. TeleportSystem. asmdef | MixedReality。Toolkit。TeleportSystem. asmdef |

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. asmdef | MixedReality。Toolkit。Asmdef |
| MixedRealityToolkit. asmdef | MixedReality。Toolkit。SDK.Asmdef |

**MixedRealityToolkit 示例**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. asmdef | MixedReality。Toolkit。示例。 asmdef |
| MixedRealityToolkit. Gltf. asmdef | MixedReality。Toolkit。Gltf. asmdef |
| MixedRealityToolkit. StandardShader. asmdef | MixedReality。Toolkit。StandardShader. asmdef |
| MixedRealityToolkit. InspectorFields. asmdef | MixedReality。Toolkit。InspectorFields. asmdef |
| MixedRealityToolkit. InspectorFields. asmdef。 | MixedReality。Toolkit。InspectorFields. asmdef |
| MixedRealityToolkit. Interactables. asmdef | MixedReality。Toolkit。Interactables. asmdef |
