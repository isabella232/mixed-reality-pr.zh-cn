---
title: 发布到 Microsoft Store
description: 了解如何打包、认证 Unreal 混合现实应用程序，以及如何将它们发布到 Microsoft Store。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 发布, 分发, Microsoft Store
ms.openlocfilehash: 2e0e628439c187d787fe64902cbb9a17d617559623d90830ef4a57f6c7b34338
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226250"
---
# <a name="publishing-to-the-microsoft-store"></a>发布到 Microsoft Store

若已准备好对外发布你的 Unreal 应用，在将应用提交到 Microsoft Store 之前，需要更新一些项目设置。 所有这些设置都具有默认值，但为了以最佳方式表示应用程序，这些设置应针对生产环境进行更改。

## <a name="project-settings-for-the-store-packaging"></a>应用商店打包的项目设置

1. 首先，选择“项目设置”>“说明”，更新游戏和发布者信息： 
    * 游戏名称将在 HoloLens 上的应用磁贴中显示
    * 在生成项目证书时，会使用公司可分辨名称，该名称应采用以下格式： 
        * CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName：

![Unreal 编辑器的屏幕截图，其中项目设置中展开了说明部分](images/unreal-publishing-img-01.png)

2. 展开项目设置的“HoloLens”部分，更新打包资源。  这些资源名称将显示在应用程序的“应用商店”页上：

![Unreal 编辑器的屏幕截图，其中项目设置中展开了打包部分](images/unreal-publishing-img-02.png)

3. 展开“图像”部分，并使用表示应用商店应用的纹理更新默认应用商店图像。  根据需要，选中“3D 徽标”复选框，上传一个 glb 文件，在启动应用程序时将其用作 3D 实时多维数据集：

![Unreal 编辑器的屏幕截图，其中项目设置中展开了图像部分](images/unreal-publishing-img-03.png)

4. 最后，选择“生成新项”，根据项目名称和公司可分辨名称生成一个签名证书  
    * 设置一种磁贴背景颜色，这种颜色会显示在应用商店图像中任何透明像素的位置。
    * 展开下拉菜单并启用“使用零售 Windows 应用商店环境”，以便在零售锁定的设备（而不是开发解锁的设备）上运行。

![Unreal 编辑器的屏幕截图，其中项目设置中展开了生成证书部分](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>可选的应用安装程序

可以通过“项目设置”>“HoloLens”创建应用安装程序文件，该文件可用于在应用商店外分发应用程序。  启用“应创建应用安装程序”复选框，并设置要在其中存储游戏的 appxbundle 的 URL 或网络路径。  

![Unreal 编辑器的屏幕截图，其中项目设置中展开了应用安装程序部分](images/unreal-publishing-img-05.png)

应用进行打包时，appxbundle 和 appinstaller 将随之生成。  将 appxbundle 上传到安装 URL，然后启动 appinstaller 以从该网络位置安装应用。

## <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

Windows 10 SDK 随附 Windows 应用认证工具包 (WACK)，用于验证可能影响将包上传到应用商店的常见问题。  可在 Windows Kits 目录中找到 WACK，目录通常位于以下路径下： 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. 将 appx 文件打包以进行发布后，运行 appcertui.exe 并按照提示扫描 appx：

![屏幕截图显示了 Windows 应用认证工具包中要选中用于验证的应用](images/unreal-publishing-img-06.png)

2. 选择“验证应用商店应用”：

![Windows 应用认证工具包中验证选择的屏幕截图](images/unreal-publishing-img-07.png)

3. 在顶部浏览找到 appx，并选择“下一步”：

![Windows 应用认证工具包中选择测试的屏幕截图](images/unreal-publishing-img-08.png)

4. 选择“下一步”，运行测试并创建报表：
    * 默认情况下，可在主机上运行的所有可用测试都将启用

![Windows 应用认证工具包中应用验证进度的屏幕截图](images/unreal-publishing-img-09.png)

5. 等待测试完成。 完成后，最终窗口将显示一个指示“通过”或“失败”的结果，可在保存的报表中查看该结果。

![Windows 应用认证工具包中最终报表结果的屏幕截图](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>4\.25 版的已知 WACK 故障

Unreal 4.25 中的 Windows Mixed Reality 插件无法通过 WACK 测试，因为在针对 HoloLens 进行打包时，其中包含一些 x64 二进制文件。 故障如下所示：

![Windows 应用认证工具包中，由于二进制分析器和支持的 API 导致的失败结果的屏幕截图](images/unreal-publishing-img-11.png)

若要解决这一问题，请执行以下操作：
1. 打开一个 Unreal 项目并右键单击任务栏中的 Unreal 图标，浏览到 Unreal 安装或源目录根。
2. 右键单击 UE4Editor，选择“属性”，然后浏览到“位置”条目中的路径：

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. 在 WindowsMixedRealityHMD.Build.cs 中，修改第 32 行 ：

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

to:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. 关闭 Unreal，重新打开该项目，并重新针对 HoloLens 进行打包。  重新运行 WACK，错误将消失。 

## <a name="see-also"></a>另请参阅

* [将应用提交到 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Windows 应用认证工具包](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [手动创建应用安装程序文件](/windows/msix/app-installer/how-to-create-appinstaller-file)