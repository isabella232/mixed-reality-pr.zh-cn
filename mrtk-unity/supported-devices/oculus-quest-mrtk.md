---
title: 眼部追寻 MRTK
description: 在 MRTK 中为 Oculus Quest 配置的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Oculus Quest，
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908388"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a>使用 XR SDK 管道生成 MRTK 并部署到 Oculus Quest

需要[Oculus Quest。](https://www.oculus.com/quest/)

MRTK 对 Oculus Quest 的支持通过两个不同的源提供：Unity 的 XR SDK 管道和 Oculus Integration Unity 包。 **Oculus XRSDK 数据提供程序** 允许使用这两个源，并且必须使用 在 Oculus Quest 上部署 MRTK。

Unity [XR SDK 管道](https://docs.unity3d.com/Manual/XR.html) 支持将 Oculus Touch 控制器和头部跟踪与 Oculus Quest 一同使用。
此管道是在 Unity 2019.3 及更中开发 XR 应用程序的标准。 若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。 这是 **将** MRTK 应用程序部署到 Oculus Quest 所需的。

[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许将 **手部跟踪与** Oculus Quest 一起使用。 此数据访问接口 **不使用** Unity 的 **XR SDK 管道** 或 **旧版 XR 管道**。

## <a name="setting-up-project-for-the-oculus-quest"></a>为 Oculus Quest 设置项目

1. 请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保项目已准备好在 Oculus Quest 上部署。

1. 确保在 [设备上启用](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 开发人员模式。 安装 Oculus ADB 驱动程序是可选的。

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>为 Oculus Quest 设置 XR SDK 管道

1. 确保 **Oculus XR 插件** 安装在 **"窗口"--> 程序包管理器**

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. 通过访问"编辑 --> 项目设置 "--> XR 插件管理 --> 插件提供程序，确保 **Oculus 插件提供程序包含在项目中**

    ![Oculus 插件提供程序](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>设置 Oculus Integration Unity 包以启用跟踪

1. 从 Unity [资产存储下载并导入 Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 集成。 经过测试的最新版本为 20.0.0。 可以从此存档[找到旧版本。](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. 导航到集成 Oculus Integration Unity 模块> Oculus >实用工具>混合现实工具包。 这样做会使用相关 Oculus Quest 代码正常运行所需的定义和引用来更新 asmdef。 它还将更新 csc 文件，以筛选出 Oculus 集成资产生成的过时警告。 MRTK 存储库包含将警告转换为错误的 csc 文件，此转换会MRTK-Quest配置过程。

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. 在导入的 Oculus 文件夹 (应位于 Assets/Oculus) ，有一个可编写脚本的对象，名为 OculusProjectConfig。 在配置文件中，需要将 HandTrackingSupport 设置为"控制器和手"。

    ![Oculus 集成控制器和手部](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>设置场景

1. 创建新的 Unity 场景或打开预先存在的场景，例如 HandInteractionExamples。
1. 导航到"混合现实工具包""添加到场景"和"配置"，将 MRTK  >  **添加到场景**。

## <a name="using-the-oculus-xr-sdk-data-provider"></a>使用 Oculus XR SDK 数据提供程序

::: moniker range=">= mrtkunity-2021-05"

1. 将配置文件配置为使用 **Oculus XR SDK 数据提供程序**
    - 如果不打算修改配置文件
        - 使用所有跨 Unity XR 管道配置的默认 MRTK 配置文件。 以前的 DefaultXRSDKConfigurationProfile 现在标记为已过时。
        - 转到" [生成"，将项目部署到 Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。
    - 否则，请执行下列操作：
        - 选择层次结构中的 MixedRealityToolkit 游戏对象，然后选择"复制和自定义"以克隆默认的混合现实配置文件。

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - 选择" **输入** 配置文件"。

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - 在 **输入** 系统配置文件中选择"克隆"以启用修改。

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - 打开"**输入数据提供程序"** 部分，选择顶部的"添加数据提供程序"，将在列表末尾添加新的数据提供程序。  打开新的数据访问接口，将"类型"设置为 **"Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager"。**

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. 将配置文件配置为使用 **Oculus XR SDK 数据提供程序**
    - 如果不打算修改配置文件
        - 将配置文件更改为 DefaultXRSDKConfigurationProfile。
        - 转到" [生成"，将项目部署到 Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。
    - 否则，请执行下列操作：
        - 选择层次结构中的 MixedRealityToolkit 游戏对象，然后选择"复制和自定义"以克隆默认的混合现实配置文件。

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - 选择" **输入** 配置文件"。

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - 在 **输入** 系统配置文件中选择"克隆"以启用修改。

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - 打开"**输入数据提供程序"** 部分，选择顶部的"添加数据提供程序"，将在列表末尾添加新的数据提供程序。  打开新的数据访问接口，将"类型"设置为 **"Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager"。**

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. Oculus XR SDK 数据提供程序包括一个 OVR 相机设备预制器，它使用 OVR 相机设备以及 OVR 手自动配置项目，以正确路由输入。 手动将 OVR 相机设备添加到场景中需要手动配置设置和输入。

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>生成项目并部署到 Oculus Quest

1. 通过 USB 3.0 -> USB C 电缆插入 Oculus Quest
1. 导航到 **"文件>生成设置"**
1. 将部署更改为 **Android**
1. 确保选择 Oculus Quest 作为适用的运行设备

    ![Oculus 运行设备](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. 选择"生成并运行"
    - 首次选择"生成并运行"时，可能会遇到以下一组 *生成错误* 。 再次选择"生成并运行"后，应该能够 *成功* 部署。

    ![Oculus 预期生成错误](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. 从 _任务内部接受"允许 USB_ 调试"提示
1. 在 Oculus 任务中查看场景

## <a name="removing-oculus-integration-from-the-project"></a>从项目中删除 Oculus 集成

1. 导航到混合现实工具包 > Oculus >独立 Oculus Integration Unity 模块  ![ Oculus 分离 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. 在此步骤中，将修改 Unity 作为 Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef 和其他文件中的引用进行刷新
1. 关闭 Unity
1. 关闭Visual Studio（如果已打开）
1. 打开文件资源管理器并导航到 MRTK Unity 项目的根目录
1. 删除 UnityProjectName/Library 目录
1. 删除 UnityProjectName/Assets/Oculus 目录
1. 删除 UnityProjectName/Assets/Oculus.meta 文件
1. 重新打开 Unity

## <a name="common-errors"></a>常见错误

### <a name="quest-not-recognized-by-unity"></a>Unity 无法识别的探索

请确保正确配置 Android 路径。 如果仍然遇到问题，请遵循 [本指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**在 Android >外部>编辑>首选项**

![Android 工具配置](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
