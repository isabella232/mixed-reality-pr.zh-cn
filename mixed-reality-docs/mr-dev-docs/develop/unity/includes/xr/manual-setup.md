---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394581"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

使用新的混合现实功能工具应用程序安装 OpenXR 插件。 按照安装和 [使用说明操作，](../../welcome-to-mr-feature-tool.md) 在"混合现实工具包"类别中选择"混合现实 **OpenXR** 插件"包：

![混合现实功能工具包窗口，突出显示了打开的 xr 插件](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>设置生成目标

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1. 选择 **"文件>生成设置..."**
2. 在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3. 将“体系结构”设置为“ARM 64” 
4. 将“目标设备”设置为“HoloLens” 
5. 将“生成类型”设置为“D3D” 
6. 将“UWP SDK”设置为“最近安装的版本” 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要在 Unity 中将 OpenXR 设置为运行时，请执行以下操作：

1. 在 Unity 编辑器中，导航到 **"编辑>项目设置"**
2. 在"设置"列表中，选择 **"XR 插件管理"**
3. 选中"**启动时初始化 XR"和****"OpenXR"** 框
4. 如果以HoloLens 2为目标，请确保你位于 UWP 平台上，然后选择"Microsoft HoloLens **功能集"**

![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../../images/openxr-img-05.png)

### <a name="optimization"></a>优化

如果要针对 HoloLens 2 进行开发，请导航到"混合现实> **OpenXR >应用** 针对 HoloLens 2 的建议项目设置，以获得更好的应用性能。

![已选中 OpenXR 的混合现实菜单项的屏幕截图](../../images/openxr-img-08.png)

> [!IMPORTANT]
> 如果在 **OpenXR** 插件旁边看到黄色警告图标，请单击该图标并选择" **全部修复** "，然后再继续。 Unity 编辑器可能需要自动重启以使更改生效。

![OpenXR 项目验证窗口的屏幕截图](../../images/openxr-img-06.png)

现在，你已准备好在 Unity 中开始使用 OpenXR 进行开发！  继续学习下一部分，了解如何使用 OpenXR 示例。

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 和 HoloLens 2 的 Unity 示例项目

请查看 [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 示例存储库，了解示例 Unity 项目，了解如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实头戴显示设备生成 Unity 应用程序。

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1.  选择 **"文件>生成设置..."**
2.  在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图：

1. 在 Unity 编辑器中，导航到"编辑 **>项目设置"，然后选择****"XR 插件管理"**

2. 选择 **"安装 XR 插件管理"**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR"，****然后选择Windows Mixed Reality**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-7.png)

4. 展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows 平台设置"** 选项卡
5. 如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。** 
    * 可以选择任一运行时。  如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，查看使用适用于 Unity 的混合现实 [OpenXR](../../openxr-getting-started.md) 插件指南，在返回到本教程之前，请正确设置这些设备

> [!NOTE]
> 从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。  迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。 有关详细信息，请参阅 [使用混合现实 OpenXR 插件](../../openxr-getting-started.md)。

6. 如果决定选择"深度提交 **Windows Mixed Reality，** 请选中所有框，将"深度提交模式"设置为"深度 **16 位"**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中Windows Mixed Reality部分](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1.  选择 **"文件>生成设置..."**
2.  在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图。

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。

1. 从 **"生成设置..."** 打开" **播放器设置..."。窗口** 并展开 **"XR 设置"** 组
2. 在 **"XR 设置"** 部分中 **，选择"** 支持的虚拟现实"以添加"虚拟现实设备"列表
3. 将 **深度格式设置为** **16 位深度** 并启用 **深度缓冲区共享**
4. 将 **立体声渲染模式设置为****单通道实例**
5. 如果要 **使用全息远程处理** ，请选择"支持的 WSA 全息远程处理" 

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了"播放器设置"部分](../../images/wmr-config-img-9.png)