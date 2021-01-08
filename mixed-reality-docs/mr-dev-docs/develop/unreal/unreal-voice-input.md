---
title: Unreal 中的语音输入
description: 了解如何设置和使用适用于 HoloLens 2 设备的 Unreal mixed reality 应用中的语音输入、语音映射和识别。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，Unreal，Unreal 引擎4，UE4，HoloLens 2，语音，语音输入，语音识别，混合现实，开发，功能，文档，指南，全息影像，游戏开发，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010067"
---
# <a name="voice-input-in-unreal"></a>Unreal 中的语音输入

使用 Unreal 中的语音输入，无需使用手手势即可与全息图进行交互，并且仅支持 HoloLens 2。 HoloLens 2 上的语音输入由支持所有其他通用 Windows 应用中的语音的同一引擎提供支持，但 Unreal 使用更有限的引擎来处理语音输入。 这会将 Unreal 中的语音输入功能限制为预定义的语音映射，如以下各节中所述。 

## <a name="enabling-speech-recognition"></a>启用语音识别

在 HoloLens 上启用语音识别：
1. 选择 " **项目设置" > 平台 > HoloLens > 功能** 并启用 **麦克风**。 
2. 已在 " **设置" > 隐私 > 语音** "中启用语音识别，然后选择" **英语**"。

> [!NOTE]
> 语音识别始终在 " **设置** " 应用程序中配置的 Windows 显示语言中工作。 建议你同时启用 **在线语音识别** ，以获得最佳的服务质量。

![Windows 语音识别设置](images/unreal/speech-recognition-settings.png)

3. 当应用程序首次启动时，将显示一个对话框，询问你是否要启用麦克风。 选择 **"是"** 将在应用中启动语音输入。

语音输入不需要任何特殊的 Windows Mixed Reality Api;它基于现有的 Unreal Engine 4 [输入](https://docs.unrealengine.com/Gameplay/Input/index.html) 映射 API 构建。 

## <a name="adding-speech-mappings"></a>添加语音映射

使用语音输入时，将语音连接到操作非常重要。 这些映射会监视用户可能会说出的语音关键字应用，然后发出链接的操作。 可以通过以下方式找到语音映射：
1. 选择 " **编辑 > 项目设置**"，滚动到 " **引擎** " 部分，然后单击 " **输入**"。

添加跳转命令的新语音映射：
1. 选择 " **+** **数组元素** " 旁边的图标，然后填写以下值：
    * **操作名称** 的 **jumpWord**
    * **跳转****语音关键字**

> [!NOTE]
>  () 的任何英语单词 () 或短句子都可以用作关键字。 

![UE4 引擎输入设置](images/unreal/engine-input.png)

语音映射可用作操作或轴映射等输入组件或事件图中的蓝图节点。 例如，可以链接 "跳转" 命令，根据字词的讲述时间打印出两个不同的日志：

1. 双击蓝图以在 **事件图** 中打开它。
2. **右键单击** 并搜索语音映射的 **操作名称** (在本例中为 **JumpWord**) ，然后按 **Enter** 将 " **输入操作** " 节点添加到关系图中。
3. 将 **按下** 的 pin 拖放到 " **打印字符串** " 节点，如下图所示。 你可以保留已 **释放** 的 pin，而不会对语音映射执行任何操作。
 
![简单的语音操作](images/unreal/voice-input-img-03.png)

4. 播放应用程序，口述 " **跳转**"，并观看控制台来打印日志！

这就是在 Unreal 中开始向 HoloLens 应用添加语音输入所需的全部设置。 你可以在下面的链接中找到有关语音和交互性的详细信息，并确保考虑你为用户创建的体验。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unreal 开发旅程，下一项任务就是探索混合现实平台功能和 Api： 

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [语音输入](../../design/voice-input.md)
* [凝视和提交](../../design/gaze-and-commit.md)
* [本能交互](../../design/interaction-fundamentals.md)

