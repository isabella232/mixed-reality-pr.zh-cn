---
title: 可定位相机
description: 有关面向HoloLens相机、工作原理以及可供开发人员使用配置文件和分辨率的常规信息。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: camera， hololens， 彩色相机， 前置， hololens 2， cv， 计算机视觉， fiducial， 标记， qr 码， qr， 照片， 视频
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217093"
---
# <a name="locatable-camera"></a>可定位相机

HoloLens包括安装在设备正面的面向世界相机，使应用能够查看用户看到的信息。 开发人员可以访问和控制相机，就像在智能手机、笔记本电脑或台式机上使用彩色相机一样。 在移动[和桌面上](/uwp/api/Windows.Media.Capture.MediaCapture)工作的相同通用 Windows 媒体捕获和 Windows 媒体基础 API HoloLens。 Unity[已包装这些 Windows API，](../unity/locatable-camera-in-unity.md)以在 HoloLens 上抽象相机使用HoloLens。 功能任务包括使用或 (全息影像拍摄常规) 以及定位相机在场景中的位置和透视。

## <a name="device-camera-information"></a>设备相机信息

### <a name="hololens-first-generation"></a>HoloLens (第一代) 

* 修复了具有自动 () 自动白平衡、自动曝光和完整图像处理管道的 PV 相机焦点照片/视频。
* 每当摄像头处于活动状态时，面向全球的白色隐私 LED 都会亮起
* 相机支持以下模式 (所有模式在 30、24、20、15 和 5 fps) 16：9 纵横比：

  |  视频  |  预览  |  还  |  水平视场 (H-FOV)  |  建议的用法 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45 deg  |   (具有视频稳定功能的默认)  | 
  |  不适用 |  不适用 |  2048x1152 |  67 deg |  最高分辨率的静止图像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  在视频 (之前) 过度扫描填充) 分辨率 | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  具有过度扫描的大型 FOV 视频模式 | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  图像处理任务的低功率/低分辨率模式 | 

### <a name="hololens-2"></a>HoloLens 2

* 自动聚焦照片/视频 (PV) 相机，具有自动白平衡、自动曝光和完整的图像处理管道。
* 每当摄像头处于活动状态时，面向全球的白色隐私 LED 都会亮起。
* HoloLens 2支持不同的相机配置文件。 了解如何发现 [和选择相机功能](/windows/uwp/audio-video-camera/camera-profiles)。
* 相机支持以下配置文件和分辨率 (所有视频模式都为 16：9 纵横比) ：
  
  | 配置文件                                         | 视频     | 预览   | 还     | 帧速率 | 水平视场 (H-FOV)  | 建议的用法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy，0 BalancedVideoAndPhoto，100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | 高质量的视频录制                |
  | Legacy，0 BalancedVideoAndPhoto，100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | 用于高质量照片捕获的预览流 |
  | Legacy，0 BalancedVideoAndPhoto，100             |           |           | 3904x2196 |             | 64.69                            | 高质量的照片捕获                  |
  | BalancedVideoAndPhoto， 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | 长持续时间方案                     |
  | BalancedVideoAndPhoto， 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | 长持续时间方案                     |
  | VideoConferencing，100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | 视频会议，持续时间长的方案 |
  | 中国，100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 1128x636  |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 960x540   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 760x428   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 640x360   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 500x282   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 100 BalancedVideoAndPhoto，120 | 424x240   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |

> [!NOTE]
> 客户可以利用 [混合现实捕获](/hololens/holographic-photos-and-videos) 来拍摄应用的视频或照片，包括全息影像和视频稳定。
>
>作为开发人员，如果希望应用在客户捕获内容时看起来尽可能好，则创建应用时应考虑一些注意事项。 还可以直接在 (中) 和自定义混合现实捕获。 在开发人员 [的混合现实捕获中了解有关详细信息](mixed-reality-capture-for-developers.md)。

## <a name="locating-the-device-camera-in-the-world"></a>定位世界中的设备相机

当HoloLens拍摄照片和视频时，捕获的帧包括相机在世界上的位置和相机的镜头模型。 这样，应用程序可以针对增强的图像处理方案来了解相机在现实世界中的位置。 开发人员可以使用他们最喜欢的图像处理或自定义计算机视觉库，以创意方式滚动自己的方案。

