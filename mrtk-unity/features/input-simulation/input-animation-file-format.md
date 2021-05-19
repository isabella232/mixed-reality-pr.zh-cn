---
title: 输入动画文件格式
description: MRTK 中有关输入动画二进制文件格式规范的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145119"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="9689f-104">输入动画二进制文件格式规范</span><span class="sxs-lookup"><span data-stu-id="9689f-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="9689f-105">整体结构</span><span class="sxs-lookup"><span data-stu-id="9689f-105">Overall structure</span></span>

<span data-ttu-id="9689f-106">输入动画二进制文件以64位整数幻数开头。</span><span class="sxs-lookup"><span data-stu-id="9689f-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="9689f-107">此数字在十六进制表示法中的值为 `0x6a8faf6e0f9e42c6` ，并且可用于标识有效的输入动画文件。</span><span class="sxs-lookup"><span data-stu-id="9689f-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="9689f-108">接下来的八个字节是声明文件的主版本号和次版本号的两个 Int32 值。</span><span class="sxs-lookup"><span data-stu-id="9689f-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="9689f-109">文件的其余部分由动画数据占用，动画数据在版本号之间可能会更改。</span><span class="sxs-lookup"><span data-stu-id="9689f-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="9689f-110">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-110">Section</span></span> | <span data-ttu-id="9689f-111">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-112">幻数</span><span class="sxs-lookup"><span data-stu-id="9689f-112">Magic Number</span></span> | <span data-ttu-id="9689f-113">Int64</span><span class="sxs-lookup"><span data-stu-id="9689f-113">Int64</span></span> |
| <span data-ttu-id="9689f-114">主要版本号</span><span class="sxs-lookup"><span data-stu-id="9689f-114">Major Version Number</span></span> | <span data-ttu-id="9689f-115">Int32</span><span class="sxs-lookup"><span data-stu-id="9689f-115">Int32</span></span> |
| <span data-ttu-id="9689f-116">次版本号</span><span class="sxs-lookup"><span data-stu-id="9689f-116">Minor Version Number</span></span> | <span data-ttu-id="9689f-117">Int32</span><span class="sxs-lookup"><span data-stu-id="9689f-117">Int32</span></span> |
| <span data-ttu-id="9689f-118">动画数据</span><span class="sxs-lookup"><span data-stu-id="9689f-118">Animation Data</span></span> | <span data-ttu-id="9689f-119">_请参阅版本部分_</span><span class="sxs-lookup"><span data-stu-id="9689f-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="9689f-120">版本 1.1</span><span class="sxs-lookup"><span data-stu-id="9689f-120">Version 1.1</span></span>

