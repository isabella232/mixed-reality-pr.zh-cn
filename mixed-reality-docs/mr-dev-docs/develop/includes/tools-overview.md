---
ms.openlocfilehash: b6e75419ef9cdd4595e23e6217ab1b1762cd134e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605337"
---
# <a name="unity"></a>[<span data-ttu-id="cb184-101">Unity</span><span class="sxs-lookup"><span data-stu-id="cb184-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="cb184-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="cb184-103">1. Download the latest version</span></span>

<span data-ttu-id="cb184-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="cb184-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="cb184-105">目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="cb184-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="cb184-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="cb184-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="cb184-107">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="cb184-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="cb184-109">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="cb184-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="cb184-110">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="cb184-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="cb184-111">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="cb184-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="cb184-112">若要安装，建议完成我们策划的 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 开发历程中的入门部分。</span><span class="sxs-lookup"><span data-stu-id="cb184-112">For installation, we recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="cb184-113">如果你已遵循针对 HoloLens 的 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="cb184-113">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb184-114">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.4.0 和 Unity 2019.3.15 。</span><span class="sxs-lookup"><span data-stu-id="cb184-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-115">如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="cb184-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cb184-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="cb184-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="cb184-117">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="cb184-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="cb184-118">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="cb184-118">Other tools [optional]</span></span>
* <span data-ttu-id="cb184-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="cb184-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="cb184-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="cb184-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb184-121">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="cb184-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="cb184-122">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="cb184-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb184-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="cb184-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb184-124">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="cb184-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-125">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="cb184-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb184-126">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="cb184-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb184-127">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="cb184-127">For HoloLens development</span></span>

<span data-ttu-id="cb184-128">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb184-129">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="cb184-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="cb184-130">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="cb184-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb184-131">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="cb184-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="cb184-132">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="cb184-133">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="cb184-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="cb184-134">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="cb184-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="cb184-135">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="cb184-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="cb184-136">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="cb184-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="cb184-137">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="cb184-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="cb184-138">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="cb184-138">Possible solutions include:</span></span>

* <span data-ttu-id="cb184-139">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="cb184-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="cb184-140">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="cb184-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="cb184-141">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="cb184-141">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="cb184-142">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="cb184-142">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-143">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="cb184-143">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="cb184-144">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="cb184-144">I can't deploy over USB</span></span>

<span data-ttu-id="cb184-145">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。</span><span class="sxs-lookup"><span data-stu-id="cb184-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb184-146">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="cb184-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb184-147">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="cb184-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb184-148">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="cb184-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb184-149">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="cb184-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb184-150">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="cb184-150">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb184-151">最低配置</span><span class="sxs-lookup"><span data-stu-id="cb184-151">Minimum</span></span></th><th> <span data-ttu-id="cb184-152">建议</span><span class="sxs-lookup"><span data-stu-id="cb184-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb184-153">处理器</span><span class="sxs-lookup"><span data-stu-id="cb184-153">Processor</span></span></td><td> <span data-ttu-id="cb184-154"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="cb184-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb184-155"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="cb184-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-156">GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-156">GPU</span></span></td><td> <span data-ttu-id="cb184-157"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb184-158"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-159">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="cb184-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb184-160">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="cb184-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-161">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="cb184-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb184-162">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="cb184-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-163">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="cb184-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-164">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="cb184-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-165">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="cb184-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb184-166">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="cb184-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-167">内存</span><span class="sxs-lookup"><span data-stu-id="cb184-167">Memory</span></span></td><td> <span data-ttu-id="cb184-168">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb184-169">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-170">存储</span><span class="sxs-lookup"><span data-stu-id="cb184-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb184-171">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="cb184-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-172">USB 端口</span><span class="sxs-lookup"><span data-stu-id="cb184-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-173">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="cb184-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb184-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb184-175">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="cb184-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="cb184-176">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="cb184-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-177">开始针对 HoloLens 的 Unity历程</span><span class="sxs-lookup"><span data-stu-id="cb184-177">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-178">开始针对 VR 的 Unity 历程</span><span class="sxs-lookup"><span data-stu-id="cb184-178">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="cb184-179">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="cb184-179">Next Development Checkpoint</span></span>

<span data-ttu-id="cb184-180">如果你遵循我们规划的针对 HoloLens 的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="cb184-180">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-181">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="cb184-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="cb184-182">如果你遵循针对 VR 的 Unity 历程，那么接下来是设置项目。</span><span class="sxs-lookup"><span data-stu-id="cb184-182">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-183">针对 WMR 配置项目</span><span class="sxs-lookup"><span data-stu-id="cb184-183">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="cb184-184">你可随时回到针对 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 的 Unity 开发检查点。</span><span class="sxs-lookup"><span data-stu-id="cb184-184">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="cb184-185">Unreal</span><span class="sxs-lookup"><span data-stu-id="cb184-185">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="cb184-187">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="cb184-187">1. Download the latest version</span></span>

<span data-ttu-id="cb184-188">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="cb184-188">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="cb184-189">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="cb184-189">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="cb184-191">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="cb184-191">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="cb184-192">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="cb184-192">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="cb184-193">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="cb184-193">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="cb184-194">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="cb184-194">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="cb184-195">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="cb184-195">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cb184-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="cb184-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="cb184-197">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="cb184-197">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="cb184-198">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="cb184-198">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="cb184-199">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="cb184-199">Other tools [optional]</span></span>
* <span data-ttu-id="cb184-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="cb184-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="cb184-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="cb184-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb184-202">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="cb184-202">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="cb184-203">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="cb184-203">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb184-204">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="cb184-204">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb184-205">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="cb184-205">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-206">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="cb184-206">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb184-207">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="cb184-207">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb184-208">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="cb184-208">For HoloLens development</span></span>

