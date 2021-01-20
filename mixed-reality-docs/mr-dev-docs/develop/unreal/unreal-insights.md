---
title: 使用 Unreal Insights 进行分析
description: 了解如何在 HoloLens 2 上使用 Unreal Insights。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，开发，分析，Unreal insights，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580837"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="6055f-104">使用 Unreal Insights 进行分析</span><span class="sxs-lookup"><span data-stu-id="6055f-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="6055f-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) 是一种分析系统，用于从 Unreal 引擎收集、分析和可视化数据。</span><span class="sxs-lookup"><span data-stu-id="6055f-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="6055f-106">分析系统可以帮助你找到优化瓶颈，以及你的应用程序性能可以使用提升的区域。</span><span class="sxs-lookup"><span data-stu-id="6055f-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="6055f-107">通常，你可以直接从编辑器中启用 Unreal Insights，但对于 HoloLens 2，你需要使用命令行。</span><span class="sxs-lookup"><span data-stu-id="6055f-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="6055f-108">设置</span><span class="sxs-lookup"><span data-stu-id="6055f-108">Setup</span></span>

<span data-ttu-id="6055f-109">Unreal 允许你使用启用 Unreal Insights 的命令行参数在 HoloLens 启动器中创建和配置 "自定义配置文件"。</span><span class="sxs-lookup"><span data-stu-id="6055f-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="6055f-110">在命令提示符下使用 **ipconfig** 命令查找计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="6055f-111">IP 地址是由 ipconfig 列出的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="6055f-112">请记住，稍后在设置命令行参数时，请记住这一点。</span><span class="sxs-lookup"><span data-stu-id="6055f-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6055f-113">如果你使用的是 VPN，你可能需要提供通过 VPN 提供的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Ipconfig 命令的命令行结果的屏幕截图](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="6055f-115">在 Unreal 引擎面板的顶部，打开 "**启动**" 按钮下的 **设备管理器**：</span><span class="sxs-lookup"><span data-stu-id="6055f-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![突出显示了 "设备管理器" 的启动选项的屏幕截图](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="6055f-117">在设备管理器中，选择 " **添加未列出的设备**"：</span><span class="sxs-lookup"><span data-stu-id="6055f-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![在 Unreal 引擎中打开设备管理器的屏幕截图](images/unreal-insights-img-03.png)

4. <span data-ttu-id="6055f-119">单击 " **选择平台** "，然后选择 " **HoloLens**：</span><span class="sxs-lookup"><span data-stu-id="6055f-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![突出显示了 HoloLens 的 "添加未列出的设备" 下拉列表](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="6055f-121">如果使用的是 IPoverUSB，请输入127.0.0.1：10080作为设备标识符。</span><span class="sxs-lookup"><span data-stu-id="6055f-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="6055f-122">在相应的字段中输入 HoloLens 用户和密码，并根据需要填写 **显示名称** 。</span><span class="sxs-lookup"><span data-stu-id="6055f-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6055f-123">设备标识符是 HoloLens 的 IP 地址，而不是在步骤1中找到的运行 Unreal Insights 的计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![设备管理器中的 HoloLens 设备详细信息的屏幕截图](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="6055f-125">选择 " **添加** "，HoloLens 应显示在设备管理器的设备列表中：</span><span class="sxs-lookup"><span data-stu-id="6055f-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![HoloLens 已添加到设备列表的屏幕截图](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="6055f-127">启动</span><span class="sxs-lookup"><span data-stu-id="6055f-127">Launch</span></span>

1. <span data-ttu-id="6055f-128">从 "**启动**" 按钮下的 "UE4" 面板打开 **项目启动器**：</span><span class="sxs-lookup"><span data-stu-id="6055f-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![突出显示项目启动器的启动选项的屏幕截图](images/unreal-insights-img-07.png)

2. <span data-ttu-id="6055f-130">选择 " **+** **自定义启动配置文件**" 下的按钮以创建自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="6055f-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="6055f-131">创建后，你始终可以在以后编辑此配置文件：</span><span class="sxs-lookup"><span data-stu-id="6055f-131">Once created, you can always edit this profile later:</span></span>

![突出显示自定义启动配置文件的项目启动器的屏幕截图](images/unreal-insights-img-08.png)

3. <span data-ttu-id="6055f-133">在 HoloLens 自定义启动配置文件上选择 " **编辑配置文件** " 按钮，并配置：</span><span class="sxs-lookup"><span data-stu-id="6055f-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="6055f-134">**通过书籍** 选择要复制到设备的 **库**</span><span class="sxs-lookup"><span data-stu-id="6055f-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="6055f-135">你可能想要检查 **是否要存档？** 在 " **存档** " 部分中，保留生成的 .appxbundle 而不是 "删除" 来节省磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="6055f-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="6055f-136">指定 .appxbundle 的位置，并根据需要切换到开发版本</span><span class="sxs-lookup"><span data-stu-id="6055f-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![配置文件中的 "库" 选项的屏幕截图，其 "库" 为 "已突出显示"](images/unreal-insights-img-09.png)

4. <span data-ttu-id="6055f-138">设置 **你希望如何部署生成？** 要 **复制到设备** 以激活 UI 的 **启动** 部分，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6055f-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![项目启动器的屏幕截图，其中突出显示了 "复制到设备" 的部署选项](images/unreal-insights-img-10.png)

5. <span data-ttu-id="6055f-140">设置 "**启动**" 部分中的 **其他命令行参数**。</span><span class="sxs-lookup"><span data-stu-id="6055f-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="6055f-141">参数将写入 ue4commandline.txt 文件中，打包到捆绑包，并在启动时使用。</span><span class="sxs-lookup"><span data-stu-id="6055f-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="6055f-142">对于初学者，请尝试以下操作： **-tracehost = IP_OF_YOUR_PC 跟踪 = 日志、书签、框架、CPU、GPU、LoadTime、文件、网络**</span><span class="sxs-lookup"><span data-stu-id="6055f-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="6055f-143">可以在 [Unreal Insights 参考文档](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用启动参数的完整列表。</span><span class="sxs-lookup"><span data-stu-id="6055f-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="6055f-144">"IP_OF_YOUR_PC" 是我们在步骤1中找到的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="6055f-145">这是运行 Unreal Insights 的计算机的 IP 地址，而不是 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6055f-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6055f-146">跟踪可能会非常快。</span><span class="sxs-lookup"><span data-stu-id="6055f-146">Traces can get large very quickly.</span></span> <span data-ttu-id="6055f-147">只启用那些需要使跟踪大小保持较低的通道。</span><span class="sxs-lookup"><span data-stu-id="6055f-147">Enable only those channels you need to keep trace size low.</span></span>

![启动配置选项的屏幕截图](images/unreal-insights-img-11.png)

6. <span data-ttu-id="6055f-149">在应用启动之前启动 Unreal Insights，否则 Unreal Insights 在应用之前将无法正确初始化：</span><span class="sxs-lookup"><span data-stu-id="6055f-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="6055f-150">Unreal Insights 可执行文件存储在二进制引擎文件夹中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="6055f-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![运行的 unreal insights 可执行文件的屏幕截图](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="6055f-152">选择 " **上一步** " 返回到 " **项目启动器** " 对话框的根</span><span class="sxs-lookup"><span data-stu-id="6055f-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="6055f-153">返回编辑器中，单击自定义启动配置文件中的 " **启动** "</span><span class="sxs-lookup"><span data-stu-id="6055f-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![自定义启动配置文件的屏幕截图](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="6055f-155">查看项目已打包、安装在设备上并启动</span><span class="sxs-lookup"><span data-stu-id="6055f-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="6055f-156">分析</span><span class="sxs-lookup"><span data-stu-id="6055f-156">Profiling</span></span>

<span data-ttu-id="6055f-157">返回到 Unreal Insights，选择要开始分析的设备的 **实时** 连接</span><span class="sxs-lookup"><span data-stu-id="6055f-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="6055f-158">自定义配置文件在项目之间共享。</span><span class="sxs-lookup"><span data-stu-id="6055f-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="6055f-159">从这里开始，你可以使用你创建的自定义配置文件，而不必每次都执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6055f-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="6055f-160">每次启动 Unreal 时，你只需在 " [设置" 部分](#setup)中通过步骤3到步骤6重新创建与设备的连接。</span><span class="sxs-lookup"><span data-stu-id="6055f-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="6055f-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6055f-161">See also</span></span>
* [<span data-ttu-id="6055f-162">Unreal Insights 文档</span><span class="sxs-lookup"><span data-stu-id="6055f-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

