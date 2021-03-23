---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "100496086"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 进行部署和调试

无论你是使用 DirectX 还是 Unity 来开发混合现实应用，Visual Studio 都是你用于进行调试和部署的首选工具。 本部分介绍以下操作：
* 通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。
* 使用 Visual Studio 中内置的 HoloLens 仿真器。
* 调试混合现实应用。

## <a name="prerequisites"></a>必备条件

1. 有关安装说明，请参阅[安装工具](../../develop/install-the-tools.md#installation-checklist)。
2. 在 Visual Studio 中创建新的通用 Windows 应用项目。  对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。  对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。 支持 C# 和 C++。 （或按说明[在 Unity 中创建应用](../../develop/unity/tutorials/holograms-100.md)。）

## <a name="enabling-developer-mode"></a>启用开发人员模式

首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 

### <a name="hololens"></a>HoloLens

1. 打开 HoloLens，然后戴上设备。
2. 使用[开始手势](../../design/system-gesture.md)以启动主菜单。
3. 选择“设置”  磁贴，以在你的环境中启动应用。
4. 选择“更新”  菜单项。
5. 选择“面向开发人员”  菜单项。
6. 启用“开发人员模式”，将应用从 Visual Studio 部署到 HoloLens。
7. 可选：向下滚动，并启用设备门户，以便从 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows 电脑

如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。
1. 转到“设置” 
2. 选择“更新和安全” 
3. 选择“面向开发人员” 
4. 启用“开发人员模式”，阅读所选设置的免责声明，然后选择“是”以接受更改。

## <a name="deploying-a-hololens-app-over-wi-fi"></a>通过 Wi-Fi 部署 HoloLens 应用 

为 Visual Studio 项目配置以下属性：

1. 选择应用编译选项
    * 对于 Unity 项目，请选择“Master”或“Master”  
    * 对于所有其他项目，请选择“Release”

> [!NOTE]
> 可以在[导出和生成 Visual Studio 解决方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中找到每个编译选项的完整定义。

2. 根据设备选择生成配置

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 在部署目标下拉菜单中选择“远程计算机” 

![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)

接下来，需要设置远程连接。 对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。  如果正在处理 C# 项目，将自动显示一个对话框。

> [!NOTE]
> 如果 C# 项目中未显示远程连接对话框，你可以从“属性”>“调试”手动打开它。

1. 在“地址”或“计算机名”字段中输入设备的 IP 地址。   
    * 可在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址
    * 我们始终建议手动输入你的 IP 地址，而不要依赖于“自动检测到”功能

2. 将身份验证模式设置为“通用(未加密协议)” 

  ![Visual Studio 中的远程连接对话框](images/remotedeploy.png)

3. 根据需要生成、部署和调试应用
    * 选择“调试”>“开始调试”以部署应用并开始调试 
    * 选择“生成”>“部署”以生成并部署而不调试

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)

4. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明 **配对设备**。

## <a name="deploying-a-hololens-app-over-usb"></a>通过 USB部署 HoloLens 应用 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. 选择应用编译选项
    * 对于 Unity 项目，请选择“Master”或“Master”  
    * 对于所有其他项目，请选择“Release”

> [!NOTE]
> 可以在[导出和生成 Visual Studio 解决方案](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)中找到每个编译选项的完整定义。

2. 根据设备选择生成配置

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 在部署目标下拉菜单中选择“设备” 

![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)

4. 根据需要生成、部署和调试应用
    * 选择“调试”>“开始调试”以部署应用并开始调试 
    * 选择“生成”>“部署”以生成并部署而不调试

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>

5. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明 **配对设备**。

> [!NOTE]
> 如果通过 USB 进行应用部署时出现相当长的延迟时间，建议使用上一节中的[远程计算机说明](#deploying-a-hololens-app-over-wi-fi)。

## <a name="deploying-an-app-to-the-hololens-emulator"></a>将应用部署到 HoloLens 仿真器

1. 请确保已[安装 HoloLens 2 或 HoloLens（第一代）仿真器](../install-the-tools.md#installation-checklist)
2. 根据设备选择生成配置和仿真器

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 根据需要生成、部署和调试应用
    * 选择“调试”>“开始调试”以部署应用并开始调试 
    * 选择“生成”>“部署”以生成并部署而不调试

![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a>将 VR 应用部署到本地 PC 

使用连接到电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式头戴显示设备：
1. 为应用选择一种 **x86** 或 **x64** 生成配置
2. 在部署目标下拉菜单中选择“本地计算机” 
3. 根据需要生成、部署和调试应用
    * 选择“调试”>“开始调试”以部署应用并开始调试 
    * 选择“生成”>“部署”以生成并部署而不调试

## <a name="pairing-your-device"></a>配对设备

首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。 在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。  当 PIN 显示在 HoloLens 上时，请将其键入 Visual Studio。 配对完成后，在 HoloLens 上点击“完成”关闭对话框。  此电脑现已与 HoloLens 配对，你可以自动部署应用。 请针对用于将应用部署到 HoloLens 的每台电脑重复上述步骤。

将 HoloLens 与所有配对的计算机取消配对：
* 启动“设置”应用，转到“更新”>“面向开发人员”，并点击“清除”  。

## <a name="graphics-debugger-for-hololens-1st-gen"></a>适用于 HoloLens（第一代）的图形调试器

在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。 有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)。

**启动图形调试器**
1. 按上面的说明将目标指定为设备或仿真器
2. 转到“调试”>“图形”>“启动诊断” 
3. 首次在 HoloLens 上开始诊断时，可能会出现“拒绝访问”错误。 请重启 HoloLens 以使更新的权限生效，然后重试。

## <a name="profiling"></a>分析

使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。 这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。 有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)。

**在 HoloLens 上启动分析工具**
1. 按上面的说明将目标指定为设备或仿真器
2. 转到“调试”>“启动诊断工具但不调试...” 
3. 选择要使用的工具
4. 选择“启动”
5. 首次在 HoloLens 上启动诊断但不调试时，可能会出现“拒绝访问”错误。 请重启 HoloLens 以使更新的权限生效，然后重试。

## <a name="debugging-an-installed-or-running-app"></a>调试已安装的或正在运行的应用

可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。 要调试已安装的应用包，或者要调试已经在运行的应用，此方法非常有用。
1. 转到“调试”->“其他调试目标”->“调试已安装的应用包” 
2. 为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  
3. 输入设备的 **IP 地址**
4. 选择“通用”身份验证模式 
5. 窗口中会显示正在运行的和非活动的应用。 选择要调试的应用。
6. 选择要调试的代码类型（“托管”、“本机”、“混合”）
7. 选择“附加”或“开始” 

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。 从这里，你可以继续了解下一个主题：

> [!div class="nextstepaction"]
> [部署到 HoloLens 模拟器](using-the-hololens-emulator.md)

或直接跳到添加高级服务：

> [!div class="nextstepaction"]
> [高级服务](../../develop/unity/unity-development-overview.md#5-adding-services)

你可以随时返回到 [Unity 开发检查点](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)。

## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [部署和调试通用 Windows 平台 (UWP) 应用](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [启用设备进行开发](/windows/uwp/get-started/enable-your-device-for-development)