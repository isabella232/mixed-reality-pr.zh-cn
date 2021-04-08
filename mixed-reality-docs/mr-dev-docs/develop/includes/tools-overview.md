---
ms.openlocfilehash: d7e248788d4c4976acbb9ff23177d354894f57dd
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105958284"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity 徽标横幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a>1. 下载推荐的 Unity 版本 

用于 Mixed Reality 开发的最新推荐版本是 Unity 2019.4 LTS（长期支持）。 最好通过 Unity Hub 安装和管理 Unity。 

> [!NOTE]
>  如果使用 Unity 2020 LTS，则可对 HoloLens 2 开发提供 Mixed Reality 支持。 但当前有一些已知问题。 今年晚些时候，这将成为推荐的 Unity 版本。 

请参阅[选择 Unity 版本和 XR 插件](../unity/choosing-unity-version.md)，了解不同的 Unity 引擎和 XR 插件版本中提供了哪些 Mixed Reality 支持。

> [!div class="nextstepaction"]
> [下载 Unity Hub](https://unity3d.com/get-unity/download)

安装 Unity 时，请务必在“平台”下检查以下组件。
* **通用 Windows 平台生成支持** 
* **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](../../develop/images/Unity_Install_Option_UWP.png)

如果安装 Unity 时未使用这些选项，可以通过 Unity Hub 中的“添加模块”菜单添加它们。

![Unity Windows 生成支持选项](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a>2.安装混合现实功能工具

[混合现实功能工具](../unity/welcome-to-mr-feature-tool.md)是开发人员发现混合现实功能包并将其添加到 Unity 项目中的一种新方式。 

你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。 验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。

#### <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

![MRTK](../../design/images/MRTK_UX_Hero.png)

[混合现实工具包](../unity/mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。 

* 遵循下面的[安装和使用说明](../unity/welcome-to-mr-feature-tool.md#system-requirements)，选择“Mixed Reality Toolkit Foundation”包，安装混合现实工具包。

建议完成我们策划的 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 开发历程中的入门部分。 如果你已遵循针对 HoloLens 的 Unity 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unity/tutorials/mr-learning-base-01.md)。

> [!IMPORTANT]
> 请注意，安装说明面向的是 MRTK 和 Unity 版本的最新稳定组合，即 MRTK 2.6.1 和 Unity 2019.4 LTS 。

> [!NOTE]
> 如果你不想使用 MRTK for Unity，则需要[自行编写所有交互和行为的脚本](../unity/configure-unity-project.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 横幅](../images/MRTK-Unity-Banner.png)<br>**混合现实工具包 - Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>其他工具 [可选]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。 如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

#### <a name="hololens-troubleshooting"></a>HoloLens 故障排除

##### <a name="setting-developer-mode-is-grayed-out"></a>“开发人员模式”设置呈灰显

如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。 在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。 但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。

可能的解决方案包括：

* 要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式
* 建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置
* 使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。

##### <a name="i-cant-deploy-over-usb"></a>我无法通过 USB 进行部署

如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

如果你尚不熟悉使用 Unity 开发 MRTK，建议你遵循我们精心策划的 Unity 开发历程：

> [!div class="nextstepaction"]
> [开始针对 HoloLens 的 Unity历程](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [开始针对 VR 的 Unity 历程](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的针对 HoloLens 的 Unity 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。

> [!div class="nextstepaction"]
> [HoloLens 2 教程系列](../unity/tutorials/mr-learning-base-01.md)

如果你遵循针对 VR 的 Unity 历程，那么接下来是设置项目。

> [!div class="nextstepaction"]
> [针对 WMR 配置项目](../unity/configure-unity-project.md)

你可随时回到针对 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 的 Unity 开发检查点。

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1.下载最新版本

建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。

转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。   在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。
![Unreal 安装选项 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.导入混合现实工具包 (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。

对于安装，我们建议完成策划的 [Unreal 开发历程](../unreal/unreal-development-overview.md)的[入门部分](../unreal/unreal-development-overview.md#1-getting-started)。 如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](../unreal/tutorials/unreal-uxt-ch1.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)<br>**混合现实工具包 - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。

#### <a name="other-tools-optional"></a>其他工具 [可选]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。 如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

#### <a name="hololens-troubleshooting"></a>HoloLens 故障排除

##### <a name="setting-developer-mode-is-grayed-out"></a>“开发人员模式”设置呈灰显

如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。 在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。 但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。

可能的解决方案包括：

* 要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式
* 建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置
* 使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。

##### <a name="i-cant-deploy-over-usb"></a>我无法通过 USB 进行部署

如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](../unreal/tutorials/unreal-uxt-ch6.md)操作。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

如果你尚不熟悉使用 Unreal 开发 MRTK，建议你遵循我们精心策划的 Unreal 开发历程：

> [!div class="nextstepaction"]
> [开始你的 Unreal 之旅](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发检查点历程，下一项任务就是完成我们的 HoloLens 2 教程系列。

> [!div class="nextstepaction"]
> [HoloLens 2 教程系列](../unreal/tutorials/unreal-uxt-ch1.md)

你可以随时返回到 [Unreal 开发检查点](../unreal/unreal-development-overview.md#1-getting-started)。

# <a name="native-openxr"></a>[原生 (OpenXR)](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

原生 OpenXR 开发没有可供下载的引擎。 可在 [OpenXR 入门](../native/openxr-getting-started.md)文档中找到开始开发所需的全部内容。

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)进行操作。 如果打算使用 [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="hololens-troubleshooting"></a>HoloLens 故障排除

##### <a name="setting-developer-mode-is-grayed-out"></a>“开发人员模式”设置呈灰显

如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。 在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。 但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。

可能的解决方案包括：

* 要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式
* 建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。 
    * 此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置
* 使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

如果你尚不熟悉使用 MRTK 开发 Native，建议你遵循我们精心策划的 Native 开发历程：

> [!div class="nextstepaction"]
> [开始你的原生开发之旅](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Native 开发检查点历程，下一项任务就是为 HoloLens 2 配置开发环境。

> [!div class="nextstepaction"]
> [HoloLens 2 安装](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

你可以随时返回到 [Native 开发检查点](../native/directx-development-overview.md#1-getting-started)。