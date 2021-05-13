---
title: OculusQuestMRTK
description: 在 MRTK 中为 Oculus Quest 配置的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Oculus Quest，
ms.openlocfilehash: 9350ed7c8426c3bb31cf41493056fb6fc1e26107
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852336"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a>如何使用 XR SDK 管道在 MRTK 中配置 Oculus Quest

需要[Oculus Quest。](https://www.oculus.com/quest/)

MRTK 对 Oculus Quest 的支持通过两个不同的源提供：Unity 的 XR 管道和 Oculus Integration Unity 包。 **Oculus XRSDK 数据提供程序** 允许使用这两个源，并且必须用于在 Oculus Quest 上使用 MRTK。

Unity [的 XR 管道](https://docs.unity3d.com/Manual/XR.html) 支持将 Oculus Touch 控制器和头部跟踪与 Oculus Quest 一同使用。
此管道是在 Unity 2019.3 及更中开发 XR 应用程序的标准。 若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。

[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许将 **手部跟踪与** Oculus Quest 一起使用。
此数据访问接口不使用Unity 的 **XR** 管道或旧版 **XR** 管道，但由于控制器和头跟踪由 Unity 的 XR 管道处理，因此，必须遵循为 **Oculus Quest** 设置项目中的步骤，以确保使用的是 **XR 管道**，而不是要弃用的旧 **XR 管道**。

## <a name="setting-up-project-for-the-oculus-quest"></a>为 Oculus Quest 设置项目

1. 请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保项目已准备好在 Oculus Quest 上部署。

1. 确保在 [设备上启用](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 开发人员模式。 安装 Oculus ADB 驱动程序是可选的。

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>为 Oculus Quest 设置 XR 管道

1. 确保 **Oculus XR 插件** 安装在 **"窗口"--> 程序包管理器**

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. 通过访问"编辑 --> 项目设置 "--> XR 插件管理 --> 插件提供程序，确保 **Oculus 插件提供程序包含在项目中**

    ![Oculus 插件提供程序](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>设置 Oculus Integration Unity 包以启用 handtracking

1. 从 Unity 资产存储中下载并导入 [Oculus 集成](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。 已测试的最新版本为20.0.0。 可以从此[存档](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到旧版本

1. 导航到混合现实工具包 > 实用程序 > Oculus > 集成 Oculus Integration Unity 模块。 执行此操作将更新 asmdefs，其中包含相关 Oculus 获取代码运行所需的定义和引用。 它还将更新 csc 文件，以筛选出 Oculus 集成资产生成的过时警告。 MRTK 存储库包含将警告转换为错误的 csc 文件，此转换会暂停 MRTK-Quest 配置过程。

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. 在导入的 Oculus 文件夹中 (应在资产/Oculus) 中找到该文件夹，这是一个名为 OculusProjectConfig 的可编写脚本的对象。 在该配置文件中，需要将 HandTrackingSupport 设置为 "控制器和手"。

    ![Oculus Integration 控制器和指针](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>设置场景

1. 创建新的 Unity 场景或打开预先存在的场景，如 HandInteractionExamples
1. 通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景

## <a name="using-the-oculus-xr-sdk-data-provider"></a>使用 Oculus XR SDK 数据提供程序

1. 将配置文件配置为使用 **OCULUS XR SDK 数据提供程序**
    - 如果不打算修改配置文件
        - 将配置文件更改为 DefaultXRSDKConfigurationProfile，然后转到 [生成项目并将其部署到 Oculus 的寻找](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - 否则，请执行以下操作：
        - 选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - 选择 **输入** 配置文件

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - 选择输入系统配置文件中的 " **克隆** " 以启用修改。

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - 打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据提供程序** "，新的数据访问接口将添加到列表的末尾。  打开新的数据提供程序并将 **类型** 设置为 **MixedReality. Oculus > OculusXRSDKDeviceManager**

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. Oculus XR SDK 数据提供程序包括一个 OVR 相机远程处理 Prefab，它自动使用 OVR 相机 Rig 配置项目，并使用 OVR 来正确路由输入。 手动将 OVR 摄像装置添加到场景需要手动配置设置和输入。

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>生成项目并将其部署到 Oculus 的寻找

1. 通过 USB 3.0 > USB C 线插入 Oculus 寻找
1. 导航到 **文件 > 生成设置**
1. 将部署更改为 **Android**
1. 确保选择 "Oculus" 作为适用的运行设备

    ![Oculus 运行设备](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. 选择生成并运行
    - 当您选择 " *生成" 并* 首次运行时，您可能会遇到以下生成错误集。 再次选择"生成并运行"后，应该能够 *成功* 部署。

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
