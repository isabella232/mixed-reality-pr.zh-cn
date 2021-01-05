---
title: 安装适用于 HoloLens 2 的 PIX
description: 了解如何安装适用于 HoloLens 2 设备的 PIX。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens，HoloLens 2，PIX，捕获，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822921"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="5c747-104">安装适用于 HoloLens 2 的 PIX</span><span class="sxs-lookup"><span data-stu-id="5c747-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="5c747-105">[PIX](https://devblogs.microsoft.com/pix) 是适用于 Windows 上的 DirectX 12 应用程序的性能优化和调试工具。</span><span class="sxs-lookup"><span data-stu-id="5c747-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="5c747-106">设置</span><span class="sxs-lookup"><span data-stu-id="5c747-106">Setup</span></span>

1. <span data-ttu-id="5c747-107">从主机 PC 获取最新的 PIX [版本]( https://devblogs.microsoft.com/pix/download) ，并通过 USB 电缆将您的 HoloLens 2 连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="5c747-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="5c747-108">如果你的 HoloLens 2 在 [Windows 有问必答版本](https://insider.windows.com) 上，或具有用于中断 PIX 的配置，则  [刷新你的设备](https://docs.microsoft.com/hololens/hololens-recovery) 以清除所有数据。</span><span class="sxs-lookup"><span data-stu-id="5c747-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="5c747-109">启用 **开发人员模式** 和 **设备门户**：</span><span class="sxs-lookup"><span data-stu-id="5c747-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="5c747-110">从混合现实主页打开 **设置** ：</span><span class="sxs-lookup"><span data-stu-id="5c747-110">Open **Settings** from Mixed Reality Home:</span></span>

![突出显示 "设置" 按钮的 HoloLens 菜单的屏幕截图](images/pix-img-01.jpg)

* <span data-ttu-id="5c747-112">选择 " **更新" & 安全**：</span><span class="sxs-lookup"><span data-stu-id="5c747-112">Select **Update & Security**:</span></span>

![突出显示了 "更新和安全" 按钮的 "设置" 窗口的屏幕截图](images/pix-img-02.jpg)

* <span data-ttu-id="5c747-114">**为开发人员** 选择：</span><span class="sxs-lookup"><span data-stu-id="5c747-114">Select **For Developers**:</span></span>

!["安全和更新" 窗口的屏幕截图，其中突出显示了 "开发人员" 按钮](images/pix-img-03.jpg)

* <span data-ttu-id="5c747-116">启用 **使用开发人员功能** 并 **启用设备门户**</span><span class="sxs-lookup"><span data-stu-id="5c747-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

!["开发人员" 窗口的屏幕截图在 "启用设备门户" 按钮的 "设置" 中打开](images/pix-img-04.jpg)

!["开发人员" 窗口的屏幕截图在 "设置" 中打开 "使用开发功能" 切换突出显示](images/pix-img-05.jpg)

* <span data-ttu-id="5c747-119">如果设备仍处于连接状态、处于唤醒状态，并且用户已登录，则启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5c747-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c747-120">请确保设备不处于待机模式或睡眠状态。</span><span class="sxs-lookup"><span data-stu-id="5c747-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="5c747-121">如果在此步骤中遇到问题，请参阅 [Windows 设备门户说明](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="5c747-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="5c747-122">准备部署</span><span class="sxs-lookup"><span data-stu-id="5c747-122">Preparing for deployment</span></span>

1. <span data-ttu-id="5c747-123">在 Visual Studio 中，将 " **ARM64** " 设置为 "平台" 和 " **设备** " 作为设备：</span><span class="sxs-lookup"><span data-stu-id="5c747-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![突出显示了平台和设备设置的 visual studio 解决方案屏幕截图](images/pix-img-06.png)

2. <span data-ttu-id="5c747-125">当 Visual Studio 提示你输入来自设备的 **PIN** 时：</span><span class="sxs-lookup"><span data-stu-id="5c747-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Visual studio 弹出窗口的屏幕截图要求提供 PIN](images/pix-img-07.png)

* <span data-ttu-id="5c747-127">从 Shell 选择 **设置**</span><span class="sxs-lookup"><span data-stu-id="5c747-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="5c747-128">选择 **更新 & 安全性**</span><span class="sxs-lookup"><span data-stu-id="5c747-128">Select **Update & Security**</span></span>
* <span data-ttu-id="5c747-129">**为开发人员** 选择，并在 **设备发现** 下按对</span><span class="sxs-lookup"><span data-stu-id="5c747-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

!["开发人员" 窗口的屏幕截图在 "设置" 中打开，并突出显示设备发现](images/pix-img-08.jpg)

![突出显示注册代码的付费设备弹出窗口屏幕截图](images/pix-img-09.jpg)

* <span data-ttu-id="5c747-132">在 Visual Studio 中输入生成的 PIN 号</span><span class="sxs-lookup"><span data-stu-id="5c747-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="5c747-133">Visual Studio 会将应用部署到连接的 HoloLens 2，这可能需要几分钟的时间，具体取决于应用程序。</span><span class="sxs-lookup"><span data-stu-id="5c747-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="5c747-134">启动 PIX</span><span class="sxs-lookup"><span data-stu-id="5c747-134">Launching PIX</span></span>

<span data-ttu-id="5c747-135">首先，使用设备门户验证应用未在 HoloLens 2 上运行。</span><span class="sxs-lookup"><span data-stu-id="5c747-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="5c747-136">然后，启动 PIX，连接到你的设备，然后选择 **Home**：</span><span class="sxs-lookup"><span data-stu-id="5c747-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![PIX 应用程序主屏幕的屏幕截图](images/pix-img-10.png)

* <span data-ttu-id="5c747-138">从左侧菜单中选择 " **连接** "：</span><span class="sxs-lookup"><span data-stu-id="5c747-138">Select **Connect** from the left-side menu:</span></span>

![突出显示了 "连接" 按钮的 PIX 应用程序左侧菜单的屏幕截图](images/pix-img-11.png)

2. <span data-ttu-id="5c747-140">从 " **计算机** " 选项卡中，选择 " **添加**"，然后输入以下凭据：</span><span class="sxs-lookup"><span data-stu-id="5c747-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="5c747-141">别名：由用户决定</span><span class="sxs-lookup"><span data-stu-id="5c747-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="5c747-142">主机名或 IP 地址：127.0.0。1</span><span class="sxs-lookup"><span data-stu-id="5c747-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="5c747-143">在 "**计算机**" 选项卡的右下方选择 "**连接**"：</span><span class="sxs-lookup"><span data-stu-id="5c747-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![已突出显示 "别名"、"主机名"、"IP 地址" 和 "添加" 按钮的 PIX 应用连接窗口屏幕截图](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="5c747-145">第一次连接始终较慢，因为正在复制二进制文件。</span><span class="sxs-lookup"><span data-stu-id="5c747-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="5c747-146">当 PIX 连接到 HoloLens 2 时，请在 "启动 UWP" 选项卡的 " **选择目标进程** " 部分找到你的应用，然后选择 " **启动**"：</span><span class="sxs-lookup"><span data-stu-id="5c747-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![选择 "目标进程" 窗口并突出显示 "启动" 按钮时 PIX 应用程序的屏幕截图](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="5c747-148">捕获的 GPU</span><span class="sxs-lookup"><span data-stu-id="5c747-148">GPU captured</span></span>

1. <span data-ttu-id="5c747-149">在 **Gpu 捕获** 部分中单击 "**照片**"，启动 gpu 捕获：</span><span class="sxs-lookup"><span data-stu-id="5c747-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![显示了 "电脑连接" 面板的 PIX 应用程序屏幕截图，其中突出显示了 GPU 捕获](images/pix-img-14.png)

2. <span data-ttu-id="5c747-151">单击 **GPU 捕获** 面板中生成的屏幕快照，打开捕获以进行分析：</span><span class="sxs-lookup"><span data-stu-id="5c747-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![带有 gpu 捕获部分打开的 PIX 应用程序的屏幕截图，其中突出显示了 GPU 捕获面板](images/pix-img-15.png)

3. <span data-ttu-id="5c747-153">按 " **开始** " 以开始分析：</span><span class="sxs-lookup"><span data-stu-id="5c747-153">Press **Start** to begin the analysis:</span></span>

!["启动" 按钮突出显示的 PIX 应用程序的屏幕截图](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="5c747-155">如果在拍摄 GPU 捕获后收集计时数据，则需要重新启动耳机。</span><span class="sxs-lookup"><span data-stu-id="5c747-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="5c747-156">这是一次重新启动设备，并且是计时数据收集所必需的。</span><span class="sxs-lookup"><span data-stu-id="5c747-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="5c747-157">PIX 现在可以使用！</span><span class="sxs-lookup"><span data-stu-id="5c747-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="5c747-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c747-158">See also</span></span>
* [<span data-ttu-id="5c747-159">PIX 主页</span><span class="sxs-lookup"><span data-stu-id="5c747-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)