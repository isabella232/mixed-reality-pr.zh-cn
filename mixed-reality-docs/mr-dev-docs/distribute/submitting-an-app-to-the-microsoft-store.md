---
title: 将应用提交到 Microsoft Store
description: 探索打包、测试和将混合现实应用提交到 Microsoft Store。
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store、HoloLens、沉浸式头戴显示设备、应用、uwp、提交、提交、筛选器、元数据、系统要求、关键字、wack、认证、包、appx、merchand requirements、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197707"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>将应用提交到 Microsoft Store

> [!IMPORTANT]
> 如果要提交 Unreal 应用程序，请确保在继续之前遵循 **[发布](../develop/unreal/unreal-publishing-to-store.md)** 说明。

## <a name="prerequisites"></a>先决条件

为[沉HoloLens](/hololens/hololens1-hardware)头戴显示设备Windows 10的手机和电脑都运行[](../discover/immersive-headset-hardware-details.md)通用 Windows 平台应用。 无论你是提交支持 HoloLens 和/或电脑的应用，应用提交都通过[合作伙伴中心。](https://partner.microsoft.com/dashboard)

如果还没有一个开发人员合作伙伴中心帐户， [请注册一](https://developer.microsoft.com/store/register) 个帐户，然后再继续。 有关提交准则和清单的信息，请参阅此 [应用提交一文](/windows/uwp/publish/app-submissions)。

> [!IMPORTANT]
> 如果你的开发人员帐户未通过雇佣Microsoft Store验证检查合作伙伴中心无法将任何应用程序提交到客户。 请联系 合作伙伴中心 [支持团队](https://developer.microsoft.com/windows/support) 了解更多详细信息。

## <a name="packaging-a-mixed-reality-app"></a>打包混合现实应用

打包混合现实应用程序有几个步骤，包括：

* 正确准备所有映像资产
* 选择磁贴中显示的磁贴HoloLens "开始"菜单
* 为应用设置Windows和最低版本
* 在应用依赖项中设置目标设备系列
* 添加元数据以将应用与Microsoft Store
* 创建上传包

下面的每个提交阶段都在其各自的部分中介绍 - 建议在首次提交尝试时不留下任何内容。建议按顺序完成这些阶段。

### <a name="prepare-image-assets-included-in-the-appx"></a>准备 appx 中包含的映像资产

Appx 生成工具需要以下映像资产，才能将应用程序生成到 appx 包中，这是提交到 Microsoft Store。 可以在 MSDN 上 [详细了解磁贴和图标资产](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) 的准则。

| 必需资产 | 建议的规模 | 图像格式 | 资产显示在何处？ | 
|----------|----------|----------|------------------|
| Square 71x71 徽标 | 任意 |  PNG | 不适用 | 
| Square 150x150 徽标 | 150x150 (100% 缩放) 或 225x225 (150% 缩放)  | PNG | 如果 310x31) 0 未 (、商店搜索建议、商店列表页、商店浏览、商店搜索，则启动图钉和"所有应用"将启动 | 
|  宽 310x150 徽标 |  任意  |  PNG  |  不适用 | 
|  应用商店徽标 |  75x75 (150% 缩放)   |  PNG  |  合作伙伴中心，报表应用，编写评审，我的库 | 
|  初始屏幕 |  930x450 (150% 缩放)   |  PNG  |  2D 应用启动器 (板)  | 

如果要针对 HoloLens 进行开发，可以使用其他建议的资产：

| 建议的资产 | 建议的规模 | 资产显示在何处？ | 
|----------|----------|----------|
|  Square 310x310 徽标 |  310x310 (150% 缩放)  |  启动图钉和"所有应用" | 

### <a name="live-tile-requirements"></a>动态磁贴要求

默认情况下"开始"菜单上HoloLens将使用包含的最大正方形图块图像。 Microsoft 发布的应用具有可选的 3D 启动器，可以按照 [3D](implementing-3d-app-launchers.md) 应用启动器实现说明将其添加到应用。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定目标版本和最低版本Windows

如果混合现实应用包含特定于 Windows 版本的功能，则指定支持的目标版本和最低平台版本非常重要。

**请特别注意以沉浸式头 [戴显示设备Windows Mixed Reality](../discover/immersive-headset-hardware-details.md)的应用，它们至少需要 Windows 10 Fall Creators Update (10.0;内部版本 16299) 正常运行。**

在 Visual Studio 中创建新的通用Windows时，系统会提示你设置 Windows Project 和最低Visual Studio。 **对于** 现有项目，**可以在**"Project"菜单中选择<下拉菜单底部的"应用名称的> 属性"来更改此设置。

![设置 2019 年 Visual Studio 版本和目标平台版本](images/visual-studio-min-version-500px.png)<br>
*在 Visual Studio 中设置最低和目标平台版本*

### <a name="specifying-target-device-families"></a>指定目标设备系列

Windows Mixed Reality适用于 ([HoloLens](/hololens/hololens1-hardware)和沉浸式头戴显示设备 [](../discover/immersive-headset-hardware-details.md)) 的应用程序是通用 Windows 平台的一部分，因此任何具有 Windows **的应用包。通用**[目标设备系列](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)可以在具有沉浸式头戴显示设备HoloLens或Windows 10 PC 上运行。 如果未在应用清单中指定目标设备系列，可能会无意中打开应用，让设备Windows 10设备。 按照以下步骤指定Windows 10设备系列，然后仔细检查在 合作伙伴中心 中上传应用包以用于提交Microsoft Store设备[系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* 若要在 Visual Studio中设置此字段，请右键单击 **Package.appxmanifest** 并选择"查看代码"，然后找到 **"TargetDeviceFamily 名称"** 字段。 默认情况下，它应如以下条目所示：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* 如果要创建一个 **HoloLens** 应用，可以通过将目标设备系列设置为"HoloLens"，确保它仅安装在 **Windows。全息：** 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* 如果应用HoloLens 2眼或手部跟踪等功能，可以通过将目标设备系列设置为 Windows，确保它面向 Windows 版本 18362 **或Windows。MinVersion** 为10.0.18362.0 的全息：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* 如果为 **Windows Mixed Reality** 沉浸式头戴显示设备创建了应用，则可以通过将目标设备系列设置为 Windows，确保它仅安装在 Windows 10 PC 上，Windows 10 Fall Creators Update (**Windows Mixed Reality) 。MinVersion** 为 10.0.16299.0 的桌面：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* 最后，如果应用旨在同时在 HoloLens 和 **Windows Mixed Reality** 沉浸式头戴显示设备上运行，可以确保该应用仅适用于这两个设备系列，同时确保每个目标都有正确的最低 Windows 版本，为此，每个目标设备系列包含一行及其各自的 MinVersion：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

若要详细了解如何面向设备系列，请参阅 [TargetDeviceFamily UWP 文档](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。

### <a name="associate-app-with-the-store"></a>将应用与应用商店关联

将应用与应用Microsoft Store，以下值将下载到当前项目本地应用清单文件中：

* 包显示名称
* 包名称
* 发布者 ID
* 发行者显示名称
* 版本

如果要使用自己的自定义 .xml 文件重写默认 package.appxmanifest 文件，则不能将应用与Microsoft Store。 将自定义清单文件与 Store 关联将导致错误消息。

还可通过以下方法测试购买和通知方案：Visual Studio解决方案，然后选择"Project > **Store">"将应用与应用商店关联"。**

### <a name="creating-an-upload-package"></a>创建上传包

按照打包适用于 Windows[的通用应用中的Windows 10。](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2)

创建上传包的最后一步是使用应用程序认证工具包[Windows包](#windows-app-certification-kit)。

如果要将特定于HoloLens包添加到其他设备系列上可用的现有产品Windows 10，请注意： 

* [版本号如何影响将哪些包传送到特定客户](/windows/uwp/publish/package-version-numbering)
* [如何将包分发到不同的操作系统](/windows/uwp/publish/guidance-for-app-package-management)

一般指南是，设备版本号最高的包是由 Store 分发的包。

在存在一个 **Windows。通用** 包和 **Windows。全息包** 和Windows。通用包的版本号较高，HoloLens用户会下载更高的版本号Windows。通用包而不是Windows。全息包。 

如果上述方案不是你期望的结果，则有几个可用的解决方案：

* 确保平台特定的包，例如Windows。Holographic 的版本号始终高于平台不可知的包（如 Windows）。普遍
* 不要将应用打包为Windows。通用（如果还有特定于平台的包） - 改为打包Windows。适用于希望其用于的特定平台的通用包
* 创建单个Windows。跨所有平台工作的通用包。 目前对此选项的支持并不大，因此建议使用上述解决方案。

>[!NOTE]
> 若要在 HoloLens (Gen) 和 HoloLen 2 上支持应用，需要上传两个应用包;一个包含 x86 for HoloLens (第一代) ，另一个包含 ARM 或 ARM64 for HoloLens 2。 
> 
> 如果包中同时包含 ARM 和 ARM64，则 ARM64 版本将是在 HoloLens 2。 

>[!NOTE]
> 可以声明单个包以适用于多个目标设备系列

## <a name="testing-your-app"></a>测试应用程序

### <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

创建要通过 合作伙伴中心 提交到 Visual Studio 的应用包时，"创建应用包"向导会提示你针对创建的包运行 Windows 应用认证工具包。 若要顺利提交到应用商店，最好先验证应用的本地副本是否通过了[Windows 应用认证工具包](/previous-versions/windows/apps/jj657973(v=win.10))测试，然后再将其提交到 Store。 目前Windows远程HoloLens应用程序认证工具包。

### <a name="run-on-all-targeted-device-families"></a>在所有目标设备系列中运行

使用Windows通用平台，可以创建跨所有设备系列运行的Windows 10应用程序。 但是，它并不保证通用Windows应用在所有设备系列上都正常工作。 在每个所选 [设备](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) 系列上测试应用以确保良好的体验非常重要。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>将混合现实应用提交到应用商店

如果要提交基于 Unity 项目的混合现实应用，请首先 [观看此视频](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 。

通常，提交适用于 Windows Mixed Reality 头戴显示设备或沉浸式头戴显示设备HoloLens就像将任何 UWP 应用提交到 Microsoft Store。 通过保留应用 [名称](/windows/uwp/publish/create-your-app-by-reserving-a-name)创建应用后，请遵循 [UWP 提交清单](/windows/uwp/publish/app-submissions)。

首先需要为混合现实体验选择类别和子[](/windows/uwp/publish/category-and-subcategory-table)类别。 为应用 选择最 **准确的类别非常重要**。 类别有助于将应用程序显示在正确的 Store 类别中，并确保它使用相关的搜索查询显示。 **将 VR 标题作为** 游戏列出不会为应用带来更好的曝光，并且可能会阻止它显示在更合适且不太人满的类别中。

但是，在提交过程中有四个关键区域需要做出特定于混合现实的选择：
1. 在" **[产品声明"部分中的](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** "属性 ["下](/windows/uwp/publish/enter-app-properties)。
2. 在" **[系统要求"部分](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 中的"属性 ["下](/windows/uwp/publish/enter-app-properties)。
3. 在" **[包"下的"](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 设备系列可用性 ["部分](/windows/uwp/publish/upload-app-packages)。
4. 在一些Store 一览 **[页](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 字段。

### <a name="mixed-reality-product-declarations"></a>混合现实产品声明

在 **[应用提交](/windows/uwp/publish/enter-app-properties)** 过程的"属性"页上，"产品声明"部分提供了多个与混合 **[现实相关的](/windows/uwp/publish/app-declarations)** 选项。

![混合现实产品声明](images/product-declarations-900px.png)<br>
混合现实产品声明

首先，需要确定应用提供混合现实体验的设备类型。 标识设备类型可确保应用包含在应用商店Windows Mixed Reality集合中。

在"此体验适用于Windows Mixed Reality旁边：
* 当 **沉浸** 式头戴显示设备连接到用户的电脑时，如果应用提供 VR 体验，请选中"电脑"框。 建议选中此框，确定应用是否设置为在沉浸式头戴显示设备上以独占方式运行，还是设置为在连接头戴显示设备时提供混合现实模式或额外内容的标准电脑游戏或应用。
* 仅在 **HoloLens** 应用运行时提供全息体验时，才选中"HoloLens" 框。
* 如果 **应用** 在这两种设备类型上提供混合现实体验，请选中这两个框。

如果选择了上面的"电脑"，需要将"混合现实设置"设置为 (级别) 。 这仅适用于在连接到沉浸式头戴显示设备 PC 上运行的混合现实体验，因为 HoloLens 上的混合现实应用是全球规模的，并且用户在安装过程中不会定义边界。
* 如果你 **将应用** 设计为让用户停留在一个位置，请选择"固定 + 站"。 例如，在控制飞机驾驶舱的游戏中。
* 如果 **应用** 的设计目的是让用户在设置过程中定义的设置边界内四处移动，请选择"所有体验"。 例如， 可能是一个游戏，你可在这里避免遭受攻击。

### <a name="mixed-reality-system-requirements"></a>混合现实系统要求

在 **[应用提交](/windows/uwp/publish/enter-app-properties)** 过程的"属性"页上，你将在"系统要求"部分找到多个与混合 **[现实相关的](/windows/uwp/publish/enter-app-properties#system-requirements)** 选项。

![系统要求](images/system-reqs-800px.png)<br>
系统要求

在本部分，你将确定混合现实 () 所需的最低 () 可选硬件。

**输入硬件：**

使用复选框告知潜在客户你的应用是否支持麦克风进行语音 **[) 、Xbox](../discover/hardware-accessories.md#bluetooth-gamepads)**[](../design/voice-input.md)控制器或游戏板，或者Windows Mixed Reality **[控制器](../design/motion-controllers.md)**。 此信息将显示于应用商店中应用的产品详细信息页上，可帮助应用包含在相应的应用/游戏集合中。 例如，支持运动控制器的所有游戏可能存在集合。

对于为输入类型选择"最低硬件"或"推荐硬件"复选框时，要十分周密。 

例如： 
* 如果游戏需要运动控制器，但通过麦克风接受语音输入，请选中"Windows Mixed Reality运动控制器"旁边的"最低硬件"复选框，但选中"麦克风"旁边的"推荐硬件"复选框。 
* 如果游戏可以使用 Xbox 控制器、游戏板或运动控制器进行播放，可以选择"Xbox 控制器或游戏板"旁边的"最低硬件"复选框，并选择"Windows Mixed Reality 运动控制器"旁边的"推荐硬件"复选框，因为运动控制器可能会提供从游戏板升级的体验。

**Windows Mixed Reality沉浸式头戴显示设备：**

指示沉浸式头戴显示设备是使用应用所需的，还是可选，对于客户满意度和教育至关重要。

如果应用只能 *通过* 沉浸式头戴显示设备使用，请选中"沉浸式头戴显示设备"旁边的"Windows Mixed Reality"复选框。 这将在应用商店的应用产品详细信息页上显示，作为购买按钮上方的警告，因此客户不会认为他们购买的应用将像传统桌面应用一样在电脑上运行。

如果应用像传统电脑应用一样在桌面上运行，但在连接沉浸式头戴显示设备时提供 VR 体验 (无论应用的完整内容是否可用，还是只有一部分) ，请选择"Windows Mixed Reality 沉浸式头戴显示设备"旁边的"推荐硬件"复选框。 如果应用在未连接沉浸式头戴显示设备的情况下作为传统桌面应用运行，则应用产品详细信息页上的"购买"按钮上方不会显示任何警告。

**电脑规格：**

如果希望应用访问尽可能多Windows Mixed Reality沉浸式头戴显示设备用户，请针对具有集成图形[](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) [Windows Mixed Reality电脑的电脑规格](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

无论混合现实应用面向最低 Windows Mixed Reality PC 要求，还是需要特定电脑配置（如 [Windows Mixed Reality Ultra PC] (的专用 GPU），都应在"最低硬件"列中添加相关的 https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines 电脑规格。

如果混合现实应用旨在提高性能，或提供特定电脑配置或图形卡上更高分辨率的图形，应在"建议的硬件"列中包含相关的电脑规格。

这仅适用于混合现实应用使用连接到电脑的沉浸式头戴显示设备的情况。 如果混合现实应用仅在 HoloLens 上运行，则无需指示电脑规格，因为HoloLens只有一个硬件配置。

### <a name="device-family-availability"></a>设备系列可用性

如果已正确[将应用](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)打包到 Visual Studio，则将其上传到"包"页上应会生成一个包含可用设备系列的表。

![设备系列可用性表](images/device-family-table-900px.png)<br>
设备系列可用性表

如果混合现实应用适用于沉浸式头戴显示设备，则至少应在表中选择Windows 10桌面"。 如果混合现实应用适用于HoloLens，则至少应Windows 10 全息版"应用"。 如果应用在两种头戴显示设备Windows Mixed Reality上运行，应同时选择"Windows 10桌面"和"Windows 10 全息版"。

>[!TIP]
>许多开发人员在上传其应用的包时遇到错误，因为包清单与应用中的应用/发布者帐户信息合作伙伴中心。 通常可以通过使用与 Windows 开发人员帐户关联的Visual Studio帐户登录 (，避免这些错误合作伙伴中心) 。 如果使用相同的帐户，可以在打包应用之前将应用与Microsoft Store标识关联。

![将应用与应用Microsoft Store](images/associate-your-app-700px.png)<br>
将应用与 Microsoft Store 中的Visual Studio

### <a name="store-listing-page"></a>Store 一览页

在 [Store 一览](/windows/uwp/publish/create-app-store-listings) 的"应用提交"页上，可以在多个位置添加有关混合现实应用的有用信息。

>[!IMPORTANT]
>若要确保应用按应用商店正确分类，使 Windows Mixed Reality 客户能够发现应用，应添加 **"Windows Mixed Reality"** 作为应用的"搜索词"之一 (可通过展开"共享字段"部分来查找搜索词) 。

![将Windows Mixed Reality添加到搜索词](images/search-terms-800px.png)<br>
将"Windows Mixed Reality"添加到搜索词

## <a name="offering-a-free-trial-for-your-game-or-app"></a>为游戏或应用提供免费试用版

在许多情况下，在购买沉浸式头戴显示设备之前，使用者只能体验Windows Mixed Reality体验。 他们可能不知道在密集游戏中会有什么期望，或者不熟悉自己沉浸式体验中的舒适阈值。 许多客户可能还尝试在未Windows Mixed Reality PC 上使用沉浸式头戴显示设备Windows Mixed Reality[头戴显示设备](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。 出于这些考虑，我们强烈建议你考虑为付费混合现实应用或[](/windows/uwp/publish/set-app-pricing-and-availability#free-trial)游戏提供免费试用版。

## <a name="see-also"></a>另请参阅
* [什么是混合现实？](../discover/mixed-reality.md)
* [开发概述](../develop/development.md)
* [应用视图](../design/app-views.md)
* [了解混合现实的性能](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 推荐性能](../develop/unity/performance-recommendations-for-unity.md)
* [在 HoloLens 上测试应用](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)