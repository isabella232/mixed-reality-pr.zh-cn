---
title: 设计自己的沉浸式环境
description: 了解如何创建自己的 Windows Mixed Reality 主环境。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，Home，自定义环境，地点，cliff 房子，skyloft，用户，创建，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 2a626b91b79eadb49c9da95c9d61f92a375015a0
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881214"
---
# <a name="design-your-own-immersive-environments"></a>设计自己的沉浸式环境

>[!NOTE]
>这是一项实验性功能。 试一试，并对它感兴趣，但如果所有内容均未按预期工作，则不会惊讶。 我们正在评估此功能的生存能力，并对使用它感兴趣，因此请告诉我们你的体验 (以及在 [开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)中找到) 的任何 bug。

从 [windows 10 4 月2018版更新](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)开始，我们启用了一个试验性功能，该功能使你能够将自定义环境添加到 "开始" 菜单上的 "位置选取器 (，) 用作 [Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)。 Windows Mixed Reality 提供两个默认环境： Cliff 房子和 Skyloft，你可以选择作为你的家庭。 创建自定义环境使你可以通过自己的创建来扩展列表。 我们正在使此功能在早期状态下提供，以便评估创建者和开发人员的兴趣。 了解你创建了哪些类型的世界，并了解如何使用不同的创作工具。

使用自定义环境时，您会注意到，teleporting、与应用程序的交互，并使全息影像的工作方式与在 Cliff 房子和 Skyloft 中的工作方式相同。 你可以在幻想环境中浏览 web，或使用全息影像来填充现在俨然

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>自定义家庭环境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>尝试使用示例环境

