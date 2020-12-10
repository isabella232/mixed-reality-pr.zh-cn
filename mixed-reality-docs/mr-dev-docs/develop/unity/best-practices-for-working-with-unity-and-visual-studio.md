---
title: 使用 Unity 和 Visual Studio 的最佳做法
description: 用于简化使用 Unity 和 Visual Studio 创建混合现实应用程序的工作流的提示和技巧。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署，unity，visual studio，HoloLens，HoloLens 2，沉浸式耳机，最佳实践，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，UWP，Visual Studio Tools，Windows SDK
ms.openlocfilehash: 9e80cad3e7154ae5548514297343db8efcdcb49e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010258"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳做法

使用 Unity 创建混合现实应用程序时，需要在 Unity 和 Visual Studio 之间切换，以生成应用包并将其部署到 HoloLens 或沉浸式耳机。 默认情况下，需要 Visual Studio 的两个实例-一个实例用于修改 Unity 脚本，另一个实例用于部署到设备并进行调试。 以下说明允许使用单个 Visual Studio 实例进行开发，从而降低导出 Unity 项目的频率并改善调试体验。

## <a name="improving-iteration-time"></a>提高迭代时间

Unity 中的 .NET 脚本编写后端支持在 Unity 2018 中被弃用，并且在 Unity 2019 + 中被删除。 因此，建议切换到 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 但是，从 Unity 到 Visual Studio 的生成时间可能会更长。 若要提高迭代速度，请设置你的环境以获得最佳的编译结果：

1) 使用增量生成，每次将项目生成到同一个目录，并在此处重复使用预先生成的文件
2) 禁用项目 & 生成文件夹的反恶意软件扫描
   - 在 Windows 10 设置应用下打开 **病毒 & 威胁防护**
   - 选择 "安全 **& 威胁防护设置**" 下的 "**管理设置**"
   - 选择 "**排除**" 部分下的 "**添加或删除排除** 项"
   - 选择 " **添加排除** "，然后选择包含 Unity 项目代码和生成输出的文件夹
3) 使用 SSD 进行生成

有关详细信息，请参阅 [优化 IL2CPP 的生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 。 此外，请查看 [IL2CPP 脚本编写后端的调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。

请考虑安装 [ *UnityScriptAnalyzer* Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。 此工具分析你的 Unity c # 脚本，以了解可以通过更优化的方式编写的代码。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下载 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Visual Studio Tools for Unity 的优点**
* 通过放置断点、计算变量和复杂表达式，从 Visual Studio 调试 Unity 编辑器播放模式。
* 使用 Unity 项目资源管理器查找脚本，该脚本具有 Unity 显示的完全相同的层次结构。
* 直接在 Visual Studio 中获取 Unity 控制台。
* 使用向导快速创建或导航到脚本。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公开 c # 类变量以便轻松优化

可以通过两种方式公开类变量。 建议将 [SerializeField] 特性添加到专用变量。 序列化的字段可以从编辑器访问，但不能以编程方式公开。  另一种方法是将 c # 类变量公开为在编辑器 UI 中公开它们。 

利用这两种方法，可以在编辑器中播放时轻松地调整变量，这对于优化交互 mechanic 属性特别有用。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 或 Unity 升级后重新生成 UWP Visual Studio 解决方案

签入到源代码管理中的 UWP Visual Studio 解决方案可以在升级到新的 Windows SDK 或 Unity 引擎之后过期。 通过从 Unity 生成新的 UWP 解决方案并将差异合并到签入的解决方案中，可以在以后解决过时的解决方案。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文本格式资产以便于比较内容更改

以文本格式存储资产使你可以更轻松地在 Visual Studio 中查看内容更改差异。 可以通过选择 " **编辑 > 项目设置" > 编辑器** ，并更改 **资产序列化** 模式来 **强制文本**，以文本格式存储资产。 但是，合并文本资产文件更改很容易出错，不建议这样做，因此请考虑在源代码管理中启用独占二进制文件签出。

## <a name="see-also"></a>另请参阅
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [优化 IL2CPP 的生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
