---
ms.openlocfilehash: c5276943bab0ddc961342f879c0cf4f8986aa7b4f67b16c9c8b5415ca6fc58fd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202705"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

使用新的混合现实功能工具应用程序安装 OpenXR 插件。 按照安装和 [使用说明操作，](../../welcome-to-mr-feature-tool.md) 在"平台支持"类别中选择"混合现实 **OpenXR** **插件"** 包：

![混合现实功能工具包窗口，突出显示了打开的 xr 插件](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>设置生成目标

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"MAC"&"独立"平台](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到通用 Windows 平台：

1. 选择 **"文件>生成设置...**
2. 在 **"Windows"列表中选择**"通用平台"，然后选择"**切换平台"**
3. 将“体系结构”设置为“ARM64”
4. 将“目标设备”设置为“HoloLens” 
5. 将“生成类型”设置为“D3D 项目”
6. 将 **"目标 SDK 版本"设置为****"最新安装"**

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"通用Windows平台"](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要在 Unity 中将 OpenXR 设置为运行时，请执行以下操作：

1. 在 Unity 编辑器中，导航到"**编辑> Project 设置**
2. 在应用程序列表中，设置 MRFT (安装混合现实 OpenXR 插件时，应已安装 **XR** 插件) 
3. 选中" **启动时初始化 XR"** 框
4. 如果面向桌面 VR，请停留在"电脑独立"选项卡 (监视器) 并选中 **"OpenXR"** 和"Windows Mixed Reality **功能集**"
5. 如果面向 HoloLens 2，请切换到"通用 Windows 平台"选项卡 (Windows徽标) 并选择 **"OpenXR"** 和"Microsoft HoloLens **功能集**"

![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../../images/openxr-img-05.png)

> [!IMPORTANT]
> 如果在 **OpenXR** 插件旁边看到黄色警告图标，请单击该图标并选择"全部 **修复** "，然后再继续。 Unity 编辑器可能需要自动重启以使更改生效。

![OpenXR 项目验证窗口的屏幕截图](../../images/openxr-img-06.png)

### <a name="optimization"></a>优化

如果要针对 HoloLens 2 进行开发，请选择"混合现实> Project >应用建议的项目设置 **HoloLens 2** 获取更好的应用性能。

![已选中 OpenXR 的混合现实菜单项的屏幕截图](../../images/openxr-img-08.png)

现在，你已准备好在 Unity 中开始使用 OpenXR 进行开发！  继续学习下一部分，了解如何使用 OpenXR 示例。

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>适用于 OpenXR 和 HoloLens 2 的 Unity 示例项目

请查看[OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples)示例存储库，了解示例 Unity 项目，了解如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实头戴显示设备生成 Unity 应用程序。

或者，如果已准备好从空白项目自行开始，请继续阅读相机 [设置一](../../camera-in-unity.md) 文。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

> [!CAUTION]
> XR Windows在 Unity 2021.1 中已弃用，将在 Unity 2021.2 中删除。  对于 Unity 2020 开发，Microsoft 建议改为使用 OpenXR 插件。

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"MAC"&"独立"平台](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到通用 Windows 平台：

1.  选择 **"文件>生成设置...**
2.  在 **"Windows"列表中选择**"通用平台"，然后选择"**切换平台"**
3.  将“体系结构”设置为“ARM64”
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D 项目”
6.  将 **"目标 SDK 版本"设置为****"最新安装"**
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"通用Windows平台"](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图：

1. 在 Unity 编辑器中，导航到 **"编辑> Project"，然后选择****"XR 插件管理"**

2. 选择 **"安装 XR 插件管理** "（如果显示）

![unity 编辑器中Project 设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR"，****然后选择Windows Mixed Reality**

![unity 编辑器中Project"设置"窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-7.png)

4. 选择 **"XR 插件管理"Windows Mixed Reality** 部分，选中所有框，将"深度缓冲区格式"设置为"深度缓冲区  >  **16 位"** 

![unity 编辑器中Project设置窗口的屏幕截图，其中突出显示了Windows Mixed Reality部分](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"MAC"&"独立"平台](../../images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到通用 Windows 平台：

1.  选择 **"文件>生成设置...**
2.  在 **"Windows"列表中选择**"通用平台"，然后选择"**切换平台"**
3.  将“体系结构”设置为“ARM64”
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D 项目”
6.  将 **"目标 SDK 版本"设置为****"最新安装"**
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中设置"生成"窗口的屏幕截图，其中突出显示了"通用Windows平台"](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../../../design/app-views.md)沉浸式视图而不是 2D 视图。

1. 从 **"生成设置..."** 打开"**播放器设置..."窗口** 并展开 **XR 设置** 组
2. 在 **"XR** **设置"** 部分中，选择"支持虚拟现实"以添加"虚拟现实设备"列表
3. 将 **"深度格式"** 设置为 **"16 位** 深度"，并选中" **启用深度缓冲区共享"**
4. 将“立体渲染模式”设置为“单通道实例化”
5. 如果要使用全息播放模式远程处理，请选择"支持的 **WSA** 全息远程处理"

![unity 编辑器中Project"设置"窗口的屏幕截图，其中突出显示了"播放器设置"部分](../../images/wmr-config-img-9.png)
