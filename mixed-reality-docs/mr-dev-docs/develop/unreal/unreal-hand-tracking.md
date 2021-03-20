---
title: Unreal 中的手部跟踪
description: 了解如何在 Unreal mixed reality 应用中使用手跟踪输入、姿势、手写网格和实时链接动画。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，手动跟踪，Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，混合现实，开发，功能，文档，指南，全息影像，游戏开发，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 415a0773586ab232e925fd0f18a3a8e6f8217e88
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695795"
---
# <a name="hand-tracking-in-unreal"></a>Unreal 中的手部跟踪

手写跟踪系统使用用户的不要和手指作为输入。 每个手指的位置和旋转数据都可用。 从 Unreal 4.26 开始，手动跟踪基于 Unreal HeadMountedDisplay 插件，并在所有 XR 平台和设备上使用公共 API。 对于 Windows Mixed Reality 和 OpenXR 系统，功能是相同的。

## <a name="hand-pose"></a>举手

使用举手功能，您可以跟踪和使用用户的手和手指作为输入，可在蓝图和 c + + 中访问。 Unreal API 以坐标系统的形式发送数据，并使用 Unreal 引擎同步刻度。

![带有接点叠加的手形图像 ](images/hand-tracking-img-02.png)
 ![ 手形框架](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>手动实时链接动画

使用 [实时链接插件](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)向动画显示手姿势。

如果启用了 Windows Mixed Reality 和 Live Link 插件：
1. 选择 " **窗口 >" 实时链接** "，打开" 实时链接编辑器 "窗口。
2. 选择 **源** 并启用 **Windows Mixed Reality 手动跟踪源**

![实时链接源](images/unreal/live-link-source.png)

启用源并打开动画资产后，展开 "**预览场景**" 选项卡中的 "**动画**" 部分也会显示其他选项。

![实时链接动画](images/unreal/live-link-animation.png)

手型动画层次结构与在中相同 `EWMRHandKeypoint` 。 动画可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定向：

![实时链接动画2](images/unreal/live-link-animation2.png)

还可以在编辑器中将它作为子类：

![实时链接重新映射](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>手写网格

### <a name="hand-mesh-as-a-tracked-geometry"></a>手动网格作为跟踪的几何图形

> [!IMPORTANT]
> 若要在 OpenXR 中将手写网格作为跟踪的几何获取，则需要调用 **已启用跟踪几何** 的 "**使用手网格**"。

若要启用该模式，应调用 **已启用跟踪几何** 的 "**使用手网格**"：

![事件开始播放的蓝图连接到已启用跟踪几何模式的 "使用手写" 功能](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> 不可能同时启用这两种模式。 如果启用，则会自动禁用另一个。

### <a name="accessing-hand-mesh-data"></a>访问手写网格数据

![手写网格](images/unreal/hand-mesh.png)

在可以访问手写网格数据之前，你需要：
- 选择 **ARSessionConfig** 资产，展开 " **AR 设置->** " "世界" 映射设置，然后选中 " **根据跟踪的几何生成网格数据**"。

下面是默认的网格参数：

1.  将网格数据用于封闭
2.  为网格数据生成冲突
3.  为网格数据生成导航网格
4.  以线框–用于显示生成的网格的 debug 参数呈现网格数据

这些参数值用作空间映射网格和手写网格默认值。 你可以在任何网格的蓝图或代码中随时对其进行更改。

### <a name="c-api-reference"></a>C + + API 参考
用于 `EEARObjectClassification` 查找所有以可跟踪对象中的手写网格值。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

当系统检测到任何以可跟踪对象（包括手写网格）时，将调用以下委托。

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

请确保委托处理程序遵循下面的函数签名：

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

可以通过以下操作访问网格数据  `UARTrackedGeometry::GetUnderlyingMesh` ：

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>蓝图 API 参考

若要在蓝图中使用手写网格：
1. 将 **ARTrackableNotify** 组件添加到蓝图参与者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. 请参阅 " **详细信息** " 面板，展开 " **事件** " 部分。

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. 添加/更新/删除跟踪的几何图形时覆盖事件图中的以下节点：

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>OpenXR 中的手写图形可视化效果

可视化手写网格的建议方法是将长篇故事的 XRVisualization 插件与 [Microsoft OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)结合使用。 

然后，在蓝图编辑器中，应使用 **启用了 XRVisualization** 的 [Microsoft OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)中的 "**使用手网格**" 功能作为参数：

![事件开始播放的蓝图已连接到已启用 xrvisualization 模式的 "使用手动网格" 功能](images/unreal-hand-tracking-img-05.png)

若要管理呈现过程，应使用 XRVisualization 中的 **Render 运动控制器** ：

![连接到呈现运动控制器函数的 get 运动控制器数据函数蓝图](images/unreal-hand-tracking-img-06.png)

结果：

![重叠的数字手图像](images/unreal-hand-tracking-img-07.png) 

如果需要更复杂的内容，如使用自定义着色器绘制手写网格，则需要将网格作为跟踪的几何获取。 

## <a name="hand-rays"></a>手部射线

手动姿势用于接近对象或按下按钮等关闭交互。 但是，有时您需要使用离用户更远的全息影像。 这可以使用手动光线完成，可在 c + + 和蓝图中用作指针设备。 您可以从手中将一条射线绘制到远处，并在 Unreal ray 跟踪的情况下，选择一种在其他情况下不会到达的全息图。 

> [!IMPORTANT]
> 由于所有函数结果都会更改每个帧，因此它们都是可调用的。 有关纯函数和非纯函数或可调用函数的详细信息，请参阅蓝图用户 guid on [函数](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)。

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>笔势

HoloLens 2 跟踪空间手势，这意味着您可以将这些手势捕获为输入。 手势跟踪基于订阅模型。 应使用 "配置手势" 功能告诉设备要跟踪的手势。 可以在 [HoloLens 2 基本使用](/hololens/hololens2-basic-usage) 文档中找到有关手势的更多详细信息。

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [本地空间定位点](unreal-spatial-anchors.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。