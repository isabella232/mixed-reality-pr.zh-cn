---
title: QR 码跟踪
description: 了解如何在 HoloLens 2 上检测 QR 码，添加网络摄像机功能并管理混合现实应用中的坐标系统。
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr，lbe，基于位置的娱乐，vr 拱廊类，拱廊类，沉浸，qr，qr 码，hololens2
ms.openlocfilehash: 2617d5f811b9d437ece0d5ba2e7dbc909eb16988
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "103574943"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="d13e4-104">QR 码跟踪</span><span class="sxs-lookup"><span data-stu-id="d13e4-104">QR code tracking</span></span>

<span data-ttu-id="d13e4-105">HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="d13e4-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="d13e4-106">启用设备的网络摄像机后，便可以在最新版本的 Unreal 或 Unity 项目中识别 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="d13e4-107">在转到生产环境之前，我们建议遵循本文末尾介绍的 [最佳实践](#best-practices-for-qr-code-detection) 。</span><span class="sxs-lookup"><span data-stu-id="d13e4-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="d13e4-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="d13e4-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d13e4-109">功能</span><span class="sxs-lookup"><span data-stu-id="d13e4-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d13e4-110"><a href="/hololens/hololens1-hardware">HoloLens (第一代) </a></span><span class="sxs-lookup"><span data-stu-id="d13e4-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d13e4-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d13e4-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d13e4-112"><a href="../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="d13e4-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d13e4-113">QR 码检测</span><span class="sxs-lookup"><span data-stu-id="d13e4-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="d13e4-114">️</span><span class="sxs-lookup"><span data-stu-id="d13e4-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d13e4-115">✔️</span><span class="sxs-lookup"><span data-stu-id="d13e4-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d13e4-116">✔️</span><span class="sxs-lookup"><span data-stu-id="d13e4-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="d13e4-117">Windows 10 版本2004及更高版本支持在台式计算机上通过沉浸式 Windows Mixed Reality 耳机进行 QR 代码跟踪。</span><span class="sxs-lookup"><span data-stu-id="d13e4-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="d13e4-118">使用 IsSupported () API 来确定当前设备上是否支持该功能。</span><span class="sxs-lookup"><span data-stu-id="d13e4-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="d13e4-119">获取 QR 包</span><span class="sxs-lookup"><span data-stu-id="d13e4-119">Getting the QR package</span></span>

