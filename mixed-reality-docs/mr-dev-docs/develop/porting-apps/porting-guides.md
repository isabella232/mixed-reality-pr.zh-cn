---
title: 将 VR 应用移植到 Windows Mixed Reality
description: 介绍如何将现有沉浸式应用程序移植到 Windows Mixed Reality 的分步演练。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 端口，unity，unreal，中间件，引擎，UWP，Win32，移植，HoloLens 第一代，混合现实耳机，windows mixed reality 耳机，迁移，Windows 10，输入映射，
ms.openlocfilehash: 9f3e064c4462fc3d12a23bd94885476bcd2f9466
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925951"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>将 VR 应用移植到 Windows Mixed Reality

Windows 10 包括对沉浸式和全息耳机的直接支持。 如果已为其他设备（如 Oculus Rift 或 HTC Naopak）生成内容，这些内容将依赖于操作系统的平台 API 之上的库。 将现有的 Win32 Unity VR 应用引入 Windows Mixed Reality 涉及到重定目标使用特定于供应商的 VR Sdk 到 Unity 的跨供应商 VR Api。

## <a name="porting-requirements"></a>移植要求

在高级别上，迁移现有内容涉及以下步骤：
1. **请确保你的电脑正在运行 Windows 10 秋季创意者更新 (16299) 。** 我们不再建议从有问必答向后跳环接收预览版，因为这些版本对于混合现实开发不是最稳定的。
2. **升级到最新版本的图形或游戏引擎。** 游戏引擎需要支持 Windows 10 SDK 版本 10.0.15063.0 (于2017年4月) 或更高版本发布。
3. **升级任何中间件、插件或组件。** 如果你的应用程序包含任何组件，则最好升级到最新版本。
4. **删除重复的 sdk 依赖项**。 根据你的内容面向哪个设备，你将需要删除或有条件地编译该 SDK (例如 SteamVR) 以便可以改为面向 Windows Api。
5. **处理生成问题。** 此时，迁移练习特定于您的应用程序、您的引擎和您拥有的组件依赖项。

## <a name="common-porting-steps"></a>常见的移植步骤

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. 确保拥有正确的开发硬件

" [安装工具](../install-the-tools.md#immersive-vr-headset-requirements) " 页将列出推荐的开发硬件。

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. 升级到 Windows 10 的最新航班

Windows Mixed Reality 平台仍处于积极开发阶段。 建议 [加入 Windows 预览体验计划](https://insider.windows.com/) ，以访问 "Windows 有问必答 Fast" 航班。
1. 安装 [Windows 10 创意者更新](https://www.microsoft.com/software-download/windows10)
2. [加入](https://insider.windows.com/) Windows 预览体验计划。
3. 启用 [开发人员模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 通过 "**设置" > 更新 & 安全 "部分**，切换到 [Windows 预览体验快速航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. 升级到最新版本的 Visual Studio
* 如果使用的是 Visual Studio，请升级到最新版本
* 请参阅 Visual Studio 2019 下 [的安装工具](../install-the-tools.md#installation-checklist) 页面

### <a name="4-choose-the-correct-adapter"></a>4. 选择正确的适配器
* 在包含两个 Gpu 的笔记本系统中， [针对正确的适配器](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 这适用于 Unity 和本机 DirectX 应用，其中 ID3D11Device 是显式或隐式 (为其功能媒体基础) 创建的。

## <a name="unity-porting-guidance"></a>Unity 移植指南

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal 移植指南

> [!IMPORTANT]
> 如果你使用的是 HP 回音 G2 控制器，请参阅 [此文](../unreal/unreal-reverb-g2-controllers.md) ，了解更多输入映射说明。

## <a name="see-also"></a>另请参阅
* [Windows Mixed Reality 最小电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [了解混合现实的性能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 性能建议](../unity/performance-recommendations-for-unity.md)
* [运动控制器](../../design/motion-controllers.md)
* [Unity 中的手势和运动控制器](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)