---
title: 添加 Azure 认知服务语音翻译组件
description: 在本课程中，你将学习如何在混合现实应用程序中添加 Azure 认知服务语音翻译。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10, 语音翻译
ms.localizationpriority: high
ms.openlocfilehash: b6172ff5d313cadb3a270fdf4b6a56f45e924e97ec92d071d5c6b0e4636bd658
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202067"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3.添加 Azure 认知服务语音翻译组件

在本教程中，你将在项目中添加语音翻译，以便可以将语音翻译和听录成三种不同的语言。

## <a name="objectives"></a>目标

* 了解如何集成 Azure 语音翻译

## <a name="instructions"></a>说明

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 翻译识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：   

* 将“目标语言”更改为所选语言，例如“德语”  

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> MRTK 中未包含“Lunarcom 翻译识别器(脚本)”组件。 本教程的资产中随附了该组件。

如果现在进入“游戏”模式，可以先按卫星按钮来测试语音翻译。 假设计算机上配备了麦克风，当你讲话时，你的语音将翻译成所选语言，并在终端面板上听录：

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> 应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

项目现在可以成功地将你讲出的词语翻译成多种不同的语言。 请在设备上运行该应用程序，以确保功能正常。

> [!div class="nextstepaction"]
> [下一教程：4.设置意向和自然语言理解](mrlearning-speechSDK-ch4.md)
