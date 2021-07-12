---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392533"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. 切换生成平台

在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。

在“生成设置”窗口中，选择“PC、Mac 和 Linux 单机”，然后单击“切换平台”按钮以更改生成平台： 

![切换生成平台](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

当 Unity 完成平台切换后，单击 x 图标，关闭“生成设置”窗口。

### <a name="2-set-the-project-settings"></a>2. 设置项目设置

在 Unity 菜单中，选择“编辑” > “项目设置” > “XR 插件管理”，以确保您位于“Windows 单机”选项卡中，然后选中“OpenXR”和“Windows Mixed Reality 功能集”复选框。    

![启用 OpenXR 和 Windows Mixed Reality 功能集](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

在“项目设置”窗口中，选择“OpenXR”，并确保您位于“Windows 单机”选项卡中，将“深度提交模式”从“无”更改为“深度 16 位”。  

在交互配置文件选项卡中，单击 + 符号添加“目视交互配置文件”和“Microsoft 手部交互配置文件”。

![添加目视交互配置文件和 Microsoft 手部交互配置文件](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

在“打开 XR 功能组” > “所有功能”下面，选中“全息应用远程处理”复选框。

![启用全息应用远程处理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

接下来选中“Windows Mixed Reality”复选框，并在 Windows Mixed Reality 组下选择“全息应用远程处理”复选框。

![启用 Windows Mixed Reality 全息应用远程处理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. 生成 Unity 项目

在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。

在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。 在“生成”列表中，单击“生成”按钮：

![添加了场景的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

选择合适的位置来存储您生成的项目，例如 Documents\MixedRealityLearning。 创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。 然后单击“选择文件夹”按钮，开始生成过程：

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

等待 Unity 完成生成过程。

![Unity 正在生成进程](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

双击可执行文件，在 PC 中打开 PC 全息远程处理应用程序。

> [!NOTE]
> 由于作为 UWP 生成的 PC 全息远程处理应用存在一些已知问题，我们正在将 PC 应用生成为 OpenXR Windows 单机。


# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1.设置播放器设置

在“XR 设置”部分，选中“支持的 WSA 全息远程处理”复选框，启用全息远程处理 。

![启用了“支持 WSA 全息远程处理”的 Unity XR 设置窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2.生成 Unity 项目

在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。

在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。 在“生成”列表中，单击“生成”按钮以打开“生成通用 Windows 平台”窗口：

![添加了场景的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

在“生成通用 Windows 平台”窗口中，选择一个合适的位置来存储生成结果，例如 Documents\MixedRealityLearning。 创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。 然后单击“选择文件夹”按钮，开始生成过程：

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

等待 Unity 完成生成过程。

![Unity 正在生成进程](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击 .sln 文件，在 Visual Studio 中其打开：

![选中了新建的“Visual Studio 解决方案”的 Windows 资源管理器](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保按照安装工具文档中的说明安装所有必备组件。

通过选择“发布配置”、“x64 体系结构”和“本地计算机”作为目标，配置 PC 版 Visual Studio：

![配置了“本地计算机”的 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

单击“本地计算机”按钮。 它会开始生成应用程序并将其部署到你的电脑。 该应用程序将默认安装在你的电脑中。
