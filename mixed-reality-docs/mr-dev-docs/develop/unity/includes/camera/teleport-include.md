---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748523"
---
# <a name="mrtk"></a>[<span data-ttu-id="baeaf-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="baeaf-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="baeaf-102">MRTK 提供了一个内置的 [传送系统](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) ，该系统可在所表述的双手和控制器之间自动运行。</span><span class="sxs-lookup"><span data-stu-id="baeaf-102">MRTK provides an in-box [teleport system](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="baeaf-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="baeaf-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="baeaf-104">建议使用 MRTK 的 teleportation 实现。</span><span class="sxs-lookup"><span data-stu-id="baeaf-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="baeaf-105">如果选择不使用 MRTK，Unity 将在 [XR 交互工具包](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)中提供 teleportation 实现。</span><span class="sxs-lookup"><span data-stu-id="baeaf-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="baeaf-106">如果你选择自行实现，请记住，你不能直接移动相机。</span><span class="sxs-lookup"><span data-stu-id="baeaf-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="baeaf-107">由于 Unity 控制用于头跟踪的照相机，你需要在层次结构中为相机提供父项并改为移动该 GameObject。</span><span class="sxs-lookup"><span data-stu-id="baeaf-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="baeaf-108">这等效于 MRTK 的 Playspace。</span><span class="sxs-lookup"><span data-stu-id="baeaf-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="baeaf-109">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="baeaf-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="baeaf-110">建议使用 MRTK 的 teleportation 实现。</span><span class="sxs-lookup"><span data-stu-id="baeaf-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="baeaf-111">如果你选择自行实现，请记住，你不能直接移动相机。</span><span class="sxs-lookup"><span data-stu-id="baeaf-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="baeaf-112">由于 Unity 控制用于头跟踪的照相机，你需要在层次结构中为相机提供父项并改为移动该 GameObject。</span><span class="sxs-lookup"><span data-stu-id="baeaf-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="baeaf-113">这等效于 MRTK 的 Playspace。</span><span class="sxs-lookup"><span data-stu-id="baeaf-113">This is the equivalent of MRTK's Playspace.</span></span>