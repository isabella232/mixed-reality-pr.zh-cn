---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212237"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 当前没有针对 reprojection 模式的帮助器。 有关详细信息，请参阅其中一个选项卡。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

可以通过将 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) 设置为适当的值，来配置 reprojection 模式。

例如，如果您正在使用严格的正文锁定内容构建 [仅限方向的体验](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度视频内容) ，则只能通过将 reprojection 模式设置为 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)，将其显式设置为 "方向"。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

可以通过将 [HolographicSettings](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 设置为适当的值，来配置 reprojection 模式。

例如，如果您正在使用严格的正文锁定内容构建 [仅限方向的体验](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度视频内容) ，则只能通过将 reprojection 模式设置为 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，将其显式设置为 "方向"。