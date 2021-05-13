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
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>如何在 MRTK 中配置 Ultraleap (Leap Motion) 手动跟踪

[使用此数据访问接口](https://www.ultraleap.com/product/leap-motion-controller/)需要 Leap Motion 控制器。

Leap Motion 数据提供程序支持 VR 的明确手部跟踪，并且可用于在编辑器中快速原型制作。  可以将数据访问接口配置为使用安装在头戴显示设备上或放在桌面人脸上的 Leap Motion 控制器。

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

在独立平台上，此提供程序可在编辑器和设备上使用。  它还可以在 UWP 平台上的编辑器中使用，但不能在 UWP 生成中使用。

|支持 Leap Motion Unity 模块版本|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>使用 Ultraleap (Leap Motion) MRTK 中的手动跟踪

1. 导入 MRTK 和 Leap Motion Unity 模块
    - 安装 [Leap Motion SDK 4.0.0（](https://developer.leapmotion.com/releases/?category=orion) 如果尚未安装）
    - 将 **Microsoft.MixedReality.Toolkit.Foundation** 包导入 Unity 项目。
    - 下载最新版本的 Leap Motion [Unity 模块并导入](https://developer.leapmotion.com/unity) 到项目中
        - 仅导入 **Unity** 模块中的 Core 包

1. 将 Leap Motion Unity 模块与 MRTK 集成
    - Unity 模块进入项目后，导航到"混合 **现实工具包**  >  **""Leap Motion**  >  **集成 Leap Motion Unity 模块"**
    > [!NOTE]
    > 将 Unity 模块集成到 MRTK 会向项目添加 10 个程序集定义，并添加 **对 Microsoft.MixedReality.Toolkit.Providers.LeapMotion** 程序集定义的引用。 确保已关闭 Visual Studio。

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. 添加 Leap 运动数据提供程序
    - 创建新的 Unity 场景
    - 通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景
    - 选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - 选择 **输入** 配置文件

    ![输入配置文件1](../images/cross-platform/InputConfigurationProfile.png)

    - 选择输入系统配置文件中的 " **克隆** " 以启用修改。

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - 打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据访问接口** "，将在列表的末尾添加一个新的数据提供程序。  打开新的数据提供程序并将 **类型** 设置为 **MixedReality > LeapMotionDeviceManager**

    ![Leap 添加数据提供程序](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - 选择 " **克隆** " 以更改默认的 Leap 运动设置。

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Leap 运动数据提供程序包含属性，该 `LeapControllerOrientation` 属性是 Leap 运动控制器的位置。 `LeapControllerOrientation.Headset` 指示控制器已装入耳机。 `LeapControllerOrientation.Desk` 指示控制器位于桌面上。 默认值设置为 `LeapControllerOrientation.Headset` 。
    - 每个控制器方向都包含偏移属性：
      - 头 **戴** 显示设备方向偏移属性镜像 LeapXRServiceProvider 组件中的偏移属性。  有 `LeapVRDeviceOffsetMode` 三个选项："默认"、"手动头部偏移"和"转换"。  如果偏移模式为 Default，则偏移量将不会应用于 Leap Motion 控制器。  手动头部偏移模式允许修改三个属性： 和 `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` 。  然后，轴偏移属性值将应用于默认控制器位置。  转换偏移模式包含 `LeapVRDeviceOrigin` Transform 属性，该属性指定 Leap Motion 控制器的新原点。
      - 桌面 **方向** 包含 `LeapControllerOffset` 属性，该属性定义桌面闰手的定位点位置。  偏移量相对于主相机位置进行计算，默认值为 (0、-0.2、0.35) 以确保手出现在相机的前面和视图中。

        > [!NOTE]
        > 应用程序启动时，将应用配置文件中的偏移属性一次。  若要在运行时修改值，请从 Leap Motion 提供程序获取 Leap Motion 设备管理器：
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance``ExitPinchDistance`和 是收缩/敲击手势检测的距离阈值。  收缩手势是通过测量索引指尖和拇指尖之间的距离计算的。  若要在输入关闭事件时引发 ，默认值 `EnterPinchDistance` 设置为 0.02。  若要在退出收缩 (时引发输入 up 事件，) 指提示和指纹提示之间的默认距离为 0.05。

    `LeapControllerOrientation`：头戴显示 (默认)  |  `LeapControllerOrientation`：服务台
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. 测试 Leap 运动数据提供程序
    - 在将 Leap 运动数据提供程序添加到输入系统配置文件后，按 "播放"，将你的手移动到 Leap 运动控制器的前方，你应该会看到手的接合表示形式。

1. 生成项目
    - 导航到 **文件 > 生成设置**
    - 如果使用 Leap 运动数据提供程序，则仅支持独立生成。
    - 有关如何使用 Windows Mixed Reality 耳机进行独立生成的说明，请参阅 [生成和部署 MRTK (独立) ](wmr-mrtk.md#building-and-deploying-mrtk-standalone)。

## <a name="getting-the-hand-joints"></a>获取手型

使用 Leap 运动数据提供程序的联系，与 MRTK 的有无表述的手的联合检索相同。  有关详细信息，请参阅 [手动跟踪](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)。

使用 unity 场景中的 MRTK 和在输入系统配置文件中添加为输入数据提供程序的 Leap 运动数据提供程序时，请创建一个空游戏对象并附加以下示例脚本。

此脚本是一个简单的示例，说明如何在 Leap 运动手中检索手掌接点的姿势。  当多维数据集遵循适当的 Leap 时，球会跟随左侧的 Leap。

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

## <a name="unity-editor-workflow-tip"></a>Unity 编辑器工作流提示

使用 Leap 运动数据提供程序不需要 VR 耳机。  无需耳机即可在编辑器中测试对 MRTK 应用的更改。

闰运动将显示在编辑器中，并且不会插入 VR 耳机。  如果 `LeapControllerOrientation` 设置为 **头戴式耳机**，则需要将 Leap 运动控制器向上保持一只手。

> [!NOTE]
> 如果使用 WASD 中的 "键" 来移动照相机并且 `LeapControllerOrientation` 为 " **耳机**"，则不会跟随摄像机。 如果在 `LeapControllerOrientation` 设置了 **耳机** 时插入了 VR 耳机，则只会跟随摄像机运动。  如果设置为 "桌面"，则在编辑器中，Leap 会按照相机的移动进行操作 `LeapControllerOrientation` 。 

## <a name="removing-leap-motion-from-the-project"></a>从项目中删除 Leap Motion

1. 导航到混合 **现实工具包**  >  **Leap Motion**  >  **独立闰运动 Unity 模块**
    - 在此步骤中修改 **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** 文件中的引用时，让 Unity 刷新
1. 关闭 Unity
1. 关闭Visual Studio（如果已打开）
1. 打开文件资源管理器并导航到 MRTK Unity 项目的根目录
    - 删除 **UnityProjectName/Library** 目录
    - 删除 **UnityProjectName/Assets/Plugins/LeapMotion** 目录
    - 删除 **UnityProjectName/Assets/Plugins/LeapMotion.meta** 文件
1. 重新打开 Unity

在 Unity 2018.4 中，你可能会注意到，删除库和 Leap Motion Core 资产后，错误仍然存在于控制台中。
如果在重新打开后记录错误，请再次重启 Unity。

## <a name="common-errors"></a>常见错误

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion 未与 MRTK 集成

测试 Leap Motion Unity 模块是否与 MRTK 集成：

- 导航到 **Mixed Reality Toolkit > Utilities > Leap Motion >检查集成状态**
  - 此时会显示一个弹出窗口，显示一条消息，指示 Leap Motion Unity 模块是否已与 MRTK 集成。
- 如果消息显示资产尚未集成：
  - 确保 Leap Motion Unity 模块在项目中
  - 请确保支持添加的版本，请参阅页面顶部的表，了解支持的版本。
  - 在 **集成 Leap Motion Unity 模块> Leap Motion >混合现实工具包>实用工具**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>复制程序集多人 HLAPI 失败

导入 Leap 运动 Unity 核心资产时，可能会记录此错误：

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**解决方案**

- 短期解决方案是重新启动 Unity。 有关详细信息，请参阅 [问题 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。

## <a name="leap-motion-example-scene"></a>Leap 运动示例场景

示例场景使用 DefaultLeapMotionConfiguration 配置文件，并确定是否已正确配置 Unity 项目以使用 Leap 运动数据提供程序。

示例场景包含在 **MRTK/example/演示程序/HandTracking/** 目录中的 **MixedReality** 包中。  

## <a name="see-also"></a>另请参阅

-[输入提供程序](../features/input/input-providers.md) 
-[手动跟踪](../features/input/hand-tracking.md)
