---
title: 感知模拟
description: 使用感知模拟库自动完成沉浸式应用程序模拟输入的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens，模拟，测试
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530394"
---
# <a name="perception-simulation"></a><span data-ttu-id="9a9a4-104">感知模拟</span><span class="sxs-lookup"><span data-stu-id="9a9a4-104">Perception simulation</span></span>

<span data-ttu-id="9a9a4-105">是否要为应用生成自动测试？</span><span class="sxs-lookup"><span data-stu-id="9a9a4-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="9a9a4-106">是否希望你的测试超出组件级别的单元测试，并真正运用端到端应用？</span><span class="sxs-lookup"><span data-stu-id="9a9a4-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="9a9a4-107">感知模拟是你要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="9a9a4-108">感知模拟库将人类和世界输入数据发送到你的应用，因此你可以自动执行测试。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="9a9a4-109">例如，可以模拟查找特定的可重复位置的人工输入，然后使用笔势或运动控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="9a9a4-110">感知模拟可以将此类模拟输入发送到物理 HoloLens，HoloLens 模拟器 (第一代) 、HoloLens 2 模拟器或安装有混合现实门户的 PC。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="9a9a4-111">感知模拟会绕过混合现实设备上的实时传感器，并将模拟输入发送到设备上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="9a9a4-112">应用程序通过它们始终使用的相同 Api 来接收这些输入事件，无法判断运行与感知模拟之间的差异。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="9a9a4-113">认知模拟是将模拟输入发送到 HoloLens 虚拟机所使用的一种技术。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="9a9a4-114">若要开始在代码中使用模拟，请首先创建 IPerceptionSimulationManager 对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="9a9a4-115">在该对象中，可以发出命令来控制模拟 "人体" 的属性，包括头位置、手形位置和手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="9a9a4-116">还可以启用和操作运动控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="9a9a4-117">设置用于感知模拟的 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="9a9a4-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="9a9a4-118">在开发电脑上[安装 HoloLens 模拟器](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="9a9a4-119">模拟器包含用于感知模拟的库。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="9a9a4-120">创建新的 Visual Studio c # 桌面项目 (控制台项目非常适合) 入门。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="9a9a4-121">将以下二进制文件添加到项目中，作为 (项目->添加 >引用 ... ) 中的引用。可以在% ProgramFiles (x86) % \ Microsoft XDE \\ () 版本中找到它们，例如，为 HoloLens 2 模拟器% **ProgramFiles (x86) % \ microsoft XDE \\ 10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="9a9a4-122"> (注意：尽管二进制文件是 HoloLens 2 模拟器的一部分，但它们也适用于桌面上的 Windows Mixed Reality。 ) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="9a9a4-123">用于感知模拟的 PerceptionSimulationManager.Interop.dll 托管 c # 包装。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="9a9a4-124">b.</span><span class="sxs-lookup"><span data-stu-id="9a9a4-124">b.</span></span> <span data-ttu-id="9a9a4-125">用于设置到 HoloLens 或仿真程序的 web 套接字通信通道的 PerceptionSimulationRest.dll 库。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="9a9a4-126">c.</span><span class="sxs-lookup"><span data-stu-id="9a9a4-126">c.</span></span> <span data-ttu-id="9a9a4-127">用于模拟 SimulationStream.Interop.dll 共享的类型。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="9a9a4-128">将实现二进制 PerceptionSimulationManager.dll 添加到项目 a。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="9a9a4-129">首先将它作为二进制添加到项目 (项目->添加 >的现有项 ... ) 。将其保存为链接，使其不会将其复制到项目源文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="9a9a4-130">![将 PerceptionSimulationManager.dll 作为链接 b 添加到项目 ](images/saveaslink.png) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="9a9a4-131">然后，确保它在生成时复制到输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="9a9a4-132">这位于二进制文件的属性表中。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="9a9a4-133">![将 PerceptionSimulationManager.dll 标记为复制到输出目录](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="9a9a4-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="9a9a4-134">将活动解决方案平台设置为 x64。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="9a9a4-135"> (使用 Configuration Manager 为 x64 创建平台项（如果尚不存在）。 ) </span><span class="sxs-lookup"><span data-stu-id="9a9a4-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="9a9a4-136">创建 IPerceptionSimulation Manager 对象</span><span class="sxs-lookup"><span data-stu-id="9a9a4-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="9a9a4-137">若要控制模拟，你将对从 IPerceptionSimulationManager 对象检索到的对象进行更新。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="9a9a4-138">第一步是获取该对象，并将其连接到目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="9a9a4-139">可以通过单击[工具栏](using-the-hololens-emulator.md)中的 "设备门户" 按钮来获取仿真程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="9a9a4-140">![打开设备门户图标 ](images/emulator-deviceportal.png) **打开设备门户**：在模拟器中打开用于 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="9a9a4-141">对于 Windows Mixed Reality，可以在 "设置" 应用程序中的 "更新 & 安全性" 下检索此项，然后在 "启用设备门户" 下的 "连接使用：" 部分中的 "开发人员"。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="9a9a4-142">请务必记下 IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="9a9a4-143">首先，调用 RestSimulationStreamSink 来获取 RestSimulationStreamSink 对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="9a9a4-144">这是你将通过 http 连接控制的目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="9a9a4-145">命令将传递到设备或模拟器上运行的 [Windows 设备门户](using-the-windows-device-portal.md) 并进行处理。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="9a9a4-146">创建对象需要四个参数：</span><span class="sxs-lookup"><span data-stu-id="9a9a4-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="9a9a4-147">Uri uri-目标设备的 IP 地址 (例如，" https://123.123.123.123 " 或 " https://123.123.123.123:50080 " ) </span><span class="sxs-lookup"><span data-stu-id="9a9a4-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="9a9a4-148">系统 NetworkCredential 凭据-用于在目标设备或模拟器上连接到 [Windows 设备门户](using-the-windows-device-portal.md) 的用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="9a9a4-149">如果是通过其本地地址连接到模拟器 (例如，168。*.*.\* ) 在同一台计算机上，将接受任何凭据。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="9a9a4-150">布尔标准-对于普通优先级为 True，低优先级为 false。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="9a9a4-151">通常，你需要将此值设置为 *true* ，以便测试方案允许你的测试进行控制。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="9a9a4-152">仿真程序和 Windows Mixed Reality 模拟使用低优先级连接。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="9a9a4-153">如果你的测试也使用低优先级连接，则最新建立的连接将处于控制之下。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="9a9a4-154">CancellationToken 标记-用于取消异步操作的标记。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="9a9a4-155">其次，你将创建 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="9a9a4-156">这是用于控制模拟的对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="9a9a4-157">还必须在异步方法中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="9a9a4-158">控制模拟的人工</span><span class="sxs-lookup"><span data-stu-id="9a9a4-158">Control the simulated Human</span></span>

