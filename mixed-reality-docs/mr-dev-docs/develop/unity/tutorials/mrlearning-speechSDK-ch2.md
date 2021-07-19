---
title: 使用 Azure 语音识别执行命令
description: 完成本课程，了解如何在混合现实应用程序中使用 Azure 语音识别执行命令。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 8d031896a1725c0121272b68578016edf38a36cf
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656619"
---
# <a name="2-execute-commands-using-azure-speech-recognition"></a>2. 使用 Azure 语音识别执行命令

在本教程中，你将添加使用 Azure 语音识别执行命令的功能，以便可以根据定义的单词或短语执行一些操作。

## <a name="objectives"></a>目标

* 了解如何使用 Azure 语音识别执行命令

## <a name="instructions"></a>说明

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 唤醒字词识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：  

* 在“唤醒字词”字段中输入适当的短语，例如“激活终端”。
* 在“解除字词”字段中输入适当的短语，例如“解除终端”。

![Unity 编辑器，其中 Lunarcom 唤醒字词识别器脚本组件突出显示](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> MRTK 中未包含“Lunarcom 唤醒字词识别器(脚本)”组件。 本教程的资产中随附了该组件。

如果现在进入“游戏”模式，与在上一篇教程中一样，默认已启用终端面板，但你现在可以通过讲出解除字词“解除终端”来禁用它：

![播放模式中的 Unity 编辑器，其中语音识别器功能正在使用](images/mrlearning-speech/tutorial2-section1-step1-2.png)

讲出唤醒字词“激活终端”以再次启用终端面板：

![播放模式中的 Unity 编辑器，带有活动终端](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> 应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。

> [!TIP]
> 如果你预计经常无法连接到 Azure，还可以按照[使用语音命令](mr-learning-base-09.md)说明，使用 MRTK 实现语音命令。

## <a name="congratulations"></a>祝贺

现已实现了由 Azure 提供支持的语音命令。 请在设备上运行该应用程序，以确保功能正常。

下一篇教程将介绍如何使用 Azure 语音翻译来翻译语音。

> [!div class="nextstepaction"]
> [下一教程：3.添加 Azure 认知服务语音翻译组件](mrlearning-speechSDK-ch3.md)
