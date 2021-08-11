---
title: 感知模拟
description: 使用感知模拟库自动完成沉浸式应用程序模拟输入的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、模拟、测试
ms.openlocfilehash: 8d2999868bfdcf67c1174209566e67fe937005946ef82dd50337d9098c1e1971
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193763"
---
# <a name="perception-simulation"></a>感知模拟

是否要为应用生成自动测试？ 是否希望你的测试超出组件级别的单元测试，并真正运用端到端应用？ 感知模拟是你要查找的内容。 感知模拟库将人类和世界输入数据发送到你的应用，因此你可以自动执行测试。 例如，可以模拟查找特定的可重复位置的人工输入，然后使用笔势或运动控制器。

感知模拟可以将此类模拟输入发送到物理 HoloLens、HoloLens 模拟器 (第一代) 、HoloLens 2 Emulator 或安装有混合现实门户的 PC。 感知模拟会绕过混合现实设备上的实时传感器，并将模拟输入发送到设备上运行的应用程序。 应用程序通过它们始终使用的相同 Api 来接收这些输入事件，无法判断运行与感知模拟之间的差异。 感知模拟是 HoloLens 模拟器用来向 HoloLens 虚拟机发送模拟输入的一种技术。

若要开始在代码中使用模拟，请首先创建 IPerceptionSimulationManager 对象。 在该对象中，可以发出命令来控制模拟 "人体" 的属性，包括头位置、手形位置和手势。 还可以启用和操作运动控制器。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>设置用于感知模拟的 Visual Studio Project
1. 在开发电脑上[安装 HoloLens 模拟器](../install-the-tools.md)。 模拟器包含用于感知模拟的库。
2.  (控制台创建新的 Visual Studio c # 桌面项目 Project 非常适合入门) 。
3. 将以下二进制文件作为引用添加到你的项目中， (Project >>引用 ... ) 。可以在% ProgramFiles (x86) % \ microsoft XDE \\ () 版本中找到它们，如 () HoloLens 2 **x86 Emulator% \ microsoft XDE \\ 10.0.18362.0** 。   (注意：尽管二进制文件是 HoloLens 2 Emulator 的一部分，但它们也适用于桌面上的 Windows Mixed Reality。 ) 。 用于感知模拟的 PerceptionSimulationManager.Interop.dll 托管 c # 包装。
    b. 用于设置到 HoloLens 或仿真程序的 web 套接字通信通道 PerceptionSimulationRest.dll 库。
    c. 用于模拟 SimulationStream.Interop.dll 共享的类型。
4. 将实现二进制 PerceptionSimulationManager.dll 添加到项目 a。 首先，将其作为二进制文件添加到项目中， (Project >>"现有项 ..." ) 。将其保存为链接，使其不会将其复制到项目源文件夹。 ![将 PerceptionSimulationManager.dll 作为链接 b 添加到项目 ](images/saveaslink.png) 。 然后，确保它在生成时复制到输出文件夹。 这位于二进制文件的属性表中。 ![将 PerceptionSimulationManager.dll 标记为复制到输出目录](images/copyalways.png)
5. 将活动解决方案平台设置为 x64。   (使用 Configuration Manager 为 x64 创建平台项（如果尚不存在）。 ) 

## <a name="creating-an-iperceptionsimulation-manager-object"></a>创建 IPerceptionSimulation Manager 对象

若要控制模拟，你将对从 IPerceptionSimulationManager 对象检索到的对象进行更新。 第一步是获取该对象，并将其连接到目标设备或仿真程序。 可以通过单击[工具栏](using-the-hololens-emulator.md)中的 "设备门户" 按钮来获取仿真程序的 IP 地址。

![打开设备门户图标 ](images/emulator-deviceportal.png) **打开设备门户**：在模拟器中打开 HoloLens OS 的 Windows 设备门户。  对于 Windows Mixed Reality，可以在 "更新 & 安全性" 下的设置应用程序中检索此项，然后在 "启用设备门户" 下 "连接 using：" 部分中的 "开发人员"。  请务必记下 IP 地址和端口。

首先，调用 RestSimulationStreamSink 来获取 RestSimulationStreamSink 对象。 这是你将通过 http 连接控制的目标设备或仿真程序。 你的命令将传递到设备或模拟器上运行[Windows 设备门户](using-the-windows-device-portal.md)并由其进行处理。 创建对象需要四个参数：
* Uri uri-目标设备的 IP 地址 (例如，" https://123.123.123.123 " 或 " https://123.123.123.123:50080 " ) 
* 系统 NetworkCredential 凭据-用于连接到目标设备或模拟器上的[Windows 设备门户](using-the-windows-device-portal.md)的用户名/密码。 如果是通过其本地地址连接到模拟器 (例如，168。*.*.* ) 在同一台计算机上，将接受任何凭据。
* 布尔标准-对于普通优先级为 True，低优先级为 false。 通常，你需要将此值设置为 *true* ，以便测试方案允许你的测试进行控制。  模拟器和 Windows Mixed Reality 模拟使用低优先级连接。  如果你的测试也使用低优先级连接，则最新建立的连接将处于控制之下。
* CancellationToken 标记-用于取消异步操作的标记。

其次，你将创建 IPerceptionSimulationManager。 这是用于控制模拟的对象。 还必须在异步方法中完成此操作。

## <a name="control-the-simulated-human"></a>控制模拟的人工

IPerceptionSimulationManager 具有返回 ISimulatedHuman 对象的人属性。 若要控制模拟人力，请对此对象执行操作。 例如：

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>基本示例 c # 控制台应用程序

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>扩展的示例 c # 控制台应用程序

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>DOF 控制器上的注意事项

在模拟 DOF 控制器上调用方法的任何属性之前，必须激活控制器。  如果不这样做，将导致异常。  从 Windows 10 2019 年5月更新开始，可以通过将 ISimulatedSixDofController 对象的 Status 属性设置为 SimulatedSixDofControllerStatus，来安装和激活模拟 DOF 控制器。
在 Windows 10 2018 年10月更新及更早版本中，必须先通过调用 \ Windows \System32 文件夹中的 PerceptionSimulationDevice 工具单独安装模拟 6 DOF 控制器。  此工具的用法如下所示：


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

例如

```
    PerceptionSimulationDevice.exe i 6dof 1
```

支持的操作包括：
* i = 安装
* q = 查询
* r = 删除

支持的实例包括：
* 1 = 左 6-DOF 控制器
* 2 = 右 6-DOF 控制器

该进程的退出代码将指示成功 (零返回值) 或 (非零返回值) 。  当使用 "q" 操作来查询控制器是否已安装时，如果未安装控制器，则返回值将为零 (0) 如果控制器已安装，则返回 (1) 。

删除 Windows 10 2018 年10月更新或更早版本上的控制器时，请先通过 API 将其状态设置为 Off，然后调用 PerceptionSimulationDevice 工具。

必须以管理员身份运行此工具。




## <a name="api-reference"></a>API 参考

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>PerceptionSimulation. SimulatedDeviceType

描述模拟设备类型

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**PerceptionSimulation. SimulatedDeviceType. 引用**

虚构引用设备，PerceptionSimulationManager 的默认值

### <a name="microsoftperceptionsimulationheadtrackermode"></a>PerceptionSimulation. HeadTrackerMode

描述 head 跟踪器模式

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**PerceptionSimulation. HeadTrackerMode**

默认标题跟踪。 这意味着系统可能会根据运行时条件选择最佳的标题跟踪模式。

**PerceptionSimulation. HeadTrackerMode**

仅定向到头跟踪。 这意味着跟踪的位置可能不可靠，并且某些依赖于头位置的功能可能不可用。

**PerceptionSimulation. HeadTrackerMode. 位置**

位置标题跟踪。 这意味着跟踪的头位置和方向都是可靠的

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>PerceptionSimulation. SimulatedGesture

描述模拟手势

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**PerceptionSimulation. SimulatedGesture**

用于指示没有笔势的 sentinel 值。

**PerceptionSimulation. SimulatedGesture. FingerPressed**

手指按下的手势。

**PerceptionSimulation. SimulatedGesture. FingerReleased**

用手指释放的手势。

**PerceptionSimulation. SimulatedGesture**

Home/system 手势。

**PerceptionSimulation. SimulatedGesture. Max**

最大有效手势。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>PerceptionSimulation. SimulatedSixDofControllerStatus

模拟 6 DOF 控制器的可能状态。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**PerceptionSimulation. SimulatedSixDofControllerStatus。**

6-DOF 控制器已关闭。

**PerceptionSimulation. SimulatedSixDofControllerStatus。**

6-DOF 控制器已打开并进行跟踪。

**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

6-DOF 控制器已打开，但无法跟踪。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>PerceptionSimulation. SimulatedSixDofControllerButton

模拟 6 DOF 控制器上支持的按钮。

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**PerceptionSimulation. SimulatedSixDofControllerButton**

用于指示没有按钮的 sentinel 值。

**PerceptionSimulation. SimulatedSixDofControllerButton**

"主页" 按钮处于按下状态。

**PerceptionSimulation. SimulatedSixDofControllerButton**

按下菜单按钮。

**PerceptionSimulation. SimulatedSixDofControllerButton**

按下 "手柄" 按钮。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

触摸板已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. Select**

按 "选择" 按钮。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

触摸板接触。

**PerceptionSimulation. SimulatedSixDofControllerButton**

已按下操纵杆。

**PerceptionSimulation. SimulatedSixDofControllerButton. Max**

"最大有效" 按钮。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>PerceptionSimulation. SimulatedEyesCalibrationState

模拟眼睛的校准状态

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**PerceptionSimulation. SimulatedEyesCalibrationState. 不可用**

眼睛校准不可用。

**PerceptionSimulation. SimulatedEyesCalibrationState。**

眼睛已经校准。  这是默认值。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

正在校准眼睛。

**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

需要校准眼睛。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>PerceptionSimulation. SimulatedHandJointTrackingAccuracy

手的接点的跟踪准确性。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 不可用**

不会跟踪接头。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

将推断联合位置。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy。**

将完全跟踪联合。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>PerceptionSimulation. SimulatedHandPose

手的接点的跟踪准确性。

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**PerceptionSimulation. SimulatedHandPose. 关闭**

手的 finger 接头被配置为反映闭合的姿势。

**PerceptionSimulation. SimulatedHandPose。**

触接头的配置以反映开放姿势。

**PerceptionSimulation. SimulatedHandPose. 点**

触接头的配置以反映一个指示。

**PerceptionSimulation. SimulatedHandPose**

触接头的配置以反映收缩的姿势。

**PerceptionSimulation. SimulatedHandPose. Max**

SimulatedHandPose 的最大有效值。


### <a name="microsoftperceptionsimulationplaybackstate"></a>PerceptionSimulation. PlaybackState

描述播放的状态。

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**PerceptionSimulation. PlaybackState. 已停止**

录制当前已停止，可供播放。

**PerceptionSimulation. PlaybackState**

当前正在播放记录。

**PerceptionSimulation. PlaybackState. 暂停**

当前已暂停录制。

**PerceptionSimulation. PlaybackState. 结束**

记录已结束。

### <a name="microsoftperceptionsimulationvector3"></a>PerceptionSimulation. System.numerics.vector2

介绍三个组件向量，它可能在三维空间中描述点或向量。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**PerceptionSimulation. System.numerics.vector2. X**

向量的 X 分量。

**PerceptionSimulation. System.numerics.vector2**

向量的 Y 分量。

**PerceptionSimulation. System.numerics.vector2. Z**

向量的 Z 分量。

**PerceptionSimulation (系统) 的 #ctor： single、system.object**

构造一个新的 System.numerics.vector2。

参数
* x-向量的 x 分量。
* y-向量的 y 分量。
* z-矢量的 z 分量。

### <a name="microsoftperceptionsimulationrotation3"></a>PerceptionSimulation. Rotation3

介绍三个组件旋转。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**PerceptionSimulation. Rotation3**

旋转的螺距分量，围绕 X 轴向下旋转。

**PerceptionSimulation. Rotation3. 偏航**

旋转的偏航组件，绕 Y 轴旋转。

**PerceptionSimulation. Rotation3**

围绕 Z 轴旋转的滚动部分。

**Microsoft.PerceptionSimulation.Rotation3.#ctor (System.Single，System.Single，System.Single)**

构造新的 Rotation3。

参数
* pitch - 旋转的间距部分。
* yaw - 旋转的偏偏分量。
* roll - 旋转的滚动组件。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

描述模拟手部联合的配置。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

联合的位置。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

联合的旋转。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

联合的跟踪准确性。


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

描述视图图面，如相机通常使用。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

frustum 中包含的最小距离。

**Microsoft.PerceptionSimulation.Frustum.Far**

frustum 中包含的最大距离。

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

frustum 的水平视场（以弧度 (小于 PI) 。

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

视图水平字段与垂直视图字段的比率。

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration

描述模拟头戴显示设备的配置。

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**

从头部中心到左眼的转换，用于立体声渲染。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**

用于立体声渲染的左眼旋转。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**

从头部中心到右眼的转换，用于立体声渲染。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**

用于立体声渲染的右眼旋转。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**

系统出于立体声渲染目的报告的 Ipd 值。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**

为左眼和右眼转换提供的值是否被视为有效并应用于正在运行的系统。

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**

为 Ipd 提供的值是否应当被视为有效并应用于正在运行的系统。


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

用于生成用于控制设备的数据包的根。

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

检索模拟设备对象，该对象解释模拟人类和模拟世界。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

检索控制模拟人类的对象。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

将模拟重置为默认状态。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

描述设备的接口，用于解释模拟世界和模拟人类

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

从模拟设备检索头跟踪器。

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

从模拟设备检索手部跟踪器。

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType (Microsoft.PerceptionSimulation.SimulatedDeviceType)**

设置模拟设备的属性，以匹配所提供的设备类型。

参数
* type - 模拟设备的新类型

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft.PerceptionSimulation.ISimulatedDevice2

通过将 ISimulatedDevice 强制转换到 ISimulatedDevice2，可以使用其他属性

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**

检索或设置模拟人类是否正在主动戴着头戴显示设备。

**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**

检索或设置模拟显示的属性。

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

描述模拟设备跟踪模拟人类头部的部分的接口。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

检索和设置当前头跟踪器模式。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

描述模拟设备跟踪模拟人类手部部分的接口

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

检索节点相对于世界的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

检索并设置模拟手部跟踪器相对于头部中心的位置。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

检索并设置模拟手部跟踪器向下的间距。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

检索并设置是否忽略模拟手部跟踪器图面。 如果忽略，两手始终可见。 如果未 (，则) 指针仅在手部跟踪器图面内时可见。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

检索并设置用于确定手对模拟手部跟踪器是否可见的 frustum 属性。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

用于控制模拟人类顶级接口。

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

检索并设置节点相对于世界的位置（以米为单位）。 该位置对应于位于人脚中心的点。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

检索并设置模拟人脸在世界上的方向。 0 弧度朝下负 Z 轴。 正弧度围绕 Y 轴顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

检索并设置模拟人类的高度（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

检索模拟人类左侧。

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

检索模拟人类右侧。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

检索模拟人类的头。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move (Microsoft.PerceptionSimulation.Vector3)**

移动模拟人类相对于其当前位置（以米为单位）。

参数
* translation - 相对于当前位置要移动的翻译。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate (System.Single)**

围绕 Y 轴顺时针旋转模拟人类相对于其当前方向

参数
* 弧度 - 围绕 Y 轴旋转的量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

通过将 ISimulatedHuman 强制转换到 ISimulatedHuman2，可以使用其他属性

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

检索左侧 6 DOF 控制器。

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

检索正确的 6-DOF 控制器。


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

描述模拟人类手的界面

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

检索节点相对于世界的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

检索并设置模拟手相对于人类的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

检索并设置当前是否激活手部。

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

检索 Hand 当前是否对 SimulatedDevice (可见，即，手是否处于 HandTracker) 。

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

移动手，使它对 SimulatedDevice 可见。

**Microsoft.PerceptionSimulation.ISimulatedHand.Move (Microsoft.PerceptionSimulation.Vector3)**

移动模拟手相对于其当前位置的位置（以米为单位）。

参数
* translation - 要翻译模拟手的量。

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture (Microsoft.PerceptionSimulation.SimulatedGesture)**

使用模拟手执行手势。  只有启用手部时，系统才能检测到它。

参数
* 笔势 - 要执行的操作笔势。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

通过强制将 ISimulatedHand 强制转换到 ISimulatedHand2，可以使用其他属性。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

检索或设置模拟手的旋转。  沿轴查看时，正弧度沿顺时针旋转。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

通过强制将 ISimulatedHand 强制转换到 ISimulatedHand3，可以使用其他属性
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

获取指定联合的联合配置。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

为指定的联合设置联合配置。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

将手部设置为具有可选标志的已知姿势进行动画处理。  注意：进行动画处理不会立即反映其最终联合配置。


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

描述模拟人类头部的接口。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

检索节点相对于世界的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

检索模拟头部的旋转。 沿轴查看时，正弧度沿顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

检索模拟头部的孔。 此值用于确定头部的中心旋转点 (旋转) 。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate (Microsoft.PerceptionSimulation.Rotation3)**

相对于其当前旋转旋转模拟的头。 沿轴查看时，正弧度沿顺时针旋转。

参数
* rotation - 要旋转的量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

通过强制将 ISimulatedHead 强制转换到 ISimulatedHead2，可以使用其他属性

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

检索模拟人类眼睛。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

描述与模拟人类关联的 6 DOF 控制器的接口。

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

检索节点相对于世界的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

检索或设置控制器的当前状态。  控制器状态必须设置为"关闭"值，然后才能成功调用移动、旋转或按下按钮。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

检索或设置模拟控制器相对于人类的位置（以米为单位）。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

检索或设置模拟控制器的方向。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move (Microsoft.PerceptionSimulation.Vector3)**

移动模拟控制器相对于其当前位置的位置（以米为单位）。

参数
* translation - 要转换模拟控制器的数量。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton (SimulatedSixDofControllerButton)**

按模拟控制器上的按钮。  只有启用控制器后，系统才能检测到它。

参数
* 按钮 - 要按下的按钮。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton (SimulatedSixDofControllerButton)**

释放模拟控制器上的按钮。  只有启用控制器后，系统才能检测到它。

参数
* 按钮 - 要释放的按钮。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (float，out float)**

获取模拟控制器触摸板上模拟手指的位置。

参数
* x - 手指的水平位置。
* y - 手指的垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition (float、float)**

设置模拟手指在模拟控制器的触摸板上的位置。

参数
* x - 手指的水平位置。
* y - 手指的垂直位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

将 ISimulatedSixDofController 强制转换到 ISimulatedSixDofController2，可以使用其他属性和方法

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (float，out float)**

获取模拟控制器上模拟指纹的位置。

参数
* x - 滚动块的水平位置。
* y - 滚动块的垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition (float、float)**

设置模拟控制器上模拟指纹的位置。

参数
* x - 滚动块的水平位置。
* y - 滚动块的垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

检索或设置模拟控制器的电池电量。  该值必须大于 0.0 且小于或等于 100.0。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

描述模拟人类眼睛的界面。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

检索模拟眼睛的旋转。 沿轴查看时，正弧度沿顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate (Microsoft.PerceptionSimulation.Rotation3)**

相对于其当前旋转旋转模拟眼睛。 沿轴查看时，正弧度沿顺时针旋转。

参数
* rotation - 要旋转的量。

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

检索或设置模拟眼睛的校准状态。

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

检索节点相对于世界的位置（以米为单位）。


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

用于与加载用于播放的单个录制进行交互的接口。

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

检索记录中的数据类型列表。

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

检索记录的当前状态。

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

开始播放。 如果录制暂停，则播放会从暂停的位置恢复;如果停止，播放会从开头开始。 如果已在播放，则忽略此调用。

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

暂停当前位置的播放。 如果录制已停止，则忽略调用。

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek (System.UInt64)**

以 100 纳秒 (以 100 纳秒为间隔查找到指定时间间隔的录制) 该位置暂停。 如果时间超出录制结束时间，则它会暂停到最后一帧。

参数
* 刻度 - 要查找的时间。

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

停止播放，将位置重置为开头。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

用于接收播放期间状态更改的接口。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged (Microsoft.PerceptionSimulation.PlaybackState)**

当 ISimulationRecording 的播放状态发生更改时调用。

参数
* newState - 记录的新状态。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

用于创建感知模拟对象的根对象。

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager (Microsoft.PerceptionSimulation.ISimulationStreamSink)**

在 对象上创建 ，用于生成模拟数据包，并传送它们到提供的接收器。

参数
* sink - 将接收所有生成的数据包的接收器。

返回值

创建的管理器。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording (System.String)**

创建接收器，该接收器将接收到的所有数据包存储在指定路径的文件中。

参数
* path - 要创建的文件的路径。

返回值

创建的接收器。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String，Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

从指定文件加载记录。

参数
* path - 要加载的文件的路径。
* factory - 记录用于创建 ISimulationStreamSink（如果需要）的工厂。

返回值

加载的记录。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String，Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

从指定文件加载记录。

参数
* path - 要加载的文件的路径。
* factory - 记录用于创建 ISimulationStreamSink（如果需要）的工厂。
* callback - 一个回调，接收重新升级录制状态的更新。

返回值

加载的记录。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

描述不同类型的流数据。

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

用于指示无流数据类型的 sentinel 值。

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

头部位置和方向的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

手的位置和手势的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

用于环境的空间映射的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

用于设备校准的数据流。 校准数据包仅由远程模式下的系统接受。

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

设备环境的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**

运动控制器的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**

模拟人类眼睛的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**

具有设备的显示配置的数据流。

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

一个 sentinel 值，该值用于指示所有记录的数据类型。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

从模拟流接收数据包的对象。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (uint length， byte[] packet)**

接收单个数据包，该数据包在内部类型化且版本控制。

参数
* length - 数据包的长度。
* packet - 数据包的数据。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

创建 ISimulationStreamSink 的对象。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink ()**

创建 ISimulationStreamSink 的单个实例。

返回值

创建的接收器。