<span data-ttu-id="9689f-121">输入动画数据由三个布尔值组成，这些布尔值指示动画是否包含相机、手和眼睛数据，后跟一系列动画曲线。</span><span class="sxs-lookup"><span data-stu-id="9689f-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="9689f-122">曲线存在取决于这些布尔值的值。</span><span class="sxs-lookup"><span data-stu-id="9689f-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="9689f-123">每条曲线可以有不同数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="9689f-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="9689f-124">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-124">Section</span></span> | <span data-ttu-id="9689f-125">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-125">Type</span></span> | <span data-ttu-id="9689f-126">注释</span><span class="sxs-lookup"><span data-stu-id="9689f-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="9689f-127">具有照相机姿势</span><span class="sxs-lookup"><span data-stu-id="9689f-127">Has Camera Pose</span></span> | <span data-ttu-id="9689f-128">布尔</span><span class="sxs-lookup"><span data-stu-id="9689f-128">Boolean</span></span> | |
| <span data-ttu-id="9689f-129">具有手写数据</span><span class="sxs-lookup"><span data-stu-id="9689f-129">Has Hand Data</span></span> | <span data-ttu-id="9689f-130">布尔</span><span class="sxs-lookup"><span data-stu-id="9689f-130">Boolean</span></span> | |
| <span data-ttu-id="9689f-131">有眼睛</span><span class="sxs-lookup"><span data-stu-id="9689f-131">Has Eye Gaze</span></span>| <span data-ttu-id="9689f-132">布尔</span><span class="sxs-lookup"><span data-stu-id="9689f-132">Boolean</span></span> | |
| <span data-ttu-id="9689f-133">照相机</span><span class="sxs-lookup"><span data-stu-id="9689f-133">Camera</span></span> | [<span data-ttu-id="9689f-134">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="9689f-135">仅当具有照相机姿势时</span><span class="sxs-lookup"><span data-stu-id="9689f-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="9689f-136">手动跟踪左侧</span><span class="sxs-lookup"><span data-stu-id="9689f-136">Hand Tracked Left</span></span> | [<span data-ttu-id="9689f-137">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9689f-138">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-139">手部跟踪右侧</span><span class="sxs-lookup"><span data-stu-id="9689f-139">Hand Tracked Right</span></span> | [<span data-ttu-id="9689f-140">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9689f-141">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-142">向左收缩手部</span><span class="sxs-lookup"><span data-stu-id="9689f-142">Hand Pinching Left</span></span> | [<span data-ttu-id="9689f-143">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9689f-144">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-145">右手收缩</span><span class="sxs-lookup"><span data-stu-id="9689f-145">Hand Pinching Right</span></span> | [<span data-ttu-id="9689f-146">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="9689f-147">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-148">左手部</span><span class="sxs-lookup"><span data-stu-id="9689f-148">Hand Joints Left</span></span> | [<span data-ttu-id="9689f-149">联合姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="9689f-150">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-151">手部右侧</span><span class="sxs-lookup"><span data-stu-id="9689f-151">Hand Joints Right</span></span> | [<span data-ttu-id="9689f-152">联合姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="9689f-153">仅在"具有手部数据"为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="9689f-154">眼睛凝视</span><span class="sxs-lookup"><span data-stu-id="9689f-154">Eye Gaze</span></span> | <span data-ttu-id="9689f-155">[光线曲线](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="9689f-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="9689f-156">仅当有眼睛为 true 时</span><span class="sxs-lookup"><span data-stu-id="9689f-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="9689f-157">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="9689f-157">Version 1.0</span></span>

<span data-ttu-id="9689f-158">输入动画数据由一系列动画曲线组成。</span><span class="sxs-lookup"><span data-stu-id="9689f-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="9689f-159">动画曲线的数量和含义是固定的，但是每条曲线可以有不同数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="9689f-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="9689f-160">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-160">Section</span></span> | <span data-ttu-id="9689f-161">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-162">照相机</span><span class="sxs-lookup"><span data-stu-id="9689f-162">Camera</span></span> | [<span data-ttu-id="9689f-163">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-164">手动跟踪</span><span class="sxs-lookup"><span data-stu-id="9689f-164">Hand Tracked Left</span></span> | [<span data-ttu-id="9689f-165">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9689f-166">手动跟踪权限</span><span class="sxs-lookup"><span data-stu-id="9689f-166">Hand Tracked Right</span></span> | [<span data-ttu-id="9689f-167">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9689f-168">左收缩</span><span class="sxs-lookup"><span data-stu-id="9689f-168">Hand Pinching Left</span></span> | [<span data-ttu-id="9689f-169">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9689f-170">手动收缩权限</span><span class="sxs-lookup"><span data-stu-id="9689f-170">Hand Pinching Right</span></span> | [<span data-ttu-id="9689f-171">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="9689f-172">手动接头靠左</span><span class="sxs-lookup"><span data-stu-id="9689f-172">Hand Joints Left</span></span> | [<span data-ttu-id="9689f-173">接合曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="9689f-174">右侧接头</span><span class="sxs-lookup"><span data-stu-id="9689f-174">Hand Joints Right</span></span> | [<span data-ttu-id="9689f-175">接合曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="9689f-176">接合曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-176">Joint pose curves</span></span>

<span data-ttu-id="9689f-177">每个局都存储一系列接点动画曲线。</span><span class="sxs-lookup"><span data-stu-id="9689f-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="9689f-178">联接的数目是固定的，为每个接合存储一组姿势曲线。</span><span class="sxs-lookup"><span data-stu-id="9689f-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="9689f-179">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-179">Section</span></span> | <span data-ttu-id="9689f-180">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-181">无</span><span class="sxs-lookup"><span data-stu-id="9689f-181">None</span></span> | [<span data-ttu-id="9689f-182">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-183">手腕</span><span class="sxs-lookup"><span data-stu-id="9689f-183">Wrist</span></span> | [<span data-ttu-id="9689f-184">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-185">Palm</span><span class="sxs-lookup"><span data-stu-id="9689f-185">Palm</span></span> | [<span data-ttu-id="9689f-186">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="9689f-188">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="9689f-190">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="9689f-192">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="9689f-193">ThumbTip</span></span> | [<span data-ttu-id="9689f-194">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9689f-195">IndexMetacarpal</span></span> | [<span data-ttu-id="9689f-196">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="9689f-197">IndexKnuckle</span></span> | [<span data-ttu-id="9689f-198">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="9689f-200">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-201">IndexDistalJoint</span></span> | [<span data-ttu-id="9689f-202">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-203">索引提示</span><span class="sxs-lookup"><span data-stu-id="9689f-203">IndexTip</span></span> | [<span data-ttu-id="9689f-204">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9689f-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="9689f-206">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="9689f-207">MiddleKnuckle</span></span> | [<span data-ttu-id="9689f-208">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="9689f-210">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="9689f-212">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="9689f-213">MiddleTip</span></span> | [<span data-ttu-id="9689f-214">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9689f-215">RingMetacarpal</span></span> | [<span data-ttu-id="9689f-216">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="9689f-217">RingKnuckle</span></span> | [<span data-ttu-id="9689f-218">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-219">RingMiddleJoint</span></span> | [<span data-ttu-id="9689f-220">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-221">RingDistalJoint</span></span> | [<span data-ttu-id="9689f-222">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="9689f-223">RingTip</span></span> | [<span data-ttu-id="9689f-224">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="9689f-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="9689f-226">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-227">UckyKnuckle</span><span class="sxs-lookup"><span data-stu-id="9689f-227">PinkyKnuckle</span></span> | [<span data-ttu-id="9689f-228">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="9689f-230">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="9689f-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="9689f-232">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="9689f-233">浅色提示</span><span class="sxs-lookup"><span data-stu-id="9689f-233">PinkyTip</span></span> | [<span data-ttu-id="9689f-234">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="9689f-235">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-235">Pose curves</span></span>

<span data-ttu-id="9689f-236">姿势曲线是位置向量的 3 条动画曲线序列，后跟 4 条旋转四元数的动画曲线。</span><span class="sxs-lookup"><span data-stu-id="9689f-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="9689f-237">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-237">Section</span></span> | <span data-ttu-id="9689f-238">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-239">位置 X</span><span class="sxs-lookup"><span data-stu-id="9689f-239">Position X</span></span> | [<span data-ttu-id="9689f-240">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-241">位置 Y</span><span class="sxs-lookup"><span data-stu-id="9689f-241">Position Y</span></span> | [<span data-ttu-id="9689f-242">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-243">位置 Z</span><span class="sxs-lookup"><span data-stu-id="9689f-243">Position Z</span></span> | [<span data-ttu-id="9689f-244">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-245">旋转 X</span><span class="sxs-lookup"><span data-stu-id="9689f-245">Rotation X</span></span> | [<span data-ttu-id="9689f-246">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-247">旋转 Y</span><span class="sxs-lookup"><span data-stu-id="9689f-247">Rotation Y</span></span> | [<span data-ttu-id="9689f-248">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-249">旋转 Z</span><span class="sxs-lookup"><span data-stu-id="9689f-249">Rotation Z</span></span> | [<span data-ttu-id="9689f-250">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-251">旋转 W</span><span class="sxs-lookup"><span data-stu-id="9689f-251">Rotation W</span></span> | [<span data-ttu-id="9689f-252">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="9689f-253">射线曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-253">Ray curves</span></span>

<span data-ttu-id="9689f-254">Ray 曲线是原点向量的3个动画曲线的序列，后跟方向向量的3个动画曲线。</span><span class="sxs-lookup"><span data-stu-id="9689f-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="9689f-255">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-255">Section</span></span> | <span data-ttu-id="9689f-256">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-257">原点 X</span><span class="sxs-lookup"><span data-stu-id="9689f-257">Origin X</span></span> | [<span data-ttu-id="9689f-258">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-259">源 Y</span><span class="sxs-lookup"><span data-stu-id="9689f-259">Origin Y</span></span> | [<span data-ttu-id="9689f-260">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-261">原点 Z</span><span class="sxs-lookup"><span data-stu-id="9689f-261">Origin Z</span></span> | [<span data-ttu-id="9689f-262">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-263">方向 X</span><span class="sxs-lookup"><span data-stu-id="9689f-263">Direction X</span></span> | [<span data-ttu-id="9689f-264">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-265">方向 Y</span><span class="sxs-lookup"><span data-stu-id="9689f-265">Direction Y</span></span> | [<span data-ttu-id="9689f-266">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="9689f-267">Z 方向</span><span class="sxs-lookup"><span data-stu-id="9689f-267">Direction Z</span></span> | [<span data-ttu-id="9689f-268">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="9689f-269">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-269">Float curve</span></span>

<span data-ttu-id="9689f-270">浮点曲线是完全成熟的 Bézier 曲线，具有可变数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="9689f-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="9689f-271">每个关键帧都存储时间和曲线值，以及每个关键帧左侧和右侧之间的切线和权重。</span><span class="sxs-lookup"><span data-stu-id="9689f-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="9689f-272">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-272">Section</span></span> | <span data-ttu-id="9689f-273">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-274">预包装模式</span><span class="sxs-lookup"><span data-stu-id="9689f-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="9689f-275">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9689f-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9689f-276">后包装模式</span><span class="sxs-lookup"><span data-stu-id="9689f-276">Post-Wrap Mode</span></span> | <span data-ttu-id="9689f-277">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9689f-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9689f-278">关键帧数</span><span class="sxs-lookup"><span data-stu-id="9689f-278">Number of keyframes</span></span> | <span data-ttu-id="9689f-279">Int32</span><span class="sxs-lookup"><span data-stu-id="9689f-279">Int32</span></span> |
| <span data-ttu-id="9689f-280">关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-280">Keyframes</span></span> | [<span data-ttu-id="9689f-281">Float 关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="9689f-282">Float 关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-282">Float keyframe</span></span>

<span data-ttu-id="9689f-283">float 关键帧将切值和权重值与基本时间和值一起存储。</span><span class="sxs-lookup"><span data-stu-id="9689f-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="9689f-284">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-284">Section</span></span> | <span data-ttu-id="9689f-285">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-286">时间</span><span class="sxs-lookup"><span data-stu-id="9689f-286">Time</span></span> | <span data-ttu-id="9689f-287">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-287">Float32</span></span> |
| <span data-ttu-id="9689f-288">Value</span><span class="sxs-lookup"><span data-stu-id="9689f-288">Value</span></span> | <span data-ttu-id="9689f-289">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-289">Float32</span></span> |
| <span data-ttu-id="9689f-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="9689f-290">InTangent</span></span> | <span data-ttu-id="9689f-291">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-291">Float32</span></span> |
| <span data-ttu-id="9689f-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="9689f-292">OutTangent</span></span> | <span data-ttu-id="9689f-293">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-293">Float32</span></span> |
| <span data-ttu-id="9689f-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="9689f-294">InWeight</span></span> | <span data-ttu-id="9689f-295">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-295">Float32</span></span> |
| <span data-ttu-id="9689f-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="9689f-296">OutWeight</span></span> | <span data-ttu-id="9689f-297">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-297">Float32</span></span> |
| <span data-ttu-id="9689f-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="9689f-298">WeightedMode</span></span> | <span data-ttu-id="9689f-299">Int32， [加权模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="9689f-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="9689f-300">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="9689f-300">Boolean curve</span></span>

<span data-ttu-id="9689f-301">布尔曲线是开/关值的简单序列。</span><span class="sxs-lookup"><span data-stu-id="9689f-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="9689f-302">在每个关键帧上，曲线的值会立即反转。</span><span class="sxs-lookup"><span data-stu-id="9689f-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="9689f-303">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-303">Section</span></span> | <span data-ttu-id="9689f-304">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-305">预包装模式</span><span class="sxs-lookup"><span data-stu-id="9689f-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="9689f-306">Int32， [环绕模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9689f-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9689f-307">包装后模式</span><span class="sxs-lookup"><span data-stu-id="9689f-307">Post-Wrap Mode</span></span> | <span data-ttu-id="9689f-308">Int32， [环绕模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="9689f-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="9689f-309">关键帧数量</span><span class="sxs-lookup"><span data-stu-id="9689f-309">Number of keyframes</span></span> | <span data-ttu-id="9689f-310">Int32</span><span class="sxs-lookup"><span data-stu-id="9689f-310">Int32</span></span> |
| <span data-ttu-id="9689f-311">关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-311">Keyframes</span></span> | [<span data-ttu-id="9689f-312">布尔关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="9689f-313">布尔关键帧</span><span class="sxs-lookup"><span data-stu-id="9689f-313">Boolean keyframe</span></span>

<span data-ttu-id="9689f-314">布尔关键帧仅存储时间和值。</span><span class="sxs-lookup"><span data-stu-id="9689f-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="9689f-315">部分</span><span class="sxs-lookup"><span data-stu-id="9689f-315">Section</span></span> | <span data-ttu-id="9689f-316">类型</span><span class="sxs-lookup"><span data-stu-id="9689f-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="9689f-317">时间</span><span class="sxs-lookup"><span data-stu-id="9689f-317">Time</span></span> | <span data-ttu-id="9689f-318">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-318">Float32</span></span> |
| <span data-ttu-id="9689f-319">Value</span><span class="sxs-lookup"><span data-stu-id="9689f-319">Value</span></span> | <span data-ttu-id="9689f-320">Float32</span><span class="sxs-lookup"><span data-stu-id="9689f-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="9689f-321">环绕模式</span><span class="sxs-lookup"><span data-stu-id="9689f-321">Wrap mode</span></span>

<span data-ttu-id="9689f-322">前后换行模式的语义遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定义。</span><span class="sxs-lookup"><span data-stu-id="9689f-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="9689f-323">它们是以下位的组合：</span><span class="sxs-lookup"><span data-stu-id="9689f-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="9689f-324">Value</span><span class="sxs-lookup"><span data-stu-id="9689f-324">Value</span></span> | <span data-ttu-id="9689f-325">含义</span><span class="sxs-lookup"><span data-stu-id="9689f-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="9689f-326">0</span><span class="sxs-lookup"><span data-stu-id="9689f-326">0</span></span> | <span data-ttu-id="9689f-327">默认值：读取设置较高的默认重复模式。</span><span class="sxs-lookup"><span data-stu-id="9689f-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="9689f-328">1</span><span class="sxs-lookup"><span data-stu-id="9689f-328">1</span></span> | <span data-ttu-id="9689f-329">一次：当时间到达动画剪辑的末尾时，剪辑会自动停止播放，时间将重置为剪辑的开始位置。</span><span class="sxs-lookup"><span data-stu-id="9689f-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="9689f-330">2</span><span class="sxs-lookup"><span data-stu-id="9689f-330">2</span></span> | <span data-ttu-id="9689f-331">循环：当时间到达动画剪辑的末尾时，将在开始时继续进行。</span><span class="sxs-lookup"><span data-stu-id="9689f-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="9689f-332">4</span><span class="sxs-lookup"><span data-stu-id="9689f-332">4</span></span> | <span data-ttu-id="9689f-333">PingPong：当时间到达动画剪辑的末尾时，将在开始和结束之间 ping 回来。</span><span class="sxs-lookup"><span data-stu-id="9689f-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="9689f-334">8</span><span class="sxs-lookup"><span data-stu-id="9689f-334">8</span></span> | <span data-ttu-id="9689f-335">ClampForever：播放动画。</span><span class="sxs-lookup"><span data-stu-id="9689f-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="9689f-336">当它到达末尾时，它将一直播放最后一帧，而永远不会停止播放。</span><span class="sxs-lookup"><span data-stu-id="9689f-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="9689f-337">加权模式</span><span class="sxs-lookup"><span data-stu-id="9689f-337">Weighted mode</span></span>

<span data-ttu-id="9689f-338">加权模式的语义遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定义。</span><span class="sxs-lookup"><span data-stu-id="9689f-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="9689f-339">Value</span><span class="sxs-lookup"><span data-stu-id="9689f-339">Value</span></span> | <span data-ttu-id="9689f-340">含义</span><span class="sxs-lookup"><span data-stu-id="9689f-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="9689f-341">0</span><span class="sxs-lookup"><span data-stu-id="9689f-341">0</span></span> | <span data-ttu-id="9689f-342">无：计算曲线段时，排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="9689f-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="9689f-343">1</span><span class="sxs-lookup"><span data-stu-id="9689f-343">1</span></span> | <span data-ttu-id="9689f-344">In：计算上一条曲线段时包括 inWeight。</span><span class="sxs-lookup"><span data-stu-id="9689f-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="9689f-345">2</span><span class="sxs-lookup"><span data-stu-id="9689f-345">2</span></span> | <span data-ttu-id="9689f-346">Out：计算下一个曲线段时包括 outWeight。</span><span class="sxs-lookup"><span data-stu-id="9689f-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="9689f-347">3</span><span class="sxs-lookup"><span data-stu-id="9689f-347">3</span></span> | <span data-ttu-id="9689f-348">两者：计算曲线段时包括 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="9689f-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
