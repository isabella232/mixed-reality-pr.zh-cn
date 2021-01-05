---
ms.openlocfilehash: 283bfffb2d59d92712e86e12c05be8974f04fae6
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717325"
---
# <a name="unity"></a>[<span data-ttu-id="40de5-101">Unity</span><span class="sxs-lookup"><span data-stu-id="40de5-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="40de5-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="40de5-103">1. Download the latest version</span></span>

<span data-ttu-id="40de5-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="40de5-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="40de5-105">目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="40de5-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="40de5-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="40de5-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="40de5-107">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="40de5-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="40de5-109">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="40de5-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="40de5-110">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="40de5-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="40de5-111">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="40de5-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="40de5-112">对于安装，我们建议完成策划的 [Unity 开发历程](../unity/unity-development-overview.md)的[入门部分](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="40de5-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="40de5-113">如果你已遵循 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="40de5-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40de5-114">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.4.0 和 Unity 2019.3.15 。</span><span class="sxs-lookup"><span data-stu-id="40de5-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-115">如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="40de5-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="40de5-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="40de5-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="40de5-117">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="40de5-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="40de5-118">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="40de5-118">Other tools [optional]</span></span>
* <span data-ttu-id="40de5-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="40de5-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="40de5-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="40de5-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="40de5-121">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="40de5-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="40de5-122">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="40de5-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="40de5-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="40de5-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="40de5-124">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="40de5-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-125">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="40de5-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="40de5-126">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="40de5-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="40de5-127">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="40de5-127">For HoloLens development</span></span>

<span data-ttu-id="40de5-128">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="40de5-129">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="40de5-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="40de5-130">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="40de5-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="40de5-131">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="40de5-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="40de5-132">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="40de5-133">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="40de5-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="40de5-134">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="40de5-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="40de5-135">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="40de5-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="40de5-136">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="40de5-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="40de5-137">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="40de5-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="40de5-138">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="40de5-138">Possible solutions include:</span></span>

* <span data-ttu-id="40de5-139">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="40de5-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="40de5-140">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="40de5-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="40de5-141">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="40de5-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="40de5-142">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="40de5-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-143">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="40de5-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="40de5-144">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="40de5-144">I can't deploy over USB</span></span>

<span data-ttu-id="40de5-145">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。</span><span class="sxs-lookup"><span data-stu-id="40de5-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="40de5-146">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="40de5-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="40de5-147">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="40de5-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="40de5-148">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="40de5-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="40de5-149">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="40de5-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="40de5-150">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="40de5-150">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="40de5-151">最低配置</span><span class="sxs-lookup"><span data-stu-id="40de5-151">Minimum</span></span></th><th> <span data-ttu-id="40de5-152">建议</span><span class="sxs-lookup"><span data-stu-id="40de5-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="40de5-153">处理器</span><span class="sxs-lookup"><span data-stu-id="40de5-153">Processor</span></span></td><td> <span data-ttu-id="40de5-154"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="40de5-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="40de5-155"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="40de5-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-156">GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-156">GPU</span></span></td><td> <span data-ttu-id="40de5-157"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="40de5-158"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-159">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="40de5-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="40de5-160">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="40de5-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-161">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="40de5-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="40de5-162">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="40de5-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-163">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="40de5-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-164">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="40de5-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-165">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="40de5-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="40de5-166">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="40de5-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-167">内存</span><span class="sxs-lookup"><span data-stu-id="40de5-167">Memory</span></span></td><td> <span data-ttu-id="40de5-168">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="40de5-169">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-170">存储</span><span class="sxs-lookup"><span data-stu-id="40de5-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="40de5-171">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="40de5-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-172">USB 端口</span><span class="sxs-lookup"><span data-stu-id="40de5-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-173">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="40de5-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="40de5-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="40de5-175">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="40de5-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="40de5-176">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="40de5-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-177">开始你的 Unity 之旅</span><span class="sxs-lookup"><span data-stu-id="40de5-177">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="40de5-178">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="40de5-178">Next Development Checkpoint</span></span>

<span data-ttu-id="40de5-179">如果你遵循我们规划的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="40de5-179">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-180">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="40de5-180">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="40de5-181">你可以随时返回到 [Unity 开发检查点](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="40de5-181">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="40de5-182">Unreal</span><span class="sxs-lookup"><span data-stu-id="40de5-182">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="40de5-184">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="40de5-184">1. Download the latest version</span></span>

<span data-ttu-id="40de5-185">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="40de5-185">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="40de5-186">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="40de5-186">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="40de5-188">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="40de5-188">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="40de5-189">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="40de5-189">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="40de5-190">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="40de5-190">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="40de5-191">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="40de5-191">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="40de5-192">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="40de5-192">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="40de5-193"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="40de5-193"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="40de5-194">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="40de5-194">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="40de5-195">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="40de5-195">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="40de5-196">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="40de5-196">Other tools [optional]</span></span>
* <span data-ttu-id="40de5-197"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="40de5-197"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="40de5-198"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="40de5-198"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="40de5-199">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="40de5-199">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="40de5-200">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="40de5-200">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="40de5-201">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="40de5-201">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="40de5-202">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="40de5-202">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-203">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="40de5-203">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="40de5-204">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="40de5-204">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="40de5-205">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="40de5-205">For HoloLens development</span></span>

<span data-ttu-id="40de5-206">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-206">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="40de5-207">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="40de5-207">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="40de5-208">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="40de5-208">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="40de5-209">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-209">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="40de5-210">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="40de5-210">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="40de5-211">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="40de5-211">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="40de5-212">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="40de5-212">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="40de5-213">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="40de5-213">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="40de5-214">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="40de5-214">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="40de5-215">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="40de5-215">Possible solutions include:</span></span>

