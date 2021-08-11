---
title: 按钮
description: MRTK 中的按钮概述
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、MRTK 按钮
ms.openlocfilehash: 7d1c141981ec402d85e1e2004739e9ab9f0ebe9da5361e4e3100b43a2b5b4129
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228880"
---
# <a name="buttons"></a>按钮

![主要按钮](../images/button/MRTK_Button_Main.png)

按钮为用户提供了触发即时操作的方法。 这是混合现实中最基本的组件之一。 MRTK 提供各种类型的按钮 prototyping。

## <a name="button-prefabs-in-mrtk"></a>MRTK 中的按钮 prototyping

文件夹下的按钮 prototyping 示例 ``MRTK/SDK/Features/UX/Interactable/Prefabs``

### <a name="unity-ui-imagegraphic-based-buttons"></a>Unity UI 图像/基于图形的按钮

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>基于碰撞器的按钮

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
    HoloLens 2 的带有 backplate 的 shell 样式按钮，该按钮支持各种视觉反馈，如边框细、邻近浅色和压缩前板
    :::column-end:::
    :::column:::
    不带 backplate HoloLens 2 的 shell 样式按钮
    :::column-end:::
    :::column:::
    带有圆形形状的 HoloLens 2 shell 样式按钮
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
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
    宽 HoloLens 2 的 shell 样式按钮32x96mm
    :::column-end:::
    :::column:::
    具有共享 backplate 的水平 HoloLens 2 按钮栏
    :::column-end:::
    :::column:::
    带有共享 backplate 的垂直 HoloLens 2 按钮栏
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    HoloLens 2 的 shell 样式复选框32x32mm
    :::column-end:::
    :::column:::
    HoloLens 2 的 shell 样式开关32x32mm 
    :::column-end:::
    :::column:::
    HoloLens 2 的 shell 样式收音机32x32mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 2 的 shell 样式复选框32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 的 shell 样式开关32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2 的 shell 样式收音机32x96mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![放射 ](../images/button/MRTK_Button_Radial.png) 辐射
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
    ![按钮基 ](../images/button/MRTK_Button_Base.png) **按钮**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 第一代的 "shell 样式" 按钮
    :::column-end:::
    :::column:::
    圆形形状推送按钮
    :::column-end:::
    :::column:::
    “基本”按钮
    :::column-end:::
:::row-end:::

`Button` (资产/MRTK/SDK/功能/UX/种不可交互/prototyping/prefab) 基于[种不可交互](interactable.md)概念，以便为按钮或其他类型的交互表面提供简单的 UI 控件。 "基线" 按钮支持所有可用的输入方法，包括接近交互的有向右输入，还支持 "注视" 和 "空中点击" 进行远距离交互。 你还可以使用语音命令触发该按钮。

`PressableButtonHoloLens2` (资产/MRTK/SDK/Features/UX/种不可交互/prototyping/PressableButtonHoloLens2) 是 HoloLens 2 的 shell 样式按钮，该按钮支持直接手动跟踪输入的按钮的精确移动。 它将 `Interactable` 脚本与 `PressableButton` 脚本结合起来。

对于 HoloLens 2，建议使用不透明 backplate 的按钮。 不建议使用透明按钮，因为存在以下可用性和稳定性问题：

* 在物理环境中，无法读取图标和文本
* 事件触发时很难理解
* 通过透明平面显示的全息影像可能与 HoloLens 2 深度 LSR 稳定性不稳定

