---
title: 眼动跟踪基本设置
description: 如何在 MRTK 中设置目视跟踪
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，眼睛跟踪
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197442"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>MRTK 中的目视跟踪入门

本页介绍如何在应用中设置 Unity MRTK 场景以使用目视跟踪。
下面假设你开始使用全新的新场景。
此外，还可以查看已配置的 [MRTK 目视跟踪示例](../../example-scenes/eye-tracking-examples-overview.md) ，其中包含可直接在上生成的大量极佳示例。

## <a name="eye-tracking-requirements-checklist"></a>目视跟踪要求清单

要使目视跟踪正常工作，必须满足以下要求。
如果你不熟悉 HoloLens 2 上的目视跟踪以及如何在 MRTK 中设置目视跟踪，请不要担心！
接下来，我们将详细介绍如何解决上述每个问题。

1. 必须将 _"眼睛数据提供程序"_ 添加到输入系统。 这从平台提供了目视跟踪数据。
2. 必须在应用程序清单中启用 _"GazeInput"_ 功能。
   **此功能可以在 unity 2019 中进行设置，但在 unity 2018 和更早版本中，此功能仅在 Visual Studio 和通过 MRTK 生成工具提供**
3. 对于当前用户，HoloLens **必须** 进行目视校准。 请查看我们 [的示例，检测用户是否已校准](eye-tracking-is-user-calibrated.md)。

### <a name="a-note-on-the-gazeinput-capability"></a>GazeInput 功能注意事项

MRTK 提供的生成工具 (即混合现实 Toolkit > 实用工具-> 生成窗口) 可以自动为你启用 GazeInput 功能。 要执行此操作，需要确保在 "Appx 生成选项" 选项卡上选中 "注视输入功能"：

![MRTK 生成工具](../../images/eye-tracking/mrtk_et_buildsetup.png)

此工具将在 Unity 生成完成后找到 AppX 清单，并手动添加 GazeInput 功能。
**在 unity 2019 之前，在使用 unity 的内置生成窗口时，此工具不会处于活动状态，** (即 > 版本设置) 。

在 Unity 2019 之前，使用 Unity 的生成窗口时，需要在 Unity 生成后手动添加功能，如下所示：

1. 打开已编译的 Visual Studio 项目，然后在解决方案中打开 _"appxmanifest.xml"_ 。
2. 请确保在 "_功能_" 下勾选 _"GazeInput"_ 复选框。 如果看不到 _"GazeInput"_ 功能，请检查系统是否满足 (使用 Windows SDK 版本) 的 [先决条件](/windows/mixed-reality/develop/install-the-tools)。

_请注意：_ 仅当生成到新的生成文件夹时，才需要执行此操作。
这意味着，如果你已经生成了 Unity 项目并在 appxmanifest.xml 之前设置了该文件，则不需要重新应用所做的更改。

## <a name="setting-up-eye-tracking-step-by-step"></a>逐步设置目视跟踪

### <a name="setting-up-the-scene"></a>设置场景

只需单击 _"Mixed Reality Toolkit-> 配置 ..."_ 即可设置 _MixedRealityToolkit_ 在菜单栏中。