<span data-ttu-id="d13e4-120">可在 [此处](https://nuget.org/Packages/Microsoft.MixedReality.QR)下载用于 QR 码检测的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="d13e4-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="d13e4-121">检测 QR 码</span><span class="sxs-lookup"><span data-stu-id="d13e4-121">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="d13e4-122">添加网络摄像机功能</span><span class="sxs-lookup"><span data-stu-id="d13e4-122">Adding the webcam capability</span></span>

<span data-ttu-id="d13e4-123">需要将功能添加 `webcam` 到清单以检测 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-123">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="d13e4-124">此功能是必需的，因为用户环境中检测到的代码中的数据可能包含敏感信息。</span><span class="sxs-lookup"><span data-stu-id="d13e4-124">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="d13e4-125">可以通过调用来请求权限 `QRCodeWatcher.RequestAccessAsync()` ：</span><span class="sxs-lookup"><span data-stu-id="d13e4-125">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="d13e4-126">_导向_</span><span class="sxs-lookup"><span data-stu-id="d13e4-126">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d13e4-127">_C_</span><span class="sxs-lookup"><span data-stu-id="d13e4-127">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="d13e4-128">构造 QRCodeWatcher 对象之前，必须先请求权限。</span><span class="sxs-lookup"><span data-stu-id="d13e4-128">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="d13e4-129">尽管 QR 码检测需要 `webcam` 功能，但使用设备的跟踪相机进行检测。</span><span class="sxs-lookup"><span data-stu-id="d13e4-129">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="d13e4-130">与使用设备的照片/视频 (PV) 照相机进行检测相比，此功能可提供更广泛的检测 FOV 和更好的电池寿命。</span><span class="sxs-lookup"><span data-stu-id="d13e4-130">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="d13e4-131">检测 Unity 中的 QR 码</span><span class="sxs-lookup"><span data-stu-id="d13e4-131">Detecting QR codes in Unity</span></span>

<span data-ttu-id="d13e4-132">你可以使用 Unity 中的 QR 代码检测 API，而无需导入 MRTK，方法是使用 [nuget For Unity](https://github.com/GlitchEnzo/NuGetForUnity)安装 nuget 包。</span><span class="sxs-lookup"><span data-stu-id="d13e4-132">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="d13e4-133">如果要了解其工作原理，请下载 [示例 Unity 应用](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)。</span><span class="sxs-lookup"><span data-stu-id="d13e4-133">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="d13e4-134">该示例应用包含的示例演示了如何使用 QR 代码和关联数据（如 GUID、物理大小、时间戳和解码的数据）显示全息方形。</span><span class="sxs-lookup"><span data-stu-id="d13e4-134">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="d13e4-135">在 c + + 中检测 QR 码</span><span class="sxs-lookup"><span data-stu-id="d13e4-135">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="d13e4-136">获取 QR 码的坐标系统</span><span class="sxs-lookup"><span data-stu-id="d13e4-136">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="d13e4-137">每个检测到的 QR 码都公开一个 [空间坐标系统](../../design/coordinate-systems.md) ，该系统与左上角快速检测方的左上角中的 QR 代码对齐：</span><span class="sxs-lookup"><span data-stu-id="d13e4-137">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR 码坐标系统](images/Qr-coordinatesystem.png) 

<span data-ttu-id="d13e4-139">当直接使用 QR SDK 时，Z 轴指向纸张 (不显示) -在转换为 Unity 坐标时，Z 轴将从纸上指向并向左传递。</span><span class="sxs-lookup"><span data-stu-id="d13e4-139">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="d13e4-140">QR 码的 SpatialCoordinateSystem 对齐方式如下所示。</span><span class="sxs-lookup"><span data-stu-id="d13e4-140">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="d13e4-141">可以通过调用 <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：： CreateCoordinateSystemForNode</a> 并传入代码的 SpatialGraphNodeId，从平台中获取坐标系。</span><span class="sxs-lookup"><span data-stu-id="d13e4-141">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="d13e4-142">下面的 c + + 代码演示如何创建一个矩形，并使用 QR 码的坐标系统来放置它：</span><span class="sxs-lookup"><span data-stu-id="d13e4-142">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="d13e4-143">可以使用物理尺寸来创建 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="d13e4-143">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="d13e4-144">坐标系统可用于绘制 QR 码，或将全息影像附加到该位置：</span><span class="sxs-lookup"><span data-stu-id="d13e4-144">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="d13e4-145">*QRCodeAddedHandler* 可以完全像下面这样：</span><span class="sxs-lookup"><span data-stu-id="d13e4-145">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="d13e4-146">QR 码检测的最佳实践</span><span class="sxs-lookup"><span data-stu-id="d13e4-146">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="d13e4-147">关于 QR 码的安静区</span><span class="sxs-lookup"><span data-stu-id="d13e4-147">Quiet zones around QR Codes</span></span>

<span data-ttu-id="d13e4-148">若要正确读取，QR 码需要代码两侧的边距。</span><span class="sxs-lookup"><span data-stu-id="d13e4-148">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="d13e4-149">此边距不能包含任何打印内容，并且应为四个模块， (代码中的单个黑色方块) 宽度。</span><span class="sxs-lookup"><span data-stu-id="d13e4-149">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="d13e4-150">[QR 规范](https://www.qrcode.com/en/howto/code.html)包含有关 quiet 区域的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d13e4-150">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="d13e4-151">照明和背景</span><span class="sxs-lookup"><span data-stu-id="d13e4-151">Lighting and backdrop</span></span>
<span data-ttu-id="d13e4-152">QR 码检测质量容易产生不同的照明和背景。</span><span class="sxs-lookup"><span data-stu-id="d13e4-152">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="d13e4-153">在具有明亮光照的场景中，打印灰色背景上的黑色代码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-153">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="d13e4-154">否则，在白色背景上打印黑色 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-154">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="d13e4-155">如果代码的背景较暗，则尝试使用黑色的灰色代码（如果检测频率较低）。</span><span class="sxs-lookup"><span data-stu-id="d13e4-155">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="d13e4-156">如果背景相对较轻，则常规代码应正常工作。</span><span class="sxs-lookup"><span data-stu-id="d13e4-156">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="d13e4-157">QR 码的大小</span><span class="sxs-lookup"><span data-stu-id="d13e4-157">Size of QR codes</span></span>
<span data-ttu-id="d13e4-158">Windows Mixed Reality 设备不适用于每个边小于 5 cm 的 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-158">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="d13e4-159">对于介于 5 cm 到 10 cm 长度之间的 QR 码，必须非常接近检测代码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-159">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="d13e4-160">它还需要更长的时间来检测此大小的代码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-160">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="d13e4-161">检测代码的确切时间不仅取决于 QR 码的大小，还取决于代码的距离。</span><span class="sxs-lookup"><span data-stu-id="d13e4-161">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="d13e4-162">接近代码会有助于偏移大小问题。</span><span class="sxs-lookup"><span data-stu-id="d13e4-162">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="d13e4-163">QR 代码的距离和角度位置</span><span class="sxs-lookup"><span data-stu-id="d13e4-163">Distance and angular position from the QR code</span></span>
<span data-ttu-id="d13e4-164">跟踪相机只能检测到特定级别的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d13e4-164">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="d13e4-165">对于小代码-沿两侧 < 10 厘米-必须非常接近。</span><span class="sxs-lookup"><span data-stu-id="d13e4-165">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="d13e4-166">对于版本 1 QR 码，从10厘米到 25 cm，最小检测距离范围为0.15 米到0.5 米。</span><span class="sxs-lookup"><span data-stu-id="d13e4-166">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="d13e4-167">大小的检测距离线性增加，但也依赖于 QR 版本或模块大小。</span><span class="sxs-lookup"><span data-stu-id="d13e4-167">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="d13e4-168">版本越高，模块就越小，只能从更近的位置检测到它们。</span><span class="sxs-lookup"><span data-stu-id="d13e4-168">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="d13e4-169">如果希望检测的距离更长，还可以尝试微 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-169">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="d13e4-170">QR 检测适用于一系列角度 + = 45 度，以确保我们有合适的分辨率来检测代码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-170">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d13e4-171">请始终确保有足够的对比度和正确的边框。</span><span class="sxs-lookup"><span data-stu-id="d13e4-171">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="d13e4-172">带有徽标的 QR 码</span><span class="sxs-lookup"><span data-stu-id="d13e4-172">QR codes with logos</span></span>
<span data-ttu-id="d13e4-173">带有徽标的 QR 码尚未经过测试，当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="d13e4-173">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="d13e4-174">管理 QR 码数据</span><span class="sxs-lookup"><span data-stu-id="d13e4-174">Managing QR code data</span></span>
<span data-ttu-id="d13e4-175">Windows Mixed Reality 设备检测驱动程序的系统级别的 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-175">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="d13e4-176">设备重新启动后，检测到的 QR 码已消失，并将在下次重新检测为新对象。</span><span class="sxs-lookup"><span data-stu-id="d13e4-176">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="d13e4-177">建议将应用配置为忽略特定时间戳之前的 QR 码。</span><span class="sxs-lookup"><span data-stu-id="d13e4-177">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="d13e4-178">目前，API 不支持清除 QR 码历史记录。</span><span class="sxs-lookup"><span data-stu-id="d13e4-178">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="d13e4-179">空格中的 QR 码位置</span><span class="sxs-lookup"><span data-stu-id="d13e4-179">QR code placement in a space</span></span>
<span data-ttu-id="d13e4-180">有关在何处以及如何放置 QR 码的建议，请参阅 [HoloLens 环境注意事项](/hololens/hololens-environment-considerations)。</span><span class="sxs-lookup"><span data-stu-id="d13e4-180">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="d13e4-181">QR API 参考</span><span class="sxs-lookup"><span data-stu-id="d13e4-181">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d13e4-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d13e4-182">See also</span></span>
* [<span data-ttu-id="d13e4-183">坐标系统</span><span class="sxs-lookup"><span data-stu-id="d13e4-183">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="d13e4-184"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="d13e4-184"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>