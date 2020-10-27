---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638622"
---
# <a name="all-platforms"></a>[<span data-ttu-id="ce762-101">所有平台</span><span class="sxs-lookup"><span data-stu-id="ce762-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="ce762-102">启用 HP 运动控制器插件</span><span class="sxs-lookup"><span data-stu-id="ce762-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="ce762-103">交互配置文件和控制器映射位于 HP 运动控制器插件中，必须启用此插件才能向 Unreal 的输入系统公开控制器映射。</span><span class="sxs-lookup"><span data-stu-id="ce762-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![启用 OpenXRHPController 插件](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="ce762-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="ce762-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="ce762-106">配置启动和 HMDPluginPriority</span><span class="sxs-lookup"><span data-stu-id="ce762-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="ce762-107">使用 SteamVR 的 Unreal 中的输入有几个不同之处。</span><span class="sxs-lookup"><span data-stu-id="ce762-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="ce762-108">设置项目时，请首先通过添加 vr 确保它正在使用 SteamVR 的新输入系统 **。SteamVR. EnableVRInput = 1** 到 **Engine/Config/ConsoleVariables.ini** 中的 **启动** 部分。</span><span class="sxs-lookup"><span data-stu-id="ce762-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="ce762-109">此 ini 位于引擎安装目录中，而不是项目目录中。</span><span class="sxs-lookup"><span data-stu-id="ce762-109">This ini is found in the engine install directory, not the project directory.</span></span>

![更新启动配置](../images/reverb-g2-img-07.png)

<span data-ttu-id="ce762-111">HP 运动控制器插件将启用 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="ce762-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="ce762-112">如果使用的不是 OpenXR，则需要在 ConsoleVariables.ini 的同一目录中编辑 BaseEngine.ini 的 SteamVR 的 HMDPluginPriority。</span><span class="sxs-lookup"><span data-stu-id="ce762-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="ce762-113">将 SteamVR 值更改为大于 OpenXRHMD 值。</span><span class="sxs-lookup"><span data-stu-id="ce762-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![正在更新 HMDPluginPriority 配置](../images/reverb-g2-img-08.png)


