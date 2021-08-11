---
title: Unreal 中的 WinRT
description: 了解如何在适用于 HoloLens 设备的 Unreal mixed reality 应用中编写和管理自定义 WinRT 功能。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，流式处理，远程处理，混合现实，开发，入门，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，WinRT，DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198368"
---
# <a name="winrt-in-unreal"></a>Unreal 中的 WinRT

在 HoloLens 开发过程中，可能需要使用 WinRT 编写功能。 例如，在 HoloLens 应用程序中打开文件对话需要 winrt/Windows 中的 FileSavePicker。存储。选取器 .h 标头文件。 从版本4.26 开始，Unreal 的生成系统支持 WinRT。

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发历程，则你处于探索混合现实平台功能和 API 的过程之中。 在这里，你可以继续阅读任何 [主题](unreal-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或模拟器上部署你的应用程序。

> [!div class="nextstepaction"]
> [部署到设备](unreal-deploying.md)

## <a name="see-also"></a>另请参阅

* [C + +/WinRT Api](/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker 类](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal 第三方库](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)