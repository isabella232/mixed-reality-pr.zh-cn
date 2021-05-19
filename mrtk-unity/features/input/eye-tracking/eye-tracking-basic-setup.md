---
title: 眼动跟踪基本设置
description: 如何在 MRTK 中设置眼动跟踪
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 眼动跟踪，
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144093"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="190ba-104">MRTK 中的眼动跟踪入门</span><span class="sxs-lookup"><span data-stu-id="190ba-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="190ba-105">本页介绍如何设置 Unity MRTK 场景，以在应用中使用眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="190ba-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="190ba-106">以下假设你从全新的场景开始。</span><span class="sxs-lookup"><span data-stu-id="190ba-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="190ba-107">或者，你可以查看我们已配置的 [MRTK](../../example-scenes/eye-tracking-examples-overview.md) 眼动跟踪示例，以及可以直接构建的众多出色的示例。</span><span class="sxs-lookup"><span data-stu-id="190ba-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="190ba-108">眼动跟踪要求清单</span><span class="sxs-lookup"><span data-stu-id="190ba-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="190ba-109">若要正常进行眼动跟踪，必须满足以下要求。</span><span class="sxs-lookup"><span data-stu-id="190ba-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="190ba-110">如果你对眼动跟踪HoloLens 2 MRTK 中设置眼动跟踪，请不要担心！</span><span class="sxs-lookup"><span data-stu-id="190ba-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="190ba-111">下面将详细介绍如何进一步解决每个问题。</span><span class="sxs-lookup"><span data-stu-id="190ba-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="190ba-112">必须将 _"眼睛凝视_ 数据提供程序"添加到输入系统。</span><span class="sxs-lookup"><span data-stu-id="190ba-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="190ba-113">这会从平台提供眼动跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="190ba-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="190ba-114">必须在 _应用程序清单中启用"GazeInput"_ 功能。</span><span class="sxs-lookup"><span data-stu-id="190ba-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="190ba-115">**此功能可以在 Unity 2019 中设置，但在 Unity 2018 及更早的 Unity 中，此功能仅在 Visual Studio 和 MRTK 生成工具中可用**</span><span class="sxs-lookup"><span data-stu-id="190ba-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="190ba-116">必须为当前 **用户** 校准 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="190ba-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="190ba-117">请查看我们 [的示例，以检测用户是否进行了眼部校准](eye-tracking-is-user-calibrated.md)。</span><span class="sxs-lookup"><span data-stu-id="190ba-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="190ba-118">有关 GazeInput 功能说明</span><span class="sxs-lookup"><span data-stu-id="190ba-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="190ba-119">MRTK 提供的生成工具 (即混合现实工具包 -> 实用工具 -> 生成窗口) 可自动启用 GazeInput 功能。</span><span class="sxs-lookup"><span data-stu-id="190ba-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="190ba-120">为此，需要确保在"Appx 生成选项"选项卡上选中"凝视输入功能"：</span><span class="sxs-lookup"><span data-stu-id="190ba-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![MRTK 生成工具](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="190ba-122">此工具将在 Unity 生成完成后找到 AppX 清单，并手动添加 GazeInput 功能。</span><span class="sxs-lookup"><span data-stu-id="190ba-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="190ba-123">**在 unity 2019 之前，在使用 unity 的内置生成窗口时，此工具不会处于活动状态，** (即 > 生成设置) 。</span><span class="sxs-lookup"><span data-stu-id="190ba-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="190ba-124">在 Unity 2019 之前，使用 Unity 的生成窗口时，需要在 Unity 生成后手动添加功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="190ba-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="190ba-125">打开已编译的 Visual Studio 项目，然后在解决方案中打开 _"appxmanifest.xml"_ 。</span><span class="sxs-lookup"><span data-stu-id="190ba-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="190ba-126">请确保在 "_功能_" 下勾选 _"GazeInput"_ 复选框。</span><span class="sxs-lookup"><span data-stu-id="190ba-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="190ba-127">如果看不到 _"GazeInput"_ 功能，请检查系统是否满足 (使用 Windows SDK 版本) 的 [先决条件](/windows/mixed-reality/develop/install-the-tools) 。</span><span class="sxs-lookup"><span data-stu-id="190ba-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="190ba-128">_请注意：_ 仅当生成到新的生成文件夹时，才需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="190ba-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="190ba-129">这意味着，如果你已经生成了 Unity 项目并在 appxmanifest.xml 之前设置了该文件，则不需要重新应用所做的更改。</span><span class="sxs-lookup"><span data-stu-id="190ba-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="190ba-130">逐步设置目视跟踪</span><span class="sxs-lookup"><span data-stu-id="190ba-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="190ba-131">设置场景</span><span class="sxs-lookup"><span data-stu-id="190ba-131">Setting up the scene</span></span>

<span data-ttu-id="190ba-132">只需单击 _"混合现实工具包-> 配置 ..."_ 即可设置 _MixedRealityToolkit_</span><span class="sxs-lookup"><span data-stu-id="190ba-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="190ba-133">在菜单栏中。</span><span class="sxs-lookup"><span data-stu-id="190ba-133">in the menu bar.</span></span>

![MRTK 配置](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="190ba-135">设置目视跟踪所需的 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="190ba-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="190ba-136">设置 MRTK 场景后，将要求你选择 MRTK 的配置文件。</span><span class="sxs-lookup"><span data-stu-id="190ba-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="190ba-137">只需选择 " _DefaultMixedRealityToolkitConfigurationProfile_ "，然后选择 _"复制 & 自定义"_ 选项。</span><span class="sxs-lookup"><span data-stu-id="190ba-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![MRTK 配置文件](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="190ba-139">创建 "眼睛数据提供程序"</span><span class="sxs-lookup"><span data-stu-id="190ba-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="190ba-140">在 MRTK 配置文件中单击 _"输入"_ 选项卡。</span><span class="sxs-lookup"><span data-stu-id="190ba-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="190ba-141">若要编辑 ( _"DefaultMixedRealityInputSystemProfile"_ ) 的默认值，请单击其旁边的 _"克隆"_ 按钮。</span><span class="sxs-lookup"><span data-stu-id="190ba-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="190ba-142">将显示 _"克隆配置文件"_ 菜单。</span><span class="sxs-lookup"><span data-stu-id="190ba-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="190ba-143">只需单击 _该菜单底部的_ "克隆"即可。</span><span class="sxs-lookup"><span data-stu-id="190ba-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="190ba-144">双击新的输入配置文件，展开 _"输入数据提供程序"，_ 然后选择 _"+ 添加数据提供程序"。_</span><span class="sxs-lookup"><span data-stu-id="190ba-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="190ba-145">创建新的数据访问接口：</span><span class="sxs-lookup"><span data-stu-id="190ba-145">Create a new data provider:</span></span>
  - <span data-ttu-id="190ba-146">在 **"类型**"下，选择 _"Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input""WindowsMixedRealityEyeGazeDataProvider"_  ->  </span><span class="sxs-lookup"><span data-stu-id="190ba-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="190ba-147">对于 **"平台 (")** 选择 _"Windows 通用"。_</span><span class="sxs-lookup"><span data-stu-id="190ba-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![MRTK 数据提供程序](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="190ba-149">在 Unity 编辑器中模拟眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="190ba-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="190ba-150">可以在 Unity 编辑器中模拟眼动跟踪输入，确保在将应用部署到应用之前正确触发HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="190ba-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="190ba-151">只需将相机的位置用作眼睛凝视原点，将相机的向前矢量用作眼睛凝视方向，来模拟眼睛凝视信号。</span><span class="sxs-lookup"><span data-stu-id="190ba-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="190ba-152">虽然这非常适用于初始测试，但请注意，它并不是快速眼部运动的良好选择。</span><span class="sxs-lookup"><span data-stu-id="190ba-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="190ba-153">为此，最好确保对基于眼睛的交互进行频繁的测试，HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="190ba-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="190ba-154">**启用模拟眼动跟踪**：</span><span class="sxs-lookup"><span data-stu-id="190ba-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="190ba-155">单击 MRTK _配置文件中的_ "输入"选项卡。</span><span class="sxs-lookup"><span data-stu-id="190ba-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="190ba-156">从该页导航 _到"输入数据提供程序_  ->  _""输入模拟服务"。_</span><span class="sxs-lookup"><span data-stu-id="190ba-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="190ba-157">克隆 _"DefaultMixedRealityInputSimpulationProfile"_ 以进行更改。</span><span class="sxs-lookup"><span data-stu-id="190ba-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="190ba-158">选中" _模拟眼睛位置"_ 复选框。</span><span class="sxs-lookup"><span data-stu-id="190ba-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK 眼睛模拟](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="190ba-160">**禁用默认头部凝** 视光标：一般情况下，建议避免显示眼睛凝视光标，或者绝对需要使其非常 _细微_ 。</span><span class="sxs-lookup"><span data-stu-id="190ba-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="190ba-161">建议默认隐藏附加到 MRTK 凝视指针配置文件的默认头部凝视光标。</span><span class="sxs-lookup"><span data-stu-id="190ba-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="190ba-162">导航到 MRTK 配置文件 > _"输入"_  ->  _"指针"_</span><span class="sxs-lookup"><span data-stu-id="190ba-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="190ba-163">克隆 _"DefaultMixedRealityInputPointerProfile"_ 以对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="190ba-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="190ba-164">在 _"指针设置"_ 的顶部，应将不可见的光标 prefab 分配给 _"GazeCursor"_。</span><span class="sxs-lookup"><span data-stu-id="190ba-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="190ba-165">为此，可以从 MRTK Foundation 中选择 _"EyeGazeCursor"_ prefab。</span><span class="sxs-lookup"><span data-stu-id="190ba-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="190ba-166">在注视提供商中启用基于眼睛的注视</span><span class="sxs-lookup"><span data-stu-id="190ba-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="190ba-167">在 HoloLens v1 中，打印头用作主指针技术。</span><span class="sxs-lookup"><span data-stu-id="190ba-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="190ba-168">尽管仍可通过附加到 [相机](https://docs.unity3d.com/ScriptReference/Camera.html)的 MRTK 中的 _GazeProvider_ 来使用打印头，但你可以通过勾选输入指针配置文件的 "注视" 设置中的 _"IsEyeTrackingEnabled"_ 复选框来进行检查。</span><span class="sxs-lookup"><span data-stu-id="190ba-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="190ba-169">通过更改 _"GazeProvider"_ 的 _"IsEyeTrackingEnabled"_ 属性，开发人员可以在代码中切换基于眼睛的眼睛和头。</span><span class="sxs-lookup"><span data-stu-id="190ba-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="190ba-170">如果未满足任何目视跟踪要求，应用程序将自动回退到基于头部的注视。</span><span class="sxs-lookup"><span data-stu-id="190ba-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="190ba-171">访问目视数据</span><span class="sxs-lookup"><span data-stu-id="190ba-171">Accessing eye gaze data</span></span>

<span data-ttu-id="190ba-172">现在，你的场景已设置为使用目视跟踪，接下来让我们看看如何在脚本中访问它： [通过 EyeGazeProvider 访问目视跟踪数据](eye-tracking-eye-gaze-provider.md) 和 [目视支持的目标选择](eye-tracking-target-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="190ba-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="190ba-173">在 HoloLens 2 上测试 Unity 应用</span><span class="sxs-lookup"><span data-stu-id="190ba-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="190ba-174">用目视跟踪生成应用应类似于编译其他 HoloLens 2 MRTK 应用的方式。</span><span class="sxs-lookup"><span data-stu-id="190ba-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="190ba-175">请确保已启用 *"注视输入"* 功能，如上文中的 [*GazeInput 功能说明*](#a-note-on-the-gazeinput-capability)部分所述。</span><span class="sxs-lookup"><span data-stu-id="190ba-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="190ba-176">目视校准</span><span class="sxs-lookup"><span data-stu-id="190ba-176">Eye calibration</span></span>

<span data-ttu-id="190ba-177">最后，请不要忘记在 HoloLens 2 上通过目视校准来运行。</span><span class="sxs-lookup"><span data-stu-id="190ba-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="190ba-178">如果没有校准用户，则眼睛跟踪系统不会返回任何输入。</span><span class="sxs-lookup"><span data-stu-id="190ba-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="190ba-179">获取校准的最简单方法是向上翻转面板并向下移动。</span><span class="sxs-lookup"><span data-stu-id="190ba-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="190ba-180">系统通知应显示欢迎你作为新用户，并要求你完成眼睛校准。</span><span class="sxs-lookup"><span data-stu-id="190ba-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="190ba-181">此外，还可以在 "系统设置"： "设置" > 系统 > 校准 "中找到眼睛校准，> 运行目视校准。</span><span class="sxs-lookup"><span data-stu-id="190ba-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="190ba-182">目视跟踪权限</span><span class="sxs-lookup"><span data-stu-id="190ba-182">Eye tracking permission</span></span>

<span data-ttu-id="190ba-183">首次在 HoloLens 2 上启动应用时，会弹出提示，要求用户提供使用目视跟踪的权限。</span><span class="sxs-lookup"><span data-stu-id="190ba-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="190ba-184">如果未显示，则这通常表示未设置 _"GazeInput"_ 功能。</span><span class="sxs-lookup"><span data-stu-id="190ba-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="190ba-185">权限提示出现一次后，就不会再次显示。</span><span class="sxs-lookup"><span data-stu-id="190ba-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="190ba-186">如果 _"拒绝了目视跟踪权限"_，则可以在设置-> 隐私-> 应用中对此进行重置。</span><span class="sxs-lookup"><span data-stu-id="190ba-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="190ba-187">这会使你开始在 MRTK Unity 应用中使用目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="190ba-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="190ba-188">别忘了查看 [我们的 MRTK 眼跟踪教程和示例，](../../example-scenes/eye-tracking-examples-overview.md) 演示如何使用目视跟踪输入并方便地提供可在项目中重复使用的脚本。</span><span class="sxs-lookup"><span data-stu-id="190ba-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="190ba-189">返回 "MixedRealityToolkit" 中的眼睛跟踪</span><span class="sxs-lookup"><span data-stu-id="190ba-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)