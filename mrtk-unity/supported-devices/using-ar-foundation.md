---
title: 使用 AR Foundation
description: 在 unity 中使用 ARFoundation 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，AR Core，AR 工具包
ms.openlocfilehash: 1c39950e8b64968e182ddc551ef344dee42060e9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143944"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>如何配置适用于 iOS 和 Android 的 MRTK [实验]

## <a name="install-required-packages"></a>安装所需程序包

1. 从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [Unity 包管理器](../configuration/usingupm.md)下载并导入 **MixedReality** 包

1. 在 Unity 包管理器 (UPM) 中，安装以下包：

    **Unity 2018.4.x**

    | **Android** | **iOS** | 注释 |
    | --- | --- | --- |
    | AR Foundation  <br/> 版本： 1.5.0 _ 预览6 | AR Foundation  <br/> 版本： 1.5.0 _ 预览6 | 对于 Unity 2018.4，此包包含为预览版。 查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 插件 <br/> 版本：2.1。2 | ARKit XR 插件 <br/> 版本：2.1。2 | |

    **Unity 2019。4**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：2.1。8 |  AR Foundation  <br/> 版本：2.1。8 |
    | ARCore XR 插件 <br/> 版本：2.1.11 | ARKit XR 插件 <br/> 版本：2.1.9 |

    **Unity 2020.1.x (目前不受正式支持，仅出于信息目的包含在)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：3.1.3 |  AR Foundation  <br/> 版本：3.1.3 |
    | ARCore XR 插件 <br/> 版本：3.1.4 | ARKit XR 插件 <br/> 版本：3.1.3 |

1. 通过调用菜单项更新 MRTK UnityAR 脚本定义：混合现实工具包 > 实用工具 > **UnityAR >更新脚本定义**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>启用 Unity AR 相机设置提供程序

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. 选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. 选择照相机配置文件旁边的 " **克隆** "。

    ![克隆 MRTK 照相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 将检查器面板导航到 "照相机系统" 部分，然后展开 " **照相机设置提供程序** " 部分。

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. 单击 " **添加照相机设置提供程序** "，然后展开新添加的 " **相机设置** " 条目。

    ![展开新的设置提供程序](../features/images/camera-system/ExpandNewProvider.png)

1. 选择 Unity AR 照相机设置提供程序

    ![选择 Unity AR 设置提供程序](../features/images/camera-system/SelectUnityArSettings.png)

    有关配置 Unity AR 照相机设置提供程序的详细信息： [UNITY ar 照相机设置提供程序](../features/camera-system/unity-ar-camera-settings.md)。

> [!NOTE]
> 当应用程序启动时，此安装检查 () 如果 AR 基础组件在场景中。 否则，会自动添加它们以使其与 ARCore 和 ARKit 一起使用。
> 如果需要设置特定行为，你应该自行添加所需的组件。
> 有关 AR Foundation 组件和安装的详细信息，请查看此 [文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。

## <a name="building-a-scene-for-android-and-ios-devices"></a>构建适用于 Android 和 iOS 设备的场景

1. 请确保已将 UnityAR 照相机设置提供程序添加到场景中。

1. 在 Unity 生成设置中将平台切换到 Android 或 iOS

    切换平台时，应会看到 "MRTK 项目配置器" 窗口，其中包含所选平台的设置。  单击 "应用" 以启用特定于平台的设置。

    iOS 项目配置器设置

    ![iOS 项目配置器](../features/images/camera-system/MRTKProjectConfigurator.png)

1. 切换适用于 Android 的平台后，无需执行其他步骤。

1. 如果平台为 iOS，请>">播放器">"其他设置"下，取消选中"条 **带引擎代码** "

    ![iOS 设置](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > 取消选中"带状引擎代码"是 Xcode 中错误的短期[#6646。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)  我们正在努力解决长期问题。

1. 生成并运行场景

## <a name="see-also"></a>另请参阅

- [Unity AR 相机设置](../features/camera-system/unity-ar-camera-settings.md)
