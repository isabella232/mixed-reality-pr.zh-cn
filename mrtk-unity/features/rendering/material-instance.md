---
title: 材料实例
description: 有关材料实例及其在 MRTK 中的用法的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， MaterialInstance，
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145213"
---
# <a name="material-instance"></a><span data-ttu-id="b8b51-104">材料实例</span><span class="sxs-lookup"><span data-stu-id="b8b51-104">Material instance</span></span>

<span data-ttu-id="b8b51-105">该 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于跟踪实例材料生存期，并自动销毁用户的实例材料。</span><span class="sxs-lookup"><span data-stu-id="b8b51-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="b8b51-106">此实用工具组件可用于替换 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 或 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)。</span><span class="sxs-lookup"><span data-stu-id="b8b51-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="b8b51-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 比材料实例化更可取，但并非在所有方案中始终可用。</span><span class="sxs-lookup"><span data-stu-id="b8b51-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="b8b51-108">为什么使用 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 是一个问题？</span><span class="sxs-lookup"><span data-stu-id="b8b51-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="b8b51-109">如果将以下代码添加到 Unity 场景并点击播放内存使用量将继续增加和减少：</span><span class="sxs-lookup"><span data-stu-id="b8b51-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="b8b51-110">如果运行时间 **过长，上述** 泄漏行为将崩溃 Unity！</span><span class="sxs-lookup"><span data-stu-id="b8b51-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="b8b51-111">作为替代方法，请尝试使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为：</span><span class="sxs-lookup"><span data-stu-id="b8b51-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="b8b51-112">使用情况</span><span class="sxs-lookup"><span data-stu-id="b8b51-112">Usage</span></span>

<span data-ttu-id="b8b51-113">在调用 Unity 的 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) (时) Unity 会自动实例化新的材料。</span><span class="sxs-lookup"><span data-stu-id="b8b51-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="b8b51-114">当不再需要材料或游戏对象被销毁时，调用方负责销毁材料。</span><span class="sxs-lookup"><span data-stu-id="b8b51-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="b8b51-115">该 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于避免材料泄漏，并保持材料分配路径在编辑和运行时保持一致。</span><span class="sxs-lookup"><span data-stu-id="b8b51-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="b8b51-116">当 [无法使用 MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 并且必须实例化材料时，可以使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8b51-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="b8b51-117">如果多个对象需要材料实例的所有权，则最好使用显式所有权进行引用跟踪。</span><span class="sxs-lookup"><span data-stu-id="b8b51-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="b8b51-118"> (ownership 的 aide 存在名为 的可选接口 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) ) 下面是用法示例：</span><span class="sxs-lookup"><span data-stu-id="b8b51-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="b8b51-119">有关详细信息，请参阅行为中演示的示例 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 用法。</span><span class="sxs-lookup"><span data-stu-id="b8b51-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b51-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8b51-120">See also</span></span>

* [<span data-ttu-id="b8b51-121">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="b8b51-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
