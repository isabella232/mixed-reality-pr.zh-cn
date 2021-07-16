---
title: 按钮
description: MRTK 中的按钮概述
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、MRTK 按钮
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281856"
---
# <a name="buttons"></a>按钮

![按钮主按钮](../images/button/MRTK_Button_Main.png)

按钮为用户提供了触发即时操作的方法。 它是混合现实中最基础的组件之一。 MRTK 提供各种类型的按钮预制。

## <a name="button-prefabs-in-mrtk"></a>MRTK 中的按钮预制

文件夹下的 ``MRTK/SDK/Features/UX/Interactable/Prefabs`` 按钮预制示例

### <a name="unity-ui-imagegraphic-based-buttons"></a>基于 Unity UI 图像/图形的按钮

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>基于碰撞体按钮

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    HoloLens 2外壳样式按钮，带底板，支持各种视觉反馈，例如边框光、邻近感应光和压缩的前板
    :::column-end:::
    :::column:::
    HoloLens 2不带反板的 shell 样式按钮
    :::column-end:::
    :::column:::
    HoloLens 2圆形的 shell 样式按钮
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96 PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    宽HoloLens 2 shell 样式按钮 32x96mm
    :::column-end:::
    :::column:::
    水平HoloLens 2带共享底板的按钮栏
    :::column-end:::
    :::column:::
    具有HoloLens 2底板的垂直按钮栏
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32 PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32 PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32 PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    HoloLens 2 shell 样式复选框 32x32mm
    :::column-end:::
    :::column:::
    HoloLens 2 shell 样式开关 32x32mm 
    :::column-end:::
    :::column:::
    HoloLens 2 shell 样式的无线电 32x32mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96 PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96 PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96 PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 2 shell 样式复选框 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 shell 样式开关 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 shell 样式的无线电 32x96mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![径 ](../images/button/MRTK_Button_Radial.png) **向径向**
    :::column-end:::
    :::column:::
    ![复选框 ](../images/button/MRTK_Button_Checkbox.png) **复选框**
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    径向按钮 
    :::column-end:::
    :::column:::
    复选框 
    :::column-end:::
    :::column:::
    切换开关
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![按钮基本 ](../images/button/MRTK_Button_Base.png) **按钮**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens第一代的 shell 样式按钮
    :::column-end:::
    :::column:::
    圆形按钮
    :::column-end:::
    :::column:::
    “基本”按钮
    :::column-end:::
:::row-end:::

 (`Button` Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) 基于可交互概念，为[](interactable.md)按钮或其他类型的交互式图面提供简单的 UI 控件。 基线按钮支持所有可用的输入方法，包括近部交互的表达手部输入，以及远端交互的凝视 + 空敲击。 还可使用语音命令触发按钮。

`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) 是 HoloLens 2 的 shell 样式按钮，支持直接手部跟踪输入的按钮的精确移动。 它将脚本 `Interactable` 与脚本 `PressableButton` 组合在一起。

对于HoloLens 2，建议使用具有不透明底板的按钮。 由于以下可用性和稳定性问题，不建议使用透明按钮：

* 物理环境难以读取图标和文本
* 很难理解何时触发事件
* 全息影像深度 LSR 稳定时，通过透明平面显示HoloLens 2不稳定

![按钮已设置色块](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>如何使用可按下按钮

### <a name="unity-ui-based-buttons"></a>基于 Unity UI 的按钮

使用 (GameObject -> UI -> Canvas) 在场景中创建画布。 在画布的"检查器"面板中：

* 单击"转换为 MRTK 画布"
* 单击"添加 NearInteractionTouchableUnityUI"
* 将矩形转换组件的 X、Y 和 Z 刻度设置为 0.001

然后，拖动 `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab) ， `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab) ，或画布上的 `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) 。

### <a name="collider-based-buttons"></a>基于碰撞体按钮

