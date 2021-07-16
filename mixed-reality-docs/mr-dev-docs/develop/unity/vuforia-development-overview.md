---
title: 将 Vuforia 与 Unity 配合使用
description: 使用 Vuforia 在 Unity Windows Mixed Reality应用程序。
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia， 标记， 坐标， 参考框架， 跟踪， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity， HoloLens， 设备跟踪， 性能模式， Vuforia 开发人员门户
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232167"
---
# <a name="using-vuforia-engine-with-unity"></a>将 Vuforia 引擎与 Unity 一起使用

Vuforia 引擎为 HoloLens一项重要功能 - 将 AR 体验连接到环境中的特定图像和对象的功能。 可以使用此功能覆盖工业企业机器顶层的引导式分步说明，或向物理产品或游戏添加数字功能和体验。

Vuforia 引擎提供了广泛的功能和目标，使 AR 开发过程更灵活。 我们最新的功能之一 Vuforia 模型目标是商业用途和工业用途的关键功能。 模型目标允许应用程序识别计算机、汽车或玩具等物理对象，并基于 CAD 或数字 3D 模型跟踪它们。 对于工业用途，此功能可以在工厂或现场外向程序集工作人员和服务技术人员提供 AR 工作说明和过程指南。

为手机和平板电脑构建的现有 Vuforia 引擎应用可以轻松地在 Unity 中配置为在 HoloLens。 甚至可以使用 Vuforia 引擎将新的 HoloLens 应用Windows 10平板电脑（如 Surface Pro Surface Book）。


## <a name="get-the-tools"></a>获取工具

[安装推荐版本的](../install-the-tools.md)Visual Studio 和 Unity，然后将 Unity 配置为使用 Visual Studio IDE 和编译器。 

安装 Unity 时，请务必安装"Windows Store IL2CPP 脚本后端"。

添加 Vuforia 引擎包，如此处 [所述](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)。

## <a name="getting-started-with-vuforia-engine"></a>Vuforia 引擎入门

了解 Vuforia 引擎和 HoloLens 的最佳起点是 Unity 资产存储 HoloLens 中提供的[Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)引擎 (示例) 。 此示例提供了一个完整的HoloLens项目，包括可部署到 HoloLens 的预配置场景。

场景显示如何使用 Vuforia 图像目标来识别图像，并使用数字内容在图像体验中HoloLens图像。 Vuforia 引擎HoloLens示例还包括一个场景，其中显示了模型目标和 VuMarks 在HoloLens。 你可以轻松地在场景中替换自己的内容，尝试创建HoloLens Vuforia 引擎的应用。



## <a name="configuring-a-vuforia-app-for-hololens"></a>为 Vuforia 应用配置HoloLens

