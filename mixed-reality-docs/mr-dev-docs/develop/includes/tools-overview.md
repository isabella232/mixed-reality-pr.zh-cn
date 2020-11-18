---
ms.openlocfilehash: cd6541dd651573f31ddc2e2a388be53394059c5f
ms.sourcegitcommit: f459c7deb254409fd5db3967bcc875bcbc367e77
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94482407"
---
# <a name="unity"></a>[<span data-ttu-id="55aeb-101">Unity</span><span class="sxs-lookup"><span data-stu-id="55aeb-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="55aeb-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="55aeb-103">1. Download the latest version</span></span>

<span data-ttu-id="55aeb-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="55aeb-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="55aeb-105">目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="55aeb-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="55aeb-107">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="55aeb-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="55aeb-109">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="55aeb-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="55aeb-110">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="55aeb-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="55aeb-111">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="55aeb-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="55aeb-112">对于安装，我们建议完成策划的 [Unity 开发历程](../unity/unity-development-overview.md)的[入门部分](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="55aeb-113">如果你已遵循 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55aeb-114">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.4.0 和 Unity 2019.3.15 。</span><span class="sxs-lookup"><span data-stu-id="55aeb-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-115">如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="55aeb-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="55aeb-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="55aeb-117">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="55aeb-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="55aeb-118">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="55aeb-118">Other tools [optional]</span></span>
* <span data-ttu-id="55aeb-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="55aeb-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="55aeb-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="55aeb-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="55aeb-121">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="55aeb-122">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="55aeb-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="55aeb-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="55aeb-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="55aeb-124">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="55aeb-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-125">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="55aeb-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="55aeb-126">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="55aeb-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="55aeb-127">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-127">For HoloLens development</span></span>

<span data-ttu-id="55aeb-128">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="55aeb-129">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="55aeb-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="55aeb-130">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="55aeb-131">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="55aeb-132">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="55aeb-133">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="55aeb-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="55aeb-134">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="55aeb-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="55aeb-135">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="55aeb-136">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="55aeb-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="55aeb-137">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="55aeb-138">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="55aeb-138">Possible solutions include:</span></span>

* <span data-ttu-id="55aeb-139">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="55aeb-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="55aeb-140">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="55aeb-141">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="55aeb-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="55aeb-142">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="55aeb-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-143">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="55aeb-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="55aeb-144">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="55aeb-144">I can't deploy over USB</span></span>

