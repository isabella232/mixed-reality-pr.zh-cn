---
title: 具有 Windows Mixed Reality 的基于位置的娱乐
description: 了解基于位置娱乐的 Windows Mixed Reality-硬件、背包 Pc、跟踪、配置和支持。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: mixed reality，vr，lbe，位置，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，硬件，HoloLens，多玩家，云服务，azure
ms.openlocfilehash: 323981d49c99f5cb175b71645851496bfa1f268c
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757825"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="680a3-104">具有 Windows Mixed Reality 的基于位置的娱乐</span><span class="sxs-lookup"><span data-stu-id="680a3-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="680a3-105">在过去几年中，我们在基于地点的娱乐类别中看到了惊人的增长和创新。</span><span class="sxs-lookup"><span data-stu-id="680a3-105">In the last couple of years, we've seen an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="680a3-106">传统的会场（如主题公园和电影院）已开始提供沉浸式多玩家体验，作为现有搭乘和安装的免费体验。</span><span class="sxs-lookup"><span data-stu-id="680a3-106">Traditional venues like theme parks and theaters have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="680a3-107">新的操作员和会场为面向大众带来了独特的多 sensorial、多玩家体验。</span><span class="sxs-lookup"><span data-stu-id="680a3-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="680a3-108">所有这些经验都是通过推送信封来实现混合现实。</span><span class="sxs-lookup"><span data-stu-id="680a3-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="680a3-109">本文档是在基于位置的娱乐类别中开始使用 Windows Mixed Reality 的指南。</span><span class="sxs-lookup"><span data-stu-id="680a3-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="680a3-110">下面的指南可能还适用于超出娱乐的位置体验，例如培训、产品设计和其他用例。</span><span class="sxs-lookup"><span data-stu-id="680a3-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design, and other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="680a3-111">工程常见问题</span><span class="sxs-lookup"><span data-stu-id="680a3-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="680a3-112">硬件</span><span class="sxs-lookup"><span data-stu-id="680a3-112">Hardware</span></span>

<span data-ttu-id="680a3-113">**问： Microsoft 及其合作伙伴提供的可在我的设置中使用的硬件**</span><span class="sxs-lookup"><span data-stu-id="680a3-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="680a3-114">答： Microsoft 及其 OEM 合作伙伴提供了一套极具吸引力的设备，可根据需要进行选择。</span><span class="sxs-lookup"><span data-stu-id="680a3-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="680a3-115">如果你向客户提供的体验需要虚拟现实耳机，HP、Samsung 和 Acer 的市场耳机都非常合适。</span><span class="sxs-lookup"><span data-stu-id="680a3-115">If the experiences you’re providing to your customers requires a virtual reality headset, in-market headsets from HP, Samsung, and Acer are a great fit.</span></span> <span data-ttu-id="680a3-116">每个耳机都有其各自的不同属性。</span><span class="sxs-lookup"><span data-stu-id="680a3-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="680a3-117">以下各项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="680a3-117">More details on each below.</span></span>

