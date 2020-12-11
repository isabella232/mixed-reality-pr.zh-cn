---
ms.openlocfilehash: a8258f1ba99fdd1607014624c4ad4d6ec0a8e330
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609600"
---
# <a name="425"></a>[<span data-ttu-id="8ce2f-101">4.25</span><span class="sxs-lookup"><span data-stu-id="8ce2f-101">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="8ce2f-102">从 MRC 的 PV 摄像头渲染</span><span class="sxs-lookup"><span data-stu-id="8ce2f-102">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="8ce2f-103">这需要 Unreal Engine 4.25 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-103">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="8ce2f-104">系统和自定义 MRC 记录器通过将 PV 摄像头与应用渲染的全息影像结合在一起，创建混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-104">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="8ce2f-105">默认情况下，混合现实捕获使用右眼的全息影像输出。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-105">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="8ce2f-106">如果沉浸式应用选择[从 PV 摄像头进行渲染](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则会改用它。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-106">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="8ce2f-107">从 PV 摄像头进行渲染改进了真实世界与 MRC 视频中全息影像之间的映射。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-107">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="8ce2f-108">若要选择从 PV 摄像头进行渲染：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-108">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="8ce2f-109">调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera </span><span class="sxs-lookup"><span data-stu-id="8ce2f-109">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="8ce2f-110">使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 </span><span class="sxs-lookup"><span data-stu-id="8ce2f-110">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三人称摄像头](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="8ce2f-112">然后，Unreal 将处理 MRC 要从 PV 摄像头的角度进行渲染的请求。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-112">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="8ce2f-113">仅当触发[混合现实捕获](../../../mixed-reality-capture.md)时，才会要求应用从照片/视频摄像头的角度进行渲染。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-113">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="8ce2f-114">使用 PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="8ce2f-114">Using the PV Camera</span></span>

<span data-ttu-id="8ce2f-115">在游戏中，可以在运行时检索网络摄像头纹理，但需要在编辑器的“编辑 > 项目设置”中启用它：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-115">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="8ce2f-116">转到“平台 > HoloLens > 功能”，然后选中“网络摄像头”。 </span><span class="sxs-lookup"><span data-stu-id="8ce2f-116">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="8ce2f-117">在运行时通过 StartCameraCapture 函数使用网络摄像头，通过 StopCameraCapture 函数停止录像。 </span><span class="sxs-lookup"><span data-stu-id="8ce2f-117">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![摄像头开始/停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="8ce2f-119">渲染图像</span><span class="sxs-lookup"><span data-stu-id="8ce2f-119">Rendering an image</span></span>
<span data-ttu-id="8ce2f-120">渲染摄像头图像：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-120">To render the camera image:</span></span>
1. <span data-ttu-id="8ce2f-121">基于项目中的材料创建动态材料实例，下方的屏幕截图将其命名为“PVCamMat”。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-121">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="8ce2f-122">将动态材料实例设置为“材料实例动态对象引用”变量。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-122">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="8ce2f-123">设置场景中的对象的材料，它会将摄像头源渲染到这个新的动态材料实例。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-123">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="8ce2f-124">启动计时器，用于将摄像头图像与材料绑定。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-124">Start a timer that will be used to bind the camera image to the material.</span></span>