<span data-ttu-id="9a9a4-159">IPerceptionSimulationManager 具有返回 ISimulatedHuman 对象的人属性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="9a9a4-160">若要控制模拟人力，请对此对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="9a9a4-161">例如：</span><span class="sxs-lookup"><span data-stu-id="9a9a4-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="9a9a4-162">基本示例 c # 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="9a9a4-162">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="9a9a4-163">扩展的示例 c # 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="9a9a4-163">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="9a9a4-164">DOF 控制器上的注意事项</span><span class="sxs-lookup"><span data-stu-id="9a9a4-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="9a9a4-165">在模拟 DOF 控制器上调用方法的任何属性之前，必须激活控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="9a9a4-166">如果不这样做，将导致异常。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="9a9a4-167">从 Windows 10 可能2019更新开始，可以通过将 ISimulatedSixDofController 对象的 Status 属性设置为 SimulatedSixDofControllerStatus，来安装和激活模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="9a9a4-168">在 Windows 10 2018 10 月版更新及更早版本中，必须先通过调用 \Windows\System32 文件夹中的 PerceptionSimulationDevice 工具单独安装模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="9a9a4-169">此工具的用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a9a4-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="9a9a4-170">例如</span><span class="sxs-lookup"><span data-stu-id="9a9a4-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="9a9a4-171">支持的操作包括：</span><span class="sxs-lookup"><span data-stu-id="9a9a4-171">Supported actions are:</span></span>
* <span data-ttu-id="9a9a4-172">i = 安装</span><span class="sxs-lookup"><span data-stu-id="9a9a4-172">i = install</span></span>
* <span data-ttu-id="9a9a4-173">q = 查询</span><span class="sxs-lookup"><span data-stu-id="9a9a4-173">q = query</span></span>
* <span data-ttu-id="9a9a4-174">r = 删除</span><span class="sxs-lookup"><span data-stu-id="9a9a4-174">r = remove</span></span>

