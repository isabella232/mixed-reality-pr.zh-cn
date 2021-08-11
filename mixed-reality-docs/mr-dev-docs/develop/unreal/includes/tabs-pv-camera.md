---
ms.openlocfilehash: 45b171d3d5856dd17f9223d945a1d0fd46326600b3ed65bc4198c6da5fa524f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207472"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>PV 摄像头馈送设置

> [!IMPORTANT]
> PV 摄像头是在 Windows Mixed Reality 和 OpenXR 插件中实现的。 不过，OpenXR 要求安装 [Microsoft OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。 此外，OpenXR 目前存在限制，摄像头只能用于 DirectX11 RHI。 这一限制将在后续的 Unreal 版本中得到修复。 

- 在“项目设置”>“HoloLens”中，启用网络摄像头功能 ：

![HoloLens 项目设置的屏幕截图，其中突出显示了网络摄像头属性](../images/unreal-pvc-img-01.png)

- 新建一个名为“CamCapture”的 Actor，再添加一个平面来渲染摄像头馈送：

![已添加平面的 Actor 的屏幕截图](../images/unreal-pvc-img-02.png)

- 将该 Actor 添加到场景中，使用纹理对象参数和纹理示例创建一个名为 CamTextureMaterial 的新材料。  将纹理的 rgb 数据发送到输出自发光颜色：

![材料和纹理示例蓝图](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>渲染 PV 摄像头馈送

- 在 CamCapture 蓝图中，启用 PV 摄像头：

![Toggle ARCapture 函数的蓝图，其中已启用 PV 摄像头](../images/unreal-pvc-img-04.png)

- 从 CamTextureMaterial 创建一个动态材料实例，再将此材料分配到 Actor 的平面：

![Create Dynamic Material Instance 函数的蓝图](../images/unreal-pvc-img-05.png)

- 从摄像头馈送中获取纹理，然后将其分配到动态材料（若有效）。  如果纹理无效，请启动计时器，并在超时后重试：

![分配给动态材料的摄像头馈送纹理的蓝图](../images/unreal-pvc-img-06.png)

- 最后，按相机图像的纵横比缩放平面：

![对照相机图像纵横比进行缩放的平面的蓝图](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>在世界空间中查找摄像头位置

HoloLens 2 上的摄像头在垂直方向上与设备的头部跟踪存在偏移。  有几个函数可用于在世界空间中定位摄像头，以解决偏移问题。

GetPVCameraToWorldTransform 可获取 PV 摄像头的世界空间中的变形，并将其定位在相机镜头上：

![Get PVCamera to World Transform 函数的蓝图](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint 将摄像头中的射线投射到 Unreal 世界空间中的场景，以查找相机帧中像素的内容：

![“从摄像头点获取世界空间射线”的蓝图](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics 会返回摄像头固有值，在相机帧上执行计算机视觉处理时可使用这些值：

![Get PVCamera Intrinsics 函数的蓝图](../images/unreal-pvc-img-10.png)

若要在世界空间中查找特定像素坐标处的内容，请将线条跟踪与世界空间射线一起使用：

![用于在世界空间中查找特定坐标处的内容的世界空间射线的蓝图](../images/unreal-pvc-img-11.png)

在这里，我们将来自摄像头的一条 2 米射线从帧的左上角投射到相机空间位置 ¼ 处。  然后，使用命中结果来渲染对象在世界空间中的位置：

![显示将来自摄像头的一条 2 米射线从帧的左上角投射到相机空间位置 ¼ 处的蓝图](../images/unreal-pvc-img-12.png)

使用空间映射时，此命中位置将与摄像头当前看到的表面匹配。

## <a name="rendering-the-pv-camera-feed-in-c"></a>使用 C++ 渲染 PV 摄像头馈送

- 新建名为 CamCapture 的 C++ Actor
- 在项目的 build.cs 中，向 PublicDependencyModuleNames 列表添加“AugmentedReality”：

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- 在 CamCapture.h 中，包含 ARBlueprintLibrary.h

```cpp
#include "ARBlueprintLibrary.h"
```

- 还需要为网格和材料添加本地变量：

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- 在 CamCapture.cpp 中，更新构造函数来向场景添加静态网格：

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

在 BeginPlay 中，从项目的相机材料创建一个动态材料实例，将它应用于静态网格组件，然后启动 HoloLens 摄像头。 
 
在编辑器中，右键单击内容浏览器中的 CamTextureMaterial，然后选择“复制引用”来获取 CameraMatPath 的字符串。

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

在时钟周期中，从相机获取纹理，在 CamTextureMaterial 材料中将其设置为纹理参数，然后按相机帧的纵横比缩放静态网格组件：

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>从 MRC 的 PV 摄像头渲染

> [!NOTE]
> 这需要 Unreal Engine 4.25 或更高版本。

系统和自定义 MRC 记录器通过将 PV 摄像头与应用渲染的全息影像结合在一起，创建混合现实捕获。

默认情况下，混合现实捕获使用右眼的全息影像输出。 如果沉浸式应用选择[从 PV 摄像头进行渲染](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则会改用它。 从 PV 摄像头进行渲染改进了真实世界与 MRC 视频中全息影像之间的映射。

若要选择从 PV 摄像头进行渲染：

1. 调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera 
    * 使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 

![第三人称摄像头](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

然后，Unreal 将处理 MRC 要从 PV 摄像头的角度进行渲染的请求。

> [!NOTE]
> 仅当触发[混合现实捕获](/hololens/holographic-photos-and-videos)时，才会要求应用从照片/视频摄像头的角度进行渲染。

## <a name="using-the-pv-camera"></a>使用 PV 摄像头

在游戏中，可以在运行时检索网络摄像头纹理，但需要在编辑器的“编辑 > 项目设置”中启用它：
1. 转到“平台 > HoloLens > 功能”，然后选中“网络摄像头”。 
    * 在运行时通过 StartCameraCapture 函数使用网络摄像头，通过 StopCameraCapture 函数停止录像。 

![摄像头开始/停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>渲染图像
渲染摄像头图像：
1. 基于项目中的材料创建动态材料实例，下方的屏幕截图将其命名为“PVCamMat”。  
2. 将动态材料实例设置为“材料实例动态对象引用”变量。  
3. 设置场景中的对象的材料，它会将摄像头源渲染到这个新的动态材料实例。
    * 启动计时器，用于将摄像头图像与材料绑定。

![摄像头渲染](../images/unreal-camera-render.PNG)

4. 为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。   
5. 如果此纹理有效，则将着色器中的纹理参数设置为此图像。  否则，请重新启动材质计时器。

![来自网络摄像头的摄像头纹理](../images/unreal-camera-texture.PNG)

5. 请确保材料的参数与绑定到颜色条目的 SetTextureParameterValue 中的名称匹配。 若没有该参数，便无法正确显示摄像头图像。

![摄像头纹理](../images/unreal-camera-material.PNG)