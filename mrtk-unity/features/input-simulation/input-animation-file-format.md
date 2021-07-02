---
title: 输入动画文件格式
description: MRTK 中有关输入动画二进制文件格式规范的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 400212d80833f5d8dfbb3c5265c755ed2e127131
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177007"
---
# <a name="input-animation-file-format"></a><span data-ttu-id="97a80-104">输入动画文件格式</span><span class="sxs-lookup"><span data-stu-id="97a80-104">Input animation file format</span></span>

## <a name="overall-structure"></a><span data-ttu-id="97a80-105">整体结构</span><span class="sxs-lookup"><span data-stu-id="97a80-105">Overall structure</span></span>

<span data-ttu-id="97a80-106">输入动画二进制文件以64位整数幻数开头。</span><span class="sxs-lookup"><span data-stu-id="97a80-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="97a80-107">此数字在十六进制表示法中的值为 `0x6a8faf6e0f9e42c6` ，并且可用于标识有效的输入动画文件。</span><span class="sxs-lookup"><span data-stu-id="97a80-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="97a80-108">接下来的八个字节是声明文件的主版本号和次版本号的两个 Int32 值。</span><span class="sxs-lookup"><span data-stu-id="97a80-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="97a80-109">文件的其余部分由动画数据占用，动画数据在版本号之间可能会更改。</span><span class="sxs-lookup"><span data-stu-id="97a80-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="97a80-110">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-110">Section</span></span> | <span data-ttu-id="97a80-111">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-112">幻数</span><span class="sxs-lookup"><span data-stu-id="97a80-112">Magic Number</span></span> | <span data-ttu-id="97a80-113">Int64</span><span class="sxs-lookup"><span data-stu-id="97a80-113">Int64</span></span> |
| <span data-ttu-id="97a80-114">主要版本号</span><span class="sxs-lookup"><span data-stu-id="97a80-114">Major Version Number</span></span> | <span data-ttu-id="97a80-115">Int32</span><span class="sxs-lookup"><span data-stu-id="97a80-115">Int32</span></span> |
| <span data-ttu-id="97a80-116">次版本号</span><span class="sxs-lookup"><span data-stu-id="97a80-116">Minor Version Number</span></span> | <span data-ttu-id="97a80-117">Int32</span><span class="sxs-lookup"><span data-stu-id="97a80-117">Int32</span></span> |
| <span data-ttu-id="97a80-118">动画数据</span><span class="sxs-lookup"><span data-stu-id="97a80-118">Animation Data</span></span> | <span data-ttu-id="97a80-119">_请参阅版本部分_</span><span class="sxs-lookup"><span data-stu-id="97a80-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="97a80-120">版本 1.1</span><span class="sxs-lookup"><span data-stu-id="97a80-120">Version 1.1</span></span>

