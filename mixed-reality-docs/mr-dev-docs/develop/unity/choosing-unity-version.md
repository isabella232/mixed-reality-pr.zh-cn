---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080694"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="c3658-104">选择 Unity 版本和 XR 插件</span><span class="sxs-lookup"><span data-stu-id="c3658-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="c3658-105">虽然我们目前建议安装具有用于混合现实开发的最新混合现实 OpenXR 插件的 **Unity 2020.3 LTS，** 但也可使用其他 Unity 配置生成应用。</span><span class="sxs-lookup"><span data-stu-id="c3658-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="c3658-106">Unity 2020.3 LTS (建议) </span><span class="sxs-lookup"><span data-stu-id="c3658-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="c3658-107">Microsoft 当前推荐的用于 HoloLens 2 Windows Mixed Reality 的 Unity 配置是具有最新混合现实 OpenXR 插件 的 **Unity 2020.3 LTS。**</span><span class="sxs-lookup"><span data-stu-id="c3658-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="c3658-108">必须使用 Unity 修补程序版本 2020.3.8f1 或更高版本，以避免 2020.3 早期版本的已知性能问题。</span><span class="sxs-lookup"><span data-stu-id="c3658-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3658-109">Unity 2020 不支持将 HoloLens (第一代) 。</span><span class="sxs-lookup"><span data-stu-id="c3658-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="c3658-110">在 Unity 2019 LTS 的整个生命周期（到 2022 年年中）中，具有旧版内置 XR 的 **[Unity 2019 LTS](#unity-20194-lts)** 仍支持这些头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="c3658-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="c3658-111">Azure 远程渲染尚未发布支持 Unity 2020 的更新版本。</span><span class="sxs-lookup"><span data-stu-id="c3658-111">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="c3658-112">如果 Unity 项目使用 Azure 远程渲染，建议在更新的包可用之前，继续将项目升级到 Unity 2020。</span><span class="sxs-lookup"><span data-stu-id="c3658-112">If your Unity project uses Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until an updated package is available.</span></span>

<span data-ttu-id="c3658-113">最好通过 Unity Hub 安装和管理 Unity。</span><span class="sxs-lookup"><span data-stu-id="c3658-113">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="c3658-114">安装后，打开 Unity 中心：</span><span class="sxs-lookup"><span data-stu-id="c3658-114">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="c3658-115">选择" **安装"选项卡** ，然后选择" **添加"**</span><span class="sxs-lookup"><span data-stu-id="c3658-115">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="c3658-116">选择 Unity 2020.3 LTS，然后单击"下一 **步"**</span><span class="sxs-lookup"><span data-stu-id="c3658-116">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity 中心安装新版本](images/unity-hub-img-01.png)

3. <span data-ttu-id="c3658-118">检查"平台" **下的以下组件**</span><span class="sxs-lookup"><span data-stu-id="c3658-118">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="c3658-119">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="c3658-119">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="c3658-120">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="c3658-120">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="c3658-122">如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：</span><span class="sxs-lookup"><span data-stu-id="c3658-122">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3658-124">使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c3658-124">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="c3658-125">虽然我们建议将 OpenXR 用于所有新项目，但 Unity 2020.3 LTS 也支持 [Windows XR 插件](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)。</span><span class="sxs-lookup"><span data-stu-id="c3658-125">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="c3658-126">虽然此插件不会获得 AR Foundation 4.0 支持等新功能，但完全受支持。</span><span class="sxs-lookup"><span data-stu-id="c3658-126">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="c3658-127">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="c3658-127">Unity 2019.4 LTS</span></span>

<span data-ttu-id="c3658-128">如果需要使用 Unity 2019，可以将 Unity **2019 LTS 与旧版内置 XR 一起使用**。</span><span class="sxs-lookup"><span data-stu-id="c3658-128">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="c3658-129">若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：</span><span class="sxs-lookup"><span data-stu-id="c3658-129">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3658-130">设置旧版内置 XR</span><span class="sxs-lookup"><span data-stu-id="c3658-130">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="c3658-131">自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="c3658-131">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="c3658-132">虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。</span><span class="sxs-lookup"><span data-stu-id="c3658-132">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="c3658-133">在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="c3658-133">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="c3658-134">如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。</span><span class="sxs-lookup"><span data-stu-id="c3658-134">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="c3658-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="c3658-135">Unity 2021.1</span></span>

<span data-ttu-id="c3658-136">如果要尝试早期 Unity **2021.1** 版本，应前进到 **OpenXR** 插件，因为 Windows XR 插件已弃用。</span><span class="sxs-lookup"><span data-stu-id="c3658-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="c3658-137">从 Unity 2021.2 开始，OpenXR 插件将是混合现实开发的唯一路径，因为将不再支持 Windows XR 插件。</span><span class="sxs-lookup"><span data-stu-id="c3658-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="c3658-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="c3658-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="c3658-139">如果已有一个使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受支持 2 年。</span><span class="sxs-lookup"><span data-stu-id="c3658-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="c3658-140">Unity 2018 LTS 将于 2021 年春季终止服务。</span><span class="sxs-lookup"><span data-stu-id="c3658-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
