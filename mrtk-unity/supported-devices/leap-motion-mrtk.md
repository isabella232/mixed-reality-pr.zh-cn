---
title: 使用 Leap Motion
description: 为 Leap 运动配置的文档
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，Leap 运动，
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176517"
---
# <a name="using-leap-motion"></a><span data-ttu-id="dc3cb-104">使用 Leap Motion</span><span class="sxs-lookup"><span data-stu-id="dc3cb-104">Using Leap Motion</span></span>

<span data-ttu-id="dc3cb-105">需要使用 [Leap 运动控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="dc3cb-106">Leap 运动数据提供程序支持用于 VR 的有表述的手动跟踪，可用于在编辑器中快速制作原型。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="dc3cb-107">可以将数据访问接口配置为使用耳机上装入的 Leap 运动控制器，或将其放置在桌面面上。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="dc3cb-109">在独立平台上，可以在编辑器和设备上使用此提供程序。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="dc3cb-110">它还可用于在 UWP 平台而不是 UWP 版本中的编辑器中。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="dc3cb-111">MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="dc3cb-111">MRTK Version</span></span> | <span data-ttu-id="dc3cb-112">支持 Leap 运动 Unity 模块版本</span><span class="sxs-lookup"><span data-stu-id="dc3cb-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="dc3cb-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="dc3cb-113">2.6.x</span></span> | <span data-ttu-id="dc3cb-114">4.5.0，4.5。1</span><span class="sxs-lookup"><span data-stu-id="dc3cb-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="dc3cb-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="dc3cb-115">2.7.x</span></span>| <span data-ttu-id="dc3cb-116">4.5.0、4.5.1、4.6.0、4.7.0、4.7.1、4.8。0</span><span class="sxs-lookup"><span data-stu-id="dc3cb-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="dc3cb-117">在 MRTK 中使用 Ultraleap) 手动跟踪的 Leap 运动 (</span><span class="sxs-lookup"><span data-stu-id="dc3cb-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="dc3cb-118">导入 MRTK 和 Leap 运动 Unity 模块</span><span class="sxs-lookup"><span data-stu-id="dc3cb-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="dc3cb-119">安装最新的 [Leap 运动 SDK](https://developer.leapmotion.com/releases/?category=orion) （如果尚未安装）</span><span class="sxs-lookup"><span data-stu-id="dc3cb-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="dc3cb-120">导入 **MixedReality Toolkit。Foundation** 打包到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="dc3cb-121">下载最新版本的 [Leap 运动 Unity 模块](https://developer.leapmotion.com/unity) 并将其导入到项目中</span><span class="sxs-lookup"><span data-stu-id="dc3cb-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="dc3cb-122">仅导入 Unity 模块内的 **核心** 包</span><span class="sxs-lookup"><span data-stu-id="dc3cb-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="dc3cb-123">将 Leap 运动 Unity 模块与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="dc3cb-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="dc3cb-124">在 Unity 模块位于项目中后，导航到 **混合现实 Toolkit**  >  **leap 运动**  >  **集成 Leap 运动 Unity 模块**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="dc3cb-125">将 Unity 模块集成到 MRTK 会将10个程序集定义添加到项目，并添加对 Toolkit MixedReality 的引用。 **LeapMotion** 程序集定义。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="dc3cb-126">确保已关闭 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="dc3cb-128">添加 Leap 运动数据提供程序</span><span class="sxs-lookup"><span data-stu-id="dc3cb-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="dc3cb-129">创建新的 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="dc3cb-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="dc3cb-130">通过导航到 **混合现实 Toolkit** 添加到场景  >  **，并配置**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="dc3cb-131">选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="dc3cb-133">选择 **输入** 配置文件</span><span class="sxs-lookup"><span data-stu-id="dc3cb-133">Select the **Input** Configuration Profile</span></span>

    ![输入配置文件1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="dc3cb-135">选择输入系统配置文件中的 " **克隆** " 以启用修改。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="dc3cb-137">打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据访问接口** "，将在列表的末尾添加一个新的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="dc3cb-138">打开新的数据提供程序并将 **类型** 设置为 " **Toolkit MixedReality"。LeapMotion > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap 添加数据提供程序](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="dc3cb-140">选择 " **克隆** " 以更改默认的 Leap 运动设置。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="dc3cb-142">Leap 运动数据提供程序包含属性，该 `LeapControllerOrientation` 属性是 Leap 运动控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="dc3cb-143">`LeapControllerOrientation.Headset` 指示控制器已装入耳机。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="dc3cb-144">`LeapControllerOrientation.Desk` 指示控制器位于桌面上。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="dc3cb-145">默认值设置为 `LeapControllerOrientation.Headset` 。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="dc3cb-146">每个控制器方向都包含偏移属性：</span><span class="sxs-lookup"><span data-stu-id="dc3cb-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="dc3cb-147">**头戴** 显示在 LeapXRServiceProvider 组件中的偏移属性的位置。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="dc3cb-148">`LeapVRDeviceOffsetMode`有三个选项：默认值、手动头偏移和转换。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="dc3cb-149">如果偏移模式为默认值，则不会对 Leap 运动控制器应用偏移量。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="dc3cb-150">手动 Head 偏移模式允许修改三个属性： `LeapVRDeviceOffsetY` 、 `LeapVRDeviceOffsetZ` 和 `LeapVRDeviceTiltX` 。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="dc3cb-151">然后，"轴偏移量" 属性值将应用到默认控制器位置。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="dc3cb-152">转换偏移模式包含 `LeapVRDeviceOrigin` 转换属性，该属性指定 Leap 运动控制器的新原点。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="dc3cb-153">**桌面** 方向包含 `LeapControllerOffset` 用于定义桌面 leap 定位位置的属性。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="dc3cb-154">偏移量是相对于摄像机的主位置计算的，默认值为 (0，-0.2，0.35) ，以确保指针显示在相机的正面和下方。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="dc3cb-155">当应用程序启动时，会应用配置文件中的偏移量属性。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="dc3cb-156">若要在运行时中修改这些值，请从 Leap 运动 Device Manager 获取 Leap 运动服务提供程序：</span><span class="sxs-lookup"><span data-stu-id="dc3cb-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="dc3cb-157">`EnterPinchDistance` 和 `ExitPinchDistance` 是用于挤压/空中攻攻的距离阈值检测。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="dc3cb-158">通过测量食指笔尖和 thumb 笔尖之间的距离来计算挤压手势。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="dc3cb-159">若要引发输入关闭事件，则默认值 `EnterPinchDistance` 设置为0.02。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="dc3cb-160">若要在 (退出 "挤压") 时引发输入事件，请使用0.05 的默认距离。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="dc3cb-161">`LeapControllerOrientation`：耳机 (默认值) </span><span class="sxs-lookup"><span data-stu-id="dc3cb-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="dc3cb-162">`LeapControllerOrientation`：书桌</span><span class="sxs-lookup"><span data-stu-id="dc3cb-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="dc3cb-167">测试 Leap 运动数据提供程序</span><span class="sxs-lookup"><span data-stu-id="dc3cb-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="dc3cb-168">在将 Leap 运动数据提供程序添加到输入系统配置文件后，按 "播放"，将你的手移动到 Leap 运动控制器的前方，你应该会看到手的接合表示形式。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="dc3cb-169">生成项目</span><span class="sxs-lookup"><span data-stu-id="dc3cb-169">Building your project</span></span>
    - <span data-ttu-id="dc3cb-170">导航到 **文件 > 生成设置**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="dc3cb-171">如果使用 Leap 运动数据提供程序，则仅支持独立生成。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="dc3cb-172">有关如何使用 Windows Mixed Reality 耳机来实现独立版本的说明，请参阅[构建和部署 MRTK 到 WMR 耳机 (独立) ](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="dc3cb-173">获取手型</span><span class="sxs-lookup"><span data-stu-id="dc3cb-173">Getting the hand joints</span></span>

<span data-ttu-id="dc3cb-174">使用 Leap 运动数据提供程序的联系，与 MRTK 的有无表述的手的联合检索相同。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="dc3cb-175">有关详细信息，请参阅 [手动跟踪](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="dc3cb-176">使用 unity 场景中的 MRTK 和在输入系统配置文件中添加为输入数据提供程序的 Leap 运动数据提供程序时，请创建一个空游戏对象并附加以下示例脚本。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="dc3cb-177">此脚本是一个简单的示例，说明如何在 Leap 运动手中检索手掌接点的姿势。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="dc3cb-178">当多维数据集遵循适当的 Leap 时，球会跟随左侧的 Leap。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="dc3cb-179">Unity 编辑器工作流提示</span><span class="sxs-lookup"><span data-stu-id="dc3cb-179">Unity editor workflow tip</span></span>

<span data-ttu-id="dc3cb-180">使用 Leap 运动数据提供程序不需要 VR 耳机。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="dc3cb-181">无需耳机即可在编辑器中测试对 MRTK 应用的更改。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="dc3cb-182">闰运动将显示在编辑器中，并且不会插入 VR 耳机。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="dc3cb-183">如果 `LeapControllerOrientation` 设置为 **头戴式耳机**，则需要将 Leap 运动控制器向上保持一只手。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="dc3cb-184">如果使用 WASD 中的 "键" 来移动照相机并且 `LeapControllerOrientation` 为 " **耳机**"，则不会跟随摄像机。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="dc3cb-185">如果在 `LeapControllerOrientation` 设置了 **耳机** 时插入了 VR 耳机，则只会跟随摄像机运动。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="dc3cb-186">如果设置为 "桌面"，则在编辑器中，Leap 会按照相机的移动进行操作 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="dc3cb-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="dc3cb-187">从 Project 中移除 Leap 运动</span><span class="sxs-lookup"><span data-stu-id="dc3cb-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="dc3cb-188">导航到 **混合现实 Toolkit**  >  **leap**  >  **单独的 leap 移动**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="dc3cb-189">让 Unity 刷新为 Toolkit MixedReality 中的引用。 **LeapMotion. asmdef** 文件在此步骤中进行了修改</span><span class="sxs-lookup"><span data-stu-id="dc3cb-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="dc3cb-190">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="dc3cb-190">Close Unity</span></span>
1. <span data-ttu-id="dc3cb-191">关闭 Visual Studio （如果它已打开）</span><span class="sxs-lookup"><span data-stu-id="dc3cb-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="dc3cb-192">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="dc3cb-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="dc3cb-193">删除 **UnityProjectName/库** 目录</span><span class="sxs-lookup"><span data-stu-id="dc3cb-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="dc3cb-194">删除 **UnityProjectName/资产/插件/LeapMotion** 目录</span><span class="sxs-lookup"><span data-stu-id="dc3cb-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="dc3cb-195">删除 **UnityProjectName/资产/插件/LeapMotion** 文件</span><span class="sxs-lookup"><span data-stu-id="dc3cb-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="dc3cb-196">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="dc3cb-196">Reopen Unity</span></span>

<span data-ttu-id="dc3cb-197">在 Unity 2018.4 中，你可能会注意到，在删除库和 Leap 运动核心资产后，错误仍然保留在控制台中。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="dc3cb-198">如果重新打开后记录错误，请重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="dc3cb-199">常见错误</span><span class="sxs-lookup"><span data-stu-id="dc3cb-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="dc3cb-200">Leap 运动尚未与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="dc3cb-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="dc3cb-201">测试 Leap 运动 Unity 模块是否与 MRTK 集成：</span><span class="sxs-lookup"><span data-stu-id="dc3cb-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="dc3cb-202">导航到 **混合现实 Toolkit > 实用工具 > Leap 运动 > 检查集成状态**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="dc3cb-203">此时将显示一个弹出窗口，其中包含有关 Leap 运动 Unity 模块是否与 MRTK 集成的消息。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="dc3cb-204">如果消息指出尚未集成资产：</span><span class="sxs-lookup"><span data-stu-id="dc3cb-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="dc3cb-205">请确保 Leap 运动 Unity 模块在项目中</span><span class="sxs-lookup"><span data-stu-id="dc3cb-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="dc3cb-206">请确保所添加的版本受支持，请参阅页面顶部的表中支持的版本。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="dc3cb-207">尝试将 **混合现实 Toolkit > 实用工具 > leap 运动 > 集成 leap 运动 Unity 模块**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="dc3cb-208">复制程序集多人 HLAPI 失败</span><span class="sxs-lookup"><span data-stu-id="dc3cb-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="dc3cb-209">导入 Leap 运动 Unity 核心资产时，可能会记录此错误：</span><span class="sxs-lookup"><span data-stu-id="dc3cb-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="dc3cb-210">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="dc3cb-210">**Solution**</span></span>

- <span data-ttu-id="dc3cb-211">短期解决方案是重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="dc3cb-212">有关详细信息，请参阅 [问题 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="dc3cb-213">Leap 运动示例场景</span><span class="sxs-lookup"><span data-stu-id="dc3cb-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="dc3cb-214">示例场景使用 DefaultLeapMotionConfiguration 配置文件，并确定是否已正确配置 Unity 项目以使用 Leap 运动数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="dc3cb-215">示例场景包含在 **Toolkit MixedReality 中。** **MRTK/示例/演示程序/HandTracking/** 目录中的示例包。</span><span class="sxs-lookup"><span data-stu-id="dc3cb-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="dc3cb-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc3cb-216">See also</span></span>

- [<span data-ttu-id="dc3cb-217">输入提供者</span><span class="sxs-lookup"><span data-stu-id="dc3cb-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="dc3cb-218">手动跟踪</span><span class="sxs-lookup"><span data-stu-id="dc3cb-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
