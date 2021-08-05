---
title: MRTK 包
description: MRTK 中的包支持混合现实硬件和平台。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Unity 程序包管理器，
ms.openlocfilehash: 13f18c0a43d8b0cf6cc8eb66949b506c51ca9bbaa733e74cd38de110f70d8ee1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212558"
---
# <a name="mrtk-packages"></a>MRTK 包

混合现实Toolkit (MRTK) 是一个包集合，通过为混合现实硬件和平台提供支持，实现跨平台混合现实应用程序开发。

MRTK 作为资产[包](#asset-packages) (.unitypackage) 通过[Unity](#unity-package-manager)程序包管理器 提供。

## <a name="asset-packages"></a>资产包

可以从) 下载 MRTK (.unitypackage [GitHub。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)

使用资产包的一些好处包括：

- 适用于 Unity 2018.4 及更高版本
- 轻松更改 MRTK
  - MRTK 位于 Assets 文件夹中

下面是一些难点：

- MRTK 是项目的 Assets 文件夹的一部分，导致
  - 大型项目
  - 编译时间更慢
- 无依赖项管理
  - 客户需要手动解析包依赖项
- 手动更新过程
  - 多个步骤
  - 包含 (3000 多个文件) 源代码管理更新
  - 丢失对 MRTK 所做的更改的风险
- 导入示例包通常意味着包括所有示例

可用的包包括：

- [Foundation](#foundation-package)
- [扩展](#extensions-package)
- [工具](#tools-package)
- [测试实用工具](#test-utilities-package)
- [示例](#examples-package)

这些包由 Microsoft 从 mrtk_release[分支中的](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release)源代码发布GitHub。

### <a name="foundation-package"></a>基础包

Mixed Reality Toolkit Foundation 是一组代码，可让应用程序跨混合现实平台利用常见功能。

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>MRTK 基础包</sup>

MRTK Foundation 包包含以下内容。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/Core | | 接口和类型定义、基类、标准着色器。 |
| MRTK/核心/提供程序 | | 与平台无关的数据访问者 |
| | 手 | 用于手部跟踪的基类支持和服务。 |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 支持记录头部移动和手部跟踪数据。 |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 支持手动和眼睛输入的编辑器内模拟。 |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 空间感知观察程序使用三维模型作为数据。 |
| | UnityInput | 常见的输入设备 (、鼠标等) Unity 的输入 API 实现。 |
| MRTK/提供程序 | | 特定于平台的数据提供程序 |
| | LeapMotion | 支持 UltraLeap Leap Motion 控制器。 |
| | OpenVR | 支持 OpenVR 设备。 |
| | Oculus | 支持 Oculus 设备，例如 Quest。 |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) |  (用于) AR 设备的 MRTK 的实验性相机设置提供程序。 |
| | WindowsMixedReality | 支持Windows Mixed Reality设备，包括Microsoft HoloLens头戴显示设备。 |
| | Windows | 支持 Microsoft Windows特定 API，例如语音和听写。 |
| | XR SDK |  (Unity) 2019.3 及更高版本中对 Unity 的新 [XR](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 框架的实验性支持。 |
| MRTK/SDK | | |
| | 实验 | 实验性功能，包括着色器、用户界面控件和单个系统管理员。 |
| | 功能 | 基于 Foundation 包构建的功能。 |
| | 配置文件 | Microsoft Mixed Reality 的默认配置文件Toolkit系统和服务。 |
| | StandardAssets | 常见资产;模型、纹理、材料等。 |
| MRTK/SceneSystemResources | | 场景系统使用的资产和资源 |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | 实现 VR 边界支持的系统。 |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 实现相机配置和管理的系统。 |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 在应用程序诊断中实现的系统，例如可视化探查器。 |
| | [InputSystem](../features/input/overview.md) | 为访问和处理用户输入提供支持的系统。 |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 提供多场景应用程序支持的系统。 |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 提供用户环境感知支持的系统。 |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | 系统为远程传送提供支持 (移动跳转体验) 。 |
| MRTK/StandardAssets | | 混合现实体验的 MRTK 标准着色器、基本材料和其他标准资产 |

### <a name="extensions-package"></a>扩展包

可选的 Microsoft.MixedRealityToolkit.Unity.Extensions 包包含其他服务，这些服务扩展了 Microsoft Mixed Reality Toolkit。

> [!NOTE]
> 扩展包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/扩展 | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 向手部添加物理支持的服务。 |
| | LostTrackingService | 简化在设备上处理跟踪丢失Microsoft HoloLens的服务。 |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 可简化平滑场景转换添加的服务。 |

### <a name="tools-package"></a>工具包

可选的 Microsoft.MixedRealityToolkit.Unity.Tools 包包含有用的工具，这些工具使用 Microsoft Mixed Reality Toolkit。
这些工具位于 Unity 编辑器中的"混合现实 **Toolkit >实用工具**"菜单中。

> [!NOTE]
> 工具包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/工具 | |
| | BuildWindow | 有助于简化 UWP 应用程序的生成和部署过程的工具。 |
| | [DependencyWindow](../features/tools/dependency-window.md) | 在项目中创建资产依赖项关系图的工具。 |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 帮助创建扩展服务的向导。 |
| | [MigrationWindow](../features/tools/migration-window.md) | 可帮助更新使用已弃用 MRTK 组件的代码的工具。  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | 可帮助自动配置混合现实项目的实用工具，以在 Unity 中实现最佳性能。 |
| | ReserializeAssetsUtility | 提供对重新初始化特定 Unity 文件的支持。 |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 使开发人员能够快速确定硬件控制器的 Unity 映射的实用工具。 |
| | ScreenshotUtility | 在 Unity 编辑器中启用捕获应用程序映像。 |
| | TextureCombinerWindow | 用于组合图形纹理的实用工具。 |
| | [工具箱](../features/ux-building-blocks/toolbox.md) | UI，可轻松发现和使用 MRTK UX 组件。 |

### <a name="test-utilities-package"></a>测试实用工具包

可选的 Microsoft.MixedRealityToolkit.TestUtilities 包是帮助程序脚本的集合，开发人员可以轻松地 [创建播放模式测试](../contributing/unit-tests.md#play-mode-tests)。 这些实用工具对于创建 MRTK 组件的开发人员特别有用。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/测试 | |
| | TestUtilities | 简化播放模式测试创建的方法，包括手动模拟实用工具。 |

### <a name="examples-package"></a>示例包

示例包包含演示、示例脚本和在基础包中练习功能的示例场景。 此包包含 [handInteractionExample](../features/example-scenes/hand-interaction-examples.md) 场景 (如下图) 其中包含响应各种手动输入的示例对象，这些对象 (表达和非) 。

![HandInteractionExample 场景](../features/images/MRTK_Examples.png)

此包还包含眼动跟踪演示， [此处记录了这些演示](../features/example-scenes/eye-tracking-examples-overview.md)

更一般而言，MRTK 中任何新功能都应包含示例包中的相应示例，大致遵循相同的文件夹结构和位置。

> [!NOTE]
> 示例包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/示例 | | |
| | 演示 | 演示一个或两个相关功能的简单场景。 |
| | 实验 | 演示实验性功能的演示场景。 |
| | StandardAssets | 由多个演示场景共享的常见资产。 |

## <a name="unity-package-manager"></a>Unity 程序包管理器

对于使用 Unity 2019.4 及更高版本创建的体验，MRTK 可通过[Unity](https://docs.unity3d.com/Manual/Packages.html)程序包管理器。

使用资产包的一些好处包括：

- 较小的项目
  - 更Visual Studio解决方案
  - 在 MRTK (签入的文件更少是文件中简单的 `Packages/manifest.json`) 
- 更快的编译速度
  - Unity 无需在生成期间重新编译 MRTK
- 依赖项解析
  - 指定具有依赖项的包时，会自动安装所需的 MRTK 包
- 轻松更新到新的 MRTK 版本
  - 更改文件中 `Packages/manifest.json` 的版本

下面是一些难点：

- MRTK 是不可变的
  - 无法在包解析过程中删除更改
- MRTK 不支持 Unity 2018.4 的 UPM 包

### <a name="foundation-package"></a>基础包

基础包 `com.microsoft.mixedreality.toolkit.foundation` () 混合现实解决方案的基础Toolkit。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/Core | | 接口和类型定义、基类、标准着色器。 |
| MRTK/核心/提供程序 | | 与平台无关的数据访问者 |
| | 手 | 用于手部跟踪的基类支持和服务。 |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 支持记录头部移动和手部跟踪数据。 |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 支持手动和眼睛输入的编辑器内模拟。 |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 空间感知观察程序使用三维模型作为数据。 |
| | UnityInput | 常见的输入设备 (、鼠标等) Unity 的输入 API 实现。 |
| MRTK/提供程序 | | 特定于平台的数据提供程序 |
| | LeapMotion | 对 UltraLeap Leap 运动控制器的支持。 |
| | OpenVR | 支持 OpenVR 设备。 |
| | Oculus | 支持 Oculus 设备，如寻找。 |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) |  (试验性) 照相机设置提供程序启用 MRTK 与移动 AR 设备一起使用。 |
| | WindowsMixedReality | 支持 Windows Mixed Reality 设备，包括 Microsoft HoloLens 和沉浸式耳机。 |
| | Windows | 支持 Microsoft Windows 特定的 api，例如语音和听写。 |
| | XR SDK |  (了对 unity 2019.3 和更高版本中 [unity 的 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的实验性) 支持。 |
| MRTK/SDK | | |
| | 实验 | 实验功能，包括着色器、用户界面控件和单个系统管理器。 |
| | 功能 | 基于基础包生成的功能。 |
| | 配置文件 | Microsoft Mixed Reality Toolkit 系统和服务的默认配置文件。 |
| | StandardAssets | 常用资产;模型、纹理、材料等。 |
| MRTK/服务 | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | 实现 VR 边界支持的系统。 |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 实现照相机配置和管理的系统。 |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 应用程序诊断中的系统实现，例如，可视化探查器。 |
| | [InputSystem](../features/input/overview.md) | 系统为访问和处理用户输入提供支持。 |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 提供多场景应用程序支持的系统。 |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 系统提供对用户环境感知的支持。 |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | 系统为 teleporting 提供支持 (移动) 中的体验。 |

依赖项：

- 标准资产 (`com.microsoft.mixedreality.toolkit.standardassets`) 

### <a name="standard-assets"></a>标准资产

标准资产包 (`com.microsoft.mixedreality.toolkit.standardassets)` 是为所有混合现实体验推荐的组件集合，其中包括：

- MRTK 标准着色器
- 使用 MRTK 标准着色器的基本材料
- 音频文件
- 字体
- 纹理
- 图标

> [!Note]
> 若要避免基于程序集定义的重大更改，用于控制 MRTK 标准着色器的某些功能的脚本不包括在标准资产包中。 可以在文件夹的基础包中找到这些脚本 `MRTK/Core/Utilities/StandardShader` 。

依赖关系：无

### <a name="extension-packages"></a>扩展包

可选扩展包 (`com.microsoft.mixedreality.toolkit.extensions)` 包含扩展 MRTK 功能的附加组件。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 将物理支持添加到明确表述的服务。 |
| | LostTrackingService | 简化 Microsoft HoloLens 设备上跟踪丢失的处理服务。 |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 简化场景过渡的简化。 |
| | 示例 ~ | Unity 编辑器中的隐藏 () 包含样本场景和资产的文件夹。 |

有关使用包含示例项目的包的过程的更多详细信息，可在[混合现实 Toolkit 和 Unity 程序包管理器](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)一文中找到。

依赖项：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 

### <a name="tools-package"></a>工具包

可选的工具包 (`com.microsoft.mixedreality.toolkit.tools)` 包含可用于创建混合现实体验的工具。 通常，这些工具是编辑器组件，其代码不作为应用程序的一部分提供。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | 有助于简化生成和部署 UWP 应用程序的过程的工具。 |
| | [DependencyWindow](../features/tools/dependency-window.md) | 用于创建项目中资产的依赖项关系图的工具。 |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 用于帮助创建扩展服务的向导。 |
| | [MigrationWindow](../features/tools/migration-window.md) | 有助于更新使用不推荐使用的 MRTK 组件的代码的工具。  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | 用于帮助自动配置混合现实项目以获得 Unity 中最佳性能的实用程序。 |
| | ReserializeAssetsUtility | 提供对 reserializing 特定 Unity 文件的支持。 |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 实用工具，使开发人员能够快速确定硬件控制器的 Unity 映射。 |
| | ScreenshotUtility | 启用在 Unity 编辑器中捕获应用程序映像。 |
| | TextureCombinerWindow | 用于合并图形纹理的实用程序。 |
| | [工具箱](../features/ux-building-blocks/toolbox.md) | 使用户能够轻松发现和使用 MRTK UX 组件的 UI。 |

依赖项：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 

### <a name="test-utilities-package"></a>测试实用工具包

可选的测试实用工具包 (`com.microsoft.mixedreality.toolkit.testutilities`) 包含帮助开发人员轻松创建播放模式测试的帮助器脚本集合。 对于创建 MRTK 组件的开发人员而言，这些实用工具特别有用。

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/测试 | |
| | TestUtilities | 简化播放模式测试创建的方法，包括手动模拟实用工具。 |

依赖项：

- 基础 `com.microsoft.mixedreality.toolkit.foundation` () 

### <a name="examples-package"></a>示例包

示例包 `com.microsoft.mixedreality.toolkit.examples` () ，其结构允许开发人员仅导入感兴趣的示例。

有关使用包含示例项目的包的过程的更多详细信息，请参阅混合现实和 Unity Toolkit一[程序包管理器。](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

| 文件夹 | 组件 | 说明 |
| --- | --- | --- |
| MRTK/示例 | | |
| | 示例~ | Unity 编辑器 (隐藏) 包含示例场景和资产的文件夹中。 |
| | StandardAssets | 由多个演示场景共享的常见资产。 |

依赖项：

- 基础 `com.microsoft.mixedreality.toolkit.foundation` () 
- 扩展 (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>另请参阅

- [体系结构概述](../architecture/overview.md)
- [系统、扩展服务和数据提供程序](../architecture/systems-extensions-providers.md)
- [混合现实Toolkit Unity 程序包管理器](../configuration/usingupm.md)
