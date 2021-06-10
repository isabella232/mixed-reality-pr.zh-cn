---
title: 眼部追寻 MRTK
description: 用于在 MRTK 中配置 Oculus 寻找的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Oculus 寻找，
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441178"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a>使用 XR SDK 管道构建 MRTK 并将其部署到 Oculus

需要 [Oculus](https://www.oculus.com/quest/) 请求。

MRTK 对 Oculus 的寻找支持通过两个不同的源： Unity 的 XR SDK 管道和 Oculus Integration Unity 包提供。 **OCULUS XRSDK 数据提供程序** 允许同时使用这两个源，并且必须用于在 Oculus 的寻找上部署 MRTK。

[UNITY XR SDK 管道](https://docs.unity3d.com/Manual/XR.html)允许使用 Oculus 触摸控制器和使用 Oculus 寻找进行头跟踪。
此管道是在 Unity 2019.3 和更高版本中开发 XR 应用程序的标准。 若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。 这是将 MRTK 应用程序部署到 Oculus **请求所必需** 的。 

[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许在 Oculus 中使用 **手动跟踪**。 此数据访问接口 **不** 使用 Unity 的 **XR SDK 管道** 或 **旧的 XR 管道**。

## <a name="setting-up-project-for-the-oculus-quest"></a>设置 Oculus 的项目

1. 请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保你的项目已准备好在 Oculus 上部署。

1. 确保在你的设备上启用了 [开发人员模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。 安装 Oculus ADB 驱动程序是可选的。

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>设置用于 Oculus 的 XR SDK 管道

1. 确保 **OCULUS XR 插件** 安装在 " **> 包管理器" 窗口** 中

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. 转到 "**编辑 > 项目设置--> XR 插件" "> 插件提供程序**，确保项目中包含 Oculus 插件提供程序

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
    - 当您选择 " *生成" 并* 首次运行时，您可能会遇到以下生成错误集。 选择 " *生成" 并再次运行* 后，应该能够成功部署。

    ![Oculus 预期生成错误](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. 接受来自接收内部的 " _允许 USB 调试_ " 提示
1. 查看 Oculus 的内部场景

## <a name="removing-oculus-integration-from-the-project"></a>从项目中删除 Oculus 集成

1. 导航到混合现实工具包 > Oculus > 单独的 Oculus 集成 Unity 模块  ![ Oculus 隔离 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. 允许 Unity 刷新为 MixedReality 中的引用，并在此步骤中修改其他文件
1. 关闭 Unity
1. 关闭 Visual Studio （如果它已打开）
1. 打开文件资源管理器并导航到 MRTK Unity 项目的根目录
1. 删除 UnityProjectName/库目录
1. 删除 UnityProjectName/资产/Oculus 目录
1. 删除 UnityProjectName/资产/Oculus 文件
1. 重新打开 Unity

## <a name="common-errors"></a>常见错误

### <a name="quest-not-recognized-by-unity"></a>Unity 无法识别的寻找

请确保正确配置了 Android 路径。 如果继续遇到问题，请遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**> 外部工具 > Android 编辑 > 首选项**

![Android 工具配置](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
