---
title: 在 HoloLens 上测试应用
description: 了解有关测试和性能优化 HoloLens 混合现实应用程序的一般指南和建议。
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，测试
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212087"
---
# <a name="testing-your-app-on-hololens"></a>在 HoloLens 上测试应用

测试 HoloLens 应用程序类似于测试 Windows 应用程序。 你仍需要考虑功能、互操作性、性能、安全性、可靠性等。 但是，PC 或手机应用中未弹出的某些区域需要特殊处理。 全息应用需要在一组不同的环境中顺利运行。 它们还需要始终保持性能和用户舒适。 本指南可帮助你测试这些区域。

## <a name="performance"></a>性能

全息应用需要在一组不同的环境中顺利运行。 它们还需要始终保持性能和用户舒适。 性能对用户使用全息版应用程序的体验非常重要，我们有一个专门的主题。 请确保阅读并遵循 [混合现实的了解性能](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>在三维中测试3D

1. **在尽可能多的不同空间中测试您的应用程序。** 尝试大房间、小房间、bathrooms、kitchens、间卧室、办公室等。 还需要考虑使用非标准功能的房间，如非垂直壁、弯曲壁、非水平上限。 当在房间间过渡时，它是否能正常工作，并经历走廊或楼梯？
2. **在不同的照明条件中测试您的应用程序。** 它是否能正确响应光源、黑色曲面等不同环境条件，以及镜像和玻璃壁等不同环境条件。
3. **在不同的动作条件中测试您的应用程序。** 放在设备上，尝试各种运动状态的方案。 它是否响应了不同的移动或稳定状态？
4. **测试应用程序在不同角度的工作方式。** 如果你有世界各地锁定的全息图，则当你的用户执行此操作时，会发生什么情况？ 如果用户与全息影像之间发生了什么情况？ 如果用户查看上面或下面的全息图，该怎么办？
5. **使用空间和音频提示。** 请确保应用使用空间和音频提示来防止用户丢失。
6. **在不同的环境噪音级别测试应用。** 如果你已经实现了语音命令，请尝试对它们调用不同的环境噪音级别。
7. **测试您的应用程序的安装**。 请确保从座位和位置进行测试。
8. **从不同的距离测试你的应用程序**。 UI 元素是否可以从远处开始进行读取和交互？ 您的应用程序是否会对用户与全息影像非常接近的用户做出反应？
9. **针对常见的应用程序栏交互测试您的应用程序**。 所有应用磁贴和2D 通用应用都具有一个 [应用栏](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) ，可用于控制混合环境中的应用位置。 请确保单击 "删除" 以正常结束应用过程，并确保在二维通用应用的上下文中支持 "后退" 按钮。 尝试在 " [调整" 模式下](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) 进行缩放并将其移动到 "调整" 模式，同时处于活动状态，而是 "已暂停应用" 磁贴。

### <a name="environmental-test-matrix"></a>环境测试矩阵

![用于 HoloLens 应用开发的环境测试矩阵](images/environment-matrix-600px.png)

## <a name="comfort"></a>舒适感

