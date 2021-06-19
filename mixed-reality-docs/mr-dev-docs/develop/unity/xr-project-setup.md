---
title: 设置 XR 配置
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity XR 配置建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394561"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="6f407-104">设置 XR 配置</span><span class="sxs-lookup"><span data-stu-id="6f407-104">Setting up your XR configuration</span></span>

<span data-ttu-id="6f407-105">启动新的 Unity 项目时，可以使用三个不同的选项来处理 XR 需求：</span><span class="sxs-lookup"><span data-stu-id="6f407-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="6f407-106">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="6f407-106">OpenXR plugin</span></span>
* <span data-ttu-id="6f407-107">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="6f407-107">Windows XR plugin</span></span>
* <span data-ttu-id="6f407-108">旧 XR 插件</span><span class="sxs-lookup"><span data-stu-id="6f407-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="6f407-109">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="6f407-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="6f407-110">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="6f407-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="6f407-111">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="6f407-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="6f407-112">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="6f407-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6f407-113">试用我们的 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="6f407-113">Try out our MRTK tutorials</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

<span data-ttu-id="6f407-114">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="6f407-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="6f407-115">结合使用 MRTK 与 OpenXR 支持</span><span class="sxs-lookup"><span data-stu-id="6f407-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="6f407-116">MRTK-Unity 2.7 版本为混合现实 OpenXR 插件提供更好的支持。</span><span class="sxs-lookup"><span data-stu-id="6f407-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="6f407-117">再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="6f407-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="6f407-118">OpenXR 支持在 **基础** 包中提供。</span><span class="sxs-lookup"><span data-stu-id="6f407-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="6f407-119">有关 [迁移到 OpenXR 的更深入信息](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，请参阅 MRTK 文档。</span><span class="sxs-lookup"><span data-stu-id="6f407-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="6f407-120">从早于 **2.5.3** 的 MRTK 的早期版本进行升级时，请确保 **资产/MixedRealityToolkit 和 link.xml** 文件中有以下行：</span><span class="sxs-lookup"><span data-stu-id="6f407-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="6f407-121">如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。</span><span class="sxs-lookup"><span data-stu-id="6f407-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="6f407-122">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="6f407-122">Manual setup without MRTK</span></span>

<span data-ttu-id="6f407-123">尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。</span><span class="sxs-lookup"><span data-stu-id="6f407-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]
