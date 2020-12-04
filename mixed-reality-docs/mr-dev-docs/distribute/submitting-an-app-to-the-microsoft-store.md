---
title: 将应用提交到 Microsoft Store
description: 探讨将混合现实应用打包、测试和提交到 Microsoft Store 的过程。
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store，HoloLens，沉浸式耳机，应用，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 1d37337279e46e5f0f9d5cea82813af8de9d0f76
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578896"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>将应用提交到 Microsoft Store

> [!IMPORTANT]
> 如果你正在提交 Unreal 应用程序，请确保在此处按照 **[发布说明](../develop/unreal/unreal-publishing-to-store.md)** 操作，然后再继续。

[HoloLens](../hololens-hardware-details.md)和 WINDOWS 10 PC 均支持[沉浸式耳机](../discover/immersive-headset-hardware-details.md)运行通用 Windows 平台应用。 无论是提交支持 HoloLens、PC 还是同时提交这两种应用，都可以通过 [合作伙伴中心](https://partner.microsoft.com/dashboard)进行应用提交。

如果还没有合作伙伴中心开发人员帐户，请在继续之前 [注册](https://developer.microsoft.com/store/register) 一个。

## <a name="packaging-a-mixed-reality-app"></a>打包混合现实应用

打包混合现实应用程序的步骤包括：

* 正确准备所有映像资产
* 选择在 "HoloLens 开始" 菜单中显示的磁贴图像
* 设置应用的目标和最低 Windows 版本
* 在应用程序依赖项中设置目标设备系列
* 添加元数据以将应用与 Microsoft Store
* 创建上传包

以下每个提交阶段都包含在下面的部分中，我们建议你在第一次提交尝试时不留下任何内容。

### <a name="prepare-image-assets-included-in-the-appx"></a>准备包含在 appx 中的映像资产

Appx 构建工具需要以下图像资产，以便将应用程序构建到 appx 包中，这对于提交到 Microsoft Store 是必需的。 你可以在 MSDN 上详细了解 [磁贴和图标资产的准则](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) 。

| 所需资产 | 建议的缩放 | 图像格式 | 资产显示在哪个位置？ | 
|----------|----------|----------|------------------|
| 方块字71x71 徽标 | 任意 |  PNG | 不可用 | 
| 方块字150x150 徽标 | 150x150 (100% 规模) 或 225x225 (150% 规模)  | PNG | 如果未提供310x310，则启动 pin 和所有应用 () ，存储搜索建议，商店列表页，商店浏览，存储搜索 | 
|  宽310x150 徽标 |  任意  |  PNG  |  不可用 | 
|  应用商店徽标 |  75x75 (150% 规模)   |  PNG  |  合作伙伴中心，报表应用，编写评审，我的媒体库 | 
|  初始屏幕 |  930x450 (150% 规模)   |  PNG  |  2D 应用启动器 (盖板)  | 

如果正在开发 HoloLens，还可以利用其他建议资产：

| 推荐的资产 | 建议的缩放 | 资产显示在哪个位置？ | 
|----------|----------|----------|
|  方块字310x310 徽标 |  310x310 (150% 规模)  |  启动 pin 和所有应用 | 

### <a name="live-tile-requirements"></a>动态磁贴要求

默认情况下，HoloLens 上的 "开始" 菜单将使用最大的包含正方形磁贴图像。 Microsoft 发布的应用具有可选的3D 启动器，你可以按照 [3d 应用启动器实现](implementing-3d-app-launchers.md) 说明将其添加到应用。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定 Windows 的目标和最低版本

如果混合现实应用包含特定于 Windows 版本的功能，则必须指定支持的目标和最低平台版本。

**对于面向 [Windows Mixed Reality 沉浸式耳机](../discover/immersive-headset-hardware-details.md)的应用，请特别注意，这需要至少 Windows 10 秋季创意者更新 (10.0;生成 16299) 可以正常工作。**

当你在 Visual Studio 中创建新的通用 Windows 项目时，系统将提示你设置 Windows 的目标和最低版本。 对于现有项目，可以在 " **项目** " 菜单中选择 " **<您的应用程序名称** 在下拉菜单底部的> 属性。

![在 Visual Studio 2019 中设置最低和目标平台版本](images/visual-studio-min-version-500px.png)<br>
*在 Visual Studio 中设置最低平台版本和目标平台版本*

### <a name="specifying-target-device-families"></a>指定目标设备系列

适用于 [hololens](../hololens-hardware-details.md)和 [沉浸式耳机](../discover/immersive-headset-hardware-details.md)) 的 Windows Mixed Reality 应用程序 (是通用 Windows 平台的一部分，因此具有 **Windows 通用**[目标设备系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)的任何应用包都可以通过沉浸式耳机在 HoloLens 或 windows 10 电脑上运行。 如果未在应用程序清单中指定目标设备系列，可能会无意中打开应用程序，使其不会出现意外的 Windows 10 设备。 按照以下步骤指定所需的 Windows 10 设备系列，然后在 ["合作伙伴 Microsoft Store 中心" 中上传应用程序包时，请仔细检查是否设置了正确的设备系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* 若要在 Visual Studio 中设置此字段，请右键单击 **appxmanifest.xml** 并选择 " **查看代码**"，然后找到 " **y 名称** " 字段。 默认情况下，它应类似于以下条目：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* 如果创建的是 **hololens** 应用，则可以通过将目标设备系列设置为 Windows，确保它仅在 HoloLens 上安装 **。全息** 版： 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* 如果你的应用需要 **HoloLens 2** 功能，如目视或手动跟踪，则可以通过将目标设备系列 **设置为适用于 windows 版本** 18362 或更高 **版本的 10.0.18362.0** ，确保它面向 windows 版本或更高版本：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* 如果你的应用是为 **Windows Mixed reality 沉浸式耳机** 创建的，则可以确保它仅安装在 Windows 10 计算机上，并通过 Windows 10 秋季创意者更新 (Windows Mixed Reality) **通过将目标** 设备系列 **设置为 10.0.16299.0** ：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* 最后，如果你的应用程序应在 **HoloLens** 和 **Windows Mixed Reality 沉浸式耳机** 上运行，你可以确保此应用仅适用于这两个设备家族，同时确保每个目标都具有正确的最低 Windows 版本，方法是为每个目标设备系列包含其各自的 MinVersion：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

若要了解有关面向设备家族的详细信息，请阅读 [y UWP 文档](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。

### <a name="associate-app-with-the-store"></a>将应用与应用商店关联

当你将应用程序与 Microsoft Store 相关联时，以下值将下载到当前项目本地应用程序清单文件中：

* 包显示名称
* 包名称
* 发布者 ID
* 发行者显示名称
* 版本

如果用自己的自定义 .xml 文件覆盖默认的 appxmanifest.xml 文件，则不能将应用程序与 Microsoft Store 相关联。 将自定义清单文件与应用商店关联将导致错误消息。

你还可以通过转到 Visual Studio 解决方案并选择 " **Project > Store > 将应用与应用商店关联** 来测试购买和通知方案。

### <a name="creating-an-upload-package"></a>创建上传包

按照 [打包适用于 windows 10 的通用 windows 应用程序中的](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)准则。

创建上传包的最后一步是使用 [Windows 应用认证](#windows-app-certification-kit)包验证包。

如果要将特定于 HoloLens 的包添加到其他 Windows 10 设备家族上可用的现有产品，请注意以下事项： 

* [版本号可能如何影响向特定客户发送的包](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)
* [如何将包分发到不同的操作系统](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)

一般指导原则是，设备中版本号最高的包是存储区分发的包。

在出现 **Windows 通用** 包和 **windows 全息** 包的情况下，如果 windows 通用包具有较高的版本号，则 HoloLens 用户将下载较高的版本号 windows 通用包而不是 windows 全息包。 

如果上述方案不是你要寻找的结果，则可以使用以下几种解决方案：

* 确保特定于平台的包（如 Windows. 全息）的版本号比平台无关包（如 Windows 通用）的版本号更高。
* 不要将应用打包为 Windows。如果你还具有特定于平台的包，请将 Windows 通用包打包为你要在其上可用的特定平台
* 创建跨所有平台工作的单个 Windows 通用包。 目前尚不支持此选项，因此建议使用上述解决方案。

>[!NOTE]
> 若要在 HoloLens (第一代) 和 HoloLen 2 上支持你的应用，你需要上传两个应用包;一个包含 x86 for HoloLens (第一代) ，一个包含 ARM 或 ARM64 （适用于 HoloLens 2）。 
> 
> 如果在包中同时包含 ARM 和 ARM64，则 ARM64 版本将是在 HoloLens 2 上使用的版本。 

>[!NOTE]
> 可以声明单个包，使其适用于多个目标设备系列

## <a name="testing-your-app"></a>测试应用程序

### <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

通过 Visual Studio 创建要提交到合作伙伴中心的应用包时，"创建应用程序包" 向导会提示你针对创建的包运行 Windows 应用认证工具包。 若要对应用程序进行平滑提交，最好先验证应用的本地副本是否通过 [Windows 应用认证包测试](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) ，然后再将其提交到应用商店。 当前不支持在远程 HoloLens 上运行 Windows 应用程序认证包。

### <a name="run-on-all-targeted-device-families"></a>在所有目标设备系列上运行

使用 Windows 通用平台，您可以创建跨所有 Windows 10 设备系列运行的单一应用程序。 但是，它并不保证通用 Windows 应用程序将只在所有设备家族上工作。 在所选的每个设备家族上 [测试您的应用程序](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) 很重要，以确保获得良好的体验。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>将混合现实应用提交到应用商店

如果要提交基于 Unity 项目的混合现实应用，请先参阅此 [视频](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 。

通常，提交在 HoloLens 和/或沉浸式耳机上运行的 Windows Mixed Reality 应用就像将任何 UWP 应用提交到 Microsoft Store。 [通过保留应用名称创建应用](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)后，请遵循[UWP 提交清单](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

你要做的第一项工作就是为混合现实体验 [选择一个类别和子](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) 类别。 **请务必为应用选择最准确的类别**。 类别可帮助将应用程序商品置于正确的存储类别中，并确保它使用相关搜索查询显示。 将 **您的 VR 标题列为游戏不会导致您的应用程序的曝光更好，** 可能会阻止其显示在更具可容纳性和更少的类别中。

但在提交过程中，有四个重要方面需要进行特定于现实的特定选择：
1. 在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 "**[产品声明](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)**" 部分。
2. 在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 "**[系统要求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)**" 部分。
3. "[包](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)" 下的 "**[设备系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)**" 部分。
4. 几个 **[商店列表页](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 字段。

### <a name="mixed-reality-product-declarations"></a>混合现实产品声明

在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[产品声明](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** " 部分中找到几个与混合现实相关的选项。

![混合现实产品声明](images/product-declarations-900px.png)<br>
混合现实产品声明

首先，需要确定应用为其提供混合现实体验的设备类型。 标识设备类型可确保应用包含在应用商店中的 Windows Mixed Reality 集合中。

"这一体验是针对 Windows Mixed Reality 设计的："
* 如果你的应用程序在沉浸式耳机连接到用户的 PC 时提供了 VR 体验，请选中 " **电脑** " 框。 建议选中此框，无论你的应用程序设置为在沉浸式耳机上以独占方式运行，还是在连接了耳机时提供混合现实模式和/或附赠内容。
* 仅当你的应用程序在 HoloLens 上运行时提供了全息体验时，才检查 **hololens** 框。
* 如果你的应用在这两个设备类型上都提供混合现实体验，请选中 **这两个** 框。

如果选择上述 "PC"，则需要将 "混合现实设置" (活动级别) 。 这仅适用于在连接到沉浸式头设备的 Pc 上运行的混合现实体验，因为 HoloLens 上的混合现实应用是全球规模的，用户在安装过程中未定义边界。
* 如果你设计的应用程序位于同一位置，请选择 " **固定 +** 上"。 例如，在你掌控飞机考核中心的游戏中。
* 如果你的应用程序的设计目的是让用户在安装过程中定义的集边界内进行浏览，则选择 " **所有体验** "。 例如，可能是一项游戏，你可以在其中进行逐步操作并对减减减攻击。

### <a name="mixed-reality-system-requirements"></a>混合现实系统要求

在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[系统要求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** " 部分中找到几个与混合现实相关的选项。

![系统要求](images/system-reqs-800px.png)<br>
系统要求

在本部分中，你将确定) 硬件所需的最小 (，以及建议用于混合现实应用的 (可选) 硬件。

**输入硬件：**

如果应用支持 [语音输入](../design/voice-input.md)) 、 **[Xbox 控制器或游戏板](../discover/hardware-accessories.md#bluetooth-gamepads)** 和/或 **[Windows Mixed Reality 运动控制器](../design/motion-controllers.md)** 的 **麦克风**，请使用复选框来告知潜在客户。 此信息将显示在应用商店中的应用的 "产品详细信息" 页上，可帮助你的应用包含在适当的应用/游戏集合中。 例如，对于支持运动控制器的所有游戏，都可能存在一个集合。

为输入类型选择 "最低硬件" 或 "推荐的硬件" 复选框。 

例如： 
* 如果游戏需要运动控制器，但通过麦克风接受语音输入，请选择 "Windows Mixed Reality 运动控制器" 旁边的 "最小硬件" 复选框，但 "麦克风" 旁边的 "推荐的硬件" 复选框。 
* 如果可以使用 Xbox 控制器、游戏板或运动控制器播放游戏，则可以选择 "Xbox 控制器或游戏板" 旁边的 "最小硬件" 复选框，并选择 "Windows Mixed Reality 运动控制器" 旁边的 "推荐的硬件" 复选框，因为运动控制器可能会在游戏板上提供一个步骤。

**Windows Mixed Reality 沉浸式耳机：**

指示是否需要沉浸式耳机来使用你的应用，或是否可选，这对于客户满意度和教育至关重要。

如果你的应用 *只能* 通过沉浸式耳机使用，请选择 "Windows Mixed Reality 沉浸式耳机" 旁边的 "最小硬件" 复选框。 这会显示在应用程序中应用程序的产品详细信息页上，在 "购买" 按钮上显示为警告，因此客户不会认为他们购买的应用程序将在其电脑上运行，如传统桌面应用程序。

如果你的应用程序在桌面上运行，如传统的 PC 应用程序，但在连接沉浸式头戴式耳机时提供了 VR 体验 (你的应用的完整内容是否可用，或者仅) 部分，请选中 "Windows Mixed Reality 沉浸式耳机" 旁边的 "推荐的硬件" 复选框。 如果你的应用程序在未连接沉浸式头戴式的情况下作为传统桌面应用程序运行，则不会出现任何警告。

**PC 规范：**

如果你希望你的应用程序尽可能多地访问 Windows Mixed reality 沉浸式耳机用户，请将适用于[Windows Mixed Reality 电脑](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 PC 规格作为集成图形[定位](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

无论你的混合现实应用程序是以最低的 Windows Mixed Reality PC 需求为目标还是需要特定的 PC 配置（如 [Windows Mixed Reality 超 PC] (的专用 GPU https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines ），都应该在 "最低硬件" 列中添加相关的 pc 规范。

如果混合现实应用旨在提供更好的性能，或在特定 PC 配置或图形卡上提供更高分辨率的图形，则应在 "推荐的硬件" 列中包含相关的 PC 规范。

仅当混合现实应用使用连接到电脑的沉浸式头戴式耳机时，此情况才适用。 如果混合现实应用仅在 HoloLens 上运行，则无需指示 PC 规范，因为 HoloLens 只有一个硬件配置。

### <a name="device-family-availability"></a>设备系列可用性

如果已在 Visual Studio 中 [正确打包了应用](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) ，则在 "包" 页上上传该应用时，应生成包含可用设备系列的表。

![设备家族可用性表](images/device-family-table-900px.png)<br>
设备家族可用性表

如果混合现实应用适用于沉浸式耳机，则应在表中选择至少 "Windows 10 桌面"。 如果你的混合现实应用在 HoloLens 上工作，则应至少选择 "Windows 10 全息版"。 如果你的应用在两个 Windows Mixed Reality 耳机类型上运行，则应选择 "Windows 10 桌面" 和 "Windows 10 全息版"。

>[!TIP]
>许多开发人员在上载其应用包时出现错误，这些错误与 "合作伙伴中心" 中的包清单与你的应用/发布者帐户信息的不匹配相关。 使用与您的 Windows 开发人员帐户关联的同一帐户登录到 Visual Studio （ (用于登录到合作伙伴中心) 的帐户）通常可以避免这些错误。 如果你使用相同的帐户，则在打包应用程序之前，你可以将应用与其在 Microsoft Store 中的标识相关联。

![将你的应用与 Microsoft Store](images/associate-your-app-700px.png)<br>
在 Visual Studio 中将应用与 Microsoft Store 相关联

### <a name="store-listing-page"></a>商店列表页

在应用提交过程的 "应用 [商店列表](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) " 页上，可以添加有关混合现实应用的有用信息。

>[!IMPORTANT]
>若要确保应用程序正确地分类了应用程序并将其视为 Windows Mixed Reality 客户，应将 **"Windows Mixed Reality"** 添加为应用的 "搜索词"， (可以通过展开 "共享字段" 部分) 来查找搜索词。

![将 Windows Mixed Reality 添加到搜索词](images/search-terms-800px.png)<br>
向搜索词添加 "Windows Mixed Reality"

## <a name="offering-a-free-trial-for-your-game-or-app"></a>为游戏或应用提供免费试用版

在许多情况下，使用者在购买 Windows Mixed Reality 沉浸式耳机之前，将不会受到虚拟现实的经验限制。 他们可能不知道从重要游戏中获得的内容，或者在沉浸式体验中熟悉自己的舒适阈值。 许多客户还可能会尝试在未徽章为 [Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的电脑上使用 Windows mixed reality 沉浸式耳机。 出于上述考虑，强烈建议您考虑为付费混合现实应用或游戏提供 [免费试用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 。

## <a name="see-also"></a>另请参阅
* [什么是混合现实？](../discover/mixed-reality.md)
* [开发概述](../develop/development.md)
* [应用视图](../design/app-views.md)
* [了解混合现实的性能](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 性能建议](../develop/unity/performance-recommendations-for-unity.md)
* [在 HoloLens 上测试应用](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