只需将 `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) 或 `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) 拖动到场景中。 这些按钮预制项已配置为提供各种类型的输入（包括明确手部输入和凝视）的音频视觉对象反馈。

预制件本身以及可交互组件中公开的事件可用于触发其他操作[](interactable.md)。 [HandInteractionExample](../example-scenes/hand-interaction-examples.md)场景中的可按下按钮使用 Interactable 的 *OnClick* 事件触发多维数据集颜色的变化。 对于不同类型的输入方法（如凝视、敲击、手部射线，以及通过可按下按钮脚本的物理按钮按下）触发此事件。

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

可以通过按钮上的 来配置可按下按钮何时触发 *OnClick* `PhysicalPressEventRouter` 事件。 例如，可以将 *OnClick* 设置为在首次按下按钮时启动，而不是按下和释放，只需将"可交互"设置为"单击时事件"*即可。*

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

若要利用特定的手部输入状态信息，可以使用可按下按钮事件 - Touch *Begin、Touch* *End、Button* *Pressed、Button* *Released。* 但是，这些事件不会在响应敲击、手部射线或眼睛输入时发生。 **若要同时支持近近交互，建议使用 Interactable 的 *OnClick* 事件。**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>交互状态

处于空闲状态时，按钮的前盘不可见。 当手指接近或光标从凝视输入指向表面时，前盘的闪烁边框将变为可见。 前板图面上的指指位置有额外的突出显示。 当用手指推入时，前盘会随手移动。 当手指触摸前盘表面时，它会显示一种细微的脉冲效果，提供触摸点的视觉反馈。

在HoloLens 2 shell 样式按钮中，有许多视觉提示和视觉元素，可增强用户对交互的置信度。

