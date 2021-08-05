---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212233"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 将基于 [照相机系统配置文件中的配置](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)自动处理特定相机设置。

**命名空间：** *MixedReality。 Toolkit。CameraSystem*<br>
**类型：** *MixedRealityCameraSystem*

若要检查相机的 opaqueness，MixedRealityCamera 系统具有 [ `IsOpaque` 属性](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。

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