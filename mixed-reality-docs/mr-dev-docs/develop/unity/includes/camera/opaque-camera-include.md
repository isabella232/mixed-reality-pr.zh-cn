---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636264"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 将基于 [照相机系统配置文件中的配置](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)自动处理特定相机设置。

**命名空间：** *MixedReality. CameraSystem*<br>
**类型：** *MixedRealityCameraSystem*

若要检查相机的 opaqueness，MixedRealityCamera 系统具有 [ `IsOpaque` 属性](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空间：** *UnityEngine. XR*<br>
**类型：** *XRDisplaySubsystem*

你可以使用脚本代码来确定在运行时，耳机是沉浸式还是全息的，因为在主动运行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上检查[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空间：** *UnityEngine. XR*<br>
**类型：** *HolographicSettings*

您可以使用脚本代码，通过检查 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴式耳机是沉浸还是全息。