---
title: 跳跃运动 MRTK
description: 为 Leap Motion 配置的文档
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Leap Motion，
ms.openlocfilehash: 8ef5d26512d50a93691932789e84c099c6246bc3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543233"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="31dfd-104">如何在 MRTK 中配置 Ultraleap (Leap Motion) 手动跟踪</span><span class="sxs-lookup"><span data-stu-id="31dfd-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="31dfd-105">[使用此数据访问接口](https://www.ultraleap.com/product/leap-motion-controller/)需要 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="31dfd-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="31dfd-106">Leap Motion 数据提供程序支持 VR 的明确手部跟踪，并且可用于在编辑器中快速原型制作。</span><span class="sxs-lookup"><span data-stu-id="31dfd-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="31dfd-107">可以将数据访问接口配置为使用安装在头戴显示设备上或放在桌面人脸上的 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="31dfd-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="31dfd-109">在独立平台上，此提供程序可在编辑器和设备上使用。</span><span class="sxs-lookup"><span data-stu-id="31dfd-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="31dfd-110">它还可以在 UWP 平台上的编辑器中使用，但不能在 UWP 生成中使用。</span><span class="sxs-lookup"><span data-stu-id="31dfd-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="31dfd-111">MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="31dfd-111">MRTK Version</span></span> | <span data-ttu-id="31dfd-112">支持 Leap Motion Unity 模块版本</span><span class="sxs-lookup"><span data-stu-id="31dfd-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="31dfd-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="31dfd-113">2.6.x</span></span> | <span data-ttu-id="31dfd-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="31dfd-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="31dfd-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="31dfd-115">2.7.x</span></span>| <span data-ttu-id="31dfd-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="31dfd-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="31dfd-117">使用 Ultraleap (Leap Motion) MRTK 中的手动跟踪</span><span class="sxs-lookup"><span data-stu-id="31dfd-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="31dfd-118">导入 MRTK 和 Leap Motion Unity 模块</span><span class="sxs-lookup"><span data-stu-id="31dfd-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="31dfd-119">安装最新的 [Leap Motion SDK（](https://developer.leapmotion.com/releases/?category=orion) 如果尚未安装）</span><span class="sxs-lookup"><span data-stu-id="31dfd-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="31dfd-120">将 **Microsoft.MixedReality.Toolkit.Foundation** 包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="31dfd-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="31dfd-121">下载最新版本的 Leap Motion [Unity 模块并导入](https://developer.leapmotion.com/unity) 到项目中</span><span class="sxs-lookup"><span data-stu-id="31dfd-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="31dfd-122">仅导入 **Unity** 模块中的 Core 包</span><span class="sxs-lookup"><span data-stu-id="31dfd-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="31dfd-123">将 Leap Motion Unity 模块与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="31dfd-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="31dfd-124">Unity 模块进入项目后，导航到"混合 **现实工具包**  >  **""Leap Motion**  >  **集成 Leap Motion Unity 模块"**</span><span class="sxs-lookup"><span data-stu-id="31dfd-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="31dfd-125">将 Unity 模块集成到 MRTK 会向项目添加 10 个程序集定义，并添加 **对 Microsoft.MixedReality.Toolkit.Providers.LeapMotion** 程序集定义的引用。</span><span class="sxs-lookup"><span data-stu-id="31dfd-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="31dfd-126">确保已关闭 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="31dfd-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="31dfd-128">添加 Leap Motion 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="31dfd-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="31dfd-129">创建新的 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="31dfd-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="31dfd-130">导航到"混合现实工具包""添加到场景并配置"，将 MRTK  >  **添加到场景**</span><span class="sxs-lookup"><span data-stu-id="31dfd-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="31dfd-131">选择层次结构中的 MixedRealityToolkit 游戏对象，然后选择"复制和自定义"以克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="31dfd-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="31dfd-133">选择 **输入** 配置文件</span><span class="sxs-lookup"><span data-stu-id="31dfd-133">Select the **Input** Configuration Profile</span></span>

    ![输入配置文件 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="31dfd-135">在 **输入** 系统配置文件中选择"克隆"以启用修改。</span><span class="sxs-lookup"><span data-stu-id="31dfd-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="31dfd-137">打开"**输入数据提供程序"** 部分，选择顶部的"添加数据提供程序"，将在列表末尾添加新的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="31dfd-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="31dfd-138">打开新的数据访问接口，将"类型"设置为 **"Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager"**</span><span class="sxs-lookup"><span data-stu-id="31dfd-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap 添加数据提供程序](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="31dfd-140">选择 **"克隆** "以更改默认的 Leap Motion 设置。</span><span class="sxs-lookup"><span data-stu-id="31dfd-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="31dfd-142">Leap Motion 数据提供程序包含 `LeapControllerOrientation` 属性，该属性是 Leap Motion 控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="31dfd-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="31dfd-143">`LeapControllerOrientation.Headset` 指示控制器已装载在头戴显示设备上。</span><span class="sxs-lookup"><span data-stu-id="31dfd-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="31dfd-144">`LeapControllerOrientation.Desk` 指示控制器在桌面上平面放置。</span><span class="sxs-lookup"><span data-stu-id="31dfd-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="31dfd-145">默认值设置为 `LeapControllerOrientation.Headset` 。</span><span class="sxs-lookup"><span data-stu-id="31dfd-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="31dfd-146">每个控制器方向都包含偏移量属性：</span><span class="sxs-lookup"><span data-stu-id="31dfd-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="31dfd-147">头 **戴** 显示设备方向偏移属性镜像 LeapXRServiceProvider 组件中的偏移属性。</span><span class="sxs-lookup"><span data-stu-id="31dfd-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="31dfd-148">有 `LeapVRDeviceOffsetMode` 三个选项："默认"、"手动头部偏移"和"转换"。</span><span class="sxs-lookup"><span data-stu-id="31dfd-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="31dfd-149">如果偏移模式为 Default，则偏移量将不会应用于 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="31dfd-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="31dfd-150">手动头部偏移模式允许修改三个属性： 和 `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` 。</span><span class="sxs-lookup"><span data-stu-id="31dfd-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="31dfd-151">然后，轴偏移属性值将应用于默认控制器位置。</span><span class="sxs-lookup"><span data-stu-id="31dfd-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="31dfd-152">转换偏移模式包含 `LeapVRDeviceOrigin` Transform 属性，该属性指定 Leap Motion 控制器的新原点。</span><span class="sxs-lookup"><span data-stu-id="31dfd-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="31dfd-153">桌面 **方向** 包含 `LeapControllerOffset` 属性，该属性定义桌面闰手的定位点位置。</span><span class="sxs-lookup"><span data-stu-id="31dfd-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="31dfd-154">偏移量相对于主相机位置进行计算，默认值为 (0、-0.2、0.35) 以确保手出现在相机的前面和视图中。</span><span class="sxs-lookup"><span data-stu-id="31dfd-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="31dfd-155">应用程序启动时，将应用配置文件中的偏移属性一次。</span><span class="sxs-lookup"><span data-stu-id="31dfd-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="31dfd-156">若要在运行时修改值，请从 Leap Motion 提供程序获取 Leap Motion 设备管理器：</span><span class="sxs-lookup"><span data-stu-id="31dfd-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="31dfd-157">`EnterPinchDistance``ExitPinchDistance`和 是收缩/敲击手势检测的距离阈值。</span><span class="sxs-lookup"><span data-stu-id="31dfd-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="31dfd-158">收缩手势是通过测量索引指尖和拇指尖之间的距离计算的。</span><span class="sxs-lookup"><span data-stu-id="31dfd-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="31dfd-159">若要在输入关闭事件时引发 ，默认值 `EnterPinchDistance` 设置为 0.02。</span><span class="sxs-lookup"><span data-stu-id="31dfd-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="31dfd-160">若要在退出收缩 (时引发输入 up 事件，) 指提示和指纹提示之间的默认距离为 0.05。</span><span class="sxs-lookup"><span data-stu-id="31dfd-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="31dfd-161">`LeapControllerOrientation`：头戴显示 (默认) </span><span class="sxs-lookup"><span data-stu-id="31dfd-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="31dfd-162">`LeapControllerOrientation`：服务台</span><span class="sxs-lookup"><span data-stu-id="31dfd-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="31dfd-167">测试 Leap Motion 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="31dfd-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="31dfd-168">将 Leap Motion 数据提供程序添加到输入系统配置文件后，按"播放"，将手移到 Leap Motion 控制器的前面，应会看到手的联合表示形式。</span><span class="sxs-lookup"><span data-stu-id="31dfd-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="31dfd-169">生成项目</span><span class="sxs-lookup"><span data-stu-id="31dfd-169">Building your project</span></span>
    - <span data-ttu-id="31dfd-170">导航到 **"文件>生成设置"**</span><span class="sxs-lookup"><span data-stu-id="31dfd-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="31dfd-171">如果使用 Leap Motion 数据提供程序，则仅支持独立生成。</span><span class="sxs-lookup"><span data-stu-id="31dfd-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="31dfd-172">有关如何使用独立版本Windows Mixed Reality头戴显示设备的说明，请参阅生成 MRTK 并部署到独立 ([WMR 头戴显示) 。 ](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)</span><span class="sxs-lookup"><span data-stu-id="31dfd-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="31dfd-173">获取手部</span><span class="sxs-lookup"><span data-stu-id="31dfd-173">Getting the hand joints</span></span>

<span data-ttu-id="31dfd-174">使用 Leap Motion 数据提供程序获取联合与 MRTK 表达手部手动联合检索相同。</span><span class="sxs-lookup"><span data-stu-id="31dfd-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="31dfd-175">有关详细信息，请参阅 [手部跟踪](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)。</span><span class="sxs-lookup"><span data-stu-id="31dfd-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="31dfd-176">在 Unity 场景中使用 MRTK，并将 Leap Motion 数据提供程序添加为输入系统配置文件中的输入数据提供程序，创建一个空游戏对象并附加以下示例脚本。</span><span class="sxs-lookup"><span data-stu-id="31dfd-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="31dfd-177">此脚本是一个简单的示例，演示了如何在 Leap Motion Hand 中检索手部手部姿势。</span><span class="sxs-lookup"><span data-stu-id="31dfd-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="31dfd-178">球体在左闰手后，立方体在右闰手后。</span><span class="sxs-lookup"><span data-stu-id="31dfd-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="31dfd-179">Unity 编辑器工作流提示</span><span class="sxs-lookup"><span data-stu-id="31dfd-179">Unity editor workflow tip</span></span>

<span data-ttu-id="31dfd-180">使用 Leap Motion 数据提供程序不需要 VR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="31dfd-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="31dfd-181">可以使用 Leap 手在编辑器中测试对 MRTK 应用的更改，而无需头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="31dfd-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="31dfd-182">闰运动手会显示在编辑器中，无需插入 VR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="31dfd-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="31dfd-183">如果 `LeapControllerOrientation` 设置为头 **戴显示设备**，则闰运动控制器需要一手放在摄像头向前。</span><span class="sxs-lookup"><span data-stu-id="31dfd-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="31dfd-184">如果在编辑器中使用 WASD 键移动相机，并且 是头戴显示设备，则 `LeapControllerOrientation` 手不会跟随相机。 </span><span class="sxs-lookup"><span data-stu-id="31dfd-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="31dfd-185">只有在设置"头戴显示设备"时，VR 头戴显示设备已接通电源时，手 `LeapControllerOrientation` 部才跟随 **摄像头移动**。</span><span class="sxs-lookup"><span data-stu-id="31dfd-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="31dfd-186">如果 设置为 Desk，Leap 手将跟随编辑器 `LeapControllerOrientation` 中的照相机 **移动**。</span><span class="sxs-lookup"><span data-stu-id="31dfd-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="31dfd-187">从项目中删除 Leap Motion</span><span class="sxs-lookup"><span data-stu-id="31dfd-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="31dfd-188">导航到混合 **现实工具包**  >  **Leap Motion**  >  **独立闰运动 Unity 模块**</span><span class="sxs-lookup"><span data-stu-id="31dfd-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="31dfd-189">在此步骤中修改 **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** 文件中的引用时，让 Unity 刷新</span><span class="sxs-lookup"><span data-stu-id="31dfd-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="31dfd-190">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="31dfd-190">Close Unity</span></span>
1. <span data-ttu-id="31dfd-191">关闭Visual Studio（如果已打开）</span><span class="sxs-lookup"><span data-stu-id="31dfd-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="31dfd-192">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="31dfd-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="31dfd-193">删除 **UnityProjectName/Library** 目录</span><span class="sxs-lookup"><span data-stu-id="31dfd-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="31dfd-194">删除 **UnityProjectName/Assets/Plugins/LeapMotion** 目录</span><span class="sxs-lookup"><span data-stu-id="31dfd-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="31dfd-195">删除 **UnityProjectName/Assets/Plugins/LeapMotion.meta** 文件</span><span class="sxs-lookup"><span data-stu-id="31dfd-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="31dfd-196">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="31dfd-196">Reopen Unity</span></span>

<span data-ttu-id="31dfd-197">在 Unity 2018.4 中，你可能会注意到，删除库和 Leap Motion Core 资产后，错误仍然存在于控制台中。</span><span class="sxs-lookup"><span data-stu-id="31dfd-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="31dfd-198">如果在重新打开后记录错误，请再次重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="31dfd-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="31dfd-199">常见错误</span><span class="sxs-lookup"><span data-stu-id="31dfd-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="31dfd-200">Leap Motion 未与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="31dfd-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="31dfd-201">测试 Leap Motion Unity 模块是否与 MRTK 集成：</span><span class="sxs-lookup"><span data-stu-id="31dfd-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="31dfd-202">导航到 **Mixed Reality Toolkit > Utilities > Leap Motion >检查集成状态**</span><span class="sxs-lookup"><span data-stu-id="31dfd-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="31dfd-203">此时会显示一个弹出窗口，显示一条消息，指示 Leap Motion Unity 模块是否已与 MRTK 集成。</span><span class="sxs-lookup"><span data-stu-id="31dfd-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="31dfd-204">如果消息显示资产尚未集成：</span><span class="sxs-lookup"><span data-stu-id="31dfd-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="31dfd-205">确保 Leap Motion Unity 模块在项目中</span><span class="sxs-lookup"><span data-stu-id="31dfd-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="31dfd-206">请确保支持添加的版本，请参阅页面顶部的表，了解支持的版本。</span><span class="sxs-lookup"><span data-stu-id="31dfd-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="31dfd-207">在 **集成 Leap Motion Unity 模块> Leap Motion >混合现实工具包>实用工具**</span><span class="sxs-lookup"><span data-stu-id="31dfd-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="31dfd-208">复制程序集多人游戏 HLAPI 失败</span><span class="sxs-lookup"><span data-stu-id="31dfd-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="31dfd-209">导入 Leap Motion Unity Core 资产时，可能会记录此错误：</span><span class="sxs-lookup"><span data-stu-id="31dfd-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="31dfd-210">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="31dfd-210">**Solution**</span></span>

- <span data-ttu-id="31dfd-211">短期解决方案是重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="31dfd-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="31dfd-212">有关详细信息，请参阅问题[7761。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="31dfd-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="31dfd-213">闰运动示例场景</span><span class="sxs-lookup"><span data-stu-id="31dfd-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="31dfd-214">示例场景使用 DefaultLeapMotionConfiguration 配置文件，并确定 Unity 项目是否正确配置为使用 Leap Motion 数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="31dfd-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="31dfd-215">示例场景包含在 **MRTK/Examples/Demos/HandTracking/** 目录中 **的 Microsoft.MixedReality.Toolkit.Examples** 包中。</span><span class="sxs-lookup"><span data-stu-id="31dfd-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="31dfd-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31dfd-216">See also</span></span>

- [<span data-ttu-id="31dfd-217">输入提供者</span><span class="sxs-lookup"><span data-stu-id="31dfd-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="31dfd-218">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="31dfd-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
