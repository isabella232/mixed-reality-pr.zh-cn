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
# <a name="material-instance"></a>材料实例

[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)行为 aides 跟踪实例材料生存期，并自动销毁用户的实例材料。 此实用程序组件可用于替代[呈现器。材料](https://docs.unity3d.com/ScriptReference/Renderer-material.html)或呈现器[。](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 优于材料实例，但并不是在所有方案中始终可用。

为什么使用 [呈现](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器可能会遇到问题？ 如果将下面的代码添加到 Unity 场景，则命中播放内存使用将继续进行顺和顺操作：

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
> 如果运行的时间太长，上述泄漏行为 **会使 Unity 崩溃** ！

作为替代方法，请尝试使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为：

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

## <a name="usage"></a>使用情况

当调用 Unity 的 [呈现](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器)  (时，unity 会自动实例化新材料。 当不再需要材料或销毁游戏对象时，调用方负责销毁材料。 此 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于避免材料泄漏，并使材料分配路径在编辑和运行时保持一致。

当无法使用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 并且必须实例化材料时， [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 可按如下所示使用：

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

如果多个对象需要材料实例的所有权，则最好将显式所有权用于引用跟踪。  (名 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 为的可选接口 ) 具有所有权的助手。下面的示例用法：

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

有关详细信息，请参阅行为中演示的示例用法 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 。

## <a name="see-also"></a>另请参阅

* [MRTK 标准着色器](mrtk-standard-shader.md)
