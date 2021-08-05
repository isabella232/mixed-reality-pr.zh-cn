---
title: Unity Visual Studio最佳做法
description: 使用技巧和技巧来简化使用 Unity 和 Visual Studio 创建混合现实应用程序的工作流。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy， unity， visual studio， HoloLens， HoloLens 2， 沉浸式头戴显示设备， 最佳做法， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， UWP， Visual Studio Tools， Windows SDK
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186877"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳做法

使用 Unity 创建混合现实应用程序时，需要在 Unity 和 Visual Studio 之间切换，以生成应用包HoloLens或沉浸式头戴显示设备。 默认情况下，需要两个 Visual Studio实例 - 一个实例用于修改 Unity 脚本，另一个实例用于部署到设备和调试。 以下说明允许使用单个 Visual Studio 实例进行开发，从而减少导出 Unity 项目的频率并改进调试体验。

## <a name="improving-iteration-time"></a>改善迭代时间

Unity 中对 .NET 脚本后端的支持在 Unity 2018 中已弃用，从 Unity 2019+ 开始已删除，因此建议切换到 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 但是，从 Unity 到 Visual Studio。 若要提高迭代速度，请设置环境以获得最佳编译结果：

1) 使用增量生成，每次将项目生成到同一目录，并在那里重新使用预生成文件
2) 在生成文件夹中禁用项目的反恶意软件&扫描
   - 在 **& 设置应用下打开**"病毒Windows 10威胁防护"
   - 在 **"病毒设置****威胁防护&下选择"管理应用程序"**
   - 在 **"排除项"部分下选择** " **添加或删除排除** 项"
   - 选择 **"添加排除** 项"，然后选择包含 Unity 项目代码和生成输出的文件夹
3) 使用 SSD 进行生成

有关详细信息 [，请查看优化 IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 的生成时间。 另请查看 [IL2CPP 脚本后端 上的调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。

请考虑安装 [*UnityScriptAnalyzer* Visual Studio扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。 此工具分析 Unity C# 脚本，了解以更优化的方式编写的代码。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下载[Visual Studio Tools for Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**服务Visual Studio Tools for Unity**
* 通过放置断点、计算变量和复杂表达式Visual Studio调试编辑器中的 Unity 播放模式。
* 使用 Unity Project资源管理器查找与 Unity 显示的层次结构完全相同的脚本。
* 直接在控制台内部获取 Unity Visual Studio。
* 使用向导快速创建或导航到脚本。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公开 C# 类变量以轻松优化

有两种方法可以公开类变量。 建议的方式是向专用变量添加 [SerializeField] 属性。 序列化字段可以从编辑器访问，但不能以编程方式公开。  另一个选项是使 C# 类变量成为公共变量，以在编辑器 UI 中公开它们。 

这两种方法都使得在编辑器中播放时可以轻松调整变量，这一点对于优化交互选项属性特别有用。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>在升级 SDK Visual Studio Unity Windows重新生成 UWP 解决方案

升级到Visual Studio SDK 或 Unity 引擎后，已签入到源代码管理中的 UWP Windows可能过期。 可以通过从 Unity 生成新的 UWP 解决方案，将差异合并到签入解决方案中，解决过期的解决方案。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文本格式资产轻松比较内容更改

通过以文本格式存储资产，可以更轻松地查看文本格式中的内容Visual Studio。 可以通过选择"编辑编辑器"，将资产序列> Project 设置 >更改为"强制文本 **"，** 以文本 **格式存储资产**。  但是，合并文本资产文件更改容易出错，不建议这样做，因此请考虑在源代码管理中启用独占二进制签出。

## <a name="see-also"></a>另请参阅
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [优化 IL2CPP 的生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)