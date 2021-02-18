---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496086"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="2a32c-104">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="2a32c-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="2a32c-105">无论你是使用 DirectX 还是 Unity 来开发混合现实应用，Visual Studio 都是你用于进行调试和部署的首选工具。</span><span class="sxs-lookup"><span data-stu-id="2a32c-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="2a32c-106">本部分介绍以下操作：</span><span class="sxs-lookup"><span data-stu-id="2a32c-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="2a32c-107">通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="2a32c-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="2a32c-108">使用 Visual Studio 中内置的 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="2a32c-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="2a32c-109">调试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a32c-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="2a32c-110">Prerequisites</span></span>

1. <span data-ttu-id="2a32c-111">有关安装说明，请参阅[安装工具](../../develop/install-the-tools.md#installation-checklist)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="2a32c-112">在 Visual Studio 中创建新的通用 Windows 应用项目。</span><span class="sxs-lookup"><span data-stu-id="2a32c-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="2a32c-113">对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2a32c-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="2a32c-114">对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2a32c-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="2a32c-115">支持 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="2a32c-115">C# and C++ are supported.</span></span> <span data-ttu-id="2a32c-116">（或按说明[在 Unity 中创建应用](../../develop/unity/tutorials/holograms-100.md)。）</span><span class="sxs-lookup"><span data-stu-id="2a32c-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="2a32c-117">启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="2a32c-117">Enabling Developer Mode</span></span>

<span data-ttu-id="2a32c-118">首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 </span><span class="sxs-lookup"><span data-stu-id="2a32c-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="2a32c-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="2a32c-119">HoloLens</span></span>

1. <span data-ttu-id="2a32c-120">打开 HoloLens，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="2a32c-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="2a32c-121">使用[开始手势](../../design/system-gesture.md)以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="2a32c-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="2a32c-122">选择“设置”  磁贴，以在你的环境中启动应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="2a32c-123">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="2a32c-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="2a32c-124">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="2a32c-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="2a32c-125">启用“开发人员模式”，将应用从 Visual Studio 部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2a32c-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="2a32c-126">可选：向下滚动，并启用设备门户，以便从 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="2a32c-127">Windows 电脑</span><span class="sxs-lookup"><span data-stu-id="2a32c-127">Windows PC</span></span>

<span data-ttu-id="2a32c-128">如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="2a32c-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="2a32c-129">转到“设置” </span><span class="sxs-lookup"><span data-stu-id="2a32c-129">Go to **Settings**</span></span>
2. <span data-ttu-id="2a32c-130">选择“更新和安全” </span><span class="sxs-lookup"><span data-stu-id="2a32c-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="2a32c-131">选择“面向开发人员” </span><span class="sxs-lookup"><span data-stu-id="2a32c-131">Select **For developers**</span></span>
4. <span data-ttu-id="2a32c-132">启用“开发人员模式”，阅读所选设置的免责声明，然后选择“是”以接受更改。</span><span class="sxs-lookup"><span data-stu-id="2a32c-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="2a32c-133">通过 Wi-Fi 部署 HoloLens 应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="2a32c-134">为 Visual Studio 项目配置以下属性：</span><span class="sxs-lookup"><span data-stu-id="2a32c-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="2a32c-135">选择应用编译选项</span><span class="sxs-lookup"><span data-stu-id="2a32c-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="2a32c-136">对于 Unity 项目，请选择“Master”或“Master” </span><span class="sxs-lookup"><span data-stu-id="2a32c-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="2a32c-137">对于所有其他项目，请选择“Release”</span><span class="sxs-lookup"><span data-stu-id="2a32c-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="2a32c-138">可以在[导出和生成 Visual Studio 解决方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中找到每个编译选项的完整定义。</span><span class="sxs-lookup"><span data-stu-id="2a32c-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="2a32c-139">根据设备选择生成配置</span><span class="sxs-lookup"><span data-stu-id="2a32c-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2a32c-140">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="2a32c-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)

<span data-ttu-id="2a32c-142">接下来，需要设置远程连接。</span><span class="sxs-lookup"><span data-stu-id="2a32c-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="2a32c-143">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="2a32c-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="2a32c-144">如果正在处理 C# 项目，将自动显示一个对话框。</span><span class="sxs-lookup"><span data-stu-id="2a32c-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="2a32c-145">如果 C# 项目中未显示远程连接对话框，你可以从“属性”>“调试”手动打开它。</span><span class="sxs-lookup"><span data-stu-id="2a32c-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="2a32c-146">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="2a32c-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="2a32c-147">可在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="2a32c-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="2a32c-148">我们始终建议手动输入你的 IP 地址，而不要依赖于“自动检测到”功能</span><span class="sxs-lookup"><span data-stu-id="2a32c-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="2a32c-149">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="2a32c-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Visual Studio 中的远程连接对话框](images/remotedeploy.png)

3. <span data-ttu-id="2a32c-151">根据需要生成、部署和调试应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2a32c-152">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="2a32c-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2a32c-153">选择“生成”>“部署”以生成并部署而不调试</span><span class="sxs-lookup"><span data-stu-id="2a32c-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)

