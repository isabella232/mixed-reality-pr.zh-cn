---
title: 生成并部署到 Oculus 的寻找
description: 用于在 MRTK 中配置 Oculus 寻找的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Oculus 寻找
ms.openlocfilehash: 96b4b5b8a68c3b61d54b6796ba01c9e2516ba959
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449756"
---
# <a name="building-and-deploying-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="ce078-104">使用 XR SDK 管道生成并部署到 Oculus 的情况</span><span class="sxs-lookup"><span data-stu-id="ce078-104">Building and deploying to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="ce078-105">需要 [Oculus](https://www.oculus.com/quest/) 请求。</span><span class="sxs-lookup"><span data-stu-id="ce078-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="ce078-106">MRTK 对 Oculus 的寻找支持通过两个不同的源： Unity 的 XR SDK 管道和 Oculus Integration Unity 包提供。</span><span class="sxs-lookup"><span data-stu-id="ce078-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="ce078-107">**OCULUS XRSDK 数据提供程序** 允许同时使用这两个源，并且必须用于在 Oculus 的寻找上部署 MRTK。</span><span class="sxs-lookup"><span data-stu-id="ce078-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="ce078-108">[UNITY XR SDK 管道](https://docs.unity3d.com/Manual/XR.html)允许使用 Oculus 触摸控制器和使用 Oculus 寻找进行头跟踪。</span><span class="sxs-lookup"><span data-stu-id="ce078-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="ce078-109">此管道是在 Unity 2019.3 和更高版本中开发 XR 应用程序的标准。</span><span class="sxs-lookup"><span data-stu-id="ce078-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="ce078-110">若要使用此管道，请确保使用 **Unity 2019.3 或更高版本**。</span><span class="sxs-lookup"><span data-stu-id="ce078-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="ce078-111">这是将 MRTK 应用程序部署到 Oculus **请求所必需** 的。</span><span class="sxs-lookup"><span data-stu-id="ce078-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="ce078-112">[Oculus Integration Unity 包](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)允许在 Oculus 中使用 **手动跟踪**。</span><span class="sxs-lookup"><span data-stu-id="ce078-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="ce078-113">此数据访问接口 **不** 使用 Unity 的 **XR SDK 管道** 或 **旧的 XR 管道**。</span><span class="sxs-lookup"><span data-stu-id="ce078-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="ce078-114">设置 Oculus 的项目</span><span class="sxs-lookup"><span data-stu-id="ce078-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="ce078-115">请按照 [以下步骤](https://developer.oculus.com/documentation/unity/book-unity-gsg/) 操作，确保你的项目已准备好在 Oculus 上部署。</span><span class="sxs-lookup"><span data-stu-id="ce078-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="ce078-116">确保在你的设备上启用了 [开发人员模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。</span><span class="sxs-lookup"><span data-stu-id="ce078-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="ce078-117">安装 Oculus ADB 驱动程序是可选的。</span><span class="sxs-lookup"><span data-stu-id="ce078-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="ce078-118">设置用于 Oculus 的 XR SDK 管道</span><span class="sxs-lookup"><span data-stu-id="ce078-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="ce078-119">确保 **OCULUS XR 插件** 安装在 " **> 包管理器" 窗口** 中</span><span class="sxs-lookup"><span data-stu-id="ce078-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 插件包](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="ce078-121">转到 "**编辑 > 项目设置--> XR 插件" "> 插件提供程序**，确保项目中包含 Oculus 插件提供程序</span><span class="sxs-lookup"><span data-stu-id="ce078-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 插件提供程序](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="ce078-123">设置 Oculus Integration Unity 包以启用 handtracking</span><span class="sxs-lookup"><span data-stu-id="ce078-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="ce078-124">从 Unity 资产存储中下载并导入 [Oculus 集成](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。</span><span class="sxs-lookup"><span data-stu-id="ce078-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="ce078-125">已测试的最新版本为20.0.0。</span><span class="sxs-lookup"><span data-stu-id="ce078-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="ce078-126">可以从此 [存档](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到旧版本。</span><span class="sxs-lookup"><span data-stu-id="ce078-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="ce078-127">导航到混合现实工具包 > 实用程序 > Oculus > 集成 Oculus Integration Unity 模块。</span><span class="sxs-lookup"><span data-stu-id="ce078-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="ce078-128">执行此操作将更新 asmdefs，其中包含相关 Oculus 获取代码运行所需的定义和引用。</span><span class="sxs-lookup"><span data-stu-id="ce078-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="ce078-129">它还将更新 csc 文件，以筛选出 Oculus 集成资产生成的过时警告。</span><span class="sxs-lookup"><span data-stu-id="ce078-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="ce078-130">MRTK 存储库包含将警告转换为错误的 csc 文件，此转换会暂停 MRTK-Quest 配置过程。</span><span class="sxs-lookup"><span data-stu-id="ce078-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="ce078-132">在导入的 Oculus 文件夹中 (应在资产/Oculus) 中找到该文件夹，这是一个名为 OculusProjectConfig 的可编写脚本的对象。</span><span class="sxs-lookup"><span data-stu-id="ce078-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="ce078-133">在该配置文件中，需要将 HandTrackingSupport 设置为 "控制器和手"。</span><span class="sxs-lookup"><span data-stu-id="ce078-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus Integration 控制器和指针](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="ce078-135">设置场景</span><span class="sxs-lookup"><span data-stu-id="ce078-135">Setting up the scene</span></span>

