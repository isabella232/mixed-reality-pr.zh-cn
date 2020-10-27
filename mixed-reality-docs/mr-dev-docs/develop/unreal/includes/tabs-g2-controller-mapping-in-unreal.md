---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638621"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

游戏输入项目设置中的相同操作和轴映射可用于 c + +。

1. 使用文件/新 c + + 类创建新的 c + + 类 .。。

![创建新的 c + + 类](../images/reverb-g2-img-11.png)

2. 创建卒

![创建卒](../images/reverb-g2-img-12.png)

3. 在项目的 Visual Studio 解决方案中，找到新的卒类并将其配置为输入。
* 首先，在构造函数中，将 AutoPossessPlayer 设置为第一个玩家，将输入路由到卒。

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* 然后，在 SetupPlayerInputComponent 中，将操作和轴事件绑定到项目的输入设置中的操作名称。

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* 将回调函数添加到类：

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

* 用回调函数定义更新卒的标头：

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. 从 Visual Studio 编译，用新的卒启动编辑器。 将 "内容浏览器" 中的卒拖放到游戏，并且在按下输入时，卒现在将执行回调。

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

使用操纵杆轴事件时，轴事件的名称必须以 "_X" 或 "_Y" 结束，对应于所使用的键。

![使用操纵杆事件](../images/reverb-g2-img-09.png)

最后，使用 SteamVR 中的 " **重新生成操作清单** " 和 "在项目设置中 **重新生成控制器绑定** " 按钮 > 流 VR 输入）在游戏中注册操作。

![在项目设置中注册操作](../images/reverb-g2-img-10.png)

