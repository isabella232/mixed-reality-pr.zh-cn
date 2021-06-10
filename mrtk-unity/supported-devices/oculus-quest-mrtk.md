---
title: 眼部追寻 MRTK
description: 用于在 MRTK 中配置 Oculus 寻找的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Oculus 寻找，
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441178"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="889f9-104">使用 XR SDK 管道构建 MRTK 并将其部署到 Oculus</span><span class="sxs-lookup"><span data-stu-id="889f9-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="889f9-105">需要 [Oculus](https://www.oculus.com/quest/) 请求。</span><span class="sxs-lookup"><span data-stu-id="889f9-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="889f9-106">MRTK 对 Oculus 的寻找支持通过两个不同的源： Unity 的 XR SDK 管道和 Oculus Integration Unity 包提供。</span><span class="sxs-lookup"><span data-stu-id="889f9-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="889f9-107">**OCULUS XRSDK 数据提供程序** 允许同时使用这两个源，并且必须用于在 Oculus 的寻找上部署 MRTK。</span><span class="sxs-lookup"><span data-stu-id="889f9-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="889f9-108">[UNITY XR SDK 管道](https://docs.unity3d.com/Manual/XR.html)允许使用 Oculus 触摸控制器和使用 Oculus 寻找进行头跟踪。</span><span class="sxs-lookup"><span data-stu-id="889f9-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="889f9-109">此管道是在 Unity 2019.3 和更高版本中开发 XR 应用程序的标准。</span><span class="sxs-lookup"><span data-stu-id="889f9-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="889f9-110">若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="889f9-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="889f9-111">这是将 MRTK 应用程序部署到 Oculus **请求所必需** 的。</span><span class="sxs-lookup"><span data-stu-id="889f9-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span> 

<span data-ttu-id="889f9-112">[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许在 Oculus 中使用 **手动跟踪**。</span><span class="sxs-lookup"><span data-stu-id="889f9-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="889f9-113">此数据访问接口 **不** 使用 Unity 的 **XR SDK 管道** 或 **旧的 XR 管道**。</span><span class="sxs-lookup"><span data-stu-id="889f9-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="889f9-114">设置 Oculus 的项目</span><span class="sxs-lookup"><span data-stu-id="889f9-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="889f9-115">请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保你的项目已准备好在 Oculus 上部署。</span><span class="sxs-lookup"><span data-stu-id="889f9-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="889f9-116">确保在你的设备上启用了 [开发人员模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。</span><span class="sxs-lookup"><span data-stu-id="889f9-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="889f9-117">安装 Oculus ADB 驱动程序是可选的。</span><span class="sxs-lookup"><span data-stu-id="889f9-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="889f9-118">设置用于 Oculus 的 XR SDK 管道</span><span class="sxs-lookup"><span data-stu-id="889f9-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="889f9-119">确保 **OCULUS XR 插件** 安装在 " **> 包管理器" 窗口** 中</span><span class="sxs-lookup"><span data-stu-id="889f9-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="889f9-121">转到 "**编辑 > 项目设置--> XR 插件" "> 插件提供程序**，确保项目中包含 Oculus 插件提供程序</span><span class="sxs-lookup"><span data-stu-id="889f9-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 插件提供程序](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="889f9-123">设置 Oculus Integration Unity 包以启用 handtracking</span><span class="sxs-lookup"><span data-stu-id="889f9-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="889f9-124">从 Unity 资产存储中下载并导入 [Oculus 集成](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。</span><span class="sxs-lookup"><span data-stu-id="889f9-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="889f9-125">已测试的最新版本为20.0.0。</span><span class="sxs-lookup"><span data-stu-id="889f9-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="889f9-126">可以从此[存档](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到旧版本</span><span class="sxs-lookup"><span data-stu-id="889f9-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="889f9-127">导航到混合现实工具包 > 实用程序 > Oculus > 集成 Oculus Integration Unity 模块。</span><span class="sxs-lookup"><span data-stu-id="889f9-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="889f9-128">执行此操作将更新 asmdefs，其中包含相关 Oculus 获取代码运行所需的定义和引用。</span><span class="sxs-lookup"><span data-stu-id="889f9-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="889f9-129">它还将更新 csc 文件，以筛选出 Oculus 集成资产生成的过时警告。</span><span class="sxs-lookup"><span data-stu-id="889f9-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="889f9-130">MRTK 存储库包含将警告转换为错误的 csc 文件，此转换会暂停 MRTK-Quest 配置过程。</span><span class="sxs-lookup"><span data-stu-id="889f9-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="889f9-132">在导入的 Oculus 文件夹中 (应在资产/Oculus) 中找到该文件夹，这是一个名为 OculusProjectConfig 的可编写脚本的对象。</span><span class="sxs-lookup"><span data-stu-id="889f9-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="889f9-133">在该配置文件中，需要将 HandTrackingSupport 设置为 "控制器和手"。</span><span class="sxs-lookup"><span data-stu-id="889f9-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus Integration 控制器和指针](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="889f9-135">设置场景</span><span class="sxs-lookup"><span data-stu-id="889f9-135">Setting up the scene</span></span>

1. <span data-ttu-id="889f9-136">创建新的 Unity 场景或打开预先存在的场景，如 HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="889f9-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="889f9-137">通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景</span><span class="sxs-lookup"><span data-stu-id="889f9-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="889f9-138">使用 Oculus XR SDK 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="889f9-138">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="889f9-139">将配置文件配置为使用 **OCULUS XR SDK 数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="889f9-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="889f9-140">如果不打算修改配置文件</span><span class="sxs-lookup"><span data-stu-id="889f9-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="889f9-141">将配置文件更改为 DefaultXRSDKConfigurationProfile，然后转到 [生成项目并将其部署到 Oculus 的寻找](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="889f9-141">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="889f9-142">否则，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="889f9-142">Otherwise follow the following:</span></span>
        - <span data-ttu-id="889f9-143">选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="889f9-143">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="889f9-145">选择 **输入** 配置文件</span><span class="sxs-lookup"><span data-stu-id="889f9-145">Select the **Input** Configuration Profile</span></span>

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="889f9-147">选择输入系统配置文件中的 " **克隆** " 以启用修改。</span><span class="sxs-lookup"><span data-stu-id="889f9-147">Select **Clone** in the input system profile to enable modification.</span></span>

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="889f9-149">打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据提供程序** "，新的数据访问接口将添加到列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="889f9-149">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="889f9-150">打开新的数据提供程序并将 **类型** 设置为 **MixedReality. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="889f9-150">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="889f9-152">Oculus XR SDK 数据提供程序包括一个 OVR 相机远程处理 Prefab，它自动使用 OVR 相机 Rig 配置项目，并使用 OVR 来正确路由输入。</span><span class="sxs-lookup"><span data-stu-id="889f9-152">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="889f9-153">手动将 OVR 摄像装置添加到场景需要手动配置设置和输入。</span><span class="sxs-lookup"><span data-stu-id="889f9-153">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="889f9-154">生成项目并将其部署到 Oculus 的寻找</span><span class="sxs-lookup"><span data-stu-id="889f9-154">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="889f9-155">通过 USB 3.0 > USB C 线插入 Oculus 寻找</span><span class="sxs-lookup"><span data-stu-id="889f9-155">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="889f9-156">导航到 **文件 > 生成设置**</span><span class="sxs-lookup"><span data-stu-id="889f9-156">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="889f9-157">将部署更改为 **Android**</span><span class="sxs-lookup"><span data-stu-id="889f9-157">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="889f9-158">确保选择 "Oculus" 作为适用的运行设备</span><span class="sxs-lookup"><span data-stu-id="889f9-158">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 运行设备](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="889f9-160">选择生成并运行</span><span class="sxs-lookup"><span data-stu-id="889f9-160">Select Build and Run</span></span>
    - <span data-ttu-id="889f9-161">当您选择 " *生成" 并* 首次运行时，您可能会遇到以下生成错误集。</span><span class="sxs-lookup"><span data-stu-id="889f9-161">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="889f9-162">选择 " *生成" 并再次运行* 后，应该能够成功部署。</span><span class="sxs-lookup"><span data-stu-id="889f9-162">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 预期生成错误](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="889f9-164">接受来自接收内部的 " _允许 USB 调试_ " 提示</span><span class="sxs-lookup"><span data-stu-id="889f9-164">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="889f9-165">查看 Oculus 的内部场景</span><span class="sxs-lookup"><span data-stu-id="889f9-165">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="889f9-166">从项目中删除 Oculus 集成</span><span class="sxs-lookup"><span data-stu-id="889f9-166">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="889f9-167">导航到混合现实工具包 > Oculus > 单独的 Oculus 集成 Unity 模块  ![ Oculus 隔离 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="889f9-167">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="889f9-168">允许 Unity 刷新为 MixedReality 中的引用，并在此步骤中修改其他文件</span><span class="sxs-lookup"><span data-stu-id="889f9-168">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="889f9-169">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="889f9-169">Close Unity</span></span>
1. <span data-ttu-id="889f9-170">关闭 Visual Studio （如果它已打开）</span><span class="sxs-lookup"><span data-stu-id="889f9-170">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="889f9-171">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="889f9-171">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="889f9-172">删除 UnityProjectName/库目录</span><span class="sxs-lookup"><span data-stu-id="889f9-172">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="889f9-173">删除 UnityProjectName/资产/Oculus 目录</span><span class="sxs-lookup"><span data-stu-id="889f9-173">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="889f9-174">删除 UnityProjectName/资产/Oculus 文件</span><span class="sxs-lookup"><span data-stu-id="889f9-174">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="889f9-175">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="889f9-175">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="889f9-176">常见错误</span><span class="sxs-lookup"><span data-stu-id="889f9-176">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="889f9-177">Unity 无法识别的寻找</span><span class="sxs-lookup"><span data-stu-id="889f9-177">Quest not recognized by Unity</span></span>

<span data-ttu-id="889f9-178">请确保正确配置了 Android 路径。</span><span class="sxs-lookup"><span data-stu-id="889f9-178">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="889f9-179">如果继续遇到问题，请遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="889f9-179">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="889f9-180">**> 外部工具 > Android 编辑 > 首选项**</span><span class="sxs-lookup"><span data-stu-id="889f9-180">**Edit > Preferences > External Tools > Android**</span></span>

![Android 工具配置](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