<span data-ttu-id="680a3-118">HP 回音： [详细信息](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="680a3-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="680a3-119">Samsung 太空 +： [详细信息](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="680a3-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="680a3-120">Acer： [详细信息](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="680a3-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="680a3-121">如果你的位置专门使用 "查看" 耳机来实现混合或扩充的现实体验，请查看 Microsoft HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="680a3-121">If your location specializes in mixed or augmented reality experiences with see-through headsets, check out the Microsoft HoloLens 2.</span></span>  

<span data-ttu-id="680a3-122">HoloLens 2： [订购利息](https://www.microsoft.com//hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="680a3-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com//hololens/buy)</span></span>

<span data-ttu-id="680a3-123">如果你正在试验使用高级计算机视觉、语音和正文跟踪的体验，Azure Kinect 深色的优点非常合适。</span><span class="sxs-lookup"><span data-stu-id="680a3-123">If you’re experimenting with experiences that use advanced computer vision, speech, and body tracking, the Azure Kinect DK is a good fit.</span></span>  

<span data-ttu-id="680a3-124">Azure Kinect： [详细信息](https://azure.microsoft.com//services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="680a3-124">Azure Kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)</span></span>

<span data-ttu-id="680a3-125">**问：我可以使用哪些背包电脑组合来运行我的电脑-受限 VR 体验？**</span><span class="sxs-lookup"><span data-stu-id="680a3-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="680a3-126">对于电脑受限 VR 体验，我们的 Oem 提供了令人难以置信地选择的背包 Pc。</span><span class="sxs-lookup"><span data-stu-id="680a3-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="680a3-127">HP 刚刚启动了其 HP VR 背包 G2，这是世界上最强大的可穿戴 PC –为自由漫游体验进行了优化，现在，在内部使用 RTX 2080 GPU 可提高30% 的电量。</span><span class="sxs-lookup"><span data-stu-id="680a3-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="680a3-128">详细信息</span><span class="sxs-lookup"><span data-stu-id="680a3-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="680a3-129">设置</span><span class="sxs-lookup"><span data-stu-id="680a3-129">Setup</span></span>

<span data-ttu-id="680a3-130">**问：如何更轻松地配置安装并为 LBE 自定义混合现实门户？**</span><span class="sxs-lookup"><span data-stu-id="680a3-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="680a3-131">此功能需要2000.19061.1011.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="680a3-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="680a3-132">你可能会发现，你需要对混合现实门户进行更多的自定义，而不是通常通过用于将应用部署到展台或自定义体验的应用使用。</span><span class="sxs-lookup"><span data-stu-id="680a3-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="680a3-133">混合现实门户的最新7月更新支持多个高级设置，你可以通过配置文件进行设置：</span><span class="sxs-lookup"><span data-stu-id="680a3-133">The latest July update of Mixed Reality Portal supports several advanced settings, which you can set via a configuration file:</span></span>  

<span data-ttu-id="680a3-134">允许故障系统检查–在完成安装程序之前，安装过程通常会检查 PC 与 Windows Mixed Reality 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="680a3-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="680a3-135">如果存在兼容性问题，则在尝试运行 Windows Mixed Reality 时，绕过兼容性检查可能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="680a3-135">Bypassing compatibility checks may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="680a3-136">跳过设备辅助应用– DCA 提供制造商提供的耳机特定的设置步骤，并允许更新耳机固件。</span><span class="sxs-lookup"><span data-stu-id="680a3-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="680a3-137">跳过房间安装-不会提示你创建房间边界，你可以继续在 "固定"/"固定" 模式下直接进入耳机。</span><span class="sxs-lookup"><span data-stu-id="680a3-137">Skip room setup – instead of being prompted to create a room boundary, you can continue directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="680a3-138">跳过从应用商店安装应用-普通安装程序将安装多个应用商店应用，包括3D 查看器和 Edge 360 查看器加载项。</span><span class="sxs-lookup"><span data-stu-id="680a3-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="680a3-139">这会跳过这些应用的安装，但可能缺少设备功能。</span><span class="sxs-lookup"><span data-stu-id="680a3-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="680a3-140">全屏显示预览–混合现实门户将默认为在使用耳机时在台式计算机上全屏显示耳机预览。</span><span class="sxs-lookup"><span data-stu-id="680a3-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="680a3-141">隐藏侧面板的新增部分–禁止在启动混合现实门户时展开面板的新新。</span><span class="sxs-lookup"><span data-stu-id="680a3-141">Hide New for your side panel – prevents the New for your panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="680a3-142">配置方式：</span><span class="sxs-lookup"><span data-stu-id="680a3-142">How to configure:</span></span>  

<span data-ttu-id="680a3-143">若要设置这些配置中的任何一种，需要在此目录下创建一个名为 _UserConfig.js_ 的文件： _$env \\ ： localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate_</span><span class="sxs-lookup"><span data-stu-id="680a3-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="680a3-144">对于大多数用户，此内容如下所示： _C:\Users \<username> \Appdata\local\packages\ microsoft.mixedreality.portal_8wekyb3d8bbwe \\ \localstate_</span><span class="sxs-lookup"><span data-stu-id="680a3-144">For most users, this will look like: _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="680a3-145">对于您想要启用的任意设置，JSON 文件的内容应为 "true"：</span><span class="sxs-lookup"><span data-stu-id="680a3-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="680a3-146">**问：是否有关于配置 playspace 的指导？**</span><span class="sxs-lookup"><span data-stu-id="680a3-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="680a3-147">答：配置 playspace 应像使用使用者安装体验一样完成。</span><span class="sxs-lookup"><span data-stu-id="680a3-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="680a3-148">房间设置过程还将允许您定义房间边界。</span><span class="sxs-lookup"><span data-stu-id="680a3-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="680a3-149">有关配置空间边界的详细信息，请参阅 [此处](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)。</span><span class="sxs-lookup"><span data-stu-id="680a3-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="680a3-150">如以上文档中所述，最大合理的单个坐标 playspace 是围绕5mx5m 的。</span><span class="sxs-lookup"><span data-stu-id="680a3-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="680a3-151">如果要获得更大的区域，可以使用 Windows 全息 API 堆栈中的空间锚功能。</span><span class="sxs-lookup"><span data-stu-id="680a3-151">If you want to have a larger area, you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="680a3-152">使用此 API 需要在生成的体验中进行自定义工程。</span><span class="sxs-lookup"><span data-stu-id="680a3-152">Using this API will require custom engineering in the experiences you're producing.</span></span>  

<span data-ttu-id="680a3-153">可在 [此处](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems)阅读有关如何针对不同的空间大小优化内容的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="680a3-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="680a3-154">**问：我的空间太大了，在尝试使用边界建立持续的体验时，我遇到了错误。设置大的免费漫游体验应该怎么办？**</span><span class="sxs-lookup"><span data-stu-id="680a3-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to set up my large free-roam experience work?**</span></span>

<span data-ttu-id="680a3-155">答：若要设置比 ~ 18x18ft 更大的空间，则无法使用系统提供的边界体验。</span><span class="sxs-lookup"><span data-stu-id="680a3-155">A: To set up a larger space than ~18x18ft, you can't use the boundary experience provided by the system.</span></span>  <span data-ttu-id="680a3-156">边界系统依赖于单个固定坐标 "锚点"，当用户离中心舞台锚点太远时，这会变得不稳定。</span><span class="sxs-lookup"><span data-stu-id="680a3-156">The boundary systems rely on a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="680a3-157">你可以设置 "固定" 模式，这种模式不会显示边界，也不会配置阶段边界或 playspace。</span><span class="sxs-lookup"><span data-stu-id="680a3-157">You can set up “seated” mode, which won't display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="680a3-158">需要在应用程序中配置多个空间锚点以引用物理边界区域。</span><span class="sxs-lookup"><span data-stu-id="680a3-158">You’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="680a3-159">应用程序开发人员负责显示必要的安全措施，使用户不会与物理环境发生冲突。</span><span class="sxs-lookup"><span data-stu-id="680a3-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="680a3-160">这可能是经验或自定义游戏边界视觉对象中的数字背景。</span><span class="sxs-lookup"><span data-stu-id="680a3-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="680a3-161">可在 [此处](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到有关通过 WMR 设置空间边界的指南。</span><span class="sxs-lookup"><span data-stu-id="680a3-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="680a3-162">**问： playspace 的来源是什么？**</span><span class="sxs-lookup"><span data-stu-id="680a3-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="680a3-163">答： playspace 的来源取决于房间安装体验，更具体地说是在安装过程中按下中心按钮时的 HMD 位置。</span><span class="sxs-lookup"><span data-stu-id="680a3-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="680a3-164">多玩家安装</span><span class="sxs-lookup"><span data-stu-id="680a3-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="680a3-165">**问：我在我的场所部署了多玩家体验。Windows Mixed Reality 是否支持？**</span><span class="sxs-lookup"><span data-stu-id="680a3-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="680a3-166">答：如果你通过我们的预览体验计划选择加入 Windows 20H1 或更高版本，则可以访问用于地图共享的新接口。</span><span class="sxs-lookup"><span data-stu-id="680a3-166">A: If you opt into the Windows 20H1 or later build via our Insider program, you can access a new interface for map sharing.</span></span> <span data-ttu-id="680a3-167">此新功能可通过 Windows 设备门户的 " [映射管理器](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) " 界面获得。</span><span class="sxs-lookup"><span data-stu-id="680a3-167">This new functionality is available via the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) interface of the Windows Device portal.</span></span> <span data-ttu-id="680a3-168">若要使用此工具，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="680a3-168">To use this tool, follow the steps below:</span></span>
* <span data-ttu-id="680a3-169">请确保选择加入20H1 或更高版本（2019年9月之后），这意味着使用预览体验计划</span><span class="sxs-lookup"><span data-stu-id="680a3-169">Make sure you're opted into 20H1 or later - after September 2019, this means using our Insider program</span></span>
* <span data-ttu-id="680a3-170">使用以下[说明](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop)启用 Windows 设备门户 (WDP) </span><span class="sxs-lookup"><span data-stu-id="680a3-170">Enable the Windows Device Portal (WDP) using these [instructions](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop)</span></span>
* <span data-ttu-id="680a3-171">插入想要从其下载现有映射的 Windows Mixed Reality HMD，或导入新的映射</span><span class="sxs-lookup"><span data-stu-id="680a3-171">Plug in a Windows Mixed Reality HMD that you wish to either download an existing map from or import a new map</span></span>
* <span data-ttu-id="680a3-172">使用在 "设置" 屏幕中提供的 URL，在所选浏览器中导航到 WDP。</span><span class="sxs-lookup"><span data-stu-id="680a3-172">Navigate to the WDP in your browser of choice using the URL provided in the settings screen.</span></span>
    * <span data-ttu-id="680a3-173">导航到 "Mixed Reality" 部分，然后选择 "映射管理器"。</span><span class="sxs-lookup"><span data-stu-id="680a3-173">Once there Navigate to the "Mixed Reality" section and select "Map Manager".</span></span>
    * <span data-ttu-id="680a3-174">你现在可以使用 "下载" 按钮从计算机导出现有映射。</span><span class="sxs-lookup"><span data-stu-id="680a3-174">You can now use the "Download" button to export an existing map from the machine.</span></span>
    * <span data-ttu-id="680a3-175">您可以使用 "上传地图文件" 按钮从上一个导出 (导入地图，) 。</span><span class="sxs-lookup"><span data-stu-id="680a3-175">You can use the "Upload a map file" button to import a map from a previous export (perhaps on a different machine).</span></span>
    * <span data-ttu-id="680a3-176">您可以使用 "导入" 使系统能够在此计算机上为此 HMD 使用该映射。</span><span class="sxs-lookup"><span data-stu-id="680a3-176">You can use "Import" to enable the system to use that map for this HMD on this machine.</span></span>

> [!NOTE] 
> <span data-ttu-id="680a3-177">以前，可以使用空间数据包装器工具，不过，该工具最初发布为不受支持的功能，现已正式弃用并且在20H1 上不再可用。</span><span class="sxs-lookup"><span data-stu-id="680a3-177">Previously, it was possible to use the Spatial Data Packager Tool, however, that tool was originally released as unsupported and is now officially deprecated and no longer functional on 20H1.</span></span> <span data-ttu-id="680a3-178">请改用上文所述的收件箱 [地图管理器](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) 工具。</span><span class="sxs-lookup"><span data-stu-id="680a3-178">Instead, please use the inbox [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool as described above.</span></span> 

### <a name="tracking"></a><span data-ttu-id="680a3-179">字距</span><span class="sxs-lookup"><span data-stu-id="680a3-179">TRACKING</span></span>

<span data-ttu-id="680a3-180">问： Windows Mixed Reality 耳机中的跟踪技术是如何工作的？</span><span class="sxs-lookup"><span data-stu-id="680a3-180">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="680a3-181">混合现实与 HoloLens 共享相同的跟踪技术。</span><span class="sxs-lookup"><span data-stu-id="680a3-181">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="680a3-182">若要详细了解内部输出跟踪系统，请查看 [此处](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system)的文档。</span><span class="sxs-lookup"><span data-stu-id="680a3-182">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="680a3-183">有关更高级的空间映射系统的工作原理的说明，请参阅 [此处](../design/spatial-mapping.md)的说明。</span><span class="sxs-lookup"><span data-stu-id="680a3-183">For a description of how the higher-level spatial mapping system works you can read our description [here](../design/spatial-mapping.md).</span></span>

<span data-ttu-id="680a3-184">**问：是否有用于获取可靠跟踪卷的最佳实践？**</span><span class="sxs-lookup"><span data-stu-id="680a3-184">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="680a3-185">为了最好地配置用于跟踪成功的环境，您可以阅读此 [文章](../environment-considerations-for-hololens.md)中的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="680a3-185">To best configure the environment for tracking success, you can read best practices in this [post](../environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="680a3-186">**问：在仓库规模空间或要考虑的优化中，是否有任何特定的细微差别？**</span><span class="sxs-lookup"><span data-stu-id="680a3-186">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="680a3-187">答：以下做法可帮助获取更可靠的跟踪卷：</span><span class="sxs-lookup"><span data-stu-id="680a3-187">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="680a3-188">在房间中提供与多个位置重叠的不同功能将有助于跟踪系统获得稳定锁定。</span><span class="sxs-lookup"><span data-stu-id="680a3-188">Providing different features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="680a3-189">请考虑随机绘制 splatters 和阴影，而不是使用纯色等高线样式线条。</span><span class="sxs-lookup"><span data-stu-id="680a3-189">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="680a3-190">尽可能最大程度地减小区域中的光线的动态范围。</span><span class="sxs-lookup"><span data-stu-id="680a3-190">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="680a3-191">混合现实 HMDs 上的跟踪相机并不是 HDR，AGC (自动) ，而 AEC (自动曝光) 处理不同的照明。</span><span class="sxs-lookup"><span data-stu-id="680a3-191">The tracking cameras on our Mixed Reality HMDs aren't HDR and have AGC (auto gain) and AEC (auto exposure) going to deal with different lighting.</span></span> <span data-ttu-id="680a3-192">根据不同的表面效果、图案和对比度，无论是 AGC 还是 AEC，都可以使您完全成为所有白色或黑色房间，这会使您的功能变得相对 "颜色"。</span><span class="sxs-lookup"><span data-stu-id="680a3-192">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a much all white or black room, which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="680a3-193">如果你正在尝试在具有鲜日光的外部窗口的前方拍摄内部图片，并调整了曝光以便查看外的详细信息，则内部的所有内容都是 underexposed 和黑色。</span><span class="sxs-lookup"><span data-stu-id="680a3-193">If you're trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="680a3-194">或者，如果在内部设置，则所有外部的内容现在都是 overexposed，所有白色。</span><span class="sxs-lookup"><span data-stu-id="680a3-194">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="680a3-195">在房间中的聚光灯 (甚至是在) 的情况下，如果跟踪相机有时原因，这会导致跟踪相机的 AEC/AGC 混乱。</span><span class="sxs-lookup"><span data-stu-id="680a3-195">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits, which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="680a3-196">平面/散射照明可帮助。</span><span class="sxs-lookup"><span data-stu-id="680a3-196">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="680a3-197">混合现实云服务和 AZURE</span><span class="sxs-lookup"><span data-stu-id="680a3-197">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="680a3-198">**问： Microsoft Azure 如何帮助我的业务规模？**</span><span class="sxs-lookup"><span data-stu-id="680a3-198">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="680a3-199">答：基于 Azure 的现场和远程管理可帮助你的企业进行数据驱动，降低运营成本并在现有和新位置扩展部署。</span><span class="sxs-lookup"><span data-stu-id="680a3-199">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="680a3-200">Azure 云服务（例如 Azure 存储、Azure Functions、应用服务、Azure 网络和 IOT 中心）可帮助解决以下用例：</span><span class="sxs-lookup"><span data-stu-id="680a3-200">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking, and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="680a3-201">远程设备部署 & 管理</span><span class="sxs-lookup"><span data-stu-id="680a3-201">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="680a3-202">Real-Time 现场分析</span><span class="sxs-lookup"><span data-stu-id="680a3-202">Real-Time Onsite Analytics</span></span> 

<span data-ttu-id="680a3-203">智能适应性 LBE 游戏</span><span class="sxs-lookup"><span data-stu-id="680a3-203">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="680a3-204">LBE 内容流式处理和部署</span><span class="sxs-lookup"><span data-stu-id="680a3-204">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="680a3-205">LBE Player 首选项热度地图</span><span class="sxs-lookup"><span data-stu-id="680a3-205">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="680a3-206">LBE 预订系统和预订系统</span><span class="sxs-lookup"><span data-stu-id="680a3-206">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="680a3-207">**问：我要开发一个空间 MMOG 来部署大量占用空间。有助于管理内容和对象持久性的任何服务？**</span><span class="sxs-lookup"><span data-stu-id="680a3-207">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="680a3-208">答： Azure 空间锚点是一项新的混合现实服务，可实现通过 HoloLens、iOS 和 Android 设备的多用户、空间丰富的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="680a3-208">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS, and Android devices.</span></span> <span data-ttu-id="680a3-209">可在 [此处](https://azure.microsoft.com//services/spatial-anchors/)了解有关 Azure 空间定位点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="680a3-209">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com//services/spatial-anchors/).</span></span>

<span data-ttu-id="680a3-210">**：.我们的场地专用于多玩家体验，我想将开发时间集中在内容和前端开发上。是否有可帮助我启动或卸载后端开发的产品？**</span><span class="sxs-lookup"><span data-stu-id="680a3-210">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="680a3-211">答： Azure PlayFab 是适用于现场游戏的完整后端平台。</span><span class="sxs-lookup"><span data-stu-id="680a3-211">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="680a3-212">可在 [此处](https://playfab.com/)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="680a3-212">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="680a3-213">杂项</span><span class="sxs-lookup"><span data-stu-id="680a3-213">Misc</span></span>

<span data-ttu-id="680a3-214">**问：我使用 SteamVR 来部署我的体验。Windows Mixed Reality 是否适用于 SteamVR？**</span><span class="sxs-lookup"><span data-stu-id="680a3-214">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="680a3-215">答： SteamVR 的 Windows Mixed Reality 允许用户在 Windows Mixed Reality 沉浸式耳机上运行 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="680a3-215">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="680a3-216">[在此处](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)了解有关 SteamVR 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="680a3-216">Learn more about SteamVR with WMR [here](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="680a3-217">支持和社区</span><span class="sxs-lookup"><span data-stu-id="680a3-217">Support and community</span></span>  

<span data-ttu-id="680a3-218">我们提供了一些有用的资源，可帮助你在我们的团队中与行业专家进行合作，获取故障排除支持，并为更广泛的混合现实开发社区提供帮助。</span><span class="sxs-lookup"><span data-stu-id="680a3-218">We have a few helpful resources to help you engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="680a3-219">如果遇到任何公开发布功能的问题，请使用反馈中心提交 bug。有关指南，请参阅此 [页](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="680a3-219">If you run into issues with any publicly released features, file a bug using Feedback Hub.For guidance, refer to this [page](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="680a3-220">有关 WMR 的其他故障排除帮助，请向我们的客户支持团队提供 [支持请求](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) 。</span><span class="sxs-lookup"><span data-stu-id="680a3-220">For other troubleshooting help with WMR, file a [support request](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) with our customer support team.</span></span>

<span data-ttu-id="680a3-221">加入我们的 HoloDevelopers 时差通道，与混合现实开发人员和主题专家合作： [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="680a3-221">Join our HoloDevelopers Slack channel to engage with the mixed reality developers and subject matter experts: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="680a3-222">Twitter：关注混合现实开发人员关系团队以获取新闻、活动和更新 @MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="680a3-222">Twitter: Follow our Mixed Reality Developer Relations team for news, events, and updates @MxdRealityDev</span></span> 

<span data-ttu-id="680a3-223">如果你的工作发生在旧金山或周围，则 Microsoft 反应器中始终会出现一些问题。</span><span class="sxs-lookup"><span data-stu-id="680a3-223">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="680a3-224">[此处](https://developer.microsoft.com//reactor/Location/San%20Francisco)可以看到我们的事件日历。</span><span class="sxs-lookup"><span data-stu-id="680a3-224">You can see our calendar of events [here](https://developer.microsoft.com//reactor/Location/San%20Francisco).</span></span>
