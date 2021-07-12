---
title: 选择 Unity 版本和 XR 插件
description: 随时了解最新的 Unity 和 XR 插件建议 HoloLens 应用程序开发。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603678"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="49e32-104">选择 Unity 版本和 XR 插件</span><span class="sxs-lookup"><span data-stu-id="49e32-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="49e32-105">尽管我们目前 **建议安装 Unity 2020.3 LTS 以及用于混合现实开发的最新混合现实 OpenXR 插件** ，但你也可以通过其他 Unity 配置来构建应用。</span><span class="sxs-lookup"><span data-stu-id="49e32-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="49e32-106">Unity 2020.3 LTS (建议) </span><span class="sxs-lookup"><span data-stu-id="49e32-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="49e32-107">Microsoft 针对 HoloLens 2 和 Windows Mixed Reality 开发的当前推荐 unity 配置是 **具有最新混合现实 OpenXR 插件的 unity 2020.3 LTS**。</span><span class="sxs-lookup"><span data-stu-id="49e32-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="49e32-108">**必须** 使用 Unity patch release 2020.3.8 f1 或更高版本，以避免在早期的2020.3 版本中出现已知的性能问题。</span><span class="sxs-lookup"><span data-stu-id="49e32-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49e32-109">Unity 2020 不支持 (第一代) HoloLens 目标。</span><span class="sxs-lookup"><span data-stu-id="49e32-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="49e32-110">在 **[unity 2019 LTS](#unity-20194-lts)** 中，这些耳机仍受支持，其中内置内置 XR 用于 UNITY 2019 LTS 2022 到的完整生命周期。</span><span class="sxs-lookup"><span data-stu-id="49e32-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="49e32-111">安装和管理 Unity 的最佳方式是通过 **Unity 中心**：</span><span class="sxs-lookup"><span data-stu-id="49e32-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="49e32-112">安装 <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 中心**</a>。</span><span class="sxs-lookup"><span data-stu-id="49e32-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="49e32-113">选择 " **安装** " 选项卡，然后选择 " **添加**"。</span><span class="sxs-lookup"><span data-stu-id="49e32-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="49e32-114">选择 " **Unity 2020.3 LTS** "，然后单击 " **下一步**"。</span><span class="sxs-lookup"><span data-stu-id="49e32-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Unity 中心安装新版本](images/unity-hub-img-01.png)

4. <span data-ttu-id="49e32-116">检查 **"平台"** 下的以下组件：</span><span class="sxs-lookup"><span data-stu-id="49e32-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="49e32-117">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="49e32-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="49e32-118">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="49e32-118">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="49e32-120">如果你以前安装了 Unity 但没有这些选项，则可以通过 Unity 中心中 **的 "添加模块"** 菜单添加它们：</span><span class="sxs-lookup"><span data-stu-id="49e32-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="49e32-122">安装 Unity 2020.3 后，开始使用混合现实 OpenXR 插件创建项目或升级现有项目：</span><span class="sxs-lookup"><span data-stu-id="49e32-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49e32-123">用 OpenXR 插件设置项目</span><span class="sxs-lookup"><span data-stu-id="49e32-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="49e32-124">尽管我们建议为所有新项目使用 OpenXR，但 Unity 2020.3 LTS 还支持[Windows XR 插件](xr-project-setup.md?tabs=windowsxr)。</span><span class="sxs-lookup"><span data-stu-id="49e32-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="49e32-125">此插件完全受支持，但它不会收到 AR Foundation 4.0 支持等新功能。</span><span class="sxs-lookup"><span data-stu-id="49e32-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="49e32-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="49e32-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="49e32-127">如果需要使用 Unity 2019，可将 **unity 2019 LTS 与旧内置 XR 结合** 使用。</span><span class="sxs-lookup"><span data-stu-id="49e32-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="49e32-128">若要开始处理 Unity 2019.4 LTS 中的旧内置 XR，请单击此处：</span><span class="sxs-lookup"><span data-stu-id="49e32-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49e32-129">设置具有旧内置 XR 的项目</span><span class="sxs-lookup"><span data-stu-id="49e32-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="49e32-130">Unity 已弃用了它在 Unity 2019 中的旧内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="49e32-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="49e32-131">虽然 Unity 2019 提供了新的 XR 插件框架，但 Microsoft 目前并未建议使用 Unity 2019 中的路径，因为 Azure 空间锚与 AR Foundation 2 不兼容。</span><span class="sxs-lookup"><span data-stu-id="49e32-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="49e32-132">在 Unity 2020 中，XR 插件框架支持 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="49e32-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="49e32-133">如果要为 HoloLens (第一代) 开发应用程序，则在 unity 2019 LTS 中，这些耳机仍受支持，其中内置 XR 用于 unity 2019 LTS 2022 到的完整生命周期。</span><span class="sxs-lookup"><span data-stu-id="49e32-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="49e32-134">Unity 2021。2</span><span class="sxs-lookup"><span data-stu-id="49e32-134">Unity 2021.2</span></span>

<span data-ttu-id="49e32-135">如果你正在试用早期 **Unity 2021.2** 生成，请开始处理 [**Mixed Reality OpenXR 插件**](xr-project-setup.md?tabs=openxr)。</span><span class="sxs-lookup"><span data-stu-id="49e32-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="49e32-136">OpenXR 插件是 unity 2021.2 和更高版本中混合现实开发的唯一路径，作为支持 Windows XR 插件的最终 Unity 版本是 Unity 2021.1。</span><span class="sxs-lookup"><span data-stu-id="49e32-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="49e32-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="49e32-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="49e32-138">Unity 2018.4 LTS 已到达 Unity 的两年 Long-Term 支持窗口的末尾，不再接收来自 Unity 的更新，但你的项目将继续运行。</span><span class="sxs-lookup"><span data-stu-id="49e32-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="49e32-139">如果你有一个 Unity 2018 项目，则应考虑计划迁移到 Unity 2020.3 LTS 和 Mixed Reality OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="49e32-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>