4. <span data-ttu-id="2a32c-155">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="2a32c-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2a32c-156">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="2a32c-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="2a32c-157">通过 USB部署 HoloLens 应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="2a32c-158">选择应用编译选项</span><span class="sxs-lookup"><span data-stu-id="2a32c-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="2a32c-159">对于 Unity 项目，请选择“Master”或“Master” </span><span class="sxs-lookup"><span data-stu-id="2a32c-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="2a32c-160">对于所有其他项目，请选择“Release”</span><span class="sxs-lookup"><span data-stu-id="2a32c-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="2a32c-161">可以在[导出和生成 Visual Studio 解决方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中找到每个编译选项的完整定义。</span><span class="sxs-lookup"><span data-stu-id="2a32c-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="2a32c-162">根据设备选择生成配置</span><span class="sxs-lookup"><span data-stu-id="2a32c-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2a32c-163">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="2a32c-163">Select **Device** in the deployment target drop-down menu</span></span>

![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="2a32c-165">根据需要生成、部署和调试应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2a32c-166">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="2a32c-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2a32c-167">选择“生成”>“部署”以生成并部署而不调试</span><span class="sxs-lookup"><span data-stu-id="2a32c-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="2a32c-169">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="2a32c-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2a32c-170">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="2a32c-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="2a32c-171">如果通过 USB 进行应用部署时出现相当长的延迟时间，建议使用上一节中的[远程计算机说明](#deploying-a-hololens-app-over-wi-fi)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="2a32c-172">将应用部署到 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="2a32c-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="2a32c-173">请确保已[安装 HoloLens 2 或 HoloLens（第一代）仿真器](../install-the-tools.md#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="2a32c-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="2a32c-174">根据设备选择生成配置和仿真器</span><span class="sxs-lookup"><span data-stu-id="2a32c-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2a32c-175">根据需要生成、部署和调试应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2a32c-176">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="2a32c-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2a32c-177">选择“生成”>“部署”以生成并部署而不调试</span><span class="sxs-lookup"><span data-stu-id="2a32c-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="2a32c-179">将 VR 应用部署到本地 PC</span><span class="sxs-lookup"><span data-stu-id="2a32c-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="2a32c-180">使用连接到电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式头戴显示设备：</span><span class="sxs-lookup"><span data-stu-id="2a32c-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="2a32c-181">为应用选择一种 **x86** 或 **x64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="2a32c-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="2a32c-182">在部署目标下拉菜单中选择“本地计算机” </span><span class="sxs-lookup"><span data-stu-id="2a32c-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="2a32c-183">根据需要生成、部署和调试应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2a32c-184">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="2a32c-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2a32c-185">选择“生成”>“部署”以生成并部署而不调试</span><span class="sxs-lookup"><span data-stu-id="2a32c-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="2a32c-186">配对设备</span><span class="sxs-lookup"><span data-stu-id="2a32c-186">Pairing your device</span></span>

<span data-ttu-id="2a32c-187">首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="2a32c-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2a32c-188">在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。 </span><span class="sxs-lookup"><span data-stu-id="2a32c-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="2a32c-189">当 PIN 显示在 HoloLens 上时，请将其键入 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2a32c-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="2a32c-190">配对完成后，在 HoloLens 上点击“完成”关闭对话框。 </span><span class="sxs-lookup"><span data-stu-id="2a32c-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="2a32c-191">此电脑现已与 HoloLens 配对，你可以自动部署应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="2a32c-192">请针对用于将应用部署到 HoloLens 的每台电脑重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="2a32c-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="2a32c-193">将 HoloLens 与所有配对的计算机取消配对：</span><span class="sxs-lookup"><span data-stu-id="2a32c-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="2a32c-194">启动“设置”应用，转到“更新”>“面向开发人员”，并点击“清除”  。</span><span class="sxs-lookup"><span data-stu-id="2a32c-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="2a32c-195">适用于 HoloLens（第一代）的图形调试器</span><span class="sxs-lookup"><span data-stu-id="2a32c-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="2a32c-196">在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="2a32c-197">有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="2a32c-198">**启动图形调试器**</span><span class="sxs-lookup"><span data-stu-id="2a32c-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="2a32c-199">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="2a32c-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="2a32c-200">转到“调试”>“图形”>“启动诊断” </span><span class="sxs-lookup"><span data-stu-id="2a32c-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="2a32c-201">首次在 HoloLens 上开始诊断时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="2a32c-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="2a32c-202">请重启 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="2a32c-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="2a32c-203">分析</span><span class="sxs-lookup"><span data-stu-id="2a32c-203">Profiling</span></span>

<span data-ttu-id="2a32c-204">使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="2a32c-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="2a32c-205">这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。</span><span class="sxs-lookup"><span data-stu-id="2a32c-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="2a32c-206">有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="2a32c-207">**在 HoloLens 上启动分析工具**</span><span class="sxs-lookup"><span data-stu-id="2a32c-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="2a32c-208">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="2a32c-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="2a32c-209">转到“调试”>“启动诊断工具但不调试...” </span><span class="sxs-lookup"><span data-stu-id="2a32c-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="2a32c-210">选择要使用的工具</span><span class="sxs-lookup"><span data-stu-id="2a32c-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="2a32c-211">选择“启动”</span><span class="sxs-lookup"><span data-stu-id="2a32c-211">Select **Start**</span></span>
5. <span data-ttu-id="2a32c-212">首次在 HoloLens 上启动诊断但不调试时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="2a32c-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="2a32c-213">请重启 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="2a32c-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="2a32c-214">调试已安装的或正在运行的应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-214">Debugging an installed or running app</span></span>

<span data-ttu-id="2a32c-215">可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="2a32c-216">要调试已安装的应用包，或者要调试已经在运行的应用，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="2a32c-217">转到“调试”->“其他调试目标”->“调试已安装的应用包” </span><span class="sxs-lookup"><span data-stu-id="2a32c-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="2a32c-218">为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  </span><span class="sxs-lookup"><span data-stu-id="2a32c-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="2a32c-219">输入设备的 **IP 地址**</span><span class="sxs-lookup"><span data-stu-id="2a32c-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="2a32c-220">选择“通用”身份验证模式 </span><span class="sxs-lookup"><span data-stu-id="2a32c-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="2a32c-221">窗口中会显示正在运行的和非活动的应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="2a32c-222">选择要调试的应用。</span><span class="sxs-lookup"><span data-stu-id="2a32c-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="2a32c-223">选择要调试的代码类型（“托管”、“本机”、“混合”）</span><span class="sxs-lookup"><span data-stu-id="2a32c-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="2a32c-224">选择“附加”或“开始” </span><span class="sxs-lookup"><span data-stu-id="2a32c-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2a32c-225">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="2a32c-225">Next Development Checkpoint</span></span>

<span data-ttu-id="2a32c-226">如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。</span><span class="sxs-lookup"><span data-stu-id="2a32c-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="2a32c-227">从这里，你可以继续了解下一个主题：</span><span class="sxs-lookup"><span data-stu-id="2a32c-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a32c-228">部署到 HoloLens 模拟器</span><span class="sxs-lookup"><span data-stu-id="2a32c-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="2a32c-229">或直接跳到添加高级服务：</span><span class="sxs-lookup"><span data-stu-id="2a32c-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a32c-230">高级服务</span><span class="sxs-lookup"><span data-stu-id="2a32c-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="2a32c-231">你可以随时返回到 [Unity 开发检查点](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="2a32c-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a32c-232">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a32c-232">See also</span></span>
* [<span data-ttu-id="2a32c-233">安装工具</span><span class="sxs-lookup"><span data-stu-id="2a32c-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="2a32c-234">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="2a32c-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="2a32c-235">部署和调试通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="2a32c-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="2a32c-236">启用设备进行开发</span><span class="sxs-lookup"><span data-stu-id="2a32c-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)