<span data-ttu-id="cb184-209">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-209">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb184-210">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="cb184-210">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="cb184-211">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="cb184-211">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb184-212">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-212">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="cb184-213">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="cb184-213">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="cb184-214">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="cb184-214">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="cb184-215">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="cb184-215">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="cb184-216">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="cb184-216">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="cb184-217">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="cb184-217">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="cb184-218">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="cb184-218">Possible solutions include:</span></span>

* <span data-ttu-id="cb184-219">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="cb184-219">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="cb184-220">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="cb184-220">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="cb184-221">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="cb184-221">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="cb184-222">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="cb184-222">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-223">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="cb184-223">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="cb184-224">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="cb184-224">I can't deploy over USB</span></span>

<span data-ttu-id="cb184-225">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。</span><span class="sxs-lookup"><span data-stu-id="cb184-225">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb184-226">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="cb184-226">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb184-227">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="cb184-227">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb184-228">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="cb184-228">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb184-229">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="cb184-229">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb184-230">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="cb184-230">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb184-231">最低配置</span><span class="sxs-lookup"><span data-stu-id="cb184-231">Minimum</span></span></th><th> <span data-ttu-id="cb184-232">建议</span><span class="sxs-lookup"><span data-stu-id="cb184-232">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb184-233">处理器</span><span class="sxs-lookup"><span data-stu-id="cb184-233">Processor</span></span></td><td> <span data-ttu-id="cb184-234"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="cb184-234"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb184-235"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="cb184-235"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-236">GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-236">GPU</span></span></td><td> <span data-ttu-id="cb184-237"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-237"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb184-238"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-238"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-239">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="cb184-239">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb184-240">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="cb184-240">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-241">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="cb184-241">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb184-242">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="cb184-242">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-243">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="cb184-243">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-244">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="cb184-244">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-245">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="cb184-245">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb184-246">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="cb184-246">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-247">内存</span><span class="sxs-lookup"><span data-stu-id="cb184-247">Memory</span></span></td><td> <span data-ttu-id="cb184-248">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-248">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb184-249">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-249">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-250">存储</span><span class="sxs-lookup"><span data-stu-id="cb184-250">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb184-251">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="cb184-251">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-252">USB 端口</span><span class="sxs-lookup"><span data-stu-id="cb184-252">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-253">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="cb184-253">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-254">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb184-254">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb184-255">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="cb184-255">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="cb184-256">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="cb184-256">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-257">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="cb184-257">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="cb184-258">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="cb184-258">Next Development Checkpoint</span></span>

<span data-ttu-id="cb184-259">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="cb184-259">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-260">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="cb184-260">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="cb184-261">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="cb184-261">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="cb184-262">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cb184-262">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="cb184-264">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="cb184-264">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="cb184-265">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="cb184-265">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="cb184-266">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="cb184-266">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="cb184-267">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="cb184-267">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="cb184-268">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="cb184-268">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="cb184-269">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="cb184-269">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="cb184-270">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="cb184-270">For HoloLens development</span></span>

<span data-ttu-id="cb184-271">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-271">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="cb184-272">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="cb184-272">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="cb184-273">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="cb184-273">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="cb184-274">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="cb184-274">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-275">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="cb184-275">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="cb184-276">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="cb184-276">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="cb184-277">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="cb184-277">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="cb184-278">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="cb184-278">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="cb184-279">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="cb184-279">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="cb184-280">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="cb184-280">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="cb184-281">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="cb184-281">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="cb184-282">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="cb184-282">Possible solutions include:</span></span>

* <span data-ttu-id="cb184-283">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="cb184-283">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="cb184-284">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="cb184-284">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="cb184-285">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="cb184-285">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="cb184-286">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="cb184-286">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="cb184-287">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="cb184-287">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="cb184-288">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="cb184-288">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="cb184-289">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="cb184-289">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="cb184-290">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="cb184-290">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="cb184-291">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="cb184-291">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="cb184-292">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="cb184-292">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="cb184-293">最低配置</span><span class="sxs-lookup"><span data-stu-id="cb184-293">Minimum</span></span></th><th> <span data-ttu-id="cb184-294">建议</span><span class="sxs-lookup"><span data-stu-id="cb184-294">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cb184-295">处理器</span><span class="sxs-lookup"><span data-stu-id="cb184-295">Processor</span></span></td><td> <span data-ttu-id="cb184-296"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="cb184-296"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="cb184-297"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="cb184-297"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-298">GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-298">GPU</span></span></td><td> <span data-ttu-id="cb184-299"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-299"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="cb184-300"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="cb184-300"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-301">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="cb184-301">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="cb184-302">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="cb184-302">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-303">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="cb184-303">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="cb184-304">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="cb184-304">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-305">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="cb184-305">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-306">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="cb184-306">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-307">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="cb184-307">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="cb184-308">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="cb184-308">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-309">内存</span><span class="sxs-lookup"><span data-stu-id="cb184-309">Memory</span></span></td><td> <span data-ttu-id="cb184-310">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-310">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="cb184-311">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="cb184-311">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-312">存储</span><span class="sxs-lookup"><span data-stu-id="cb184-312">Storage</span></span></td><td colspan="2"> <span data-ttu-id="cb184-313">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="cb184-313">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-314">USB 端口</span><span class="sxs-lookup"><span data-stu-id="cb184-314">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="cb184-315">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="cb184-315">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="cb184-316">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="cb184-316">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="cb184-317">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="cb184-317">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="cb184-318">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="cb184-318">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-319">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="cb184-319">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="cb184-320">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="cb184-320">Next Development Checkpoint</span></span>

<span data-ttu-id="cb184-321">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="cb184-321">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cb184-322">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="cb184-322">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="cb184-323">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="cb184-323">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>