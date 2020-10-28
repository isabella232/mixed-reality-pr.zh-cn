---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638621"
---
# <a name="all-platforms"></a>[<span data-ttu-id="2a5f3-101">所有平台</span><span class="sxs-lookup"><span data-stu-id="2a5f3-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="2a5f3-102">游戏输入项目设置中的相同操作和轴映射可用于 c + +。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="2a5f3-103">使用文件/新 c + + 类创建新的 c + + 类 .。。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-103">Create a new C++ Class with File/New C++ Class...</span></span>

![创建新的 c + + 类](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="2a5f3-105">创建卒</span><span class="sxs-lookup"><span data-stu-id="2a5f3-105">Create a pawn</span></span>

![创建卒](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="2a5f3-107">在项目的 Visual Studio 解决方案中，找到新的卒类并将其配置为输入。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="2a5f3-108">首先，在构造函数中，将 AutoPossessPlayer 设置为第一个玩家，将输入路由到卒。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="2a5f3-109">然后，在 SetupPlayerInputComponent 中，将操作和轴事件绑定到项目的输入设置中的操作名称。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="2a5f3-110">将回调函数添加到类：</span><span class="sxs-lookup"><span data-stu-id="2a5f3-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="2a5f3-111">用回调函数定义更新卒的标头：</span><span class="sxs-lookup"><span data-stu-id="2a5f3-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="2a5f3-112">从 Visual Studio 编译，用新的卒启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="2a5f3-113">将 "内容浏览器" 中的卒拖放到游戏，并且在按下输入时，卒现在将执行回调。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="2a5f3-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="2a5f3-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="2a5f3-115">使用操纵杆轴事件时，轴事件的名称必须以 "_X" 或 "_Y" 结束，对应于所使用的键。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![使用操纵杆事件](../images/reverb-g2-img-09.png)

<span data-ttu-id="2a5f3-117">最后，使用 SteamVR 中的 " **重新生成操作清单** " 和 "在项目设置中 **重新生成控制器绑定** " 按钮 > 流 VR 输入）在游戏中注册操作。</span><span class="sxs-lookup"><span data-stu-id="2a5f3-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![在项目设置中注册操作](../images/reverb-g2-img-10.png)

