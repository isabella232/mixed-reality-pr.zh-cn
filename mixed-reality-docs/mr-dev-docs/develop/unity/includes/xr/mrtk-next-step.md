---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603702"
---
# <a name="openxr"></a>[<span data-ttu-id="8c8ca-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="8c8ca-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="8c8ca-102">若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：</span><span class="sxs-lookup"><span data-stu-id="8c8ca-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c8ca-103">使用 MRTK 设置新的 OpenXR 项目</span><span class="sxs-lookup"><span data-stu-id="8c8ca-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="8c8ca-104">如果要将现有 MRTK 项目升级到 **OpenXR，** 首先需要将 MRTK-Unity 升级到最新版本 (2.7.2 或更高版本) ，以获得与混合现实 OpenXR 插件兼容的关键修补程序。</span><span class="sxs-lookup"><span data-stu-id="8c8ca-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="8c8ca-105">使用 [混合现实功能工具](../../welcome-to-mr-feature-tool.md) 升级到最新版本的 MRTK，然后按照下面的 [手动 OpenXR 设置步骤操作](#manual-setup-without-mrtk)。</span><span class="sxs-lookup"><span data-stu-id="8c8ca-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="8c8ca-106">有关将现有 MRTK 项目迁移到 OpenXR 的更深入的信息，请参阅 [MRTK 文档](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)。</span><span class="sxs-lookup"><span data-stu-id="8c8ca-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="8c8ca-107">从低于 **2.5.3** 的旧版 MRTK 升级时，请确保以下行位于 **Assets/MixedRealityToolkit.Generated/link.xml** 文件中：</span><span class="sxs-lookup"><span data-stu-id="8c8ca-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="8c8ca-108">如果从 MRTK 2.5.4 或更高版本开始，则默认情况下将添加此行。</span><span class="sxs-lookup"><span data-stu-id="8c8ca-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="8c8ca-109">WindowsXR</span><span class="sxs-lookup"><span data-stu-id="8c8ca-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="8c8ca-110">若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：</span><span class="sxs-lookup"><span data-stu-id="8c8ca-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c8ca-111">使用 MRTK Windows XR 项目</span><span class="sxs-lookup"><span data-stu-id="8c8ca-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="8c8ca-112">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="8c8ca-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="8c8ca-113">若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：</span><span class="sxs-lookup"><span data-stu-id="8c8ca-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c8ca-114">使用 MRTK 设置新的旧版 XR 项目</span><span class="sxs-lookup"><span data-stu-id="8c8ca-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)