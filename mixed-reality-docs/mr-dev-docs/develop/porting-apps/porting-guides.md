---
title: 将 VR 应用移植到 Windows Mixed Reality
description: 分步演练，说明如何将现有沉浸式应用程序移植到Windows Mixed Reality。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port， unity， unreal， 中间件， 引擎， UWP， Win32， 移植， HoloLens 第一代， 混合现实头戴显示设备， windows 混合现实头戴显示设备， 迁移， Windows 10， 输入映射，
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213503"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>将 VR 应用移植到 Windows Mixed Reality

Windows 10支持沉浸式和全息头戴显示设备。 如果已针对其他设备（如 Oculus Rift 或）。这些设备依赖于位于操作系统平台 API 上方的库。 将现有的 Win32 Unity VR 应用Windows Mixed Reality涉及将供应商特定的 VR SDK 重新定向到 Unity 的跨供应商 VR API。

## <a name="porting-requirements"></a>移植要求

从较高层面来说，移植现有内容涉及以下步骤：
1. **确保电脑运行 16299 Windows 10 Fall Creators Update (16299) 。** 我们不再建议从 Insider Skip Ahead 环接收预览版本，因为对于混合现实开发，这些生成不是最稳定的。
2. **升级到最新版本的图形或游戏引擎。** 游戏引擎需要支持 Windows 10 SDK 版本 10.0.15063.0 (2017 年 4 月发布的) 或更高版本。
3. **升级任何中间件、插件或组件。** 如果应用包含任何组件，则建议升级到最新版本。
4. **删除重复 SDK 的依赖项**。 根据内容的目标设备，需要删除或有条件地编译出该 SDK，以便可以改为面向Windows API。 这种情况的一个示例是 SteamVR。
5. **解决生成问题。** 此时，移植练习特定于应用、引擎以及你拥有的组件依赖项。

## <a name="common-porting-steps"></a>常见移植步骤

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1.确保具有正确的开发硬件

[VR 友元指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)页列出了推荐的开发硬件。

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2.升级到最新航班Windows 10

Windows Mixed Reality平台仍处于积极开发阶段。 建议[加入 Windows 会员计划](https://insider.windows.com/)以访问"Windows 预览体验成员 - 快"航班。
1. 安装[Windows 10 创意者更新](https://www.microsoft.com/software-download/windows10)
2. [联接](https://insider.windows.com/)Windows 会员计划。
3. 启用 [开发人员模式](/windows/uwp/get-started/enable-your-device-for-development)
4. 通过"更新 [Windows 预览体验成员 - 快安全](/archive/blogs/uktechnet/joining-insider-preview)**设置 >切换到&航班**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3.升级到最新版Visual Studio
* 如果使用的是 Visual Studio，请升级到最新的内部版本
* 请参阅[](../install-the-tools.md#installation-checklist)2019 Visual Studio下的工具页

### <a name="4-choose-the-correct-adapter"></a>4.选择正确的适配器
* 在具有两个 GPU 的笔记本等系统中， [以正确的适配器 为目标](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 这适用于 Unity 和本机 DirectX 应用，其中显式或隐式创建 ID3D11Device (媒体基础) ，用于实现其功能。

## <a name="unity-porting-guidance"></a>Unity 移植指南

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal 移植指南

> [!IMPORTANT]
> 如果使用的是 HP Reverb G2 控制器，请参阅此 [文](../unreal/unreal-reverb-g2-controllers.md) ，获得其他输入映射说明。

## <a name="see-also"></a>另请参阅
* [Windows Mixed Reality电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [了解混合现实的性能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 推荐性能](../unity/performance-recommendations-for-unity.md)
* [运动控制器](../../design/motion-controllers.md)
* [Unity 中的运动控制器](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)