---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流 (深度、环境跟踪和反射率) 。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens，HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677372"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="3d153-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="3d153-104">HoloLens Research Mode</span></span>

<span data-ttu-id="3d153-105">第一代 HoloLens 中引入了研究模式，可用于访问设备上的关键传感器，尤其适用于不适用于部署的研究应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d153-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="3d153-106">HoloLens 2 的研究模式保留了 HoloLens 1 的功能，并添加了对其他流的访问权限：</span><span class="sxs-lookup"><span data-stu-id="3d153-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="3d153-107">**可见的轻型环境跟踪相机** -系统用于 head 跟踪和地图构建的灰色缩放相机。</span><span class="sxs-lookup"><span data-stu-id="3d153-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="3d153-108">**深度相机** –在两种模式下运行：</span><span class="sxs-lookup"><span data-stu-id="3d153-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="3d153-109">AHAT，高频 (45 FPS) 用于手动跟踪的近深度感应。</span><span class="sxs-lookup"><span data-stu-id="3d153-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="3d153-110">不同于第一个版本的短整型模式，AHAT 提供了超出1米的相位覆盖的伪深度。</span><span class="sxs-lookup"><span data-stu-id="3d153-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="3d153-111">长整型引发、低频率 (1-5 FPS) [空间映射](../../design/spatial-mapping.md)使用的深度感应</span><span class="sxs-lookup"><span data-stu-id="3d153-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="3d153-112">**反射率的两个版本** ： HoloLens 用于计算深度。</span><span class="sxs-lookup"><span data-stu-id="3d153-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="3d153-113">这些图像通过红外，并不受环境可见光的影响。</span><span class="sxs-lookup"><span data-stu-id="3d153-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="3d153-114">如果使用的是 HoloLens 2，还可以访问下面的其他输入：</span><span class="sxs-lookup"><span data-stu-id="3d153-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="3d153-115">**加速感应** 程序–由系统用来确定沿 X、Y 和 Z 轴和重心的线性加速度。</span><span class="sxs-lookup"><span data-stu-id="3d153-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="3d153-116">**Gyro** –系统用来确定旋转。</span><span class="sxs-lookup"><span data-stu-id="3d153-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="3d153-117">**磁力仪** –系统用于估计绝对方向。</span><span class="sxs-lookup"><span data-stu-id="3d153-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d153-118">研究模式目前为公共预览版。</span><span class="sxs-lookup"><span data-stu-id="3d153-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="3d153-119">![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="3d153-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="3d153-120">*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*</span><span class="sxs-lookup"><span data-stu-id="3d153-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="3d153-121">使用情况</span><span class="sxs-lookup"><span data-stu-id="3d153-121">Usage</span></span>

<span data-ttu-id="3d153-122">研究模式旨在使学术和工业研究人员了解计算机视觉和机器人的字段中的新想法。</span><span class="sxs-lookup"><span data-stu-id="3d153-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="3d153-123">它不适合企业环境中部署的应用程序，也不能通过 Microsoft Store 或其他分发渠道提供。</span><span class="sxs-lookup"><span data-stu-id="3d153-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="3d153-124">此外，Microsoft 不保证在未来的硬件或操作系统更新中将支持研究模式或等效的功能。</span><span class="sxs-lookup"><span data-stu-id="3d153-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="3d153-125">但是，这不会阻止你使用它来开发和测试新的观点！</span><span class="sxs-lookup"><span data-stu-id="3d153-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="3d153-126">安全性和性能</span><span class="sxs-lookup"><span data-stu-id="3d153-126">Security and performance</span></span>

<span data-ttu-id="3d153-127">请注意，在正常情况下，启用研究模式比使用 HoloLens 2 时使用的电池电量更多。</span><span class="sxs-lookup"><span data-stu-id="3d153-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="3d153-128">即使使用调研模式功能的应用程序没有运行，也是如此。</span><span class="sxs-lookup"><span data-stu-id="3d153-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="3d153-129">启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。</span><span class="sxs-lookup"><span data-stu-id="3d153-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="3d153-130">您可以在 [HoloLens 安全常见问题](https://docs.microsoft.com/hololens/hololens-faq-security)中找到有关设备安全的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3d153-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="3d153-131">设备支持</span><span class="sxs-lookup"><span data-stu-id="3d153-131">Device support</span></span>
<table><span data-ttu-id="3d153-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="3d153-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="3d153-133"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="3d153-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3d153-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 代</strong></a></span><span class="sxs-lookup"><span data-stu-id="3d153-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="3d153-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="3d153-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3d153-136">标题跟踪相机</span><span class="sxs-lookup"><span data-stu-id="3d153-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="3d153-137">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-137">✔️</span></span></td>
        <td><span data-ttu-id="3d153-138">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d153-139">IR 相机 & 深度</span><span class="sxs-lookup"><span data-stu-id="3d153-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="3d153-140">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-140">✔️</span></span></td>
        <td><span data-ttu-id="3d153-141">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d153-142">加速计</span><span class="sxs-lookup"><span data-stu-id="3d153-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3d153-143">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d153-144">陀螺仪</span><span class="sxs-lookup"><span data-stu-id="3d153-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3d153-145">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d153-146">磁力计</span><span class="sxs-lookup"><span data-stu-id="3d153-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3d153-147">✔️</span><span class="sxs-lookup"><span data-stu-id="3d153-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="3d153-148">启用研究模式 (HoloLens 第一代和 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="3d153-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="3d153-149">研究模式是开发人员模式的扩展。</span><span class="sxs-lookup"><span data-stu-id="3d153-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="3d153-150">在开始之前，需要启用设备的开发人员功能才能访问 "研究模式" 设置：</span><span class="sxs-lookup"><span data-stu-id="3d153-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="3d153-151">打开 " **开始" 菜单 > 设置** "，然后选择" **更新** "。</span><span class="sxs-lookup"><span data-stu-id="3d153-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="3d153-152">**为开发人员** 选择并启用 **开发人员模式** 。</span><span class="sxs-lookup"><span data-stu-id="3d153-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="3d153-153">**向下滚动** 并启用“设备门户”。</span><span class="sxs-lookup"><span data-stu-id="3d153-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="3d153-154">启用开发人员功能后， [连接到设备门户](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) 以启用研究模式功能：</span><span class="sxs-lookup"><span data-stu-id="3d153-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="3d153-155">在 **设备门户** 中转到 " **系统 > 研究模式** "。</span><span class="sxs-lookup"><span data-stu-id="3d153-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="3d153-156">选择 " **允许访问传感器流** "。</span><span class="sxs-lookup"><span data-stu-id="3d153-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="3d153-157">从页面顶部的 **Power** menu 项重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="3d153-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="3d153-158">重新启动设备后，通过 **设备门户** 加载的应用程序可以访问研究模式流。</span><span class="sxs-lookup"><span data-stu-id="3d153-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="3d153-159">![HoloLens 设备门户的研究模式选项卡](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="3d153-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="3d153-160">*HoloLens 设备门户中的研究模式窗口*</span><span class="sxs-lookup"><span data-stu-id="3d153-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d153-161">HoloLens 2 的研究模式从版本19041.1356 开始提供。</span><span class="sxs-lookup"><span data-stu-id="3d153-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="3d153-162">如果在早期版本中需要访问权限，请注册我们的预览 [体验](https://docs.microsoft.com/hololens/hololens-insider) 计划。</span><span class="sxs-lookup"><span data-stu-id="3d153-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="3d153-163">在应用中使用传感器数据</span><span class="sxs-lookup"><span data-stu-id="3d153-163">Using sensor data in your apps</span></span>

<span data-ttu-id="3d153-164">应用程序可以访问传感器流数据，其方式与通过 [媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)访问照片和视频相机流的方式相同。</span><span class="sxs-lookup"><span data-stu-id="3d153-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="3d153-165">适用于 HoloLens 开发的所有 Api 在研究模式下也可用。</span><span class="sxs-lookup"><span data-stu-id="3d153-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="3d153-166">具体而言，应用程序在每个传感器帧捕获时间确切地了解 HoloLens 在6DoF 空间的位置。</span><span class="sxs-lookup"><span data-stu-id="3d153-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="3d153-167">你可以在访问各种研究模式流时找到示例应用程序，使用 [内部函数和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，并在各自的研究模式存储库中记录流：</span><span class="sxs-lookup"><span data-stu-id="3d153-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="3d153-168">HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="3d153-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="3d153-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3d153-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="3d153-170">支持</span><span class="sxs-lookup"><span data-stu-id="3d153-170">Support</span></span>

<span data-ttu-id="3d153-171">对于 HoloLens (第一代) ，请使用 HoloLensForCV 存储库中的 [问题跟踪](https://github.com/Microsoft/HololensForCV/issues) 程序发布反馈并跟踪已知问题。</span><span class="sxs-lookup"><span data-stu-id="3d153-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="3d153-172">对于 HoloLens 2，请使用 HoloLens2ForCV 存储库中的 [问题跟踪](https://github.com/microsoft/HoloLens2ForCV/issues) 程序发布反馈并跟踪已知问题。</span><span class="sxs-lookup"><span data-stu-id="3d153-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d153-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="3d153-173">See also</span></span>

* [<span data-ttu-id="3d153-174">Microsoft 媒体基础</span><span class="sxs-lookup"><span data-stu-id="3d153-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="3d153-175">HoloLensForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="3d153-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="3d153-176">HoloLens2ForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="3d153-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="3d153-177">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="3d153-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
