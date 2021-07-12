---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603704"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

安装具有新的混合现实功能工具应用程序的 OpenXR 插件。 按照 [安装和使用说明](../../welcome-to-mr-feature-tool.md)进行操作，并在 **平台支持** 类别中选择 **混合现实 OpenXR 插件** 包：

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>设置生成目标

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

如果以 HoloLens 2 为目标，则需要切换到通用 Windows 平台：

1. 选择 **文件 > 生成设置 ...**
2. 选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3. 将“体系结构”设置为“ARM64”
4. 将“目标设备”设置为“HoloLens” 
5. 将“生成类型”设置为“D3D 项目”
6. 将 **目标 SDK 版本** 设置为 **已安装的最新** 版本

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，并突出显示通用 Windows 平台](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要将 OpenXR 设置为 Unity 中的运行时：

1. 在 Unity 编辑器中，导航到 "**编辑 >" Project "设置**
2. 在设置列表中，如果使用 MRFT 安装了 Mixed Reality OpenXR 插件，请选择 " **XR 插件管理**" (应已安装) 
3. 选中 " **在启动时初始化 XR** " 框
4. 如果面向的是 Desktop VR，请在 "监视器")  ("计算机" "独立" 选项卡，然后选中 " **OpenXR** " 和 " **Windows Mixed Reality 功能**" 框
5. 如果以 HoloLens 2 为目标，请切换到 "通用 Windows 平台" 选项卡 (Windows 徽标) 并选中 " **OpenXR** " 和 " **Microsoft HoloLens 功能集**" 框

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](../../images/openxr-img-05.png)

> [!IMPORTANT]
> 如果在 " **OpenXR" 插件** 旁出现黄色警告图标，请单击该图标，然后选择 " **全部修复** "，然后继续。 Unity 编辑器可能需要自动重启以使更改生效。

![OpenXR 项目验证窗口的屏幕截图](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

如果要为 HoloLens 2 进行开发，请选择 "**混合现实" > Project > "HoloLens 2 菜单项应用推荐的项目设置**，以获得更好的应用性能。

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](../../images/openxr-img-08.png)

你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！  继续阅读下一节，了解如何使用 OpenXR 示例。

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 和 HoloLens 2 的 Unity 示例项目

查看示例 unity 项目的[OpenXR 混合现实示例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples)存储库展示如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实耳机构建 unity 应用程序。

或者，如果你已准备好开始使用空白项目，请转到 [相机设置](../../camera-in-unity.md) 一文。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

> [!CAUTION]
> Windows XR 插件在 unity 2021.1 中已弃用，并将在 unity 2021.2 中删除。  对于 Unity 2020 开发，Microsoft 建议改用 OpenXR 插件。

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

如果以 HoloLens 2 为目标，则需要切换到通用 Windows 平台：

1.  选择 **文件 > 生成设置 ...**
2.  选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3.  将“体系结构”设置为“ARM64”
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D 项目”
6.  将 **目标 SDK 版本** 设置为 **已安装的最新** 版本
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，并突出显示通用 Windows 平台](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../../../design/app-views.md) 而不是2d 视图：

1. 在 Unity 编辑器中，导航到 "**编辑 > Project" 设置**"，然后选择" **XR 插件管理**"

2. 如果出现，请选择 " **安装 XR 插件管理** "

![在 unity 编辑器中打开的 Project 设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality**

![在 unity 编辑器中打开的 Project 设置窗口的屏幕截图，其中突出显示了 XR 插件管理](../../images/wmr-config-img-7.png)

4. 选择 " **XR 插件管理**  >  **Windows Mixed Reality** " 部分，选中 "所有" 框并将 **深度缓冲区格式** 设置为 **深度缓冲区16位**

![在 unity 编辑器中打开的 Project 设置窗口的屏幕截图，其中突出显示了 Windows Mixed Reality 部分](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](../../images/wmr-config-img-3.png)

如果以 HoloLens 2 为目标，则需要切换到通用 Windows 平台：

1.  选择 **文件 > 生成设置 ...**
2.  选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3.  将“体系结构”设置为“ARM64”
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D 项目”
6.  将 **目标 SDK 版本** 设置为 **已安装的最新** 版本
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，并突出显示通用 Windows 平台](../../images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../../../design/app-views.md) 而不是2d 视图。

1. 从生成设置打开 **播放机设置**... **窗口** 并展开 **XR 设置** 组
2. 在 " **XR 设置**" 部分中，选择 "**支持的虚拟现实**" 以添加虚拟现实设备列表
3. 将 **深度格式** 设置为 **16 位深度**，并选中 "**启用深度缓冲区共享**"
4. 将“立体渲染模式”设置为“单通道实例化”
5. 如果要使用全息播放模式远程处理，请选择 " **支持 WSA 全息远程处理** "

![突出显示了 "播放机设置" 部分的 "Project 设置" 窗口的屏幕截图](../../images/wmr-config-img-9.png)