1. **剪辑平面。** 要留心到 [呈现全息影像](hologram-stability.md#hologram-render-distances)的位置。
2. **避免与实际头运动不一致的虚拟移动。** 避免以不代表用户实际运动的方式移动相机。 如果你的应用程序要求通过场景移动用户，则可预测运动，尽量减少加速度，并让用户控制移动。
3. **按照全息图质量指导原则进行操作。** 实现 [全息影像质量指导的高](hologram-stability.md) 性能应用程序不太可能导致用户 discomfort。
4. **横向分布全息影像，而不是垂直分布。** 强制用户花很长时间查找或缩小可能会导致疲劳。

## <a name="input"></a>输入

### <a name="interaction-models"></a>交互模型

请确保全息影像交互适用于所选的 [交互模型](../../design/interaction-fundamentals.md)。
如果需要支持辅助功能，则最好使用鼠标和键盘之类的其他附件进行验证。

**当你的应用程序具有与鼠标和触控不同的行为时进行验证。** 确定不一致并帮助设计决策，使用户更自然地体验体验。 例如，根据悬停触发操作。


### <a name="custom-voice-commands"></a>自定义语音命令

[语音输入](../../design/voice-input.md) 是一种自然的交互方式。 用户体验可能会神奇或混淆，具体取决于你选择的命令以及如何公开它们。 通常，不应使用系统语音命令，如 "Select" 或 "你好 Cortana" 作为自定义命令。 下面是几个需要注意的要点：
1. **避免使用类似的命令。** 可能会触发错误的命令。
2. **尽可能选择发音丰富的字词。** 最小化和/或避免错误激活。

### <a name="peripherals"></a>外设

用户可以通过 [外围设备](../../discover/hardware-accessories.md)与你的应用进行交互。 应用无需执行任何特殊操作即可利用此功能，但有几个值得注意的事项。
1. **验证自定义交互。** 例如，应用的自定义键盘快捷方式。
2. **验证切换输入类型。** 尝试使用多个输入方法完成同一方案中的任务，如语音、手势、鼠标和键盘。

## <a name="system-integration"></a>系统集成

### <a name="battery"></a>电池

在未连接电源的情况下测试应用程序，以了解它消耗电池的速度。 通过查看电源 LED 读数，可以轻松地了解电池状态。 

![指示电池电量的 LED 状态](images/batterypowerledindication-500px.png)<br>

*指示电池电量的 LED 状态*

### <a name="power-state-transitions"></a>电源状态转换

验证密钥方案在电源状态之间转换时按预期方式工作。 例如，应用程序是否仍保留在其原始位置？ 它是否正确保存其状态？ 它是否继续按预期方式工作？
1. **备用/继续。** 若要进入备用状态，可以立即按下并释放电源按钮。 设备还会在处于非活动状态3分钟后自动进入待机状态。 若要从待机状态恢复，可以立即按下并释放电源按钮。 如果将设备连接或断开连接电源，该设备也会恢复。
2. **关闭/重新启动。** 若要关闭，请按住电源按钮6秒钟。 若要重新启动，请按 "电源" 按钮。

### <a name="multi-app-scenarios"></a>多应用方案

在应用程序之间切换时验证核心应用程序的功能，尤其是在实现后台任务的情况下。 如果适用，还需要检查复制/粘贴和 Cortana 集成。

## <a name="telemetry"></a>遥测

使用遥测和分析指导你。 将分析集成到应用中有助于从 Beta 测试人员和最终用户获取有关应用的见解。 此数据可用于帮助在提交到 Store 之前优化应用，以及用于将来的更新。 有许多分析选项。 如果不确定从何处开始，请查看应用[Insights。](https://www.visualstudio.com/products/application-insights-vs.aspx)

要考虑的问题：
1. 用户如何使用空间？
2. 应用如何将对象放置在世界上 - 可以检测问题吗？
3. 他们在应用程序的不同阶段花费了多少时间？
4. 他们在应用中花费了多少时间？
5. 用户尝试的最常见的使用路径是什么？
6. 用户是否达到意外状态或错误？

## <a name="emulator-and-simulated-input"></a>Emulator和模拟输入

使用[HoloLens仿真](using-the-hololens-emulator.md)器是使用不同类型的模拟用户特征和空间高效测试全息应用的重要方法。 下面是有效使用模拟器测试应用的一些建议：
1. **使用模拟器的虚拟房间来扩展测试。** 模拟器附带一组虚拟房间，可用于在更多环境中测试应用。
2. **使用模拟器从所有角度查看应用。** PageUp/PageDn 键会使模拟用户更高或更短。
3. **使用真实应用测试HoloLens。** HoloLens Emulator是一个很好的工具，可帮助你快速访问应用并捕获新的 bug，但请确保在提交到 Windows Store 之前，还要在物理HoloLens进行测试。 这一点对于确保性能和体验在真实硬件上是出色的非常重要。

## <a name="automated-testing-with-perception-simulation"></a>使用感知模拟进行自动测试

某些应用开发人员可能希望自动测试其应用。 除了简单的单元测试之外，还可以在应用中使用感知[模拟](perception-simulation.md)堆栈HoloLens自动化对应用的人类和世界输入。 感知模拟 API 可以将模拟输入发送到HoloLens仿真器或物理HoloLens。

## <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

若要使应用有机会在 Windows Store 上[发布](../../distribute/submitting-an-app-to-the-microsoft-store.md)，请在本地验证并测试它，然后再提交该应用进行认证。 如果应用面向 Windows。全息设备系列[，Windows认证工具包](/windows/uwp/debug-test-perf/windows-app-certification-kit)只会在电脑上运行本地静态分析测试。 不会在应用程序上运行HoloLens。

## <a name="see-also"></a>另请参阅

* [将应用提交到 Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)