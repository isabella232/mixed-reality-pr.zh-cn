---
title: 设计自己的沉浸式环境
description: 了解如何创建自己的 Windows Mixed Reality 主环境。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，Home，自定义环境，地点，cliff 房子，skyloft，用户，创建，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: ca6a41f8388a767b1191ddc3b377822567a603a6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583306"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="10b3f-104">设计自己的沉浸式环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="10b3f-105">这是一项实验性功能。</span><span class="sxs-lookup"><span data-stu-id="10b3f-105">This is an experimental feature.</span></span> <span data-ttu-id="10b3f-106">试一试，并对它感兴趣，但如果所有内容均未按预期工作，则不会惊讶。</span><span class="sxs-lookup"><span data-stu-id="10b3f-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="10b3f-107">我们正在评估此功能的生存能力，并对使用它感兴趣，因此请告诉我们你的体验 (以及在 [开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)中找到) 的任何 bug。</span><span class="sxs-lookup"><span data-stu-id="10b3f-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="10b3f-108">从 [windows 10 4 月2018版更新](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)开始，我们启用了一个试验性功能，该功能使你能够将自定义环境添加到 "开始" 菜单上的 "位置选取器 (，) 用作 [Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="10b3f-108">Starting with the [Windows 10 April 2018 update](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="10b3f-109">Windows Mixed Reality 提供两个默认环境： Cliff 房子和 Skyloft，你可以选择作为你的家庭。</span><span class="sxs-lookup"><span data-stu-id="10b3f-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, you can choose as your home.</span></span> <span data-ttu-id="10b3f-110">创建自定义环境使你可以通过自己的创建来扩展列表。</span><span class="sxs-lookup"><span data-stu-id="10b3f-110">Creating custom environments allows you to expand the list with your own creations.</span></span> <span data-ttu-id="10b3f-111">我们正在使此功能在早期状态下提供，以便评估创建者和开发人员的兴趣。</span><span class="sxs-lookup"><span data-stu-id="10b3f-111">We're making this feature available in an early state to evaluate interest from creators and developers.</span></span> <span data-ttu-id="10b3f-112">了解你创建了哪些类型的世界，并了解如何使用不同的创作工具。</span><span class="sxs-lookup"><span data-stu-id="10b3f-112">See what kinds of worlds you create and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="10b3f-113">使用自定义环境时，您会注意到，teleporting、与应用程序的交互，并使全息影像的工作方式与在 Cliff 房子和 Skyloft 中的工作方式相同。</span><span class="sxs-lookup"><span data-stu-id="10b3f-113">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="10b3f-114">你可以在幻想环境中浏览 web，或使用全息影像来填充现在俨然</span><span class="sxs-lookup"><span data-stu-id="10b3f-114">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="10b3f-115">设备支持</span><span class="sxs-lookup"><span data-stu-id="10b3f-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="10b3f-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="10b3f-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="10b3f-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="10b3f-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="10b3f-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="10b3f-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="10b3f-119">自定义家庭环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-119">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="10b3f-120">✔️</span><span class="sxs-lookup"><span data-stu-id="10b3f-120">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="10b3f-121">尝试使用示例环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-121">Trying a sample environment</span></span>

<span data-ttu-id="10b3f-122">我们创建了一个示例环境，其中显示了自定义 home 环境的一些创新可能性。</span><span class="sxs-lookup"><span data-stu-id="10b3f-122">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="10b3f-123">请按照以下步骤进行试用：</span><span class="sxs-lookup"><span data-stu-id="10b3f-123">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="10b3f-124">[下载示例幻想岛环境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (链接点到自解压缩可执行文件) 。</span><span class="sxs-lookup"><span data-stu-id="10b3f-124">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="10b3f-125">![幻想岛示例环境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="10b3f-125">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="10b3f-126">*幻想岛示例环境*</span><span class="sxs-lookup"><span data-stu-id="10b3f-126">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="10b3f-127">运行下载的 **Fantasy_Island.exe** 文件。</span><span class="sxs-lookup"><span data-stu-id="10b3f-127">Run the **Fantasy_Island.exe** file you downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="10b3f-128">尝试运行从 web (下载的 .exe 文件时) ，可能会遇到 "受 Windows 保护的 PC" 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="10b3f-128">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="10b3f-129">若要从此弹出窗口中运行 Fantasy_Island.exe，请选择 " **详细信息** "，然后 **继续运行**。</span><span class="sxs-lookup"><span data-stu-id="10b3f-129">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="10b3f-130">此安全设置旨在防止您下载可能不想要信任的文件，因此，请仅当您信任文件的源时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="10b3f-130">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="10b3f-131">打开 **文件资源管理器** 并导航到 "环境" 文件夹，方法是在地址栏中粘贴以下文件位置： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 。</span><span class="sxs-lookup"><span data-stu-id="10b3f-131">Open **File Explorer** and navigate to the environments folder by pasting the following file location in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="10b3f-132">将下载的示例环境复制到此文件夹。</span><span class="sxs-lookup"><span data-stu-id="10b3f-132">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="10b3f-133">重新启动 **混合现实门户** ，以便在 "位置" 选取器中刷新环境列表。</span><span class="sxs-lookup"><span data-stu-id="10b3f-133">Restart **Mixed Reality Portal** to refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="10b3f-134">戴上耳机。</span><span class="sxs-lookup"><span data-stu-id="10b3f-134">Put on your headset.</span></span> <span data-ttu-id="10b3f-135">进入 home 后，使用 Windows 按钮打开 " **开始" 菜单** 。</span><span class="sxs-lookup"><span data-stu-id="10b3f-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="10b3f-136">选择固定应用列表上方的 " **位置** " 图标以选择 home 环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="10b3f-137">你会发现你在位置列表中下载的幻想岛环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-137">You'll find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="10b3f-138">选择 " **幻想岛** " 输入新的自定义家庭环境！</span><span class="sxs-lookup"><span data-stu-id="10b3f-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="10b3f-139">创建自己的自定义环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-139">Creating your own custom environment</span></span>

<span data-ttu-id="10b3f-140">除了使用我们的示例环境以外，你还可以使用你最喜欢的3D 编辑软件导出你自己的自定义环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="10b3f-141">建模准则</span><span class="sxs-lookup"><span data-stu-id="10b3f-141">Modeling guidelines</span></span>

<span data-ttu-id="10b3f-142">在对环境进行建模时，请记住以下建议，以便用户在 believably 规模世界中以正确的方向进行：</span><span class="sxs-lookup"><span data-stu-id="10b3f-142">When modeling your environment, keep the following recommendations in mind so that users spawns in the correct orientation in a believably sized world:</span></span>

1. <span data-ttu-id="10b3f-143">用户将生成0，0，0，以便将衍生位置围绕原点居中。</span><span class="sxs-lookup"><span data-stu-id="10b3f-143">Users will spawn at 0,0,0 so center your spawn location around the origin.</span></span>
2. <span data-ttu-id="10b3f-144">工作单元应设置为 "米"，以便可以在全球范围内创作资产。</span><span class="sxs-lookup"><span data-stu-id="10b3f-144">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="10b3f-145">向上轴应设置为 "Y"。</span><span class="sxs-lookup"><span data-stu-id="10b3f-145">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="10b3f-146">资产应正面朝正 Z 轴 "前进"。</span><span class="sxs-lookup"><span data-stu-id="10b3f-146">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="10b3f-147">无需合并所有网格，但建议将其定向到 "资源受限设备"。</span><span class="sxs-lookup"><span data-stu-id="10b3f-147">You don't have to combine all your meshes, but it's recommended if you're targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="10b3f-148">导出环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-148">Exporting your environment</span></span>

<span data-ttu-id="10b3f-149">Windows Mixed Reality 依赖于二进制 glTF (. glb) 作为环境的资产传送格式。</span><span class="sxs-lookup"><span data-stu-id="10b3f-149">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="10b3f-150">glTF 是由 Khronos 组维护的用于3D 资产交付的版税免费开放标准。</span><span class="sxs-lookup"><span data-stu-id="10b3f-150">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="10b3f-151">Microsoft 对跨 Windows 应用和体验的格式的支持将随着 glTF 发展为可互操作的3D 内容的行业标准而发展。</span><span class="sxs-lookup"><span data-stu-id="10b3f-151">Microsoft’s support for the format across Windows apps and experiences will grow as glTF evolves as an industry standard for interoperable 3D content.</span></span>

<span data-ttu-id="10b3f-152">导出要用作自定义家庭环境的资产的第一步是生成 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="10b3f-152">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="10b3f-153">GlTF 工作组维护一 [系列受支持的导出程序和转换器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) ，以创建 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="10b3f-153">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="10b3f-154">若要开始使用，请使用此页上列出的程序之一创建和导出 glTF 2.0 模型，或使用其中一个受支持的转换器转换现有的模型。</span><span class="sxs-lookup"><span data-stu-id="10b3f-154">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="10b3f-155">此外，请查看 [这篇有用的文章，其中概述了如何直接从 Blender 和 3DS Max 导出 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="10b3f-155">Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="10b3f-156">环境限制</span><span class="sxs-lookup"><span data-stu-id="10b3f-156">Environment limits</span></span>

<span data-ttu-id="10b3f-157">所有环境必须 < 256 mb。</span><span class="sxs-lookup"><span data-stu-id="10b3f-157">All environments must be < 256 mbs.</span></span> <span data-ttu-id="10b3f-158">大于 256 mb 的环境将无法加载，并将使用围绕用户的默认 skybox 来回退到空世界。</span><span class="sxs-lookup"><span data-stu-id="10b3f-158">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="10b3f-159">创建模型时，请记住此文件大小限制。</span><span class="sxs-lookup"><span data-stu-id="10b3f-159">Keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="10b3f-160">此外，如果您计划使用 WindowsMRAssetConverter 按如下所述的方式优化您的环境，则必须 cognizant 纹理大小会随着优化器创建具有更大文件大小但加载速度更快的纹理而增加。</span><span class="sxs-lookup"><span data-stu-id="10b3f-160">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="10b3f-161">优化环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-161">Optimizing your environment</span></span>

<span data-ttu-id="10b3f-162">Windows Mixed Reality 支持很多可显著减少环境加载时间的可选优化。</span><span class="sxs-lookup"><span data-stu-id="10b3f-162">Windows Mixed Reality supports many optional optimizations that can significantly reduce your environment load times.</span></span> <span data-ttu-id="10b3f-163">请特别注意具有大量纹理的环境，因为它们有时会在加载时超时。</span><span class="sxs-lookup"><span data-stu-id="10b3f-163">Pay special attention with environments that have lots of textures, as they'll sometimes time out while loading.</span></span> <span data-ttu-id="10b3f-164">通常，我们建议对所有资产执行此步骤，但是，具有少量或低分辨率纹理的小型环境不会始终需要此步骤。</span><span class="sxs-lookup"><span data-stu-id="10b3f-164">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="10b3f-165">为了使此过程更容易，我们已创建了 [在 GitHub 上可用的 Windows Mixed Reality 资产转换器 () ](https://github.com/Microsoft/glTF-Toolkit/releases) ，以便进行优化。</span><span class="sxs-lookup"><span data-stu-id="10b3f-165">To make this process easier, we've created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to do your optimizations.</span></span> <span data-ttu-id="10b3f-166">此工具使用 Microsoft glTF 工具包中提供的一组实用工具来优化任何标准 2.0 glTF 或 glb，方法是执行额外的纹理打包、压缩和分辨率下降。</span><span class="sxs-lookup"><span data-stu-id="10b3f-166">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or.glb by performing an extra texture packing, compression, and resolution down-scaling.</span></span> 

<span data-ttu-id="10b3f-167">转换器当前支持多个标志来调整优化的确切行为。</span><span class="sxs-lookup"><span data-stu-id="10b3f-167">The converter currently supports several flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="10b3f-168">建议运行以下标志以获得最佳结果：</span><span class="sxs-lookup"><span data-stu-id="10b3f-168">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="10b3f-169">Flag</span><span class="sxs-lookup"><span data-stu-id="10b3f-169">Flag</span></span>|<span data-ttu-id="10b3f-170">建议值 (s) </span><span class="sxs-lookup"><span data-stu-id="10b3f-170">Recommended Value(s)</span></span>|<span data-ttu-id="10b3f-171">说明</span><span class="sxs-lookup"><span data-stu-id="10b3f-171">Description</span></span>
---|---|---
<span data-ttu-id="10b3f-172">-最大纹理大小</span><span class="sxs-lookup"><span data-stu-id="10b3f-172">-max-texture-size</span></span>|<span data-ttu-id="10b3f-173">1024或2048</span><span class="sxs-lookup"><span data-stu-id="10b3f-173">1024 or 2048</span></span>| <span data-ttu-id="10b3f-174">调整该值以提高纹理质量，默认值为512x512。</span><span class="sxs-lookup"><span data-stu-id="10b3f-174">Tweak the value to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="10b3f-175">较大的值将显著影响环境的文件大小，因此请记住 256 mb 的限制</span><span class="sxs-lookup"><span data-stu-id="10b3f-175">A larger value will significantly impact the file size of the environment so keep the 256-mb limit in mind</span></span>
<span data-ttu-id="10b3f-176">-最小版本</span><span class="sxs-lookup"><span data-stu-id="10b3f-176">-min-version</span></span>|<span data-ttu-id="10b3f-177">1803</span><span class="sxs-lookup"><span data-stu-id="10b3f-177">1803</span></span>|<span data-ttu-id="10b3f-178">仅在 windows >= 1803 的版本上支持自定义环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-178">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="10b3f-179">此标志将删除较旧版本的纹理，并减小最终资产的文件大小</span><span class="sxs-lookup"><span data-stu-id="10b3f-179">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="10b3f-180">例如：</span><span class="sxs-lookup"><span data-stu-id="10b3f-180">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="10b3f-181">测试环境</span><span class="sxs-lookup"><span data-stu-id="10b3f-181">Testing your environment</span></span>

<span data-ttu-id="10b3f-182">拥有最终的 glb 环境后，就可以在耳机中进行测试了。</span><span class="sxs-lookup"><span data-stu-id="10b3f-182">Once you have your final.glb environment, you're ready to test it out in the headset.</span></span> <span data-ttu-id="10b3f-183">从 ["尝试示例环境"](#trying-a-sample-environment) 部分的步骤2开始，使用自定义环境作为混合现实主页。</span><span class="sxs-lookup"><span data-stu-id="10b3f-183">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="sending-feedback"></a><span data-ttu-id="10b3f-184">发送反馈</span><span class="sxs-lookup"><span data-stu-id="10b3f-184">Sending feedback</span></span>

<span data-ttu-id="10b3f-185">尽管我们正在评估此试验性功能，但我们有兴趣了解你使用自定义环境的方式、可能发现的任何错误，以及你喜欢该功能的方式。</span><span class="sxs-lookup"><span data-stu-id="10b3f-185">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may find, and how you like the feature.</span></span> <span data-ttu-id="10b3f-186">在 [开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)中共享用于创建和使用自定义家庭环境的任何反馈。</span><span class="sxs-lookup"><span data-stu-id="10b3f-186">Share any feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="10b3f-187">疑难解答和提示</span><span class="sxs-lookup"><span data-stu-id="10b3f-187">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="10b3f-188">如何实现更改环境的名称？</span><span class="sxs-lookup"><span data-stu-id="10b3f-188">How do I change the name of the environment?</span></span>

<span data-ttu-id="10b3f-189">"环境" 文件夹中的文件名将用在 "位置" 选取器中。</span><span class="sxs-lookup"><span data-stu-id="10b3f-189">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="10b3f-190">若要更改环境的名称，请重命名环境文件名称，然后重启混合现实门户。</span><span class="sxs-lookup"><span data-stu-id="10b3f-190">To change the name of your environment, rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="10b3f-191">如何实现从 "我的位置" 选取器中删除自定义环境？</span><span class="sxs-lookup"><span data-stu-id="10b3f-191">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="10b3f-192">若要删除自定义环境，请打开电脑上的 "环境" 文件夹 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 并删除环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-192">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="10b3f-193">重新启动混合现实门户后，此环境将不再显示在 "位置" 选取器中。</span><span class="sxs-lookup"><span data-stu-id="10b3f-193">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="10b3f-194">默认情况下，如何实现到我最喜欢的自定义环境？</span><span class="sxs-lookup"><span data-stu-id="10b3f-194">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="10b3f-195">当前无法更改默认环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-195">You can't currently change the default environment.</span></span> <span data-ttu-id="10b3f-196">每次重新启动混合现实门户时，都将返回到 Cliff 房子环境。</span><span class="sxs-lookup"><span data-stu-id="10b3f-196">Each time you restart Mixed Reality Portal, you'll be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="10b3f-197">我将生成空白空间</span><span class="sxs-lookup"><span data-stu-id="10b3f-197">I spawn into a blank space</span></span>

<span data-ttu-id="10b3f-198">Windows Mixed Reality [不支持超过 256 mb 的环境](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="10b3f-198">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="10b3f-199">当某个环境超过此限制时，你将在不带任何型号的空天空中居住。</span><span class="sxs-lookup"><span data-stu-id="10b3f-199">When an environment exceeds this limit, you'll land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="10b3f-200">加载环境需要很长时间</span><span class="sxs-lookup"><span data-stu-id="10b3f-200">It takes a long time to load my environment</span></span>

<span data-ttu-id="10b3f-201">可以在环境中添加可选优化，使其更快加载。</span><span class="sxs-lookup"><span data-stu-id="10b3f-201">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="10b3f-202">有关详细信息，请参阅 ["优化你的环境"](#optimizing-your-environment) 。</span><span class="sxs-lookup"><span data-stu-id="10b3f-202">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="10b3f-203">我的环境规模不正确</span><span class="sxs-lookup"><span data-stu-id="10b3f-203">The scale of my environment is incorrect</span></span>

<span data-ttu-id="10b3f-204">加载环境时，Windows Mixed Reality 会将 glTF 单位转换为1米。</span><span class="sxs-lookup"><span data-stu-id="10b3f-204">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="10b3f-205">如果你的环境加载了意外的规模，请仔细检查你的导出器，以确保按1计量规模进行建模。</span><span class="sxs-lookup"><span data-stu-id="10b3f-205">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1-meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="10b3f-206">我的环境中的生成位置不正确</span><span class="sxs-lookup"><span data-stu-id="10b3f-206">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="10b3f-207">默认生成位置位于环境中的0，0，0。</span><span class="sxs-lookup"><span data-stu-id="10b3f-207">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="10b3f-208">目前不能自定义此位置，因此你必须通过导出环境来修改衍生点，并将源置于所需的生成点。</span><span class="sxs-lookup"><span data-stu-id="10b3f-208">It's not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the spawn point you want.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="10b3f-209">音频在环境中不正确</span><span class="sxs-lookup"><span data-stu-id="10b3f-209">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="10b3f-210">创建自定义环境时，它将使用与所创建的物理空间不匹配的噪声渲染模拟。</span><span class="sxs-lookup"><span data-stu-id="10b3f-210">When you create your custom environment, it will be using an acoustics rendering simulation that doesn't match the physical space you've created.</span></span> <span data-ttu-id="10b3f-211">声音可能来自错误的方向，可能听起来 muffled。</span><span class="sxs-lookup"><span data-stu-id="10b3f-211">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="10b3f-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10b3f-212">See also</span></span>
* [<span data-ttu-id="10b3f-213">GitHub 上的 Windows Mixed Reality 资产转换器 () </span><span class="sxs-lookup"><span data-stu-id="10b3f-213">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)