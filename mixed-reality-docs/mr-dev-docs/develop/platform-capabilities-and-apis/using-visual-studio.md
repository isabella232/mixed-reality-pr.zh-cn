---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: c4ffe3a426ad82c324efef20639cf836f16a7f63
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583612"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="01ff8-104">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="01ff8-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="01ff8-105">无论你是使用 DirectX 还是 Unity 来开发混合现实应用，Visual Studio 都是你用于进行调试和部署的首选工具。</span><span class="sxs-lookup"><span data-stu-id="01ff8-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="01ff8-106">本部分介绍以下操作：</span><span class="sxs-lookup"><span data-stu-id="01ff8-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="01ff8-107">通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="01ff8-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="01ff8-108">使用 Visual Studio 中内置的 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="01ff8-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="01ff8-109">调试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01ff8-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="01ff8-110">Prerequisites</span></span>
1. <span data-ttu-id="01ff8-111">有关安装说明，请参阅[安装工具](../../develop/install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-111">See [Install the Tools](../../develop/install-the-tools.md) for installation instructions.</span></span>
2. <span data-ttu-id="01ff8-112">在 Visual Studio 中创建新的通用 Windows 应用项目。</span><span class="sxs-lookup"><span data-stu-id="01ff8-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="01ff8-113">对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="01ff8-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="01ff8-114">对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="01ff8-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="01ff8-115">支持 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="01ff8-115">C# and C++ are supported.</span></span> <span data-ttu-id="01ff8-116">（或按说明[在 Unity 中创建应用](../../develop/unity/tutorials/holograms-100.md)。）</span><span class="sxs-lookup"><span data-stu-id="01ff8-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="01ff8-117">启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="01ff8-117">Enabling Developer Mode</span></span>

<span data-ttu-id="01ff8-118">首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 </span><span class="sxs-lookup"><span data-stu-id="01ff8-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="01ff8-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="01ff8-119">HoloLens</span></span>
1. <span data-ttu-id="01ff8-120">打开 HoloLens，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="01ff8-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="01ff8-121">使用[开始手势](../../design/system-gesture.md)以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="01ff8-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="01ff8-122">选择“设置”  磁贴，以在你的环境中启动应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="01ff8-123">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="01ff8-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="01ff8-124">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="01ff8-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="01ff8-125">启用“开发人员模式”，[将应用从 Visual Studio 部署到](using-visual-studio.md) HoloLens。</span><span class="sxs-lookup"><span data-stu-id="01ff8-125">Enable **Developer Mode** to [deploy apps from Visual Studio](using-visual-studio.md) to your HoloLens.</span></span>
7. <span data-ttu-id="01ff8-126">可选：向下滚动，并启用设备门户，以便从 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="01ff8-127">Windows 电脑</span><span class="sxs-lookup"><span data-stu-id="01ff8-127">Windows PC</span></span>

<span data-ttu-id="01ff8-128">如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="01ff8-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="01ff8-129">转到“设置” </span><span class="sxs-lookup"><span data-stu-id="01ff8-129">Go to **Settings**</span></span>
2. <span data-ttu-id="01ff8-130">选择“更新和安全” </span><span class="sxs-lookup"><span data-stu-id="01ff8-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="01ff8-131">选择“面向开发人员” </span><span class="sxs-lookup"><span data-stu-id="01ff8-131">Select **For developers**</span></span>
4. <span data-ttu-id="01ff8-132">启用“开发人员模式”，阅读所选设置的免责声明，然后选择“是”以接受更改。</span><span class="sxs-lookup"><span data-stu-id="01ff8-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a><span data-ttu-id="01ff8-133">通过 Wi-Fi 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="01ff8-133">Deploying an app over Wi-Fi - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="01ff8-134">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="01ff8-134">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="01ff8-135">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-135">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="01ff8-136">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="01ff8-136">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-137">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-137">![Remote machine deployment target in Visual Studio](images/remotemachinesetting.png)</span></span></br>
3. <span data-ttu-id="01ff8-138">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="01ff8-138">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="01ff8-139">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="01ff8-139">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="01ff8-140">a.</span><span class="sxs-lookup"><span data-stu-id="01ff8-140">a.</span></span> <span data-ttu-id="01ff8-141">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="01ff8-141">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="01ff8-142">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="01ff8-142">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="01ff8-143">b.</span><span class="sxs-lookup"><span data-stu-id="01ff8-143">b.</span></span> <span data-ttu-id="01ff8-144">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="01ff8-144">Set Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="01ff8-145">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-145">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="01ff8-146">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-146">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-147">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-147">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="01ff8-148">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="01ff8-148">The first time you deploy an app to your HoloLens from your PC, you'lll be prompted for a PIN.</span></span> <span data-ttu-id="01ff8-149">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="01ff8-149">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a><span data-ttu-id="01ff8-150">通过 Wi-Fi 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="01ff8-150">Deploying an app over Wi-Fi - HoloLens 2</span></span>
1. <span data-ttu-id="01ff8-151">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="01ff8-151">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="01ff8-152">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-152">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="01ff8-153">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="01ff8-153">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-154">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-154">![Remote machine deployment target in Visual Studio](images/remotemachinesetting_arm64.png)</span></span></br>
3. <span data-ttu-id="01ff8-155">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="01ff8-155">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="01ff8-156">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="01ff8-156">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="01ff8-157">a.</span><span class="sxs-lookup"><span data-stu-id="01ff8-157">a.</span></span> <span data-ttu-id="01ff8-158">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="01ff8-158">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="01ff8-159">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="01ff8-159">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="01ff8-160">b.</span><span class="sxs-lookup"><span data-stu-id="01ff8-160">b.</span></span> <span data-ttu-id="01ff8-161">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="01ff8-161">Set the Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="01ff8-162">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-162">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="01ff8-163">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-163">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-164">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-164">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="01ff8-165">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="01ff8-165">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="01ff8-166">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="01ff8-166">Follow the **Pairing your device** instructions below.</span></span>

<span data-ttu-id="01ff8-167">如果 HoloLens IP 地址已更改，你可以转到“项目”>“属性”>“配置属性”>“调试”来更改目标计算机的 IP 地址 </span><span class="sxs-lookup"><span data-stu-id="01ff8-167">If your HoloLens IP address changes, you can change the IP address of the target machine by going to **Project > Properties > Configuration Properties > Debugging**</span></span>

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a><span data-ttu-id="01ff8-168">通过 USB 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="01ff8-168">Deploying an app over USB - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="01ff8-169">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="01ff8-169">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="01ff8-170">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-170">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="01ff8-171">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="01ff8-171">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-172">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-172">![Device deployment in Visual Studio](images/buildsettingsusbdeploy.png)</span></span></br>
3. <span data-ttu-id="01ff8-173">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-173">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-174">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-174">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="01ff8-175">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="01ff8-175">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="01ff8-176">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="01ff8-176">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-usb---hololens-2"></a><span data-ttu-id="01ff8-177">通过 USB 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="01ff8-177">Deploying an app over USB - HoloLens 2</span></span>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="01ff8-178">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="01ff8-178">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="01ff8-179">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-179">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="01ff8-180">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="01ff8-180">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-181">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-181">![Device deployment in Visual Studio](images/buildsettingsusbdeploy_arm64.png)</span></span></br>
3. <span data-ttu-id="01ff8-182">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-182">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-183">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-183">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="01ff8-184">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="01ff8-184">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="01ff8-185">按下面的说明 **配对设备**。</span><span class="sxs-lookup"><span data-stu-id="01ff8-185">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a><span data-ttu-id="01ff8-186">将应用部署到本地电脑 - 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="01ff8-186">Deploying an app to your Local PC - immersive headset</span></span>

<span data-ttu-id="01ff8-187">使用连接到电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式头戴显示设备：</span><span class="sxs-lookup"><span data-stu-id="01ff8-187">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="01ff8-188">为应用选择一种 **x86** 或 **x64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="01ff8-188">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="01ff8-189">在部署目标下拉菜单中选择“本地计算机” </span><span class="sxs-lookup"><span data-stu-id="01ff8-189">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="01ff8-190">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-190">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="01ff8-191">配对设备</span><span class="sxs-lookup"><span data-stu-id="01ff8-191">Pairing your device</span></span>

<span data-ttu-id="01ff8-192">首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="01ff8-192">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="01ff8-193">在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。 </span><span class="sxs-lookup"><span data-stu-id="01ff8-193">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="01ff8-194">当 PIN 显示在 HoloLens 上时，请将其键入 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="01ff8-194">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="01ff8-195">配对完成后，在 HoloLens 上点击“完成”关闭对话框。 </span><span class="sxs-lookup"><span data-stu-id="01ff8-195">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="01ff8-196">此电脑现已与 HoloLens 配对，你可以自动部署应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-196">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="01ff8-197">请针对用于将应用部署到 HoloLens 的每台电脑重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="01ff8-197">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="01ff8-198">将 HoloLens 与所有配对的计算机取消配对：</span><span class="sxs-lookup"><span data-stu-id="01ff8-198">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="01ff8-199">启动“设置”应用，转到“更新”>“面向开发人员”，并点击“清除”  。</span><span class="sxs-lookup"><span data-stu-id="01ff8-199">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a><span data-ttu-id="01ff8-200">将应用部署到 HoloLens（第一代）仿真器</span><span class="sxs-lookup"><span data-stu-id="01ff8-200">Deploying an app to the HoloLens (1st gen) Emulator</span></span>
1. <span data-ttu-id="01ff8-201">请确保已[安装 HoloLens 仿真器](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-201">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="01ff8-202">为应用选择一种 **x86** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="01ff8-202">Select an **x86** build configuration for your app.</span></span></br>
<span data-ttu-id="01ff8-203">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-203">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="01ff8-204">在部署目标下拉菜单中选择“HoloLens 仿真器” </span><span class="sxs-lookup"><span data-stu-id="01ff8-204">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-205">![Visual Studio 中的仿真器目标](images/deployemulator.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-205">![Emulator target in Visual Studio](images/deployemulator.png)</span></span></br>
4. <span data-ttu-id="01ff8-206">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-206">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-207">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-207">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a><span data-ttu-id="01ff8-208">将应用部署到 HoloLens 2 仿真器</span><span class="sxs-lookup"><span data-stu-id="01ff8-208">Deploying an app to the HoloLens 2 Emulator</span></span>
1. <span data-ttu-id="01ff8-209">请确保已[安装 HoloLens 仿真器](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-209">Make sure you've **[installed the HoloLens Emulator](../install-the-tools.md)**.</span></span>
2. <span data-ttu-id="01ff8-210">为应用选择一种 **x86** 或 **x64** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="01ff8-210">Select an **x86** or **x64** build configuration for your app.</span></span></br>
<span data-ttu-id="01ff8-211">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-211">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="01ff8-212">在部署目标下拉菜单中选择“HoloLens 2 仿真器” </span><span class="sxs-lookup"><span data-stu-id="01ff8-212">Select **HoloLens 2 Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="01ff8-213">![Visual Studio 中的仿真器目标](images/deployemulator2.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-213">![Emulator target in Visual Studio](images/deployemulator2.png)</span></span></br>
4. <span data-ttu-id="01ff8-214">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="01ff8-214">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="01ff8-215">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="01ff8-215">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="01ff8-216">适用于 HoloLens（第一代）的图形调试器</span><span class="sxs-lookup"><span data-stu-id="01ff8-216">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="01ff8-217">在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-217">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="01ff8-218">有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-218">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="01ff8-219">**启动图形调试器**</span><span class="sxs-lookup"><span data-stu-id="01ff8-219">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="01ff8-220">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="01ff8-220">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="01ff8-221">转到“调试”>“图形”>“启动诊断” </span><span class="sxs-lookup"><span data-stu-id="01ff8-221">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="01ff8-222">首次在 HoloLens 上开始诊断时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="01ff8-222">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="01ff8-223">请重启 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="01ff8-223">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="01ff8-224">分析</span><span class="sxs-lookup"><span data-stu-id="01ff8-224">Profiling</span></span>

<span data-ttu-id="01ff8-225">使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="01ff8-225">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="01ff8-226">这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。</span><span class="sxs-lookup"><span data-stu-id="01ff8-226">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="01ff8-227">有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-227">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="01ff8-228">**在 HoloLens 上启动分析工具**</span><span class="sxs-lookup"><span data-stu-id="01ff8-228">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="01ff8-229">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="01ff8-229">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="01ff8-230">转到“调试”>“启动诊断工具但不调试...” </span><span class="sxs-lookup"><span data-stu-id="01ff8-230">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="01ff8-231">选择要使用的工具</span><span class="sxs-lookup"><span data-stu-id="01ff8-231">Select the tools you want to use</span></span>
4. <span data-ttu-id="01ff8-232">选择“启动”</span><span class="sxs-lookup"><span data-stu-id="01ff8-232">Select **Start**</span></span>
5. <span data-ttu-id="01ff8-233">首次在 HoloLens 上启动诊断但不调试时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="01ff8-233">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="01ff8-234">请重启 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="01ff8-234">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="01ff8-235">调试已安装的或正在运行的应用</span><span class="sxs-lookup"><span data-stu-id="01ff8-235">Debugging an installed or running app</span></span>

<span data-ttu-id="01ff8-236">可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-236">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="01ff8-237">要调试已安装的应用包，或者要调试已经在运行的应用，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-237">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="01ff8-238">转到“调试”->“其他调试目标”->“调试已安装的应用包” </span><span class="sxs-lookup"><span data-stu-id="01ff8-238">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="01ff8-239">为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  </span><span class="sxs-lookup"><span data-stu-id="01ff8-239">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="01ff8-240">输入设备的 **IP 地址**</span><span class="sxs-lookup"><span data-stu-id="01ff8-240">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="01ff8-241">选择“通用”身份验证模式 </span><span class="sxs-lookup"><span data-stu-id="01ff8-241">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="01ff8-242">窗口中会显示正在运行的和非活动的应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-242">The window shows both running and inactive apps.</span></span> <span data-ttu-id="01ff8-243">选择要调试的应用。</span><span class="sxs-lookup"><span data-stu-id="01ff8-243">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="01ff8-244">选择要调试的代码类型（“托管”、“本机”、“混合”）</span><span class="sxs-lookup"><span data-stu-id="01ff8-244">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="01ff8-245">选择“附加”或“开始” </span><span class="sxs-lookup"><span data-stu-id="01ff8-245">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="01ff8-246">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="01ff8-246">Next Development Checkpoint</span></span>

<span data-ttu-id="01ff8-247">如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。</span><span class="sxs-lookup"><span data-stu-id="01ff8-247">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="01ff8-248">从这里，你可以继续了解下一个主题：</span><span class="sxs-lookup"><span data-stu-id="01ff8-248">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01ff8-249">部署到 HoloLens 模拟器</span><span class="sxs-lookup"><span data-stu-id="01ff8-249">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="01ff8-250">或直接跳到添加高级服务：</span><span class="sxs-lookup"><span data-stu-id="01ff8-250">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01ff8-251">高级服务</span><span class="sxs-lookup"><span data-stu-id="01ff8-251">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="01ff8-252">你可以随时返回到 [Unity 开发检查点](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="01ff8-252">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="01ff8-253">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01ff8-253">See also</span></span>
* [<span data-ttu-id="01ff8-254">安装工具</span><span class="sxs-lookup"><span data-stu-id="01ff8-254">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="01ff8-255">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="01ff8-255">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="01ff8-256">部署和调试通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="01ff8-256">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="01ff8-257">启用设备进行开发</span><span class="sxs-lookup"><span data-stu-id="01ff8-257">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)