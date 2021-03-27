---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636263"
---
# <a name="mrtk"></a>[<span data-ttu-id="51ff4-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="51ff4-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="51ff4-102">MRTK 当前没有针对 reprojection 模式的帮助器。</span><span class="sxs-lookup"><span data-stu-id="51ff4-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="51ff4-103">有关详细信息，请参阅其中一个选项卡。</span><span class="sxs-lookup"><span data-stu-id="51ff4-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="51ff4-104">XR SDK</span><span class="sxs-lookup"><span data-stu-id="51ff4-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="51ff4-105">可以通过将 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) 设置为适当的值，来配置 reprojection 模式。</span><span class="sxs-lookup"><span data-stu-id="51ff4-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="51ff4-106">例如，如果您正在使用严格的正文锁定内容构建 [仅限方向的体验](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度视频内容) ，则只能通过将 reprojection 模式设置为 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)，将其显式设置为 "方向"。</span><span class="sxs-lookup"><span data-stu-id="51ff4-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="51ff4-107">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="51ff4-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="51ff4-108">可以通过将 [HolographicSettings](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 设置为适当的值，来配置 reprojection 模式。</span><span class="sxs-lookup"><span data-stu-id="51ff4-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="51ff4-109">例如，如果您正在使用严格的正文锁定内容构建 [仅限方向的体验](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度视频内容) ，则只能通过将 reprojection 模式设置为 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，将其显式设置为 "方向"。</span><span class="sxs-lookup"><span data-stu-id="51ff4-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>