---
title: 在 Unreal 中升级项目
description: 简要介绍 Unreal 项目中的版本升级步骤和已弃用的 API。
author: hferrone
ms.author: v-hferrone
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: efad783ee199ed42c7355917a180855b3ec4f11b
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355638"
---
# <a name="upgrading-projects-in-unreal"></a>在 Unreal 中升级项目

更新到新版本的 Unreal 后，在编译蓝图或打包项目时，已弃用的函数将显示为“警告”。  如果已添加新函数，且应改为使用此函数，那么这些函数会被弃用。 

## <a name="426-upgrades"></a>4.26 版升级
 
在 4.26 版本中，所有 AR 和 VR 平台都已经过重构，添加了常见接口，且仍然与应用程序代码平台无关。  由于此重构，更新到 4.26 版的 HoloLens 项目看到的警告可能比平时的多。  建议更新到新的 API，使项目能够更轻松地移植到其他平台。

警报消息将显示哪个函数已被弃用，并指出该改用哪个函数。  所有已弃用的函数都将继续适用于此版本，但可能在未来版本中失效。  在蓝图中搜索函数时，也将不再列出已弃用的函数。

![Create Named ARPin 函数的蓝图](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>4.25 版弃用项

| 弃用的函数 | 新建函数 |
| --- | --- |
| CreateNamedARPin | ![Pin Component 函数的蓝图](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Load ARPins from Local Store 函数的蓝图](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Save ARPin to Local Store 函数的蓝图](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Remove ARPin from Local Store 函数的蓝图](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Set Enabled XRCamera 函数的蓝图](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Resize XRCamera 函数的蓝图](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![用于启动摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![用于停止摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![用于启动 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![用于停止 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-11.png) |
| 空间映射之前自动在 4.25 版中启动，但现在 4.26 版中需要进行切换。 | ![用于启用空间映射的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-12.png) |
| ShowKeyboard | 已在 4.26 版中删除，这是因为当焦点在文本小组件上时，会自动显示键盘。 |
| HideKeyboard | 已在 4.26 版中删除，这是因为当焦点不在文本小组件上时，将自动隐藏键盘。 |
| SupportsHandTracking | ![“支持手部跟踪”属性的蓝图](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![IsDisplayOpaque 属性的蓝图](images/unreal-porting-img-14.png) |
| GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus | ![Get Motion Controller Data 函数的蓝图](images/unreal-porting-img-15.png) |
| GetVersionString | ![Get Version String 函数的蓝图](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![IsTrackingAvailable 属性的蓝图](images/unreal-porting-img-17.png) |
| IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed | 使用 Unreal 的输入操作系统。 |
| SetFocusPointForFrame | 已在 4.26 版中删除。  之前，它用于在远程时重新投影，而现在支持深度重新投影。 |