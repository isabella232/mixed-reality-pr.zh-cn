---
title: Unity 中的照片/视频摄像头
description: 了解如何将照片捕获到文件或 Texture2D、如何捕获照片以及与原始字节交互，以及如何捕获视频。
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: 照片， 视频， hololens， 相机， unity， 可定位， PVC， 照片视频相机， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， 网络摄像头， 照片捕获， 视频捕获
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193501"
---
# <a name="photo-video-camera-in-unity"></a>Unity 中的照片/视频摄像头

## <a name="enabling-the-capability-for-camera-access"></a>启用相机访问功能

必须为应用声明"WebCam"功能，以使用 [相机](../platform-capabilities-and-apis/locatable-camera.md)。

1. 在 Unity 编辑器中，导航到"编辑播放器> Project 设置 >播放器设置"
2. 选择"Windows Store"选项卡
3. 在"发布设置 >功能"部分中，检查 **WebCam** 和 **麦克风** 功能

一次只能对相机执行一个操作。 可以在 Unity 2018 及更早版本或 `UnityEngine.XR.WSA.WebCam.Mode` Unity 2019 及更高版本中检查相机当前 `UnityEngine.Windows.WebCam.Mode` 处于哪种模式。 可用模式包括照片、视频或无模式。

## <a name="photo-capture"></a>照片捕获

**Unity 2019 (** 的命名空间) ：UnityEngine.XR.WSA.WebCam <br>
**Unity (2019 及更高版本** 的命名空间) *UnityEngine.Windows。WebCam*<br>
**类型***：PhotoCapture*

*PhotoCapture* 类型允许使用照片相机拍摄静止照片。 使用 *PhotoCapture* 拍摄照片的一般模式如下：

1. 创建 *PhotoCapture* 对象
2. 使用 *想要的设置创建 CameraParameters* 对象
3. 通过 *StartPhotoModeAsync 启动照片模式*
4. 拍摄想要的照片
    *  (可选) "与图片交互"
5. 停止照片模式并清理资源

### <a name="common-set-up-for-photocapture"></a>PhotoCapture 的常见设置

对于这三种用途，请从上述前三个步骤开始

首先创建 *PhotoCapture* 对象

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

接下来，存储对象、设置参数并启动照片模式

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

最后，还将使用此处介绍的相同清理代码

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

执行这些步骤后，可以选择要捕获的照片类型。

### <a name="capture-a-photo-to-a-file"></a>将照片捕获到文件

最简单的操作是直接将照片捕获到文件。 照片可以保存为 JPG 或 PNG。

如果成功启动照片模式，请拍摄照片，并存储在磁盘上

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

将照片捕获到磁盘后，退出照片模式，然后清理对象

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>将照片捕获到具有位置的 Texture2D

将数据捕获到 Texture2D 时，该过程类似于捕获到磁盘。

按照上述安装过程操作。

在 *OnPhotoModeStarted* 中，将帧捕获到内存。

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

然后，将结果应用于纹理，并使用上述常见清理代码。

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a>可定位相机

若要将此纹理放在场景中，然后使用可定位的相机矩阵显示它，请在检查中将以下代码添加到 *OnCapturedPhotoToMemory：* `result.success`

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[Unity 提供了示例代码](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) ，用于将投影矩阵应用到其论坛上的特定着色器。

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>捕获照片并与原始字节交互

若要与内存中帧的原始字节进行交互，请遵循与上面和 *OnPhotoModeStarted* 相同的设置步骤，如将照片捕获到 Texture2D 中一样。 不同之处在于 *OnCapturedPhotoToMemory，* 可在其中获取原始字节并与之交互。

本示例将创建一个 *列表 <Color>*，用于通过 *SetPixels* () 

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a>视频视频

**Unity 2019 (** 的命名空间) ：UnityEngine.XR.WSA.WebCam <br>
**Unity (2019 及更高版本** 的命名空间) *UnityEngine.Windows。WebCam*<br>
**类型***：VideoCapture*

*VideoCapture* 函数类似于 *PhotoCapture*。 唯一的两个区别是，必须指定每秒帧数 (FPS) 值，并且只能直接保存到磁盘作为.mp4文件。 使用 *VideoCapture* 的步骤如下所示：

1. 创建 *VideoCapture* 对象
2. 使用 *想要的设置创建 CameraParameters* 对象
3. 通过 *StartVideoModeAsync 启动视频模式*
4. 开始录制视频
5. 停止录制视频
6. 停止视频模式并清理资源

首先创建 *VideoCapture* 对象 *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

接下来，设置记录时需要的参数并启动。

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

开始后，开始录制

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

开始录制后，可以更新 UI 或行为以启用停止。 在这里，只需记录。

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

例如，稍后需要使用计时器或用户输入来停止录制。

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

停止录制后，停止视频模式并清理资源。

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a>疑难解答

* 没有可用的解决方法
  * 确保在项目中指定 **WebCam** 功能。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发检查点旅程，则你正在探索混合现实平台功能和 API。 从这里，你可以继续了解下一个主题：

> [!div class="nextstepaction"]
> [焦点](focus-point-in-unity.md)

或直接跳到在设备或模拟器上部署应用：

> [!div class="nextstepaction"]
> [部署到HoloLens或Windows Mixed Reality沉浸式头戴显示设备](../platform-capabilities-and-apis/using-visual-studio.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另请参阅

* [可定位相机](../platform-capabilities-and-apis/locatable-camera.md)