![摄像头渲染](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="8ce2f-126">为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。 </span><span class="sxs-lookup"><span data-stu-id="8ce2f-126">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="8ce2f-127">如果此纹理有效，则将着色器中的纹理参数设置为此图像。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-127">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="8ce2f-128">否则，请重新启动材质计时器。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-128">Otherwise, start the material timer again.</span></span>

![来自网络摄像头的摄像头纹理](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="8ce2f-130">请确保材料的参数与绑定到颜色条目的 SetTextureParameterValue 中的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-130">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="8ce2f-131">若没有该参数，便无法正确显示摄像头图像。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-131">Without the parameter, the camera image can't be displayed properly.</span></span>

![摄像头纹理](../images/unreal-camera-material.PNG)

# <a name="426"></a>[<span data-ttu-id="8ce2f-133">4.26</span><span class="sxs-lookup"><span data-stu-id="8ce2f-133">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="8ce2f-134">PV 摄像头馈送设置</span><span class="sxs-lookup"><span data-stu-id="8ce2f-134">PV Camera Feed Setup</span></span>

- <span data-ttu-id="8ce2f-135">在“项目设置”>“HoloLens”中，启用网络摄像头功能 ：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-135">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![HoloLens 项目设置的屏幕截图，其中突出显示了网络摄像头属性](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="8ce2f-137">新建一个名为“CamCapture”的 Actor，再添加一个平面来渲染摄像头馈送：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-137">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![已添加平面的 Actor 的屏幕截图](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="8ce2f-139">将该 Actor 添加到场景中，使用纹理对象参数和纹理示例创建一个名为 CamTextureMaterial 的新材料。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-139">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="8ce2f-140">将纹理的 rgb 数据发送到输出自发光颜色：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-140">Send the texture’s rgb data to the output emissive color:</span></span>

![材料和纹理示例蓝图](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="8ce2f-142">渲染 PV 摄像头馈送</span><span class="sxs-lookup"><span data-stu-id="8ce2f-142">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="8ce2f-143">在 CamCapture 蓝图中，启用 PV 摄像头：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-143">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Toggle ARCapture 函数的蓝图，其中已启用 PV 摄像头](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="8ce2f-145">从 CamTextureMaterial 创建一个动态材料实例，再将此材料分配到 Actor 的平面：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-145">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Create Dynamic Material Instance 函数的蓝图](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="8ce2f-147">从摄像头馈送中获取纹理，然后将其分配到动态材料（若有效）。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-147">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="8ce2f-148">如果纹理无效，请启动计时器，并在超时后重试：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-148">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![分配给动态材料的摄像头馈送纹理的蓝图](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="8ce2f-150">最后，按相机图像的纵横比缩放平面：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-150">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![对照相机图像纵横比进行缩放的平面的蓝图](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="8ce2f-152">在世界空间中查找摄像头位置</span><span class="sxs-lookup"><span data-stu-id="8ce2f-152">Find Camera Positions in World Space</span></span>

<span data-ttu-id="8ce2f-153">HoloLens 2 上的摄像头在垂直方向上与设备的头部跟踪存在偏移。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-153">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="8ce2f-154">有几个函数可用于在世界空间中定位摄像头，以解决偏移问题。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-154">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="8ce2f-155">GetPVCameraToWorldTransform 可获取 PV 摄像头的世界空间中的变形，并将其定位在相机镜头上：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-155">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Get PVCamera to World Transform 函数的蓝图](../images/unreal-pvc-img-08.png)

<span data-ttu-id="8ce2f-157">GetWorldSpaceRayFromCameraPoint 将摄像头中的射线投射到 Unreal 世界空间中的场景，以查找相机帧中像素的内容：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-157">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![“从摄像头点获取世界空间射线”的蓝图](../images/unreal-pvc-img-09.png)

<span data-ttu-id="8ce2f-159">GetPVCameraIntrinsics 会返回摄像头固有值，在相机帧上执行计算机视觉处理时可使用这些值：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-159">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Get PVCamera Intrinsics 函数的蓝图](../images/unreal-pvc-img-10.png)

<span data-ttu-id="8ce2f-161">若要在世界空间中查找特定像素坐标处的内容，请将线条跟踪与世界空间射线一起使用：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-161">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![用于在世界空间中查找特定坐标处的内容的世界空间射线的蓝图](../images/unreal-pvc-img-11.png)

<span data-ttu-id="8ce2f-163">在这里，我们将来自摄像头的一条 2 米射线从帧的左上角投射到相机空间位置 ¼ 处。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-163">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="8ce2f-164">然后，使用命中结果来渲染对象在世界空间中的位置：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-164">Then use the hit result to render something where the object exists in world space:</span></span>

![显示将来自摄像头的一条 2 米射线从帧的左上角投射到相机空间位置 ¼ 处的蓝图](../images/unreal-pvc-img-12.png)

<span data-ttu-id="8ce2f-166">使用空间映射时，此命中位置将与摄像头当前看到的表面匹配。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-166">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="8ce2f-167">使用 C++ 渲染 PV 摄像头馈送</span><span class="sxs-lookup"><span data-stu-id="8ce2f-167">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="8ce2f-168">新建名为 CamCapture 的 C++ Actor</span><span class="sxs-lookup"><span data-stu-id="8ce2f-168">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="8ce2f-169">在项目的 build.cs 中，向 PublicDependencyModuleNames 列表添加“AugmentedReality”：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-169">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="8ce2f-170">在 CamCapture.h 中，包含 ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="8ce2f-170">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="8ce2f-171">还需要为网格和材料添加本地变量：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-171">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="8ce2f-172">在 CamCapture.cpp 中，更新构造函数来向场景添加静态网格：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-172">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

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

<span data-ttu-id="8ce2f-173">在 BeginPlay 中，从项目的相机材料创建一个动态材料实例，将它应用于静态网格组件，然后启动 HoloLens 摄像头。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-173">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="8ce2f-174">在编辑器中，右键单击内容浏览器中的 CamTextureMaterial，然后选择“复制引用”来获取 CameraMatPath 的字符串。</span><span class="sxs-lookup"><span data-stu-id="8ce2f-174">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="8ce2f-175">在时钟周期中，从相机获取纹理，在 CamTextureMaterial 材料中将其设置为纹理参数，然后按相机帧的纵横比缩放静态网格组件：</span><span class="sxs-lookup"><span data-stu-id="8ce2f-175">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

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

