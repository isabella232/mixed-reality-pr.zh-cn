---
title: 案例研究-在混合现实中创建 galaxy
description: 了解 "Galaxy 资源管理器" 应用程序，并了解它是如何为 Microsft HoloLens 构建的，以及如何通过社区开发人员进行的24小时 Twitter 轮询。
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 资源管理器，HoloLens，Windows Mixed Reality，分享你的想法，案例研究
ms.openlocfilehash: ef97920d22df65a9d4fa5e630840759e58c80b53
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583547"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="927fa-104">案例研究-在混合现实中创建 galaxy</span><span class="sxs-lookup"><span data-stu-id="927fa-104">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="927fa-105">在发布 Microsoft HoloLens 之前，我们会询问开发人员社区要为新设备查看有经验的内部团队构建的应用类型。</span><span class="sxs-lookup"><span data-stu-id="927fa-105">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="927fa-106">共享了5000多个想法，在24小时的 Twitter 投票后，入选方是一个称为 [Galaxy 资源管理器](../develop/unity/galaxy-explorer.md)的概念。</span><span class="sxs-lookup"><span data-stu-id="927fa-106">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](../develop/unity/galaxy-explorer.md).</span></span>

<span data-ttu-id="927fa-107">Zibits 是项目上的艺术线索，Karim Luccin，团队的图形工程师谈论的是在 "Galaxy 资源管理器" 中创建银河方法的精确、交互式表示形式的艺术与工程之间的协作工作。</span><span class="sxs-lookup"><span data-stu-id="927fa-107">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="927fa-108">技术人员</span><span class="sxs-lookup"><span data-stu-id="927fa-108">The Tech</span></span>