<span data-ttu-id="9a9a4-175">支持的实例包括：</span><span class="sxs-lookup"><span data-stu-id="9a9a4-175">Supported instances are:</span></span>
* <span data-ttu-id="9a9a4-176">1 = 左 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="9a9a4-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="9a9a4-177">2 = 右 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="9a9a4-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="9a9a4-178">该进程的退出代码将指示成功 (零返回值) 或 (非零返回值) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="9a9a4-179">当使用 "q" 操作来查询控制器是否已安装时，如果未安装控制器，则返回值将为零 (0) 如果控制器已安装，则返回 (1) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="9a9a4-180">在 Windows 10 2018 10 月更新版或更早版本上删除控制器时，请先通过 API 将其状态设置为 Off，然后调用 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="9a9a4-181">必须以管理员身份运行此工具。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="9a9a4-182">API 参考</span><span class="sxs-lookup"><span data-stu-id="9a9a4-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="9a9a4-183">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="9a9a4-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="9a9a4-184">描述模拟设备类型</span><span class="sxs-lookup"><span data-stu-id="9a9a4-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="9a9a4-185">**PerceptionSimulation. SimulatedDeviceType. 引用**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="9a9a4-186">虚构引用设备，PerceptionSimulationManager 的默认值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="9a9a4-187">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="9a9a4-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="9a9a4-188">描述 head 跟踪器模式</span><span class="sxs-lookup"><span data-stu-id="9a9a4-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="9a9a4-189">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="9a9a4-190">默认标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-190">Default Head Tracking.</span></span> <span data-ttu-id="9a9a4-191">这意味着系统可能会根据运行时条件选择最佳的标题跟踪模式。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="9a9a4-192">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="9a9a4-193">仅定向到头跟踪。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="9a9a4-194">这意味着跟踪的位置可能不可靠，并且某些依赖于头位置的功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="9a9a4-195">**PerceptionSimulation. HeadTrackerMode. 位置**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="9a9a4-196">位置标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-196">Positional Head Tracking.</span></span> <span data-ttu-id="9a9a4-197">这意味着跟踪的头位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="9a9a4-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="9a9a4-198">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="9a9a4-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="9a9a4-199">描述模拟手势</span><span class="sxs-lookup"><span data-stu-id="9a9a4-199">Describes a simulated gesture</span></span>

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

<span data-ttu-id="9a9a4-200">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="9a9a4-201">用于指示没有笔势的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="9a9a4-202">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="9a9a4-203">手指按下的手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-203">A finger pressed gesture.</span></span>

<span data-ttu-id="9a9a4-204">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="9a9a4-205">用手指释放的手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-205">A finger released gesture.</span></span>

<span data-ttu-id="9a9a4-206">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="9a9a4-207">Home/system 手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-207">The home/system gesture.</span></span>

<span data-ttu-id="9a9a4-208">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="9a9a4-209">最大有效手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="9a9a4-210">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="9a9a4-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="9a9a4-211">模拟 6 DOF 控制器的可能状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="9a9a4-212">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="9a9a4-213">6-DOF 控制器已关闭。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="9a9a4-214">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="9a9a4-215">6-DOF 控制器已打开并进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="9a9a4-216">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="9a9a4-217">6-DOF 控制器已打开，但无法跟踪。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="9a9a4-218">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="9a9a4-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="9a9a4-219">模拟 6 DOF 控制器上支持的按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-219">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="9a9a4-220">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="9a9a4-221">用于指示没有按钮的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="9a9a4-222">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="9a9a4-223">"主页" 按钮处于按下状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-223">The Home button is pressed.</span></span>

<span data-ttu-id="9a9a4-224">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="9a9a4-225">按下菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-225">The Menu button is pressed.</span></span>

<span data-ttu-id="9a9a4-226">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="9a9a4-227">按下 "手柄" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-227">The Grip button is pressed.</span></span>

<span data-ttu-id="9a9a4-228">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="9a9a4-229">触摸板已按下。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="9a9a4-230">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="9a9a4-231">按 "选择" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-231">The Select button is pressed.</span></span>

<span data-ttu-id="9a9a4-232">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="9a9a4-233">触摸板接触。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-233">The TouchPad is touched.</span></span>

<span data-ttu-id="9a9a4-234">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="9a9a4-235">已按下操纵杆。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="9a9a4-236">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="9a9a4-237">"最大有效" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="9a9a4-238">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="9a9a4-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="9a9a4-239">模拟眼睛的校准状态</span><span class="sxs-lookup"><span data-stu-id="9a9a4-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="9a9a4-240">**PerceptionSimulation. SimulatedEyesCalibrationState. 不可用**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="9a9a4-241">眼睛校准不可用。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="9a9a4-242">**PerceptionSimulation. SimulatedEyesCalibrationState。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="9a9a4-243">眼睛已经校准。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="9a9a4-244">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-244">This is the default value.</span></span>

