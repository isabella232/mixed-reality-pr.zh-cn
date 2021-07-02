---
title: 材料实例
description: 有关材料实例及其在 MRTK 中的使用的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，MaterialInstance，
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176726"
---
# <a name="material-instance"></a><span data-ttu-id="4a793-104">材料实例</span><span class="sxs-lookup"><span data-stu-id="4a793-104">Material instance</span></span>

<span data-ttu-id="4a793-105">[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)行为 aides 跟踪实例材料生存期，并自动销毁用户的实例材料。</span><span class="sxs-lookup"><span data-stu-id="4a793-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="4a793-106">此实用程序组件可用于替代[呈现器。材料](https://docs.unity3d.com/ScriptReference/Renderer-material.html)或呈现器[。](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)</span><span class="sxs-lookup"><span data-stu-id="4a793-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="4a793-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 优于材料实例，但并不是在所有方案中始终可用。</span><span class="sxs-lookup"><span data-stu-id="4a793-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="4a793-108">为什么使用 [呈现](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器可能会遇到问题？</span><span class="sxs-lookup"><span data-stu-id="4a793-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="4a793-109">如果将下面的代码添加到 Unity 场景，则命中播放内存使用将继续进行顺和顺操作：</span><span class="sxs-lookup"><span data-stu-id="4a793-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

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
> <span data-ttu-id="4a793-110">如果运行的时间太长，上述泄漏行为 **会使 Unity 崩溃** ！</span><span class="sxs-lookup"><span data-stu-id="4a793-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="4a793-111">作为替代方法，请尝试使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为：</span><span class="sxs-lookup"><span data-stu-id="4a793-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

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

## <a name="usage"></a><span data-ttu-id="4a793-112">使用情况</span><span class="sxs-lookup"><span data-stu-id="4a793-112">Usage</span></span>

<span data-ttu-id="4a793-113">当调用 Unity 的 [呈现](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器)  (时，unity 会自动实例化新材料。</span><span class="sxs-lookup"><span data-stu-id="4a793-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="4a793-114">当不再需要材料或销毁游戏对象时，调用方负责销毁材料。</span><span class="sxs-lookup"><span data-stu-id="4a793-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="4a793-115">此 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于避免材料泄漏，并使材料分配路径在编辑和运行时保持一致。</span><span class="sxs-lookup"><span data-stu-id="4a793-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="4a793-116">当无法使用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 并且必须实例化材料时， [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 可按如下所示使用：</span><span class="sxs-lookup"><span data-stu-id="4a793-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

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

<span data-ttu-id="4a793-117">如果多个对象需要材料实例的所有权，则最好将显式所有权用于引用跟踪。</span><span class="sxs-lookup"><span data-stu-id="4a793-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="4a793-118"> (名 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 为的可选接口 ) 具有所有权的助手。下面的示例用法：</span><span class="sxs-lookup"><span data-stu-id="4a793-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

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

<span data-ttu-id="4a793-119">有关详细信息，请参阅行为中演示的示例用法 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 。</span><span class="sxs-lookup"><span data-stu-id="4a793-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a793-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a793-120">See also</span></span>

* [<span data-ttu-id="4a793-121">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="4a793-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
