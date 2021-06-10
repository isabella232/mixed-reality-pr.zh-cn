---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748468"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 将基于相机系统配置文件 中的配置自动 [处理特定的相机设置](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)。

**命名空间***：Microsoft.MixedReality.Toolkit.CameraSystem*<br>
**类型***：MixedRealityCameraSystem*

为了检查相机的不透明性，MixedRealityCamera 系统具有 [ `IsOpaque` 属性](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空间***：UnityEngine.XR*<br>
**类型***：XRDisplaySubsystem*

可以使用脚本代码在运行时通过检查主动运行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上的[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html)来确定头戴显示设备是沉浸式还是全息的。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空间***：UnityEngine.XR.WSA*<br>
**类型***：HolographicSettings*

可以使用脚本代码在运行时通过检查 [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴显示设备是沉浸式还是全息。