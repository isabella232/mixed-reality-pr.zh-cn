---
title: 全息远程处理
description: 文档全息远程处理 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176645"
---
# <a name="holographic-remoting"></a><span data-ttu-id="ee7a3-104">全息远程处理</span><span class="sxs-lookup"><span data-stu-id="ee7a3-104">Holographic remoting</span></span>

<span data-ttu-id="ee7a3-105">全息远程处理使用 Wi-Fi 或 USB 电缆连接将全息内容从电脑实时流式Microsoft HoloLens到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="ee7a3-106">在开发混合现实应用程序时，此功能可以显著提高开发人员的工作效率。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="ee7a3-107">下面提到的 XR SDK 是指 Unity [2019.3](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)及更新的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="ee7a3-108">请参阅 [此处](../../configuration/getting-started-with-mrtk-and-xrsdk.md) ，详细了解将 XR SDK 与 MRTK 一起使用。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="ee7a3-109">旧版 XR 是指 Unity 2018 中包含的现有 XR 管道，在 Unity 2019.3 中已弃用，在 Unity 2020 中已删除。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="ee7a3-110">初始设置</span><span class="sxs-lookup"><span data-stu-id="ee7a3-110">Initial setup</span></span>

<span data-ttu-id="ee7a3-111">若要启用远程处理HoloLens，必须确保项目使用最新的远程处理组件。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="ee7a3-112">打开 **窗口> 程序包管理器**</span><span class="sxs-lookup"><span data-stu-id="ee7a3-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="ee7a3-113">如果使用旧版 XR：验证是否安装了最新版本 **Windows Mixed Reality** 包。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="ee7a3-114">如果使用 XR SDK：验证是否安装了最新版本 **Windows XR 插件** 包。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="ee7a3-115">确保最新的全息远程处理应用程序已安装在 HoloLens 上，通过 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="ee7a3-116">请继续阅读 [旧版 XR 设置说明](#legacy-xr-setup-instructions) 或 [XR SDK](#xr-sdk-setup-instructions) 安装说明，具体取决于项目中使用的管道。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="ee7a3-117">旧版 XR 安装说明</span><span class="sxs-lookup"><span data-stu-id="ee7a3-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="ee7a3-118">以下说明仅适用于使用远程处理HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="ee7a3-119">如果仅使用第一代 HoloLens (执行远程) ，请跳到使用[Wi-Fi HoloLens远程处理](#connecting-to-the-hololens-with-wi-fi)。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="ee7a3-120">使用远程HoloLens 2，MRTK 中添加了对远程处理手部和眼动跟踪数据的支持。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="ee7a3-121">若要启用这些功能，请按照将 [DotNetWinRT](#import-dotnetwinrt-into-the-project)导入项目 中记录的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="ee7a3-122">导入后，下一步是 **选择"混合** 现实Toolkit  >    >  **实用工具Windows Mixed Reality**  >    >  **检查配置"。**</span><span class="sxs-lookup"><span data-stu-id="ee7a3-122">Once imported, the next step is to select **Mixed Reality** > **Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="ee7a3-123">此步骤添加启用 DotNetWinRT 依赖项的脚本定义。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="ee7a3-124">使用 Unity 2019.4 及更高版本时，不需要运行"检查配置"实用工具。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="ee7a3-125">若要启用手部眼部跟踪和眼动跟踪，请按照通过 **Unity** 包导入HoloLens 2远程处理调试"部分中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="ee7a3-126">调试HoloLens 2 Unity 包导入进行远程处理</span><span class="sxs-lookup"><span data-stu-id="ee7a3-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="ee7a3-127">如果HoloLens 2和眼动跟踪无法通过远程处理工作，则存在一些常见的潜在问题。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="ee7a3-128">下面按应检查的顺序列出它们。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="ee7a3-129">在 **Unity 2019.3** 或更高版本上运行时，这些问题尤其相关。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="ee7a3-130">将 DotNetWinRT 导入项目</span><span class="sxs-lookup"><span data-stu-id="ee7a3-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="ee7a3-131">下载 [混合现实功能工具](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="ee7a3-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="ee7a3-132">在" **发现功能"视图中** ，选择" *混合现实 WinRT 投影"*</span><span class="sxs-lookup"><span data-stu-id="ee7a3-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![选择 DotNetWinRT 包](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="ee7a3-134">单击 **"获取功能** "并继续 [导入包](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="ee7a3-135">DOTNETWINRT_PRESENT定义写入播放器设置</span><span class="sxs-lookup"><span data-stu-id="ee7a3-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="ee7a3-136">使用 Unity 2019.4 及更高版本时，DOTNETWINRT_PRESENT定义包含在相应的 .asmdef 文件中，而不是包含在 Unity Player 设置。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="ee7a3-137">"检查配置"步骤不是必需的。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="ee7a3-138">从 MRTK 版本 2.5.0 开始，出于性能原因，#define自动设置此版本。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="ee7a3-139">若要启用此标志，请使用"混合现实Toolkit  >  **实用工具**  >  **"Windows Mixed Reality"**  >  **检查配置"** 菜单项。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="ee7a3-140">"检查配置"项不显示确认。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="ee7a3-141">若要确认已设置定义，请导航到 Unity Player 设置。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="ee7a3-142">然后，在"UWP"选项卡下，在"其他设置"下查看"脚本定义符号"。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="ee7a3-143">请确保DOTNETWINRT_PRESENT正确写入该列表。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="ee7a3-144">如果存在，则此步骤成功。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT 存在](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="ee7a3-146">删除HoloLens 2远程处理支持</span><span class="sxs-lookup"><span data-stu-id="ee7a3-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="ee7a3-147">如果由于存在 DotNetWinRT 适配器而发生冲突或其他问题，请访问我们的帮助资源 之 [一](../../index.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="ee7a3-148">XR SDK 安装说明</span><span class="sxs-lookup"><span data-stu-id="ee7a3-148">XR SDK setup instructions</span></span>

<span data-ttu-id="ee7a3-149">按照[Windows Mixed Reality MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality)和 XR SDK 入门"页上的说明进行操作，并确保执行编辑器内远程处理HoloLens步骤。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="ee7a3-150">使用 HoloLens 连接到Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="ee7a3-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="ee7a3-151">配置项目后，可以建立与项目HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="ee7a3-152">在 **">生成设置** 中，确保项目生成类型设置为"通用Windows **平台"**</span><span class="sxs-lookup"><span data-stu-id="ee7a3-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="ee7a3-153">在HoloLens，启动 **全息远程处理** 应用程序。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="ee7a3-154">在 Unity 中，如果使用的是旧版 **XR) /Windows XR** 插件远程 (，请选择"窗口"> XR >全息仿真 (（如果使用 XR SDK) ）。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![启动全息仿真](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="ee7a3-156">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="ee7a3-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![设置仿真模式](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="ee7a3-158"> (**_仅适用于旧版 XR)_** 选择 **设备版本**。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![选择"设备版本"](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="ee7a3-160">使用全息远程处理播放器应用程序显示的 IP 地址，设置" **远程计算机"** 字段。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![输入 IP 地址](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="ee7a3-162">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="ee7a3-163">如果无法连接，请确保HoloLens 2连接到电脑并重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="ee7a3-164">使用 USB HoloLens连接到设备</span><span class="sxs-lookup"><span data-stu-id="ee7a3-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="ee7a3-165">USB 电缆连接提供更好的渲染质量和稳定性。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="ee7a3-166">若要使用 USB 电缆连接，请从 HoloLens Wi-Fi HoloLens 中设置全息远程播放器应用。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="ee7a3-167">它将显示以 169 开头的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="ee7a3-168">在 Unity 的全息仿真设置中使用此 IP 地址进行连接。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="ee7a3-169">识别 USB 电缆的 IP 地址后，可以安全地将 USB 电缆HoloLensWi-Fi连接。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="ee7a3-170">启动远程处理会话</span><span class="sxs-lookup"><span data-stu-id="ee7a3-170">Starting a remoting session</span></span>

<span data-ttu-id="ee7a3-171">将 Unity 连接到 HoloLens，在编辑器中进入播放模式。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="ee7a3-172">会话完成后，退出播放模式。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="ee7a3-173">某些版本的 Unity 存在一个已知问题，即编辑器在远程处理会话期间进入播放模式时可能会挂起。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="ee7a3-174">加载项目时，如果全息窗口已打开，则可能会显示此问题。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="ee7a3-175">若要确保此问题不会发生，请始终在退出 Unity 之前关闭全息对话。</span><span class="sxs-lookup"><span data-stu-id="ee7a3-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee7a3-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee7a3-176">See also</span></span>

- [<span data-ttu-id="ee7a3-177">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="ee7a3-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="ee7a3-178">Microsoft 全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="ee7a3-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