文档中其他位置HoloLens"相机"可引用应用呈现到 (的"虚拟游戏) 。 除非另有说明，否则此页上的"相机"是指真实的 RGB 彩色相机。

### <a name="using-unity"></a>使用 Unity

若要从"CameraIntrinsics"和"CameraCoordinateSystem"转到应用程序/世界坐标系，请按照 [Unity](../unity/locatable-camera-in-unity.md) 中可定位相机一文的说明进行操作。  CameraToWorldMatrix 由 PhotoCaptureFrame 类自动提供，因此无需担心下面讨论的 CameraCoordinateSystem 转换。

### <a name="using-mediaframereference"></a>使用 MediaFrameReference

如果使用 [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) 类从相机读取图像帧，则这些说明适用。

每个图像帧 (照片或视频) 是否包含捕获时位于相机的[SpatialCoordinateSystem，](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)可以使用[MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)属性访问该空间帧。 每个帧都包含相机镜头模型的说明，可在 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 属性中找到。 这些转换共同为每个像素定义 3D 空间中表示生成像素的光子所拍摄路径的射线。 这些射线可以通过从框架的坐标系转换为其他坐标系 (例如，从固定参考框架获取) 。这些射线可以与应用中的其他[内容相关。](../../design/coordinate-systems.md#stationary-frame-of-reference) 

每个图像帧提供以下内容：
* 像素数据 (RGB/NV12/JPEG 等格式) 
* 捕获[位置中的 SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 包含 [相机的镜头模式的 CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 类

[HolographicFaceTracking 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)演示了查询相机坐标系和你自己的应用程序坐标系之间的转换的非常简单的方法。

### <a name="using-media-foundation"></a>使用 媒体基础

如果直接使用 媒体基础 从相机读取图像帧，可以使用每个帧的 [MFSampleExtension_CameraExtrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) 属性和 [MFSampleExtension_PinholeCameraIntrinsics](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 属性来查找相对于应用程序的其他坐标系的相机帧，如此示例代码所示：

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>扭曲错误

在HoloLens，在将帧提供给应用程序之前，视频和静止图像流不会在系统的图像处理管道中公开 (预览流包含原始的扭曲帧) 。 由于只有 CameraIntrinsics 可用，因此应用程序必须假设图像帧代表完美引脚相机。

在HoloLens (第一代) ，在帧元数据中使用 CameraIntrinsics 时，图像处理器中的不存储函数仍可能会保留最多 10 像素的错误。 在许多用例中，此错误并不重要，但例如，如果将全息影像与现实世界的海报/标记对齐，并且你注意到定位在 2 米外) 的全息影像的 <10-px 偏移量 (约为 11 mm，则这种扭曲错误可能是原因。 

## <a name="locatable-camera-usage-scenarios"></a>可定位相机使用方案

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>在捕获照片或视频的世界上显示照片或视频

设备相机帧具有"相机到世界"转换，可用于准确显示拍摄图像时设备位置。 例如，你可以在此位置放置一个小全息图标 (CameraToWorld.MultiplyPoint (Vector3.0) ) ，甚至可以在相机面向 (CameraToWorld.MultiplyVector (Vector3.forward) ) 的方向绘制一个小箭头。

### <a name="tag--pattern--poster--object-tracking"></a>标记/模式/海报/对象跟踪

许多混合现实应用程序使用可识别的图像或视觉模式在空间中创建可跟踪的点。 然后，它用于呈现相对于该点的对象或创建已知位置。 HoloLens 的一些用途包括查找标有 fiducials (的真实对象，例如带有 QR 码) 的电视监视器、将全息影像放置在 fiducial 上，以及以可视方式与非 HoloLens 设备（例如已设置为通过 Wi-Fi 与 HoloLens 通信的平板电脑）配对。

需要一些内容来识别视觉模式，将对象放在应用程序世界空间中：
1. 图像模式识别工具包，例如 QR 码、AR 标记、人脸查找器、圆形跟踪器、OCR 等。
2. 在运行时收集图像帧，并传递给识别层
3. 将图像位置取消项目处理回世界位置，或者可能是世界射线。 
4. 将虚拟模型定位到这些世界位置

一些重要的图像处理链接：
* [OpenCV](https://opencv.org/)
* [QR 标记](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

保持交互式应用程序帧速率至关重要，尤其是在处理长时间运行的图像识别算法时。 因此，我们通常使用以下模式：
1. 主线程：管理相机对象
2. 主线程：请求异步 (新) 
3. 主线程：将新帧传递给跟踪线程
4. 跟踪线程：处理图像以收集关键点
5. 主线程：移动虚拟模型以匹配找到的要点
6. 主线程：从步骤 2 重复

某些图像标记系统仅提供单个像素位置 (其他部分提供完全转换，在这种情况下，不需要此部分) ，这相当于可能的位置。 若要访问单个3d 位置，我们可以利用多个射线，并按大致交集查找最终结果。 为此需要：
1. 获取正在收集多个照相机图像的循环
2. 查找关联的功能点及其世界光线
3. 如果有一个功能字典，每个功能都有多个世界光线，则可以使用以下代码来解决这些光线的交集：

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

如果有两个或多个跟踪的标记位置，则可以将建模的场景定位到适合用户的当前方案。 如果无法假定重心，则需要三个标记位置。 在许多情况下，我们使用颜色方案，其中白色球体表示实时跟踪标记位置，蓝色球体表示建模标记位置。 这允许用户以直观方式衡量对齐质量。 我们假定在所有应用程序中都进行以下设置：
* 两个或更多模型标记位置
* 一个 "校准空间"，场景是标记的父项
* 相机功能标识符
* 行为，这会移动校准空间，以使模型标记与实时标记对齐 (建议移动父空间，而不是模型标记本身，因为其他连接是相对于它们) 的位置。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>使用 Led 或其他识别器库跟踪或确定标记为静止或移动现实世界对象/面部

示例:
* 工业机器人，其中包含 Led (或用于速度缓慢移动对象的 QR 码) 
* 标识并识别房间中的对象
* 标识并识别房间中的人员，例如，将全息联系人卡片置于面部上

## <a name="see-also"></a>另请参阅
* [定位相机示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Unity 中的可定位相机](../unity/locatable-camera-in-unity.md)
* [混合现实捕获](/hololens/holographic-photos-and-videos)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [媒体捕获简介](/windows/uwp/audio-video-camera/)
* [全息面部跟踪示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)