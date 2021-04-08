---
ms.openlocfilehash: d7e248788d4c4976acbb9ff23177d354894f57dd
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105958284"
---
# <a name="unity"></a>[<span data-ttu-id="07796-101">Unity</span><span class="sxs-lookup"><span data-stu-id="07796-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a><span data-ttu-id="07796-103">1. 下载推荐的 Unity 版本</span><span class="sxs-lookup"><span data-stu-id="07796-103">1. Download the recommended Unity version</span></span> 

<span data-ttu-id="07796-104">用于 Mixed Reality 开发的最新推荐版本是 Unity 2019.4 LTS（长期支持）。</span><span class="sxs-lookup"><span data-stu-id="07796-104">The current recommended version for Mixed Reality development is **Unity 2019.4 LTS (Long Term Support)**.</span></span> <span data-ttu-id="07796-105">最好通过 Unity Hub 安装和管理 Unity。</span><span class="sxs-lookup"><span data-stu-id="07796-105">The best way to install and manage Unity is through the **Unity Hub**.</span></span> 

> [!NOTE]
>  <span data-ttu-id="07796-106">如果使用 Unity 2020 LTS，则可对 HoloLens 2 开发提供 Mixed Reality 支持。</span><span class="sxs-lookup"><span data-stu-id="07796-106">If you’re using Unity 2020 LTS, Mixed Reality support is available for HoloLens 2 development.</span></span> <span data-ttu-id="07796-107">但当前有一些已知问题。</span><span class="sxs-lookup"><span data-stu-id="07796-107">However, there are currently some known issues.</span></span> <span data-ttu-id="07796-108">今年晚些时候，这将成为推荐的 Unity 版本。</span><span class="sxs-lookup"><span data-stu-id="07796-108">This will become the recommended Unity version later this year.</span></span> 

<span data-ttu-id="07796-109">请参阅[选择 Unity 版本和 XR 插件](../unity/choosing-unity-version.md)，了解不同的 Unity 引擎和 XR 插件版本中提供了哪些 Mixed Reality 支持。</span><span class="sxs-lookup"><span data-stu-id="07796-109">See [Choosing a Unity version and XR plugin](../unity/choosing-unity-version.md) to learn what Mixed Reality support is available in different Unity engine and XR plugin versions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-110">下载 Unity Hub</span><span class="sxs-lookup"><span data-stu-id="07796-110">Download Unity Hub</span></span>](https://unity3d.com/get-unity/download)

<span data-ttu-id="07796-111">安装 Unity 时，请务必在“平台”下检查以下组件。</span><span class="sxs-lookup"><span data-stu-id="07796-111">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>
* <span data-ttu-id="07796-112">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="07796-112">**Universal Windows Platform Build Support**</span></span> 
* <span data-ttu-id="07796-113">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="07796-113">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平台生成支持选项](../../develop/images/Unity_Install_Option_UWP.png)

<span data-ttu-id="07796-115">如果安装 Unity 时未使用这些选项，可以通过 Unity Hub 中的“添加模块”菜单添加它们。</span><span class="sxs-lookup"><span data-stu-id="07796-115">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

