---
title: 使用 HoloLens 仿真器
description: 了解如何使用 HoloLens 仿真器在未配备物理 HoloLens 的电脑上测试混合现实应用。
author: hamalawi
ms.author: moelhama
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 仿真器
ms.openlocfilehash: a9ecb121652dde39be0f91a24a4d57856a874071
ms.sourcegitcommit: eb39526f9620f0459bd30e4484307892f4609334
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201628"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 仿真器

HoloLens 仿真器包括 HoloLens 开发工具集，可让你在未配备物理 HoloLens 的电脑上测试全息应用程序。 该仿真器使用 Hyper-V 虚拟机，这意味着 HoloLens 传感器读取的人类和环境输入通过键盘、鼠标或 Xbox 控制器模拟。 项目甚至无需经过修改即可在仿真器上运行，并且应用不知道其不是在真实的 HoloLens 上运行。

如果想要开发适用于台式机的 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备应用程序或游戏，请查看 [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)，该设备可用于模拟桌面头戴显示设备。

## <a name="hololens-2-emulator-overview"></a>HoloLens 2 仿真器概述

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>安装 HoloLens 仿真器
下载 HoloLens 仿真器。

版本：
* [HoloLens 2 仿真器（Windows 全息版 21H1，2021 年 7 月更新）](https://go.microsoft.com/fwlink/?linkid=2167725)。
* [HoloLens 仿真器（第 1 代）和全息项目模板](https://go.microsoft.com/fwlink/?linkid=2065980)。

可以在 [HoloLens 仿真器存档](hololens-emulator-archive.md)页上找到 HoloLens 仿真器的发行说明和旧版本。

### <a name="hololens-emulator-system-requirements"></a>HoloLens 仿真器系统要求

HoloLens 仿真器结合使用 Hyper-V 和 RemoteFx（第 1 代仿真器）或 GPU-PV（HoloLens 2 仿真器）来实现图形硬件加速。 若要使用仿真器，请确保电脑符合以下硬件要求：
* 64 位 Windows 10 专业版、企业版或教育版
    >[!NOTE]
    >Windows 10 家庭版不支持 Hyper-V 或 HoloLens 仿真器。  
    >HoloLens 2 仿真器需要 Windows 10 2018 年 10 月更新版或更高版本。
* 64 位 CPU
* 4 核 CPU（或总共有 4 个核心的多个 CPU）
* 8 GB 或更大的 RAM
* 在 BIOS 中，必须[支持且启用](/archive/blogs/iftekhar/enable-hardware-settings-in-bios-to-run-hyper-v)以下功能：
   * 硬件协助的虚拟化
   * 二级地址转换 (SLAT)
   * 基于硬件的数据执行保护 (DEP)
* GPU 要求
   * DirectX 11.0 或更高版本
   * WDDM 1.2 图形驱动程序或更高版本（第 1 代）
   * WDDM 2.5 图形驱动程序（HoloLens 2 仿真器）
   * 仿真器可与不受支持的 GPU 配合工作，但速度会变慢

如果你的系统满足上面列出的要求，请确保已在系统上启用“Hyper-V”功能。 转到“控制面板”->“程序”->“程序和功能”->“打开或关闭 Windows 功能”，并检查是否选中了“Hyper-V” 。

## <a name="deploying-apps-to-the-hololens-emulator"></a>将应用部署到 HoloLens 仿真器

1. 在 Visual Studio 中加载应用程序解决方案。
    >[!NOTE]
    >使用 Unity 时，请从 Unity 生成项目，然后像往常一样将生成的解决方案载入 Visual Studio。
2. 对于 HoloLens 仿真器（第 1 代），请确保将“平台”设置为“x86”。 对于 HoloLens 2 仿真器，请确保将“平台”设置为“x86”或“x64”。 
3. 选择所需的 HoloLens 仿真器版本作为目标调试设备。
4. 转到“调试”>“开始调试”或按 **F5** 启动仿真器，然后部署要调试的应用程序。

仿真器在首次启动时，可能需要花费一分钟或更长的时间来完成引导。 建议在调试会话期间让仿真器保持打开状态，以便将应用程序快速部署到仿真器。

## <a name="basic-emulator-input"></a>基本的仿真器输入

控制仿真器与控制许多常见的 3D 视频游戏相似。 可以通过输入选项来使用键盘、鼠标或 Xbox 控制器。 通过定向佩戴 HoloLens 的模拟用户执行的操作来控制仿真器。 你的操作可在环境中四处移动该模拟用户。 仿真器中运行的应用程序可以像在真实设备上一样做出响应。

HoloLens（第 1 代）上的光标可跟踪头部运动和旋转。 在 HoloLens 2 仿真器中，光标跟踪手部运动和方向。

* **前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。
* **上下左右注视** - 选择并拖动鼠标、使用键盘上的箭头键，或使用 Xbox 控制器上的右摇杆。
* **隔空敲击手势** - 单击鼠标右键、按键盘上的 Enter 键，或使用 Xbox 控制器上的 A 按钮。
* **开花手势/系统手势** - 按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。
* **滚动时的手部运动** - 按住 Alt 键和鼠标右键的同时向上或向下拖动鼠标。 在 Xbox 控制器中按住右扳机键和 A 按钮的同时向上和向下移动右摇杆。
* **手部运动和方向**（仅适用于 HoloLens 2 仿真器）- 按住 Alt 键的同时向上、向下、向左或向右拖动鼠标以移动手部。 也可以使用箭头键和 Q 或 E 来旋转和倾斜手部。 在 Xbox 控制器中，请在按住左缓冲键或右缓冲键的同时，使用左拇指操纵杆向左、向右、向前和向后移动手部，使用右拇指操纵杆旋转手部。 使用 Dpad 上的向上或向下键来抬高或降低手部。

有 Windows Mixed Reality 沉浸式头戴显示设备？  从 HoloLens 2 仿真器（Windows 全息版 2004）开始，可以使用 Windows Mixed Reality 沉浸式头戴显示设备和运动控制器来控制 HoloLens 2 仿真器，并以立体方式观看它。  请参阅[将 Windows Mixed Reality 沉浸式头戴显示设备和运动控制器与 HoloLens 2 仿真器配合使用](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator)

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 仿真器剖析

### <a name="main-window"></a>主窗口

![HoloLens 2 仿真器主窗口](images/emulator2-900px.png)

### <a name="toolbar"></a>工具栏

在主窗口的右侧，可以看到仿真器工具栏。 工具栏包含以下按钮：
* ![“关闭”图标](images/emulator-close.png) **关闭**：关闭仿真器。
* ![“最小化”图标](images/emulator-minimize.png) **最小化**：最小化仿真器窗口。
* ![“模拟”图标](images/emulator-simulation-panel.png) **模拟控制面板**：显示或隐藏 [模拟控制面板](#simulation-control-panel)，以便配置和控制 [仿真器的输入](#basic-emulator-input)。
* ![“适合屏幕大小”图标](images/emulator-fit.png) **适合屏幕大小**：使仿真器适合屏幕大小。
* ![“缩放”图标](images/emulator-zoom.png) **缩放**：放大和缩小仿真器。
* ![“帮助”图标](images/emulator-help.png) **帮助**：打开仿真器帮助。
* ![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。
* ![“工具”图标](images/emulator-tools.png) **工具**：打开“其他工具”窗格。

### <a name="simulation-control-panel"></a>模拟控制面板

使用模拟控制面板可以查看模拟人类和输入设备的当前位置与方向。 使用它还可以配置模拟输入（例如，显示或隐藏一只或两只手）和用于控制模拟输入的设备（例如电脑的键盘、鼠标和游戏手柄）。

![模拟控制面板](images/emulator-simulation-control-panel.png)

* 要隐藏或显示模拟面板，请选择工具栏按钮或按键盘上的 F7。
* 将鼠标悬停在控件或字段上可显示工具提示，其中包含键盘、鼠标和游戏手柄的控件。
* 若要显示或隐藏手部，请切换左手或右手下方的相应开关。
* 若要控制手部，请使用键盘上的左/右 Alt 键，或游戏手柄上的左/右缓冲键。
* 要将所有输入指向一只手或两只手，请选择切换开关下的图钉按钮，这相当于针对手部按住 Alt 键。
* 要控制视线方向，请选择“眼睛”部分中的图钉，这相当于按住键盘上的 Y 键。
* 要加载房间录制内容，请选择“录制”部分中的“加载”按钮。 有关详细信息，请参阅[模拟的房间](#simulated-rooms)。
* 要调整模拟人类或输入设备在响应键盘、鼠标或游戏手柄输入时移动或旋转的速度，请选择“输入设置”旁边的齿轮图标并调整滑块。
* 默认情况下，键盘输入会控制模拟人类和模拟输入。 若要将电脑的键盘输入发送到 HoloLens，请取消选中“使用键盘进行模拟”。 F4 是此项设置的快捷键。
* 如果模拟面板已显示，按 F8 会将键盘焦点转移到模拟面板。
* 要在仿真器窗口中取消停靠模拟面板，请选择面板底部的按钮，或按键盘上的 F9。  关闭窗口或再次按 F9 会恢复为仿真器窗口。
* 可将模拟控制面板作为单独的应用程序启动，这样就可以通过运行 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\ 中的 PerceptionSimulationInput.exe，来连接和控制 HoloLens 2 仿真器、HoloLens 2 设备或 Windows Mixed Reality 模拟。

### <a name="account-tab"></a>“帐户”选项卡

在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。 在测试需要用户使用帐户登录的 API 时，此配置非常有用。 切换此选项需要完全关闭并重启 HoloLens 仿真器，使设置生效。 如果启用此选项，则后续启动仿真器时，系统会要求你登录，就像用户首次启动 HoloLens 时一样。 若要使用电脑键盘输入凭据，请先在模拟控制面板中关闭“使用键盘进行模拟”，或按键盘上的 F4 打开或关闭键盘设置。

### <a name="optional-settings-tab"></a>“可选设置”选项卡

“可选设置”选项卡显示用于启用或禁用硬件加速图形的控件。 默认情况下，如果电脑的图形适配器驱动器支持硬件加速图形，则会使用硬件加速图形。 如果图形适配器的驱动程序不支持 GPU-PV，则不会显示此选项。

### <a name="diagnostics-tab"></a>“诊断”选项卡

“诊断”选项卡以 Windows 设备门户链接的形式显示仿真器的 IP 地址，以及虚拟 GPU 的状态。

### <a name="network-tab"></a>“网络”选项卡

“网络”选项卡显示仿真器的网络适配器详细信息，以及主机的网络适配器详细信息。 对于 HoloLens 2 仿真器，只有在 Windows 10 2019 年 5 月更新版或更高版本上运行此仿真器时，此选项卡才会显示。

### <a name="nat-configuration-tab"></a>“NAT 配置”选项卡

只有在 Windows 10 2019 年 5 月更新版或更高版本上运行此仿真器时，此选项卡才会显示。

此仿真器使用电脑的网络连接，位于 NAT 后面。  可以通过此选项卡将端口从主机电脑映射到仿真器，使远程设备能够连接到在仿真器中运行的应用程序和服务。

例如，如果需要从远程电脑访问仿真器上的设备门户，请执行以下操作：

1. 通过双击表中的可用行，为内部端口 80（设备门户在其上进行侦听的端口）添加一个条目。  对于其他应用程序，请输入应用程序正在其上侦听的端口号。
2. 选择任何可用的外部端口。  在此示例中，我们将使用端口 8080 作为外部端口。
3. 选择协议。  默认协议为 TCP。  由于设备门户使用 TCP，我们会保留默认设置。
4. 单击“应用更改”以启用映射。  “状态”会从“挂起”更改为“活动”。
5. 在远程电脑上打开浏览器，导航到“(运行仿真器的电脑的 IP):8080”。  此时会显示设备门户界面。  在远程电脑上使用的 IP 地址必须是运行仿真器的电脑的 IP 地址，而不是仿真器本身的 IP 地址。  可以通过各种方式检索 IP，例如，在电脑上的“设置应用”的“网络和 Internet”类别中检索、在命令提示符中使用“ipconfig”进行检索，以及在仿真器的“工具”对话框的“网络”选项卡中通过查找“桌面适配器”条目进行检索。

另请注意，如果为设备门户添加端口映射，则可以远程方式控制仿真器，方法是：使用包括在仿真器安装中的“感知模拟控制”工具，或者使用感知模拟 API，只需连接到主机电脑的 IP 地址和设备门户的外部端口（例如以上示例中的 8080）即可。  使用感知模拟控制连接到仿真器并对其进行远程控制时，请仅指定电脑的 IP 地址和配置的端口。  不要包含“https://”。

默认情况下，没有端口映射。  多次启动 HoloLens 2 仿真器时，配置的任何映射都会保持不变，并且会在仿真器完全启动后自动启用。

请使用“导出”按钮将映射保存到文件。  然后，可以将此文件与其他可以使用“导入”按钮自动配置相同映射的团队成员共享。

![HoloLens 仿真程序的“NAT 配置”选项卡](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>“更新”选项卡

只有在 Windows 10 2019 年 5 月更新版或更高版本上运行此仿真器时，此选项卡才会显示。

启动时，仿真程序会检查是否有新版本。  如果有可用的新版本，仿真程序会显示一个提示（其中会显示你的现有版本和可用版本），并询问你是否希望更新。  如果你选择“是”，系统会下载新版本的安装程序。

使用“更新”选项卡，你可以通过在其上切换“自动检查更新”复选框来控制是否允许仿真程序检查新版本。还可以通过它查看和下载其他可用的仿真程序版本（从 2019 年 9 月更新版开始）。  除当前正在运行的版本之外的其他版本都提供了下载链接。  单击该链接会下载该版本的安装程序。

![HoloLens 仿真器的“更新”选项卡](images/emulator-updates-500px.png)

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>将 Windows Mixed Reality 沉浸式头戴显示设备和运动控制器与 HoloLens 2 仿真器配合使用

从 HoloLens 2 仿真器（Windows 全息版 2004）开始，可以使用 Windows Mixed Reality 沉浸式头戴显示设备和运动控制器，以立体方式观看 HoloLens 2 仿真器并与之交互。  这样，你便可以在没有 HoloLens 2 设备的情况下利用头部和手部进行更快、更自然的运动。  这并非用于完全替代 HoloLens 2 设备，而是旨在提供改善的体验，使用户不仅仅能够在 2D 桌面窗口中使用键盘、鼠标和手柄与仿真器进行交互。  若要启用此功能：

1. 请确保在电脑上配置了 Windows Mixed Reality，并且连接了 Windows Mixed Reality 沉浸式头戴显示设备。
2. 启动 HoloLens 2 仿真器
3. 单击工具栏按钮或按 F7 打开“仿真”面板。
4. 向下滚动到面板底部。
5. 选中标记了“使用 HMD 进行仿真”的框
6. Windows Mixed Reality 将启动，并且仿真器显示内容将略有变化。  如果未使用头戴显示设备，仿真器会将两只眼睛置于头部中心，并且只显示一只眼睛。  如果使用了头戴显示设备，仿真器会生成真正的立体输出，但只会在其桌面窗口中呈现一只眼睛，而会在头戴显示设备中呈现两只眼睛。
7. 可以选择启用一个或两个运动控制器。  控制器输入映射到仿真器中的手动输入。  例如，若要点击，请在运动控制器上按下扳机键。  若要四处移动，请使用控制杆。  有关控制的完整列表，请参阅[高级 HoloLens 仿真器和混合现实仿真器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)

在头戴显示设备中查看内容时遇到问题？

- 如果显示内容在头戴显示设备和混合现实门户中均为空白，但你在桌面上的“HoloLens 2 仿真器”窗口中看到了内容，请验证是否在仿真器中启用了硬件图形加速。  Windows Mixed Reality 沉浸式头戴显示设备支持要求在仿真器中启用硬件图形加速。
- 如果在头戴显示设备中看到内容，但全息影像比较模糊，或者你看到双像，请使用以下步骤为你的眼睛调整立体视图：

1. 暂时禁用“使用 HMD 进行仿真”。
2. 启动注册表编辑器 (regedit.exe)
3. 导航到 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation
4. 创建一个名为“EnableEyePoseControl”的新 DWORD 值，并将其值设置为 1。
5. 在仿真器中启用“使用 HMD 进行仿真”。
6. 当内容显示在头戴显示设备中时，使用箭头键调整眼睛转动。  按住左 Alt 键可调整左眼，按住右 Alt 键可调整右眼。  使用“Q”和“E”为每个眼睛调整转动，同时再次按住适用于该眼睛的 Alt 键。  使用“+”和“-”键调整眼睛之间的距离。  （请注意，数字键盘上的 +/- 不会起作用。  请使用主键盘上的按键。）
7. 当立体视图看起来正常时，请按“S”保存更改。  新配置将保存起来，以用于以后启动仿真器。
8. 如果要放弃所做的更改并恢复到以前的配置，请按“L”加载默认配置或以前的配置。
9. 在注册表中将“EnableEyePoseControl”值更改为 0，然后禁用“使用 HMD 进行仿真”选项并再次启用该选项。

如果已保存配置，并想要删除它，则可以在 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation 下删除名为“DisplayConfiguration”的值。  如果当前正在将头戴显示设备与仿真器配合使用，则需要禁用“使用 HMD 进行仿真”并将其重新启用，才能看到此更改生效。

## <a name="anatomy-of-the-hololens-first-gen-emulator"></a>HoloLens（第 1 代）仿真器剖析

### <a name="main-window"></a>主窗口

当仿真器启动时，你会看到一个显示 HoloLens OS 的窗口。

![HoloLens 仿真器主窗口](images/emulator-890px.png)

### <a name="toolbar"></a>工具栏

在主窗口的右侧，可以看到仿真器工具栏。 工具栏包含以下按钮：
* ![“关闭”图标](images/emulator-close.png) **关闭**：关闭仿真器。
* ![“最小化”图标](images/emulator-minimize.png) **最小化**：最小化仿真器窗口。
* ![“人类输入”图标](images/emulator-control.png) **人类输入**：使用鼠标和键盘来模拟 [仿真器的人类输入](#basic-emulator-input)。
* ![“键盘和鼠标输入”图标](images/emulator-input.png) **键盘和鼠标输入**：键盘和鼠标输入将作为键盘和鼠标事件直接传递给 HoloLens OS，就如同已连接蓝牙键盘和鼠标一样。
* ![“适合屏幕大小”图标](images/emulator-fit.png) **适合屏幕大小**：使仿真器适合屏幕大小。
* ![“缩放”图标](images/emulator-zoom.png) **缩放**：放大和缩小仿真器。
* ![“帮助”图标](images/emulator-help.png) **帮助**：打开仿真器帮助。
* ![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。
* ![“工具”图标](images/emulator-tools.png) **工具**：打开“其他工具”窗格。

### <a name="simulation-tab"></a>“模拟”选项卡

“其他工具”窗格中的默认选项卡是“模拟”选项卡。 

![HoloLens 仿真器的“其他工具”窗格](images/emulator-simulation-500px.png)

“模拟”选项卡显示用于在仿真器中驱动 HoloLens OS 的模拟传感器的当前状态。 将鼠标悬停在“模拟”选项卡中的任一值上会显示工具提示，其中描述了如何控制该值。

### <a name="room-tab"></a>“房间”选项卡

仿真器以模拟“房间”的空间映射网格形式模拟世界坐标输入。 使用此选项卡可以选择要加载的房间而不是默认房间。

![HoloLens 仿真器的“房间”选项卡](images/emulator-room-500px.png)

有关详细信息，请参阅[模拟的房间](#simulated-rooms)。

### <a name="account-tab"></a>“帐户”选项卡

在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。 在测试需要用户使用帐户登录的 API 时，此配置非常有用。 选中此页上的框后，后续启动仿真器时，系统会要求你登录，如同用户首次启动 HoloLens 时那样。

## <a name="simulated-rooms"></a>模拟的房间

模拟的房间可用于在多个环境中测试应用程序。 仿真器随附了多个房间。 安装仿真器后，可以在 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms 中找到这些房间。 所有这些房间是使用 HoloLens 在真实环境中捕获的：

* **DefaultRoom.xef** - 配有一台电视机、一个茶几和两套沙发的小客厅。 启动仿真器时，默认会加载该房间。
* **Bedroom1.xef** - 配有一张桌子的小卧室。
* **Bedroom2.xef** - 配有一张双人床、梳妆台、床头柜和步入式衣橱的卧室。
* **GreatRoom.xef** - 配有客厅、餐桌和厨房的开阔大房间。
* **LivingRoom.xef** - 配有壁炉、沙发、摇椅和摆放了花瓶的茶几的客厅。

也可以在 HoloLens（第 1 代）上使用 [Windows 设备门户](using-the-windows-device-portal.md)的“模拟”页录制你自己的房间，以便在仿真器中使用它们。

在仿真器中，你只会看到自己渲染的全息影像。 但你会看到全息影像后面的模拟房间。 而在实际的 HoloLens 中，你会同时看到两者的混合形式。 若要在 HoloLens 仿真器中查看模拟的房间，需要更新应用程序，以便在场景中渲染空间映射网格。

## <a name="known-issues"></a>已知问题

* 卸载 HoloLens 2 仿真器时，硬盘映像 (Flash.vhdx) 可能会留在硬盘驱动器上的 Windows Kits\10\Emulation\HoloLens\<build number> 文件夹中。  删除此文件是安全的。
* 硬件图形加速可能导致全息应用在一些带有 AMD 或 Intel 显卡的系统上崩溃。  在仿真器的“工具”窗口中禁用硬件图形加速可以解决此问题。
* 自 2020 年 7 月起安装最新的 Windows 更新后，HoloLens 仿真器（第 1 代）中的硬件图形加速功能可能不再可用。
硬件图形加速所需的 RemoteFX 组件已被弃用，将在将来的 Windows 版本中删除。  若要重新启用硬件图形加速，请使用 [Enable-VMRemoteFXPhysicalVideoAdapter PowerShell cmdlet](/powershell/module/hyper-v/enable-vmremotefxphysicalvideoadapter)。  有关其他信息，请参阅[有关在 Windows 中弃用和删除 RemoteFX 支持的文档](https://support.microsoft.com/help/4570006/update-to-disable-and-remove-the-remotefx-vgpu-component)。

## <a name="troubleshooting"></a>疑难解答

安装仿真器时，可能会出现错误消息，指出需要“Visual Studio 2015 Update 1 和 UWP 工具版本 1.2”。 出现此错误的三个可能原因如下：
* Visual Studio 的版本不够新（需要 Visual Studio 2019、Visual Studio 2017 或 Visual Studio 2015 Update 1 或更高版本）。 若要纠正此问题，请安装最新版本的 Visual Studio。
* 已安装最新版本的 Visual Studio，但未安装通用 Windows 平台 (UWP) 工具。 这是 Visual Studio 的一项可选功能。 对于 HoloLens（第 1 代），你需要适用于 Visual Studio 2015 或 Visual Studio 2017 的 UWP 工具。

此外，在 Windows 的非专业版/企业版/教育版 SKU 上安装仿真器，或者未启用 Hyper-V 功能时，也可能会看到错误。
* 有关完整的要求，请阅读前面的[系统要求](#hololens-emulator-system-requirements)部分。
* 另请确保已在系统上启用 Hyper-V 功能。

如果安装成功完成，但未看到 HoloLens 仿真器作为一个部署和调试选项列出：
* Visual Studio 项目配置已设置为 x86（HoloLens 第 1 代）或者 x86 或 x64（HoloLens 2 仿真器）。
* 如果使用 Visual Studio 2019，则项目配置中的平台工具集应设置为 v142。

如果安装成功完成，但尝试启动 HoloLens 仿真器时 Visual Studio 显示错误：
* 以管理员身份运行 Visual Studio
* 如果曾经只安装过 Visual Studio 2019，请检查 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots 中的“KitsRoot10”注册表值是否指向 32 位 Program Files 文件夹（例如“C:\Program Files (x86)\Windows Kits\10”）。  如果不是，请卸载 HoloLens 仿真器，将该注册表值更改为你的 32 位 Program Files 文件夹，然后重新安装 HoloLens 仿真器。  此问题在 Visual Studio 2019 16.0.3 中已得到解决。

如果启动时仿真器显示“无效的字节编码”错误对话框：
* 请删除 %localappdata%\Microsoft\XDE\HCS 中的所有文件，然后重试。

如果 Visual Studio 中的调试目标列表为空（例如，“启动”是唯一选项），并且你已遵循上述所有故障排除步骤：
* 请删除 %localappdata%\Microsoft\VisualStudio\\<*安装 ID*>\CoreCon 中的 ConfigurationCache 文件夹，然后重试。

如果仿真器启动时系统挂起，请对仿真器图形禁用硬件加速。
* 在“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0”中创建名为“DisableGPU”的注册表 DWORD 值，并将其值设置为 1。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。 从这里，你可以继续了解下一个主题：

> [!div class="nextstepaction"]
> [部署到 HoloLens 模拟器](using-the-hololens-emulator.md)

或直接跳到添加高级服务：

> [!div class="nextstepaction"]
> [高级服务](../../develop/unity/unity-development-overview.md#5-adding-services)

你可以随时返回到 [Unity 开发检查点](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。

## <a name="see-also"></a>另请参阅
* [高级 HoloLens 仿真器和混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 仿真器软件历史记录](hololens-emulator-archive.md)
* [Unity 中的空间映射](../../develop/unity/spatial-mapping-in-unity.md)
* [DirectX 中的空间映射](../../develop/native/spatial-mapping-in-directx.md)