---
title: ScreenshotUtility
description: Hopw 上关于使用 MRTK 中屏幕截图工具的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6aafcf6602caae94cf69bc62faf02601de830bbd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687886"
---
# <a name="screenshot-utility"></a>屏幕截图实用工具

在 Unity 中拍摄文档和促销图像的屏幕截图通常会很繁琐，而且输出通常会不理想。 这就是 `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) 类的有用之处。

ScreenshotUtility 类可以帮助在 Unity 编辑器中通过菜单项和公共 API 拍摄屏幕截图。 可以以各种分辨率和透明色捕获屏幕截图，以便后期用于轻松组合图像。 此工具不支持从独立版本拍摄屏幕截图。

## <a name="taking-screenshots"></a>拍摄屏幕截图

可以在编辑器中选择“混合现实工具包”->“实用程序”>“拍摄屏幕截图”，然后选择所需的选项，轻松拍摄屏幕截图。 如果在未播放时拍摄，请确保让游戏窗口选项卡可见，否则无法保存屏幕截图。

默认情况下，所有屏幕截图都保存到[临时缓存路径](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)，屏幕截图的路径将显示在 Unity 控制台中。

![屏幕截图实用工具菜单项](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>屏幕截图拍摄示例

以下屏幕截图是使用“4x 分辨率(透明背景)”选项拍摄的。 这会输出高分辨率的图像，其中通常由透明色表示的像素都保留为透明像素。 此方法可将此图像覆盖在其他图像上，帮助开发人员在应用商店或其他媒体渠道中展示其应用程序。

![屏幕截图实用工具拍摄示例](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
