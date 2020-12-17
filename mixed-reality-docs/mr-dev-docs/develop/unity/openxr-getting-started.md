---
title: 为 Unity 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 05adee2d88bc90dcfb5cf8b780212c7622aff786
ms.sourcegitcommit: ce4975f584bb62075bcb66349237b77081fb982b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644914"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>为 Unity 使用混合现实 OpenXR 插件

从 Unity 版本2020.2 开始，Microsoft 的 Mixed Reality OpenXR 插件包可通过 Unity 包管理器 (UPM) 提供。

## <a name="prerequisites"></a>先决条件

*   Unity 2020.2 或更高版本
*   Unity OpenXR 插件0.1.1 或更高版本
*   Visual Studio 2019 或更高版本
*   在适用于 HoloLens 2 应用的 Unity 中安装 **UWP** 平台支持

> [!NOTE]
> 如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。 但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。

## <a name="installing-the-mixed-reality-openxr-plugin"></a>安装混合现实 OpenXR 插件

你的项目需要在使用混合现实 OpenXR 插件之前安装 **OpenXR 插件** 和 **XR 插件管理** 包。 如果已安装了这些文件，很好！ 否则，安装混合现实 OpenXR 插件会自动将它们作为依赖项进行安装：

1. 在 Unity 编辑器中，导航到 "**编辑" > 项目设置 > 包管理器**"
2. 展开 " **限定作用域** " 部分，输入以下信息，然后选择 " **保存**"：   
    * 将 **名称** 设置为 **Microsoft Mixed Reality**
    * 将 **URL** 设置为 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * 将 **范围 (s)** 设置为 **mixedreality**

3. 在 "**高级设置**" 下，选择 "**启用预览包**"

![在项目设置中打开的 "Unity 包管理器" 窗口的屏幕截图](images/openxr-img-01.png)

Unity 包管理器使用名为 *manifest.js* 的清单文件来确定要安装的包以及可以从中安装这些包的注册表。

> [!IMPORTANT]
> OpenXR 仍在 Unity 中试验，此过程可能会随时间而改变，因为我们将努力优化开发人员体验。

### <a name="registering-the-mixed-reality-dependency"></a>注册混合现实依赖项

将 Microsoft 混合现实范围内的注册表添加到清单后，可以指定 OpenXR 包。

添加 OpenXR 包：

1. 在文本编辑器中打开 **<projectRoot> /Packages/manifest.js** ，如 Visual Studio Code
2. 按如下所示修改文件 *中包/manifest.js* 的依赖项部分：

> [!IMPORTANT]
> 清单文件中的依赖关系可能比此处显示的更多。 请勿删除任何文件，只需将 "OpenXR" 依赖项添加到列表。

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. 保存该文件，切换回 Unity 编辑器，打开 **包管理器** 以确认已安装插件： 

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了混合现实 OpenXR 插件](images/openxr-img-03.png)

> [!Note] 
> 如果使用 Unity 包管理器删除 OpenXR 包，则必须使用前面介绍的步骤重新添加它。

## <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要将 OpenXR 设置为 Unity 中的运行时： 

1. 在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"
2. 在设置列表中，选择 " **XR 插件管理**"
3. 选中 " **在启动时初始化 XR"** 和 " **OpenXR (预览")** 框
4. 如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

> [!IMPORTANT]
> 如果在 OpenXR 插件旁边出现一个红色警告图标 **(预览 ")**，请单击该图标，然后选择" **全部修复** "，然后继续。 Unity 编辑器可能需要重新启动才能使更改生效。

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！  继续阅读下一节，了解如何使用 OpenXR 示例。

## <a name="optimization"></a>Optimization

如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>试用 Unity 示例场景

若要利用一个或多个示例，请从 **程序包 Manager** 安装 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：

![在 Unity 编辑器中打开的 Unity 包管理器的屏幕截图，其中突出显示了 AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>HoloLens 2 示例

1. 在 Unity 编辑器中，导航到 "**窗口 >" 包管理器**"
2. 在包列表中，选择 " **混合现实 OpenXR" 插件**
3. 在 **示例** 列表中找到示例，然后选择 "**导入**"

![已在 Unity 编辑器中打开 Unity 包管理器的屏幕截图，并选中混合现实 OpenXR 插件，并突出显示示例导入按钮](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  更新包时，Unity 提供更新导入的示例的选项。  更新导入的示例将覆盖对示例和关联的资产所做的任何更改。

## <a name="next-steps"></a>后续步骤 

现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。

## <a name="see-also"></a>另请参阅
* [不 MRTK 配置你的项目](configure-unity-project.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md#how-to-profile-with-unity)