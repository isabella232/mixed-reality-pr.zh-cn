---
title: 3D 应用启动器设计指南
description: 3D 应用启动器是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，3D 应用程序启动器，沉浸式耳机，动态立方体，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，UWP，Win32，照明，颜色
ms.openlocfilehash: a501b4bdc86df17f6d005c2f7ccf4fe6a94a4b43
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703473"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="13488-104">3D 应用启动器设计指南</span><span class="sxs-lookup"><span data-stu-id="13488-104">3D app launcher design guidance</span></span>

<span data-ttu-id="13488-105">当你在 Windows Mixed Reality 沉浸式 (VR) 耳机上，你可以输入 Windows Mixed Reality 主页，在山上和水 (周围的 cliff 上以房子显示，但你可以 [选择其他环境，甚至创建自己的](../design/add-custom-home-environments.md)) 。</span><span class="sxs-lookup"><span data-stu-id="13488-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="13488-106">在此家中，用户可以自由地按所需的方式排列和组织3D 对象和应用。</span><span class="sxs-lookup"><span data-stu-id="13488-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="13488-107">**3d 应用启动器** 是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。</span><span class="sxs-lookup"><span data-stu-id="13488-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="13488-108">![示例： Floaty 鸟3D 应用启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13488-109">*Floaty 鸟3D 应用启动器示例 (虚构应用)*</span><span class="sxs-lookup"><span data-stu-id="13488-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="13488-110">3D 应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="13488-110">3D app launcher creation process</span></span>

<span data-ttu-id="13488-111">创建三维应用启动器有三个步骤：</span><span class="sxs-lookup"><span data-stu-id="13488-111">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="13488-112">本文 (设计和 concepting) </span><span class="sxs-lookup"><span data-stu-id="13488-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="13488-113">建模和导出</span><span class="sxs-lookup"><span data-stu-id="13488-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="13488-114">将其集成到应用程序中：</span><span class="sxs-lookup"><span data-stu-id="13488-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="13488-115">UWP 应用</span><span class="sxs-lookup"><span data-stu-id="13488-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="13488-116">Win32 应用</span><span class="sxs-lookup"><span data-stu-id="13488-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="13488-117">设计概念</span><span class="sxs-lookup"><span data-stu-id="13488-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="13488-118">太棒了</span><span class="sxs-lookup"><span data-stu-id="13488-118">Fantastic yet familiar</span></span>

<span data-ttu-id="13488-119">应用启动器所在的 Windows Mixed Reality 环境是部分熟悉的部分精巧/科幻。</span><span class="sxs-lookup"><span data-stu-id="13488-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="13488-120">最佳启动器遵循这一领域的规则。</span><span class="sxs-lookup"><span data-stu-id="13488-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="13488-121">考虑如何从应用程序中获取熟悉的代表对象，但要折上一些实际现实规则。</span><span class="sxs-lookup"><span data-stu-id="13488-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="13488-122">将产生幻数。</span><span class="sxs-lookup"><span data-stu-id="13488-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="13488-123">直观</span><span class="sxs-lookup"><span data-stu-id="13488-123">Intuitive</span></span>

<span data-ttu-id="13488-124">当你查看应用程序启动器时，启动你的应用程序的目的是非常明显，不会造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="13488-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="13488-125">例如，请确保您的启动器是您的应用程序的一个显而易见的代表，这不会对 Cliff 房子中的一 décor。</span><span class="sxs-lookup"><span data-stu-id="13488-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="13488-126">应用启动器应邀请人员触摸/选择。</span><span class="sxs-lookup"><span data-stu-id="13488-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="13488-127">![示例：全新备注3D 应用启动器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13488-128">*全新说明3D 应用启动器示例 (虚构应用)*</span><span class="sxs-lookup"><span data-stu-id="13488-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="13488-129">主比例</span><span class="sxs-lookup"><span data-stu-id="13488-129">Home scale</span></span>

<span data-ttu-id="13488-130">Cliff 房子中的三维应用启动器及其默认大小对于空间中的其他 "物理" 对象应该是有意义的。</span><span class="sxs-lookup"><span data-stu-id="13488-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="13488-131">如果将您的启动器置于附近（比如，房屋植物或某个家具），则应在家中、按大小进行调整。</span><span class="sxs-lookup"><span data-stu-id="13488-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="13488-132">很好的起点是查看它如何以30立方米为单位显示，但请记住，如果用户喜欢，可以增加或减少。</span><span class="sxs-lookup"><span data-stu-id="13488-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="13488-133">自己可以</span><span class="sxs-lookup"><span data-stu-id="13488-133">Own-able</span></span>

