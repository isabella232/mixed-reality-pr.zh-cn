---
title: MRTK 和托管代码剥离
description: MRTK 和 Unity 中的代码剥离
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176291"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK 和托管代码剥离

使用 Unity 的 IL2CPP 脚本后端 (在 Unity 2018.4 中是可选的，在2019和更高版本中是必需的) ，则会发生 [托管代码剥离](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) 。
Unity 的链接器将执行此过程以减小二进制大小并减少生成时间。

混合现实 Toolkit 使用文件 `link.xml` 来影响 Unity 链接器如何处理 MRTK 程序集。 此文件（在 [Unity 的文档](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)中进行了完整说明）为链接器提供了有关如何在无法推断代码时如何保留代码的说明 (ex：通过反射) 使用。

作为一个灵活且可自定义的平台， `link.xml` `Assets/MixedRealityToolkit.Generated` 如果发现该文件不存在，MRTK 将在导入时创建该文件。 不会覆盖预先存在的 link.xml 文件。 建议将 `link.xml` 和 `link.xml.meta` 添加到版本控制中。 开发人员应随意自定义 `Assets/MixedRealityToolkit.Generated/link.xml` 以满足项目需求。

默认情况下，MRTK 创建的 link.xml 文件会保留以下数据中所示的完整程序集。

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

有关 link.xml 文件格式的详细信息，请参阅 Unity 文档。

## <a name="see-also"></a>另请参阅

- [Unity：托管代码剥离](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity：链接 XML 文件](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
