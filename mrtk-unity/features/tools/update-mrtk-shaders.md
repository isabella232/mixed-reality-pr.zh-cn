---
title: 着色器更新工具
description: 有关如何更新 MRTK 标准着色器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647103"
---
# <a name="updating-shaders"></a><span data-ttu-id="59b23-104">更新着色器</span><span class="sxs-lookup"><span data-stu-id="59b23-104">Updating Shaders</span></span>

<span data-ttu-id="59b23-105">从版本 2.6.0 开始，MRTK 着色器通过 MRTK 进行版本控制。Shaders.sentinel 文件。</span><span class="sxs-lookup"><span data-stu-id="59b23-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="59b23-106">升级到新版本的 MRTK 时，可能会出现以下消息。</span><span class="sxs-lookup"><span data-stu-id="59b23-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![更新着色器提示](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="59b23-108">选择 **"** 是"会指示 MRTK 使用最新版本覆盖 **资产**  >  **MRTK**  >  着色器的内容。</span><span class="sxs-lookup"><span data-stu-id="59b23-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="59b23-109">选择 **"否** "将保留当前文件。</span><span class="sxs-lookup"><span data-stu-id="59b23-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="59b23-110">**忽略** 将在资产 MRTK 着色 () 创建文件，这将 `IgnoreUpdateCheck.sentinel`   >    >  禁止将来的着色器更新检查。</span><span class="sxs-lookup"><span data-stu-id="59b23-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59b23-111">覆盖着色器文件时，任何自定义修改都将丢失。</span><span class="sxs-lookup"><span data-stu-id="59b23-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="59b23-112">在升级之前，请务必备份任何已修改的着色器文件。</span><span class="sxs-lookup"><span data-stu-id="59b23-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="59b23-113">如果项目已配置为使用通用呈现管道 (URP) - 以前是轻型呈现管道 (LWRP) ，请重新运行混合现实工具包实用工具升级轻型呈现管道 >  >  >
>  **的 MRTK** 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="59b23-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="59b23-114">还可以在 Unity 编辑器的菜单栏上随时使用混合现实工具包实用工具检查着色器更新检查着色器  >    >    >  更新。</span><span class="sxs-lookup"><span data-stu-id="59b23-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![检查着色器更新](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="59b23-116">**检查着色器更新** 是否忽略 `IgnoreUpdateCheck.sentinel` 文件并允许按需着色器更新。</span><span class="sxs-lookup"><span data-stu-id="59b23-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="59b23-117">导入 MRTK .unitypackage 文件时，无需检查着色器更新。</span><span class="sxs-lookup"><span data-stu-id="59b23-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
