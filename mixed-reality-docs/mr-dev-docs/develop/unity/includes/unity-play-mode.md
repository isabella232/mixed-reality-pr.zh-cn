---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345102"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**
1. 选择 **"XR 插件管理"。**
1. 确保选中 **"Windows** 独立"选项卡，在列表中找到 **"OpenXR"Windows Mixed Reality"** 功能集，并选中其复选框。 
1. 接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"OpenXR 编辑器远程处理"。**
1. 单击 **"启用编辑器远程处理"。**
1. 如果显示 **"启用缺少依赖项"** 按钮，则也单击该按钮。 按钮上方的错误框描述了它启用的功能以及原因。
1. 对于 **"远程主机名**"，请输入 HoloLens 的 IP 地址。
   1. 根据需要更改其他设置。
   1. 启动播放模式后，编辑器将尝试连接。
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。

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
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

1. 在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
1. 在 HoloLens 上，启动 **全息远程处理播放器** 应用。
1. 在 Unity 中，转到"**窗口**"菜单，展开 **XR** 子菜单，然后选择"全息仿真" (在 Unity 2019) 中标记为已弃用。
1. 将 **仿真模式设置为****"远程"到"设备"。**
1. 如果 **使用的是第一** 代 HoloLens 或设备，根据设备版本HoloLens 2。
1. 对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。
1. 选择“连接”  。 应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。
1. 选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。
