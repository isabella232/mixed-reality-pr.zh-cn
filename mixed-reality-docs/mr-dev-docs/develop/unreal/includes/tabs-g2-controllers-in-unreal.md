---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204205"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>启用 HP 运动控制器插件 

交互配置文件和控制器映射在 HP 运动控制器插件中，必须启用该插件，以向 Unreal 的输入系统公开控制器映射。

![启用 OpenXRHPController 插件](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>配置 Startup 和 HMDPluginPriority

使用 SteamVR 的 Unreal 中的输入存在一些差异。  设置项目时，请首先通过添加 vr 来确保它使用 SteamVR 的新输入 **系统。SteamVR.EnableVRInput=1** 到 **Engine/Config/ConsoleVariables.ini中的"启动"部分**。  此 ini 位于引擎安装目录中，而不是项目目录中。

![更新启动配置](../images/reverb-g2-img-07.png)

HP 运动控制器插件将启用 OpenXR。  如果不使用 OpenXR，则需要在 BaseEngine.ini 中编辑与 OpenXR 相同的目录中的 HMDPluginPriority ConsoleVariables.ini。  将 SteamVR 值更改为大于 OpenXRHMD 值。

![更新 HMDPluginPriority 配置](../images/reverb-g2-img-08.png)


