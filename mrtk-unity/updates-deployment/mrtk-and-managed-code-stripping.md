---
title: MRTK 和托管代码剥离
description: MRTK 和 Unity 中的代码去除
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143730"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="1d392-104">MRTK 和 Unity 托管代码去除</span><span class="sxs-lookup"><span data-stu-id="1d392-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="1d392-105">使用 Unity 的 IL2CPP 脚本后端 (Unity 2018.4 中是可选的（在 2019 和更高版本[](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)) 中是必需的）时，将发生托管代码去除。</span><span class="sxs-lookup"><span data-stu-id="1d392-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="1d392-106">Unity 的链接器执行此过程以减少二进制大小并减少生成时间。</span><span class="sxs-lookup"><span data-stu-id="1d392-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="1d392-107">混合现实工具包使用文件 来影响 `link.xml` Unity 的链接器处理 MRTK 程序集的过程。</span><span class="sxs-lookup"><span data-stu-id="1d392-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="1d392-108">此文件在 [Unity](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)文档中完整描述，为链接器提供有关在无法推断代码用法时如何保留代码的说明 (例如：通过反射) 。</span><span class="sxs-lookup"><span data-stu-id="1d392-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="1d392-109">作为一个灵活且可自定义的平台，MRTK 在导入时在 中创建文件（如果发现 `link.xml` `Assets/MixedRealityToolkit.Generated` 该文件不存在）。</span><span class="sxs-lookup"><span data-stu-id="1d392-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="1d392-110">不会覆盖link.xml文件。</span><span class="sxs-lookup"><span data-stu-id="1d392-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="1d392-111">建议将 `link.xml` 和 `link.xml.meta` 添加到版本控制。</span><span class="sxs-lookup"><span data-stu-id="1d392-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="1d392-112">开发人员应随意进行自定义 `Assets/MixedRealityToolkit.Generated/link.xml` 以满足项目的需求。</span><span class="sxs-lookup"><span data-stu-id="1d392-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="1d392-113">默认情况下，MRTK link.xml文件将保留以下数据中所示的整个程序集。</span><span class="sxs-lookup"><span data-stu-id="1d392-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

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

<span data-ttu-id="1d392-114">有关文件格式link.xml，请参阅 Unity 文档。</span><span class="sxs-lookup"><span data-stu-id="1d392-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d392-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d392-115">See also</span></span>

- [<span data-ttu-id="1d392-116">Unity：托管代码去除</span><span class="sxs-lookup"><span data-stu-id="1d392-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="1d392-117">Unity：链接 XML 文件</span><span class="sxs-lookup"><span data-stu-id="1d392-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
