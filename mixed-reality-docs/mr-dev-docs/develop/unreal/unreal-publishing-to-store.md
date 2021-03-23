---
title: 发布到 Microsoft Store
description: 了解如何打包、认证 Unreal 混合现实应用程序，以及如何将它们发布到 Microsoft Store。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 发布, 分发, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583592"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="925cc-104">发布到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="925cc-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="925cc-105">若已准备好对外发布你的 Unreal 应用，在将应用提交到 Microsoft Store 之前，需要更新一些项目设置。</span><span class="sxs-lookup"><span data-stu-id="925cc-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="925cc-106">所有这些设置都具有默认值，但为了以最佳方式表示应用程序，这些设置应针对生产环境进行更改。</span><span class="sxs-lookup"><span data-stu-id="925cc-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="925cc-107">应用商店打包的项目设置</span><span class="sxs-lookup"><span data-stu-id="925cc-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="925cc-108">首先，选择“项目设置”>“说明”，更新游戏和发布者信息：</span><span class="sxs-lookup"><span data-stu-id="925cc-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="925cc-109">游戏名称将在 HoloLens 上的应用磁贴中显示</span><span class="sxs-lookup"><span data-stu-id="925cc-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="925cc-110">在生成项目证书时，会使用公司可分辨名称，该名称应采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="925cc-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="925cc-111">CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName：</span><span class="sxs-lookup"><span data-stu-id="925cc-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Unreal 编辑器的屏幕截图，其中项目设置中展开了说明部分](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="925cc-113">展开项目设置的“HoloLens”部分，更新打包资源。</span><span class="sxs-lookup"><span data-stu-id="925cc-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="925cc-114">这些资源名称将显示在应用程序的“应用商店”页上：</span><span class="sxs-lookup"><span data-stu-id="925cc-114">These resource names will be shown on the application’s store page:</span></span>

![Unreal 编辑器的屏幕截图，其中项目设置中展开了打包部分](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="925cc-116">展开“图像”部分，并使用表示应用商店应用的纹理更新默认应用商店图像。</span><span class="sxs-lookup"><span data-stu-id="925cc-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="925cc-117">根据需要，选中“3D 徽标”复选框，上传一个 glb 文件，在启动应用程序时将其用作 3D 实时多维数据集：</span><span class="sxs-lookup"><span data-stu-id="925cc-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Unreal 编辑器的屏幕截图，其中项目设置中展开了图像部分](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="925cc-119">最后，选择“生成新项”，根据项目名称和公司可分辨名称生成一个签名证书</span><span class="sxs-lookup"><span data-stu-id="925cc-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="925cc-120">设置一种磁贴背景颜色，这种颜色会显示在应用商店图像中任何透明像素的位置。</span><span class="sxs-lookup"><span data-stu-id="925cc-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="925cc-121">展开下拉菜单并启用“使用零售 Windows 应用商店环境”，以便在零售锁定的设备（而不是开发解锁的设备）上运行。</span><span class="sxs-lookup"><span data-stu-id="925cc-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Unreal 编辑器的屏幕截图，其中项目设置中展开了生成证书部分](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="925cc-123">可选的应用安装程序</span><span class="sxs-lookup"><span data-stu-id="925cc-123">Optional App Installer</span></span>

<span data-ttu-id="925cc-124">可以通过“项目设置”>“HoloLens”创建应用安装程序文件，该文件可用于在应用商店外分发应用程序。</span><span class="sxs-lookup"><span data-stu-id="925cc-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="925cc-125">启用“应创建应用安装程序”复选框，并设置要在其中存储游戏的 appxbundle 的 URL 或网络路径。</span><span class="sxs-lookup"><span data-stu-id="925cc-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Unreal 编辑器的屏幕截图，其中项目设置中展开了应用安装程序部分](images/unreal-publishing-img-05.png)

<span data-ttu-id="925cc-127">应用进行打包时，appxbundle 和 appinstaller 将随之生成。</span><span class="sxs-lookup"><span data-stu-id="925cc-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="925cc-128">将 appxbundle 上传到安装 URL，然后启动 appinstaller 以从该网络位置安装应用。</span><span class="sxs-lookup"><span data-stu-id="925cc-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="925cc-129">Windows 应用认证工具包</span><span class="sxs-lookup"><span data-stu-id="925cc-129">Windows App Certification Kit</span></span>

