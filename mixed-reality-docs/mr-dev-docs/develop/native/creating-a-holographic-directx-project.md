---
title: 创建全息 DirectX 项目
description: 了解如何基于 Windows Mixed Reality 应用程序模板创建新的全息版 DirectX 应用程序。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality，全息应用，新应用，UWP 应用，模板应用，全息影像，新项目，演练，下载，示例代码，混合现实耳机，Windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200139"
---
# <a name="creating-a-holographic-directx-project"></a>创建全息 DirectX 项目

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](openxr-getting-started.md)**。

为 HoloLens 创建的全息应用将是<a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank"> (UWP) 应用的通用 Windows 平台</a>。  如果面向桌面 Windows Mixed Reality 耳机，则可以创建 UWP 应用或 Win32 应用。

DirectX 11 全息 UWP 应用模板非常类似于 DirectX 11 UWP 应用模板。 该模板包括一个程序循环、一个用于管理 Direct3D 设备和上下文的 **DeviceResources** 类和一个简化的内容呈现器类。 它还有 <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像其他任何 UWP 应用一样。

然而，混合现实应用有一些其他功能，这些功能在典型的 Direct3D UWP 应用中不存在。 Windows Mixed Reality 应用模板可以：
* 处理与全息相机关联的 Direct3D 设备资源。
* 从系统检索相机后台缓冲区。 对于 Direct3D12，创建全息后台缓冲区资源并管理资源生存期。
* 处理 [注视](../../design/gaze-and-commit.md) 的输入，并识别 [手势](../../design/gaze-and-commit.md#composite-gestures)。
* 进入全屏立体声呈现模式。

## <a name="how-do-i-get-started"></a>如何入门？

请按照下载 Visual Studio 2019 和 Windows Mixed Reality 应用程序模板中的说明，先[安装这些工具](../install-the-tools.md)。 混合现实应用模板在 Visual Studio marketplace 上可作为[web 下载](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)，或通过 Visual Studio UI 将它们安装为扩展。

现在，你已准备好创建 DirectX 11 Windows Mixed Reality 应用！ 请注意，若要删除示例内容，请在 *pch* 中注释掉 **DRAW_SAMPLE_CONTENT** 预处理器指令。

## <a name="creating-a-uwp-project"></a>创建 UWP 项目

安装工具后，] (。/install-the-tools.md) 你可以创建一个全息的 DirectX UWP 项目。

