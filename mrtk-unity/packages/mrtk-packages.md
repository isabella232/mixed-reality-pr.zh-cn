---
title: MRTK 包
description: 支持混合现实硬件和平台的 MRTK 中的包。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Unity 包管理器，
ms.openlocfilehash: 3c92448d99cd67efa0a06feff9b0c7561a6aea79
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143802"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="84871-104">混合现实工具包包</span><span class="sxs-lookup"><span data-stu-id="84871-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="84871-105">混合现实工具包 (MRTK) 是一系列包，通过为混合现实硬件和平台提供支持，实现跨平台混合现实应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="84871-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="84871-106">MRTK 可用作 [资产](#asset-packages) (. unitypackage) 包和通过 [Unity 包管理器](#unity-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="84871-106">MRTK is available as [asset](#asset-packages) (.unitypackage) packages and via the [Unity Package Manager](#unity-package-manager).</span></span>

## <a name="asset-packages"></a><span data-ttu-id="84871-107">资产包</span><span class="sxs-lookup"><span data-stu-id="84871-107">Asset packages</span></span>

<span data-ttu-id="84871-108">可以从 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下载 MRTK 资产 (. unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="84871-108">The MRTK asset (.unitypackage) can be downloaded from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span>

<span data-ttu-id="84871-109">使用资产包的一些优点包括：</span><span class="sxs-lookup"><span data-stu-id="84871-109">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="84871-110">适用于 Unity 2018.4 和更高版本</span><span class="sxs-lookup"><span data-stu-id="84871-110">Available for Unity 2018.4 and newer</span></span>
- <span data-ttu-id="84871-111">易于对 MRTK 进行更改</span><span class="sxs-lookup"><span data-stu-id="84871-111">Easy to make changes to MRTK</span></span>
  - <span data-ttu-id="84871-112">MRTK 位于 "资产" 文件夹中</span><span class="sxs-lookup"><span data-stu-id="84871-112">MRTK is in the Assets folder</span></span>

<span data-ttu-id="84871-113">下面是一些难点：</span><span class="sxs-lookup"><span data-stu-id="84871-113">Some of the challenges are:</span></span>

- <span data-ttu-id="84871-114">MRTK 是项目的 "资产" 文件夹的一部分，旨在</span><span class="sxs-lookup"><span data-stu-id="84871-114">MRTK is part of the project's Assets folder, leading to</span></span>
  - <span data-ttu-id="84871-115">大型项目</span><span class="sxs-lookup"><span data-stu-id="84871-115">Larger projects</span></span>
  - <span data-ttu-id="84871-116">编译时间较慢</span><span class="sxs-lookup"><span data-stu-id="84871-116">Slower compilation times</span></span>
- <span data-ttu-id="84871-117">无依赖关系管理</span><span class="sxs-lookup"><span data-stu-id="84871-117">No dependency management</span></span>
  - <span data-ttu-id="84871-118">客户需要手动解析包依赖关系</span><span class="sxs-lookup"><span data-stu-id="84871-118">Customers are required to resolve package dependencies manually</span></span>
- <span data-ttu-id="84871-119">手动更新过程</span><span class="sxs-lookup"><span data-stu-id="84871-119">Manual update process</span></span>
  - <span data-ttu-id="84871-120">多个步骤</span><span class="sxs-lookup"><span data-stu-id="84871-120">Multiple steps</span></span>
  - <span data-ttu-id="84871-121">大型 (3000 多个文件) 源代码管理更新</span><span class="sxs-lookup"><span data-stu-id="84871-121">Large (3000+ file) source control updates</span></span>
  - <span data-ttu-id="84871-122">丢失对 MRTK 进行的更改的风险</span><span class="sxs-lookup"><span data-stu-id="84871-122">Risk of losing changes made to MRTK</span></span>
- <span data-ttu-id="84871-123">导入示例包通常意味着包括所有示例</span><span class="sxs-lookup"><span data-stu-id="84871-123">Importing the examples package typically means including all examples</span></span>

<span data-ttu-id="84871-124">可用的包包括：</span><span class="sxs-lookup"><span data-stu-id="84871-124">The available packages are:</span></span>

- [<span data-ttu-id="84871-125">基础</span><span class="sxs-lookup"><span data-stu-id="84871-125">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="84871-126">扩展</span><span class="sxs-lookup"><span data-stu-id="84871-126">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="84871-127">工具</span><span class="sxs-lookup"><span data-stu-id="84871-127">Tools</span></span>](#tools-package)
- [<span data-ttu-id="84871-128">测试实用工具</span><span class="sxs-lookup"><span data-stu-id="84871-128">Test utilities</span></span>](#test-utilities-package)
- [<span data-ttu-id="84871-129">示例</span><span class="sxs-lookup"><span data-stu-id="84871-129">Examples</span></span>](#examples-package)

<span data-ttu-id="84871-130">这些包由 Microsoft 从 GitHub 上 mrtk_release 分支 [中的源代码](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 发布和支持。</span><span class="sxs-lookup"><span data-stu-id="84871-130">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

### <a name="foundation-package"></a><span data-ttu-id="84871-131">基础包</span><span class="sxs-lookup"><span data-stu-id="84871-131">Foundation package</span></span>

<span data-ttu-id="84871-132">混合现实工具包基础是一组代码，使应用程序能够跨混合现实平台利用常见功能。</span><span class="sxs-lookup"><span data-stu-id="84871-132">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<span data-ttu-id="84871-133"><sup>MRTK 基础包</sup></span><span class="sxs-lookup"><span data-stu-id="84871-133"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="84871-134">MRTK Foundation 包包含以下内容。</span><span class="sxs-lookup"><span data-stu-id="84871-134">The MRTK Foundation package contains the following.</span></span>

| <span data-ttu-id="84871-135">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-135">Folder</span></span> | <span data-ttu-id="84871-136">组件</span><span class="sxs-lookup"><span data-stu-id="84871-136">Component</span></span> | <span data-ttu-id="84871-137">说明</span><span class="sxs-lookup"><span data-stu-id="84871-137">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-138">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="84871-138">MRTK/Core</span></span> | | <span data-ttu-id="84871-139">接口和类型定义、基类、标准着色器。</span><span class="sxs-lookup"><span data-stu-id="84871-139">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="84871-140">MRTK/核心/提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-140">MRTK/Core/Providers</span></span> | | <span data-ttu-id="84871-141">与平台无关的数据访问者</span><span class="sxs-lookup"><span data-stu-id="84871-141">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="84871-142">手</span><span class="sxs-lookup"><span data-stu-id="84871-142">Hands</span></span> | <span data-ttu-id="84871-143">用于手部跟踪的基类支持和服务。</span><span class="sxs-lookup"><span data-stu-id="84871-143">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="84871-144">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="84871-144">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="84871-145">支持记录头部移动和手部跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="84871-145">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="84871-146">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="84871-146">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="84871-147">支持手动和眼睛输入的编辑器内模拟。</span><span class="sxs-lookup"><span data-stu-id="84871-147">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="84871-148">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="84871-148">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="84871-149">空间感知观察程序使用三维模型作为数据。</span><span class="sxs-lookup"><span data-stu-id="84871-149">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="84871-150">UnityInput</span><span class="sxs-lookup"><span data-stu-id="84871-150">UnityInput</span></span> | <span data-ttu-id="84871-151">公共输入设备 (操纵杆、鼠标等 ) 通过 Unity 的输入 API 实现。</span><span class="sxs-lookup"><span data-stu-id="84871-151">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="84871-152">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-152">MRTK/Providers</span></span> | | <span data-ttu-id="84871-153">平台特定的数据提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-153">Platform specific data providers</span></span> |
| | <span data-ttu-id="84871-154">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="84871-154">LeapMotion</span></span> | <span data-ttu-id="84871-155">对 UltraLeap Leap 运动控制器的支持。</span><span class="sxs-lookup"><span data-stu-id="84871-155">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="84871-156">OpenVR</span><span class="sxs-lookup"><span data-stu-id="84871-156">OpenVR</span></span> | <span data-ttu-id="84871-157">支持 OpenVR 设备。</span><span class="sxs-lookup"><span data-stu-id="84871-157">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="84871-158">Oculus</span><span class="sxs-lookup"><span data-stu-id="84871-158">Oculus</span></span> | <span data-ttu-id="84871-159">支持 Oculus 设备，如寻找。</span><span class="sxs-lookup"><span data-stu-id="84871-159">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="84871-160">UnityAR</span><span class="sxs-lookup"><span data-stu-id="84871-160">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="84871-161"> (试验性) 照相机设置提供程序启用 MRTK 与移动 AR 设备一起使用。</span><span class="sxs-lookup"><span data-stu-id="84871-161">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="84871-162">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="84871-162">WindowsMixedReality</span></span> | <span data-ttu-id="84871-163">支持 Windows Mixed Reality 设备，包括 Microsoft HoloLens 和沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="84871-163">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="84871-164">Windows</span><span class="sxs-lookup"><span data-stu-id="84871-164">Windows</span></span> | <span data-ttu-id="84871-165">支持 Microsoft Windows 特定的 Api，例如语音和听写。</span><span class="sxs-lookup"><span data-stu-id="84871-165">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="84871-166">XR SDK</span><span class="sxs-lookup"><span data-stu-id="84871-166">XR SDK</span></span> | <span data-ttu-id="84871-167"> (了对 unity 2019.3 和更高版本中 [unity 的 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的实验性) 支持。</span><span class="sxs-lookup"><span data-stu-id="84871-167">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="84871-168">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="84871-168">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="84871-169">实验</span><span class="sxs-lookup"><span data-stu-id="84871-169">Experimental</span></span> | <span data-ttu-id="84871-170">实验功能，包括着色器、用户界面控件和单个系统管理器。</span><span class="sxs-lookup"><span data-stu-id="84871-170">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="84871-171">功能</span><span class="sxs-lookup"><span data-stu-id="84871-171">Features</span></span> | <span data-ttu-id="84871-172">基于基础包生成的功能。</span><span class="sxs-lookup"><span data-stu-id="84871-172">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="84871-173">配置文件</span><span class="sxs-lookup"><span data-stu-id="84871-173">Profiles</span></span> | <span data-ttu-id="84871-174">Microsoft 混合现实工具包系统和服务的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="84871-174">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="84871-175">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="84871-175">StandardAssets</span></span> | <span data-ttu-id="84871-176">常见资产;模型、纹理、材料等。</span><span class="sxs-lookup"><span data-stu-id="84871-176">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="84871-177">MRTK/SceneSystemResources</span><span class="sxs-lookup"><span data-stu-id="84871-177">MRTK/SceneSystemResources</span></span> | | <span data-ttu-id="84871-178">场景系统使用的资产和资源</span><span class="sxs-lookup"><span data-stu-id="84871-178">Assets and resources used by the Scene System</span></span> |
| <span data-ttu-id="84871-179">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="84871-179">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="84871-180">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="84871-180">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="84871-181">实现 VR 边界支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-181">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="84871-182">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="84871-182">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="84871-183">实现相机配置和管理的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-183">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="84871-184">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="84871-184">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="84871-185">在应用程序诊断中实现的系统，例如可视化探查器。</span><span class="sxs-lookup"><span data-stu-id="84871-185">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="84871-186">InputSystem</span><span class="sxs-lookup"><span data-stu-id="84871-186">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="84871-187">为访问和处理用户输入提供支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-187">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="84871-188">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="84871-188">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="84871-189">提供多场景应用程序支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-189">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="84871-190">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="84871-190">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="84871-191">提供用户环境感知支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-191">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="84871-192">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="84871-192">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="84871-193">系统为远程传送提供支持 (移动跳转体验) 。</span><span class="sxs-lookup"><span data-stu-id="84871-193">System providing support for teleporting (moving about the experience in jumps).</span></span> |
| <span data-ttu-id="84871-194">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="84871-194">MRTK/StandardAssets</span></span> | | <span data-ttu-id="84871-195">混合现实体验的 MRTK 标准着色器、基本材料和其他标准资产</span><span class="sxs-lookup"><span data-stu-id="84871-195">MRTK Standard shader, basic materials and other standard assets for mixed reality experiences</span></span> |

### <a name="extensions-package"></a><span data-ttu-id="84871-196">扩展包</span><span class="sxs-lookup"><span data-stu-id="84871-196">Extensions package</span></span>

<span data-ttu-id="84871-197">可选的 Microsoft.MixedRealityToolkit.Unity.Extensions 包包含扩展 Microsoft Mixed Reality Toolkit 功能的其他服务。</span><span class="sxs-lookup"><span data-stu-id="84871-197">The optional Microsoft.MixedRealityToolkit.Unity.Extensions package includes additional services that extend the functionality of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="84871-198">扩展包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。</span><span class="sxs-lookup"><span data-stu-id="84871-198">The extensions package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="84871-199">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-199">Folder</span></span> | <span data-ttu-id="84871-200">组件</span><span class="sxs-lookup"><span data-stu-id="84871-200">Component</span></span> | <span data-ttu-id="84871-201">说明</span><span class="sxs-lookup"><span data-stu-id="84871-201">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-202">MRTK/扩展</span><span class="sxs-lookup"><span data-stu-id="84871-202">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="84871-203">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="84871-203">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="84871-204">向手部添加物理支持的服务。</span><span class="sxs-lookup"><span data-stu-id="84871-204">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="84871-205">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="84871-205">LostTrackingService</span></span> | <span data-ttu-id="84871-206">简化在设备上处理跟踪丢失Microsoft HoloLens的服务。</span><span class="sxs-lookup"><span data-stu-id="84871-206">Service that simplifies handling of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="84871-207">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="84871-207">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="84871-208">可简化平滑场景转换添加的服务。</span><span class="sxs-lookup"><span data-stu-id="84871-208">Service that simplifies adding smooth scene transitions.</span></span> |

### <a name="tools-package"></a><span data-ttu-id="84871-209">工具包</span><span class="sxs-lookup"><span data-stu-id="84871-209">Tools package</span></span>

<span data-ttu-id="84871-210">可选的 Microsoft.MixedRealityToolkit.Unity.Tools 包包含有用的工具，这些工具使用 Microsoft Mixed Reality Toolkit 增强混合现实开发体验。</span><span class="sxs-lookup"><span data-stu-id="84871-210">The optional Microsoft.MixedRealityToolkit.Unity.Tools package includes helpful tools that enhance the mixed reality development experience using the Microsoft Mixed Reality Toolkit.</span></span>
<span data-ttu-id="84871-211">这些工具位于 Unity 编辑器中的"混合现实工具包 **>实用工具** "菜单中。</span><span class="sxs-lookup"><span data-stu-id="84871-211">These tools are located in the **Mixed Reality Toolkit > Utilities** menu in the Unity Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="84871-212">工具包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。</span><span class="sxs-lookup"><span data-stu-id="84871-212">The tools package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="84871-213">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-213">Folder</span></span> | <span data-ttu-id="84871-214">组件</span><span class="sxs-lookup"><span data-stu-id="84871-214">Component</span></span> | <span data-ttu-id="84871-215">说明</span><span class="sxs-lookup"><span data-stu-id="84871-215">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-216">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="84871-216">MRTK/Tools</span></span> | |
| | <span data-ttu-id="84871-217">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="84871-217">BuildWindow</span></span> | <span data-ttu-id="84871-218">有助于简化 UWP 应用程序的生成和部署过程的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-218">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="84871-219">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="84871-219">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="84871-220">在项目中创建资产依赖项关系图的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-220">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="84871-221">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="84871-221">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="84871-222">用于帮助创建扩展服务的向导。</span><span class="sxs-lookup"><span data-stu-id="84871-222">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="84871-223">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="84871-223">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="84871-224">有助于更新使用不推荐使用的 MRTK 组件的代码的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-224">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="84871-225">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="84871-225">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="84871-226">用于帮助自动配置混合现实项目以获得 Unity 中最佳性能的实用程序。</span><span class="sxs-lookup"><span data-stu-id="84871-226">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="84871-227">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="84871-227">ReserializeAssetsUtility</span></span> | <span data-ttu-id="84871-228">提供对 reserializing 特定 Unity 文件的支持。</span><span class="sxs-lookup"><span data-stu-id="84871-228">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="84871-229">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="84871-229">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="84871-230">实用工具，使开发人员能够快速确定硬件控制器的 Unity 映射。</span><span class="sxs-lookup"><span data-stu-id="84871-230">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="84871-231">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="84871-231">ScreenshotUtility</span></span> | <span data-ttu-id="84871-232">启用在 Unity 编辑器中捕获应用程序映像。</span><span class="sxs-lookup"><span data-stu-id="84871-232">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="84871-233">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="84871-233">TextureCombinerWindow</span></span> | <span data-ttu-id="84871-234">用于合并图形纹理的实用程序。</span><span class="sxs-lookup"><span data-stu-id="84871-234">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="84871-235">工具箱</span><span class="sxs-lookup"><span data-stu-id="84871-235">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="84871-236">使用户能够轻松发现和使用 MRTK UX 组件的 UI。</span><span class="sxs-lookup"><span data-stu-id="84871-236">UI that makes it easy to discover and use MRTK UX components.</span></span> |

### <a name="test-utilities-package"></a><span data-ttu-id="84871-237">测试实用工具包</span><span class="sxs-lookup"><span data-stu-id="84871-237">Test utilities package</span></span>

<span data-ttu-id="84871-238">可选的 MixedRealityToolkit 包是帮助器脚本的集合，可让开发人员轻松 [创建播放模式测试](../contributing/unit-tests.md#play-mode-tests)。</span><span class="sxs-lookup"><span data-stu-id="84871-238">The optional Microsoft.MixedRealityToolkit.TestUtilities package is a collection of helper scripts that enable developers to easily [create play mode tests](../contributing/unit-tests.md#play-mode-tests).</span></span> <span data-ttu-id="84871-239">对于创建 MRTK 组件的开发人员而言，这些实用工具特别有用。</span><span class="sxs-lookup"><span data-stu-id="84871-239">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="84871-240">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-240">Folder</span></span> | <span data-ttu-id="84871-241">组件</span><span class="sxs-lookup"><span data-stu-id="84871-241">Component</span></span> | <span data-ttu-id="84871-242">说明</span><span class="sxs-lookup"><span data-stu-id="84871-242">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-243">MRTK/测试</span><span class="sxs-lookup"><span data-stu-id="84871-243">MRTK/Tests</span></span> | |
| | <span data-ttu-id="84871-244">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="84871-244">TestUtilities</span></span> | <span data-ttu-id="84871-245">用于简化播放模式测试（包括手动模拟实用程序）的创建的方法。</span><span class="sxs-lookup"><span data-stu-id="84871-245">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

### <a name="examples-package"></a><span data-ttu-id="84871-246">示例包</span><span class="sxs-lookup"><span data-stu-id="84871-246">Examples package</span></span>

<span data-ttu-id="84871-247">示例包包含演示、示例脚本和在基础包中练习功能的示例场景。</span><span class="sxs-lookup"><span data-stu-id="84871-247">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="84871-248">此包包含 [handInteractionExample](../features/example-scenes/hand-interaction-examples.md) 场景 (如下图) 其中包含响应各种手动输入的示例对象，这些对象 (表达和非) 。</span><span class="sxs-lookup"><span data-stu-id="84871-248">This package contains the [HandInteractionExample scene](../features/example-scenes/hand-interaction-examples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![HandInteractionExample 场景](../features/images/MRTK_Examples.png)

<span data-ttu-id="84871-250">此包还包含眼动跟踪演示， [此处记录了这些演示](../features/example-scenes/eye-tracking-examples-overview.md)</span><span class="sxs-lookup"><span data-stu-id="84871-250">This package also contains eye tracking demos, which are [documented here](../features/example-scenes/eye-tracking-examples-overview.md)</span></span>

<span data-ttu-id="84871-251">更一般而言，MRTK 中任何新功能都应包含示例包中的相应示例，大致遵循相同的文件夹结构和位置。</span><span class="sxs-lookup"><span data-stu-id="84871-251">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

> [!NOTE]
> <span data-ttu-id="84871-252">示例包需要 Microsoft.MixedRealityToolkit.Unity.Foundation。</span><span class="sxs-lookup"><span data-stu-id="84871-252">The examples package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="84871-253">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-253">Folder</span></span> | <span data-ttu-id="84871-254">组件</span><span class="sxs-lookup"><span data-stu-id="84871-254">Component</span></span> | <span data-ttu-id="84871-255">说明</span><span class="sxs-lookup"><span data-stu-id="84871-255">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-256">MRTK/示例</span><span class="sxs-lookup"><span data-stu-id="84871-256">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="84871-257">演示</span><span class="sxs-lookup"><span data-stu-id="84871-257">Demos</span></span> | <span data-ttu-id="84871-258">演示一个或两个相关功能的简单场景。</span><span class="sxs-lookup"><span data-stu-id="84871-258">Simple scenes illustrating one or two related features.</span></span> |
| | <span data-ttu-id="84871-259">实验</span><span class="sxs-lookup"><span data-stu-id="84871-259">Experimental</span></span> | <span data-ttu-id="84871-260">演示实验性功能的演示场景。</span><span class="sxs-lookup"><span data-stu-id="84871-260">Demo scenes illustrating experimental features.</span></span> |
| | <span data-ttu-id="84871-261">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="84871-261">StandardAssets</span></span> | <span data-ttu-id="84871-262">由多个演示场景共享的常见资产。</span><span class="sxs-lookup"><span data-stu-id="84871-262">Common assets shared by multiple demo scenes.</span></span> |

## <a name="unity-package-manager"></a><span data-ttu-id="84871-263">Unity 程序包管理器</span><span class="sxs-lookup"><span data-stu-id="84871-263">Unity Package Manager</span></span>

<span data-ttu-id="84871-264">对于使用 Unity 2019.4 及更高版本创建的体验，MRTK 可通过 [Unity](https://docs.unity3d.com/Manual/Packages.html)程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="84871-264">For experiences being created using Unity 2019.4 and newer, the MRTK is available via the [Unity Package Manager](https://docs.unity3d.com/Manual/Packages.html).</span></span>

<span data-ttu-id="84871-265">使用资产包的一些好处包括：</span><span class="sxs-lookup"><span data-stu-id="84871-265">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="84871-266">较小的项目</span><span class="sxs-lookup"><span data-stu-id="84871-266">Smaller projects</span></span>
  - <span data-ttu-id="84871-267">更Visual Studio解决方案</span><span class="sxs-lookup"><span data-stu-id="84871-267">Cleaner Visual Studio solutions</span></span>
  - <span data-ttu-id="84871-268">在 MRTK (签入的文件更少是文件中简单的 `Packages/manifest.json`) </span><span class="sxs-lookup"><span data-stu-id="84871-268">Fewer files to check in (MRTK is a simple reference in the `Packages/manifest.json` file)</span></span>
- <span data-ttu-id="84871-269">更快的编译速度</span><span class="sxs-lookup"><span data-stu-id="84871-269">Faster compilation</span></span>
  - <span data-ttu-id="84871-270">Unity 无需在生成期间重新编译 MRTK</span><span class="sxs-lookup"><span data-stu-id="84871-270">Unity does not need to recompile MRTK during building</span></span>
- <span data-ttu-id="84871-271">依赖项解析</span><span class="sxs-lookup"><span data-stu-id="84871-271">Dependency resolution</span></span>
  - <span data-ttu-id="84871-272">指定包含依赖项的包时，将自动安装所需的 MRTK 包</span><span class="sxs-lookup"><span data-stu-id="84871-272">Required MRTK packages are automatically installed when specifying packages with dependencies</span></span>
- <span data-ttu-id="84871-273">轻松更新到新的 MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="84871-273">Easy update to new MRTK versions</span></span>
  - <span data-ttu-id="84871-274">更改文件中的版本 `Packages/manifest.json`</span><span class="sxs-lookup"><span data-stu-id="84871-274">Change the version in the `Packages/manifest.json` file</span></span>

<span data-ttu-id="84871-275">下面是一些难点：</span><span class="sxs-lookup"><span data-stu-id="84871-275">Some of the challenges are:</span></span>

- <span data-ttu-id="84871-276">MRTK 不可变</span><span class="sxs-lookup"><span data-stu-id="84871-276">MRTK is immutable</span></span>
  - <span data-ttu-id="84871-277">无法进行更改，因为在包解析过程中没有删除它们</span><span class="sxs-lookup"><span data-stu-id="84871-277">Cannot make changes without them being removed during package resolution</span></span>
- <span data-ttu-id="84871-278">MRTK 不支持包含 Unity 2018.4 的 UPM 包</span><span class="sxs-lookup"><span data-stu-id="84871-278">MRTK does not support UPM packages with Unity 2018.4</span></span>

### <a name="foundation-package"></a><span data-ttu-id="84871-279">Foundation 包</span><span class="sxs-lookup"><span data-stu-id="84871-279">Foundation package</span></span>

<span data-ttu-id="84871-280">基础软件包 (`com.microsoft.mixedreality.toolkit.foundation`) 构成混合现实工具包的基础。</span><span class="sxs-lookup"><span data-stu-id="84871-280">The foundation package (`com.microsoft.mixedreality.toolkit.foundation`) forms the basis of the Mixed Reality Toolkit.</span></span>

| <span data-ttu-id="84871-281">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-281">Folder</span></span> | <span data-ttu-id="84871-282">组件</span><span class="sxs-lookup"><span data-stu-id="84871-282">Component</span></span> | <span data-ttu-id="84871-283">说明</span><span class="sxs-lookup"><span data-stu-id="84871-283">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-284">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="84871-284">MRTK/Core</span></span> | | <span data-ttu-id="84871-285">接口和类型定义、基类、标准着色器。</span><span class="sxs-lookup"><span data-stu-id="84871-285">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="84871-286">MRTK/核心/提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-286">MRTK/Core/Providers</span></span> | | <span data-ttu-id="84871-287">平台不可知数据提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-287">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="84871-288">经验</span><span class="sxs-lookup"><span data-stu-id="84871-288">Hands</span></span> | <span data-ttu-id="84871-289">用于手动跟踪的基类支持和服务。</span><span class="sxs-lookup"><span data-stu-id="84871-289">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="84871-290">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="84871-290">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="84871-291">支持记录磁头移动和手动跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="84871-291">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="84871-292">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="84871-292">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="84871-293">支持手动模拟手写和目视输入。</span><span class="sxs-lookup"><span data-stu-id="84871-293">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="84871-294">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="84871-294">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="84871-295">使用三维模型作为数据的空间感知观察程序。</span><span class="sxs-lookup"><span data-stu-id="84871-295">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="84871-296">UnityInput</span><span class="sxs-lookup"><span data-stu-id="84871-296">UnityInput</span></span> | <span data-ttu-id="84871-297">公共输入设备 (操纵杆、鼠标等 ) 通过 Unity 的输入 API 实现。</span><span class="sxs-lookup"><span data-stu-id="84871-297">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="84871-298">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-298">MRTK/Providers</span></span> | | <span data-ttu-id="84871-299">平台特定的数据提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-299">Platform specific data providers</span></span> |
| | <span data-ttu-id="84871-300">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="84871-300">LeapMotion</span></span> | <span data-ttu-id="84871-301">对 UltraLeap Leap 运动控制器的支持。</span><span class="sxs-lookup"><span data-stu-id="84871-301">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="84871-302">OpenVR</span><span class="sxs-lookup"><span data-stu-id="84871-302">OpenVR</span></span> | <span data-ttu-id="84871-303">支持 OpenVR 设备。</span><span class="sxs-lookup"><span data-stu-id="84871-303">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="84871-304">Oculus</span><span class="sxs-lookup"><span data-stu-id="84871-304">Oculus</span></span> | <span data-ttu-id="84871-305">支持 Oculus 设备，如寻找。</span><span class="sxs-lookup"><span data-stu-id="84871-305">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="84871-306">UnityAR</span><span class="sxs-lookup"><span data-stu-id="84871-306">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="84871-307"> (试验性) 照相机设置提供程序启用 MRTK 与移动 AR 设备一起使用。</span><span class="sxs-lookup"><span data-stu-id="84871-307">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="84871-308">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="84871-308">WindowsMixedReality</span></span> | <span data-ttu-id="84871-309">支持 Windows Mixed Reality 设备，包括 Microsoft HoloLens 和沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="84871-309">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="84871-310">Windows</span><span class="sxs-lookup"><span data-stu-id="84871-310">Windows</span></span> | <span data-ttu-id="84871-311">支持 Microsoft Windows 特定的 Api，例如语音和听写。</span><span class="sxs-lookup"><span data-stu-id="84871-311">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="84871-312">XR SDK</span><span class="sxs-lookup"><span data-stu-id="84871-312">XR SDK</span></span> | <span data-ttu-id="84871-313"> (了对 unity 2019.3 和更高版本中 [unity 的 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的实验性) 支持。</span><span class="sxs-lookup"><span data-stu-id="84871-313">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="84871-314">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="84871-314">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="84871-315">实验</span><span class="sxs-lookup"><span data-stu-id="84871-315">Experimental</span></span> | <span data-ttu-id="84871-316">实验功能，包括着色器、用户界面控件和单个系统管理器。</span><span class="sxs-lookup"><span data-stu-id="84871-316">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="84871-317">功能</span><span class="sxs-lookup"><span data-stu-id="84871-317">Features</span></span> | <span data-ttu-id="84871-318">基于基础包生成的功能。</span><span class="sxs-lookup"><span data-stu-id="84871-318">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="84871-319">配置文件</span><span class="sxs-lookup"><span data-stu-id="84871-319">Profiles</span></span> | <span data-ttu-id="84871-320">Microsoft 混合现实工具包系统和服务的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="84871-320">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="84871-321">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="84871-321">StandardAssets</span></span> | <span data-ttu-id="84871-322">常见资产;模型、纹理、材料等。</span><span class="sxs-lookup"><span data-stu-id="84871-322">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="84871-323">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="84871-323">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="84871-324">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="84871-324">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="84871-325">实现 VR 边界支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-325">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="84871-326">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="84871-326">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="84871-327">实现相机配置和管理的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-327">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="84871-328">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="84871-328">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="84871-329">在应用程序诊断中实现的系统，例如可视化探查器。</span><span class="sxs-lookup"><span data-stu-id="84871-329">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="84871-330">InputSystem</span><span class="sxs-lookup"><span data-stu-id="84871-330">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="84871-331">为访问和处理用户输入提供支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-331">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="84871-332">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="84871-332">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="84871-333">提供多场景应用程序支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-333">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="84871-334">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="84871-334">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="84871-335">提供用户环境感知支持的系统。</span><span class="sxs-lookup"><span data-stu-id="84871-335">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="84871-336">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="84871-336">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="84871-337">系统为远程传送提供支持 (移动跳转体验) 。</span><span class="sxs-lookup"><span data-stu-id="84871-337">System providing support for teleporting (moving about the experience in jumps).</span></span> |

<span data-ttu-id="84871-338">依赖项：</span><span class="sxs-lookup"><span data-stu-id="84871-338">Dependencies:</span></span>

- <span data-ttu-id="84871-339">标准资产 `com.microsoft.mixedreality.toolkit.standardassets` () </span><span class="sxs-lookup"><span data-stu-id="84871-339">Standard Assets (`com.microsoft.mixedreality.toolkit.standardassets`)</span></span>

### <a name="standard-assets"></a><span data-ttu-id="84871-340">标准资产</span><span class="sxs-lookup"><span data-stu-id="84871-340">Standard Assets</span></span>

<span data-ttu-id="84871-341">标准资产包 (是建议用于所有混合现实体验的组件集合， `com.microsoft.mixedreality.toolkit.standardassets)` 包括：</span><span class="sxs-lookup"><span data-stu-id="84871-341">The standard assets package (`com.microsoft.mixedreality.toolkit.standardassets)` is a collection of components that are recommended for all mixed reality experiences, including:</span></span>

- <span data-ttu-id="84871-342">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="84871-342">MRTK Standard shader</span></span>
- <span data-ttu-id="84871-343">使用 MRTK 标准着色器的基本材料</span><span class="sxs-lookup"><span data-stu-id="84871-343">Basic materials using the MRTK Standard shader</span></span>
- <span data-ttu-id="84871-344">音频文件</span><span class="sxs-lookup"><span data-stu-id="84871-344">Audio files</span></span>
- <span data-ttu-id="84871-345">字体</span><span class="sxs-lookup"><span data-stu-id="84871-345">Fonts</span></span>
- <span data-ttu-id="84871-346">纹理</span><span class="sxs-lookup"><span data-stu-id="84871-346">Textures</span></span>
- <span data-ttu-id="84871-347">图标</span><span class="sxs-lookup"><span data-stu-id="84871-347">Icons</span></span>

> [!Note]
> <span data-ttu-id="84871-348">若要避免基于程序集定义的重大更改，用于控制 MRTK 标准着色器的某些功能的脚本不包括在标准资产包中。</span><span class="sxs-lookup"><span data-stu-id="84871-348">To avoid breaking changes based on assembly definitions, the scripts used to control some features of the MRTK Standard shader are not included in the standard assets package.</span></span> <span data-ttu-id="84871-349">可以在文件夹的基础包中找到这些脚本 `MRTK/Core/Utilities/StandardShader` 。</span><span class="sxs-lookup"><span data-stu-id="84871-349">These scripts can be found in the foundation package in the `MRTK/Core/Utilities/StandardShader` folder.</span></span>

<span data-ttu-id="84871-350">依赖关系：无</span><span class="sxs-lookup"><span data-stu-id="84871-350">Dependencies: none</span></span>

### <a name="extension-packages"></a><span data-ttu-id="84871-351">扩展包</span><span class="sxs-lookup"><span data-stu-id="84871-351">Extension packages</span></span>

<span data-ttu-id="84871-352">可选扩展包 (`com.microsoft.mixedreality.toolkit.extensions)` 包含扩展 MRTK 功能的附加组件。</span><span class="sxs-lookup"><span data-stu-id="84871-352">The optional extensions package (`com.microsoft.mixedreality.toolkit.extensions)` contains additional components that expand the functionality of the MRTK.</span></span>

| <span data-ttu-id="84871-353">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-353">Folder</span></span> | <span data-ttu-id="84871-354">组件</span><span class="sxs-lookup"><span data-stu-id="84871-354">Component</span></span> | <span data-ttu-id="84871-355">说明</span><span class="sxs-lookup"><span data-stu-id="84871-355">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-356">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="84871-356">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="84871-357">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="84871-357">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="84871-358">将物理支持添加到明确表述的服务。</span><span class="sxs-lookup"><span data-stu-id="84871-358">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="84871-359">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="84871-359">LostTrackingService</span></span> | <span data-ttu-id="84871-360">简化在 Microsoft HoloLens 设备上处理跟踪丢失情况的服务。</span><span class="sxs-lookup"><span data-stu-id="84871-360">Service that simplifies handing of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="84871-361">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="84871-361">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="84871-362">简化场景过渡的简化。</span><span class="sxs-lookup"><span data-stu-id="84871-362">Service that simplifies adding smooth scene transitions.</span></span> |
| | <span data-ttu-id="84871-363">示例 ~</span><span class="sxs-lookup"><span data-stu-id="84871-363">Samples~</span></span> | <span data-ttu-id="84871-364">Unity 编辑器中的隐藏 () 包含样本场景和资产的文件夹。</span><span class="sxs-lookup"><span data-stu-id="84871-364">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |

<span data-ttu-id="84871-365">有关使用包含示例项目的包的过程的更多详细信息，请参阅 [混合现实工具包和 Unity 包管理器](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 一文。</span><span class="sxs-lookup"><span data-stu-id="84871-365">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

<span data-ttu-id="84871-366">依赖项：</span><span class="sxs-lookup"><span data-stu-id="84871-366">Dependencies:</span></span>

- <span data-ttu-id="84871-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="84871-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="tools-package"></a><span data-ttu-id="84871-368">工具包</span><span class="sxs-lookup"><span data-stu-id="84871-368">Tools package</span></span>

<span data-ttu-id="84871-369">可选的工具包 (`com.microsoft.mixedreality.toolkit.tools)` 包含可用于创建混合现实体验的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-369">The optional tools package (`com.microsoft.mixedreality.toolkit.tools)` contains tools that are useful for creating mixed reality experiences.</span></span> <span data-ttu-id="84871-370">通常，这些工具是编辑器组件，其代码不作为应用程序的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="84871-370">In general, these tools are editor components and their code does not ship as part of an application.</span></span>

| <span data-ttu-id="84871-371">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-371">Folder</span></span> | <span data-ttu-id="84871-372">组件</span><span class="sxs-lookup"><span data-stu-id="84871-372">Component</span></span> | <span data-ttu-id="84871-373">说明</span><span class="sxs-lookup"><span data-stu-id="84871-373">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-374">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="84871-374">MRTK/Tools</span></span> | |
| | <span data-ttu-id="84871-375">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="84871-375">BuildWindow</span></span> | <span data-ttu-id="84871-376">有助于简化生成和部署 UWP 应用程序的过程的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-376">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="84871-377">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="84871-377">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="84871-378">用于创建项目中资产的依赖项关系图的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-378">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="84871-379">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="84871-379">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="84871-380">用于帮助创建扩展服务的向导。</span><span class="sxs-lookup"><span data-stu-id="84871-380">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="84871-381">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="84871-381">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="84871-382">有助于更新使用不推荐使用的 MRTK 组件的代码的工具。</span><span class="sxs-lookup"><span data-stu-id="84871-382">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="84871-383">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="84871-383">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="84871-384">用于帮助自动配置混合现实项目以获得 Unity 中最佳性能的实用程序。</span><span class="sxs-lookup"><span data-stu-id="84871-384">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="84871-385">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="84871-385">ReserializeAssetsUtility</span></span> | <span data-ttu-id="84871-386">提供对 reserializing 特定 Unity 文件的支持。</span><span class="sxs-lookup"><span data-stu-id="84871-386">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="84871-387">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="84871-387">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="84871-388">实用工具，使开发人员能够快速确定硬件控制器的 Unity 映射。</span><span class="sxs-lookup"><span data-stu-id="84871-388">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="84871-389">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="84871-389">ScreenshotUtility</span></span> | <span data-ttu-id="84871-390">启用在 Unity 编辑器中捕获应用程序映像。</span><span class="sxs-lookup"><span data-stu-id="84871-390">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="84871-391">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="84871-391">TextureCombinerWindow</span></span> | <span data-ttu-id="84871-392">用于合并图形纹理的实用程序。</span><span class="sxs-lookup"><span data-stu-id="84871-392">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="84871-393">工具箱</span><span class="sxs-lookup"><span data-stu-id="84871-393">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="84871-394">使用户能够轻松发现和使用 MRTK UX 组件的 UI。</span><span class="sxs-lookup"><span data-stu-id="84871-394">UI that makes it easy to discover and use MRTK UX components.</span></span> |

<span data-ttu-id="84871-395">依赖项：</span><span class="sxs-lookup"><span data-stu-id="84871-395">Dependencies:</span></span>

- <span data-ttu-id="84871-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="84871-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="test-utilities-package"></a><span data-ttu-id="84871-397">测试实用工具包</span><span class="sxs-lookup"><span data-stu-id="84871-397">Test utilities package</span></span>

<span data-ttu-id="84871-398">可选的测试实用工具包 () 包含一系列帮助程序脚本，开发人员可以轻松地 `com.microsoft.mixedreality.toolkit.testutilities` 创建播放模式测试。</span><span class="sxs-lookup"><span data-stu-id="84871-398">The optional test utilities package (`com.microsoft.mixedreality.toolkit.testutilities`) contains a collection of helper scripts that enable developers to easily create play mode tests.</span></span> <span data-ttu-id="84871-399">这些实用工具对于创建 MRTK 组件的开发人员特别有用。</span><span class="sxs-lookup"><span data-stu-id="84871-399">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="84871-400">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-400">Folder</span></span> | <span data-ttu-id="84871-401">组件</span><span class="sxs-lookup"><span data-stu-id="84871-401">Component</span></span> | <span data-ttu-id="84871-402">说明</span><span class="sxs-lookup"><span data-stu-id="84871-402">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-403">MRTK/测试</span><span class="sxs-lookup"><span data-stu-id="84871-403">MRTK/Tests</span></span> | |
| | <span data-ttu-id="84871-404">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="84871-404">TestUtilities</span></span> | <span data-ttu-id="84871-405">简化播放模式测试创建的方法，包括手动模拟实用工具。</span><span class="sxs-lookup"><span data-stu-id="84871-405">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

<span data-ttu-id="84871-406">依赖项：</span><span class="sxs-lookup"><span data-stu-id="84871-406">Dependencies:</span></span>

- <span data-ttu-id="84871-407">基础 `com.microsoft.mixedreality.toolkit.foundation` () </span><span class="sxs-lookup"><span data-stu-id="84871-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="examples-package"></a><span data-ttu-id="84871-408">示例包</span><span class="sxs-lookup"><span data-stu-id="84871-408">Examples package</span></span>

<span data-ttu-id="84871-409">示例包 `com.microsoft.mixedreality.toolkit.examples` () ，其结构允许开发人员仅导入感兴趣的示例。</span><span class="sxs-lookup"><span data-stu-id="84871-409">The examples package (`com.microsoft.mixedreality.toolkit.examples`), is structured to allow developers to import only the examples of interest.</span></span>

<span data-ttu-id="84871-410">有关使用包含示例项目的包过程的更多详细信息，请参阅混合现实工具包和 [Unity 程序包管理器](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 文章。</span><span class="sxs-lookup"><span data-stu-id="84871-410">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

| <span data-ttu-id="84871-411">文件夹</span><span class="sxs-lookup"><span data-stu-id="84871-411">Folder</span></span> | <span data-ttu-id="84871-412">组件</span><span class="sxs-lookup"><span data-stu-id="84871-412">Component</span></span> | <span data-ttu-id="84871-413">说明</span><span class="sxs-lookup"><span data-stu-id="84871-413">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="84871-414">MRTK/示例</span><span class="sxs-lookup"><span data-stu-id="84871-414">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="84871-415">示例~</span><span class="sxs-lookup"><span data-stu-id="84871-415">Samples~</span></span> | <span data-ttu-id="84871-416">Unity 编辑器 (隐藏) 包含示例场景和资产的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="84871-416">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |
| | <span data-ttu-id="84871-417">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="84871-417">StandardAssets</span></span> | <span data-ttu-id="84871-418">由多个演示场景共享的常见资产。</span><span class="sxs-lookup"><span data-stu-id="84871-418">Common assets shared by multiple demo scenes.</span></span> |

<span data-ttu-id="84871-419">依赖项：</span><span class="sxs-lookup"><span data-stu-id="84871-419">Dependencies:</span></span>

- <span data-ttu-id="84871-420">基础 `com.microsoft.mixedreality.toolkit.foundation` () </span><span class="sxs-lookup"><span data-stu-id="84871-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>
- <span data-ttu-id="84871-421">扩展 (`com.microsoft.mixedreality.toolkit.extensions`)</span><span class="sxs-lookup"><span data-stu-id="84871-421">Extensions (`com.microsoft.mixedreality.toolkit.extensions`)</span></span>

## <a name="see-also"></a><span data-ttu-id="84871-422">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84871-422">See also</span></span>

- [<span data-ttu-id="84871-423">体系结构概述</span><span class="sxs-lookup"><span data-stu-id="84871-423">Architecture Overview</span></span>](../architecture/overview.md)
- [<span data-ttu-id="84871-424">系统、扩展服务和数据提供程序</span><span class="sxs-lookup"><span data-stu-id="84871-424">Systems, Extension Services and Data Providers</span></span>](../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="84871-425">混合现实工具包和 Unity 程序包管理器</span><span class="sxs-lookup"><span data-stu-id="84871-425">Mixed Reality Toolkit and Unity Package Manager</span></span>](../configuration/usingupm.md)
