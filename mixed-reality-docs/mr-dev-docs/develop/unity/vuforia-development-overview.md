---
title: 将 Vuforia 与 Unity 配合使用
description: 使用 Vuforia 在 Unity 中构建 Windows Mixed Reality 应用程序。
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia，标记，坐标，引用框架，跟踪，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity，HoloLens，设备跟踪，性能模式，Vuforia 开发人员门户
ms.openlocfilehash: dd5153b5e4986ebf1ecc2c133f3d431de08ce5b923cc7d2327d9cbda4f4df61c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216413"
---
# <a name="using-vuforia-engine-with-unity"></a>将 Vuforia 引擎与 Unity 一起使用

Vuforia 引擎为 HoloLens 提供了一项重要的功能–将 AR 体验连接到环境中的特定映像和对象的能力。 你可以使用此功能来覆盖工业企业的机械上的引导式分步说明，或者向物理产品或游戏添加数字功能和体验。

Vuforia 引擎提供范围广泛的功能和目标，使 AR 开发过程更加灵活。 我们最新的功能 Vuforia 模型目标之一是用于商业和工业用途的一项重要功能。 模型目标允许应用程序识别诸如计算机、汽车或玩具等物理对象，并根据 CAD 或数字3D 模型对其进行跟踪。 对于工业用途，此功能可以为程序集工作者和服务技术人员提供 AR 工作说明和过程指南，同时在现场或现场推出。

可以轻松地在 Unity 中配置为手机和平板电脑构建的现有 Vuforia 引擎应用，以便在 HoloLens 上运行。 甚至可以使用 Vuforia 引擎将新的 HoloLens 应用程序 Windows 10 平板电脑，如 Surface Pro 和 Surface Book。


## <a name="get-the-tools"></a>获取工具

安装 Visual Studio 和 unity 的[推荐版本](../install-the-tools.md)，然后将 Unity 配置为使用 Visual Studio 和首选 IDE 和编译器。 

安装 Unity 时，请确保安装 "Windows Store IL2CPP 脚本后端"。

按 [此处](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)所述添加 Vuforia 引擎包。

## <a name="getting-started-with-vuforia-engine"></a>Vuforia 引擎入门