![Unity Windows 生成支持选项](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="07796-117">2.安装混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="07796-117">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="07796-118">[混合现实功能工具](../unity/welcome-to-mr-feature-tool.md)是开发人员发现混合现实功能包并将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="07796-118">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="07796-119">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="07796-119">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="07796-120">验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。</span><span class="sxs-lookup"><span data-stu-id="07796-120">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="07796-121">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="07796-121">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="07796-123">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="07796-123">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="07796-124">遵循下面的[安装和使用说明](../unity/welcome-to-mr-feature-tool.md#system-requirements)，选择“Mixed Reality Toolkit Foundation”包，安装混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="07796-124">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="07796-125">建议完成我们策划的 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 开发历程中的入门部分。</span><span class="sxs-lookup"><span data-stu-id="07796-125">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="07796-126">如果你已遵循针对 HoloLens 的 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="07796-126">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07796-127">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.6.1 和 Unity 2019.4 LTS 。</span><span class="sxs-lookup"><span data-stu-id="07796-127">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="07796-128">如果你不想使用 MRTK for Unity，则需要[自行编写所有交互和行为的脚本](../unity/configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="07796-128">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="07796-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="07796-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="07796-130">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="07796-130">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="07796-131">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="07796-131">Other tools [optional]</span></span>
* <span data-ttu-id="07796-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="07796-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="07796-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="07796-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="07796-134">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="07796-134">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="07796-135">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="07796-135">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="07796-136">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="07796-136">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="07796-137">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="07796-137">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="07796-138">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="07796-138">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="07796-139">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="07796-139">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="07796-140">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="07796-140">For HoloLens development</span></span>

<span data-ttu-id="07796-141">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="07796-141">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="07796-142">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="07796-142">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="07796-143">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="07796-143">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="07796-144">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="07796-144">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="07796-145">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="07796-145">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="07796-146">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="07796-146">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="07796-147">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="07796-147">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="07796-148">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="07796-148">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="07796-149">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="07796-149">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="07796-150">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="07796-150">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="07796-151">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="07796-151">Possible solutions include:</span></span>

* <span data-ttu-id="07796-152">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="07796-152">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="07796-153">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="07796-153">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="07796-154">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="07796-154">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="07796-155">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="07796-155">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="07796-156">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="07796-156">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="07796-157">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="07796-157">I can't deploy over USB</span></span>

<span data-ttu-id="07796-158">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。</span><span class="sxs-lookup"><span data-stu-id="07796-158">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="07796-159">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="07796-159">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="07796-160">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="07796-160">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="07796-161">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="07796-161">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="07796-162">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="07796-162">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="07796-163">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="07796-163">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="07796-164">最低配置</span><span class="sxs-lookup"><span data-stu-id="07796-164">Minimum</span></span></th><th> <span data-ttu-id="07796-165">建议</span><span class="sxs-lookup"><span data-stu-id="07796-165">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="07796-166">处理器</span><span class="sxs-lookup"><span data-stu-id="07796-166">Processor</span></span></td><td> <span data-ttu-id="07796-167"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="07796-167"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="07796-168"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="07796-168"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-169">GPU</span><span class="sxs-lookup"><span data-stu-id="07796-169">GPU</span></span></td><td> <span data-ttu-id="07796-170"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-170"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="07796-171"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-171"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-172">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="07796-172">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="07796-173">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="07796-173">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-174">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="07796-174">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="07796-175">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="07796-175">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-176">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="07796-176">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-177">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="07796-177">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-178">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="07796-178">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="07796-179">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="07796-179">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-180">内存</span><span class="sxs-lookup"><span data-stu-id="07796-180">Memory</span></span></td><td> <span data-ttu-id="07796-181">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-181">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="07796-182">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-182">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-183">存储</span><span class="sxs-lookup"><span data-stu-id="07796-183">Storage</span></span></td><td colspan="2"> <span data-ttu-id="07796-184">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="07796-184">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-185">USB 端口</span><span class="sxs-lookup"><span data-stu-id="07796-185">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-186">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="07796-186">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-187">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="07796-187">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="07796-188">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="07796-188">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="07796-189">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="07796-189">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-190">开始针对 HoloLens 的 Unity历程</span><span class="sxs-lookup"><span data-stu-id="07796-190">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-191">开始针对 VR 的 Unity 历程</span><span class="sxs-lookup"><span data-stu-id="07796-191">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="07796-192">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="07796-192">Next Development Checkpoint</span></span>

<span data-ttu-id="07796-193">如果你遵循我们规划的针对 HoloLens 的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="07796-193">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-194">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="07796-194">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="07796-195">如果你遵循针对 VR 的 Unity 历程，那么接下来是设置项目。</span><span class="sxs-lookup"><span data-stu-id="07796-195">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-196">针对 WMR 配置项目</span><span class="sxs-lookup"><span data-stu-id="07796-196">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="07796-197">你可随时回到针对 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 的 Unity 开发检查点。</span><span class="sxs-lookup"><span data-stu-id="07796-197">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="07796-198">Unreal</span><span class="sxs-lookup"><span data-stu-id="07796-198">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="07796-200">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="07796-200">1. Download the latest version</span></span>

<span data-ttu-id="07796-201">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="07796-201">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="07796-202">转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。  </span><span class="sxs-lookup"><span data-stu-id="07796-202">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="07796-203">在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="07796-203">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="07796-204">![Unreal 安装选项 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="07796-204">![Unreal Install Option HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="07796-205">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="07796-205">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="07796-207">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="07796-207">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="07796-208">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="07796-208">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="07796-209">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="07796-209">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="07796-210">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="07796-210">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="07796-211">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="07796-211">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="07796-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="07796-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="07796-213">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="07796-213">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="07796-214">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="07796-214">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="07796-215">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="07796-215">Other tools [optional]</span></span>
* <span data-ttu-id="07796-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="07796-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="07796-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="07796-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="07796-218">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="07796-218">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="07796-219">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="07796-219">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="07796-220">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="07796-220">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="07796-221">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="07796-221">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="07796-222">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="07796-222">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="07796-223">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="07796-223">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="07796-224">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="07796-224">For HoloLens development</span></span>

<span data-ttu-id="07796-225">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="07796-225">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="07796-226">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="07796-226">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="07796-227">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="07796-227">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="07796-228">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="07796-228">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="07796-229">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="07796-229">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="07796-230">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="07796-230">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="07796-231">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="07796-231">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="07796-232">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="07796-232">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="07796-233">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="07796-233">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="07796-234">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="07796-234">Possible solutions include:</span></span>

* <span data-ttu-id="07796-235">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="07796-235">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="07796-236">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="07796-236">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="07796-237">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="07796-237">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="07796-238">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="07796-238">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="07796-239">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="07796-239">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="07796-240">我无法通过 USB 进行部署</span><span class="sxs-lookup"><span data-stu-id="07796-240">I can't deploy over USB</span></span>

<span data-ttu-id="07796-241">如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。</span><span class="sxs-lookup"><span data-stu-id="07796-241">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="07796-242">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="07796-242">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="07796-243">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="07796-243">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="07796-244">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="07796-244">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="07796-245">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="07796-245">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="07796-246">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="07796-246">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="07796-247">最低配置</span><span class="sxs-lookup"><span data-stu-id="07796-247">Minimum</span></span></th><th> <span data-ttu-id="07796-248">建议</span><span class="sxs-lookup"><span data-stu-id="07796-248">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="07796-249">处理器</span><span class="sxs-lookup"><span data-stu-id="07796-249">Processor</span></span></td><td> <span data-ttu-id="07796-250"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="07796-250"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="07796-251"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="07796-251"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-252">GPU</span><span class="sxs-lookup"><span data-stu-id="07796-252">GPU</span></span></td><td> <span data-ttu-id="07796-253"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-253"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="07796-254"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-254"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-255">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="07796-255">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="07796-256">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="07796-256">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-257">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="07796-257">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="07796-258">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="07796-258">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-259">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="07796-259">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-260">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="07796-260">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-261">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="07796-261">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="07796-262">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="07796-262">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-263">内存</span><span class="sxs-lookup"><span data-stu-id="07796-263">Memory</span></span></td><td> <span data-ttu-id="07796-264">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-264">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="07796-265">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-265">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-266">存储</span><span class="sxs-lookup"><span data-stu-id="07796-266">Storage</span></span></td><td colspan="2"> <span data-ttu-id="07796-267">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="07796-267">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-268">USB 端口</span><span class="sxs-lookup"><span data-stu-id="07796-268">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-269">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="07796-269">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-270">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="07796-270">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="07796-271">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="07796-271">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="07796-272">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="07796-272">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-273">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="07796-273">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="07796-274">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="07796-274">Next Development Checkpoint</span></span>

<span data-ttu-id="07796-275">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="07796-275">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-276">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="07796-276">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="07796-277">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="07796-277">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="07796-278">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="07796-278">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="07796-280">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="07796-280">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="07796-281">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="07796-281">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="07796-282">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="07796-282">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="07796-283">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="07796-283">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="07796-284">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="07796-284">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="07796-285">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="07796-285">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="07796-286">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="07796-286">For HoloLens development</span></span>

<span data-ttu-id="07796-287">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="07796-287">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="07796-288">如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。</span><span class="sxs-lookup"><span data-stu-id="07796-288">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="07796-289">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="07796-289">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="07796-290">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="07796-290">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="07796-291">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="07796-291">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="07796-292">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="07796-292">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="07796-293">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="07796-293">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="07796-294">“开发人员模式”设置呈灰显</span><span class="sxs-lookup"><span data-stu-id="07796-294">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="07796-295">如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="07796-295">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="07796-296">在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。</span><span class="sxs-lookup"><span data-stu-id="07796-296">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="07796-297">但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。</span><span class="sxs-lookup"><span data-stu-id="07796-297">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="07796-298">可能的解决方案包括：</span><span class="sxs-lookup"><span data-stu-id="07796-298">Possible solutions include:</span></span>

* <span data-ttu-id="07796-299">要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="07796-299">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="07796-300">建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="07796-300">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="07796-301">此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置</span><span class="sxs-lookup"><span data-stu-id="07796-301">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="07796-302">使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="07796-302">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="07796-303">有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。</span><span class="sxs-lookup"><span data-stu-id="07796-303">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="07796-304">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="07796-304">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="07796-305">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="07796-305">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="07796-306">不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="07796-306">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="07796-307">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="07796-307">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="07796-308">某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="07796-308">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="07796-309">最低配置</span><span class="sxs-lookup"><span data-stu-id="07796-309">Minimum</span></span></th><th> <span data-ttu-id="07796-310">建议</span><span class="sxs-lookup"><span data-stu-id="07796-310">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="07796-311">处理器</span><span class="sxs-lookup"><span data-stu-id="07796-311">Processor</span></span></td><td> <span data-ttu-id="07796-312"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="07796-312"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="07796-313"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="07796-313"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-314">GPU</span><span class="sxs-lookup"><span data-stu-id="07796-314">GPU</span></span></td><td> <span data-ttu-id="07796-315"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-315"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="07796-316"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="07796-316"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-317">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="07796-317">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="07796-318">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="07796-318">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-319">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="07796-319">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="07796-320">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="07796-320">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-321">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="07796-321">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-322">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="07796-322">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-323">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="07796-323">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="07796-324">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="07796-324">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-325">内存</span><span class="sxs-lookup"><span data-stu-id="07796-325">Memory</span></span></td><td> <span data-ttu-id="07796-326">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-326">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="07796-327">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="07796-327">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-328">存储</span><span class="sxs-lookup"><span data-stu-id="07796-328">Storage</span></span></td><td colspan="2"> <span data-ttu-id="07796-329">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="07796-329">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-330">USB 端口</span><span class="sxs-lookup"><span data-stu-id="07796-330">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="07796-331">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="07796-331">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="07796-332">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="07796-332">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="07796-333">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="07796-333">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="07796-334">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="07796-334">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-335">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="07796-335">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="07796-336">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="07796-336">Next Development Checkpoint</span></span>

<span data-ttu-id="07796-337">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="07796-337">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07796-338">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="07796-338">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="07796-339">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="07796-339">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>