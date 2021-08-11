---
title: 部署到 Android 和 iOS (AR Foundation) [试验]
description: 用于在 unity 中为 Android 和 iOS (ARFoundation) 配置 MRTK 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，ar Core，ar 工具包，ios，ios，Android，ar Foundation
ms.openlocfilehash: 109241da4137664510aab27094bd508aabaee1d145e387d80da9df259dc730a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196667"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a>部署到 Android 和 iOS (AR Foundation) [试验]

## <a name="install-required-packages"></a>安装所需程序包

1. 下载并导入 **MixedReality Toolkit。unity** 包，从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)或 [unity 程序包管理器](../configuration/usingupm.md)

1. 在 Unity 程序包管理器 (UPM) ，安装以下包：

    **Unity 2018.4.x**

    | **Android** | **iOS** | 注释 |
    | --- | --- | --- |
    | AR Foundation  <br/> 版本： 1.5.0 _ 预览6 | AR Foundation  <br/> 版本： 1.5.0 _ 预览6 | 对于 Unity 2018.4，此包包含为预览版。 查看包： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 插件 <br/> 版本：2.1。2 | ARKit XR 插件 <br/> 版本：2.1。2 | |

    **Unity 2019。4**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：2.1。8 |  AR Foundation  <br/> 版本：2.1。8 |
    | ARCore XR 插件 <br/> 版本：2.1.11 | ARKit XR 插件 <br/> 版本：2.1。9 |

    **Unity 2020。3**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> 版本：3.1。3 |  AR Foundation  <br/> 版本：4.0.12 |
    | ARCore XR 插件 <br/> 版本：3.1。4 | ARKit XR 插件 <br/> 版本：4.1。7 |

1. 通过调用菜单项来更新 MRTK UnityAR 脚本定义：**混合现实 > Toolkit > 实用工具 > UnityAR > 更新脚本定义**

    ![更新脚本定义](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>启用 Unity AR 照相机设置提供程序

以下步骤假定使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置场景层次结构](../features/images/MRTK_ConfiguredHierarchy.png)

1. 选择 " **复制并自定义** "，克隆 MRTK 配置文件以启用自定义配置。

    ![克隆 MRTK 配置文件](../features/images/camera-system/CloneProfileARFoundation.png)

1. 选择照相机配置文件旁边的 " **克隆** "。

    ![克隆 MRTK 照相机配置文件](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. 将检查器面板导航到 "照相机系统" 部分，然后展开 **相机设置提供商** 部分。

    ![展开设置提供程序](../features/images/camera-system/ExpandProviders.png)

1. 单击 "**添加照相机设置提供程序**"，然后展开新添加的 "**照相机设置**" 条目。

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

1. 在 Unity 版本中将平台切换到 Android 或 iOS 设置

1. 确保已启用关联的 XR 插件管理提供程序

    iOS XR 插件管理：  ![ XR 插件管理 ios](../features/images/XRManagementiOS.png)

1. 生成和运行场景

## <a name="see-also"></a>另请参阅

- [Unity AR 照相机设置](../features/camera-system/unity-ar-camera-settings.md)