![按钮 plated](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>如何使用 pressable 按钮

### <a name="unity-ui-based-buttons"></a>基于 Unity UI 的按钮

 (GameObject-> UI > 画布) 中创建画布。 在画布的 "检查器" 面板中：

* 单击 "转换为 MRTK 画布"
* 单击 "添加 NearInteractionTouchableUnityUI"
* 将矩形转换组件的 X、Y 和 Z 刻度设置为0.001

然后，将 `PressableButtonUnityUI` (资产/MRTK/SDK/Features/ux/种不可交互/prototyping/PressableButtonUnityUI. prefab) ， `PressableButtonUnityUICircular` (资产/MRTK/Sdk/FEATURES/Ux/种不可交互/prototyping/PressableButtonUnityUICircular) ，或 `PressableButtonHoloLens2UnityUI` (资产/prefab/sdk/features//MRTK/种不可交互/prototyping) 拖到画布上。

### <a name="collider-based-buttons"></a>基于碰撞器的按钮

只需将 `PressableButtonHoloLens2` (资产/MRTK/SDK/功能/ux/种不可交互/prototyping/PressableButtonHoloLens2. prefab) 或 `PressableButtonHoloLens2Unplated` (资产/MRTK/Sdk/FEATURES/ux/种不可交互/prototyping/PressableButtonHoloLens2Unplated) 到场景中。 这些按钮 prototyping 已配置为对各种类型的输入具有音频视觉对象反馈，其中包括有表述的手写输入和注视。

Prefab 本身以及 [种不可交互](interactable.md) 组件中公开的事件可用于触发其他操作。 [HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中的 pressable 按钮使用种不可交互的 *OnClick* 事件来触发多维数据集颜色的更改。 此事件是针对不同类型的输入法（如注视、分流、手型）以及通过 pressable 按钮脚本的物理按钮按下触发的。

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

可以通过按钮上的打开 "pressable" *按钮的配置* 时间 `PhysicalPressEventRouter` 。 例如，可以将 *OnClick* 设置为第一次按下按钮时激发，而不是按下并释放，方法是 *在**按下* 时，将种不可交互设置为单击事件。

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

若要利用特定的可表述的手写输入状态信息，你可以使用 pressable 按钮事件- *Touch 开始*、 *触摸端*、 *按下按钮*、 *按钮已释放*。 不过，这些事件不会因出现空中点击、触碰或眼睛输入而激发。 **为了同时支持近交互和远交互，建议使用种不可交互的 *OnClick* 事件。**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>交互状态

处于空闲状态时，按钮的顶层印不见。 作为手指方法，或从注视输入定位到表面的光标，前面板的光亮边框变为可见。 前板面上的手指位置还有其他突出突出。 用手指推送时，前板会随手指移动。 当手指接触到前板面时，它会显示一种细小的脉冲效果，以提供触摸点的可视反馈。

在 HoloLens 2 shell 样式 "按钮中，有很多视觉提示和实用，可以提高用户交互的置信度。

|  ![邻近感应灯](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦点突出显示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![压缩箱](../images/button/ux_button_affordance_compression.jpg) | ![触发暂停](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| 邻近感应灯 | 焦点突出显示 | 压缩箱 | 触发暂停 |

精细的脉冲效果由 pressable 按钮触发，该按钮查找当前正在交互的指针上的 *ProximityLight (s)* 。 如果找到任何邻近光源，则会 `ProximityLight.Pulse` 调用方法，这会自动对着色器参数进行动画处理以显示脉冲。

## <a name="inspector-properties"></a>检查器属性

![按钮结构](../images/button/MRTK_Button_Structure.png)

**框碰撞器** 
 `Box Collider`按钮的前面板。

**Pressable 按钮** 用手按下交互的按钮移动的逻辑。

**物理按下事件路由器** 此脚本将事件从一开始按下交互发送到 [种不可交互](interactable.md)。

**种不可交互** 
[种不可交互](interactable.md)处理各种类型的交互状态和事件。 此脚本直接处理 HoloLens 注视、手势和语音输入以及沉浸式耳机运动控制器输入。

**音频源** 音频反馈剪辑的 Unity 音频源。

*NearInteractionTouchable* 是使任何对象可触摸带有明确表述的手写输入所需的。

## <a name="prefab-layout"></a>Prefab 布局

*ButtonContent* 对象包含前板、文本标签和图标。 *FrontPlate* 使用 *Button_Box* 着色器响应索引手指的邻近性。 它显示光亮边界、邻近浅色和对触控的脉冲效果。 文本标签用 TextMesh Pro。 *SeeItSayItLabel* 的可见性由 [种不可交互](interactable.md)的主题控制。

![按钮布局](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>如何更改图标和文本

MRTK 按钮使用 `ButtonConfigHelper` 组件来帮助您更改按钮图标、文本和标签。  (请注意，如果所选按钮上没有元素，则某些字段可能不存在。 ) 

![按钮配置帮助器](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>创建和修改图标集

**图标集** 是组件使用的一组共享图标资产 `ButtonConfigHelper` 。 支持三种图标 *样式* 。

* 使用在四个图标上呈现 **四** 个图标 `MeshRenderer` 。 这是默认图标样式。
* 使用呈现子 **画面** 图标 `SpriteRenderer` 。 如果希望将图标作为 sprite 表导入，或者需要将图标资产与 Unity UI 组件共享，这会很有用。 若要使用此样式，将需要安装动画编辑器包， **(Windows > 程序包管理器 > 2d Sprite)**
* 使用组件呈现 **字符** 图标 `TextMeshPro` 。 如果希望使用图标字体，这会很有用。 若要使用 HoloLens 图标字体，你将需要创建 `TextMeshPro` 字体资产。

若要更改按钮使用的样式，请展开 ButtonConfigHelper 中的 *图标* 下拉列表，并从 *图标样式* 下拉列表中进行选择。

你可以使用 "资产" 菜单创建一个新的按钮图标集： "**创建 > 混合现实" Toolkit > "图标集。** 若要添加四个和动画图标，只需将其拖到各自的数组中。 若要添加字符图标，必须首先创建和分配字体资产。

在 MRTK 2.4 和更高版本中，我们建议将自定义图标纹理移到 IconSet 中。
若要将项目中所有按钮上的资产升级为新建议的格式，请使用 ButtonConfigHelperMigrationHandler。
 (混合现实 Toolkit-> 实用工具-> 迁移窗口-> 迁移处理程序选择-> MixedReality。Toolkit。ButtonConfigHelperMigrationHandler) 

导入升级按钮所需的 MixedRealityToolkit 包。

![升级窗口对话框](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

如果在迁移过程中在默认图标集中找不到图标，将在 MixedRealityToolkit/CustomIconSets 中创建自定义图标集。 此时将显示一个对话框，指示已发生此情况。

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>创建 HoloLens 图标字体资产

首先，将图标字体导入 Unity。 在 Windows 机上，可以在 *Windows/Fonts/holomdl2.ttf.* 中找到默认的 HoloLens 字体。 将此文件复制并粘贴到 "资产" 文件夹中。

接下来，通过 **> TextMeshPro > 字体资产创建者的窗口** 打开 TextMeshPro 字体资产创建者。 下面是用于生成 HoloLens 字体阿特拉斯的推荐设置。 若要包含所有图标，请将以下 Unicode 范围粘贴到 *字符序列* 字段中：

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![按钮创建1](../images/button/MRTK_Font_Asset_Creation_1.png)

生成字体资产后，将其保存到你的项目，并将其分配给图标集的 *字符图标字体* 字段。 此时将填充 *可用图标* 下拉列表。 若要使图标可用于按钮，请单击该图标。 它将被添加到 " *选定的图标* " 下拉列表中，此时将显示在中， `ButtonConfigHelper.` 可以选择为图标指定标记。 这样就可以在运行时设置图标。

![按钮创建3](../images/button/MRTK_Font_Asset_Creation_3.png)

![按钮创建2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

若要使用图标集，请选择一个按钮，展开中的图标下拉列表， `ButtonConfigHelper` 并将其分配给 *图标集* 字段。

![按钮图标集](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>如何更改按钮大小

HoloLens 2 的 shell 样式按钮的大小为32x32mm。 若要自定义维度，请在 prefab 按钮中更改这些对象的大小：

1. **FrontPlate**
2. BackPlate 下的 **四核**
3. 根上的 **Box 碰撞** 器

然后，在 NearInteractionTouchable 脚本中单击 " **修复边界** " 按钮，该脚本位于按钮的根目录中。

更新 "FrontPlate" ![ 按钮大小自定义项的大小1](../images/button/MRTK_Button_SizeCustomization1.png)

更新四 ![ 按钮大小自定义项的大小2](../images/button/MRTK_Button_SizeCustomization2.png)

更新框碰撞器 ![ 按钮大小自定义3的大小](../images/button/MRTK_Button_SizeCustomization3.png)

单击 "修复边界" ![ 按钮大小自定义4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it&quot;></a>语音命令 ( &quot;见 ..." ) 

**语音输入处理程序** Pressable 按钮中的 [种不可交互](interactable.md) 脚本已实现 `IMixedRealitySpeechHandler` 。 可以在此处设置语音命令关键字。

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**语音输入配置文件** 此外，还需要在全局 *语音命令配置文件* 中注册语音命令关键字。

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**请参阅-it 标签** pressable 按钮 prefab 在 *SeeItSayItLabel* 对象下有一个占位符 TextMesh Pro 标签。 您可以使用此标签来向用户传达按钮的语音命令关键字。

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>如何从头开始按钮

可以在 **PressableButtonExample** 场景中找到这些按钮的示例。

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. 创建一个 pressable 按钮，其中包含多维数据集 (接近交互) 

1.  (GameObject > 3D Object > 多维数据集创建 Unity 多维数据集) 
2. 添加 `PressableButton.cs` 脚本
3. 添加 `NearInteractionTouchable.cs` 脚本

在 `PressableButton` 的 "检查器" 面板中，将 cube 对象分配给 **移动按钮视觉** 对象。

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

选择多维数据集时，会在对象上看到多个彩色层。 这会直观显示下 **设置** 的距离值。 使用句柄，可以配置何时开始按下 (将对象移动) 以及何时触发事件。

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

按下该按钮时，它将移动并生成正确的事件， `PressableButton.cs` 如 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>疑难解答

如果按钮正在执行双击，请确保 " **强制前台推送** " 属性处于活动状态，" **开始推送距离** " 平面置于 **Near 交互可触摸** 平面的前方。 **近交互可触摸** 平面由下方 gif 中白色箭头原点前面的蓝色平面表示：

![突出显示了 "强制前台推送" 属性的 Pressable 按钮脚本组件](../images/button/MRTK_Button_Enforce_Push.png)

![在接近交互可触摸平面前面移动起始推送距离的动画示例](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. 将视觉反馈添加到 "基本多维数据集" 按钮

MRTK 标准着色器提供各种功能，可轻松添加视觉反馈。 创建材料并选择着色器 `Mixed Reality Toolkit/Standard` 。 或者，您可以使用或复制 `/SDK/StandardAssets/Materials/` 使用 MRTK 标准着色器的现有材料中的一个。

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

勾选 `Hover Light` `Proximity Light` **Fluent 选项**。 这将为近手 (邻近感应) 和远端指针， (悬停光) 交互提供视觉反馈。

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. 将音频反馈添加到 "基本" 多维数据集按钮

由于 `PressableButton.cs` 脚本公开了 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此我们可以轻松地分配音频反馈。 只需将 Unity 添加 `Audio Source` 到多维数据集对象，然后通过选择 AudioSource PlayOneShot () 来分配音频剪辑。 可以使用文件夹MRTK_Select_Main MRTK_Select_Secondary音频剪辑 `/SDK/StandardAssets/Audio/` 。

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4.添加视觉状态并处理远交互事件

[可](interactable.md) 交互是一个脚本，可轻松地为各种类型的输入交互创建可视状态。 它还处理远交互事件。 添加 `Interactable.cs` 多维数据集对象并将其拖放到"配置文件"下的 **"目标"****字段** 上。 然后，创建类型为 **ScaleOffsetColorTheme 的新主题**。 在此主题下，可以指定特定交互状态（如焦点和按下）**的对象的颜色**。  还可以控制"缩放"和"偏移量"。 检查 **"缓** 动"并设置持续时间，使视觉对象转换顺畅。

![选择配置文件主题](../images/button/mrtk_button_profiles.gif)

你将看到对象同时响应远 (射线或凝视光标) 近 (和) 交互。

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>自定义按钮示例

在 [HandInteractionExample 场景中](../example-scenes/hand-interaction-examples.md)，查看同时使用 的"设置"和"圆形"按钮示例 `PressableButton` 。

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

每个密钥都分配 `PressableButton` 有 和 `NearInteractionTouchable` 脚本。 必须验证 的本地 *转发方向* `NearInteractionTouchable` 是否正确。 它由编辑器中的白色箭头表示。 请确保箭头指向按钮的正面：

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>另请参阅

* [可交互](interactable.md)
* [视觉对象主题](visual-themes.md)