<span data-ttu-id="9a9a4-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="9a9a4-246">正在校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="9a9a4-247">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="9a9a4-248">需要校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="9a9a4-249">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="9a9a4-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="9a9a4-250">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="9a9a4-251">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 不可用**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="9a9a4-252">不会跟踪接头。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-252">The joint isn't tracked.</span></span>

<span data-ttu-id="9a9a4-253">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="9a9a4-254">将推断联合位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-254">The joint position is inferred.</span></span>

<span data-ttu-id="9a9a4-255">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="9a9a4-256">将完全跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="9a9a4-257">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="9a9a4-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="9a9a4-258">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-258">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="9a9a4-259">**PerceptionSimulation. SimulatedHandPose. 关闭**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="9a9a4-260">手的 finger 接头被配置为反映闭合的姿势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="9a9a4-261">**PerceptionSimulation. SimulatedHandPose。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="9a9a4-262">触接头的配置以反映开放姿势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="9a9a4-263">**PerceptionSimulation. SimulatedHandPose. 点**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="9a9a4-264">触接头的配置以反映一个指示。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="9a9a4-265">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="9a9a4-266">触接头的配置以反映收缩的姿势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="9a9a4-267">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="9a9a4-268">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="9a9a4-269">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="9a9a4-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="9a9a4-270">描述播放的状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="9a9a4-271">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="9a9a4-272">录制当前已停止，可供播放。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="9a9a4-273">**PerceptionSimulation. PlaybackState**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="9a9a4-274">当前正在播放记录。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-274">The recording is currently playing.</span></span>

<span data-ttu-id="9a9a4-275">**PerceptionSimulation. PlaybackState. 暂停**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="9a9a4-276">当前已暂停录制。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-276">The recording is currently paused.</span></span>

<span data-ttu-id="9a9a4-277">**PerceptionSimulation. PlaybackState. 结束**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="9a9a4-278">记录已结束。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="9a9a4-279">PerceptionSimulation. System.numerics.vector2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="9a9a4-280">介绍三个组件向量，它可能在三维空间中描述点或向量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="9a9a4-281">**PerceptionSimulation. System.numerics.vector2. X**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="9a9a4-282">向量的 X 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-282">The X component of the vector.</span></span>

<span data-ttu-id="9a9a4-283">**PerceptionSimulation. System.numerics.vector2**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="9a9a4-284">向量的 Y 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-284">The Y component of the vector.</span></span>

<span data-ttu-id="9a9a4-285">**PerceptionSimulation. System.numerics.vector2. Z**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="9a9a4-286">向量的 Z 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-286">The Z component of the vector.</span></span>

<span data-ttu-id="9a9a4-287">**PerceptionSimulation (系统) 的 #ctor： single、system.object**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="9a9a4-288">构造一个新的 System.numerics.vector2。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-288">Construct a new Vector3.</span></span>

<span data-ttu-id="9a9a4-289">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-289">Parameters</span></span>
* <span data-ttu-id="9a9a4-290">x-向量的 x 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="9a9a4-291">y-向量的 y 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="9a9a4-292">z-矢量的 z 分量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="9a9a4-293">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="9a9a4-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="9a9a4-294">介绍三个组件旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="9a9a4-295">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="9a9a4-296">旋转的螺距分量，围绕 X 轴向下旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="9a9a4-297">**PerceptionSimulation. Rotation3. 偏航**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="9a9a4-298">旋转的偏航组件，绕 Y 轴旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="9a9a4-299">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="9a9a4-300">围绕 Z 轴旋转的滚动部分。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="9a9a4-301">**PerceptionSimulation (系统) 的 #ctor： single、system.object**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="9a9a4-302">构造一个新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="9a9a4-303">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-303">Parameters</span></span>
* <span data-ttu-id="9a9a4-304">螺距-旋转的螺距部分。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="9a9a4-305">偏航-旋转的偏航组件。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="9a9a4-306">滚动-旋转的滚动组件。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="9a9a4-307">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a9a4-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="9a9a4-308">描述模拟手上的接点配置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="9a9a4-309">**PerceptionSimulation. SimulatedHandJointConfiguration. 位置**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="9a9a4-310">接点的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-310">The position of the joint.</span></span>

<span data-ttu-id="9a9a4-311">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="9a9a4-312">接点的旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-312">The rotation of the joint.</span></span>