![MRTK 配置](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>设置目视跟踪所需的 MRTK 配置文件

设置 MRTK 场景后，将要求你选择 MRTK 的配置文件。
只需选择 " _DefaultMixedRealityToolkitConfigurationProfile_ "，然后选择 _"复制 & 自定义"_ 选项。

![MRTK 配置文件](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>创建 "眼睛数据提供程序"

- 在 MRTK 配置文件中单击 _"输入"_ 选项卡。
- 若要编辑 ( _"DefaultMixedRealityInputSystemProfile"_ ) 的默认值，请单击其旁边的 _"克隆"_ 按钮。 此时将显示 _"克隆配置文件"_ 菜单。 只需单击该菜单底部的 _"克隆"_ 即可。
- 双击新的输入配置文件，展开 _"输入数据提供程序"_，然后选择 _"+ 添加数据提供程序"_。
- 创建新的数据提供程序：
  - 在 "**类型**" 下，选择 _"Toolkit MixedReality"。WindowsMixedReality "_  ->  _' WindowsMixedRealityEyeGazeDataProvider"_
  - 对于 **平台 (s)** 选择 _"Windows 通用"_。

![MRTK 数据提供程序](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>在 Unity 编辑器中模拟眼睛跟踪

可以在 Unity 编辑器中模拟眼睛跟踪输入，以确保在将应用部署到 HoloLens 2 之前正确触发事件。
只需将相机的位置用作眼睛眼睛，照相机的向前向量为眼睛眼睛，就会模拟眼睛信号。
虽然这对初始测试非常有用，但请注意，这并不是一种快速的模拟。
为此，最好确保频繁测试 HoloLens 2 上的基于目视的交互。

1. **启用模拟的目视跟踪**：
    - 在 MRTK 配置文件中单击 _"输入"_ 选项卡。
    - 在该处导航到 _"输入数据提供程序"_  ->  _"输入模拟服务"_。
    - 克隆 _"DefaultMixedRealityInputSimpulationProfile"_ 以对其进行更改。
    - 选中 _"模拟眼睛位置"_ 复选框。

    ![MRTK 眼睛模拟](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **禁用默认的打印头注视光标**：通常情况下，建议不要显示眼睛眼睛光标，或者确实需要使其变 _得非常_ 微妙。
默认情况下，我们建议隐藏默认情况下连接到 MRTK 注视指针配置文件的默认打印头注视光标。
    - 导航到 MRTK 配置文件 > _"输入"_  ->  _"指针"_
    - 克隆 _"DefaultMixedRealityInputPointerProfile"_ 以对其进行更改。
    - 在 _"指针设置"_ 的顶部，应将不可见的光标 prefab 分配给 _"GazeCursor"_。 为此，可以从 MRTK Foundation 中选择 _"EyeGazeCursor"_ prefab。

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>在注视提供商中启用基于眼睛的注视

在 HoloLens v1 中，打印头用作主指针技术。
尽管仍可通过附加到 [相机](https://docs.unity3d.com/ScriptReference/Camera.html)的 MRTK 中的 _GazeProvider_ 来使用打印头，但你可以通过勾选输入指针配置文件的 "注视" 设置中的 _"IsEyeTrackingEnabled"_ 复选框来进行检查。

>[!NOTE]
>通过更改 _"GazeProvider"_ 的 _"IsEyeTrackingEnabled"_ 属性，开发人员可以在代码中切换基于眼睛的眼睛和头。  

>[!IMPORTANT]
>如果未满足任何目视跟踪要求，应用程序将自动回退到基于头部的注视。

### <a name="accessing-eye-gaze-data"></a>访问目视数据

现在，你的场景已设置为使用目视跟踪，接下来让我们看看如何在脚本中访问它： [通过 EyeGazeProvider 访问目视跟踪数据](eye-tracking-eye-gaze-provider.md) 和 [目视支持的目标选择](eye-tracking-target-selection.md)。

### <a name="testing-your-unity-app-on-a-hololens-2"></a>在 HoloLens 2 上测试 Unity 应用

用目视跟踪生成应用应类似于编译其他 HoloLens 2 MRTK 应用的方式。 请确保已启用 *"注视输入"* 功能，如上文中的 [*GazeInput 功能说明*](#a-note-on-the-gazeinput-capability)部分所述。

#### <a name="eye-calibration"></a>目视校准

最后，请不要忘记通过 HoloLens 2 上的目视校准来运行。
如果没有校准用户，则眼睛跟踪系统不会返回任何输入。
获取校准的最简单方法是向上翻转面板并向下移动。
系统通知应显示欢迎你作为新用户，并要求你完成眼睛校准。
此外，还可以在 "系统设置：设置 > 系统 > 校准" 中找到眼睛校准 > "运行目视校准"。

#### <a name="eye-tracking-permission"></a>目视跟踪权限

首次在 HoloLens 2 上启动应用时，会弹出提示，要求用户提供使用目视跟踪的权限。
如果未显示，则这通常表示未设置 _"GazeInput"_ 功能。

权限提示出现一次后，就不会再次显示。
如果 _"拒绝了目视跟踪权限"_，则可以在设置 > 的隐私 > 应用程序中对此进行重置。

---

这会使你开始在 MRTK Unity 应用中使用目视跟踪。
别忘了查看 [我们的 MRTK 眼跟踪教程和示例，](../../example-scenes/eye-tracking-examples-overview.md) 演示如何使用目视跟踪输入并方便地提供可在项目中重复使用的脚本。

---
[返回 "MixedRealityToolkit" 中的眼睛跟踪](eye-tracking-main.md)