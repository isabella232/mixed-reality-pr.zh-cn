---
title: LeapMotionMRTK
description: 为 Leap Motion 配置的文档
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Leap Motion，
ms.openlocfilehash: ea9e257815116c364fe2f1e37ca3477ec56262cb
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852348"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="fe235-104">如何在 MRTK 中配置 Ultraleap (Leap Motion) 手动跟踪</span><span class="sxs-lookup"><span data-stu-id="fe235-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="fe235-105">[使用此数据访问接口](https://www.ultraleap.com/product/leap-motion-controller/)需要 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="fe235-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="fe235-106">Leap Motion 数据提供程序支持 VR 的明确手部跟踪，并且可用于在编辑器中快速原型制作。</span><span class="sxs-lookup"><span data-stu-id="fe235-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="fe235-107">可以将数据访问接口配置为使用安装在头戴显示设备上或放在桌面人脸上的 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="fe235-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="fe235-109">在独立平台上，此提供程序可在编辑器和设备上使用。</span><span class="sxs-lookup"><span data-stu-id="fe235-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="fe235-110">它还可以在 UWP 平台上的编辑器中使用，但不能在 UWP 生成中使用。</span><span class="sxs-lookup"><span data-stu-id="fe235-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="fe235-111">支持 Leap Motion Unity 模块版本</span><span class="sxs-lookup"><span data-stu-id="fe235-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="fe235-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="fe235-112">4.5.0</span></span>|
|<span data-ttu-id="fe235-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="fe235-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="fe235-114">使用 Ultraleap (Leap Motion) MRTK 中的手动跟踪</span><span class="sxs-lookup"><span data-stu-id="fe235-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="fe235-115">导入 MRTK 和 Leap Motion Unity 模块</span><span class="sxs-lookup"><span data-stu-id="fe235-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="fe235-116">安装 [Leap Motion SDK 4.0.0（](https://developer.leapmotion.com/releases/?category=orion) 如果尚未安装）</span><span class="sxs-lookup"><span data-stu-id="fe235-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="fe235-117">将 **Microsoft.MixedReality.Toolkit.Foundation** 包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="fe235-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="fe235-118">下载最新版本的 Leap Motion [Unity 模块并导入](https://developer.leapmotion.com/unity) 到项目中</span><span class="sxs-lookup"><span data-stu-id="fe235-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="fe235-119">仅导入 **Unity** 模块中的 Core 包</span><span class="sxs-lookup"><span data-stu-id="fe235-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="fe235-120">将 Leap Motion Unity 模块与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="fe235-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="fe235-121">Unity 模块进入项目后，导航到"混合 **现实工具包**  >  **""Leap Motion**  >  **集成 Leap Motion Unity 模块"**</span><span class="sxs-lookup"><span data-stu-id="fe235-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="fe235-122">将 Unity 模块集成到 MRTK 会向项目添加 10 个程序集定义，并添加 **对 Microsoft.MixedReality.Toolkit.Providers.LeapMotion** 程序集定义的引用。</span><span class="sxs-lookup"><span data-stu-id="fe235-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="fe235-123">确保已关闭 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fe235-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="fe235-125">添加 Leap 运动数据提供程序</span><span class="sxs-lookup"><span data-stu-id="fe235-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="fe235-126">创建新的 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="fe235-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="fe235-127">通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景</span><span class="sxs-lookup"><span data-stu-id="fe235-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="fe235-128">选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。</span><span class="sxs-lookup"><span data-stu-id="fe235-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="fe235-130">选择 **输入** 配置文件</span><span class="sxs-lookup"><span data-stu-id="fe235-130">Select the **Input** Configuration Profile</span></span>

    ![输入配置文件1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="fe235-132">选择输入系统配置文件中的 " **克隆** " 以启用修改。</span><span class="sxs-lookup"><span data-stu-id="fe235-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="fe235-134">打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据访问接口** "，将在列表的末尾添加一个新的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="fe235-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="fe235-135">打开新的数据提供程序并将 **类型** 设置为 **MixedReality > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="fe235-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap 添加数据提供程序](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="fe235-137">选择 " **克隆** " 以更改默认的 Leap 运动设置。</span><span class="sxs-lookup"><span data-stu-id="fe235-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="fe235-139">Leap 运动数据提供程序包含属性，该 `LeapControllerOrientation` 属性是 Leap 运动控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="fe235-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="fe235-140">`LeapControllerOrientation.Headset` 指示控制器已装入耳机。</span><span class="sxs-lookup"><span data-stu-id="fe235-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="fe235-141">`LeapControllerOrientation.Desk` 指示控制器位于桌面上。</span><span class="sxs-lookup"><span data-stu-id="fe235-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="fe235-142">默认值设置为 `LeapControllerOrientation.Headset` 。</span><span class="sxs-lookup"><span data-stu-id="fe235-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="fe235-143">每个控制器方向都包含偏移属性：</span><span class="sxs-lookup"><span data-stu-id="fe235-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="fe235-144">头 **戴** 显示设备方向偏移属性镜像 LeapXRServiceProvider 组件中的偏移属性。</span><span class="sxs-lookup"><span data-stu-id="fe235-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="fe235-145">有 `LeapVRDeviceOffsetMode` 三个选项："默认"、"手动头部偏移"和"转换"。</span><span class="sxs-lookup"><span data-stu-id="fe235-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="fe235-146">如果偏移模式为 Default，则偏移量将不会应用于 Leap Motion 控制器。</span><span class="sxs-lookup"><span data-stu-id="fe235-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="fe235-147">手动头部偏移模式允许修改三个属性： 和 `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` 。</span><span class="sxs-lookup"><span data-stu-id="fe235-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="fe235-148">然后，轴偏移属性值将应用于默认控制器位置。</span><span class="sxs-lookup"><span data-stu-id="fe235-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="fe235-149">转换偏移模式包含 `LeapVRDeviceOrigin` Transform 属性，该属性指定 Leap Motion 控制器的新原点。</span><span class="sxs-lookup"><span data-stu-id="fe235-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="fe235-150">桌面 **方向** 包含 `LeapControllerOffset` 属性，该属性定义桌面闰手的定位点位置。</span><span class="sxs-lookup"><span data-stu-id="fe235-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="fe235-151">偏移量相对于主相机位置进行计算，默认值为 (0、-0.2、0.35) 以确保手出现在相机的前面和视图中。</span><span class="sxs-lookup"><span data-stu-id="fe235-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="fe235-152">应用程序启动时，将应用配置文件中的偏移属性一次。</span><span class="sxs-lookup"><span data-stu-id="fe235-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="fe235-153">若要在运行时修改值，请从 Leap Motion 提供程序获取 Leap Motion 设备管理器：</span><span class="sxs-lookup"><span data-stu-id="fe235-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="fe235-154">`EnterPinchDistance``ExitPinchDistance`和 是收缩/敲击手势检测的距离阈值。</span><span class="sxs-lookup"><span data-stu-id="fe235-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="fe235-155">收缩手势是通过测量索引指尖和拇指尖之间的距离计算的。</span><span class="sxs-lookup"><span data-stu-id="fe235-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="fe235-156">若要在输入关闭事件时引发 ，默认值 `EnterPinchDistance` 设置为 0.02。</span><span class="sxs-lookup"><span data-stu-id="fe235-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="fe235-157">若要在退出收缩 (时引发输入 up 事件，) 指提示和指纹提示之间的默认距离为 0.05。</span><span class="sxs-lookup"><span data-stu-id="fe235-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="fe235-158">`LeapControllerOrientation`：头戴显示 (默认) </span><span class="sxs-lookup"><span data-stu-id="fe235-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="fe235-159">`LeapControllerOrientation`：服务台</span><span class="sxs-lookup"><span data-stu-id="fe235-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="fe235-164">测试 Leap 运动数据提供程序</span><span class="sxs-lookup"><span data-stu-id="fe235-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="fe235-165">在将 Leap 运动数据提供程序添加到输入系统配置文件后，按 "播放"，将你的手移动到 Leap 运动控制器的前方，你应该会看到手的接合表示形式。</span><span class="sxs-lookup"><span data-stu-id="fe235-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="fe235-166">生成项目</span><span class="sxs-lookup"><span data-stu-id="fe235-166">Building your project</span></span>
    - <span data-ttu-id="fe235-167">导航到 **文件 > 生成设置**</span><span class="sxs-lookup"><span data-stu-id="fe235-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="fe235-168">如果使用 Leap 运动数据提供程序，则仅支持独立生成。</span><span class="sxs-lookup"><span data-stu-id="fe235-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="fe235-169">有关如何使用 Windows Mixed Reality 耳机进行独立生成的说明，请参阅 [生成和部署 MRTK (独立) ](wmr-mrtk.md#building-and-deploying-mrtk-standalone)。</span><span class="sxs-lookup"><span data-stu-id="fe235-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="fe235-170">获取手型</span><span class="sxs-lookup"><span data-stu-id="fe235-170">Getting the hand joints</span></span>

<span data-ttu-id="fe235-171">使用 Leap 运动数据提供程序的联系，与 MRTK 的有无表述的手的联合检索相同。</span><span class="sxs-lookup"><span data-stu-id="fe235-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="fe235-172">有关详细信息，请参阅 [手动跟踪](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)。</span><span class="sxs-lookup"><span data-stu-id="fe235-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="fe235-173">使用 unity 场景中的 MRTK 和在输入系统配置文件中添加为输入数据提供程序的 Leap 运动数据提供程序时，请创建一个空游戏对象并附加以下示例脚本。</span><span class="sxs-lookup"><span data-stu-id="fe235-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="fe235-174">此脚本是一个简单的示例，说明如何在 Leap 运动手中检索手掌接点的姿势。</span><span class="sxs-lookup"><span data-stu-id="fe235-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="fe235-175">当多维数据集遵循适当的 Leap 时，球会跟随左侧的 Leap。</span><span class="sxs-lookup"><span data-stu-id="fe235-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="fe235-176">Unity 编辑器工作流提示</span><span class="sxs-lookup"><span data-stu-id="fe235-176">Unity editor workflow tip</span></span>

<span data-ttu-id="fe235-177">使用 Leap 运动数据提供程序不需要 VR 耳机。</span><span class="sxs-lookup"><span data-stu-id="fe235-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="fe235-178">无需耳机即可在编辑器中测试对 MRTK 应用的更改。</span><span class="sxs-lookup"><span data-stu-id="fe235-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="fe235-179">闰运动将显示在编辑器中，并且不会插入 VR 耳机。</span><span class="sxs-lookup"><span data-stu-id="fe235-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="fe235-180">如果 `LeapControllerOrientation` 设置为 **头戴式耳机**，则需要将 Leap 运动控制器向上保持一只手。</span><span class="sxs-lookup"><span data-stu-id="fe235-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="fe235-181">如果使用 WASD 中的 "键" 来移动照相机并且 `LeapControllerOrientation` 为 " **耳机**"，则不会跟随摄像机。</span><span class="sxs-lookup"><span data-stu-id="fe235-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="fe235-182">如果在 `LeapControllerOrientation` 设置了 **耳机** 时插入了 VR 耳机，则只会跟随摄像机运动。</span><span class="sxs-lookup"><span data-stu-id="fe235-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="fe235-183">如果设置为 "桌面"，则在编辑器中，Leap 会按照相机的移动进行操作 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="fe235-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="fe235-184">从项目中删除 Leap Motion</span><span class="sxs-lookup"><span data-stu-id="fe235-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="fe235-185">导航到混合 **现实工具包**  >  **Leap Motion**  >  **独立闰运动 Unity 模块**</span><span class="sxs-lookup"><span data-stu-id="fe235-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="fe235-186">在此步骤中修改 **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** 文件中的引用时，让 Unity 刷新</span><span class="sxs-lookup"><span data-stu-id="fe235-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="fe235-187">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="fe235-187">Close Unity</span></span>
1. <span data-ttu-id="fe235-188">关闭Visual Studio（如果已打开）</span><span class="sxs-lookup"><span data-stu-id="fe235-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="fe235-189">打开文件资源管理器并导航到 MRTK Unity 项目的根目录</span><span class="sxs-lookup"><span data-stu-id="fe235-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="fe235-190">删除 **UnityProjectName/Library** 目录</span><span class="sxs-lookup"><span data-stu-id="fe235-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="fe235-191">删除 **UnityProjectName/Assets/Plugins/LeapMotion** 目录</span><span class="sxs-lookup"><span data-stu-id="fe235-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="fe235-192">删除 **UnityProjectName/Assets/Plugins/LeapMotion.meta** 文件</span><span class="sxs-lookup"><span data-stu-id="fe235-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="fe235-193">重新打开 Unity</span><span class="sxs-lookup"><span data-stu-id="fe235-193">Reopen Unity</span></span>

<span data-ttu-id="fe235-194">在 Unity 2018.4 中，你可能会注意到，删除库和 Leap Motion Core 资产后，错误仍然存在于控制台中。</span><span class="sxs-lookup"><span data-stu-id="fe235-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="fe235-195">如果在重新打开后记录错误，请再次重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="fe235-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="fe235-196">常见错误</span><span class="sxs-lookup"><span data-stu-id="fe235-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="fe235-197">Leap Motion 未与 MRTK 集成</span><span class="sxs-lookup"><span data-stu-id="fe235-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="fe235-198">测试 Leap Motion Unity 模块是否与 MRTK 集成：</span><span class="sxs-lookup"><span data-stu-id="fe235-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="fe235-199">导航到 **Mixed Reality Toolkit > Utilities > Leap Motion >检查集成状态**</span><span class="sxs-lookup"><span data-stu-id="fe235-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="fe235-200">此时会显示一个弹出窗口，显示一条消息，指示 Leap Motion Unity 模块是否已与 MRTK 集成。</span><span class="sxs-lookup"><span data-stu-id="fe235-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="fe235-201">如果消息显示资产尚未集成：</span><span class="sxs-lookup"><span data-stu-id="fe235-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="fe235-202">确保 Leap Motion Unity 模块在项目中</span><span class="sxs-lookup"><span data-stu-id="fe235-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="fe235-203">请确保支持添加的版本，请参阅页面顶部的表，了解支持的版本。</span><span class="sxs-lookup"><span data-stu-id="fe235-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="fe235-204">在 **集成 Leap Motion Unity 模块> Leap Motion >混合现实工具包>实用工具**</span><span class="sxs-lookup"><span data-stu-id="fe235-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="fe235-205">复制程序集多人 HLAPI 失败</span><span class="sxs-lookup"><span data-stu-id="fe235-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="fe235-206">导入 Leap 运动 Unity 核心资产时，可能会记录此错误：</span><span class="sxs-lookup"><span data-stu-id="fe235-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="fe235-207">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="fe235-207">**Solution**</span></span>

- <span data-ttu-id="fe235-208">短期解决方案是重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="fe235-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="fe235-209">有关详细信息，请参阅 [问题 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。</span><span class="sxs-lookup"><span data-stu-id="fe235-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="fe235-210">Leap 运动示例场景</span><span class="sxs-lookup"><span data-stu-id="fe235-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="fe235-211">示例场景使用 DefaultLeapMotionConfiguration 配置文件，并确定是否已正确配置 Unity 项目以使用 Leap 运动数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="fe235-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="fe235-212">示例场景包含在 **MRTK/example/演示程序/HandTracking/** 目录中的 **MixedReality** 包中。</span><span class="sxs-lookup"><span data-stu-id="fe235-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="fe235-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe235-213">See also</span></span>

<span data-ttu-id="fe235-214">-[输入提供程序](../features/input/input-providers.md) 
-[手动跟踪](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="fe235-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