<span data-ttu-id="9a9a4-313">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="9a9a4-314">联合的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="9a9a4-315">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="9a9a4-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="9a9a4-316">描述通常由相机使用的视图（如）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="9a9a4-317">**PerceptionSimulation。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="9a9a4-318">在锥上包含的最小距离。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="9a9a4-319">**PerceptionSimulation. Far**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="9a9a4-320">在锥中包含的最大距离。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="9a9a4-321">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="9a9a4-322">以弧度表示的（以弧度表示）的水平字段 (小于 PI) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="9a9a4-323">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="9a9a4-324">视图的水平字段与视图的垂直字段的比率。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="9a9a4-325">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a9a4-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="9a9a4-326">描述模拟耳机显示的配置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-326">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="9a9a4-327">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="9a9a4-328">从头部中心到左边的转换是为了实现立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="9a9a4-329">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="9a9a4-330">用于立体声呈现的左侧方式的旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="9a9a4-331">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="9a9a4-332">从头部中心到正确眼睛的转换是为了实现立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="9a9a4-333">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="9a9a4-334">为了实现立体声渲染，正确的眼睛旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="9a9a4-335">**PerceptionSimulation. SimulatedDisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="9a9a4-336">系统报告的 Ipd 值用于立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="9a9a4-337">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="9a9a4-338">为左和右眼转换提供的值是否应视为有效且应用于正在运行的系统。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="9a9a4-339">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="9a9a4-340">为 Ipd 提供的值是否应视为有效，并将其应用于正在运行的系统。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="9a9a4-341">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="9a9a4-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="9a9a4-342">用于生成用于控制设备的数据包的根。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="9a9a4-343">**PerceptionSimulation. IPerceptionSimulationManager. 设备**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="9a9a4-344">检索用于解释模拟人类和模拟世界的模拟设备对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="9a9a4-345">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="9a9a4-346">检索控制模拟人的对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="9a9a4-347">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="9a9a4-348">将模拟重置为其默认状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="9a9a4-349">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="9a9a4-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="9a9a4-350">描述设备的接口，该设备解释模拟世界和模拟人类</span><span class="sxs-lookup"><span data-stu-id="9a9a4-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="9a9a4-351">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="9a9a4-352">从模拟设备检索 Head 跟踪器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="9a9a4-353">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="9a9a4-354">从模拟设备检索手动跟踪器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="9a9a4-355">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="9a9a4-356">设置模拟设备的属性，使其与所提供的设备类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="9a9a4-357">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-357">Parameters</span></span>
* <span data-ttu-id="9a9a4-358">类型-新类型的模拟设备</span><span class="sxs-lookup"><span data-stu-id="9a9a4-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="9a9a4-359">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="9a9a4-360">可以通过将 ISimulatedDevice 转换为 ISimulatedDevice2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="9a9a4-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="9a9a4-361">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="9a9a4-362">检索或设置模拟人力是否正在积极地戴上耳机。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="9a9a4-363">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="9a9a4-364">检索或设置模拟的显示的属性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="9a9a4-365">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="9a9a4-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="9a9a4-366">描述模拟设备的部分的接口，该部分跟踪模拟人的头。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="9a9a4-367">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="9a9a4-368">检索和设置当前 head 跟踪器模式。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="9a9a4-369">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="9a9a4-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="9a9a4-370">描述模拟设备的部分的接口，该部分跟踪模拟人的手</span><span class="sxs-lookup"><span data-stu-id="9a9a4-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="9a9a4-371">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-372">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="9a9a4-373">**PerceptionSimulation. ISimulatedHandTracker. 位置**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="9a9a4-374">检索和设置模拟手型跟踪器的位置（相对于打印头的中心）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="9a9a4-375">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="9a9a4-376">检索和设置模拟手型跟踪器的下间距。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="9a9a4-377">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="9a9a4-378">检索和设置是否忽略模拟手动跟踪器的 "截锥"。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="9a9a4-379">如果忽略，则这两个指针始终可见。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="9a9a4-380">当未被忽略时 (默认) 只是在 "手形跟踪器" 中的</span><span class="sxs-lookup"><span data-stu-id="9a9a4-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="9a9a4-381">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="9a9a4-382">检索和设置用来确定是否对模拟手型跟踪器可见的被截锥属性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="9a9a4-383">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="9a9a4-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="9a9a4-384">用于控制模拟人的顶级接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-384">Top-level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="9a9a4-385">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-386">检索和设置与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="9a9a4-387">此位置对应于人脚的中心点。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="9a9a4-388">**PerceptionSimulation. ISimulatedHuman。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="9a9a4-389">检索和设置模拟人脸在世界中的方向。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="9a9a4-390">0弧度朝下 Z 轴向下。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="9a9a4-391">正弧度围绕 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="9a9a4-392">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="9a9a4-393">检索和设置模拟人的高度（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="9a9a4-394">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="9a9a4-395">检索模拟人的左侧。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="9a9a4-396">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="9a9a4-397">检索模拟人的右边。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="9a9a4-398">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="9a9a4-399">检索模拟人的 head。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="9a9a4-400">**PerceptionSimulation (System.numerics.vector2) （ISimulatedHuman）**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="9a9a4-401">以米为单位移动模拟人工相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="9a9a4-402">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-402">Parameters</span></span>
* <span data-ttu-id="9a9a4-403">平移-要移动的转换，相对于当前位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="9a9a4-404">**PerceptionSimulation () 中的 ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="9a9a4-405">围绕 Y 轴顺时针旋转模拟人工相对于其当前方向</span><span class="sxs-lookup"><span data-stu-id="9a9a4-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="9a9a4-406">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-406">Parameters</span></span>
* <span data-ttu-id="9a9a4-407">radians-绕 Y 轴旋转的量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="9a9a4-408">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="9a9a4-409">可以通过将 ISimulatedHuman 转换为 ISimulatedHuman2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="9a9a4-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="9a9a4-410">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="9a9a4-411">检索左 6-DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="9a9a4-412">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="9a9a4-413">检索正确的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="9a9a4-414">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="9a9a4-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="9a9a4-415">描述模拟人类</span><span class="sxs-lookup"><span data-stu-id="9a9a4-415">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="9a9a4-416">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-417">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="9a9a4-418">**PerceptionSimulation. ISimulatedHand. 位置**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="9a9a4-419">检索和设置模拟手型相对于人类的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="9a9a4-420">**PerceptionSimulation. ISimulatedHand. 已激活**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="9a9a4-421">检索和设置当前是否已激活该手型。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="9a9a4-422">**PerceptionSimulation. ISimulatedHand。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="9a9a4-423">检索当前是否对 SimulatedDevice (可见，即，该手形是否位于 HandTracker) 检测到的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="9a9a4-424">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="9a9a4-425">移动手使其对 SimulatedDevice 可见。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="9a9a4-426">**PerceptionSimulation (System.numerics.vector2) （ISimulatedHand）**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="9a9a4-427">以米为单位移动模拟手型相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="9a9a4-428">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-428">Parameters</span></span>
* <span data-ttu-id="9a9a4-429">翻译-模拟手的平移量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="9a9a4-430">**PerceptionSimulation. ISimulatedHand. PerformGesture (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="9a9a4-431">使用模拟手执行手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="9a9a4-432">只有在启用了该功能的情况，系统才会检测到它。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="9a9a4-433">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-433">Parameters</span></span>
* <span data-ttu-id="9a9a4-434">手势-要执行的手势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="9a9a4-435">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="9a9a4-436">可以通过将 ISimulatedHand 转换为 ISimulatedHand2 来获取其他属性。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="9a9a4-437">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="9a9a4-438">检索或设置模拟手的旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="9a9a4-439">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="9a9a4-440">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="9a9a4-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="9a9a4-441">可以通过将 ISimulatedHand 转换为 ISimulatedHand3 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="9a9a4-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="9a9a4-442">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="9a9a4-443">获取指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="9a9a4-444">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="9a9a4-445">设置指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="9a9a4-446">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="9a9a4-447">使用可选的动画标志将手设置为已知姿势。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="9a9a4-448">注意：动画效果不会立即反映其最终的联合配置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="9a9a4-449">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="9a9a4-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="9a9a4-450">描述模拟人的头的接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="9a9a4-451">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-452">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="9a9a4-453">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="9a9a4-454">检索模拟头部的旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="9a9a4-455">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="9a9a4-456">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="9a9a4-457">检索模拟头直径。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="9a9a4-458">此值用于确定 head 中心 (旋转点) 。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="9a9a4-459">**PerceptionSimulation (Rotation3) （ISimulatedHead）**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="9a9a4-460">相对于当前旋转旋转模拟头。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="9a9a4-461">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="9a9a4-462">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-462">Parameters</span></span>
* <span data-ttu-id="9a9a4-463">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="9a9a4-464">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="9a9a4-465">可以通过将 ISimulatedHead 转换为 ISimulatedHead2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="9a9a4-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="9a9a4-466">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="9a9a4-467">检索模拟人的眼睛。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="9a9a4-468">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="9a9a4-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="9a9a4-469">描述与模拟人类关联的 6 DOF 控制器的接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="9a9a4-470">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-471">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="9a9a4-472">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="9a9a4-473">检索或设置控制器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="9a9a4-474">在移动、旋转或按下按钮的任何调用都将成功之前，控制器状态必须设置为 Off 以外的值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="9a9a4-475">**PerceptionSimulation. ISimulatedSixDofController. 位置**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="9a9a4-476">检索或设置模拟控制器相对于人类的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="9a9a4-477">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="9a9a4-478">检索或设置模拟控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="9a9a4-479">**PerceptionSimulation (System.numerics.vector2) （ISimulatedSixDofController）**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="9a9a4-480">移动模拟控制器相对于其当前位置的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="9a9a4-481">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-481">Parameters</span></span>
* <span data-ttu-id="9a9a4-482">翻译-模拟控制器的平移量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="9a9a4-483">**PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="9a9a4-484">按模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="9a9a4-485">仅当控制器已启用时，系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="9a9a4-486">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-486">Parameters</span></span>
* <span data-ttu-id="9a9a4-487">按钮-要按下的按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-487">button - The button to press.</span></span>

<span data-ttu-id="9a9a4-488">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="9a9a4-489">释放模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="9a9a4-490">仅当控制器已启用时，系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="9a9a4-491">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-491">Parameters</span></span>
* <span data-ttu-id="9a9a4-492">按钮-要释放的按钮。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-492">button - The button to release.</span></span>

<span data-ttu-id="9a9a4-493">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out、out float)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="9a9a4-494">获取模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="9a9a4-495">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-495">Parameters</span></span>
* <span data-ttu-id="9a9a4-496">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="9a9a4-497">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="9a9a4-498">**SetTouchpadPosition (float，float)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="9a9a4-499">设置模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="9a9a4-500">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-500">Parameters</span></span>
* <span data-ttu-id="9a9a4-501">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="9a9a4-502">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="9a9a4-503">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="9a9a4-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="9a9a4-504">可以通过将 ISimulatedSixDofController 转换为 ISimulatedSixDofController2 来提供其他属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="9a9a4-505">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out、out float)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="9a9a4-506">获取模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="9a9a4-507">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-507">Parameters</span></span>
* <span data-ttu-id="9a9a4-508">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="9a9a4-509">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="9a9a4-510">**SetThumbstickPosition (float，float)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="9a9a4-511">设置模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="9a9a4-512">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-512">Parameters</span></span>
* <span data-ttu-id="9a9a4-513">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="9a9a4-514">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="9a9a4-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="9a9a4-516">检索或设置模拟控制器的电池电量级别。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="9a9a4-517">该值必须大于0.0 且小于或等于100.0。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="9a9a4-518">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="9a9a4-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="9a9a4-519">描述模拟人力的眼睛的接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="9a9a4-520">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="9a9a4-521">检索模拟眼睛的旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="9a9a4-522">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="9a9a4-523">**PerceptionSimulation (Rotation3) （ISimulatedEyes）**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="9a9a4-524">相对于当前旋转旋转模拟眼睛。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="9a9a4-525">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="9a9a4-526">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-526">Parameters</span></span>
* <span data-ttu-id="9a9a4-527">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="9a9a4-528">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="9a9a4-529">检索或设置模拟眼睛的校准状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="9a9a4-530">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="9a9a4-531">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="9a9a4-532">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="9a9a4-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="9a9a4-533">用于与为播放加载的单个录制交互的接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-533">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="9a9a4-534">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="9a9a4-535">检索记录中数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="9a9a4-536">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="9a9a4-537">检索当前记录的状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="9a9a4-538">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="9a9a4-539">开始播放。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-539">Start the playback.</span></span> <span data-ttu-id="9a9a4-540">如果记录已暂停，播放将从暂停位置恢复;如果停止，则将从开始处开始播放。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="9a9a4-541">如果已播放，则忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="9a9a4-542">**PerceptionSimulation. ISimulationRecording. 暂停**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="9a9a4-543">暂停播放当前位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="9a9a4-544">如果记录已停止，则调用将被忽略。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="9a9a4-545">**PerceptionSimulation () 中的 ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="9a9a4-546">将记录查找到指定时间 (以 100-纳秒为间隔，从开始) 到该位置暂停。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="9a9a4-547">如果该时间超出了记录的结束时间，则会在最后一帧暂停该时间。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="9a9a4-548">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-548">Parameters</span></span>
* <span data-ttu-id="9a9a4-549">计时周期-要查找的时间。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="9a9a4-550">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="9a9a4-551">停止播放并将位置重置为开始位置。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="9a9a4-552">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="9a9a4-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="9a9a4-553">用于在播放期间接收状态更改的接口。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="9a9a4-554">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="9a9a4-555">当 ISimulationRecording 的播放状态发生更改时调用。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="9a9a4-556">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-556">Parameters</span></span>
* <span data-ttu-id="9a9a4-557">newState-记录的新状态。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="9a9a4-558">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="9a9a4-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="9a9a4-559">用于创建感知模拟对象的根对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="9a9a4-560">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="9a9a4-561">针对生成模拟包并将其传送到所提供接收器的对象创建。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="9a9a4-562">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-562">Parameters</span></span>
* <span data-ttu-id="9a9a4-563">sink-接收所有生成的数据包的接收器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="9a9a4-564">返回值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-564">Return value</span></span>

