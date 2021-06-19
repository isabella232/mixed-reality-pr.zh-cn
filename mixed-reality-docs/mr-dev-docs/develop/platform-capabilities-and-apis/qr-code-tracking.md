---
title: QR 码跟踪
description: 了解如何检测 QR 码、添加网络摄像头功能，以及如何在混合现实应用中管理HoloLens 2。
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr， lbe， 基于位置的娱乐， vr 如果， 沉浸式， qr， qr 码， hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394331"
---
# <a name="qr-code-tracking"></a>QR 码跟踪

HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。 启用设备的网络摄像头后，你将能够识别最新版本的 Unreal 或 Unity 项目中的 QR 码。 在进入生产环境之前，我们建议遵循本文末尾[](#best-practices-for-qr-code-detection)介绍的最佳实践。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (第一代) </a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> QR 码检测</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>桌面电脑上的沉浸式Windows Mixed Reality头戴显示设备支持 QR 码跟踪Windows 10版本 2004 及更高版本。 使用 Microsoft.MixedReality.QRCodeWatcher.IsSupported () API 来确定当前设备上是否支持该功能。

## <a name="getting-the-qr-package"></a>获取 QR 包

可在此处下载用于 QR 代码检测的 NuGet [包](https://nuget.org/Packages/Microsoft.MixedReality.QR)。

## <a name="using-openxr"></a>使用 OpenXR

使用 OpenXR 插件时，从[ `SpatialGraphNodeId` QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)获取 ，并使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 查找 QR 代码。

有关参考，我们在 GitHub 上提供了一个[QR](https://github.com/yl-msft/QRTracking)跟踪示例项目，并详细介绍[ `SpatialGraphNode` 了 API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的用法说明。

## <a name="detecting-qr-codes"></a>检测 QR 码

### <a name="adding-the-webcam-capability"></a>添加网络摄像头功能

需要将功能添加到清单以检测 `webcam` QR 码。 此功能是必需的，因为用户环境中检测到的代码内的数据可能包含敏感信息。

可以通过调用 请求权限 `QRCodeWatcher.RequestAccessAsync()` ：

_C#：_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++：_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

在构造 QRCodeWatcher 对象之前，必须请求权限。

虽然 QR 码检测需要 `webcam` 该功能，但检测是使用设备的跟踪相机进行。 与使用 PV 相机检测设备的照片/视频相比，这提供了更广泛的检测 FOV 和 () 时间。

### <a name="detecting-qr-codes-in-unity"></a>在 Unity 中检测 QR 代码

通过使用 [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity)安装 NuGet 包，可以在 Unity 中使用 QR 代码检测 API，而无需导入 MRTK。 若要了解工作原理，请下载 [示例 Unity 应用](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)。 示例应用提供了在 QR 码和关联数据（例如 GUID、物理大小、时间戳和解码数据）上显示全息正方形的示例。

### <a name="detecting-qr-codes-in-c"></a>在 C++ 中检测 QR 代码

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>获取 QR 码的坐标系统

每个检测到的 QR 代码[](../../design/coordinate-systems.md)都公开一个空间坐标系，该系统与左上角快速检测正方形左上角的 QR 码对齐：  

![QR 码坐标系统](images/Qr-coordinatesystem.png) 

直接使用 QR SDK 时，Z 轴指向纸张 (未显示) - 转换为 Unity 坐标时，Z 轴从纸张中指向并向左。

QR 码的 SpatialCoordinateSystem 按如下所示对齐。 可以通过调用 <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：：CreateCoordinateSystemForNode</a> 并传递代码的 SpatialGraphNodeId，从平台获取坐标系。

下面的 C++ 代码演示如何使用 QR 码的坐标系创建并放置矩形：

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

可以使用物理大小创建 QR 矩形：

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

坐标系统可用于绘制 QR 码或将全息影像附加到位置：

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

总之 *，QRCodeAddedHandler* 可能如下所示：

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

## <a name="best-practices-for-qr-code-detection"></a>QR 代码检测最佳做法

### <a name="quiet-zones-around-qr-codes"></a>QR 码周围的静默区域

若要正确阅读，QR 码需要代码所有边侧的边距。 此边距不得包含任何打印内容，并且应为四个模块， (代码中的单个黑色正方形) 宽。 

[QR 规范](https://www.qrcode.com/en/howto/code.html)包含有关静默区域详细信息。

### <a name="lighting-and-backdrop"></a>照明和背景
QR 码检测质量容易受到各种照明和背景的影响。 

在具有亮光的场景中，在灰色背景上打印黑色代码。 否则，在白色背景上打印黑色 QR 码。

如果代码的背景为深色，如果检测率较低，请尝试在灰色代码上显示黑色。 如果背景相对浅，则常规代码应该可以正常工作。

### <a name="size-of-qr-codes"></a>QR 码的大小
Windows Mixed Reality设备无法处理每个边小于 5 cm 的 QR 码。

对于长度在 5 cm 到 10 cm 之间的 QR 码，必须非常接近以检测代码。 检测此大小的代码还需要更长时间。 

检测代码的确切时间不仅取决于 QR 码的大小，还取决于与代码的距离。 越接近代码，有助于偏移大小问题。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 码的距离和角度位置
跟踪相机只能检测特定级别的详细信息。 对于边边< 10 cm 的小代码，必须非常接近。 对于从 10 cm 到 25 cm 宽的 1 版 QR 码，最小检测距离范围为 0.15 米到 0.5 米。 

大小的检测距离呈线性增加，但也取决于 QR 版本或模块大小。 版本越高，模块越小，只能从更靠近的位置检测到。 如果希望检测距离更长，还可以尝试微 QR 码。 QR 检测使用角度 += 45 deg 的范围，以确保我们具有适当的分辨率来检测代码。

> [!IMPORTANT]
> 请始终确保有足够的对比度和适当的边框。

### <a name="qr-codes-with-logos"></a>具有徽标的 QR 码
带徽标的 QR 码尚未经过测试，当前不受支持。

### <a name="managing-qr-code-data"></a>管理 QR 代码数据
Windows Mixed Reality设备在驱动程序的系统级别检测 QR 码。 重新启动设备时，检测到的 QR 码将消失，下次将重新检测为新对象。

建议将应用配置为忽略超过特定时间戳的 QR 码。 目前，API 不支持清除 QR 代码历史记录。

### <a name="qr-code-placement-in-a-space"></a>QR 码在空间中的位置
有关放置 QR 码的位置和位置的建议，请参阅 [HoloLens](/hololens/hololens-environment-considerations)的环境注意事项。

## <a name="qr-api-reference"></a>QR API 参考

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

## <a name="see-also"></a>另请参阅
* [坐标系统](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>