我们创建了一个示例环境，其中显示了自定义 home 环境的一些创新可能性。 请按照以下步骤进行试用：
1. [下载示例幻想岛环境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (链接点到自解压缩可执行文件) 。

    ![幻想岛示例环境](images/FantasyLand.jpg)<br>
    *幻想岛示例环境*<br>

2. 运行下载的 **Fantasy_Island.exe** 文件。

    > [!NOTE]
    > 尝试运行从 web (下载的 .exe 文件时) ，可能会遇到 "受 Windows 保护的 PC" 弹出窗口。 若要从此弹出窗口中运行 Fantasy_Island.exe，请选择 " **详细信息** "，然后 **继续运行**。 此安全设置旨在防止您下载可能不想要信任的文件，因此，请仅当您信任文件的源时选择此选项。

3. 打开 **文件资源管理器** 并导航到 "环境" 文件夹，方法是在地址栏中粘贴以下文件位置： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 。
4. 将下载的示例环境复制到此文件夹。
5. 重新启动 **混合现实门户** ，以便在 "位置" 选取器中刷新环境列表。
6. 戴上耳机。 进入 home 后，使用 Windows 按钮打开 " **开始" 菜单** 。
7. 选择固定应用列表上方的 " **位置** " 图标以选择 home 环境。
8. 你会发现你在位置列表中下载的幻想岛环境。 选择 " **幻想岛** " 输入新的自定义家庭环境！

## <a name="creating-your-own-custom-environment"></a>创建自己的自定义环境

除了使用我们的示例环境以外，你还可以使用你最喜欢的3D 编辑软件导出你自己的自定义环境。 

### <a name="modeling-guidelines"></a>建模准则

在对环境进行建模时，请记住以下建议，以便用户在 believably 规模世界中以正确的方向进行：

1. 用户将生成0，0，0，以便将衍生位置围绕原点居中。
2. 工作单元应设置为 "米"，以便可以在全球范围内创作资产。
3. 向上轴应设置为 "Y"。
4. 资产应正面朝正 Z 轴 "前进"。
5. 无需合并所有网格，但建议将其定向到 "资源受限设备"。

### <a name="exporting-your-environment"></a>导出环境

Windows Mixed Reality 依赖于二进制 glTF (. glb) 作为环境的资产传送格式。 glTF 是由 Khronos 组维护的用于3D 资产交付的版税免费开放标准。 Microsoft 对跨 Windows 应用和体验的格式的支持将随着 glTF 发展为可互操作的3D 内容的行业标准而发展。

导出要用作自定义家庭环境的资产的第一步是生成 glTF 2.0 模型。 GlTF 工作组维护一 [系列受支持的导出程序和转换器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) ，以创建 glTF 2.0 模型。 若要开始使用，请使用此页上列出的程序之一创建和导出 glTF 2.0 模型，或使用其中一个受支持的转换器转换现有的模型。

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>环境限制

所有环境必须 < 256 mb。 大于 256 mb 的环境将无法加载，并将使用围绕用户的默认 skybox 来回退到空世界。 创建模型时，请记住此文件大小限制。 此外，如果您计划使用 WindowsMRAssetConverter 按如下所述的方式优化您的环境，则必须 cognizant 纹理大小会随着优化器创建具有更大文件大小但加载速度更快的纹理而增加。 

### <a name="optimizing-your-environment"></a>优化环境

Windows Mixed Reality 支持很多可显著减少环境加载时间的可选优化。 请特别注意具有大量纹理的环境，因为它们有时会在加载时超时。 通常，我们建议对所有资产执行此步骤，但是，具有少量或低分辨率纹理的小型环境不会始终需要此步骤。 

为了使此过程更容易，我们已创建了 [在 GitHub 上可用的 Windows Mixed Reality 资产转换器 () ](https://github.com/Microsoft/glTF-Toolkit/releases) ，以便进行优化。 此工具使用 Microsoft glTF 工具包中提供的一组实用工具来优化任何标准 2.0 glTF 或 glb，方法是执行额外的纹理打包、压缩和分辨率下降。 

转换器当前支持多个标志来调整优化的确切行为。 建议运行以下标志以获得最佳结果：

标志|建议值 (s) |说明
---|---|---
-最大纹理大小|1024或2048| 调整该值以提高纹理质量，默认值为512x512。 较大的值将显著影响环境的文件大小，因此请记住 256 mb 的限制
-最小版本|1803|仅在 windows >= 1803 的版本上支持自定义环境。 此标志将删除较旧版本的纹理，并减小最终资产的文件大小

例如：

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>测试环境

拥有最终的 glb 环境后，就可以在耳机中进行测试了。 从 ["尝试示例环境"](#trying-a-sample-environment) 部分的步骤2开始，使用自定义环境作为混合现实主页。 

## <a name="sending-feedback"></a>发送反馈

尽管我们正在评估此试验性功能，但我们有兴趣了解你使用自定义环境的方式、可能发现的任何错误，以及你喜欢该功能的方式。 在 [开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)中共享用于创建和使用自定义家庭环境的任何反馈。

## <a name="troubleshooting-and-tips"></a>疑难解答和提示

### <a name="how-do-i-change-the-name-of-the-environment"></a>如何实现更改环境的名称？

"环境" 文件夹中的文件名将用在 "位置" 选取器中。 若要更改环境的名称，请重命名环境文件名称，然后重启混合现实门户。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>如何实现从 "我的位置" 选取器中删除自定义环境？

若要删除自定义环境，请打开电脑上的 "环境" 文件夹 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 并删除环境。 重新启动混合现实门户后，此环境将不再显示在 "位置" 选取器中。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>默认情况下，如何实现到我最喜欢的自定义环境？

当前无法更改默认环境。 每次重新启动混合现实门户时，都将返回到 Cliff 房子环境。 

### <a name="i-spawn-into-a-blank-space"></a>我将生成空白空间

Windows Mixed Reality [不支持超过 256 mb 的环境](#environment-limits)。 当某个环境超过此限制时，你将在不带任何型号的空天空中居住。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>加载环境需要很长时间

可以在环境中添加可选优化，使其更快加载。 有关详细信息，请参阅 ["优化你的环境"](#optimizing-your-environment) 。

### <a name="the-scale-of-my-environment-is-incorrect"></a>我的环境规模不正确

加载环境时，Windows Mixed Reality 会将 glTF 单位转换为1米。 如果你的环境加载了意外的规模，请仔细检查你的导出器，以确保按1计量规模进行建模。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>我的环境中的生成位置不正确

默认生成位置位于环境中的0，0，0。 目前不能自定义此位置，因此你必须通过导出环境来修改衍生点，并将源置于所需的生成点。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>音频在环境中不正确

创建自定义环境时，它将使用与所创建的物理空间不匹配的噪声渲染模拟。 声音可能来自错误的方向，可能听起来 muffled。 

## <a name="see-also"></a>请参阅
* [GitHub 上的 Windows Mixed Reality 资产转换器 () ](https://github.com/Microsoft/glTF-Toolkit/releases)