了解 Vuforia 引擎和 HoloLens 的最佳起点是在 Unity 资产存储) 中提供的[Vuforia 引擎 HoloLens 示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (。 该示例提供了一个完整的 HoloLens 项目，其中包括可以部署到 HoloLens 的预配置的场景。

幕后介绍了如何使用 Vuforia 图像目标识别图像，并在 HoloLens 体验中使用数字内容对其进行扩充。 Vuforia 引擎 HoloLens 示例还包含一个场景，其中显示了 HoloLens 上模型目标和 VuMarks 的使用情况。 您可以轻松地在幕后替换您自己的内容，以试验使用 Vuforia 引擎创建 HoloLens 应用程序。



## <a name="configuring-a-vuforia-app-for-hololens"></a>为 HoloLens 配置 Vuforia 应用

为 HoloLens 开发 Vuforia 引擎应用与为其他设备开发 Vuforia 引擎应用基本相同。 然后，你可以应用以下部分中所述的生成设置和配置。 这就是使 Vuforia 引擎能够使用 HoloLens 空间映射和位置跟踪系统所需的全部操作。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>生成并运行 HoloLens 的 Vuforia 引擎示例
1.  下载 Unity 资产存储区中[HoloLens 的 Vuforia 引擎示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)
2.  [为电源和性能应用建议的 Unity 引擎选项](performance-recommendations-for-unity.md)
3.  在生成中将示例场景添加到 **场景** 中 **。**
4.  在 "**生成设置**" 中，通过单击 "**添加打开的场景**" 按钮将生成平台切换到 **UWP** 。
![图像](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  选择 "**播放器设置**" 按钮。  
   * 选择 **UWP** 图标，然后展开 " **XR 设置**" 部分。
   * 确保启用 **虚拟现实** 。    
   * 在 **虚拟现实 sdk** 下，请确保：
     * **窗口混合现实** 包含在列表中，启用 **深度缓冲区** 共享。 
     * **深度格式** 设置为 **16 位深度。** 
   * 确保将 **立体声呈现模式** 设置为 **单一传递实例。**
6.  展开 "**发布设置**" 部分。
   * 在 " **功能** " 下，确保选择 **Internet 客户端、网络摄像机、麦克风** 和 **SpatialPerception** 。
   * **注意：** 仅当打算使用 Surface 观察器 API 时，才应选择 SpatialPerception。
   * 在 " **受支持的设备系列**" 下，确保已选中 " **全息** "。 
7.  展开 " **分辨率和演示** " 部分。
   * 禁用 **后台运行** ，以便在将应用放入后台时暂停 Vuforia 引擎，并在应用恢复后再次访问相机。 
   * 在 " **默认方向** " 下拉列表中，确保选中 " **横向打印** "。
8.  返回到 "**生成设置**" 窗口并选择 "**生成**" 以生成 Visual Studio 项目。
9.  从 Visual Studio 生成可执行文件并将其安装在 HoloLens 上。

## <a name="the-vuforia-developer-portal"></a>Vuforia 开发人员门户

希望利用 Vuforia 引擎和 HoloLens 来创建自己的 AR 体验的开发人员应在[developer.vuforia.com](https://developer.vuforia.com/)的 Vuforia 开发人员门户中注册。 在门户中，开发人员有权访问 [Vuforia 引擎论坛](https://developer.vuforia.com/forum) ，他们可以在其中加入社区讨论、包含有关所有 Vuforia 引擎功能的深入文档的 [库](https://library.vuforia.com/) 以及 [Vuforia 目标管理器](https://developer.vuforia.com/target-manager) ，用户可以在其中创建自己的自定义目标。 开发人员还可以使用 [Vuforia 许可证管理器](https://developer.vuforia.com/license-manager)注册免费的开发人员许可证。

## <a name="device-tracking-with-vuforia"></a>用 Vuforia 进行设备跟踪

即使目标不再处于视图中，[设备跟踪](https://library.vuforia.com/features/environments/device-tracker-overview.html)仍将保持跟踪。 启用位置设备跟踪器后，会自动为所有目标启用此功能。 对于 HoloLens 应用程序，位置设备跟踪器会在 Unity 中自动启动。

Vuforia 引擎自动融合摄像机跟踪中的姿势，并 HoloLens 的空间跟踪，以提供稳定的目标，而不受相机是否可见。

因为该过程是自动处理的，所以开发人员无需任何编程。


**下面是此过程的概要说明：**
1. Vuforia 的目标跟踪器识别目标
2. 然后初始化目标跟踪
3. 分析目标的位置和旋转，为 HoloLens 提供可靠的姿势估算
4. Vuforia 引擎将目标的姿势转换为 HoloLens 空间映射坐标空间
5. 如果目标不再处于视图中，HoloLens 将接管跟踪。 再次查看目标时，Vuforia 将继续准确地跟踪图像和对象。

检测到但不再在视图中的目标将报告为 EXTENDED_TRACKED。 在这些情况下，用于所有目标的 DefaultTrackableEventHandler 脚本将继续呈现增加内容。 开发人员可以通过实现自定义的以可跟踪事件处理程序脚本来控制此行为。

## <a name="performance-mode-with-vuforia-engine"></a>带有 Vuforia 引擎的性能模式 

可以通过 Vuforia 引擎来管理 HoloLens 对范围内 AR 体验的性能，并减少 CPU 工作负荷。 Vuforia 引擎提供了三种可供选择的模式：默认值、优化速度和优化质量。 

*   MODE_OPTIMIZE_SPEED 使你可以最大程度地降低 HoloLens 设备上的工作负荷，并且非常适合用于扩展 AR 体验。 建议在应用跟踪静态对象/目标的情况下使用。
*   MODE_DEFAULT 是正常模式，可在大多数情况下使用。
*   MODE_OPTIMIZE_QUALITY 更适合跟踪预期选取的可移动目标或模型目标。

**设置模式**

若要在 Unity 中更改性能模式，请导航到 Vuforia Configuration (Ctrl + Shift + V/Cmd + Shift + V) ，它作为 ARCamera GameObject 中的一个组件。 
*   选择 "相机设备模式" 下拉菜单，然后选择三个选项之一。


## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)
* [坐标系统](../../design/coordinate-systems.md)
* [空间映射](../../design/spatial-mapping.md)
* [Unity 中的相机](camera-in-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 文档：用于 Windows 10 开发的带 Vuforia 引擎入门](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Vuforia 文档：在 Unity 中与 Vuforia 引擎入门](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Vuforia 文档：在 Unity 中使用 HoloLens 示例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Vuforia 文档： Vuforia 中的设备跟踪](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia 文档：帧速率和性能优化](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