<span data-ttu-id="55aeb-145">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。</span><span class="sxs-lookup"><span data-stu-id="55aeb-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="55aeb-146">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="55aeb-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="55aeb-147">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="55aeb-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="55aeb-148">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="55aeb-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="55aeb-149">如果你在使用 Reverb G2 头戴显示设备，请下载 Microsoft-Valve OpenXR 插件 (TODO: // 需要链接) 。</span><span class="sxs-lookup"><span data-stu-id="55aeb-149">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="55aeb-150">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="55aeb-150">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="55aeb-151">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-151">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="55aeb-152">最低配置</span><span class="sxs-lookup"><span data-stu-id="55aeb-152">Minimum</span></span></th><th> <span data-ttu-id="55aeb-153">建议</span><span class="sxs-lookup"><span data-stu-id="55aeb-153">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="55aeb-154">处理器</span><span class="sxs-lookup"><span data-stu-id="55aeb-154">Processor</span></span></td><td> <span data-ttu-id="55aeb-155"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-155"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="55aeb-156"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="55aeb-156"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-157">GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-157">GPU</span></span></td><td> <span data-ttu-id="55aeb-158"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-158"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="55aeb-159"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-159"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-160">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="55aeb-160">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-161">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="55aeb-161">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-162">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="55aeb-162">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-163">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="55aeb-163">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-164">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-164">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-165">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="55aeb-165">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-166">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="55aeb-166">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-167">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="55aeb-167">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-168">内存</span><span class="sxs-lookup"><span data-stu-id="55aeb-168">Memory</span></span></td><td> <span data-ttu-id="55aeb-169">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-169">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="55aeb-170">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-170">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-171">存储</span><span class="sxs-lookup"><span data-stu-id="55aeb-171">Storage</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-172">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="55aeb-172">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-173">USB 端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-173">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-174">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="55aeb-174">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-175">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="55aeb-175">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-176">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="55aeb-176">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="55aeb-177">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="55aeb-177">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-178">开始你的 Unity 之旅</span><span class="sxs-lookup"><span data-stu-id="55aeb-178">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="55aeb-179">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="55aeb-179">Next Development Checkpoint</span></span>

<span data-ttu-id="55aeb-180">如果你遵循我们规划的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="55aeb-180">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-181">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="55aeb-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="55aeb-182">你可以随时返回到 [Unity 开发检查点](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-182">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="55aeb-183">Unreal</span><span class="sxs-lookup"><span data-stu-id="55aeb-183">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="55aeb-185">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="55aeb-185">1. Download the latest version</span></span>

<span data-ttu-id="55aeb-186">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="55aeb-186">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="55aeb-187">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="55aeb-187">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="55aeb-189">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="55aeb-189">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="55aeb-190">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="55aeb-190">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="55aeb-191">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="55aeb-191">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="55aeb-192">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-192">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="55aeb-193">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-193">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="55aeb-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="55aeb-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="55aeb-195">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="55aeb-195">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="55aeb-196">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-196">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="55aeb-197">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="55aeb-197">Other tools [optional]</span></span>
* <span data-ttu-id="55aeb-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="55aeb-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="55aeb-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="55aeb-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="55aeb-200">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-200">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="55aeb-201">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="55aeb-201">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="55aeb-202">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="55aeb-202">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="55aeb-203">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="55aeb-203">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-204">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="55aeb-204">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="55aeb-205">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="55aeb-205">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="55aeb-206">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-206">For HoloLens development</span></span>

<span data-ttu-id="55aeb-207">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-207">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="55aeb-208">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="55aeb-208">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="55aeb-209">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-209">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="55aeb-210">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-210">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="55aeb-211">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="55aeb-211">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="55aeb-212">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="55aeb-212">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="55aeb-213">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-213">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="55aeb-214">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="55aeb-214">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="55aeb-215">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-215">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="55aeb-216">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="55aeb-216">Possible solutions include:</span></span>

* <span data-ttu-id="55aeb-217">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="55aeb-217">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="55aeb-218">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-218">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="55aeb-219">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="55aeb-219">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="55aeb-220">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="55aeb-220">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-221">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="55aeb-221">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="55aeb-222">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="55aeb-222">I can't deploy over USB</span></span>

<span data-ttu-id="55aeb-223">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。</span><span class="sxs-lookup"><span data-stu-id="55aeb-223">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="55aeb-224">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="55aeb-224">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="55aeb-225">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="55aeb-225">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="55aeb-226">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="55aeb-226">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="55aeb-227">如果你在使用 Reverb G2 头戴显示设备，请下载 Microsoft-Valve OpenXR 插件 (TODO: // 需要链接) 。</span><span class="sxs-lookup"><span data-stu-id="55aeb-227">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="55aeb-228">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="55aeb-228">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="55aeb-229">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-229">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="55aeb-230">最低配置</span><span class="sxs-lookup"><span data-stu-id="55aeb-230">Minimum</span></span></th><th> <span data-ttu-id="55aeb-231">建议</span><span class="sxs-lookup"><span data-stu-id="55aeb-231">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="55aeb-232">处理器</span><span class="sxs-lookup"><span data-stu-id="55aeb-232">Processor</span></span></td><td> <span data-ttu-id="55aeb-233"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-233"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="55aeb-234"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="55aeb-234"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-235">GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-235">GPU</span></span></td><td> <span data-ttu-id="55aeb-236"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-236"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="55aeb-237"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-237"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-238">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="55aeb-238">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-239">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="55aeb-239">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-240">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="55aeb-240">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-241">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="55aeb-241">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-242">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-242">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-243">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="55aeb-243">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-244">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="55aeb-244">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-245">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="55aeb-245">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-246">内存</span><span class="sxs-lookup"><span data-stu-id="55aeb-246">Memory</span></span></td><td> <span data-ttu-id="55aeb-247">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-247">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="55aeb-248">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-248">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-249">存储</span><span class="sxs-lookup"><span data-stu-id="55aeb-249">Storage</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-250">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="55aeb-250">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-251">USB 端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-251">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-252">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="55aeb-252">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-253">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="55aeb-253">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-254">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="55aeb-254">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="55aeb-255">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="55aeb-255">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-256">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="55aeb-256">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="55aeb-257">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="55aeb-257">Next Development Checkpoint</span></span>

<span data-ttu-id="55aeb-258">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="55aeb-258">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-259">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="55aeb-259">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="55aeb-260">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-260">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="55aeb-261">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="55aeb-261">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="55aeb-263">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="55aeb-263">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="55aeb-264">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="55aeb-264">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="55aeb-265">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-265">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="55aeb-266">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="55aeb-266">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="55aeb-267">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="55aeb-267">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="55aeb-268">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="55aeb-268">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="55aeb-269">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="55aeb-269">For HoloLens development</span></span>

<span data-ttu-id="55aeb-270">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-270">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="55aeb-271">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="55aeb-271">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="55aeb-272">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-272">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="55aeb-273">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="55aeb-273">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-274">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="55aeb-274">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="55aeb-275">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="55aeb-275">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="55aeb-276">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="55aeb-276">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="55aeb-277">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="55aeb-277">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="55aeb-278">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-278">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="55aeb-279">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="55aeb-279">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="55aeb-280">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-280">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="55aeb-281">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="55aeb-281">Possible solutions include:</span></span>

* <span data-ttu-id="55aeb-282">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="55aeb-282">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="55aeb-283">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-283">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="55aeb-284">此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="55aeb-284">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="55aeb-285">使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="55aeb-285">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="55aeb-286">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="55aeb-286">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="55aeb-287">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="55aeb-287">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="55aeb-288">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="55aeb-288">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="55aeb-289">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="55aeb-289">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="55aeb-290">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="55aeb-290">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="55aeb-291">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="55aeb-291">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="55aeb-292">最低配置</span><span class="sxs-lookup"><span data-stu-id="55aeb-292">Minimum</span></span></th><th> <span data-ttu-id="55aeb-293">建议</span><span class="sxs-lookup"><span data-stu-id="55aeb-293">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="55aeb-294">处理器</span><span class="sxs-lookup"><span data-stu-id="55aeb-294">Processor</span></span></td><td> <span data-ttu-id="55aeb-295"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-295"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="55aeb-296"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="55aeb-296"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-297">GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-297">GPU</span></span></td><td> <span data-ttu-id="55aeb-298"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-298"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="55aeb-299"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="55aeb-299"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-300">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="55aeb-300">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-301">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="55aeb-301">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-302">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="55aeb-302">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-303">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="55aeb-303">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-304">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-304">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-305">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="55aeb-305">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-306">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="55aeb-306">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-307">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="55aeb-307">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-308">内存</span><span class="sxs-lookup"><span data-stu-id="55aeb-308">Memory</span></span></td><td> <span data-ttu-id="55aeb-309">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-309">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="55aeb-310">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="55aeb-310">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-311">存储</span><span class="sxs-lookup"><span data-stu-id="55aeb-311">Storage</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-312">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="55aeb-312">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-313">USB 端口</span><span class="sxs-lookup"><span data-stu-id="55aeb-313">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-314">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="55aeb-314">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="55aeb-315">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="55aeb-315">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="55aeb-316">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="55aeb-316">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="55aeb-317">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="55aeb-317">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-318">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="55aeb-318">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="55aeb-319">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="55aeb-319">Next Development Checkpoint</span></span>

<span data-ttu-id="55aeb-320">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="55aeb-320">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55aeb-321">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="55aeb-321">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="55aeb-322">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="55aeb-322">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