<span data-ttu-id="13488-134">应用启动器应感觉到某个人很高兴能够在他们的空间中使用。</span><span class="sxs-lookup"><span data-stu-id="13488-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="13488-135">它们几乎都是通过这些内容来处理的，因此启动器应喜欢用户认为是足以寻找并保留附近的内容。</span><span class="sxs-lookup"><span data-stu-id="13488-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="13488-136">![示例： Astro 扭曲3D 应用启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13488-137">*Astro)  (虚构应用程序启动器示例*</span><span class="sxs-lookup"><span data-stu-id="13488-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="13488-138">识别</span><span class="sxs-lookup"><span data-stu-id="13488-138">Recognizable</span></span>

<span data-ttu-id="13488-139">你的3D 应用程序启动器应立即将 "你的应用程序" 的品牌表达为看到它的人。</span><span class="sxs-lookup"><span data-stu-id="13488-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="13488-140">如果应用中有星形或特别可识别的对象，我们建议将其作为设计的一个很大的组成部分。</span><span class="sxs-lookup"><span data-stu-id="13488-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="13488-141">在混合现实世界中，对象对用户的兴趣比单独的徽标要多。</span><span class="sxs-lookup"><span data-stu-id="13488-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="13488-142">可识别对象快速、清晰地传达品牌。</span><span class="sxs-lookup"><span data-stu-id="13488-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="13488-143">容量耗尽</span><span class="sxs-lookup"><span data-stu-id="13488-143">Volumetric</span></span>

<span data-ttu-id="13488-144">您的应用程序只需将徽标置于平整平面上，并一整天就会调用它。</span><span class="sxs-lookup"><span data-stu-id="13488-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="13488-145">您的启动器应类似于用户空间中令人兴奋的、三维的物理对象。</span><span class="sxs-lookup"><span data-stu-id="13488-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="13488-146">一种很好的方法是假设您的应用程序将在 Macy 的感恩节日醒目中有一个气球。</span><span class="sxs-lookup"><span data-stu-id="13488-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="13488-147">问问自己，究竟是什么人在街道下出现了什么呢？</span><span class="sxs-lookup"><span data-stu-id="13488-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="13488-148">所有查看角度看起来都很好？</span><span class="sxs-lookup"><span data-stu-id="13488-148">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="13488-149">![仅徽标 ](images/20171016-140436-mixedreality-640px.jpg) *徽标*</span><span class="sxs-lookup"><span data-stu-id="13488-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13488-150">![更能识别字符更可识别的字符 ](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span><span class="sxs-lookup"><span data-stu-id="13488-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="13488-151">![平面方法，而不是令人吃惊的方式，而不是令人吃惊的简单 ](images/20171016-155101-mixedreality-640px.jpg) *方法*</span><span class="sxs-lookup"><span data-stu-id="13488-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13488-152">![容量耗尽方法更好地展示您的应用程序 ](images/20171016-161407-mixedreality-640px.jpg) *容量耗尽方法更好地展示您的应用程序*</span><span class="sxs-lookup"><span data-stu-id="13488-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="13488-153">适用于三维模型的提示</span><span class="sxs-lookup"><span data-stu-id="13488-153">Tips for good 3D models</span></span>

* <span data-ttu-id="13488-154">规划应用程序启动器的维度时，会针对大致的30cm 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="13488-154">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="13488-155">因此，1:1:1 大小的比率。</span><span class="sxs-lookup"><span data-stu-id="13488-155">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="13488-156">模型必须在10000多边形下。</span><span class="sxs-lookup"><span data-stu-id="13488-156">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="13488-157">详细了解 (LODs 的三角形计数和详细级别) </span><span class="sxs-lookup"><span data-stu-id="13488-157">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="13488-158">在沉浸式耳机上测试。</span><span class="sxs-lookup"><span data-stu-id="13488-158">Test on an immersive headset.</span></span>
* <span data-ttu-id="13488-159">在可能的情况下，将详细信息生成到模型的几何图形–不要依赖于纹理获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="13488-159">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="13488-160">生成 "水紧密型" 闭合几何。</span><span class="sxs-lookup"><span data-stu-id="13488-160">Build “water tight” closed geometry.</span></span> <span data-ttu-id="13488-161">没有在中建模的孔。</span><span class="sxs-lookup"><span data-stu-id="13488-161">No holes that are not modeled in.</span></span>
* <span data-ttu-id="13488-162">使用对象中的自然材料。</span><span class="sxs-lookup"><span data-stu-id="13488-162">Use natural materials in your object.</span></span> <span data-ttu-id="13488-163">想象一下在现实世界中手工制作。</span><span class="sxs-lookup"><span data-stu-id="13488-163">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="13488-164">请确保您的模型在不同的距离和大小上都能正常阅读。</span><span class="sxs-lookup"><span data-stu-id="13488-164">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="13488-165">模型准备就绪后，请阅读 [导出资产的准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="13488-165">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="13488-166">![纹理中包含微妙细节的模型](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-166">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13488-167">*纹理中包含微妙细节的模型*</span><span class="sxs-lookup"><span data-stu-id="13488-167">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="13488-168">要避免的内容</span><span class="sxs-lookup"><span data-stu-id="13488-168">What to avoid</span></span>

* <span data-ttu-id="13488-169">不要使用高对比度详细信息或较小、繁忙的模式和纹理。</span><span class="sxs-lookup"><span data-stu-id="13488-169">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="13488-170">不要使用精简几何-它在某种程度上并不能很好地工作，并且不会产生错误。</span><span class="sxs-lookup"><span data-stu-id="13488-170">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="13488-171">不要让模型的一部分扩展到超过1:1:1 大小的比率。</span><span class="sxs-lookup"><span data-stu-id="13488-171">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="13488-172">它将创建缩放问题。</span><span class="sxs-lookup"><span data-stu-id="13488-172">It will create scaling problems.</span></span>

<span data-ttu-id="13488-173">![避免高对比度、小型繁忙模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-173">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13488-174">*避免高对比度、小型、繁忙的模式*</span><span class="sxs-lookup"><span data-stu-id="13488-174">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="13488-175">如何处理类型</span><span class="sxs-lookup"><span data-stu-id="13488-175">How to handle type</span></span>

* <span data-ttu-id="13488-176">建议你的类型包含大约1/3 的应用启动器 (或多个) 。</span><span class="sxs-lookup"><span data-stu-id="13488-176">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="13488-177">类型主要是使用户了解你的启动程序，事实上，启动程序很好，因为它非常重要。</span><span class="sxs-lookup"><span data-stu-id="13488-177">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="13488-178">避免使类型成为超级类型-尝试将其放在应用程序启动器核心维度的范围内 (更多或更少) 。</span><span class="sxs-lookup"><span data-stu-id="13488-178">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="13488-179">平面类型可正常运行，但请注意，在某些角度和某些环境下，可能难以查看。</span><span class="sxs-lookup"><span data-stu-id="13488-179">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="13488-180">您可以考虑将它放在一个实体对象或背景上，以帮助解决此情况。</span><span class="sxs-lookup"><span data-stu-id="13488-180">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="13488-181">将维度添加到您的类型非常适合3D。</span><span class="sxs-lookup"><span data-stu-id="13488-181">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="13488-182">将类型的两侧的底纹着色为不同、更暗的颜色可帮助提高可读性。</span><span class="sxs-lookup"><span data-stu-id="13488-182">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="13488-183">![从特定角度看，无背景的平面类型很难查看，在某些环境中， ](images/flattype-640px.png) *不能从特定角度和某些环境中查看无背景的平面类型*</span><span class="sxs-lookup"><span data-stu-id="13488-183">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13488-184">![带有内置背景的类型可以正常工作 ](images/flattypeandbkg-640px.png) *，且内置背景可以正常工作*</span><span class="sxs-lookup"><span data-stu-id="13488-184">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13488-185">![如果 ](images/20171016-160221-mixedreality-640px.jpg) *对边进行着色*，则拉伸类型可以很好地工作</span><span class="sxs-lookup"><span data-stu-id="13488-185">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="13488-186">**键入工作的颜色**</span><span class="sxs-lookup"><span data-stu-id="13488-186">**Type colors that work**</span></span>

* <span data-ttu-id="13488-187">白色</span><span class="sxs-lookup"><span data-stu-id="13488-187">White</span></span>
* <span data-ttu-id="13488-188">黑色</span><span class="sxs-lookup"><span data-stu-id="13488-188">Black</span></span>
* <span data-ttu-id="13488-189">亮半饱和颜色</span><span class="sxs-lookup"><span data-stu-id="13488-189">Bright semi-saturated color</span></span>

<span data-ttu-id="13488-190">![键入工作的颜色。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-190">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13488-191">*键入工作的颜色*</span><span class="sxs-lookup"><span data-stu-id="13488-191">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="13488-192">要避免的颜色</span><span class="sxs-lookup"><span data-stu-id="13488-192">Colors to avoid</span></span>

<span data-ttu-id="13488-193">导致问题的类型可能包括：</span><span class="sxs-lookup"><span data-stu-id="13488-193">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="13488-194">中声</span><span class="sxs-lookup"><span data-stu-id="13488-194">Mid-tones</span></span>
* <span data-ttu-id="13488-195">灰色</span><span class="sxs-lookup"><span data-stu-id="13488-195">Gray</span></span>
* <span data-ttu-id="13488-196">过度饱和颜色或 desaturated 颜色</span><span class="sxs-lookup"><span data-stu-id="13488-196">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="13488-197">![键入导致问题的颜色。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-197">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="13488-198">*键入导致问题的颜色*</span><span class="sxs-lookup"><span data-stu-id="13488-198">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="13488-199">照明</span><span class="sxs-lookup"><span data-stu-id="13488-199">Lighting</span></span>

<span data-ttu-id="13488-200">应用启动器的照明来自 Cliff 房子环境。</span><span class="sxs-lookup"><span data-stu-id="13488-200">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="13488-201">请确保在整个房子内的多个位置测试启动器，使其看起来很好。</span><span class="sxs-lookup"><span data-stu-id="13488-201">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="13488-202">好消息是，如果您按照本文档中的其他设计指南进行了，则您的启动器应该非常适合 Cliff 房子中的大多数照明。</span><span class="sxs-lookup"><span data-stu-id="13488-202">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="13488-203">很好的地方就是测试启动器在环境中的各种灯光上的外观，就是工作室、Media 房间、后 Patio (具体区域以及草地) 。</span><span class="sxs-lookup"><span data-stu-id="13488-203">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="13488-204">另一种好的测试是将它放在半轻和半阴影上，并查看其外观。</span><span class="sxs-lookup"><span data-stu-id="13488-204">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="13488-205">![请确保启动器在灯光和阴影中都看起来很好。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13488-205">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="13488-206">*请确保启动程序在灯光和阴影中都看起来很好*</span><span class="sxs-lookup"><span data-stu-id="13488-206">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="13488-207">绘制</span><span class="sxs-lookup"><span data-stu-id="13488-207">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="13488-208">创作纹理</span><span class="sxs-lookup"><span data-stu-id="13488-208">Authoring your textures</span></span>

<span data-ttu-id="13488-209">三维应用启动器的结束格式将为 glb 文件，该文件使用 .PBR (以物理方式呈现) 管道。</span><span class="sxs-lookup"><span data-stu-id="13488-209">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="13488-210">这可能是一项棘手的过程-现在最好是使用技术音乐家（如果尚未这样做）。</span><span class="sxs-lookup"><span data-stu-id="13488-210">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="13488-211">如果你是无畏的 DIY，则在开始之前，请花时间 [研究并了解 .pbr 术语](https://wiki.polycount.com/wiki/PBR) ，在幕后，这将有助于你避免常见错误。</span><span class="sxs-lookup"><span data-stu-id="13488-211">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="13488-212">![示例：全新备注应用](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="13488-212">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="13488-213">*全新说明3D 应用启动器示例 (虚构应用)*</span><span class="sxs-lookup"><span data-stu-id="13488-213">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="13488-214">推荐的创作工具</span><span class="sxs-lookup"><span data-stu-id="13488-214">Recommended authoring tool</span></span>

<span data-ttu-id="13488-215">建议通过 Allegorithmic 使用 [材料刷](https://www.allegorithmic.com/products/substance-painter) 来创作最终文件。</span><span class="sxs-lookup"><span data-stu-id="13488-215">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="13488-216">如果你不熟悉在物质刷中创作 .PBR 着色器，请参阅以下 [教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。</span><span class="sxs-lookup"><span data-stu-id="13488-216">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="13488-217">如果你更熟悉其中的一个，则 (交替使用 [三维 Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 。 ) </span><span class="sxs-lookup"><span data-stu-id="13488-217">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="13488-218">最佳实践</span><span class="sxs-lookup"><span data-stu-id="13488-218">Best practices</span></span>

* <span data-ttu-id="13488-219">如果你的应用启动器对象是为 .PBR 编写的，则为 Cliff 房子环境转换该对象应该非常简单。</span><span class="sxs-lookup"><span data-stu-id="13488-219">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="13488-220">着色器应为金属/粗糙度工作流– Unreal .PBR 着色器是一个关闭的传真。</span><span class="sxs-lookup"><span data-stu-id="13488-220">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="13488-221">导出纹理时，请牢记 [建议的纹理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 。</span><span class="sxs-lookup"><span data-stu-id="13488-221">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="13488-222">请确保为实时照明生成对象，这意味着：</span><span class="sxs-lookup"><span data-stu-id="13488-222">Make sure to build your objects for real-time lighting — this means:</span></span>
  * <span data-ttu-id="13488-223">避免融入阴影-或绘制阴影</span><span class="sxs-lookup"><span data-stu-id="13488-223">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="13488-224">避免纹理中的融入光照</span><span class="sxs-lookup"><span data-stu-id="13488-224">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="13488-225">使用其中一个 .PBR 材料创作包获取为着色器生成的正确地图</span><span class="sxs-lookup"><span data-stu-id="13488-225">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="13488-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13488-226">See also</span></span>

* [<span data-ttu-id="13488-227">创建用于混合现实主页的3D 模型</span><span class="sxs-lookup"><span data-stu-id="13488-227">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="13488-228">实现 3D 应用启动器（UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="13488-228">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="13488-229">实现 3D 应用启动器（Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="13488-229">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
