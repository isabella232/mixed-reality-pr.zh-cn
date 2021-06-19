---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392286"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**
1. 选择 **"XR 插件管理"。**
1. 确保选中 **"Windows** 独立"选项卡，在列表中找到 **"OpenXR"Windows Mixed Reality"** 功能集，并选中其复选框。 
1. 接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"OpenXR 编辑器远程处理"。**

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../images/openxr-features-img-02.png)

1. 单击 **"启用编辑器远程处理"。**

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了"功能"](../images/openxr-features-img-03.png)

1. 如果显示 **"启用缺少依赖项"** 按钮，则也单击该按钮。 按钮上方的错误框描述了它启用的功能以及原因。
1. 对于 **"远程主机名**"，请输入 HoloLens 的 IP 地址。
   1. 根据需要更改其他设置。
   1. 启动播放模式后，编辑器将尝试连接。
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。 若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

> [!NOTE]
> 从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。  此功能将在未来版本中推出。

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**
1. 选择 **"XR 插件管理"。**
1. 确保选中 **"Windows** 独立"选项卡 **，Windows Mixed Reality列表中** 找到该选项卡，并选中其复选框。
1. 接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"Windows XR 插件远程处理"。**
1. 将 **仿真模式设置为****"远程"到"设备"。**
1. 对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。
1. 若要连接，请进行连接：
   1. 若要手动连接，请取消选中"**播放时连接"，** 然后选择"连接 **"。** 应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。
   1. 若要自动连接，请选中"**播放时连接"。** 启动播放模式后，编辑器将尝试连接。
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。 若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，转到"**窗口**"菜单，展开 **XR** 子菜单，然后选择"全息仿真" (在 Unity 2019) 中标记为已弃用。
1. 将 **仿真模式设置为****"远程"到"设备"。**
1. 如果 **使用的是第一** 代 HoloLens 或设备，根据设备版本HoloLens 2。
1. 对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。
1. 选择“连接”  。 应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。 若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)