* <span data-ttu-id="40de5-216">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="40de5-216">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="40de5-217">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="40de5-217">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="40de5-218">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="40de5-218">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="40de5-219">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="40de5-219">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-220">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="40de5-220">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="40de5-221">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="40de5-221">I can't deploy over USB</span></span>

<span data-ttu-id="40de5-222">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。</span><span class="sxs-lookup"><span data-stu-id="40de5-222">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="40de5-223">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="40de5-223">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="40de5-224">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="40de5-224">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="40de5-225">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="40de5-225">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="40de5-226">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="40de5-226">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="40de5-227">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="40de5-227">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="40de5-228">最低配置</span><span class="sxs-lookup"><span data-stu-id="40de5-228">Minimum</span></span></th><th> <span data-ttu-id="40de5-229">建议</span><span class="sxs-lookup"><span data-stu-id="40de5-229">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="40de5-230">处理器</span><span class="sxs-lookup"><span data-stu-id="40de5-230">Processor</span></span></td><td> <span data-ttu-id="40de5-231"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="40de5-231"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="40de5-232"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="40de5-232"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-233">GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-233">GPU</span></span></td><td> <span data-ttu-id="40de5-234"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-234"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="40de5-235"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-235"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-236">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="40de5-236">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="40de5-237">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="40de5-237">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-238">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="40de5-238">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="40de5-239">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="40de5-239">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-240">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="40de5-240">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-241">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="40de5-241">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-242">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="40de5-242">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="40de5-243">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="40de5-243">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-244">内存</span><span class="sxs-lookup"><span data-stu-id="40de5-244">Memory</span></span></td><td> <span data-ttu-id="40de5-245">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-245">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="40de5-246">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-246">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-247">存储</span><span class="sxs-lookup"><span data-stu-id="40de5-247">Storage</span></span></td><td colspan="2"> <span data-ttu-id="40de5-248">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="40de5-248">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-249">USB 端口</span><span class="sxs-lookup"><span data-stu-id="40de5-249">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-250">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="40de5-250">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-251">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="40de5-251">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="40de5-252">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="40de5-252">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="40de5-253">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="40de5-253">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-254">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="40de5-254">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="40de5-255">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="40de5-255">Next Development Checkpoint</span></span>

<span data-ttu-id="40de5-256">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="40de5-256">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-257">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="40de5-257">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="40de5-258">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="40de5-258">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="40de5-259">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="40de5-259">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="40de5-261">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="40de5-261">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="40de5-262">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="40de5-262">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="40de5-263">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="40de5-263">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="40de5-264">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="40de5-264">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="40de5-265">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="40de5-265">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="40de5-266">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="40de5-266">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="40de5-267">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="40de5-267">For HoloLens development</span></span>

<span data-ttu-id="40de5-268">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-268">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="40de5-269">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="40de5-269">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="40de5-270">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="40de5-270">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="40de5-271">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="40de5-271">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-272">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="40de5-272">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="40de5-273">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="40de5-273">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="40de5-274">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="40de5-274">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="40de5-275">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="40de5-275">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="40de5-276">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="40de5-276">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="40de5-277">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="40de5-277">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="40de5-278">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="40de5-278">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="40de5-279">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="40de5-279">Possible solutions include:</span></span>

* <span data-ttu-id="40de5-280">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="40de5-280">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="40de5-281">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="40de5-281">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="40de5-282">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="40de5-282">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="40de5-283">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="40de5-283">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="40de5-284">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="40de5-284">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="40de5-285">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="40de5-285">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="40de5-286">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="40de5-286">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="40de5-287">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="40de5-287">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="40de5-288">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="40de5-288">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="40de5-289">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="40de5-289">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="40de5-290">最低配置</span><span class="sxs-lookup"><span data-stu-id="40de5-290">Minimum</span></span></th><th> <span data-ttu-id="40de5-291">建议</span><span class="sxs-lookup"><span data-stu-id="40de5-291">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="40de5-292">处理器</span><span class="sxs-lookup"><span data-stu-id="40de5-292">Processor</span></span></td><td> <span data-ttu-id="40de5-293"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="40de5-293"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="40de5-294"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="40de5-294"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-295">GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-295">GPU</span></span></td><td> <span data-ttu-id="40de5-296"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-296"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="40de5-297"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="40de5-297"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-298">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="40de5-298">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="40de5-299">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="40de5-299">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-300">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="40de5-300">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="40de5-301">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="40de5-301">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-302">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="40de5-302">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-303">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="40de5-303">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-304">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="40de5-304">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="40de5-305">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="40de5-305">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-306">内存</span><span class="sxs-lookup"><span data-stu-id="40de5-306">Memory</span></span></td><td> <span data-ttu-id="40de5-307">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-307">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="40de5-308">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="40de5-308">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-309">存储</span><span class="sxs-lookup"><span data-stu-id="40de5-309">Storage</span></span></td><td colspan="2"> <span data-ttu-id="40de5-310">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="40de5-310">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-311">USB 端口</span><span class="sxs-lookup"><span data-stu-id="40de5-311">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="40de5-312">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="40de5-312">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="40de5-313">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="40de5-313">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="40de5-314">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="40de5-314">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="40de5-315">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="40de5-315">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-316">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="40de5-316">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="40de5-317">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="40de5-317">Next Development Checkpoint</span></span>

<span data-ttu-id="40de5-318">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="40de5-318">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40de5-319">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="40de5-319">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="40de5-320">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="40de5-320">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