<span data-ttu-id="9a9a4-565">创建的管理器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-565">The created Manager.</span></span>

<span data-ttu-id="9a9a4-566">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording ()**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="9a9a4-567">创建接收器，将所有接收的数据包存储在文件中的指定路径。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="9a9a4-568">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-568">Parameters</span></span>
* <span data-ttu-id="9a9a4-569">path-要创建的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-569">path - The path of the file to create.</span></span>

<span data-ttu-id="9a9a4-570">返回值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-570">Return value</span></span>

<span data-ttu-id="9a9a4-571">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-571">The created sink.</span></span>

<span data-ttu-id="9a9a4-572">**PerceptionSimulation) LoadPerceptionSimulationRecording (PerceptionSimulation.. ISimulationStreamSinkFactory**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="9a9a4-573">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="9a9a4-574">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-574">Parameters</span></span>
* <span data-ttu-id="9a9a4-575">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="9a9a4-576">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="9a9a4-577">返回值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-577">Return value</span></span>

<span data-ttu-id="9a9a4-578">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-578">The loaded recording.</span></span>

<span data-ttu-id="9a9a4-579">**LoadPerceptionSimulationRecording (PerceptionSimulation，PerceptionSimulation) ISimulationStreamSinkFactory，PerceptionSimulation，ISimulationRecordingCallback。的**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="9a9a4-580">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="9a9a4-581">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-581">Parameters</span></span>
* <span data-ttu-id="9a9a4-582">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="9a9a4-583">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="9a9a4-584">callback-回调，用于接收 regrading 记录状态的更新。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="9a9a4-585">返回值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-585">Return value</span></span>

<span data-ttu-id="9a9a4-586">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="9a9a4-587">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="9a9a4-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="9a9a4-588">描述不同类型的流数据。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-588">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="9a9a4-589">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="9a9a4-590">用于指示没有流数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="9a9a4-591">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="9a9a4-592">数据流的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="9a9a4-593">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="9a9a4-594">用于指针位置和手势的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="9a9a4-595">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="9a9a4-596">环境的空间映射的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="9a9a4-597">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="9a9a4-598">用于校准设备的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="9a9a4-599">只有远程模式下的系统才会接受校准数据包。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="9a9a4-600">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="9a9a4-601">设备环境的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="9a9a4-602">**PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="9a9a4-603">运动控制器的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="9a9a4-604">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="9a9a4-605">具有模拟人力的眼睛的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="9a9a4-606">**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="9a9a4-607">具有设备显示配置的数据流。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="9a9a4-608">**PerceptionSimulation. StreamDataTypes。**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="9a9a4-609">用于指示所有记录的数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="9a9a4-610">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="9a9a4-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="9a9a4-611">从模拟流接收数据包的对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="9a9a4-612">**OnPacketReceived (uint length，byte [] packet)**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="9a9a4-613">接收单个数据包，该数据包在内部键入并进行版本控制。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="9a9a4-614">参数</span><span class="sxs-lookup"><span data-stu-id="9a9a4-614">Parameters</span></span>
* <span data-ttu-id="9a9a4-615">length-数据包的长度。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-615">length - The length of the packet.</span></span>
* <span data-ttu-id="9a9a4-616">数据包-包的数据。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="9a9a4-617">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="9a9a4-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="9a9a4-618">用于创建 ISimulationStreamSink 的对象。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="9a9a4-619">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ( # B1**</span><span class="sxs-lookup"><span data-stu-id="9a9a4-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="9a9a4-620">创建 ISimulationStreamSink 的单个实例。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="9a9a4-621">返回值</span><span class="sxs-lookup"><span data-stu-id="9a9a4-621">Return value</span></span>

<span data-ttu-id="9a9a4-622">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="9a9a4-622">The created sink.</span></span>