<span data-ttu-id="927fa-109">[我们的团队](../develop/unity/galaxy-explorer.md#meet-the-team) 组成了两个开发人员：三个开发人员、四个艺术家、一个制造者和一个测试人员-有六周时间来构建一个完全功能的应用程序，该应用程序允许用户了解并探索银河的 vastness 和美。</span><span class="sxs-lookup"><span data-stu-id="927fa-109">[Our team](../develop/unity/galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="927fa-110">我们想要充分利用 HoloLens 功能，以便在生活空间中直接呈现3D 对象，因此我们决定创建一个真实的 galaxy，用户可以在其中放大并查看单个星形，每个星都在各自的轨迹上。</span><span class="sxs-lookup"><span data-stu-id="927fa-110">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="927fa-111">在开发的第一周，我们提出了几个目标来实现银河的工作方式： Galaxy：它需要具有深度、移动和感觉容量耗尽，这将有助于创建 Galaxy 的形状。</span><span class="sxs-lookup"><span data-stu-id="927fa-111">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="927fa-112">创建具有数十亿星的动画 galaxy 的问题在于，每帧上需要更新的单个元素的数量可能会太大，而无法使用 CPU 进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="927fa-112">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="927fa-113">我们的解决方案涉及复杂的艺术和科学组合。</span><span class="sxs-lookup"><span data-stu-id="927fa-113">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="927fa-114">幕后</span><span class="sxs-lookup"><span data-stu-id="927fa-114">Behind the scenes</span></span>

<span data-ttu-id="927fa-115">为了让人们能够浏览各个星，我们的第一步是确定我们可以一次呈现多少粒子。</span><span class="sxs-lookup"><span data-stu-id="927fa-115">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="927fa-116">呈现粒子</span><span class="sxs-lookup"><span data-stu-id="927fa-116">Rendering particles</span></span>

<span data-ttu-id="927fa-117">当前 Cpu 非常适合用于处理串行任务，一次最多可执行几个并行任务 (具体取决于它们) 的核心数，但 Gpu 在并行处理上千个操作时更为有效。</span><span class="sxs-lookup"><span data-stu-id="927fa-117">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="927fa-118">不过，由于它们通常不与 CPU 共享同一内存，因此在 CPU<>GPU 之间交换数据可能会很快成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="927fa-118">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="927fa-119">我们的解决方案是将 galaxy 置于 GPU 上，并且它必须完全在 GPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="927fa-119">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="927fa-120">我们在各种模式中开始为成千上万点粒子进行压力测试。</span><span class="sxs-lookup"><span data-stu-id="927fa-120">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="927fa-121">这样，我们就可以在 HoloLens 上获得 galaxy，以查看工作情况和内容。</span><span class="sxs-lookup"><span data-stu-id="927fa-121">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="927fa-122">创建星形位置</span><span class="sxs-lookup"><span data-stu-id="927fa-122">Creating the position of the stars</span></span>

<span data-ttu-id="927fa-123">我们的一位团队成员已经编写了在其最初位置生成星形的 c # 代码。</span><span class="sxs-lookup"><span data-stu-id="927fa-123">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="927fa-124">星形位于一个椭圆上，并且其位置可通过 (**curveOffset**， **ellipseSize**， **仰角**) ，其中 **curveOffset** 是星形沿椭圆的角度， **ellipseSize** 是沿 X 和 Z 的椭圆的尺寸，在 galaxy 中提升星形的适当提升。</span><span class="sxs-lookup"><span data-stu-id="927fa-124">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="927fa-125">因此，我们可以创建一个缓冲区 ([Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) ，它将使用每个星型属性进行初始化，并将其发送到 GPU 上，以实现其他体验。</span><span class="sxs-lookup"><span data-stu-id="927fa-125">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="927fa-126">若要绘制此缓冲区，我们使用 [Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，它允许在) GPU 上的任意一组点上运行着色器 (代码，而无需使用表示 galaxy 的实际网格：</span><span class="sxs-lookup"><span data-stu-id="927fa-126">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="927fa-127">**CPU**</span><span class="sxs-lookup"><span data-stu-id="927fa-127">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="927fa-128">**GPU**</span><span class="sxs-lookup"><span data-stu-id="927fa-128">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="927fa-129">我们从具有数千个粒子的原始循环模式开始。</span><span class="sxs-lookup"><span data-stu-id="927fa-129">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="927fa-130">这为我们提供了我们所需的证明，我们可以管理许多粒子，并以高性能的速度运行</span><span class="sxs-lookup"><span data-stu-id="927fa-130">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="927fa-131">为了改进形状，我们尝试了各种模式和粒子系统进行旋转。</span><span class="sxs-lookup"><span data-stu-id="927fa-131">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="927fa-132">最初，这是因为粒子数和性能保持一致，但形状会在靠近中心处分解，而星形却发出表面，但这并不切合现实。</span><span class="sxs-lookup"><span data-stu-id="927fa-132">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="927fa-133">我们需要一个发射，使我们能够处理时间，并使粒子真实地移动，这种循环会更接近 galaxy 中心。</span><span class="sxs-lookup"><span data-stu-id="927fa-133">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我们尝试了多个旋转的模式和粒子系统，如下所示。](images/galaxy-patterns-500px.png)

<span data-ttu-id="927fa-135">我们尝试了多个旋转的模式和粒子系统，如下所示。</span><span class="sxs-lookup"><span data-stu-id="927fa-135">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="927fa-136">我们的团队对 galaxies 函数的方式进行了一些研究，我们为 galaxy 专门提供了一个自定义的粒子系统，以便我们可以基于 "[密度波理论](https://en.wikipedia.org/wiki/Density_wave_theory)" 移动省略号，这 theorizes 了 galaxy 的作用是密度较高的区域，如流量堵塞。</span><span class="sxs-lookup"><span data-stu-id="927fa-136">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="927fa-137">它看起来稳定稳定，但当星形沿着各自的椭圆移动时，它们实际上会移入和移出扶手。</span><span class="sxs-lookup"><span data-stu-id="927fa-137">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="927fa-138">在我们的系统中，粒子永远不会存在于 CPU 上-我们会生成卡并在 GPU 上调整它们的方向，因此整个系统只是初始状态和时间。</span><span class="sxs-lookup"><span data-stu-id="927fa-138">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="927fa-139">如下所示：</span><span class="sxs-lookup"><span data-stu-id="927fa-139">It progressed like this:</span></span>

![具有 GPU 呈现的粒子系统的进度](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="927fa-141">具有 GPU 呈现的粒子系统的进度</span><span class="sxs-lookup"><span data-stu-id="927fa-141">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="927fa-142">一旦添加了足够的省略号，并将其设置为旋转，galaxies 就会开始形成 "扶手"，其中星形的运动。</span><span class="sxs-lookup"><span data-stu-id="927fa-142">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="927fa-143">每个椭圆路径上的星形间距被赋予了一些随机性，并为每个星形增加了一个位置随机性。</span><span class="sxs-lookup"><span data-stu-id="927fa-143">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="927fa-144">这创建了一个更自然的星形运动和 arm 形状分布。</span><span class="sxs-lookup"><span data-stu-id="927fa-144">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="927fa-145">最后，我们添加了根据中心距离来驱动颜色的功能。</span><span class="sxs-lookup"><span data-stu-id="927fa-145">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="927fa-146">创建星形运动</span><span class="sxs-lookup"><span data-stu-id="927fa-146">Creating the motion of the stars</span></span>

<span data-ttu-id="927fa-147">若要对一般星形运动进行动画处理，需要为每个帧添加一个恒定角度，并使星形沿着其椭圆沿固定径向速度移动。</span><span class="sxs-lookup"><span data-stu-id="927fa-147">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="927fa-148">这是使用 **curveOffset** 的主要原因。</span><span class="sxs-lookup"><span data-stu-id="927fa-148">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="927fa-149">从技术上看，这并不正确，因为星形会沿着省略号的长边移动</span><span class="sxs-lookup"><span data-stu-id="927fa-149">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![在较长的弧线上，星形移动速度更快，但边缘速度更慢。](images/ellipse-movement.jpg)

<span data-ttu-id="927fa-151">在较长的弧线上，星形移动速度更快，但边缘速度更慢。</span><span class="sxs-lookup"><span data-stu-id="927fa-151">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="927fa-152">这样一来，就可以 (**curveOffset**、 **ellipseSize**、 **仰角**、 **age**) 对每个星形进行完全描述，其中 **age** 是自场景加载以来经过的总时间的累积。</span><span class="sxs-lookup"><span data-stu-id="927fa-152">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="927fa-153">这样一来，我们就可以在应用程序开始时生成数十个星，并沿着已建立的曲线对一组单的星形进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="927fa-153">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="927fa-154">由于所有内容都在 GPU 上，因此系统可以将所有的星形并行动态地动态显示给 CPU。</span><span class="sxs-lookup"><span data-stu-id="927fa-154">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![下面是绘制白色四边形时的样子。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="927fa-156">下面是绘制白色四边形时的样子。</span><span class="sxs-lookup"><span data-stu-id="927fa-156">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="927fa-157">为了使每个四颗面都为相机，我们使用几何着色器将每个星形位置转换为屏幕上将包含星形纹理的2D 矩形。</span><span class="sxs-lookup"><span data-stu-id="927fa-157">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![菱形而不是四边形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="927fa-159">菱形而不是四边形。</span><span class="sxs-lookup"><span data-stu-id="927fa-159">Diamonds instead of quads.</span></span>


<span data-ttu-id="927fa-160">由于我们要将过度绘制的) 处理次数限制 (，因此我们将四边形旋转，使其重叠越少。</span><span class="sxs-lookup"><span data-stu-id="927fa-160">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="927fa-161">添加云</span><span class="sxs-lookup"><span data-stu-id="927fa-161">Adding clouds</span></span>

<span data-ttu-id="927fa-162">有很多方法可让你从一个卷内的 ray marching 中获取容量耗尽的感受，以尽可能多地绘制粒子来模拟云。</span><span class="sxs-lookup"><span data-stu-id="927fa-162">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="927fa-163">实时 ray marching 的成本太高，因此很难创作，因此，我们首先尝试使用一种用于在游戏中呈现林的方法来构建冒名顶替系统，这种方法适用于照相机。</span><span class="sxs-lookup"><span data-stu-id="927fa-163">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="927fa-164">当我们在游戏中执行此操作时，我们可以从相机中呈现出一个旋转的树纹理，保存所有这些图像，并在每个布告栏上运行时，选择与视图方向匹配的图像。</span><span class="sxs-lookup"><span data-stu-id="927fa-164">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="927fa-165">如果图像是全息影像，这也不起作用。</span><span class="sxs-lookup"><span data-stu-id="927fa-165">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="927fa-166">左眼和合适的眼睛之间的区别在于，这使得我们需要更高的分辨率，否则它只是平面、化名或重复。</span><span class="sxs-lookup"><span data-stu-id="927fa-166">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="927fa-167">第二次尝试时，尝试尽可能多的粒子。</span><span class="sxs-lookup"><span data-stu-id="927fa-167">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="927fa-168">最佳视觉对象是在将微粒添加到场景之前，添加性地绘制粒子并模糊。</span><span class="sxs-lookup"><span data-stu-id="927fa-168">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="927fa-169">此方法的典型问题与我们可以同时绘制多少粒子相关，同时还会保持60fps 的屏幕区域。</span><span class="sxs-lookup"><span data-stu-id="927fa-169">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="927fa-170">模糊生成的映像，使此云感觉通常是一种非常昂贵的操作。</span><span class="sxs-lookup"><span data-stu-id="927fa-170">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![如果没有纹理，这就是云的外观，其中2% 不透明度。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="927fa-172">如果没有纹理，这就是云的外观，其中2% 不透明度。</span><span class="sxs-lookup"><span data-stu-id="927fa-172">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="927fa-173">如果是累加性的，其中有很多表示每个四边形有多个，则会对同一像素重复着色。</span><span class="sxs-lookup"><span data-stu-id="927fa-173">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="927fa-174">在 galaxy 的中心，相同的像素彼此之上有数百个四边形，在全屏显示时，这会产生巨大的成本。</span><span class="sxs-lookup"><span data-stu-id="927fa-174">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="927fa-175">执行全屏云并尝试对其进行模糊处理是一种不好的做法，因此，我们决定让硬件为我们完成工作。</span><span class="sxs-lookup"><span data-stu-id="927fa-175">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="927fa-176">首先是一个上下文</span><span class="sxs-lookup"><span data-stu-id="927fa-176">A bit of context first</span></span>

<span data-ttu-id="927fa-177">当在游戏中使用纹理时，纹理大小很少与我们要在中使用的区域匹配，但我们可以使用不同种类的纹理筛选来使图形卡从纹理 ([纹理筛选](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)) 的像素中插入所需的颜色。</span><span class="sxs-lookup"><span data-stu-id="927fa-177">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)).</span></span> <span data-ttu-id="927fa-178">对我们感兴趣的筛选是 [双线性筛选](/windows/win32/direct3d9/bilinear-texture-filtering) 器，它将使用最接近的邻居计算任何像素的值。</span><span class="sxs-lookup"><span data-stu-id="927fa-178">The filtering that interests us is [bilinear filtering](/windows/win32/direct3d9/bilinear-texture-filtering) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![筛选前的原始](images/texture-1.png)

![筛选后的结果](images/texture-2.png)

<span data-ttu-id="927fa-181">使用此属性，我们发现每次尝试将纹理绘制到一个区域的两倍时，它将使结果模糊。</span><span class="sxs-lookup"><span data-stu-id="927fa-181">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="927fa-182">我们可能会在其他内容上进行操作，而不是呈现为全屏，而是不会出现在屏幕上，而是呈现给屏幕的小版本。</span><span class="sxs-lookup"><span data-stu-id="927fa-182">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="927fa-183">然后，通过复制此纹理并按2次因子拉伸它，我们将返回全屏，同时模糊处理过程中的内容。</span><span class="sxs-lookup"><span data-stu-id="927fa-183">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 upscale 返回到完整解决方案。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="927fa-185">x3 upscale 返回到完整解决方案。</span><span class="sxs-lookup"><span data-stu-id="927fa-185">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="927fa-186">这样，我们就可以只使用一小部分原始成本来获取云部件。</span><span class="sxs-lookup"><span data-stu-id="927fa-186">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="927fa-187">我们只需绘制像素的 1/64th，而不是在完整的分辨率下添加云，只需将纹理拉伸回完整分辨率即可。</span><span class="sxs-lookup"><span data-stu-id="927fa-187">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Left，其中 upscale 从 1/8 到完全解析;右，使用2的幂2进行 3 upscale。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="927fa-189">Left，其中 upscale 从 1/8 到完全解析;右，使用2的幂2进行 3 upscale。</span><span class="sxs-lookup"><span data-stu-id="927fa-189">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="927fa-190">请注意，尝试从大小的 1/64th 到一次的全尺寸看上去完全不同，因为图形卡仍会在我们的设置中使用4个像素来向更大的区域着色，并使项目开始显示。</span><span class="sxs-lookup"><span data-stu-id="927fa-190">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="927fa-191">然后，如果我们添加具有较小卡片的完整分辨率，则会获得完整的 galaxy：</span><span class="sxs-lookup"><span data-stu-id="927fa-191">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![使用全分辨率星形的 galaxy 渲染接近最终结果](images/full-galaxy-500px.png)

<span data-ttu-id="927fa-193">完成形状的右跟踪后，我们添加了一层云，并将临时点换出到 Photoshop 中绘制的点，并添加了一些其他颜色。</span><span class="sxs-lookup"><span data-stu-id="927fa-193">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="927fa-194">结果就是一种银河的方法，Galaxy 我们的艺术和工程团队都认为是非常好的，并满足我们对 CPU 产生深刻的目标。</span><span class="sxs-lookup"><span data-stu-id="927fa-194">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![三维中的最终银河方法。](images/final-galaxy-500px.jpg)

<span data-ttu-id="927fa-196">三维中的最终银河方法。</span><span class="sxs-lookup"><span data-stu-id="927fa-196">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="927fa-197">了解更多</span><span class="sxs-lookup"><span data-stu-id="927fa-197">More to explore</span></span>

<span data-ttu-id="927fa-198">我们已经为 Galaxy 资源管理器应用程序提供了公开代码，并使其在 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 上可供开发人员使用。</span><span class="sxs-lookup"><span data-stu-id="927fa-198">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="927fa-199">想要了解有关 Galaxy 资源管理器开发过程的详细信息？</span><span class="sxs-lookup"><span data-stu-id="927fa-199">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="927fa-200">查看 [Microsoft HoloLens YouTube 频道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上的所有过去的项目更新。</span><span class="sxs-lookup"><span data-stu-id="927fa-200">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="927fa-201">关于作者</span><span class="sxs-lookup"><span data-stu-id="927fa-201">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="927fa-202"><b>Karim Luccin</b> 是一种软件工程师和别致的视觉对象爱好者。</span><span class="sxs-lookup"><span data-stu-id="927fa-202"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="927fa-203">他是用于 Galaxy 资源管理器的图形工程师。</span><span class="sxs-lookup"><span data-stu-id="927fa-203">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="927fa-204"><b>Zibits</b> 是一位艺术的线索和空间发烧，负责管理用于 Galaxy 资源管理器和孜孜以求的3d 建模团队，甚至更多粒子。</span><span class="sxs-lookup"><span data-stu-id="927fa-204"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="927fa-205">另请参阅</span><span class="sxs-lookup"><span data-stu-id="927fa-205">See also</span></span>
* [<span data-ttu-id="927fa-206">GitHub 上的 Galaxy 资源管理器</span><span class="sxs-lookup"><span data-stu-id="927fa-206">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="927fa-207">YouTube 上的 Galaxy 资源管理器项目更新</span><span class="sxs-lookup"><span data-stu-id="927fa-207">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)