1. <span data-ttu-id="ce078-136">创建新的 Unity 场景或打开预先存在的场景（如 HandInteractionExamples）。</span><span class="sxs-lookup"><span data-stu-id="ce078-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="ce078-137">通过导航到 **混合现实工具包**  >  **添加到场景并进行配置，** 将 MRTK 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="ce078-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="ce078-138">使用 Oculus XR SDK 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="ce078-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="ce078-139">将配置文件配置为使用 **OCULUS XR SDK 数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="ce078-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="ce078-140">如果不打算修改配置文件</span><span class="sxs-lookup"><span data-stu-id="ce078-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="ce078-141">使用所有默认的 MRTK 配置文件，这些配置文件都是跨 Unity 的 XR 管道配置的。</span><span class="sxs-lookup"><span data-stu-id="ce078-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="ce078-142">前面的 DefaultXRSDKConfigurationProfile 标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="ce078-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="ce078-143">请继续 [生成项目并将其部署到 Oculus](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="ce078-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="ce078-144">否则，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ce078-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="ce078-145">选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="ce078-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="ce078-147">选择 **输入** 配置文件。</span><span class="sxs-lookup"><span data-stu-id="ce078-147">Select the **Input** Configuration Profile.</span></span>

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="ce078-149">选择输入系统配置文件中的 " **克隆** " 以启用修改。</span><span class="sxs-lookup"><span data-stu-id="ce078-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="ce078-151">打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据提供程序** "，新的数据访问接口将添加到列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="ce078-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="ce078-152">打开新的数据提供程序并将 **类型** 设置为 **MixedReality。 Oculus > OculusXRSDKDeviceManager**。</span><span class="sxs-lookup"><span data-stu-id="ce078-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="ce078-154">将配置文件配置为使用 **OCULUS XR SDK 数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="ce078-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="ce078-155">如果不打算修改配置文件</span><span class="sxs-lookup"><span data-stu-id="ce078-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="ce078-156">将配置文件更改为 DefaultXRSDKConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="ce078-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="ce078-157">请继续 [生成项目并将其部署到 Oculus](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="ce078-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="ce078-158">否则，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ce078-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="ce078-159">选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="ce078-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![克隆配置文件](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="ce078-161">选择 **输入** 配置文件。</span><span class="sxs-lookup"><span data-stu-id="ce078-161">Select the **Input** Configuration Profile.</span></span>

        ![输入配置文件](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="ce078-163">选择输入系统配置文件中的 " **克隆** " 以启用修改。</span><span class="sxs-lookup"><span data-stu-id="ce078-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![克隆输入系统配置文件](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="ce078-165">打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据提供程序** "，新的数据访问接口将添加到列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="ce078-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="ce078-166">打开新的数据提供程序并将 **类型** 设置为 **MixedReality。 Oculus > OculusXRSDKDeviceManager**。</span><span class="sxs-lookup"><span data-stu-id="ce078-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 添加 XRSDK 数据提供程序](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="ce078-168">Oculus XR SDK 数据提供程序包括一个 OVR 相机远程处理 Prefab，它自动使用 OVR 相机 Rig 配置项目，并使用 OVR 来正确路由输入。</span><span class="sxs-lookup"><span data-stu-id="ce078-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="ce078-169">手动将 OVR 摄像装置添加到场景需要手动配置设置和输入。</span><span class="sxs-lookup"><span data-stu-id="ce078-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="ce078-170">生成项目并将其部署到 Oculus 的寻找</span><span class="sxs-lookup"><span data-stu-id="ce078-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="ce078-171">通过 USB 3.0 > USB C 线插入 Oculus 寻找</span><span class="sxs-lookup"><span data-stu-id="ce078-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="ce078-172">导航到 **文件 > 生成设置**</span><span class="sxs-lookup"><span data-stu-id="ce078-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="ce078-173">将部署更改为 **Android**</span><span class="sxs-lookup"><span data-stu-id="ce078-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="ce078-174">确保选择 "Oculus" 作为适用的运行设备</span><span class="sxs-lookup"><span data-stu-id="ce078-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 运行设备](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="ce078-176">选择生成并运行</span><span class="sxs-lookup"><span data-stu-id="ce078-176">Select Build and Run</span></span>
    - <span data-ttu-id="ce078-177">当您选择 " *生成" 并* 首次运行时，您可能会遇到以下生成错误集。</span><span class="sxs-lookup"><span data-stu-id="ce078-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="ce078-178">选择 " *生成" 并再次运行* 后，应该能够成功部署。</span><span class="sxs-lookup"><span data-stu-id="ce078-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 预期生成错误](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="ce078-180">接受来自接收内部的 " _允许 USB 调试_ " 提示</span><span class="sxs-lookup"><span data-stu-id="ce078-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="ce078-181">查看 Oculus 的内部场景</span><span class="sxs-lookup"><span data-stu-id="ce078-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="ce078-182">从项目中删除 Oculus 集成</span><span class="sxs-lookup"><span data-stu-id="ce078-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="ce078-183">导航到混合现实工具包 > Oculus > 单独的 Oculus 集成 Unity 模块  ![ Oculus 隔离 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="ce078-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="ce078-184">允许 Unity 刷新为 MixedReality 中的引用，并在此步骤中修改其他文件</span><span class="sxs-lookup"><span data-stu-id="ce078-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="ce078-185">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="ce078-185">Close Unity</span></span>
1. <span data-ttu-id="ce078-186">关闭 Visual Studio （如果它已打开）</span><span class="sxs-lookup"><span data-stu-id="ce078-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="ce078-187">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="ce078-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="ce078-188">删除 UnityProjectName/库目录</span><span class="sxs-lookup"><span data-stu-id="ce078-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="ce078-189">删除 UnityProjectName/资产/Oculus 目录</span><span class="sxs-lookup"><span data-stu-id="ce078-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="ce078-190">删除 UnityProjectName/资产/Oculus 文件</span><span class="sxs-lookup"><span data-stu-id="ce078-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="ce078-191">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="ce078-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="ce078-192">常见错误</span><span class="sxs-lookup"><span data-stu-id="ce078-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="ce078-193">Unity 无法识别的寻找</span><span class="sxs-lookup"><span data-stu-id="ce078-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="ce078-194">请确保正确配置了 Android 路径。</span><span class="sxs-lookup"><span data-stu-id="ce078-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="ce078-195">如果继续遇到问题，请遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="ce078-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="ce078-196">**> 外部工具 > Android 编辑 > 首选项**</span><span class="sxs-lookup"><span data-stu-id="ce078-196">**Edit > Preferences > External Tools > Android**</span></span>

![Android 工具配置](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
