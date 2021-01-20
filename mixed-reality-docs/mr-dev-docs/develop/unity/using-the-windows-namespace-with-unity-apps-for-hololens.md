---
title: 用于 HoloLens 的适用于 Unity 的 WinRT Api
description: Leanr 如何在适用于 HoloLens 的 Unity 混合现实项目中使用 WinRT Api 和 Windows 命名空间。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，演练，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，混合现实 Api
ms.openlocfilehash: 2116f0025449fdf127998e605f87de456e9bdaf9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583551"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>用于 HoloLens 的适用于 Unity 的 WinRT Api

本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。

## <a name="mixed-reality-apis"></a>混合现实 Api

已在 .NET Standard 2.0 兼容的投影中提供 Windows SDK 的混合现实重点，你可以在不带预处理器指令的项目中使用。 Windows 中的大多数 Api。 感知和 Windows UI. Input 命名空间包括在内，并且可能会在将来扩展以包含其他 Api。 在编辑器中运行时，可以使用投影的 Api，这允许使用 [播放模式](//windows/mixed-reality/unity-play-mode)。 若要使用此投影，请对项目进行以下修改：

1) 使用[NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity)添加对[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 包的引用。
2) 命名空间的前缀引用 `Windows` 包含 `Microsoft.` ：
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) 将本机指针转换替换为 `FromNativePtr` ：
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>有条件地包含 WinRT API 调用

还可以通过使用预处理器指令，在为通用 Windows 平台和 Xbox one 平台构建的 Unity 项目中使用 WinRT Api。 在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。 

这可以通过 Unity 中的两个步骤完成：
1) API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**
    - **编辑**  > **项目设置**  > **播放器**  > **配置**  > **Api 兼容级别** 到 **.net 4.6** 或 **.NET Standard 2.0**
2) 必须围绕任何 WinRT 利用代码包装预处理器指令 **ENABLE_WINMD_SUPPORT**

以下代码片段来自 Unity 手动页，适用于 [c # 脚本中通用 Windows 平台： WINRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。 在此示例中，将返回一个广告 ID，但只能在 UWP 和 Xbox one build 上生成：

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>在 Unity c # 项目中编辑脚本

双击 Unity 编辑器中的脚本时，默认情况下，该脚本将在编辑器项目中启动。 WinRT Api 将显示为 "未知"，因为 Visual Studio 项目不引用 Windows 运行时。 在将项目生成到 UWP Visual Studio 解决方案之前，将忽略 **ENABLE_WINMD_SUPPORT** 指令，并忽略任何 *#if* 包装的代码。

## <a name="see-also"></a>另请参阅
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 运行时支持 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)