|  ![邻近感应灯](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦点突出显示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![压缩机](../images/button/ux_button_affordance_compression.jpg) | ![触发时脉冲](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| 邻近感应灯 | 焦点突出显示 | 压缩机 | 触发时脉冲 |

可按下按钮触发细微脉冲效果，该按钮查找 (指针上) 的 *ProximityLight* 对象。 如果找到任何邻近光，则调用 方法，该方法会自动对着色器参数进行动画处理以显示 `ProximityLight.Pulse` 脉冲。

## <a name="inspector-properties"></a>检查器属性

![按钮结构](../images/button/MRTK_Button_Structure.png)

**盒碰撞体** 
 `Box Collider`按钮前板的 。

**可按下按钮** 按钮移动与手动按下交互的逻辑。

**物理按下事件路由器** 此脚本将事件从手动按下交互发送到 [可交互](interactable.md)的 。

**可交互** 
[可交互](interactable.md)处理各种类型的交互状态和事件。 HoloLens脚本直接处理凝视、手势和语音输入以及沉浸式头戴显示设备运动控制器输入。

**音频源** 音频反馈剪辑的 Unity 音频源。

*NearInteractionTouchable.cs* 需要使任何对象都能够触摸到已表达的手动输入。

## <a name="prefab-layout"></a>预制布局

*ButtonContent* 对象包含前板、文本标签和图标。 *FrontPlate* 使用着色器响应索引 *Button_Box邻近性*。 它显示闪烁边框、邻近光和触控脉冲效果。 文本标签是使用 TextMesh Pro。 *SeeItSayItLabel* 的可见性由 [可交互](interactable.md)的主题控制。

![按钮布局](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>如何更改图标和文本

MRTK 按钮使用 组件来帮助你更改按钮的 `ButtonConfigHelper` 图标、文本和标签。  (请注意，如果所选按钮上不存在元素，则某些字段可能不存在。) 

![按钮配置帮助程序](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>创建和修改图标集

图标 **集** 是组件使用的一组共享图标 `ButtonConfigHelper` 资产。 支持 *三种* 图标样式。

* **四** 边形图标使用 在四边形上呈现 `MeshRenderer` 。 这是默认图标样式。
* **子画面** 图标是使用 呈现的 `SpriteRenderer` 。 如果希望将图标导入为子画面表，或者希望与 Unity UI 组件共享图标资产，则此功能很有用。 若要使用此样式，需要安装 Sprite 编辑器包 (Windows **-> 程序包管理器 -> 2D 子画面)**
* **字符** 图标是使用 组件 `TextMeshPro` 呈现的。 如果希望使用图标字体，这很有用。 若要使用HoloLens图标字体，需要创建字体 `TextMeshPro` 资产。

若要更改按钮使用的样式，请展开 ButtonConfigHelper 中的"图标"下拉列表，然后从"图标样式 *"* 下拉列表中选择 。 

可以使用资产菜单创建新的按钮图标集："创建混合现实 **>"图标Toolkit >设置" 。** 若要添加四边形图标和子画面图标，只需将它们拖动到各自的数组中。 若要添加 Char 图标，必须先创建并分配字体资产。

在 MRTK 2.4 及更中，建议将自定义图标纹理移动到 IconSet 中。
若要将项目中所有按钮上的资产升级到新的推荐格式，请使用 ButtonConfigHelperMigrationHandler。
 (混合现实Toolkit -> 实用工具 -> 迁移窗口 -> 迁移处理程序选择 -> Microsoft.MixedReality。Toolkit。Utilities.ButtonConfigHelperMigrationHandler) 

导入升级按钮所需的 Microsoft.MixedRealityToolkit.Unity.Tools 包。

![升级窗口对话](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

如果在迁移过程中的默认图标集内找不到图标，将在 MixedRealityToolkit.Generated/CustomIconSets 中创建自定义图标集。 此时会显示一个对话框，指示已发生此状态。

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>创建HoloLens图标字体资产

首先，将图标字体导入 Unity。 在Windows计算机上，可以在 *HoloLens/Fonts/holomdl2.ttf Windows默认字体。* 将此文件复制并粘贴到"资产"文件夹中。

接下来，通过"窗口"打开 TextMeshPro 字体资产创建者 **> TextMeshPro >"字体资产创建者"。** 下面是用于生成字体图集HoloLens设置。 若要包括所有图标，将以下 Unicode 范围粘贴到 *"字符序列"* 字段中：

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![按钮创建 1](../images/button/MRTK_Font_Asset_Creation_1.png)

生成字体资产后，将其保存到项目中，并将其分配给图标集的 *"字符图标字体"* 字段。 现在 *将填充* "可用图标"下拉列表。 若要使图标可供按钮使用，请单击它。 它将被添加到" *所选图标* "下拉列表中，现在会显示在"可以选择为图标 `ButtonConfigHelper.` 提供标记"中。 这允许在运行时设置图标。

![按钮创建 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![按钮创建 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

若要使用图标集选择按钮，请展开 中的"图标"下拉列表 `ButtonConfigHelper` ，并将其分配给"图标集 *"* 字段。

![按钮图标集](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>如何更改按钮的大小

HoloLens 2 shell 样式按钮的大小为 32x32mm。 若要自定义维度，请更改按钮预制件中这些对象的大小：

1. **FrontPlate**
2. **BackPlate** 下的四边形
3. **根上的** 盒碰撞体

然后，单击位于按钮 **根** 目录的 NearInteractionTouchable 脚本中的"修复边界"按钮。

更新 FrontPlate 按钮 ![ 大小自定义项的大小 1](../images/button/MRTK_Button_SizeCustomization1.png)

更新四边形 ![ 按钮大小自定义项的大小 2](../images/button/MRTK_Button_SizeCustomization2.png)

更新"盒碰撞体按钮大小 ![ "自定义项的大小 3](../images/button/MRTK_Button_SizeCustomization3.png)

单击"修复边界" ![ 按钮大小自定义项 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>语音 ("see-it，假设) 

**语音输入处理程序** 可 [按下按钮](interactable.md) 中的可交互脚本已实现 `IMixedRealitySpeechHandler` 。 可以在此处设置语音命令关键字。

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**语音输入配置文件** 此外，需要在全局语音命令配置文件 中注册 voice *命令关键字*。

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**查看，Say-it 标签** 可按下按钮预制项在 *SeeItSayItLabel* Pro下具有占位符 TextMesh 标签。 可以使用此标签将按钮的语音命令关键字传达给用户。

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>如何从头开始创建按钮

可以在 **PressableButtonExample** 场景中找到这些按钮的示例。

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1.创建具有多维数据集的可按下按钮 (交互仅) 

1. 创建 Unity 多维数据集 (GameObject > 3D 对象>多维数据集) 
2. 添加 `PressableButton.cs` 脚本
3. 添加 `NearInteractionTouchable.cs` 脚本

在 `PressableButton` 的"检查器"面板中，将多维数据集对象分配给"**移动按钮视觉对象"。**

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

选择多维数据集时，对象上将看到多个彩色层。 这会将"按"下的距离值可视化 **设置。** 使用句柄，可以配置何时开始按 (对象) 触发事件。

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

按下按钮时，它将移动并生成脚本中公开的正确事件，例如 `PressableButton.cs` TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>故障排除

如果按钮正在执行双击，请确保"强制前推"属性处于活动状态，并且"开始推送距离"平面放置在近距 **交互可触摸** 平面的前面。 近 **交互可触摸** 平面由下面 gif 中白色箭头原点前面的蓝色平面指示：

![突出显示了"强制执行 Front Push"属性的可按下按钮脚本组件](../images/button/MRTK_Button_Enforce_Push.png)

![在近距交互可触摸平面前面移动起始推送距离的动画示例](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2.向基本多维数据集按钮添加视觉反馈

MRTK 标准着色器提供各种功能，便于添加视觉反馈。 创建材料并选择着色器 `Mixed Reality Toolkit/Standard` 。 或者，可以使用或复制下使用 `/SDK/StandardAssets/Materials/` MRTK 标准着色器的现有材料之一。

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

选中 `Hover Light` " `Proximity Light` 选项 **"下的 Fluent 和**。 这样，鼠标悬停光交互 (近距) 和远距指针 () 视觉反馈。

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3.向基本多维数据集按钮添加音频反馈

由于脚本公开 `PressableButton.cs` 了 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此可以轻松分配音频反馈。 只需将 Unity 添加到多维数据集 `Audio Source` 对象，然后选择 AudioSource.PlayOneShot () 。 可以使用 "文件夹" 下的 MRTK_Select_Main 和 MRTK_Select_Secondary 音频剪辑 `/SDK/StandardAssets/Audio/` 。

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. 添加可视状态并处理远距离交互事件

[种不可交互](interactable.md) 是一个脚本，可轻松地为各种类型的输入交互创建可视状态。 它还处理远距离交互事件。 添加 `Interactable.cs` 多维数据集对象并将其拖放到 "**配置文件**" 下的 **目标** 字段。 然后，使用类型 **ScaleOffsetColorTheme** 创建一个新主题。 在此主题下，可以指定特定交互状态的对象的颜色，如 **焦点** 和 **按下** 状态。 还可以控制缩放和偏移量。 检查 **缓动** 并设置持续时间，以使视觉对象过渡平滑。

![选择配置文件主题](../images/button/mrtk_button_profiles.gif)

你将看到对象同时响应 (的手 ray 或注视光标) ，并接近 (手型) 交互。

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>自定义按钮示例

在 [HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中，请参阅使用的钢琴和轮按钮示例 `PressableButton` 。

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

每个钢琴键均已 `PressableButton` 分配一个和一个 `NearInteractionTouchable` 脚本。 务必验证的 *本地前向* 方向是 `NearInteractionTouchable` 正确的。 它在编辑器中用白色箭头表示。 请确保箭头指向按钮的正面：

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>另请参阅

* [可交互](interactable.md)
* [视觉主题](visual-themes.md)
