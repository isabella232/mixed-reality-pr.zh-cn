---
title: UsingARFoundation
description: 在 unity 中使用 ARFoundation 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， AR Core， AR 工具包
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852333"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>如何为 iOS 和 Android 配置 MRTK [实验]

## <a name="install-required-packages"></a>安装所需程序包

1. 从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 Unity 页面下载并导入 **Microsoft.MixedReality.Toolkit.Unity.Foundation** [程序包管理器](../configuration/usingupm.md)

1. 在 Unity 程序包管理器 (UPM) 中，安装以下包：

    **Unity 2018.4.x**

    | **Android** | **iOS** | 注释 |
    | --- | --- | --- |
    | AR Foundation  <br/> 版本：1.5.0 - 预览版 6 | AR Foundation  <br/> 版本：1.5.0 - 预览版 6 | 对于 Unity 2018.4，此包以预览版提供。 查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 插件 <br/> 版本：2.1.2 | ARKit XR 插件 <br/> 版本：2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：2.1.8 |  AR Foundation  <br/> 版本：2.1。8 |
    | ARCore XR 插件 <br/> 版本：2.1.11 | ARKit XR 插件 <br/> 版本：2.1。9 |

    **目前尚不支持 Unity 2020.1 (，仅包含在信息中)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：3.1。3 |  AR Foundation  <br/> 版本：3.1。3 |
    | ARCore XR 插件 <br/> 版本：3.1。4 | ARKit XR 插件 <br/> 版本：3.1。3 |

1. 通过调用菜单项来更新 MRTK UnityAR 脚本定义： **混合现实工具包 > 实用程序 > UnityAR > 更新脚本定义**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>启用 Unity AR 照相机设置提供程序

以下步骤假定使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. 选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. 选择 **"相机** 配置文件"旁边的"克隆"。

    ![克隆 MRTK 相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 将"检查器"面板导航到"相机系统"部分，然后展开" **相机设置提供程序"** 部分。

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. 单击 **"添加相机设置提供程序"，** 然后展开新 **添加的"新建相机设置"** 条目。

    ![展开新设置提供程序](../features/images/camera-system/ExpandNewProvider.png)

1. 选择 Unity AR 相机设置提供程序

    ![选择 Unity AR 设置提供程序](../features/images/camera-system/SelectUnityArSettings.png)

    有关配置 Unity AR 相机设置提供程序的信息，请参阅 [Unity AR 相机设置提供程序](../features/camera-system/unity-ar-camera-settings.md)。

> [!NOTE]
> 当应用程序 (AR Foundation 组件) 时，此安装会检查其运行状况。 如果没有，则会自动添加它们，使其与 ARCore 和 ARKit 一同使用。
> 如果需要设置特定行为，应自己添加所需的组件。
> 有关 AR Foundation 组件和安装的信息，请查看 [此文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。

## <a name="building-a-scene-for-android-and-ios-devices"></a>生成适用于 Android 和 iOS 设备的场景

1. 确保已将 UnityAR 相机设置提供程序添加到场景中。

1. 在 Unity 生成设置中将平台切换到 Android 或 iOS

    切换平台时，应会看到具有所选平台设置的 MRTK 项目配置器窗口。  单击"应用"以启用特定于平台的设置。

    iOS 项目配置器设置

    ![iOS 项目配置器](../features/images/camera-system/MRTKProjectConfigurator.png)

1. 切换适用于 Android 的平台后，不需要执行其他步骤。

1. 如果该平台为 iOS，请在 "优化" 标头下编辑 > 项目设置 > Player > 其他设置 "，然后 **取消选中** " 剥离引擎代码 "

    ![iOS 设置](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > 取消选中块代码是 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)中错误的短期解决方案。  我们正在致力于长期解决方案。

1. 生成和运行场景

## <a name="see-also"></a>另请参阅

- [Unity AR 照相机设置](../features/camera-system/unity-ar-camera-settings.md)
