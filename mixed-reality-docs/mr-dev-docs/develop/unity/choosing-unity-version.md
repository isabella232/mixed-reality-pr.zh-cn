---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394404"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="5c054-104">选择 Unity 版本和 XR 插件</span><span class="sxs-lookup"><span data-stu-id="5c054-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="5c054-105">虽然我们 **目前建议安装 Unity 2019.4 LTS，** 以及使用旧版内置 XR 进行混合现实开发，但也可使用其他 Unity 配置生成应用。</span><span class="sxs-lookup"><span data-stu-id="5c054-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="5c054-106">Unity 2019.4 LTS (建议) </span><span class="sxs-lookup"><span data-stu-id="5c054-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="5c054-107">Microsoft 当前推荐的用于 HoloLens 2 和 Windows Mixed Reality 的 Unity 配置是使用旧版内置 XR 支持的 **Unity 2019.4 LTS。**</span><span class="sxs-lookup"><span data-stu-id="5c054-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="5c054-108">安装和管理 Unity 的最佳方式是通过 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>。</span><span class="sxs-lookup"><span data-stu-id="5c054-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="5c054-109">安装后，打开 Unity 中心：</span><span class="sxs-lookup"><span data-stu-id="5c054-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="5c054-110">选择" **安装"选项卡** ，然后选择" **添加"**</span><span class="sxs-lookup"><span data-stu-id="5c054-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="5c054-111">选择"Unity 2019.4 LTS"，然后单击"下一 **步"**</span><span class="sxs-lookup"><span data-stu-id="5c054-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 中心安装新版本](images/unity-hub-img-2019.png)

3. <span data-ttu-id="5c054-113">检查"平台" **下的以下组件**</span><span class="sxs-lookup"><span data-stu-id="5c054-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="5c054-114">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="5c054-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="5c054-115">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="5c054-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平台生成支持选项](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="5c054-117">如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：</span><span class="sxs-lookup"><span data-stu-id="5c054-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 生成支持选项](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="5c054-119">若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：</span><span class="sxs-lookup"><span data-stu-id="5c054-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5c054-120">设置旧版内置 XR</span><span class="sxs-lookup"><span data-stu-id="5c054-120">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="5c054-121">自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="5c054-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="5c054-122">虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。</span><span class="sxs-lookup"><span data-stu-id="5c054-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="5c054-123">在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="5c054-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="5c054-124">如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。</span><span class="sxs-lookup"><span data-stu-id="5c054-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="5c054-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="5c054-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="5c054-126">如果使用的是 Unity **2020.3 LTS，Microsoft** 的当前建议是最新的 **混合现实 OpenXR 插件**。</span><span class="sxs-lookup"><span data-stu-id="5c054-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="5c054-127">必须使用 Unity 修补程序版本 2020.3.8f1 或更高版本，以避免 2020.3 早期版本的已知性能问题。</span><span class="sxs-lookup"><span data-stu-id="5c054-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="5c054-128">混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。</span><span class="sxs-lookup"><span data-stu-id="5c054-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="5c054-129">这样，你可以编写命中测试代码一次，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。</span><span class="sxs-lookup"><span data-stu-id="5c054-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="5c054-130">但是，有一些已知问题会影响 Unity 2020 LTS 项目：</span><span class="sxs-lookup"><span data-stu-id="5c054-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="5c054-131">URP (URP) 10.5.0 或HoloLens 2性能下降。</span><span class="sxs-lookup"><span data-stu-id="5c054-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="5c054-132">如果选择在 Unity 2020 中立即开始新项目，请务必在交付应用之前，跟进未来几周更新的 Unity 生成和 URP 包。</span><span class="sxs-lookup"><span data-stu-id="5c054-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="5c054-133">这将确保用户获得适当的全息影像稳定性。</span><span class="sxs-lookup"><span data-stu-id="5c054-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5c054-134">使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="5c054-134">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="5c054-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="5c054-135">Unity 2021.1</span></span>

<span data-ttu-id="5c054-136">如果要尝试早期 Unity **2021.1** 版本，应前进到 **OpenXR** 插件，因为 Windows XR 插件已弃用。</span><span class="sxs-lookup"><span data-stu-id="5c054-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="5c054-137">从 Unity 2021.2 开始，OpenXR 插件将是混合现实开发的唯一路径，因为将不再支持 Windows XR 插件。</span><span class="sxs-lookup"><span data-stu-id="5c054-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="5c054-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="5c054-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="5c054-139">如果已有一个使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受支持 2 年。</span><span class="sxs-lookup"><span data-stu-id="5c054-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="5c054-140">Unity 2018 LTS 将于 2021 年春季终止服务。</span><span class="sxs-lookup"><span data-stu-id="5c054-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>