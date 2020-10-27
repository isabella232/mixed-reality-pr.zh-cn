---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638622"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>启用 HP 运动控制器插件 

交互配置文件和控制器映射位于 HP 运动控制器插件中，必须启用此插件才能向 Unreal 的输入系统公开控制器映射。

![启用 OpenXRHPController 插件](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>配置启动和 HMDPluginPriority

使用 SteamVR 的 Unreal 中的输入有几个不同之处。  设置项目时，请首先通过添加 vr 确保它正在使用 SteamVR 的新输入系统 **。SteamVR. EnableVRInput = 1** 到 **Engine/Config/ConsoleVariables.ini** 中的 **启动** 部分。  此 ini 位于引擎安装目录中，而不是项目目录中。

![更新启动配置](../images/reverb-g2-img-07.png)

HP 运动控制器插件将启用 OpenXR。  如果使用的不是 OpenXR，则需要在 ConsoleVariables.ini 的同一目录中编辑 BaseEngine.ini 的 SteamVR 的 HMDPluginPriority。  将 SteamVR 值更改为大于 OpenXRHMD 值。

![正在更新 HMDPluginPriority 配置](../images/reverb-g2-img-08.png)


