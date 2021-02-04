---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244924"
---
# <a name="unity"></a>[<span data-ttu-id="8e0f2-101">Unity</span><span class="sxs-lookup"><span data-stu-id="8e0f2-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="8e0f2-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="8e0f2-103">1. Download the latest version</span></span>

<span data-ttu-id="8e0f2-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="8e0f2-105">目前的建议是使用 [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-105">The current recommendation is to use **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="8e0f2-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="8e0f2-107">2.安装混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="8e0f2-107">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="8e0f2-108">[混合现实功能工具](../unity/welcome-to-mr-feature-tool.md)是开发人员发现混合现实功能包并将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-108">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="8e0f2-109">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="8e0f2-110">验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-110">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="8e0f2-111">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="8e0f2-111">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="8e0f2-113">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-113">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="8e0f2-114">遵循下面的[安装和使用说明](../unity/welcome-to-mr-feature-tool.md#system-requirements)，选择“Mixed Reality Toolkit Foundation”包，安装混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-114">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="8e0f2-115">建议完成我们策划的 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 开发历程中的入门部分。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-115">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="8e0f2-116">如果你已遵循针对 HoloLens 的 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-116">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e0f2-117">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.5.1 和 Unity 2019.4 LTS 。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-117">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.5.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-118">如果你不想使用 MRTK for Unity，则需要[自行编写所有交互和行为的脚本](../unity/configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-118">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8e0f2-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="8e0f2-120">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="8e0f2-120">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="8e0f2-121">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="8e0f2-121">Other tools [optional]</span></span>
* <span data-ttu-id="8e0f2-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="8e0f2-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="8e0f2-124">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-124">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="8e0f2-125">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-125">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="8e0f2-126">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-126">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="8e0f2-127">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-127">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-128">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-128">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="8e0f2-129">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-129">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="8e0f2-130">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-130">For HoloLens development</span></span>

<span data-ttu-id="8e0f2-131">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-131">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="8e0f2-132">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-132">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="8e0f2-133">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-133">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="8e0f2-134">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-134">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="8e0f2-135">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-135">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="8e0f2-136">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="8e0f2-136">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="8e0f2-137">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="8e0f2-137">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="8e0f2-138">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-138">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="8e0f2-139">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-139">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="8e0f2-140">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-140">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="8e0f2-141">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-141">Possible solutions include:</span></span>

* <span data-ttu-id="8e0f2-142">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="8e0f2-142">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="8e0f2-143">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-143">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="8e0f2-144">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-144">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="8e0f2-145">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-145">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-146">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-146">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="8e0f2-147">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="8e0f2-147">I can't deploy over USB</span></span>

<span data-ttu-id="8e0f2-148">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-148">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="8e0f2-149">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="8e0f2-149">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="8e0f2-150">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-150">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="8e0f2-151">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-151">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="8e0f2-152">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-152">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="8e0f2-153">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-153">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="8e0f2-154">最低配置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-154">Minimum</span></span></th><th> <span data-ttu-id="8e0f2-155">建议</span><span class="sxs-lookup"><span data-stu-id="8e0f2-155">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8e0f2-156">处理器</span><span class="sxs-lookup"><span data-stu-id="8e0f2-156">Processor</span></span></td><td> <span data-ttu-id="8e0f2-157"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-157"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="8e0f2-158"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-158"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-159">GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-159">GPU</span></span></td><td> <span data-ttu-id="8e0f2-160"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-160"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="8e0f2-161"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-161"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-162">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="8e0f2-162">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-163">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="8e0f2-163">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-164">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="8e0f2-164">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-165">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="8e0f2-165">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-166">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-166">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-167">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-167">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-168">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="8e0f2-168">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-169">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="8e0f2-169">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-170">内存</span><span class="sxs-lookup"><span data-stu-id="8e0f2-170">Memory</span></span></td><td> <span data-ttu-id="8e0f2-171">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-171">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="8e0f2-172">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-172">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-173">存储</span><span class="sxs-lookup"><span data-stu-id="8e0f2-173">Storage</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-174">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="8e0f2-174">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-175">USB 端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-175">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-176">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="8e0f2-176">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-177">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="8e0f2-177">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-178">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-178">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="8e0f2-179">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-179">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-180">开始针对 HoloLens 的 Unity历程</span><span class="sxs-lookup"><span data-stu-id="8e0f2-180">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-181">开始针对 VR 的 Unity 历程</span><span class="sxs-lookup"><span data-stu-id="8e0f2-181">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="8e0f2-182">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="8e0f2-182">Next Development Checkpoint</span></span>

<span data-ttu-id="8e0f2-183">如果你遵循我们规划的针对 HoloLens 的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-183">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-184">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="8e0f2-184">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="8e0f2-185">如果你遵循针对 VR 的 Unity 历程，那么接下来是设置项目。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-185">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-186">针对 WMR 配置项目</span><span class="sxs-lookup"><span data-stu-id="8e0f2-186">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="8e0f2-187">你可随时回到针对 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 的 Unity 开发检查点。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-187">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="8e0f2-188">Unreal</span><span class="sxs-lookup"><span data-stu-id="8e0f2-188">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="8e0f2-190">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="8e0f2-190">1. Download the latest version</span></span>

<span data-ttu-id="8e0f2-191">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-191">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="8e0f2-192">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-192">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="8e0f2-194">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-194">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="8e0f2-195">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-195">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8e0f2-196">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-196">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="8e0f2-197">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-197">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="8e0f2-198">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-198">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8e0f2-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="8e0f2-200">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="8e0f2-200">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="8e0f2-201">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-201">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="8e0f2-202">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="8e0f2-202">Other tools [optional]</span></span>
* <span data-ttu-id="8e0f2-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="8e0f2-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="8e0f2-205">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-205">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="8e0f2-206">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-206">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="8e0f2-207">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-207">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="8e0f2-208">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-208">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-209">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-209">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="8e0f2-210">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-210">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="8e0f2-211">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-211">For HoloLens development</span></span>

<span data-ttu-id="8e0f2-212">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-212">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="8e0f2-213">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-213">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="8e0f2-214">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-214">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="8e0f2-215">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-215">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="8e0f2-216">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="8e0f2-216">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="8e0f2-217">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="8e0f2-217">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="8e0f2-218">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-218">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="8e0f2-219">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-219">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="8e0f2-220">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-220">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="8e0f2-221">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-221">Possible solutions include:</span></span>

* <span data-ttu-id="8e0f2-222">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="8e0f2-222">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="8e0f2-223">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-223">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="8e0f2-224">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-224">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="8e0f2-225">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-225">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-226">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-226">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="8e0f2-227">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="8e0f2-227">I can't deploy over USB</span></span>

<span data-ttu-id="8e0f2-228">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-228">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="8e0f2-229">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="8e0f2-229">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="8e0f2-230">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-230">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="8e0f2-231">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-231">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="8e0f2-232">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-232">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="8e0f2-233">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-233">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="8e0f2-234">最低配置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-234">Minimum</span></span></th><th> <span data-ttu-id="8e0f2-235">建议</span><span class="sxs-lookup"><span data-stu-id="8e0f2-235">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8e0f2-236">处理器</span><span class="sxs-lookup"><span data-stu-id="8e0f2-236">Processor</span></span></td><td> <span data-ttu-id="8e0f2-237"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-237"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="8e0f2-238"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-238"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-239">GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-239">GPU</span></span></td><td> <span data-ttu-id="8e0f2-240"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-240"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="8e0f2-241"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-241"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-242">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="8e0f2-242">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-243">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="8e0f2-243">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-244">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="8e0f2-244">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-245">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="8e0f2-245">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-246">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-246">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-247">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-247">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-248">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="8e0f2-248">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-249">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="8e0f2-249">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-250">内存</span><span class="sxs-lookup"><span data-stu-id="8e0f2-250">Memory</span></span></td><td> <span data-ttu-id="8e0f2-251">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-251">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="8e0f2-252">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-252">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-253">存储</span><span class="sxs-lookup"><span data-stu-id="8e0f2-253">Storage</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-254">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="8e0f2-254">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-255">USB 端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-255">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-256">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="8e0f2-256">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-257">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="8e0f2-257">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-258">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-258">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="8e0f2-259">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-259">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-260">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="8e0f2-260">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="8e0f2-261">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="8e0f2-261">Next Development Checkpoint</span></span>

<span data-ttu-id="8e0f2-262">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-262">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-263">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="8e0f2-263">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="8e0f2-264">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-264">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="8e0f2-265">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-265">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="8e0f2-267">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-267">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="8e0f2-268">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-268">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="8e0f2-269">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-269">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="8e0f2-270">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-270">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="8e0f2-271">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-271">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="8e0f2-272">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-272">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="8e0f2-273">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="8e0f2-273">For HoloLens development</span></span>

<span data-ttu-id="8e0f2-274">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-274">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="8e0f2-275">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-275">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="8e0f2-276">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-276">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="8e0f2-277">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-277">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-278">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-278">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="8e0f2-279">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-279">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="8e0f2-280">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="8e0f2-280">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="8e0f2-281">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="8e0f2-281">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="8e0f2-282">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-282">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="8e0f2-283">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-283">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="8e0f2-284">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-284">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="8e0f2-285">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-285">Possible solutions include:</span></span>

* <span data-ttu-id="8e0f2-286">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="8e0f2-286">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="8e0f2-287">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-287">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="8e0f2-288">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-288">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="8e0f2-289">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="8e0f2-289">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="8e0f2-290">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-290">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="8e0f2-291">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="8e0f2-291">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="8e0f2-292">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-292">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="8e0f2-293">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-293">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="8e0f2-294">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-294">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="8e0f2-295">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-295">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="8e0f2-296">最低配置</span><span class="sxs-lookup"><span data-stu-id="8e0f2-296">Minimum</span></span></th><th> <span data-ttu-id="8e0f2-297">建议</span><span class="sxs-lookup"><span data-stu-id="8e0f2-297">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="8e0f2-298">处理器</span><span class="sxs-lookup"><span data-stu-id="8e0f2-298">Processor</span></span></td><td> <span data-ttu-id="8e0f2-299"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-299"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="8e0f2-300"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-300"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-301">GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-301">GPU</span></span></td><td> <span data-ttu-id="8e0f2-302"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-302"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="8e0f2-303"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="8e0f2-303"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-304">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="8e0f2-304">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-305">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="8e0f2-305">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-306">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="8e0f2-306">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-307">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="8e0f2-307">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-308">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-308">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-309">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-309">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-310">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="8e0f2-310">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-311">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="8e0f2-311">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-312">内存</span><span class="sxs-lookup"><span data-stu-id="8e0f2-312">Memory</span></span></td><td> <span data-ttu-id="8e0f2-313">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-313">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="8e0f2-314">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="8e0f2-314">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-315">存储</span><span class="sxs-lookup"><span data-stu-id="8e0f2-315">Storage</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-316">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="8e0f2-316">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-317">USB 端口</span><span class="sxs-lookup"><span data-stu-id="8e0f2-317">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-318">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="8e0f2-318">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="8e0f2-319">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="8e0f2-319">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="8e0f2-320">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="8e0f2-320">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="8e0f2-321">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="8e0f2-321">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-322">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="8e0f2-322">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="8e0f2-323">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="8e0f2-323">Next Development Checkpoint</span></span>

<span data-ttu-id="8e0f2-324">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-324">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e0f2-325">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="8e0f2-325">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="8e0f2-326">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="8e0f2-326">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>