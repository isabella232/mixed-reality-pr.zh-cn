---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: b0280edb2116094f6443e262d12c62243c319250
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91695702"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="08122-104">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="08122-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="08122-105">无论是要使用 DirectX 还是 Unity 来开发混合现实应用，都需要使用 Visual Studio 进行调试和部署。</span><span class="sxs-lookup"><span data-stu-id="08122-105">Whether you want to use DirectX or Unity to develop your mixed reality app, you will use Visual Studio for debugging and deploying.</span></span> <span data-ttu-id="08122-106">本部分介绍以下操作：</span><span class="sxs-lookup"><span data-stu-id="08122-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="08122-107">通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="08122-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="08122-108">使用 Visual Studio 中内置的 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="08122-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="08122-109">调试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="08122-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08122-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="08122-110">Prerequisites</span></span>
1. <span data-ttu-id="08122-111">有关安装说明，请参阅[安装工具](../../develop/install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="08122-111">See [Install the Tools](../../develop/install-the-tools.md) for installation instructions.</span></span>
2. <span data-ttu-id="08122-112">在 Visual Studio 中创建新的通用 Windows 应用项目。</span><span class="sxs-lookup"><span data-stu-id="08122-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="08122-113">对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="08122-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="08122-114">对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="08122-114">For Hololens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="08122-115">支持 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="08122-115">C# and C++ are supported.</span></span> <span data-ttu-id="08122-116">（或按说明[在 Unity 中创建应用](../../develop/unity/tutorials/holograms-100.md)。）</span><span class="sxs-lookup"><span data-stu-id="08122-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="08122-117">启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="08122-117">Enabling Developer Mode</span></span>

<span data-ttu-id="08122-118">首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 </span><span class="sxs-lookup"><span data-stu-id="08122-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="08122-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="08122-119">HoloLens</span></span>
1. <span data-ttu-id="08122-120">打开 HoloLens，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="08122-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="08122-121">执行[开始手势](../../design/system-gesture.md)以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="08122-121">Perform the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="08122-122">选择“设置”  磁贴，以在你的环境中启动应用。</span><span class="sxs-lookup"><span data-stu-id="08122-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="08122-123">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="08122-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="08122-124">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="08122-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="08122-125">启用“开发人员模式”  。</span><span class="sxs-lookup"><span data-stu-id="08122-125">Enable **Developer Mode** .</span></span> <span data-ttu-id="08122-126">这样，就可以[将应用从 Visual Studio 部署到](using-visual-studio.md) HoloLens。</span><span class="sxs-lookup"><span data-stu-id="08122-126">This will allow you to [deploy apps from Visual Studio](using-visual-studio.md) to your HoloLens.</span></span>
7. <span data-ttu-id="08122-127">可选：向下滚动，同时启用“设备门户”。 </span><span class="sxs-lookup"><span data-stu-id="08122-127">Optional: Scroll down and also enable **Device Portal** .</span></span> <span data-ttu-id="08122-128">然后，也可以通过 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="08122-128">This will also allow you to connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="08122-129">Windows 电脑</span><span class="sxs-lookup"><span data-stu-id="08122-129">Windows PC</span></span>

<span data-ttu-id="08122-130">如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。 </span><span class="sxs-lookup"><span data-stu-id="08122-130">If you are working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="08122-131">转到“设置” </span><span class="sxs-lookup"><span data-stu-id="08122-131">Go to **Settings**</span></span>
2. <span data-ttu-id="08122-132">选择“更新和安全” </span><span class="sxs-lookup"><span data-stu-id="08122-132">Select **Update and Security**</span></span>
3. <span data-ttu-id="08122-133">选择“面向开发人员” </span><span class="sxs-lookup"><span data-stu-id="08122-133">Select **For developers**</span></span>
4. <span data-ttu-id="08122-134">启用“开发人员模式”，阅读所选设置的免责声明，然后单击“是”以接受更改。 </span><span class="sxs-lookup"><span data-stu-id="08122-134">Enable **Developer Mode** , read the disclaimer for the setting you chose, then click Yes to accept the change.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a><span data-ttu-id="08122-135">通过 Wi-Fi 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="08122-135">Deploying an app over Wi-Fi - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="08122-136">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="08122-136">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="08122-137">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-137">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="08122-138">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="08122-138">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-139">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-139">![Remote machine deployment target in Visual Studio](images/remotemachinesetting.png)</span></span></br>
3. <span data-ttu-id="08122-140">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="08122-140">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging** .</span></span> <span data-ttu-id="08122-141">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="08122-141">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="08122-142">a.</span><span class="sxs-lookup"><span data-stu-id="08122-142">a.</span></span> <span data-ttu-id="08122-143">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="08122-143">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="08122-144">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="08122-144">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options** , or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="08122-145">b.</span><span class="sxs-lookup"><span data-stu-id="08122-145">b.</span></span> <span data-ttu-id="08122-146">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="08122-146">Set Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="08122-147">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="08122-147">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="08122-148">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-148">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-149">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-149">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="08122-150">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-150">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="08122-151">按下面的说明 **配对设备** 。</span><span class="sxs-lookup"><span data-stu-id="08122-151">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a><span data-ttu-id="08122-152">通过 Wi-Fi 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="08122-152">Deploying an app over Wi-Fi - HoloLens 2</span></span>
1. <span data-ttu-id="08122-153">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="08122-153">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="08122-154">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-154">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="08122-155">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="08122-155">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-156">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="08122-156">![Remote machine deployment target in Visual Studio](images/remotemachinesetting_arm64.png)</span></span></br>
3. <span data-ttu-id="08122-157">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="08122-157">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging** .</span></span> <span data-ttu-id="08122-158">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="08122-158">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="08122-159">a.</span><span class="sxs-lookup"><span data-stu-id="08122-159">a.</span></span> <span data-ttu-id="08122-160">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="08122-160">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="08122-161">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="08122-161">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options** , or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="08122-162">b.</span><span class="sxs-lookup"><span data-stu-id="08122-162">b.</span></span> <span data-ttu-id="08122-163">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="08122-163">Set the Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="08122-164">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="08122-164">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="08122-165">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-165">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-166">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-166">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="08122-167">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-167">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="08122-168">按下面的说明 **配对设备** 。</span><span class="sxs-lookup"><span data-stu-id="08122-168">Follow the **Pairing your device** instructions below.</span></span>

<span data-ttu-id="08122-169">如果 HoloLens IP 地址已更改，你可以转到“项目”>“属性”>“配置属性”>“调试”来更改目标计算机的 IP 地址 </span><span class="sxs-lookup"><span data-stu-id="08122-169">If your HoloLens IP address changes, you can change the IP address of the target machine by going to **Project > Properties > Configuration Properties > Debugging**</span></span>

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a><span data-ttu-id="08122-170">通过 USB 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="08122-170">Deploying an app over USB - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="08122-171">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="08122-171">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="08122-172">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-172">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="08122-173">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="08122-173">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-174">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)</span><span class="sxs-lookup"><span data-stu-id="08122-174">![Device deployment in Visual Studio](images/buildsettingsusbdeploy.png)</span></span></br>
3. <span data-ttu-id="08122-175">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-175">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-176">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-176">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="08122-177">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-177">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="08122-178">按下面的说明 **配对设备** 。</span><span class="sxs-lookup"><span data-stu-id="08122-178">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-usb---hololens-2"></a><span data-ttu-id="08122-179">通过 USB 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="08122-179">Deploying an app over USB - HoloLens 2</span></span>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="08122-180">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="08122-180">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="08122-181">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-181">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="08122-182">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="08122-182">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-183">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="08122-183">![Device deployment in Visual Studio](images/buildsettingsusbdeploy_arm64.png)</span></span></br>
3. <span data-ttu-id="08122-184">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-185">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-185">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="08122-186">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-186">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="08122-187">按下面的说明 **配对设备** 。</span><span class="sxs-lookup"><span data-stu-id="08122-187">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a><span data-ttu-id="08122-188">将应用部署到本地电脑 - 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="08122-188">Deploying an app to your Local PC - immersive headset</span></span>

