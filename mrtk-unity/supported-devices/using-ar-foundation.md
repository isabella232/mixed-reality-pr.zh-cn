---
title: 部署到 Android 和 iOS (AR Foundation) [实验]
description: 在 unity 中配置适用于 Android 和 iOS 的 MRTK (ARFoundation) 文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， AR Core， AR Kit， iOS， IOS， Android， AR Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281947"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a>部署到 Android 和 iOS (AR Foundation) [实验]

## <a name="install-required-packages"></a>安装所需程序包

1. 下载并导入 **Microsoft.MixedReality.Toolkit。Unity.Foundation** 包 [，GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)或 Unity [程序包管理器](../configuration/usingupm.md)

1. 在 Unity 程序包管理器 (UPM) 中，安装以下包：

    **Unity 2018.4.x**

    | **Android** | **iOS** | 注释 |
    | --- | --- | --- |
    | AR Foundation  <br/> 版本：1.5.0 - 预览版 6 | AR Foundation  <br/> 版本：1.5.0 - 预览版 6 | 对于 Unity 2018.4，此包以预览版提供。 查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 插件 <br/> 版本：2.1.2 | ARKit XR 插件 <br/> 版本：2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：2.1.8 |  AR Foundation  <br/> 版本：2.1.8 |
    | ARCore XR 插件 <br/> 版本：2.1.11 | ARKit XR 插件 <br/> 版本：2.1.9 |

    **Unity 2020.3.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：3.1.3 |  AR Foundation  <br/> 版本：4.0.12 |
    | ARCore XR 插件 <br/> 版本：3.1.4 | ARKit XR 插件 <br/> 版本：4.1.7 |

1. 通过调用菜单项更新 MRTK UnityAR 脚本定义：UnityAR > Toolkit >实用工具> **UnityAR >脚本定义**

    ![更新脚本定义](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>启用 Unity AR 相机设置提供程序

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. 选择 **"复制和自定义** "以克隆 MRTK 配置文件以启用自定义配置。

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. 选择 **"相机** 配置文件"旁边的"克隆"。

    ![克隆 MRTK 相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 将"检查器"面板导航到"相机系统"部分，然后展开"相机 **设置提供程序"** 部分。

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. 单击 **"添加设置** 提供程序"，然后展开新 **添加的"新建相机设置"** 条目。

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

1. 在 Unity 生成工具中将平台切换到 Android 或 iOS 设置

1. 确保已启用关联的 XR 插件管理提供程序

    iOS XR 插件管理  ![ ：XR 插件管理 iOS](../features/images/XRManagementiOS.png)

1. 生成并运行场景

## <a name="see-also"></a>另请参阅

- [Unity AR 相机设置](../features/camera-system/unity-ar-camera-settings.md)
