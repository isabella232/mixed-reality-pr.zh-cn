---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204198"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

游戏的输入项目设置中的相同操作和轴映射可以从 C++ 使用。

1. 使用文件/新 C++ 类创建新的 C++ 类...

![创建新的 C++ 类](../images/reverb-g2-img-11.png)

2. 创建 pawn

![创建 pawn](../images/reverb-g2-img-12.png)

3. 在项目的 Visual Studio解决方案中，找到新的 Pawn 类并对其进行配置以输入。
* 首先，在构造函数中，将 AutoPossessPlayer 设置为第一个将输入路由到 pawn 的播放器。

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* 然后，在 SetupPlayerInputComponent 中，将操作和轴事件绑定到项目输入设置中的操作名称。

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* 将回调函数添加到 类：

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* 使用回调函数定义更新 Pawn 的标头：

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. 从 Visual Studio 编译，以使用新的 pawn 启动编辑器。 将 pawn 从内容浏览器拖放到游戏，现在当按下输入时，pawn 将执行回调。

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

使用 thumbstick 轴事件时，轴事件的名称必须以与所使用的键对应的"_X"或"_Y"结尾。

![使用 thumbstick 事件](../images/reverb-g2-img-09.png)

最后，使用 Steam VR 输入中的"重新生成操作清单"和"重新生成控制器绑定"按钮，将Project 设置 >注册到 SteamVR。

![在项目设置中注册操作](../images/reverb-g2-img-10.png)

