---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748523"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 提供了一个内置的 [传送系统](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) ，该系统可在所表述的双手和控制器之间自动运行。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

建议使用 MRTK 的 teleportation 实现。
如果选择不使用 MRTK，Unity 将在 [XR 交互工具包](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)中提供 teleportation 实现。
如果你选择自行实现，请记住，你不能直接移动相机。 由于 Unity 控制用于头跟踪的照相机，你需要在层次结构中为相机提供父项并改为移动该 GameObject。 这等效于 MRTK 的 Playspace。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

建议使用 MRTK 的 teleportation 实现。
如果你选择自行实现，请记住，你不能直接移动相机。 由于 Unity 控制用于头跟踪的照相机，你需要在层次结构中为相机提供父项并改为移动该 GameObject。 这等效于 MRTK 的 Playspace。