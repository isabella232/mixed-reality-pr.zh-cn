---
title: 眼部追寻 MRTK
description: 在 MRTK 中为 Oculus Quest 配置的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Oculus Quest，
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908388"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="839ef-104">使用 XR SDK 管道生成 MRTK 并部署到 Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="839ef-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="839ef-105">需要[Oculus Quest。](https://www.oculus.com/quest/)</span><span class="sxs-lookup"><span data-stu-id="839ef-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="839ef-106">MRTK 对 Oculus Quest 的支持通过两个不同的源提供：Unity 的 XR SDK 管道和 Oculus Integration Unity 包。</span><span class="sxs-lookup"><span data-stu-id="839ef-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="839ef-107">**Oculus XRSDK 数据提供程序** 允许使用这两个源，并且必须使用 在 Oculus Quest 上部署 MRTK。</span><span class="sxs-lookup"><span data-stu-id="839ef-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="839ef-108">Unity [XR SDK 管道](https://docs.unity3d.com/Manual/XR.html) 支持将 Oculus Touch 控制器和头部跟踪与 Oculus Quest 一同使用。</span><span class="sxs-lookup"><span data-stu-id="839ef-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="839ef-109">此管道是在 Unity 2019.3 及更中开发 XR 应用程序的标准。</span><span class="sxs-lookup"><span data-stu-id="839ef-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="839ef-110">若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="839ef-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="839ef-111">这是 **将** MRTK 应用程序部署到 Oculus Quest 所需的。</span><span class="sxs-lookup"><span data-stu-id="839ef-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="839ef-112">[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许将 **手部跟踪与** Oculus Quest 一起使用。</span><span class="sxs-lookup"><span data-stu-id="839ef-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="839ef-113">此数据访问接口 **不使用** Unity 的 **XR SDK 管道** 或 **旧版 XR 管道**。</span><span class="sxs-lookup"><span data-stu-id="839ef-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="839ef-114">为 Oculus Quest 设置项目</span><span class="sxs-lookup"><span data-stu-id="839ef-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="839ef-115">请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保项目已准备好在 Oculus Quest 上部署。</span><span class="sxs-lookup"><span data-stu-id="839ef-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="839ef-116">确保在 [设备上启用](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="839ef-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="839ef-117">安装 Oculus ADB 驱动程序是可选的。</span><span class="sxs-lookup"><span data-stu-id="839ef-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="839ef-118">为 Oculus Quest 设置 XR SDK 管道</span><span class="sxs-lookup"><span data-stu-id="839ef-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="839ef-119">确保 **Oculus XR 插件** 安装在 **"窗口"--> 程序包管理器**</span><span class="sxs-lookup"><span data-stu-id="839ef-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="839ef-121">通过访问"编辑 --> 项目设置 "--> XR 插件管理 --> 插件提供程序，确保 **Oculus 插件提供程序包含在项目中**</span><span class="sxs-lookup"><span data-stu-id="839ef-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 插件提供程序](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="839ef-123">设置 Oculus Integration Unity 包以启用跟踪</span><span class="sxs-lookup"><span data-stu-id="839ef-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="839ef-124">从 Unity [资产存储下载并导入 Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 集成。</span><span class="sxs-lookup"><span data-stu-id="839ef-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="839ef-125">经过测试的最新版本为 20.0.0。</span><span class="sxs-lookup"><span data-stu-id="839ef-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="839ef-126">可以从此存档[找到旧版本。](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="839ef-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="839ef-127">导航到集成 Oculus Integration Unity 模块> Oculus >实用工具>混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="839ef-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="839ef-128">这样做会使用相关 Oculus Quest 代码正常运行所需的定义和引用来更新 asmdef。</span><span class="sxs-lookup"><span data-stu-id="839ef-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="839ef-129">它还将更新 csc 文件，以筛选出 Oculus 集成资产生成的过时警告。</span><span class="sxs-lookup"><span data-stu-id="839ef-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="839ef-130">MRTK 存储库包含将警告转换为错误的 csc 文件，此转换会MRTK-Quest配置过程。</span><span class="sxs-lookup"><span data-stu-id="839ef-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="839ef-132">在导入的 Oculus 文件夹 (应位于 Assets/Oculus) ，有一个可编写脚本的对象，名为 OculusProjectConfig。</span><span class="sxs-lookup"><span data-stu-id="839ef-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="839ef-133">在配置文件中，需要将 HandTrackingSupport 设置为"控制器和手"。</span><span class="sxs-lookup"><span data-stu-id="839ef-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus 集成控制器和手部](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="839ef-135">设置场景</span><span class="sxs-lookup"><span data-stu-id="839ef-135">Setting up the scene</span></span>

1. <span data-ttu-id="839ef-136">创建新的 Unity 场景或打开预先存在的场景，例如 HandInteractionExamples。</span><span class="sxs-lookup"><span data-stu-id="839ef-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="839ef-137">导航到"混合现实工具包""添加到场景"和"配置"，将 MRTK  >  **添加到场景**。</span><span class="sxs-lookup"><span data-stu-id="839ef-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="839ef-138">使用 Oculus XR SDK 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="839ef-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="839ef-139">将配置文件配置为使用 **Oculus XR SDK 数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="839ef-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="839ef-140">如果不打算修改配置文件</span><span class="sxs-lookup"><span data-stu-id="839ef-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="839ef-141">使用所有跨 Unity XR 管道配置的默认 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="839ef-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="839ef-142">以前的 DefaultXRSDKConfigurationProfile 现在标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="839ef-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="839ef-143">转到" [生成"，将项目部署到 Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="839ef-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="839ef-144">否则，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="839ef-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="839ef-145">选择层次结构中的 MixedRealityToolkit 游戏对象，然后选择"复制和自定义"以克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="839ef-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="839ef-147">选择" **输入** 配置文件"。</span><span class="sxs-lookup"><span data-stu-id="839ef-147">Select the **Input** Configuration Profile.</span></span>

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="839ef-149">在 **输入** 系统配置文件中选择"克隆"以启用修改。</span><span class="sxs-lookup"><span data-stu-id="839ef-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="839ef-151">打开"**输入数据提供程序"** 部分，选择顶部的"添加数据提供程序"，将在列表末尾添加新的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="839ef-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="839ef-152">打开新的数据访问接口，将"类型"设置为 **"Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager"。**</span><span class="sxs-lookup"><span data-stu-id="839ef-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="839ef-154">将配置文件配置为使用 **Oculus XR SDK 数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="839ef-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="839ef-155">如果不打算修改配置文件</span><span class="sxs-lookup"><span data-stu-id="839ef-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="839ef-156">将配置文件更改为 DefaultXRSDKConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="839ef-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="839ef-157">转到" [生成"，将项目部署到 Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="839ef-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="839ef-158">否则，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="839ef-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="839ef-159">选择层次结构中的 MixedRealityToolkit 游戏对象，然后选择"复制和自定义"以克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="839ef-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="839ef-161">选择" **输入** 配置文件"。</span><span class="sxs-lookup"><span data-stu-id="839ef-161">Select the **Input** Configuration Profile.</span></span>

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="839ef-163">在 **输入** 系统配置文件中选择"克隆"以启用修改。</span><span class="sxs-lookup"><span data-stu-id="839ef-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="839ef-165">打开"**输入数据提供程序"** 部分，选择顶部的"添加数据提供程序"，将在列表末尾添加新的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="839ef-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="839ef-166">打开新的数据访问接口，将"类型"设置为 **"Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager"。**</span><span class="sxs-lookup"><span data-stu-id="839ef-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="839ef-168">Oculus XR SDK 数据提供程序包括一个 OVR 相机设备预制器，它使用 OVR 相机设备以及 OVR 手自动配置项目，以正确路由输入。</span><span class="sxs-lookup"><span data-stu-id="839ef-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="839ef-169">手动将 OVR 相机设备添加到场景中需要手动配置设置和输入。</span><span class="sxs-lookup"><span data-stu-id="839ef-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="839ef-170">生成项目并部署到 Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="839ef-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="839ef-171">通过 USB 3.0 -> USB C 电缆插入 Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="839ef-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="839ef-172">导航到 **"文件>生成设置"**</span><span class="sxs-lookup"><span data-stu-id="839ef-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="839ef-173">将部署更改为 **Android**</span><span class="sxs-lookup"><span data-stu-id="839ef-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="839ef-174">确保选择 Oculus Quest 作为适用的运行设备</span><span class="sxs-lookup"><span data-stu-id="839ef-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 运行设备](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="839ef-176">选择"生成并运行"</span><span class="sxs-lookup"><span data-stu-id="839ef-176">Select Build and Run</span></span>
    - <span data-ttu-id="839ef-177">首次选择"生成并运行"时，可能会遇到以下一组 *生成错误* 。</span><span class="sxs-lookup"><span data-stu-id="839ef-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="839ef-178">再次选择"生成并运行"后，应该能够 *成功* 部署。</span><span class="sxs-lookup"><span data-stu-id="839ef-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 预期生成错误](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="839ef-180">从 _任务内部接受"允许 USB_ 调试"提示</span><span class="sxs-lookup"><span data-stu-id="839ef-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="839ef-181">在 Oculus 任务中查看场景</span><span class="sxs-lookup"><span data-stu-id="839ef-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="839ef-182">从项目中删除 Oculus 集成</span><span class="sxs-lookup"><span data-stu-id="839ef-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="839ef-183">导航到混合现实工具包 > Oculus >独立 Oculus Integration Unity 模块  ![ Oculus 分离 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="839ef-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="839ef-184">在此步骤中，将修改 Unity 作为 Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef 和其他文件中的引用进行刷新</span><span class="sxs-lookup"><span data-stu-id="839ef-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="839ef-185">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="839ef-185">Close Unity</span></span>
1. <span data-ttu-id="839ef-186">关闭Visual Studio（如果已打开）</span><span class="sxs-lookup"><span data-stu-id="839ef-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="839ef-187">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="839ef-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="839ef-188">删除 UnityProjectName/Library 目录</span><span class="sxs-lookup"><span data-stu-id="839ef-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="839ef-189">删除 UnityProjectName/Assets/Oculus 目录</span><span class="sxs-lookup"><span data-stu-id="839ef-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="839ef-190">删除 UnityProjectName/Assets/Oculus.meta 文件</span><span class="sxs-lookup"><span data-stu-id="839ef-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="839ef-191">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="839ef-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="839ef-192">常见错误</span><span class="sxs-lookup"><span data-stu-id="839ef-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="839ef-193">Unity 无法识别的探索</span><span class="sxs-lookup"><span data-stu-id="839ef-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="839ef-194">请确保正确配置 Android 路径。</span><span class="sxs-lookup"><span data-stu-id="839ef-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="839ef-195">如果仍然遇到问题，请遵循 [本指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="839ef-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="839ef-196">**在 Android >外部>编辑>首选项**</span><span class="sxs-lookup"><span data-stu-id="839ef-196">**Edit > Preferences > External Tools > Android**</span></span>

![Android 工具配置](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
