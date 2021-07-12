---
title: 将 HoloLens（第 1 代）应用移植到 HoloLens 2
description: 本文面向目前已在 HoloLens（第 1 代）和早期 MRTK 版本上拥有应用，且希望移植到 MRTK 版本 2 和 HoloLens 2 的开发人员。
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, MRTK, MRTK 版本 2, HoloLens 2, unity, 移植, HoloLens 第一代, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 迁移, 最佳做法, ARM
ms.openlocfilehash: 512bd3e841d40ffd606d59ee4bb4d955306cc2d0
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042248"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>将 HoloLens（第 1 代）应用移植到 HoloLens 2

本指南帮助开发人员移植其适用于 HoloLens（第 1 代）的现有 Unity 应用程序，使其可在 HoloLens 2 设备上运行。 将 HoloLens（第 1 代）Unity 应用程序移植到 HoloLens 2 需要完成四个关键步骤。 

以下部分将提供每个阶段的详细信息：

| 步骤 1 | 步骤 2 | 步骤 3 | 步骤 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 徽标](../images/visualstudio_logo.png) | ![Unity 徽标](../../design/images/logo-unity.png)| ![Unity 图标](../unity/images/hololens2_icon.jpg) | ![MRTK 徽标](../../design/images/74-12.png) |
| 下载最新的工具 | 更新 Unity 项目 | ARM 编译 | 迁移到 MRTK v2

## <a name="prerequisites"></a>先决条件

我们强烈建议在开始移植过程之前，使用源代码管理保存应用程序原始状态的快照。 此外，建议在迁移过程中的不同时间保存检查点状态。 再保留一个原始应用程序的 Unity 实例也很有帮助，这便于在移植过程中进行并列比较。 

> [!NOTE]
> 在移植之前，请确保已安装用于 Windows Mixed Reality 开发的最新工具。 对于当前大部分 HoloLens 开发人员而言，这涉及到更新到最新版的 Visual Studio 2019 并安装相应的 Windows SDK。 以下内容会深入到不同的 Unity 版本和混合现实工具包 (MRTK) 版本 2。
>
> 有关详细信息，请参阅[安装工具](../install-the-tools.md)。

## <a name="migrate-project-to-the-latest-version-of-unity"></a>将项目迁移到最新版本的 Unity

如果您使用的是 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)，我们建议先更新到 MRTK 2.7，然后再将项目升级到 [Unity 2020.3 LTS](../unity/choosing-unity-version.md)。 MRTK 2.7 支持 Unity 2018、2019 和 2020，使您能够在升级 Unity 之前确保您的项目可以在 Unity 2020 中使用。 评估项目中当前存在的所有[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)，并确定是否可为 ARM64 生成这些 DLL。 对于包含必需的 ARM64 依赖项插件的项目，可能需要继续为 ARM 生成应用。

## <a name="update-sceneproject-settings-in-unity"></a>在 Unity 中更新场景/项目设置