<span data-ttu-id="925cc-130">Windows 10 SDK 随附 Windows 应用认证工具包 (WACK)，用于验证可能影响将包上传到应用商店的常见问题。</span><span class="sxs-lookup"><span data-stu-id="925cc-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="925cc-131">可在 Windows Kits 目录中找到 WACK，目录通常位于以下路径下：</span><span class="sxs-lookup"><span data-stu-id="925cc-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="925cc-132">将 appx 文件打包以进行发布后，运行 appcertui.exe 并按照提示扫描 appx：</span><span class="sxs-lookup"><span data-stu-id="925cc-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![屏幕截图显示了 Windows 应用认证工具包中要选中用于验证的应用](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="925cc-134">选择“验证应用商店应用”：</span><span class="sxs-lookup"><span data-stu-id="925cc-134">Select **Validate Store App**:</span></span>

![Windows 应用认证工具包中验证选择的屏幕截图](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="925cc-136">在顶部浏览找到 appx，并选择“下一步”：</span><span class="sxs-lookup"><span data-stu-id="925cc-136">Browse for the appx in the top section and select **Next**:</span></span>

![Windows 应用认证工具包中选择测试的屏幕截图](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="925cc-138">选择“下一步”，运行测试并创建报表：</span><span class="sxs-lookup"><span data-stu-id="925cc-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="925cc-139">默认情况下，可在主机上运行的所有可用测试都将启用</span><span class="sxs-lookup"><span data-stu-id="925cc-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Windows 应用认证工具包中应用验证进度的屏幕截图](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="925cc-141">等待测试完成。</span><span class="sxs-lookup"><span data-stu-id="925cc-141">Wait for the tests to finish.</span></span> <span data-ttu-id="925cc-142">完成后，最终窗口将显示一个指示“通过”或“失败”的结果，可在保存的报表中查看该结果。</span><span class="sxs-lookup"><span data-stu-id="925cc-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Windows 应用认证工具包中最终报表结果的屏幕截图](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="925cc-144">4\.25 版的已知 WACK 故障</span><span class="sxs-lookup"><span data-stu-id="925cc-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="925cc-145">Unreal 4.25 中的 Windows Mixed Reality 插件无法通过 WACK 测试，因为在针对 HoloLens 进行打包时，其中包含一些 x64 二进制文件。</span><span class="sxs-lookup"><span data-stu-id="925cc-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="925cc-146">故障如下所示：</span><span class="sxs-lookup"><span data-stu-id="925cc-146">The failure will look like this:</span></span>

![Windows 应用认证工具包中，由于二进制分析器和支持的 API 导致的失败结果的屏幕截图](images/unreal-publishing-img-11.png)

<span data-ttu-id="925cc-148">若要解决这一问题，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="925cc-148">To fix the issue:</span></span>
1. <span data-ttu-id="925cc-149">打开一个 Unreal 项目并右键单击任务栏中的 Unreal 图标，浏览到 Unreal 安装或源目录根。</span><span class="sxs-lookup"><span data-stu-id="925cc-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="925cc-150">右键单击 UE4Editor，选择“属性”，然后浏览到“位置”条目中的路径：</span><span class="sxs-lookup"><span data-stu-id="925cc-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="925cc-151">在 WindowsMixedRealityHMD.Build.cs 中，修改第 32 行 ：</span><span class="sxs-lookup"><span data-stu-id="925cc-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="925cc-152">to:</span><span class="sxs-lookup"><span data-stu-id="925cc-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="925cc-153">关闭 Unreal，重新打开该项目，并重新针对 HoloLens 进行打包。</span><span class="sxs-lookup"><span data-stu-id="925cc-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="925cc-154">重新运行 WACK，错误将消失。</span><span class="sxs-lookup"><span data-stu-id="925cc-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="925cc-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="925cc-155">See also</span></span>

* [<span data-ttu-id="925cc-156">将应用提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="925cc-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="925cc-157">Windows 应用认证工具包</span><span class="sxs-lookup"><span data-stu-id="925cc-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="925cc-158">手动创建应用安装程序文件</span><span class="sxs-lookup"><span data-stu-id="925cc-158">Create an App Installer file manually</span></span>](/windows/msix/app-installer/how-to-create-appinstaller-file)