<span data-ttu-id="08122-189">使用与电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)连接的 Windows Mixed Reality 沉浸式头戴显示设备时，请按这些说明操作。</span><span class="sxs-lookup"><span data-stu-id="08122-189">Follow these instructions when using a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span> <span data-ttu-id="08122-190">在这种情况下，只需在本地电脑上部署并运行应用即可。</span><span class="sxs-lookup"><span data-stu-id="08122-190">In these cases, simply deploy and run your app on the local PC.</span></span>
1. <span data-ttu-id="08122-191">为应用选择一种 **x86** 或 **x64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="08122-191">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="08122-192">在部署目标下拉菜单中选择“本地计算机” </span><span class="sxs-lookup"><span data-stu-id="08122-192">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="08122-193">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-193">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="08122-194">配对设备</span><span class="sxs-lookup"><span data-stu-id="08122-194">Pairing your device</span></span>

<span data-ttu-id="08122-195">首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-195">The first time you deploy an app from Visual Studio to your HoloLens, you will be prompted for a PIN.</span></span> <span data-ttu-id="08122-196">在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。  </span><span class="sxs-lookup"><span data-stu-id="08122-196">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers** and tap on **Pair** .</span></span> <span data-ttu-id="08122-197">HoloLens 上会显示一个 PIN；请在 Visual Studio 中键入此 PIN。</span><span class="sxs-lookup"><span data-stu-id="08122-197">A PIN will be displayed on your HoloLens; type this PIN in Visual Studio.</span></span> <span data-ttu-id="08122-198">配对完成后，在 HoloLens 上点击“完成”关闭对话框。 </span><span class="sxs-lookup"><span data-stu-id="08122-198">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="08122-199">此电脑现已与 HoloLens 配对，接下来可以自动部署应用。</span><span class="sxs-lookup"><span data-stu-id="08122-199">This PC is now paired with the HoloLens and you will be able to deploy apps automatically.</span></span> <span data-ttu-id="08122-200">请针对用于将应用部署到 HoloLens 的每台后续电脑重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="08122-200">Repeat these steps for every subsequent PC that is used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="08122-201">若要取消 HoloLens 与所有已配对计算机的配对，请启动“设置”应用，转到“更新”>“面向开发人员”，然后点击“清除”。   </span><span class="sxs-lookup"><span data-stu-id="08122-201">To un-pair your HoloLens from all computers it was paired with, launch the **Settings** app, go to **Update > For Developers** and tap on **Clear** .</span></span>

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a><span data-ttu-id="08122-202">将应用部署到 HoloLens（第一代）仿真器</span><span class="sxs-lookup"><span data-stu-id="08122-202">Deploying an app to the HoloLens (1st gen) Emulator</span></span>
1. <span data-ttu-id="08122-203">请确保已 **[安装 HoloLens 仿真器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="08122-203">Make sure you have **[installed the HoloLens Emulator](../install-the-tools.md)** .</span></span>
2. <span data-ttu-id="08122-204">为应用选择一种 **x86** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="08122-204">Select an **x86** build configuration for your app.</span></span></br>
<span data-ttu-id="08122-205">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-205">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="08122-206">在部署目标下拉菜单中选择“HoloLens 仿真器” </span><span class="sxs-lookup"><span data-stu-id="08122-206">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-207">![Visual Studio 中的仿真器目标](images/deployemulator.png)</span><span class="sxs-lookup"><span data-stu-id="08122-207">![Emulator target in Visual Studio](images/deployemulator.png)</span></span></br>
4. <span data-ttu-id="08122-208">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-208">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-209">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-209">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a><span data-ttu-id="08122-210">将应用部署到 HoloLens 2 仿真器</span><span class="sxs-lookup"><span data-stu-id="08122-210">Deploying an app to the HoloLens 2 Emulator</span></span>
1. <span data-ttu-id="08122-211">请确保已 **[安装 HoloLens 仿真器](../install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="08122-211">Make sure you have **[installed the HoloLens Emulator](../install-the-tools.md)** .</span></span>
2. <span data-ttu-id="08122-212">为应用选择一种 **x86** 或 **x64** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="08122-212">Select an **x86** or **x64** build configuration for your app.</span></span></br>
<span data-ttu-id="08122-213">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="08122-213">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="08122-214">在部署目标下拉菜单中选择“HoloLens 2 仿真器” </span><span class="sxs-lookup"><span data-stu-id="08122-214">Select **HoloLens 2 Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="08122-215">![Visual Studio 中的仿真器目标](images/deployemulator2.png)</span><span class="sxs-lookup"><span data-stu-id="08122-215">![Emulator target in Visual Studio](images/deployemulator2.png)</span></span></br>
4. <span data-ttu-id="08122-216">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="08122-216">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="08122-217">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="08122-217">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="08122-218">适用于 HoloLens（第一代）的图形调试器</span><span class="sxs-lookup"><span data-stu-id="08122-218">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="08122-219">在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="08122-219">The Visual Studio Graphics Diagnostics tools are very helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="08122-220">有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](https://msdn.microsoft.com/library/hh315751.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08122-220">See [Visual Studio Graphics Diagnostics on MSDN](https://msdn.microsoft.com/library/hh315751.aspx) for full details.</span></span>

<span data-ttu-id="08122-221">**启动图形调试器**</span><span class="sxs-lookup"><span data-stu-id="08122-221">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="08122-222">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="08122-222">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="08122-223">转到“调试”>“图形”>“启动诊断” </span><span class="sxs-lookup"><span data-stu-id="08122-223">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="08122-224">首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="08122-224">The first time you do this with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="08122-225">请重新启动 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="08122-225">Reboot your HoloLens to allow updated permissions to take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="08122-226">分析</span><span class="sxs-lookup"><span data-stu-id="08122-226">Profiling</span></span>

<span data-ttu-id="08122-227">使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="08122-227">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="08122-228">这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。</span><span class="sxs-lookup"><span data-stu-id="08122-228">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="08122-229">有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](https://msdn.microsoft.com/library/dn957936.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08122-229">See [Run diagnostic tools without debugging on MSDN](https://msdn.microsoft.com/library/dn957936.aspx) for full details.</span></span>

<span data-ttu-id="08122-230">**在 HoloLens 上启动分析工具**</span><span class="sxs-lookup"><span data-stu-id="08122-230">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="08122-231">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="08122-231">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="08122-232">转到“调试”>“启动诊断工具但不调试...” </span><span class="sxs-lookup"><span data-stu-id="08122-232">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="08122-233">选择要使用的工具</span><span class="sxs-lookup"><span data-stu-id="08122-233">Select the tools you want to use</span></span>
4. <span data-ttu-id="08122-234">单击“启动” </span><span class="sxs-lookup"><span data-stu-id="08122-234">Click **Start**</span></span>
5. <span data-ttu-id="08122-235">首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="08122-235">The first time you do this with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="08122-236">请重新启动 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="08122-236">Reboot your HoloLens to allow updated permissions to take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="08122-237">调试已安装的或正在运行的应用</span><span class="sxs-lookup"><span data-stu-id="08122-237">Debugging an installed or running app</span></span>

<span data-ttu-id="08122-238">可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。</span><span class="sxs-lookup"><span data-stu-id="08122-238">You can use Visual Studio to debug a Universal Windows app that's installed without deploying from a Visual Studio project.</span></span> <span data-ttu-id="08122-239">若要调试已安装的应用包，或者要调试已运行的应用，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="08122-239">This is useful if you want to debug an installed app package, or if you want to debug an app that's already running.</span></span>
1. <span data-ttu-id="08122-240">转到“调试”->“其他调试目标”->“调试已安装的应用包” </span><span class="sxs-lookup"><span data-stu-id="08122-240">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="08122-241">为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  </span><span class="sxs-lookup"><span data-stu-id="08122-241">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="08122-242">输入设备的 **IP 地址**</span><span class="sxs-lookup"><span data-stu-id="08122-242">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="08122-243">选择“通用”身份验证模式 </span><span class="sxs-lookup"><span data-stu-id="08122-243">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="08122-244">窗口中会显示正在运行的和非活动的应用。</span><span class="sxs-lookup"><span data-stu-id="08122-244">The window shows both running and inactive apps.</span></span> <span data-ttu-id="08122-245">选择要调试的应用。</span><span class="sxs-lookup"><span data-stu-id="08122-245">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="08122-246">选择要调试的代码类型（“托管”、“本机”、“混合”）</span><span class="sxs-lookup"><span data-stu-id="08122-246">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="08122-247">单击“附加”或“开始”  </span><span class="sxs-lookup"><span data-stu-id="08122-247">Click **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="08122-248">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="08122-248">Next Development Checkpoint</span></span>

<span data-ttu-id="08122-249">如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。</span><span class="sxs-lookup"><span data-stu-id="08122-249">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="08122-250">从这里，你可以进入下一主题：</span><span class="sxs-lookup"><span data-stu-id="08122-250">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="08122-251">部署到 HoloLens 模拟器</span><span class="sxs-lookup"><span data-stu-id="08122-251">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="08122-252">或直接跳到添加高级服务：</span><span class="sxs-lookup"><span data-stu-id="08122-252">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="08122-253">高级服务</span><span class="sxs-lookup"><span data-stu-id="08122-253">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="08122-254">你可以随时返回到 [Unity 开发检查点](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。</span><span class="sxs-lookup"><span data-stu-id="08122-254">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="08122-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08122-255">See also</span></span>
* [<span data-ttu-id="08122-256">安装工具</span><span class="sxs-lookup"><span data-stu-id="08122-256">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="08122-257">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="08122-257">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="08122-258">部署和调试通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="08122-258">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [<span data-ttu-id="08122-259">启用设备进行开发</span><span class="sxs-lookup"><span data-stu-id="08122-259">Enable your device for development</span></span>](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
