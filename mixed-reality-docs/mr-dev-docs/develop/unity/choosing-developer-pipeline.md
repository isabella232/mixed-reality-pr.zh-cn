---
title: 选择开发人员管道
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 开发管道建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394551"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="babab-104">选择开发人员管道</span><span class="sxs-lookup"><span data-stu-id="babab-104">Choosing your developer pipeline</span></span>

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

<span data-ttu-id="babab-106">尽管我们目前 **建议安装 Unity 2019.4 LTS 并使用旧式内置 XR** 进行混合现实开发，但也可以使用其他 Unity 配置来构建应用。</span><span class="sxs-lookup"><span data-stu-id="babab-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="babab-107"> (建议) 混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="babab-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="babab-108">适用于 HoloLens 2 的 Microsoft 当前推荐 Unity 配置是混合现实工具包 .。。</span><span class="sxs-lookup"><span data-stu-id="babab-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="babab-109">安装混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="babab-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="babab-110">[混合现实功能工具](welcome-to-mr-feature-tool.md)是开发人员发现混合现实功能包并将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="babab-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="babab-111">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="babab-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="babab-112">验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。</span><span class="sxs-lookup"><span data-stu-id="babab-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="babab-113">为 Unity 导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="babab-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="babab-115">[混合现实工具包](mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="babab-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="babab-116">遵循下面的[安装和使用说明](welcome-to-mr-feature-tool.md#system-requirements)，选择“Mixed Reality Toolkit Foundation”包，安装混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="babab-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="babab-117">建议完成我们策划的 [HoloLens](unity-development-overview.md#1-getting-started) 或 [VR](unity-development-wmr-overview.md#1-getting-started) 开发历程中的入门部分。</span><span class="sxs-lookup"><span data-stu-id="babab-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="babab-118">如果你已遵循针对 HoloLens 的 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="babab-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="babab-119">请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.6.1 和 Unity 2019.4 LTS 。</span><span class="sxs-lookup"><span data-stu-id="babab-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="babab-120">如果你不想使用 MRTK for Unity，则需要[自行编写所有交互和行为的脚本](configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="babab-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="babab-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="babab-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="babab-122">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="babab-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="babab-123">手动</span><span class="sxs-lookup"><span data-stu-id="babab-123">Manual</span></span> 

<span data-ttu-id="babab-124">待定 .。。</span><span class="sxs-lookup"><span data-stu-id="babab-124">TBD...</span></span>