在 Visual Studio 2019 中创建新项目：
1. 开始 **Visual Studio**。
2. 在右侧的 "**入门**" 部分中，选择 "**创建新项目**"。
3. 在 "**创建新项目**" 对话框的下拉菜单中，选择 " **c + +**"、" **Windows Mixed Reality**" 和 " **UWP**"。
4. 选择 "**全息 DirectX 11 应用 (通用 Windows)  (c + +/WinRT)**。
   ![Visual Studio 2019 中全息版 DirectX 11 c + +/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Visual Studio 2019 中的全息 DirectX 11 c + +/WinRT UWP 应用项目模板*
   >[!IMPORTANT]
   >请确保项目模板的名称包含 " (c + +/WinRT) "。  如果没有，则已安装全息版项目模板。  若要获取最新的项目模板，请将[它们安装](../install-the-tools.md)为 Visual Studio 2019 的扩展。
5. 选择“下一步”  。
5. 填写 " **Project 名称** 和 **位置**" 文本框，然后选择或点击 "**创建**"。 创建全息应用项目。
6. 对于仅 HoloLens 2 开发目标，请确保将 **目标版本** 和 **最低版本** 设置为 **Windows 10 版本 1903**。  如果你还以 HoloLens (第一代) 或桌面 Windows Mixed Reality 耳机为目标，则可以将 **最低版本** 设置为 **Windows 10 版本 1809**。 当使用 HoloLens 2 的新功能时，这将要求在代码中进行某种<a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本自适应检查</a>。
   ![设置 Windows 10 的屏幕截图，版本1903作为目标和最低版本](images/new-uwp-project.png)<br>
   *设置 **Windows 10 版本1903，** 作为目标和最低版本*
   >[!IMPORTANT]
   >如果看不到 **Windows 10 版本 1903** 作为选项，则不会安装最新的 Windows 10 SDK。  若要使此选项显示，请<a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装 Windows 10 SDK 的版本10.0.18362.0 或更高版本</a>。

在 Visual Studio 2017 中创建新项目：
1. 开始 **Visual Studio**。
2. 从 "**文件**" 菜单中，指向 "**新建**"，然后从上下文菜单中选择 " **Project** "。 此时会打开“新建项目”对话框。 
3. 展开左侧的 " **已安装** "，然后展开 " **Visual C++** 语言" 节点。
4. 导航到 **Windows 通用 > 全息** 节点，并选择 " **(通用 Windows)  (c + +/WinRT) 中的" 全息 DirectX 11 应用**"。
   ![Visual Studio 2017 中全息版 DirectX 11 c + +/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 2017 中的全息 DirectX 11 c + +/WinRT UWP 应用项目模板*
   >[!IMPORTANT]
   >请确保项目模板的名称包含 " (c + +/WinRT) "。  如果没有，则已安装全息版项目模板。  若要获取最新的项目模板，请将[它们安装](../install-the-tools.md)为 Visual Studio 2017 的扩展。
5. 填写 " **名称** " 和 " **位置** " 文本框，然后选择或点击 **"确定"**。 创建全息应用项目。
6. 对于仅 HoloLens 2 开发目标，请确保将 **目标版本** 和 **最低版本** 设置为 **Windows 10 版本 1903**。  如果你还以 HoloLens (第一代) 或桌面 Windows Mixed Reality 耳机为目标，则可以将 **最低版本** 设置为 **Windows 10 版本 1809**。 当使用 HoloLens 2 的新功能时，这将要求在代码中进行某种<a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本自适应检查</a>。
   ![设置 Windows 10 的屏幕截图，版本1903作为目标和最低版本](images/new-uwp-project.png)<br>
   *设置 **Windows 10 版本1903，** 作为目标和最低版本*
   >[!IMPORTANT]
   >如果看不到 **Windows 10 版本 1903** 作为选项，则不会安装最新的 Windows 10 SDK。  若要使此选项显示，请<a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装 Windows 10 SDK 的版本10.0.18362.0 或更高版本</a>。

该模板将使用<a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>（一种 c + + 17 语言 Windows 运行时 api）生成项目，该项目支持任何符合标准的 c + + 17 编译器。  该项目演示了如何创建一个世界上锁定的多维数据集，该多维数据集是用户的2米。 用户 [可以按](../../design/gaze-and-commit.md#composite-gestures) 下或按下控制器上的按钮，将多维数据集置于用户 [注视](../../design/gaze-and-commit.md)指定的不同位置。 可以修改此项目来创建任何混合现实应用。

你还可以使用 **Visual c #** 全息项目模板创建一个新项目，该模板基于 SharpDX。  如果你的全息 c # 项目不是从 Windows 全息应用程序模板开始，则需要从 Windows Mixed Reality c # 模板项目复制 fxcompile 文件，然后将其导入到 .csproj 文件中，以便编译添加到项目中的 HLSL 文件。 Visual Studio 的 Windows Mixed Reality 应用程序模板扩展中还提供了 Direct3D 12 模板。

查看[使用 Visual Studio 部署和调试](../platform-capabilities-and-apis/using-visual-studio.md)，获取有关如何生成和部署示例到 HoloLens、已连接沉浸式设备的 PC 或仿真程序的信息。

下面的说明将假设你使用 c + + 生成应用。

### <a name="uwp-app-entry-point"></a>UWP 应用入口点

全息 UWP 应用在 AppView 的 **wWinMain** 函数中启动。 **WWinMain** 函数创建应用的 <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，并通过它启动 <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。

从 **AppView**：

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

从现在开始，AppView 类处理与 Windows 基本输入事件、CoreWindow 事件和消息等之间的交互。 它还将创建应用使用的 HolographicSpace。

## <a name="creating-a-win32-project"></a>创建 Win32 项目

开始构建 Win32 全息项目的最简单方法是修改 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。

此 Win32 示例使用<a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>，它是支持任何符合标准的 c + + 17 编译器的 Windows 运行时 api 的 c + + 17 语言投影。  该项目演示了如何创建一个世界上锁定的多维数据集，该多维数据集是用户的2米。 用户可以按控制器上的按钮，将多维数据集置于用户 [注视](../../design/gaze-and-commit.md)指定的不同位置。 可以修改此项目来创建任何混合现实应用。

### <a name="win32-app-entry-point"></a>Win32 应用程序入口点

全息 Win32 应用程序在 AppMain 的 **wWinMain** 函数中启动。 **WWinMain** 函数创建应用的 HWND 并启动其消息循环。

从 **AppMain**：

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

从现在开始，AppMain 类处理与基本窗口消息的交互，等等。 它还将创建应用使用的 HolographicSpace。

## <a name="render-holographic-content"></a>呈现全息内容

项目的 " **内容** " 文件夹包含用于渲染 [全息空间](getting-a-holographicspace.md)中全息影像的类。 模板中的默认全息图是远离用户的旋转多维数据集。 绘制此多维数据集是在 **SpinningCubeRenderer** 中实现的，该方法具有以下关键方法：

|  方法  |  说明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  加载着色器并创建多维数据集网格。 | 
|  `PositionHologram` |  将全息图置于所提供的 <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>指定的位置。 | 
|  `Update` |  旋转多维数据集，并设置模型矩阵。 | 
|  `Render` |  使用顶点和像素着色器呈现一个帧。 | 

**着色** 子文件夹包含四个默认着色器实现：

|  着色器  |  说明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  不修改几何图形的传递。 | 
|  `PixelShader.hlsl` |  通过颜色数据。 在光栅化步骤中，将颜色数据插值并分配给一个像素。 | 
|  `VertexShader.hlsl` |  用于在 GPU 上执行顶点处理的简单着色器。 | 
|  `VPRTVertexShader.hlsl` |  用于在 GPU 上执行顶点处理的简单着色器，针对 Windows Mixed Reality 立体声渲染进行了优化。 | 

`VertexShaderShared.hlsl` 包含在和之间共享的通用代码 `VertexShader.hlsl` `VPRTVertexShader.hlsl` 。

注意： Direct3D 12 应用模板还包括 `ViewInstancingVertexShader.hlsl` 。 此变体使用 D3D12 可选功能来更有效地呈现立体声图像。

着色器将在项目生成时编译，并在 **SpinningCubeRenderer：： CreateDeviceDependentResources** 方法中加载。

## <a name="interact-with-your-holograms"></a>与全息影像交互

用户输入在 **SpatialInputHandler** 类中处理，该类获取 <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 实例并订阅 <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 事件。 这将允许检测分流手势和其他空间输入事件。

## <a name="update-holographic-content"></a>更新全息内容

混合现实应用在游戏循环中更新，默认情况下，该循环在的 **Update** 方法中实现 `AppMain.cpp` 。 **Update** 方法更新场景对象，如旋转立方体，并返回一个 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>对象，该对象用于获取最新的视图和投影矩阵并显示交换链。

中的 **Render** 方法 `AppMain.cpp` 采用 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，并根据当前应用和空间定位状态将当前帧呈现到每个全息相机。

## <a name="notes"></a>备注

Windows Mixed Reality 应用模板现在支持在/Qspectre)  (启用了 Spectre 缓解标志的编译。 在编译启用了 Spectre 缓解功能的配置之前，请确保安装 Spectre 版本的 Microsoft Visual C++ (MSVC) 运行时库。 若要安装 Spectre 缓解的 c + + 库，请启动 Visual Studio 安装程序并选择 "**修改**"。 导航到 **各个组件** 并搜索 "spectre"。 选择与要为其编译 Spectre 的代码所需的目标平台和 MSVC 版本对应的框，然后单击 "**修改**" 开始安装。

## <a name="see-also"></a>另请参阅
* [获取 HolographicSpace](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [在 DirectX 中渲染](rendering-in-directx.md)
* [使用 Visual Studio 进行部署和调试](../platform-capabilities-and-apis/using-visual-studio.md)
* [使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [将 XAML 与全息 DirectX 应用配合使用](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)