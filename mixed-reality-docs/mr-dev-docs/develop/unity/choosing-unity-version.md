---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 3bdaa35f495d7a647a7cbf37ddcd4f85e96d74d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143674"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="a9365-104">选择 Unity 版本和 XR 插件</span><span class="sxs-lookup"><span data-stu-id="a9365-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="a9365-105">虽然我们 **目前建议安装 Unity 2019.4 LTS，** 以及使用旧版内置 XR 进行混合现实开发，但也可使用其他 Unity 配置生成应用。</span><span class="sxs-lookup"><span data-stu-id="a9365-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="a9365-106">Unity 2019.4 LTS (建议) </span><span class="sxs-lookup"><span data-stu-id="a9365-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="a9365-107">Microsoft 当前推荐的用于 HoloLens 2 和 Windows Mixed Reality 的 Unity 配置是使用旧版内置 XR 支持的 **Unity 2019.4 LTS。**</span><span class="sxs-lookup"><span data-stu-id="a9365-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="a9365-108">安装和管理 Unity 的最佳方式是通过 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>。</span><span class="sxs-lookup"><span data-stu-id="a9365-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="a9365-109">安装后，打开 Unity 中心：</span><span class="sxs-lookup"><span data-stu-id="a9365-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="a9365-110">选择" **安装"选项卡** ，然后选择" **添加"**</span><span class="sxs-lookup"><span data-stu-id="a9365-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="a9365-111">选择"Unity 2019.4 LTS"，然后单击"下一 **步"**</span><span class="sxs-lookup"><span data-stu-id="a9365-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 中心安装新版本](images/unity-hub-img-01.png)

3. <span data-ttu-id="a9365-113">检查"平台" **下的以下组件**</span><span class="sxs-lookup"><span data-stu-id="a9365-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="a9365-114">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="a9365-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="a9365-115">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="a9365-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="a9365-117">如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：</span><span class="sxs-lookup"><span data-stu-id="a9365-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="a9365-119">若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：</span><span class="sxs-lookup"><span data-stu-id="a9365-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9365-120">设置旧版内置 XR</span><span class="sxs-lookup"><span data-stu-id="a9365-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="a9365-121">自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="a9365-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="a9365-122">虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。</span><span class="sxs-lookup"><span data-stu-id="a9365-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="a9365-123">在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="a9365-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="a9365-124">如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。</span><span class="sxs-lookup"><span data-stu-id="a9365-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="a9365-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="a9365-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="a9365-126">如果使用 **Unity 2020.3 LTS，** 可以使用 **Windows XR** 插件开发HoloLens 2和Windows Mixed Reality应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9365-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="a9365-127">但是，有一些已知问题会影响全息影像稳定性和 HoloLens 2 上的其他功能：</span><span class="sxs-lookup"><span data-stu-id="a9365-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="a9365-128">使用通用 Windows 平台生成目标的全息应用远程处理应用程序无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="a9365-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="a9365-129">Unity 图形作业系统在默认情况下是打开的，即使它与 HoloLens 项目不兼容。</span><span class="sxs-lookup"><span data-stu-id="a9365-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="a9365-130">如果你现在选择在 Unity 2020 中启动一个新项目，请务必在交付应用之前，在未来几个月内跟进更新后的 Unity 生成和 Windows XR 插件版本。</span><span class="sxs-lookup"><span data-stu-id="a9365-130">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="a9365-131">这将确保用户体验到适当的全息影像稳定性。</span><span class="sxs-lookup"><span data-stu-id="a9365-131">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9365-132">使用 Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="a9365-132">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="a9365-133">使用 OpenXR</span><span class="sxs-lookup"><span data-stu-id="a9365-133">Using OpenXR</span></span>

<span data-ttu-id="a9365-134">Unity 2020.3 LTS 还支持 **混合现实 OpenXR** 插件的公共预览版。</span><span class="sxs-lookup"><span data-stu-id="a9365-134">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="a9365-135">Mixed Reality OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。</span><span class="sxs-lookup"><span data-stu-id="a9365-135">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="a9365-136">这样一来，你就可以编写命中测试代码一次，然后跨 HoloLens 2 和 ARCore/ARKit 手机和平板电脑。</span><span class="sxs-lookup"><span data-stu-id="a9365-136">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="a9365-137">今年晚些时候， **具有 OpenXR 插件的 unity 2020.3 LTS** 将成为推荐的 unity 配置，并且 unity 中的未来 HoloLens 2 功能将仅通过此插件公开。</span><span class="sxs-lookup"><span data-stu-id="a9365-137">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9365-138">使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="a9365-138">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="a9365-139">Unity 2021。1</span><span class="sxs-lookup"><span data-stu-id="a9365-139">Unity 2021.1</span></span>

<span data-ttu-id="a9365-140">如果你正在试用早期 **Unity 2021.1** 生成，则应前进到 **OpenXR 插件**，因为 Windows XR 插件已在此处弃用。</span><span class="sxs-lookup"><span data-stu-id="a9365-140">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="a9365-141">从 Unity 2021.2 开始，OpenXR 插件将成为混合现实开发的唯一路径，因为 Windows XR 插件将不再受支持。</span><span class="sxs-lookup"><span data-stu-id="a9365-141">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="a9365-142">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="a9365-142">Unity 2018.4 LTS</span></span>

<span data-ttu-id="a9365-143">如果你已有使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受到2年的支持。</span><span class="sxs-lookup"><span data-stu-id="a9365-143">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="a9365-144">Unity 2018 LTS 将在2021春季接通服务结束。</span><span class="sxs-lookup"><span data-stu-id="a9365-144">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
