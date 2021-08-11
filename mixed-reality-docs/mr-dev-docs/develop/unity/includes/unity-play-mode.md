---
ms.openlocfilehash: f579cb73389d23be5959d212d4243361f00a27b8475ce74a16acc2bffa7a192b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192167"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. 在 HoloLens 上，请参阅 **Microsoft Store** 并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，切换到 "**编辑**" 菜单并选择 " **Project 设置**"。
1. 选择 **XR 插件管理**。
1. 确保选择了 " **Windows 独立**" 选项卡，在列表中查找 " **OpenXR** " 和 " **Windows Mixed Reality 功能集**"，并选中相应的复选框。
1. 接下来，请单击 " **窗口** " 菜单，展开 " **XR** " 子菜单，然后选择 " **OpenXR 编辑器远程处理**"。

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../images/openxr-features-img-02.png)

1. 单击 " **启用编辑器远程处理**"。

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](../images/openxr-features-img-03.png)

1. 如果出现 " **启用缺失的依赖项** " 按钮，请单击该按钮。 按钮上方的错误框描述了它正在启用的功能和原因。
1. 对于 "**远程主机名**"，请输入 HOLOLENS 的 IP 地址。
   1. 根据需要更改其他设置。
   1. 启动播放模式后，编辑器将尝试连接。
1. 选择 "**播放**" 按钮以启动播放模式，并在 HoloLens 上体验应用。 若要在播放模式下调试 c # 脚本，请[将 Visual Studio 附加到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。

> [!NOTE]
> 从版本0.1.0 起，全息远程处理运行时不支持定位点，并且 ARAnchorManager 功能将无法通过远程处理。  此功能即将推出。

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

1. 在 HoloLens 上，请参阅 **Microsoft Store** 并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，切换到 "**编辑**" 菜单并选择 " **Project 设置**"。
1. 选择 **XR 插件管理**。
1. 确保已选择 "**电脑、Mac & Linux 独立** 版" 选项卡，在列表中找到 **Windows Mixed Reality** ，并选中其复选框。
1. 接下来，请单击 "**窗口**" 菜单，展开 " **XR** " 子菜单，然后选择 " **Windows XR 插件远程处理**"。
1. 将 **仿真模式** 设置为 **远程设备**。
1. 对于 **远程计算机**，请输入 HOLOLENS 的 IP 地址。
1. 若要连接，请执行以下操作之一：
   1. 若要手动连接，请 **在 "播放**" 中取消选中连接，然后选择 "**连接**"。 应会看到 "**连接状态**" 更改为 "**已连接**"，并在 HoloLens 中看到屏幕显示为空白。
   1. 若要自动连接，请选中 **"播放时连接"**。 启动播放模式后，编辑器将尝试连接。
1. 选择 "**播放**" 按钮以启动播放模式，并在 HoloLens 上体验应用。 若要在播放模式下调试 c # 脚本，请[将 Visual Studio 附加到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

1. 在 HoloLens 上，请参阅 **Microsoft Store** 并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，单击 " **窗口** " 菜单，展开 " **XR** " 子菜单，并选择 Unity 2019) 中标记为 "已弃用" 的 **全息仿真** (。
1. 将 **仿真模式** 设置为 **远程设备**。
1. 如果使用的是第一代 HoloLens 或 HoloLens 2，请根据使用设置 **设备版本**。
1. 对于 **远程计算机**，请输入 HOLOLENS 的 IP 地址。
1. 选择“连接”  。 应会看到 "**连接状态**" 更改为 "**已连接**"，并在 HoloLens 中看到屏幕显示为空白。
1. 选择 "**播放**" 按钮以启动播放模式，并在 HoloLens 上体验应用。 若要在播放模式下调试 c # 脚本，请[将 Visual Studio 附加到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。
