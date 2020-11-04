---
ms.openlocfilehash: ad8f4a5ea9bda7915731f879da96cf7e007c58fb
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755503"
---
# <a name="unity"></a>[<span data-ttu-id="be526-101">Unity</span><span class="sxs-lookup"><span data-stu-id="be526-101">Unity</span></span>](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="be526-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="be526-103">1. Download the latest version</span></span>

<span data-ttu-id="be526-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="be526-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="be526-105">目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="be526-105">The current recommendation is to use **Unity 2019** , which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="be526-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="be526-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="be526-107">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="be526-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="be526-109">[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="be526-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="be526-110">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="be526-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="be526-111">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="be526-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="be526-112">对于安装，我们建议完成策划的 [Unity 开发历程](../unity/unity-development-overview.md)的[入门部分](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="be526-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="be526-113">如果你已遵循 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="be526-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be526-114">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.4.0 和 Unity 2019.3.15 。</span><span class="sxs-lookup"><span data-stu-id="be526-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="be526-115">如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="be526-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="be526-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="be526-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="be526-117">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="be526-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="be526-118">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="be526-118">Other tools [optional]</span></span>
* <span data-ttu-id="be526-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="be526-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="be526-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="be526-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="be526-121">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="be526-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="be526-122">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="be526-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="be526-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="be526-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="be526-124">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="be526-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="be526-125">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="be526-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="be526-126">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="be526-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="be526-127">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="be526-127">For HoloLens development</span></span>

<span data-ttu-id="be526-128">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="be526-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="be526-129">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="be526-129">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="be526-130">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="be526-130">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="be526-131">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="be526-131">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="be526-132">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="be526-132">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="be526-133">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="be526-133">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="be526-134">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="be526-134">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="be526-135">如果你在使用 Reverb G2 头戴显示设备，请下载 Microsoft-Valve OpenXR 插件 (TODO: // 需要链接) 。</span><span class="sxs-lookup"><span data-stu-id="be526-135">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="be526-136">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="be526-136">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="be526-137">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="be526-137">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="be526-138">最低配置</span><span class="sxs-lookup"><span data-stu-id="be526-138">Minimum</span></span></th><th> <span data-ttu-id="be526-139">建议</span><span class="sxs-lookup"><span data-stu-id="be526-139">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="be526-140">处理器</span><span class="sxs-lookup"><span data-stu-id="be526-140">Processor</span></span></td><td> <span data-ttu-id="be526-141"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="be526-141"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="be526-142"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="be526-142"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-143">GPU</span><span class="sxs-lookup"><span data-stu-id="be526-143">GPU</span></span></td><td> <span data-ttu-id="be526-144"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-144"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="be526-145"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-145"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-146">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="be526-146">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="be526-147">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="be526-147">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-148">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="be526-148">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="be526-149">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="be526-149">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-150">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="be526-150">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-151">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="be526-151">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-152">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="be526-152">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="be526-153">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="be526-153">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-154">内存</span><span class="sxs-lookup"><span data-stu-id="be526-154">Memory</span></span></td><td> <span data-ttu-id="be526-155">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-155">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="be526-156">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-156">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-157">存储</span><span class="sxs-lookup"><span data-stu-id="be526-157">Storage</span></span></td><td colspan="2"> <span data-ttu-id="be526-158">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="be526-158">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-159">USB 端口</span><span class="sxs-lookup"><span data-stu-id="be526-159">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-160">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="be526-160">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-161">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="be526-161">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="be526-162">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="be526-162">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="be526-163">如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：</span><span class="sxs-lookup"><span data-stu-id="be526-163">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-164">开始你的 Unity 之旅</span><span class="sxs-lookup"><span data-stu-id="be526-164">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="be526-165">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="be526-165">Next Development Checkpoint</span></span>

<span data-ttu-id="be526-166">如果你遵循我们规划的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="be526-166">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-167">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="be526-167">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="be526-168">你可以随时返回到 [Unity 开发检查点](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="be526-168">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="be526-169">Unreal</span><span class="sxs-lookup"><span data-stu-id="be526-169">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="be526-171">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="be526-171">1. Download the latest version</span></span>

<span data-ttu-id="be526-172">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="be526-172">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="be526-173">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="be526-173">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="be526-175">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="be526-175">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="be526-176">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="be526-176">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="be526-177">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="be526-177">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="be526-178">对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="be526-178">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="be526-179">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="be526-179">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="be526-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="be526-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="be526-181">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="be526-181">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="be526-182">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="be526-182">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="be526-183">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="be526-183">Other tools [optional]</span></span>
* <span data-ttu-id="be526-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="be526-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="be526-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="be526-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="be526-186">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="be526-186">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="be526-187">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="be526-187">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="be526-188">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="be526-188">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="be526-189">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="be526-189">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="be526-190">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="be526-190">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="be526-191">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="be526-191">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="be526-192">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="be526-192">For HoloLens development</span></span>

<span data-ttu-id="be526-193">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="be526-193">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="be526-194">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="be526-194">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="be526-195">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="be526-195">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="be526-196">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="be526-196">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="be526-197">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="be526-197">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="be526-198">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="be526-198">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="be526-199">如果你在使用 Reverb G2 头戴显示设备，请下载 Microsoft-Valve OpenXR 插件 (TODO: // 需要链接) 。</span><span class="sxs-lookup"><span data-stu-id="be526-199">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="be526-200">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="be526-200">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="be526-201">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="be526-201">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="be526-202">最低配置</span><span class="sxs-lookup"><span data-stu-id="be526-202">Minimum</span></span></th><th> <span data-ttu-id="be526-203">建议</span><span class="sxs-lookup"><span data-stu-id="be526-203">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="be526-204">处理器</span><span class="sxs-lookup"><span data-stu-id="be526-204">Processor</span></span></td><td> <span data-ttu-id="be526-205"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="be526-205"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="be526-206"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="be526-206"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-207">GPU</span><span class="sxs-lookup"><span data-stu-id="be526-207">GPU</span></span></td><td> <span data-ttu-id="be526-208"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-208"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="be526-209"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-209"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-210">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="be526-210">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="be526-211">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="be526-211">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-212">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="be526-212">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="be526-213">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="be526-213">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-214">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="be526-214">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-215">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="be526-215">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-216">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="be526-216">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="be526-217">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="be526-217">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-218">内存</span><span class="sxs-lookup"><span data-stu-id="be526-218">Memory</span></span></td><td> <span data-ttu-id="be526-219">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-219">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="be526-220">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-220">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-221">存储</span><span class="sxs-lookup"><span data-stu-id="be526-221">Storage</span></span></td><td colspan="2"> <span data-ttu-id="be526-222">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="be526-222">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-223">USB 端口</span><span class="sxs-lookup"><span data-stu-id="be526-223">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-224">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="be526-224">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-225">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="be526-225">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="be526-226">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="be526-226">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="be526-227">如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：</span><span class="sxs-lookup"><span data-stu-id="be526-227">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-228">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="be526-228">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="be526-229">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="be526-229">Next Development Checkpoint</span></span>

<span data-ttu-id="be526-230">如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。</span><span class="sxs-lookup"><span data-stu-id="be526-230">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-231">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="be526-231">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="be526-232">你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="be526-232">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="be526-233">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="be526-233">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="be526-235">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="be526-235">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="be526-236">可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="be526-236">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="be526-237">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="be526-237">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="be526-238">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="be526-238">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="be526-239">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="be526-239">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="be526-240">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="be526-240">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="be526-241">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="be526-241">For HoloLens development</span></span>

<span data-ttu-id="be526-242">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="be526-242">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="be526-243">如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="be526-243">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="be526-244">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="be526-244">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="be526-245">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="be526-245">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="be526-246">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="be526-246">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="be526-247">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="be526-247">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="be526-248">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="be526-248">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="be526-249">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="be526-249">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="be526-250">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="be526-250">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="be526-251">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="be526-251">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="be526-252">最低配置</span><span class="sxs-lookup"><span data-stu-id="be526-252">Minimum</span></span></th><th> <span data-ttu-id="be526-253">建议</span><span class="sxs-lookup"><span data-stu-id="be526-253">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="be526-254">处理器</span><span class="sxs-lookup"><span data-stu-id="be526-254">Processor</span></span></td><td> <span data-ttu-id="be526-255"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="be526-255"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="be526-256"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="be526-256"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-257">GPU</span><span class="sxs-lookup"><span data-stu-id="be526-257">GPU</span></span></td><td> <span data-ttu-id="be526-258"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-258"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="be526-259"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="be526-259"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-260">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="be526-260">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="be526-261">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="be526-261">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-262">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="be526-262">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="be526-263">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="be526-263">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-264">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="be526-264">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-265">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="be526-265">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-266">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="be526-266">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="be526-267">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="be526-267">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-268">内存</span><span class="sxs-lookup"><span data-stu-id="be526-268">Memory</span></span></td><td> <span data-ttu-id="be526-269">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-269">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="be526-270">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="be526-270">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-271">存储</span><span class="sxs-lookup"><span data-stu-id="be526-271">Storage</span></span></td><td colspan="2"> <span data-ttu-id="be526-272">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="be526-272">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-273">USB 端口</span><span class="sxs-lookup"><span data-stu-id="be526-273">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="be526-274">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="be526-274">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="be526-275">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="be526-275">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="be526-276">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="be526-276">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="be526-277">如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：</span><span class="sxs-lookup"><span data-stu-id="be526-277">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-278">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="be526-278">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="be526-279">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="be526-279">Next Development Checkpoint</span></span>

<span data-ttu-id="be526-280">如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。</span><span class="sxs-lookup"><span data-stu-id="be526-280">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be526-281">HoloLens 2 安装</span><span class="sxs-lookup"><span data-stu-id="be526-281">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="be526-282">你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="be526-282">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