开发适用于 HoloLens 的 Vuforia 引擎应用与为其他设备开发 Vuforia 引擎应用基本相同。 然后，可以应用以下部分所述的生成设置和配置。 这就是使 Vuforia 引擎能够处理空间映射和HoloLens跟踪系统所需的一切。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>生成并运行 Vuforia 引擎示例HoloLens
1.  从 Unity 资产存储下载 HoloLens [Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)引擎示例
2.  应用 [建议用于电源和性能的 Unity 引擎选项](performance-recommendations-for-unity.md)
3.  将示例场景添加到 **"生成中的场景****"。**
4.  在 **"设置"** 中，单击"添加打开场景"按钮，将生成平台 **切换到** **UWP。**
![图像](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  选择"**播放器设置** 按钮。  
   * 选择 **"UWP"** 图标并展开 **"XR 设置** 部分。
   * 确保 **已启用"支持的虚拟现实** "。    
   * 在 **"虚拟现实 SDK"** 下，确保：
     * **"窗口混合** 现实"包含在列表中，并且 **已启用"启用深度缓冲区** 共享"。 
     * 深度 **格式** 设置为 **16 位深度。** 
   * 确保" **立体声渲染模式"** 设置为" **单通道实例"。**
6.  展开"**发布设置** 部分。
   * 在 **"功能"** 下，确保已选择 **"Internet 客户端"、"WebCam"、"麦克风****"和"SpatialPerception"。**
   * 注意：只有在打算使用 Surface Observer API 时，才应选择 **SpatialPerception。**
   * 在 **"支持的设备系列"** 下，确保 **选中** "全息"。 
7.  展开" **分辨率和呈现"** 部分。
   * 禁用 **"在后台运行** "，使 Vuforia 引擎在应用置于后台时暂停，并且可以在应用恢复时再次访问相机。 
   * 在" **默认方向"** 下拉列表中，确保 **选中"横向左侧** "。
8.  返回到"生成 **设置** 窗口，**然后选择"生成**"以生成Visual Studio项目。
9.  从应用程序生成Visual Studio，并安装到HoloLens。

## <a name="the-vuforia-developer-portal"></a>Vuforia 开发人员门户

希望使用 Vuforia Engine 和 HoloLens 创建自己的 AR 体验的开发人员应在 developer.vuforia.com 注册我们的 Vuforia[开发人员门户。](https://developer.vuforia.com/) 在门户中，开发人员可以访问[Vuforia](https://developer.vuforia.com/forum)引擎论坛，他们可在其中加入社区讨论、一个包含[](https://library.vuforia.com/)所有 Vuforia 引擎功能的深入文档的库，以及用户可以在[Vuforia](https://developer.vuforia.com/target-manager)目标管理器中创建自己的自定义目标。 开发人员还可使用 [Vuforia](https://developer.vuforia.com/license-manager)许可证管理器 注册免费的开发人员许可证。

## <a name="device-tracking-with-vuforia"></a>使用 Vuforia 进行设备跟踪

[即使目标](https://library.vuforia.com/features/environments/device-tracker-overview.html) 不再在视图中，设备跟踪也保持跟踪。 启用位置设备跟踪器后，会自动为所有目标启用此功能。 对于HoloLens应用程序，位置设备跟踪器在 Unity 中自动启动。

Vuforia 引擎自动融合相机跟踪和HoloLens的空间跟踪中的姿势，以提供与相机是否看到目标无关的稳定目标。

由于进程是自动处理的，因此不需要开发人员进行任何编程。


**下面是该过程的简要说明：**
1. Vuforia 的目标跟踪器识别目标
2. 然后初始化目标跟踪
3. 分析目标的位置和旋转，为目标提供可靠的姿势HoloLens
4. Vuforia 引擎将目标姿势转换为HoloLens空间映射坐标空间
5. HoloLens不再显示目标，则系统将接管跟踪。 每当再次查看目标时，Vuforia 将继续准确跟踪图像和对象。

检测到但不再在视图中的目标将报告为EXTENDED_TRACKED。 在这些情况下，在所有目标中使用的 DefaultTrackableEventHandler 脚本将继续呈现扩充内容。 开发人员可以通过实现自定义可跟踪事件处理程序脚本来控制此行为。

## <a name="performance-mode-with-vuforia-engine"></a>Vuforia 引擎的性能模式 

可以通过 Vuforia 引擎管理应用程序的性能，HoloLens AR 体验并减少 CPU 上的工作负荷。 Vuforia 引擎提供三种可选项模式：默认模式、优化速度模式和优化质量模式。 

*   MODE_OPTIMIZE_SPEED可最大程度地减少设备HoloLens工作负载，并且非常适用于扩展 AR 体验。 建议在应用跟踪静态对象/目标的情况下。
*   MODE_DEFAULT是正常模式，可在大多数方案中使用。
*   MODE_OPTIMIZE_QUALITY更适用于跟踪预期要选取的可移动目标或模型目标。

**设置模式**

若要在 Unity 中更改性能模式，请导航到 Vuforia 配置 (Ctrl+Shift+V / Cmd+Shift+V) ，该配置作为 ARCamera GameObject 中的组件。 
*   选择"相机设备模式"的下拉菜单，然后选择三个选项之一。


## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)
* [坐标系统](../../design/coordinate-systems.md)
* [空间映射](../../design/spatial-mapping.md)
* [Unity 中的相机](camera-in-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 文档：入门 Vuforia 引擎进行Windows 10开发](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Vuforia 文档：入门 Unity 中的 Vuforia 引擎](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Vuforia 文档：在 Unity HoloLens示例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Vuforia 文档：Vuforia 中的设备跟踪](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia 文档：帧速率和性能优化](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
