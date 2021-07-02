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
# <a name="using-leap-motion"></a>使用 Leap Motion

需要使用 [Leap 运动控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此数据访问接口。

Leap 运动数据提供程序支持用于 VR 的有表述的手动跟踪，可用于在编辑器中快速制作原型。  可以将数据访问接口配置为使用耳机上装入的 Leap 运动控制器，或将其放置在桌面面上。

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

在独立平台上，可以在编辑器和设备上使用此提供程序。  它还可用于在 UWP 平台而不是 UWP 版本中的编辑器中。

| MRTK 版本 | 支持 Leap 运动 Unity 模块版本 |
| --- | --- |
|2.6. x | 4.5.0，4.5。1|
|2.7. x| 4.5.0、4.5.1、4.6.0、4.7.0、4.7.1、4.8。0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>在 MRTK 中使用 Ultraleap) 手动跟踪的 Leap 运动 (

1. 导入 MRTK 和 Leap 运动 Unity 模块
    - 安装最新的 [Leap 运动 SDK](https://developer.leapmotion.com/releases/?category=orion) （如果尚未安装）
    - 导入 **MixedReality Toolkit。Foundation** 打包到 Unity 项目。
    - 下载最新版本的 [Leap 运动 Unity 模块](https://developer.leapmotion.com/unity) 并将其导入到项目中
        - 仅导入 Unity 模块内的 **核心** 包

1. 将 Leap 运动 Unity 模块与 MRTK 集成
    - 在 Unity 模块位于项目中后，导航到 **混合现实 Toolkit**  >  **leap 运动**  >  **集成 Leap 运动 Unity 模块**
    > [!NOTE]
    > 将 Unity 模块集成到 MRTK 会将10个程序集定义添加到项目，并添加对 Toolkit MixedReality 的引用。 **LeapMotion** 程序集定义。 确保已关闭 Visual Studio。

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. 添加 Leap 运动数据提供程序
    - 创建新的 Unity 场景
    - 通过导航到 **混合现实 Toolkit** 添加到场景  >  **，并配置**
    - 选择层次结构中的 MixedRealityToolkit 游戏对象，并选择 " **复制" 和 "自定义** " 克隆默认的混合现实配置文件。

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - 选择 **输入** 配置文件

    ![输入配置文件1](../images/cross-platform/InputConfigurationProfile.png)

    - 选择输入系统配置文件中的 " **克隆** " 以启用修改。

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - 打开 " **输入数据提供程序** " 部分，选择顶部的 " **添加数据访问接口** "，将在列表的末尾添加一个新的数据提供程序。  打开新的数据提供程序并将 **类型** 设置为 " **Toolkit MixedReality"。LeapMotion > LeapMotionDeviceManager**

    ![Leap 添加数据提供程序](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - 选择 " **克隆** " 以更改默认的 Leap 运动设置。

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Leap 运动数据提供程序包含属性，该 `LeapControllerOrientation` 属性是 Leap 运动控制器的位置。 `LeapControllerOrientation.Headset` 指示控制器已装入耳机。 `LeapControllerOrientation.Desk` 指示控制器位于桌面上。 默认值设置为 `LeapControllerOrientation.Headset` 。
    - 每个控制器方向都包含偏移属性：
      - **头戴** 显示在 LeapXRServiceProvider 组件中的偏移属性的位置。  `LeapVRDeviceOffsetMode`有三个选项：默认值、手动头偏移和转换。  如果偏移模式为默认值，则不会对 Leap 运动控制器应用偏移量。  手动 Head 偏移模式允许修改三个属性： `LeapVRDeviceOffsetY` 、 `LeapVRDeviceOffsetZ` 和 `LeapVRDeviceTiltX` 。  然后，"轴偏移量" 属性值将应用到默认控制器位置。  转换偏移模式包含 `LeapVRDeviceOrigin` 转换属性，该属性指定 Leap 运动控制器的新原点。
      - **桌面** 方向包含 `LeapControllerOffset` 用于定义桌面 leap 定位位置的属性。  偏移量是相对于摄像机的主位置计算的，默认值为 (0，-0.2，0.35) ，以确保指针显示在相机的正面和下方。

        > [!NOTE]
        > 当应用程序启动时，会应用配置文件中的偏移量属性。  若要在运行时中修改这些值，请从 Leap 运动 Device Manager 获取 Leap 运动服务提供程序：
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` 和 `ExitPinchDistance` 是用于挤压/空中攻攻的距离阈值检测。  通过测量食指笔尖和 thumb 笔尖之间的距离来计算挤压手势。  若要引发输入关闭事件，则默认值 `EnterPinchDistance` 设置为0.02。  若要在 (退出 "挤压") 时引发输入事件，请使用0.05 的默认距离。

    `LeapControllerOrientation`：耳机 (默认值)  |  `LeapControllerOrientation`：书桌
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. 测试 Leap 运动数据提供程序
    - 在将 Leap 运动数据提供程序添加到输入系统配置文件后，按 "播放"，将你的手移动到 Leap 运动控制器的前方，你应该会看到手的接合表示形式。

1. 生成项目
    - 导航到 **文件 > 生成设置**
    - 如果使用 Leap 运动数据提供程序，则仅支持独立生成。
    - 有关如何使用 Windows Mixed Reality 耳机来实现独立版本的说明，请参阅[构建和部署 MRTK 到 WMR 耳机 (独立) ](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)。

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

## <a name="removing-leap-motion-from-the-project"></a>从 Project 中移除 Leap 运动

1. 导航到 **混合现实 Toolkit**  >  **leap**  >  **单独的 leap 移动**
    - 让 Unity 刷新为 Toolkit MixedReality 中的引用。 **LeapMotion. asmdef** 文件在此步骤中进行了修改
1. 关闭 Unity
1. 关闭 Visual Studio （如果它已打开）
1. 打开文件资源管理器并导航到 MRTK Unity 项目的根目录
    - 删除 **UnityProjectName/库** 目录
    - 删除 **UnityProjectName/资产/插件/LeapMotion** 目录
    - 删除 **UnityProjectName/资产/插件/LeapMotion** 文件
1. 重新打开 Unity

在 Unity 2018.4 中，你可能会注意到，在删除库和 Leap 运动核心资产后，错误仍然保留在控制台中。
如果重新打开后记录错误，请重新启动 Unity。

## <a name="common-errors"></a>常见错误

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap 运动尚未与 MRTK 集成

测试 Leap 运动 Unity 模块是否与 MRTK 集成：

- 导航到 **混合现实 Toolkit > 实用工具 > Leap 运动 > 检查集成状态**
  - 此时将显示一个弹出窗口，其中包含有关 Leap 运动 Unity 模块是否与 MRTK 集成的消息。
- 如果消息指出尚未集成资产：
  - 请确保 Leap 运动 Unity 模块在项目中
  - 请确保所添加的版本受支持，请参阅页面顶部的表中支持的版本。
  - 尝试将 **混合现实 Toolkit > 实用工具 > leap 运动 > 集成 leap 运动 Unity 模块**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>复制程序集多人 HLAPI 失败

导入 Leap 运动 Unity 核心资产时，可能会记录此错误：

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**解决方案**

- 短期解决方案是重新启动 Unity。 有关详细信息，请参阅 [问题 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。

## <a name="leap-motion-example-scene"></a>Leap 运动示例场景

示例场景使用 DefaultLeapMotionConfiguration 配置文件，并确定是否已正确配置 Unity 项目以使用 Leap 运动数据提供程序。

示例场景包含在 **Toolkit MixedReality 中。** **MRTK/示例/演示程序/HandTracking/** 目录中的示例包。  

## <a name="see-also"></a>另请参阅

- [输入提供者](../features/input/input-providers.md)
- [手动跟踪](../features/input/hand-tracking.md)
