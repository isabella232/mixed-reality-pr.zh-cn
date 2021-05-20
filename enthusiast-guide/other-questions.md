---
title: 沉浸式硬件面临常见问题
description: 其他 Windows Mixed Reality 疑难解答技巧超出了标准使用者支持文档。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，卸载 Windows Mixed Reality，支持的语言
appliesto:
- Windows 10
ms.openlocfilehash: ede2620ca6a47b085a3d7b54fd6df073bfaa528e
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196592"
---
# <a name="other-questions"></a>其他问题

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>我的图形驱动程序不受支持 (我) 出现图形驱动程序故障错误。

搜索并运行 "dxdiag"：

1.  如果结果为 "基本呈现器"，则不安装图形驱动程序。 解决方法：
    * 请参阅 **Device Manager > 操作 > 扫描硬件更改**。
    * 使用 Windows 更新更新驱动程序。
    * 如果这不能解决问题，请前往制造商的网站并安装最新的驱动程序更新。 
    * 如果更新不适用于 GPU，则设备上可能不支持 WMR。 如果你认为它应为，请联系 [支持人员](https://support.microsoft.com)。
2.  如果收到 "WDDM 2.1" 或更低版本，则会安装图形驱动程序，但它可能不是最新版本。 获取最新版本：
    * 使用 Windows 更新更新驱动程序。
    * 如果该更新未解决此问题，请前往制造商的网站并安装最新的驱动程序更新。 
    * 如果更新不适用于 GPU，则设备上可能不支持 WMR。 如果你认为它应为，请联系 [支持人员](https://support.microsoft.com)。

如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>我的 Samsung 太空或太空 + 耳机固件更新停滞。

Samsung 拥有并发布通过其 "Samsung HMD 太空安装程序" 和 "Samsung HMD 太空 + Setup" 设备配套应用交付的耳机固件更新。 有关更多详细信息和有关 Samsung 固件更新问题的帮助，请联系 Samsung 客户服务。

如果固件更新过程停滞，并且超过五分钟没有进度：

* 暂时拔下所有其他 USB 设备，然后重试固件更新。
* 将 Samsung 头戴显示设备连接到电脑上的不同 USB 3.0 端口。
* 禁用或卸载安装的任何可能会干扰固件更新的软件，例如 GB 的 AORUS App Center。
* 使用不同的电脑更新 Samsung 头戴显示设备固件。

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>如何实现混合现实访问我的电脑桌面？
从 Windows 按钮启动头戴显示设备中的桌面应用 **>"** 所有>桌面"，以混合现实访问电脑桌面。

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>如何在混合现实中查看多个监视器

默认情况下，桌面应用会自动切换以显示具有焦点的监视器。 如果要在混合现实中查看所有监视器：

* 选择应用左上角的监视器图标。
* 禁用"自动切换监视器"。
* 选择想要查看的监视器。
* 启动桌面应用的另一个实例。
* 选择想要在实例上查看的监视器。
* 针对所有物理监视器重复上述步骤。
每次重启混合现实时，必须重新选择监视器以显示在每个桌面应用上。

## <a name="my-desktop-app-only-shows-a-black-screen"></a>我的桌面应用只显示黑屏

如果电脑具有 Nvidia 混合 GPU，则运行 runtimebroker.exe GPU（而不是集成 GPU）上的 Nvidia 设备可能是问题所在。 若要解决此问题，请按照以下说明操作，如何实现程序创建[Optimus 设置？"](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F) 以添加C:\windows\system32\runtimebroker.exe并强制它在"集成图形"处理器上运行。 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>使用Wi-Fi时，我的Windows Mixed Reality。

如果使用 2.4-GHz Wi-Fi，运动控制器可能会降低 Wi-Fi 的速度：

* 切换到 5 GHz Wi-Fi（如果有）。 [了解详细信息](https://support.microsoft.com/help/4000461)。
* 使用单独的蓝牙适配器将运动控制器连接到电脑。 请参阅 [建议的适配器](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一条消息，指出要插入电脑并收取电脑费用。 为什么？

如果使用的是笔记本电脑，则Windows Mixed Reality完全充电和接通电源时，设备性能最佳。

## <a name="what-is-the-experience-options-setting"></a>什么是体验选项设置？

**使用>混合现实>">体验** "选项，可以更改Windows Mixed Reality设置。 这样，你可在一系列内容中选择硬件配置的最佳体验。 有三个体验选项可供选择：
* 自动：Windows Mixed Reality将确定硬件配置的最佳体验。 对于大多数人来说，这是一开始的最佳选择。
* 60 Hz：将刷新速率设置为 60 Hz，并关闭某些功能，例如视频捕获和预览混合现实门户。
* 90 Hz：将刷新速率设置为 90 Hz。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>支持哪些语言Windows Mixed Reality

Windows Mixed Reality以下语言提供以下语言：

* 简体中文（中国）
* 英语（澳大利亚）
* 英语（加拿大）
* 英语（英国）
* 英语（美国）
* 法语（加拿大）
* 法语（法国）
* 德语（德国）
* 意大利语（意大利）
* 日语（日本）
* 西班牙语(墨西哥)
* 西班牙语(西班牙)

如果电脑设置为Windows Mixed Reality，可以使用其他语言。 但是，界面将以英语 (美国) ，并且语音命令和听写将不可用。 Windows Mixed Reality 屏幕键盘仅适用于英语 (美国) 。 若要以另一种语言输入文本，请使用连接到电脑的物理键盘。 你还可以使用上面列出的受支持的 Windows Mixed Reality 语言之一来使用听写，只需在屏幕键盘上选择 "麦克风" 即可。

Windows Mixed Reality 还提供以下语言版本，无需语音命令或听写功能：
* 繁体中文 (台湾和中国香港) 
* 荷兰语（荷兰）
* 韩语(韩国)
* 俄语（俄罗斯）

## <a name="i-have-questions-about-my-headset-hardware"></a>我对我的耳机硬件有疑问。

有关手机支持的详细信息，请咨询制造商。 可以在框中提供产品指南，也可以尝试使用制造商的网站。

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何实现卸载 Windows Mixed Reality？

1. 断开耳机与电脑的连接。
2. 关闭 Windows Mixed Reality 门户。
2. 请参阅  **开始 > 设置 > Mixed Reality** ，然后选择 "卸载"。

如果已准备好开始使用头戴显示，请将其插入，Windows Mixed Reality 门户将引导你完成安装过程。

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>我收到了 "我们无法完成 Windows Mixed Reality 的卸载" 消息。

某些文件（包括有关您的环境的信息）可能仍在您的计算机上。 如果你决定稍后重新安装 Windows Mixed Reality，这可能会导致问题。 你可以通过修改注册表并使用 Windows PowerShell 来运行命令，从你的电脑中手动删除任何剩余的 Windows Mixed Reality 信息。 _如果不正确地修改注册表，则可能会出现严重问题。请确保仔细执行这些步骤。为了增加保护，请在修改注册表之前对其进行备份，以便在出现问题时对其进行还原。_ 有关详细信息，请参阅 [如何在 Windows 中备份和 restory 注册表](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。 

若要使用这些命令卸载 Windows 混合现实，请执行以下命令：
1. 重启你的电脑。
2. 在" **搜索"** 框中，键入"regedit"，然后选择"是"。
3. 删除以下注册表值：
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然后删除"FirstRunSucceeded"。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>，然后删除"PreferDesktopSpeaker"和"PreferDesktopMic"。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; 设置\全息</b>，然后删除"DisableSpeechInput"。 注意：必须为已使用 HHKEY_CURRENT_USER 的 PC 上的每个用户帐户删除 Windows Mixed Reality。</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>，然后删除"DeviceID"和"Mode"。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然后删除"OnDeviceLearningCompleted"。</li> 
   </ul>
4. 删除以下注册表项： <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. 关闭注册表编辑器。
6. 转到 **C：\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** 并删除"RoomBounds.json"。 对已使用 Windows Mixed Reality 的每个用户重复Windows Mixed Reality。
7. 打开管理员 cmd 提示符并转到 **C：\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**。 删除"HeadTracking 数据"文件夹的内容 (但文件夹本身不会) 。
8. 在"搜索框"中键入"powershell"，右键单击"Windows PowerShell"，然后选择"以管理员角色运行"。
9. 在Windows PowerShell： <ul>
   <li>在命令提示符处，复制并粘贴 <b>Dism/Online/Get-Capabilities</b>，然后按 enter。</b></li> 
   <li>复制以模拟开头的功能标识。 如果未安装，则不安装该项，你可以跳到步骤 10) 。</li> 
   <li>复制并粘贴以下命令提示符，然后按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在上一步中复制的功能标识</b></li>
   </ul>
10. 重启电脑。

