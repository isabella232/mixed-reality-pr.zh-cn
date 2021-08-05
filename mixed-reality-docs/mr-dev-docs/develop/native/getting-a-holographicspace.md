---
title: 获取 HolographicSpace
description: 了解如何在混合现实应用中使用 HolographicSpace API 进行全息渲染和空间输入。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、HolographicSpace、CoreWindow、空间输入、渲染、交换链、全息帧、更新循环、游戏循环、参考框架、可定位性、示例代码、演练、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212165"
---
# <a name="getting-a-holographicspace"></a>获取 HolographicSpace

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](openxr-getting-started.md)**。

<a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类是进入全息世界门户。 它控制沉浸式渲染，提供相机数据，并提供对空间推理 API 的访问。 你将为 UWP 应用的 <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 或 Win32 应用的 HWND 创建一个。

## <a name="set-up-the-holographic-space"></a>设置全息空间

创建全息空间对象是创建应用的第一Windows Mixed Reality步骤。 传统Windows应用呈现到为应用程序视图的核心窗口创建的 Direct3D 交换链。 此交换链显示在全息 UI 中的平板电脑上。 若要使应用程序视图成为全息视图而不是 2D 平板电脑，请为应用程序的核心窗口（而不是交换链）创建全息空间。 显示此全息空间创建的全息帧会将应用置于全屏呈现模式。

对于从 [*Holographic DirectX 11 App (Universal Windows)*](creating-a-holographic-directx-project.md)模板启动的 **UWP** 应用，在 AppView.cpp 的 **SetWindow** 方法中查找此代码：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