<span data-ttu-id="97a80-121">输入动画数据由三个布尔值组成，这些布尔值指示动画是否包含相机、手和眼睛数据，后跟一系列动画曲线。</span><span class="sxs-lookup"><span data-stu-id="97a80-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="97a80-122">曲线存在取决于这些布尔值的值。</span><span class="sxs-lookup"><span data-stu-id="97a80-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="97a80-123">每条曲线可以有不同数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="97a80-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="97a80-124">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-124">Section</span></span> | <span data-ttu-id="97a80-125">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-125">Type</span></span> | <span data-ttu-id="97a80-126">说明</span><span class="sxs-lookup"><span data-stu-id="97a80-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="97a80-127">具有照相机姿势</span><span class="sxs-lookup"><span data-stu-id="97a80-127">Has Camera Pose</span></span> | <span data-ttu-id="97a80-128">布尔</span><span class="sxs-lookup"><span data-stu-id="97a80-128">Boolean</span></span> | |
| <span data-ttu-id="97a80-129">具有手写数据</span><span class="sxs-lookup"><span data-stu-id="97a80-129">Has Hand Data</span></span> | <span data-ttu-id="97a80-130">布尔</span><span class="sxs-lookup"><span data-stu-id="97a80-130">Boolean</span></span> | |
| <span data-ttu-id="97a80-131">有眼睛</span><span class="sxs-lookup"><span data-stu-id="97a80-131">Has Eye Gaze</span></span>| <span data-ttu-id="97a80-132">布尔</span><span class="sxs-lookup"><span data-stu-id="97a80-132">Boolean</span></span> | |
| <span data-ttu-id="97a80-133">照相机</span><span class="sxs-lookup"><span data-stu-id="97a80-133">Camera</span></span> | [<span data-ttu-id="97a80-134">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="97a80-135">仅当具有照相机姿势时</span><span class="sxs-lookup"><span data-stu-id="97a80-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="97a80-136">手动跟踪</span><span class="sxs-lookup"><span data-stu-id="97a80-136">Hand Tracked Left</span></span> | [<span data-ttu-id="97a80-137">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="97a80-138">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-139">手动跟踪权限</span><span class="sxs-lookup"><span data-stu-id="97a80-139">Hand Tracked Right</span></span> | [<span data-ttu-id="97a80-140">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="97a80-141">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-142">左收缩</span><span class="sxs-lookup"><span data-stu-id="97a80-142">Hand Pinching Left</span></span> | [<span data-ttu-id="97a80-143">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="97a80-144">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-145">手动收缩权限</span><span class="sxs-lookup"><span data-stu-id="97a80-145">Hand Pinching Right</span></span> | [<span data-ttu-id="97a80-146">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="97a80-147">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-148">手动接头靠左</span><span class="sxs-lookup"><span data-stu-id="97a80-148">Hand Joints Left</span></span> | [<span data-ttu-id="97a80-149">接合曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="97a80-150">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-151">右侧接头</span><span class="sxs-lookup"><span data-stu-id="97a80-151">Hand Joints Right</span></span> | [<span data-ttu-id="97a80-152">接合曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="97a80-153">仅当有手写数据为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="97a80-154">眼睛</span><span class="sxs-lookup"><span data-stu-id="97a80-154">Eye Gaze</span></span> | <span data-ttu-id="97a80-155">[射线曲线](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="97a80-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="97a80-156">仅当有眼睛为 true 时</span><span class="sxs-lookup"><span data-stu-id="97a80-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="97a80-157">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="97a80-157">Version 1.0</span></span>

<span data-ttu-id="97a80-158">输入动画数据由一系列动画曲线组成。</span><span class="sxs-lookup"><span data-stu-id="97a80-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="97a80-159">动画曲线的数量和含义是固定的，但是每条曲线可以有不同数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="97a80-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="97a80-160">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-160">Section</span></span> | <span data-ttu-id="97a80-161">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-162">照相机</span><span class="sxs-lookup"><span data-stu-id="97a80-162">Camera</span></span> | [<span data-ttu-id="97a80-163">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-164">手动跟踪</span><span class="sxs-lookup"><span data-stu-id="97a80-164">Hand Tracked Left</span></span> | [<span data-ttu-id="97a80-165">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="97a80-166">手动跟踪权限</span><span class="sxs-lookup"><span data-stu-id="97a80-166">Hand Tracked Right</span></span> | [<span data-ttu-id="97a80-167">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="97a80-168">左收缩</span><span class="sxs-lookup"><span data-stu-id="97a80-168">Hand Pinching Left</span></span> | [<span data-ttu-id="97a80-169">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="97a80-170">手动收缩权限</span><span class="sxs-lookup"><span data-stu-id="97a80-170">Hand Pinching Right</span></span> | [<span data-ttu-id="97a80-171">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="97a80-172">手动接头靠左</span><span class="sxs-lookup"><span data-stu-id="97a80-172">Hand Joints Left</span></span> | [<span data-ttu-id="97a80-173">接合曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="97a80-174">右侧接头</span><span class="sxs-lookup"><span data-stu-id="97a80-174">Hand Joints Right</span></span> | [<span data-ttu-id="97a80-175">接合曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="97a80-176">接合曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-176">Joint pose curves</span></span>

<span data-ttu-id="97a80-177">每个局都存储一系列接点动画曲线。</span><span class="sxs-lookup"><span data-stu-id="97a80-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="97a80-178">联接的数目是固定的，为每个接合存储一组姿势曲线。</span><span class="sxs-lookup"><span data-stu-id="97a80-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="97a80-179">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-179">Section</span></span> | <span data-ttu-id="97a80-180">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-181">无</span><span class="sxs-lookup"><span data-stu-id="97a80-181">None</span></span> | [<span data-ttu-id="97a80-182">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-183">手腕</span><span class="sxs-lookup"><span data-stu-id="97a80-183">Wrist</span></span> | [<span data-ttu-id="97a80-184">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-185">Palm</span><span class="sxs-lookup"><span data-stu-id="97a80-185">Palm</span></span> | [<span data-ttu-id="97a80-186">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="97a80-188">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="97a80-190">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="97a80-192">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="97a80-193">ThumbTip</span></span> | [<span data-ttu-id="97a80-194">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="97a80-195">IndexMetacarpal</span></span> | [<span data-ttu-id="97a80-196">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="97a80-197">IndexKnuckle</span></span> | [<span data-ttu-id="97a80-198">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="97a80-200">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-201">IndexDistalJoint</span></span> | [<span data-ttu-id="97a80-202">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-203">索引提示</span><span class="sxs-lookup"><span data-stu-id="97a80-203">IndexTip</span></span> | [<span data-ttu-id="97a80-204">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="97a80-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="97a80-206">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="97a80-207">MiddleKnuckle</span></span> | [<span data-ttu-id="97a80-208">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="97a80-210">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="97a80-212">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-213">中间提示</span><span class="sxs-lookup"><span data-stu-id="97a80-213">MiddleTip</span></span> | [<span data-ttu-id="97a80-214">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="97a80-215">RingMetacarpal</span></span> | [<span data-ttu-id="97a80-216">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="97a80-217">RingKnuckle</span></span> | [<span data-ttu-id="97a80-218">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-219">RingMiddleJoint</span></span> | [<span data-ttu-id="97a80-220">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-221">RingDistalJoint</span></span> | [<span data-ttu-id="97a80-222">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-223">环提示</span><span class="sxs-lookup"><span data-stu-id="97a80-223">RingTip</span></span> | [<span data-ttu-id="97a80-224">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="97a80-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="97a80-226">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-227">UckyKnuckle</span><span class="sxs-lookup"><span data-stu-id="97a80-227">PinkyKnuckle</span></span> | [<span data-ttu-id="97a80-228">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="97a80-230">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="97a80-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="97a80-232">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="97a80-233">浅色提示</span><span class="sxs-lookup"><span data-stu-id="97a80-233">PinkyTip</span></span> | [<span data-ttu-id="97a80-234">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="97a80-235">姿势曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-235">Pose curves</span></span>

<span data-ttu-id="97a80-236">姿势曲线是位置向量的 3 条动画曲线序列，后跟 4 条旋转四元数的动画曲线。</span><span class="sxs-lookup"><span data-stu-id="97a80-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="97a80-237">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-237">Section</span></span> | <span data-ttu-id="97a80-238">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-239">位置 X</span><span class="sxs-lookup"><span data-stu-id="97a80-239">Position X</span></span> | [<span data-ttu-id="97a80-240">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-241">位置 Y</span><span class="sxs-lookup"><span data-stu-id="97a80-241">Position Y</span></span> | [<span data-ttu-id="97a80-242">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-243">位置 Z</span><span class="sxs-lookup"><span data-stu-id="97a80-243">Position Z</span></span> | [<span data-ttu-id="97a80-244">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-245">旋转 X</span><span class="sxs-lookup"><span data-stu-id="97a80-245">Rotation X</span></span> | [<span data-ttu-id="97a80-246">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-247">旋转 Y</span><span class="sxs-lookup"><span data-stu-id="97a80-247">Rotation Y</span></span> | [<span data-ttu-id="97a80-248">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-249">旋转 Z</span><span class="sxs-lookup"><span data-stu-id="97a80-249">Rotation Z</span></span> | [<span data-ttu-id="97a80-250">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-251">旋转 W</span><span class="sxs-lookup"><span data-stu-id="97a80-251">Rotation W</span></span> | [<span data-ttu-id="97a80-252">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="97a80-253">光线曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-253">Ray curves</span></span>

<span data-ttu-id="97a80-254">射线曲线是原向量的 3 条动画曲线序列，后跟方向向量的 3 条动画曲线。</span><span class="sxs-lookup"><span data-stu-id="97a80-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="97a80-255">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-255">Section</span></span> | <span data-ttu-id="97a80-256">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-257">源 X</span><span class="sxs-lookup"><span data-stu-id="97a80-257">Origin X</span></span> | [<span data-ttu-id="97a80-258">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-259">源 Y</span><span class="sxs-lookup"><span data-stu-id="97a80-259">Origin Y</span></span> | [<span data-ttu-id="97a80-260">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-261">源 Z</span><span class="sxs-lookup"><span data-stu-id="97a80-261">Origin Z</span></span> | [<span data-ttu-id="97a80-262">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-263">方向 X</span><span class="sxs-lookup"><span data-stu-id="97a80-263">Direction X</span></span> | [<span data-ttu-id="97a80-264">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-265">方向 Y</span><span class="sxs-lookup"><span data-stu-id="97a80-265">Direction Y</span></span> | [<span data-ttu-id="97a80-266">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="97a80-267">方向 Z</span><span class="sxs-lookup"><span data-stu-id="97a80-267">Direction Z</span></span> | [<span data-ttu-id="97a80-268">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="97a80-269">浮点曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-269">Float curve</span></span>

<span data-ttu-id="97a80-270">浮点曲线是完全成熟的 Bézier 曲线，具有可变数量的关键帧。</span><span class="sxs-lookup"><span data-stu-id="97a80-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="97a80-271">每个关键帧都存储时间和曲线值，以及每个关键帧左侧和右侧之间的切线和权重。</span><span class="sxs-lookup"><span data-stu-id="97a80-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="97a80-272">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-272">Section</span></span> | <span data-ttu-id="97a80-273">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-274">预包装模式</span><span class="sxs-lookup"><span data-stu-id="97a80-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="97a80-275">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="97a80-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="97a80-276">后包装模式</span><span class="sxs-lookup"><span data-stu-id="97a80-276">Post-Wrap Mode</span></span> | <span data-ttu-id="97a80-277">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="97a80-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="97a80-278">关键帧数</span><span class="sxs-lookup"><span data-stu-id="97a80-278">Number of keyframes</span></span> | <span data-ttu-id="97a80-279">Int32</span><span class="sxs-lookup"><span data-stu-id="97a80-279">Int32</span></span> |
| <span data-ttu-id="97a80-280">关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-280">Keyframes</span></span> | [<span data-ttu-id="97a80-281">Float 关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="97a80-282">Float 关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-282">Float keyframe</span></span>

<span data-ttu-id="97a80-283">float 关键帧将切值和权重值与基本时间和值一起存储。</span><span class="sxs-lookup"><span data-stu-id="97a80-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="97a80-284">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-284">Section</span></span> | <span data-ttu-id="97a80-285">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-286">时间</span><span class="sxs-lookup"><span data-stu-id="97a80-286">Time</span></span> | <span data-ttu-id="97a80-287">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-287">Float32</span></span> |
| <span data-ttu-id="97a80-288">值</span><span class="sxs-lookup"><span data-stu-id="97a80-288">Value</span></span> | <span data-ttu-id="97a80-289">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-289">Float32</span></span> |
| <span data-ttu-id="97a80-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="97a80-290">InTangent</span></span> | <span data-ttu-id="97a80-291">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-291">Float32</span></span> |
| <span data-ttu-id="97a80-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="97a80-292">OutTangent</span></span> | <span data-ttu-id="97a80-293">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-293">Float32</span></span> |
| <span data-ttu-id="97a80-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="97a80-294">InWeight</span></span> | <span data-ttu-id="97a80-295">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-295">Float32</span></span> |
| <span data-ttu-id="97a80-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="97a80-296">OutWeight</span></span> | <span data-ttu-id="97a80-297">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-297">Float32</span></span> |
| <span data-ttu-id="97a80-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="97a80-298">WeightedMode</span></span> | <span data-ttu-id="97a80-299">Int32， [加权模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="97a80-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="97a80-300">布尔曲线</span><span class="sxs-lookup"><span data-stu-id="97a80-300">Boolean curve</span></span>

<span data-ttu-id="97a80-301">布尔曲线是开/关值的简单序列。</span><span class="sxs-lookup"><span data-stu-id="97a80-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="97a80-302">每个关键帧上的曲线值会立即翻转。</span><span class="sxs-lookup"><span data-stu-id="97a80-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="97a80-303">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-303">Section</span></span> | <span data-ttu-id="97a80-304">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-305">预包装模式</span><span class="sxs-lookup"><span data-stu-id="97a80-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="97a80-306">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="97a80-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="97a80-307">后包装模式</span><span class="sxs-lookup"><span data-stu-id="97a80-307">Post-Wrap Mode</span></span> | <span data-ttu-id="97a80-308">Int32， [包装模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="97a80-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="97a80-309">关键帧数</span><span class="sxs-lookup"><span data-stu-id="97a80-309">Number of keyframes</span></span> | <span data-ttu-id="97a80-310">Int32</span><span class="sxs-lookup"><span data-stu-id="97a80-310">Int32</span></span> |
| <span data-ttu-id="97a80-311">关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-311">Keyframes</span></span> | [<span data-ttu-id="97a80-312">布尔关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="97a80-313">布尔关键帧</span><span class="sxs-lookup"><span data-stu-id="97a80-313">Boolean keyframe</span></span>

<span data-ttu-id="97a80-314">布尔关键帧仅存储时间和值。</span><span class="sxs-lookup"><span data-stu-id="97a80-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="97a80-315">部分</span><span class="sxs-lookup"><span data-stu-id="97a80-315">Section</span></span> | <span data-ttu-id="97a80-316">类型</span><span class="sxs-lookup"><span data-stu-id="97a80-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="97a80-317">时间</span><span class="sxs-lookup"><span data-stu-id="97a80-317">Time</span></span> | <span data-ttu-id="97a80-318">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-318">Float32</span></span> |
| <span data-ttu-id="97a80-319">值</span><span class="sxs-lookup"><span data-stu-id="97a80-319">Value</span></span> | <span data-ttu-id="97a80-320">Float32</span><span class="sxs-lookup"><span data-stu-id="97a80-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="97a80-321">换行模式</span><span class="sxs-lookup"><span data-stu-id="97a80-321">Wrap mode</span></span>

<span data-ttu-id="97a80-322">预换模式和后包装模式的语义遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定义。</span><span class="sxs-lookup"><span data-stu-id="97a80-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="97a80-323">它们是以下位的组合：</span><span class="sxs-lookup"><span data-stu-id="97a80-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="97a80-324">值</span><span class="sxs-lookup"><span data-stu-id="97a80-324">Value</span></span> | <span data-ttu-id="97a80-325">含义</span><span class="sxs-lookup"><span data-stu-id="97a80-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="97a80-326">0</span><span class="sxs-lookup"><span data-stu-id="97a80-326">0</span></span> | <span data-ttu-id="97a80-327">默认值：读取设置更高的默认重复模式。</span><span class="sxs-lookup"><span data-stu-id="97a80-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="97a80-328">1</span><span class="sxs-lookup"><span data-stu-id="97a80-328">1</span></span> | <span data-ttu-id="97a80-329">一次：当时间到达动画剪辑的末尾时，该剪辑将自动停止播放，时间将重置为剪辑的开头。</span><span class="sxs-lookup"><span data-stu-id="97a80-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="97a80-330">2</span><span class="sxs-lookup"><span data-stu-id="97a80-330">2</span></span> | <span data-ttu-id="97a80-331">循环：当时间到达动画剪辑的末尾时，时间将在开始时继续。</span><span class="sxs-lookup"><span data-stu-id="97a80-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="97a80-332">4</span><span class="sxs-lookup"><span data-stu-id="97a80-332">4</span></span> | <span data-ttu-id="97a80-333">PingPong：当时间到达动画剪辑的末尾时，时间将在开头和结尾之间 ping 回。</span><span class="sxs-lookup"><span data-stu-id="97a80-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="97a80-334">8</span><span class="sxs-lookup"><span data-stu-id="97a80-334">8</span></span> | <span data-ttu-id="97a80-335">ClampForever：播放动画。</span><span class="sxs-lookup"><span data-stu-id="97a80-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="97a80-336">当它到达末尾时，它将持续播放最后一帧，并且永远不会停止播放。</span><span class="sxs-lookup"><span data-stu-id="97a80-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="97a80-337">加权模式</span><span class="sxs-lookup"><span data-stu-id="97a80-337">Weighted mode</span></span>

<span data-ttu-id="97a80-338">加权模式的语义遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定义。</span><span class="sxs-lookup"><span data-stu-id="97a80-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="97a80-339">值</span><span class="sxs-lookup"><span data-stu-id="97a80-339">Value</span></span> | <span data-ttu-id="97a80-340">含义</span><span class="sxs-lookup"><span data-stu-id="97a80-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="97a80-341">0</span><span class="sxs-lookup"><span data-stu-id="97a80-341">0</span></span> | <span data-ttu-id="97a80-342">无：计算曲线段时，排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="97a80-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="97a80-343">1</span><span class="sxs-lookup"><span data-stu-id="97a80-343">1</span></span> | <span data-ttu-id="97a80-344">In：计算上一条曲线段时包括 inWeight。</span><span class="sxs-lookup"><span data-stu-id="97a80-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="97a80-345">2</span><span class="sxs-lookup"><span data-stu-id="97a80-345">2</span></span> | <span data-ttu-id="97a80-346">Out：计算下一个曲线段时包括 outWeight。</span><span class="sxs-lookup"><span data-stu-id="97a80-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="97a80-347">3</span><span class="sxs-lookup"><span data-stu-id="97a80-347">3</span></span> | <span data-ttu-id="97a80-348">两者：计算曲线段时包括 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="97a80-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
