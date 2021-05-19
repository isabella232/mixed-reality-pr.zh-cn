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
# <a name="material-instance"></a>材料实例

该 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于跟踪实例材料生存期，并自动销毁用户的实例材料。 此实用工具组件可用于替换 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 或 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)。

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 比材料实例化更可取，但并非在所有方案中始终可用。

为什么使用 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 是一个问题？ 如果将以下代码添加到 Unity 场景并点击播放内存使用量将继续增加和减少：

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
> 如果运行时间 **过长，上述** 泄漏行为将崩溃 Unity！

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

在调用 Unity 的 [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) (时) Unity 会自动实例化新的材料。 当不再需要材料或游戏对象被销毁时，调用方负责销毁材料。 该 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行为有助于避免材料泄漏，并保持材料分配路径在编辑和运行时保持一致。

当 [无法使用 MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 并且必须实例化材料时，可以使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) ，如下所示：

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

如果多个对象需要材料实例的所有权，则最好使用显式所有权进行引用跟踪。  (ownership 的 aide 存在名为 的可选接口 [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) ) 下面是用法示例：

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

有关详细信息，请参阅行为中演示的示例 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 用法。

## <a name="see-also"></a>另请参阅

* [MRTK 标准着色器](mrtk-standard-shader.md)