更新到 [Unity 2020.3 LTS](https://unity3d.com/unity/qa/lts-releases) 之后，建议在 Unity 中更新特定设置，以便在设备上获得最佳结果。 [Unity 的建议设置](../unity/Recommended-settings-for-Unity.md)中详细描述了这些设置。

再次重申，[.NET 脚本后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)即将在 Unity 2018 中弃用，并将从 Unity 2019 开始删除。 强烈建议开发人员将其项目切换到 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。

> [!NOTE]
> IL2CPP 脚本后端可能导致增大从 Unity 到 Visual Studio 的生成时间，因此，开发人员应设置好其计算机，以[优化 IL2CPP 生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。
> 此外，设置[缓存服务器](https://docs.unity3d.com/Manual/CacheServer.html)可能会有所帮助，尤其是对于包含大量资产（不包括脚本文件）或不断变化的场景和资产的 Unity 项目而言。 打开项目时，Unity 会在开发人员计算机上将符合条件的资产存储为内部缓存格式。 必须重新导入项，项在修改后会重新经过处理。 此过程可以执行一次，结果可保存在缓存服务器，因此可与其他开发人员共享以节省时间，无需让每个开发人员在本地重新导入新的更改。

在处理完因移至 Unity 更新版而导致的所有中断性变更后，请在 HoloLens（第 1 代）上生成和测试你目前的应用程序。 在此阶段很适合在源代码管理中创建并保存提交内容。

## <a name="compile-dependenciesplugins-for-arm-processor"></a>编译 ARM 处理器的依赖项/插件

HoloLens（第 1 代）在 x86 处理器上执行应用程序，而 HoloLens 2 则使用 ARM 处理器。 需要移植现有的 HoloLens 应用程序才能支持 ARM。 如前所述，Unity 2018 LTS 支持 ARM32 应用的编译，而 Unity 2019 和更高版本支持 ARM32 和 ARM64 应用的编译。 最好是针对 ARM64 应用程序进行开发，因为性能方面存在本质的差异。 但是，这也需要对 ARM64 生成所有[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)。

请检查应用程序中的所有 DLL 依赖项。 建议删除项目不再需要的依赖项。 对于所需的剩余插件，请将相应的 ARM32 或 ARM64 二进制文件引入 Unity 项目中。

引入相关的 DLL 后，从 Unity 生成一个 Visual Studio 解决方案，在 Visual Studio 中编译一个适用于 ARM 的 AppX，以测试应用程序是否可以针对 ARM 处理器生成。 建议在源代码管理解决方案中保存应用程序作为提交内容。

> [!IMPORTANT]
> 在将生成目标更改为 ARM 后，应用程序使用 MRTK v1 可在 HoloLens 2 上运行，前提是满足其他所有要求。 这包括确保你具有所有插件的 ARM 版本。 但是，你的应用将无权使用手动跟踪和眼动跟踪等 HoloLens 2 特定功能。 MRTK v1 和 MRTK v2 具有不同的命名空间，使这两种版本可位于同一项目中，这对于将一种版本转换为另一版本来说非常有用。

## <a name="update-to-mrtk-version-2"></a>更新到 MRTK 版本 2

[MRTK 版本 2](https://github.com/microsoft/MixedRealityToolkit-Unity) 是基于 Unity 的新工具包，支持 HoloLens（第 1 代）和 HoloLens 2， 其中还添加了所有新的 HoloLens 2 功能，例如手动交互和眼动跟踪。

有关使用 MRTK 版本 2 的详细信息，，请查看下列资源：

- [MRTK - 文档主页](/windows/mixed-reality/mrtk-unity)
- [安装指南](/windows/mixed-reality/mrtk-unity/install-the-tools)
- [MRTK - 手部跟踪](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
- [MRTK - 眼动跟踪](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

### <a name="prepare-for-the-migration"></a>准备迁移

在引入新的[适用于 MRTK v2 的 *.unitypackage 文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)之前，建议清点：1) 与 MRTK v1 集成的任何自定义生成代码；2) 用于输入交互或 UX 组件的任何自定义生成代码 。 混合现实开发人员在引入 MRTK v2 时最常出现的冲突与输入和交互相关。 我们建议阅读并理解 [MRTK v2 输入模型](/windows/mixed-reality/mrtk-unity/features/input/overview)。

最后，新的 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 已从脚本和场景内管理器对象模型过渡到配置与服务提供程序体系结构。 这可以建立一种更简洁的场景层次结构和体系结构模型，但需要通过学习来了解新的配置文件。 请阅读[混合现实工具包配置指南](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)，以开始熟悉重要的设置和配置文件，并根据应用程序的需求进行调整。

### <a name="migrating-the-project"></a>迁移项目

导入 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 后，Unity 项目很可能会出现多种与编译器相关的错误。 这些错误通常是新的命名空间结构和新的组件名称造成的。 请将脚本修改为新的命名空间和组件，以继续解决这些错误。

若要了解 HTK/MRTK 与 MRTK v2 之间的具体 API 差异，请参阅 [MRTK 版本 2 Wiki](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide) 中的移植指南。

### <a name="best-practices"></a>最佳实践

- 优先使用 [MRTK 标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)。
- 每次处理一种重大更改类型（例如：将 IFocusable 更改为 [IMixedRealityFocusHandler](/dotnet/api/microsoft.mixedreality.toolkit.input.imixedrealityfocushandler)）。
- 每次更改后进行测试，并使用源代码管理。
- 尽可能使用默认 MRTK UX（按钮、盖板等）。
- 避免直接修改 MRTK 文件，改为创建围绕 MRTK 组件的包装器。
  - 此操作方便将来的 MRTK 引入和更新。
- 查看并探索 MRTK 中提供的示例场景，尤其是 *HandInteractionExamples.scene*。
- 使用四面体、碰撞体和 TextMeshPro 文本重新生成基于画布的 UI。
- 启用[深度缓冲区共享](../unity/camera-in-unity.md#sharing-depth-buffers)或[设置焦点](../unity/focus-point-in-unity.md)；首选使用 16 位深度缓冲区以提高性能。 确保在渲染颜色的同时渲染深度。 Unity 通常不会写入透明和文本游戏对象的深度。
- 设置单通道实例化渲染路径。
- 使用 [MRTK 的 HoloLens 2 配置文件](/windows/mixed-reality/mrtk-unity/features/profiles/profiles#hololens-2-profile)

### <a name="testing-your-application"></a>测试应用程序

在 MRTK 版本 2 中，可以直接在 Unity 中模拟手动交互，并使用新的 API 进行手动交互和眼动跟踪方面的开发。 需要使用 HoloLens 2 设备才能建立令人满意的用户体验。 我们鼓励你开始学习相应的文档和工具，以加深了解。 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 支持在 HoloLens（第 1 代）上进行开发，因此，可以在 HoloLens（第 1 代）上测试通过隔空敲击进行选择的操作。 

## <a name="updating-your-interaction-model-for-hololens-2"></a>更新 HoloLens 2 的交互模型

> [!CAUTION]
> 如果项目使用的是任一 XR.WSA API，则在将来的 Unity 版本中，这些 API 将逐步淘汰，取而代之的是 Unity 的新 XR 输入 API。 你可以在[此处](https://docs.unity3d.com/Manual/xr_input.html)找到有关 XR 输入 API 的详细信息。

移植应用程序并为 HoloLens 2 做好准备后，可以考虑更新交互模型和全息影像设计定位。
在 HoloLens（第 1 代）中，应用程序可能会使用视线和提交交互模型，而全息影像位于相对较远的位置，因此难以放入视场。

更新应用程序设计以使其最适合 HoloLens 2 的步骤如下：
1.  MRTK 组件：根据前期工作，如果已添加 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)，则可以利用已根据 HoloLens 2 进行设计和优化的各种组件/脚本。

2.  交互模型：考虑更新交互模型。 对于大多数方案，我们建议从视线和提交切换为手动。 由于全息影像通常会超出手臂的控制范围，切换为手动可以生成远距交互指向射线和抓取手势。

3.  全息影像的定位：切换到手动交互模型后，请考虑更靠近某些全息影像，以使用近距交互抓取手势直接与全息影像手动交互。 建议靠近的、以便于抓取或交互的全息影像类型包括小目标菜单、控件、按钮，以及在抓取和检查时可放入 HoloLens 2 视场中的小型全息影像。
<br>
应用程序和方案各不相同，我们会根据反馈和经验教训不断改进并发布设计指南。


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>有关将应用程序从 x86 转移到 ARM 的其他注意事项和知识点

- 规整的 Unity 应用程序非常简单，因为你可以生成一个 ARM 应用程序捆绑包，或直接部署到设备，然后该捆绑包即可运行。 某些 Unity 本机插件可能会给开发带来一定的挑战。 因此，必须将所有 Unity 本机插件升级到 Visual Studio 2019，然后针对 ARM 重新生成。

- 某个应用程序使用 Unity AudioKinetic Wwise 插件，但该版本的 Unity 没有 UWP ARM 插件，这导致需要花费大量精力将声音功能重新加入到该应用程序中，才能使该应用在 ARM 上运行。 确保开发计划所需的所有插件都已在 Unity 中安装并可用。

- 在某些情况下，应用所需的插件可能不存在 UWP/ARM 插件，因此无法在 HoloLens 2 上移植和运行应用程序。 请联系插件供应商来解决该问题并提供 ARM 方面的支持。

- 在 HoloLens 2 上，着色器中的 minfloat（和 min16float、minint 等变量）的行为可能与 HoloLens（第 1 代）上的不同。 具体而言，这些行为保证至少使用指定的位数。 在 Intel/Nvidia GPU 上，minfloat 基本上被视为 32 位。 在 ARM 上，实际上会遵循指定的位数。 这意味着，在实践中，这些数字在 HoloLens 2 上的精度或范围可能低于 HoloLens（第 1 代）。

- _asm 指令似乎在 ARM 上无法正常运行，这意味着，必须重写使用 _asm 指令的所有代码。

- ARM 不支持 SIMD 指令集，因为 xmmintrin.h、emmintrin.h、tmmintrin.h 和 immintrin.h 等各种标头在 ARM 上不可用。

- ARM 上的着色器编译器将在加载着色器，或者在着色器所依赖的设置发生更改后，在首次发出绘制调用期间运行，而不是在加载着色器时运行。 对帧速率的影响可能比较明显（具体取决于需要编译的着色器数量），并且会对应当如何在 HoloLens 2 与 HoloLens（第 1 代）上以不同方式处理、打包、更新着色器造成各种影响。

## <a name="see-also"></a>另请参阅

* [安装工具](../install-the-tools.md)
* [MRTK - 安装指南](/windows/mixed-reality/mrtk-unity/install-the-tools)
* [MRTK - 文档主页](/windows/mixed-reality/mrtk-unity)
* [从 HoloToolkit/MRTK 移植到 MRTK 版本 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
* [建议用于 Unity 的设置](../unity/recommended-settings-for-unity.md)
* [了解混合现实的性能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)