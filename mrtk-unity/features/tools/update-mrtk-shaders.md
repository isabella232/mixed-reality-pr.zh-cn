---
title: 着色器更新工具
description: 有关如何更新 MRTK 标准着色器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145136"
---
# <a name="updating-shaders"></a><span data-ttu-id="29ca6-104">正在更新着色器</span><span class="sxs-lookup"><span data-stu-id="29ca6-104">Updating Shaders</span></span>

<span data-ttu-id="29ca6-105">从版本2.6.0 开始，MRTK 着色器通过 MRTK 进行版本控制。着色器 sentinel 文件。</span><span class="sxs-lookup"><span data-stu-id="29ca6-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="29ca6-106">升级到新版本的 MRTK 时，可能会出现以下消息。</span><span class="sxs-lookup"><span data-stu-id="29ca6-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![更新着色器提示](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="29ca6-108">选择 **"是"** 将指示 MRTK   >    >  用最新版本覆盖资产 MRTK **着色** 器的内容。</span><span class="sxs-lookup"><span data-stu-id="29ca6-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="29ca6-109">选择 " **否** " 将保留当前文件。</span><span class="sxs-lookup"><span data-stu-id="29ca6-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="29ca6-110">"**忽略** `IgnoreUpdateCheck.sentinel` " 将在 **资产** MRTK 着色器中创建一个文件 ()  >    >  ，这将取消将来的着色器更新检查。</span><span class="sxs-lookup"><span data-stu-id="29ca6-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29ca6-111">当覆盖着色器文件时，任何自定义修改都将丢失。</span><span class="sxs-lookup"><span data-stu-id="29ca6-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="29ca6-112">请确保在升级之前备份任何已修改的着色器文件。</span><span class="sxs-lookup"><span data-stu-id="29ca6-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="29ca6-113">如果已将项目配置为使用 (URP) 的通用呈现管道 (LWRP) ，请重新运行 **混合现实工具包** > **实用工具** >
>  **升级 MRTK 标准着色器来实现轻型呈现管道**。</span><span class="sxs-lookup"><span data-stu-id="29ca6-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="29ca6-114">还可以使用 **混合现实工具包**  >  **实用工具** 在  >  Unity 编辑器的菜单栏上 **检查着色器更新**，同时检查着色器更新。</span><span class="sxs-lookup"><span data-stu-id="29ca6-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![检查着色器更新](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="29ca6-116">**检查着色器更新是否** 忽略 `IgnoreUpdateCheck.sentinel` 文件并允许按需着色器更新。</span><span class="sxs-lookup"><span data-stu-id="29ca6-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="29ca6-117">导入 MRTK unitypackage 文件时，不需要检查着色器更新。</span><span class="sxs-lookup"><span data-stu-id="29ca6-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