如果要从 [*BasicHologram* Win32](creating-a-holographic-directx-project.md#creating-a-win32-project)示例开始生成 **Win32** 应用，请看 **App：：CreateWindowAndHolographicSpace，** 了解 HWND 示例。 然后，可以通过创建关联的 <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>将其转换为沉浸式 HWND：

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

获取 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace 后，HolographicSpace 可以处理全息相机、创建坐标系以及执行全息渲染。 当前全息空间在 DirectX 模板中的多个位置使用：
* **DeviceResources** 类需要从 HolographicSpace 对象获取一些信息才能创建 Direct3D 设备。 这是与全息显示器关联的 DXGI 适配器 ID。 <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类使用应用的 Direct3D 11 设备来创建和管理基于设备的资源，例如每个全息相机的后端缓冲区。 如果你有兴趣了解此函数在底层的作用，你将在 DeviceResources.cpp 中找到它。
* **DeviceResources：：InitializeUsingHolographicSpace** 函数演示如何通过查找 LUID 来获取适配器 ， 以及如何在未指定首选适配器时选择默认适配器。
* 应用的主类使用 **AppView：：SetWindow** 或 **App：：CreateWindowAndHolographicSpace** 中的全息空间进行更新和呈现。

>[!NOTE]
>虽然以下部分提及了模板中的函数名称，例如 **AppView：：SetWindow，** 假定你从全息 UWP 应用模板开始，但看到的代码片段将同样适用于 UWP 和 Win32 应用。

接下来，我们将深入探讨 **SetHolographicSpace** 在 AppMain 类中负责的设置过程。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>订阅相机事件、创建和删除相机资源

应用的全息内容位于其全息空间中，并通过一个或多个全息相机进行查看，这些相机表示场景中的不同透视。 现在，你已拥有全息空间，可以接收全息相机的数据。

应用需要通过创建特定于该相机的任何资源来响应 **CameraAdded** 事件。 此类资源的一个示例是后缓冲区呈现器目标视图。 在应用创建任何全息帧之前，可以在 **AppView：：SetWindow** 调用 **的 DeviceResources：：SetHolographicSpace** 函数中查看此代码：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

应用还需要通过释放为此相机创建的资源来响应 **CameraRemoved** 事件。

从 **DeviceResources：：SetHolographicSpace**：

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件处理程序必须完成一些工作，以保持全息渲染的平滑流动以及应用呈现。 阅读代码和注释了解详细信息：可以在主类中查找 **OnCameraAdded** 和 **OnCameraRemoved，** 以了解 **DeviceResources****如何处理 m_cameraResources** 映射。

现在，我们重点关注 AppMain 及其用于使应用了解全息相机的设置。 考虑到这一点，必须注意以下两个要求：

1. 对于 **CameraAdded** 事件处理程序，应用可以异步工作，以完成新全息相机的资源创建和加载资产。 完成此工作需要多个帧的应用应请求延迟，并异步加载后完成延迟。 [PPL 任务](/cpp/parallel/concrt/parallel-patterns-library-ppl)可用于执行异步工作。 应用必须确保它已准备好在退出事件处理程序或完成延迟时向该相机呈现。 退出事件处理程序或完成延迟会告知系统，应用现在已准备好接收包含该相机的全息帧。

2. 当应用收到 **CameraRemoved** 事件时，它必须释放对后缓冲区的所有引用，并立即退出函数。 这包括呈现器目标视图，以及可能包含对 [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)的引用的其他任何资源。 应用还必须确保后端缓冲区未附加为呈现目标，如 **CameraResources：：ReleaseResourcesForBackBuffer 中所示**。 为了帮助加快操作速度，应用可以释放后缓冲区，然后启动任务以异步完成相机的其他任何拆解工作。 全息应用模板包含可用于此目的的 PPL 任务。

>[!NOTE]
>若要确定何时在帧上显示添加或删除的相机，请使用 **HolographicFrame** [AddedCameras 和](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 属性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>为全息内容创建参考框架

应用的内容必须定位在空间 [坐标系](coordinate-systems-in-directx.md) 中，以在 HolographicSpace 中呈现。 系统提供两个主要参考帧，可用于为全息影像建立坐标系。

全息版中Windows参考帧：附加到设备的参考帧，以及设备在用户环境中移动时保持固定的引用帧。 全息应用模板默认使用固定引用框架;这是呈现世界锁定全息影像的最简单方法之一。

固定参考帧旨在稳定设备当前位置附近的位置。 这意味着，当设备了解有关其周围空间的更多信息时，离设备较远的坐标可能会相对于用户环境略微偏移。 有两种方法可以创建固定参考框架：从空间阶段获取坐标系，或使用默认的<a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 [](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage) 如果要为沉浸式头戴显示设备Windows Mixed Reality应用，建议的起点是[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)。 空间阶段还提供有关播放器沉浸式头戴显示设备功能的信息。 此处，我们将展示如何使用默认的 <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空间定位器Windows Mixed Reality设备，跟踪设备运动，并提供相对于设备位置可理解的坐标系。

从 **AppMain：：OnHolographicDisplayIsAvailableChanged**：

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

启动应用后，创建一次固定引用帧。 这类似于定义世界坐标系，在应用启动时将原点置于设备的位置。 此参考帧不会随设备一起移动。

从 **AppMain：：SetHolographicSpace**：

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有引用帧都是倾斜对齐的，这意味着 y 轴相对于用户环境"向上"。 由于Windows使用"右手"坐标系，因此 –z 轴的方向与创建引用帧时设备面向的"向前"方向一致。

>[!NOTE]
>当应用需要精确放置单个全息影像时，请使用 <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> 将单个全息影像定位到现实世界中的位置。 例如，当用户指示一个点特别感兴趣时，请使用空间定位点。 定位点位置不会偏移，但可以调整它们。 默认情况下，当调整定位点时，它会在更正发生后，将定位点的位置简化为在接下来几个帧上的位置。 根据你的应用程序，当发生这种情况时，你可能希望以不同的方式处理调整 (例如，将调整延迟到全息影像无法查看) 。 <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>属性和<a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件启用这些自定义项。

## <a name="respond-to-locatability-changed-events"></a>响应可定位性更改事件

渲染被世界锁定的全息影像要求设备将自身定位到世界上。 由于环境条件的原因，这并不总是可能的，如果是这样，用户可能会期望跟踪中断的可视指示。 此视觉指示必须使用附加到设备的参考帧呈现，而不是静态呈现给世界。

如果跟踪因任何原因中断，应用可以请求收到通知。 注册 LocatabilityChanged 事件，以检测设备在世界中的定位能力何时发生变化。 从 **AppMain：：SetHolographicSpace：**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然后，使用此事件来确定全息影像何时无法向世界呈现静态图像。

## <a name="see-also"></a>另请参阅
* [在 DirectX 中渲染](rendering-in-directx.md)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)