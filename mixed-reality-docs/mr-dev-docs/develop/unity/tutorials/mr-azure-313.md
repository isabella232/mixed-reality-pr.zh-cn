---
title: HoloLens（第一代）和 Azure 313 - IoT 中心服务
description: 了解如何在运行 Ubuntu 16.4 的虚拟机上实现 Azure IoT 集线器服务，以及如何使用 Microsoft HoloLens 或 VR 耳机直观显示邮件数据。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure，混合现实，学院，边缘，iot edge，教程，api，通知，函数，表，hololens，沉浸，vr，iot，虚拟机，ubuntu，python，Windows 10，Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905767"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (第一代) 和 Azure 313： IoT 中心服务

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

![课程结果](images/AzureLabs-Lab313-00.png)

在本课程中，你将了解如何在运行 Ubuntu 16.4 操作系统的虚拟机上实现 **Azure IoT 集线器服务**。 然后， **azure Function App** 将用于从 Ubuntu VM 接收消息，并将结果存储在 **Azure 表服务** 中。 然后，你将能够使用 Microsoft HoloLens 上的 **Power BI** 或沉浸式 (VR) 耳机查看此数据。

本课程的内容 *适用* 于 IoT Edge 设备，不过，在本课程中，重点将位于虚拟机环境中，因此不需要访问物理边缘设备。

完成本课程后，你将学习：

- 将 **IoT Edge 模块** 部署到 (UBUNTU 16 OS) 虚拟机，这将表示 IoT 设备。
- 将 **Azure 自定义视觉 Tensorflow 模型** 添加到 Edge 模块，其中包含用于分析容器中存储的图像的代码。
- 设置模块以将分析结果消息发送回 **IoT 中心服务**。
- 使用 **azure Function App** 将消息存储在 **azure 表** 中。
- 设置 **Power BI** 以收集存储的消息并创建报表。
- 在 **Power BI** 中直观显示 IoT 消息数据。

将使用的服务包括：

- **Azure IoT 中心** 是一种 Microsoft Azure 服务，它允许开发人员连接、监视和管理 IoT 资产。 有关详细信息，请访问 [ **Azure IoT 中心服务** 页](https://azure.microsoft.com/services/iot-hub/)。

- **Azure 容器注册表** 是一种 Microsoft Azure 服务，它允许开发人员为各种类型的容器存储容器映像。 有关详细信息，请访问 [ **Azure 容器注册表服务** 页](https://azure.microsoft.com/services/container-registry/)。

- **azure Function App** 是一种 Microsoft Azure 服务，它允许开发人员在 Azure 中运行小部分代码 "函数"。 这提供了一种方法，可将工作委托给云，而不是本地应用程序，这可能有很多好处。 **Azure Functions** 支持多种开发语言，包括 C \# 、F \# 、Node.js、Java 和 PHP。 有关详细信息，请访问 [ **Azure Functions** 页](/azure/azure-functions/functions-overview)。

- **Azure 存储：表** 是一种 Microsoft Azure 服务，它允许开发人员在云中存储结构化、非 SQL 数据，使其在任何位置轻松访问。 此服务的设计良好，可根据需要进行表的发展，因此非常灵活。 有关详细信息，请访问 [ **Azure 表** 页](/azure/cosmos-db/table-storage-overview)

本课程将介绍如何设置和使用 IoT 中心服务，然后将设备提供的响应可视化。 您可以将这些概念应用到您可能会构建的自定义 IoT 中心服务设置。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 313：IoT 中心服务</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必备条件

有关利用混合现实进行开发的最新先决条件，包括在 Microsoft HoloLens 中，请访问[安装工具](../../install-the-tools.md)一文。

> [!NOTE]
> 本教程适用于具有 Python 的基本经验的开发人员。 请注意，本文档中的先决条件和书面说明表示在) 2018 年7月 (撰写本文时已测试和验证的内容。 您可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的软件内容完全匹配。

需要以下硬件和软件：

- Windows 10 Fall Creators Update (或更高版本) ，**已启用开发人员模式**

    > [!WARNING]
    > 不能使用 Windows 10 家庭版 Edition 上的 hyper-v 运行虚拟机。

- Windows 10SDK (最新版本) 
- **已启用 HoloLens 开发人员模式**
- 仅 Visual Studio 2017.15.4 (用于访问 Azure Cloud Explorer) 
- Azure 和 IoT 中心服务的 Internet 访问。 有关详细信息，请访问 [IoT 中心服务页面链接](https://azure.microsoft.com/services/iot-hub/)
- 一个机器学习模型。 如果没有现成的可用模型， [可以使用本课程提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。
- 在 Windows 10 开发计算机上启用 **hyper-v** 软件。
- 运行 Ubuntu 的虚拟机 (16.4 或 18.4) ，在开发计算机上运行，或者也可以使用运行 Linux (Ubuntu 16.4 或 18.4) 的单独计算机。 可以在["开始之前" 一章](#before-you-start)中找到有关如何使用 hyper-v 在 Windows 上创建 VM 的详细信息。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine) 。  



### <a name="before-you-start"></a>开始之前

1. 设置并测试 HoloLens。 如果需要支持设置 HoloLens，请[确保访问 HoloLens 安装程序一文](/hololens/hololens-setup)。
2. 在开始开发新的 HoloLens 应用程序时，最好执行 **校准** 和 **传感器调整** (有时，它可以帮助为每个用户) 执行这些任务。

有关校准的帮助信息，请访问[HoloLens 校准文章](/hololens/hololens-calibration#hololens-2)。

有关传感器优化的帮助，请访问[HoloLens 传感器优化文章](/hololens/hololens-updates)。

3. 使用 **hyper-v** 设置 **Ubuntu 虚拟机**。 以下资源将帮助你执行此过程。
    1.  首先，请单击以下链接 [下载 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/)。 选择 **64 (AMD64) 桌面映像**。
    2.  请确保在 Windows 10 计算机上启用了 **hyper-v** 。 你可以单击此链接，获取有关在[Windows 10 上安装和启用 hyper-v](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)的指南。
    3.  启动 Hyper-v 并创建新的 Ubuntu VM。 可以访问此链接，了解有关 [如何使用 hyper-v 创建 VM](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)的分步指导。 当请求 **"从可启动的映像文件安装操作系统"** 时，选择之前下载的 **Ubuntu ISO** 。

    > [!NOTE]
    > 不建议使用 **Hyper-v 快速创建** 。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第1章-检索自定义视觉模型

在本课程中，您将有权访问 [预建的自定义视觉模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) ，用于检测图像中的键盘和鼠标。 如果使用此操作，请转到 [第2章](#chapter-2---the-container-registry-service)。

但是，如果想要使用自己的自定义视觉模型，则可以执行以下步骤：

1. 在 **自定义视觉中 Project** 中转到 "**性能**" 选项卡。

    > [!WARNING]
    > 您的模型必须使用 *精简* 域来导出模型。 你可以在项目的设置中更改模型域。

    ![性能选项卡](images/AzureLabs-Lab313-01.png)

2. 选择要导出的 **迭代** ，并单击 " **导出**"。 随即出现一个边栏选项卡。

    ![导出边栏选项卡](images/AzureLabs-Lab313-02.png)

3. 在边栏选项卡中，单击 " **Docker 文件**"。

    ![选择 docker](images/AzureLabs-Lab313-03.png)

4. 在下拉菜单中单击 " **Linux** "，然后单击 " **下载**"。

    ![单击 "下载"](images/AzureLabs-Lab313-04.png)

5. 解压缩内容。 稍后将在本课程中使用它。

## <a name="chapter-2---the-container-registry-service"></a>第2章-容器注册表服务

**容器注册表服务** 是用于托管容器的存储库。

你将在本课程中构建和使用的 **IoT 中心服务** 是指 **容器注册表服务** ，用于获取要在边缘设备中部署的容器。

1. 首先，请 [在 Azure 门户](https://portal.azure.com/)中单击此链接，然后用你的凭据登录。

2. 请参阅 **创建资源** 并查找 **容器注册表**。

    ![容器注册表](images/AzureLabs-Lab313-05.png)

3. 单击“创建”。

    ![](images/AzureLabs-Lab313-06.png)

4. 设置服务设置参数：

    1. 插入项目的名称，此示例中其名称名为 **IoTCRegistry**。

    2. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种监视、控制 Azure 资产集合的访问、预配和管理计费的方法。 建议将与单个项目关联的所有 Azure 服务 (例如，这些课程) 位于公共资源组) 。

    3. 设置服务的位置。

    4. 将 **"管理员用户"** 设置为"**启用"。**

    5. 将 **"SKU"** 设置为"**基本"。** 

    ![](images/AzureLabs-Lab313-07.png)

5. 单击 **"** 创建"并等待创建服务。 

6. 一旦弹出通知通知你已成功创建容器注册表，请单击"转到要重定向到服务"页的资源。 

    ![](images/AzureLabs-Lab313-08.png)

7. 在"*容器注册表服务"* 页中，单击"**访问密钥"。**

8. 请注意 (可以使用以下记事本) 参数：
    1. **登录服务器**
    2. **用户名**
    3. **密码**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第 3 章 - IoT 中心服务

现在，你将开始创建和设置 **IoT 中心服务**。

1. 如果尚未登录，请登录到 Azure [门户](https://portal.azure.com)。

2.  登录后，单击左上角的"创建资源"，搜索 **"IoT 中心**"，然后单击"**输入"。**

 ![搜索存储帐户](images/AzureLabs-Lab313-10.png)

3.  新页面将提供帐户服务 **存储说明**。 在此提示符的左下角，单击" **创建** "按钮，创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab313-11.png)

4.  单击"创建" **后**，将显示一个面板：

    1. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些课程) 位于公共资源组) 。

        > 若要详细了解 Azure 资源组，请按照此 [链接了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。


    2. 选择适当的 **"位置** (在本课程创建的所有服务中使用相同的位置) 。

    3. 为此服务 **实例插入** 所需的名称。    

5.  在页面底部，单击"下一步 **： 大小和缩放"。**

    ![创建存储实例](images/AzureLabs-Lab313-12.png)

6.  在此页中，选择定价层和缩放 **层 (如果** 这是第一个 IoT 中心服务实例，则应该可以使用免费层) 。  

7.  单击"**查看 + 创建"。**

    ![创建存储实例](images/AzureLabs-Lab313-13.png)

8.  查看设置，然后单击"创建 **"。**

    ![创建存储实例](images/AzureLabs-Lab313-14.png)

9. 弹出通知通知已成功创建 *IoT* 中心服务后，单击"转到要重定向到服务的资源"页。

    ![创建存储实例](images/AzureLabs-Lab313-15.png)

10. 滚动左侧的侧面板，直到看到"自动 *设备管理，然后单击***"IoT Edge"。**

    ![创建存储实例](images/AzureLabs-Lab313-16.png)

11. 在右侧出现的窗口中，单击"添加IoT Edge **设备"。** 边栏选项卡将显示在右侧。

12. 在边栏选项卡中，为新设备提供设备 **ID** (选择的名称) 。 然后单击“保存” 。 如果 *已勾选**"自动生成*"，主密钥和辅助 **密钥将自动生成**。

    ![创建存储实例](images/AzureLabs-Lab313-17.png)

13. 你将导航回"IoT Edge *设备"* 部分，其中将列出新设备。 单击新设备 (下图中用红色) 。 

    ![创建存储实例](images/AzureLabs-Lab313-18.png)

14. 在出现的 *"设备* 详细信息"页上，将"连接字符串" **副本 (主**) 。

    ![创建存储实例](images/AzureLabs-Lab313-19.png)

15. 返回到左侧的面板，然后单击" *共享访问策略*"以打开它。 

16. 在出现的页面上，单击 **"iothubowner"，** 屏幕右侧将显示一个边栏选项卡。 

17. 记下 (连接记事本) 字符串 (密钥) ，供稍后在将连接字符串设置为设备时使用。 

    ![创建存储实例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第 4 章 - 设置开发环境

若要为 IoT 中心 Edge 创建和部署模块，需要在运行 *IoT* Edge 的开发计算机上安装以下Windows 10：

1.  [Docker for Windows，](https://store.docker.com/editions/community/docker-ce-desktop-windows)它将要求你创建一个能够下载的帐户。 

    [![下载适用于 Windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker *要求Windows 10 PRO* Enterprise *14393* 或 Windows Server 2016 *RTM。* 如果运行的是其他版本的 Windows 10，可以尝试使用 Docker 工具箱[安装 Docker。](https://docs.docker.com/toolbox/toolbox_install_windows/)

2.  [Python 3.6。](https://www.python.org/downloads/)

    [![下载 python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (也称为 VS Code) 。 ](https://code.visualstudio.com/download)

    [![下载VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

安装上述软件后，需要重启计算机。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第 5 章 - 设置 Ubuntu 环境

现在，可以继续设置运行 **Ubuntu OS 的设备**。 按照以下步骤安装必要的软件，在开发板上部署容器：

> [!IMPORTANT]
> 应始终在终端命令之前使用 **sudo 以** 管理员用户运行。 即：
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  打开 **Ubuntu 终端**，使用以下命令安装 **pip：**

    > [!提示] 可以使用键盘快捷方式 *轻松* 打开终端 **：Ctrl + Alt + T**。

    ```bash
        sudo apt-get install python-pip
    ```

2.  在本章中，终端可能会提示你有权使用设备存储，并提示输入 **y/n** (是或否) ，键入 **"y"，** 然后按 **Enter** 键接受。

3.  完成该命令后，使用以下命令安装 **curl**：

    ```bash
        sudo apt install curl
    ```

4.  安装 **pip** 和 **curl** 后，使用以下命令安装 IoT Edge **运行时**，这是部署和控制开发板上的模块所必需的：

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. 此时 (，在步骤 [14（](#chapter-3---the-iot-hub-service)第) 3 章）创建 **IoT** 中心服务 (时，系统会提示你打开运行时配置文件 ，以插入在 记事本) 中记下的设备连接字符串 (。 在终端中运行以下行以打开该文件：

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. 将显示 **config.yaml** 文件，可供你编辑：

    > [!WARNING]
    > 此文件打开时，可能有点令人困惑。 你将在终端本身中编辑 *此文件的文本* 。 

    1.  使用键盘上的箭头键向下滚动 (需要向下滚动一点) 才能到达包含"的行：

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. 将行 **（包括方括号**）替换为前面提到的 **设备连接** 字符串。

7. 连接字符串就位后，在键盘上按 **Ctrl-X** 键保存文件。 它会要求你键入 **Y** 进行确认。然后，按 **Enter** 键进行确认。 将返回到 *常规终端*。 

8. 这些命令全部成功运行后，你将已安装 IoT Edge **运行时**。 初始化后，每次启动设备时，运行时都将自行启动，并在后台等待模块从 **IoT 中心服务 部署**。

9.  运行以下命令行以初始化 IoT Edge *运行时*：

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > 如果对 .yaml 文件或上述设置进行更改，则需要在终端 中再次运行上述重启 *行*。

10. 通过 *IoT Edge命令行* 检查运行时状态。 运行时应显示为活动状态 (**以)** 文本显示。

    ```bash
        sudo systemctl status iotedge
    ```

11. 按 **Ctrl-C** 键退出状态页。 可以通过键入以下 *IoT Edge* 验证运行时是否正在正确拉取容器：

    ```bash
        sudo docker ps
    ```

12. 应显示一个 (2) 的列表。 这些是 IoT 中心服务自动创建的默认模块 (edgeAgent 和 edgeHub) 。 创建和部署自己的模块后，这些模块将显示在此列表的默认模块下方。

## <a name="chapter-6---install-the-extensions"></a>第 6 章 - 安装扩展

> [!IMPORTANT]
> 接下来的几章 (6-9) 在 Windows 10 计算机上执行。

1. 打开 **VS Code**。

2. 单击 VS Code 左侧栏) " (的"**扩展**"，打开"**扩展 "面板**。

3. 搜索并安装以下扩展 (如下图所示) ：

    1. Azure IoT Edge
    2. Azure IoT 工具包
    3. Docker   

    ![创建容器](images/AzureLabs-Lab313-24.png)

4. 安装扩展后，请关闭并重新打开 VS Code。

5. 再打开 VS Code，导航到 "**查看**" "  >  **集成终端**"。

6. 现在，你将安装 **Cookiecutter**。 在终端中运行以下 bash 命令：

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示] 如果你在使用此命令时遇到问题： 
    >1. 重新启动 VS Code 和/或您的计算机。
    >2. 可能需要将 **VS Code 终端** 切换到你用来安装 Python 的计算机（例如 **Powershell** (），尤其是在你的计算机上安装了 python 环境) 时。 打开终端后，会在终端的右侧找到下拉菜单。
     ![创建容器](images/AzureLabs-Lab313-24b.png) 
    >3. 请确保将 **Python** 安装路径添加为计算机上的 **环境变量** 。 Cookiecutter 应属于同一位置路径。 [有关环境变量的详细信息](/windows/win32/procthread/environment-variables)，请访问此链接 

7. **Cookiecutter** 安装完成后，应重新启动计算机，以便在系统环境中将 **Cookiecutter** 识别为命令。

## <a name="chapter-7---create-your-container-solution"></a>第7章-创建容器解决方案

此时，需要创建包含模块的容器，将其推送到 *容器注册表* 中。 推送容器后，将使用 *IoT 中心边缘* 服务将其部署到运行 *IoT Edge 运行时* 的设备。

1. 在 VS Code 中，单击 "**查看**" "  >  **命令面板**"。

2. 在调色板中，搜索并运行 **Azure IoT Edge：新的 IoT Edge 解决方案**。

3. 浏览到要在其中创建解决方案的位置。 按 **enter** 键接受该位置。

4. 为解决方案指定一个名称。 按 **enter** 键以确认所提供的名称。

5. 现在，系统将提示您选择解决方案的模板框架。 单击 " **Python 模块**"。 按 **enter** 键确认此选择。

6. 为模块指定名称。 按 **enter** 键以确认模块的名称。 请确保对模块名称的记事本) 进行注释 (，因为稍后将用到它。

7. 你会注意到，组件面板上将显示预先生成的 *Docker 映像存储库* 地址。 它将如下所示：

    **localhost： 5000/-模块的名称-**。 

8. 删除 **localhost： 5000**，并在其位置插入 *容器注册表***登录服务器** 地址（在创建 **容器注册表服务** 时记下的）， ([第2章) 中的步骤 8](#chapter-2---the-container-registry-service) 。 按 **enter** 键以确认地址。

9. 此时，将创建包含 Python 模块模板的解决方案，并将其结构显示在 "浏览" 选项卡的 "**浏览器" 选项卡** 中，在 "浏览器" 选项卡中，在 "浏览器" 选项卡中，在 "VS Code 如果 " **资源管理器" 选项卡** 未打开，则可以通过单击左侧栏中的最上面的按钮打开它。

    ![创建容器](images/AzureLabs-Lab313-25.png)

10. 本章的最后一个步骤是，从 "**浏览" 选项卡** 中单击并打开 " **env" 文件**，然后添加 *容器注册表***用户名** 和 **密码**。 Git 忽略此文件，但在构建容器时，将设置用于访问 **容器注册表服务** 的凭据。

    ![创建容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第8章-编辑容器解决方案

现在，你将通过更新下列文件来完成容器解决方案：

- *<span></span> py* python 脚本。
- *requirements.txt*。
- *deployment.template.js*。
- *Dockerfile amd64*

然后，将创建用于 python *脚本的 images 文件夹，* 以检查图像是否与 *自定义视觉模型* 匹配。 最后，您将添加 *labels.txt* 文件，以帮助读取 *您的模型和模型文件。*

1. 打开 VS Code，导航到模块文件夹，然后查找名为 **<span></span> py** 的脚本。 双击将其打开。

2. 删除文件的内容并插入以下代码：

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  打开名为 **requirements.txt** 的文件，并将其内容替换为以下内容：

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  打开名为deployment.template.js的文件，并 **根据** 以下准则来替换其内容：

    1. 因为你将拥有自己的唯一的 JSON 结构，所以需要 (手动编辑该结构，而不是复制) 的示例。 为此，请使用以下图像作为指导。
    2. 外观与你的区域不同，但你 **不应更改为黄色**。
    3. **您需要删除的部分将突出显示为红色。**
    4. 请注意删除正确的方括号，同时删除逗号。

        ![创建容器](images/AzureLabs-Lab313-27.png)

    5. 但是，已完成的 JSON 应该如下图所示 (但唯一的区别在于： *用户名/密码/模块名称/模块引用*) ：

        ![创建容器](images/AzureLabs-Lab313-28.png)

5.  打开名为 **Dockerfile** 的文件，并将其内容替换为以下内容：

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  右键单击 " **模块** " 下的文件夹 (它将具有之前提供的名称;在下面的示例中，它称为 " *pythonmodule*) "，然后单击 " **新建文件夹**"。 将文件夹命名为 **images**。

7.  在该文件夹中，添加包含鼠标或键盘的一些图像。 这些将是 Tensorflow 模型将分析的映像。

    > [!WARNING]
    > 如果你使用自己的模型，则需要更改此以反映你自己的模型数据。

8.  现在，你将需要从你之前从其下载的模型文件夹中检索 **labels.txt** 和 (文件 **，并在**[第1章](#chapter-1---retrieve-the-custom-vision-model)中从自己的 **自定义影像服务**) 中创建这些文件。 获得这些文件后，请将它们放在解决方案中，并将它们放在其他文件中。 最终结果应该如下图所示：

    ![创建容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第9章-将解决方案打包为容器

1.  现在，你可以将文件 "打包" 为容器并将其推送到 **Azure 容器注册表**。 在 VS Code 中，打开 "*集成终端*" ("**视图**  >  " "**集成终端**" 或 " **Ctrl** + **\`**) "，并使用以下行登录到 **Docker** (将命令的值替换为 **Azure 容器注册表的凭据 (ACR)**) ：

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. 右键单击 **deployment.template.js** 的文件，然后单击 " **生成 IoT Edge 解决方案**"。 此生成过程需要一段时间， (具体取决于你的设备) ，因此请准备好等待。 生成过程完成后，会在名为 **config** 的新文件夹中创建文件 **deployment.js** 。

    ![创建部署](images/AzureLabs-Lab313-30.png)

3. 再次打开 **命令面板** ，然后搜索 " **Azure：登录**"。 按照使用 Azure 帐户凭据的提示进行操作;VS Code 将向你提供一个选项，用于 *复制和打开*，这将会复制你即将需要的设备代码，并打开默认 web 浏览器。 当系统询问时，粘贴设备代码以对计算机进行身份验证。

    ![复制并打开](images/AzureLabs-Lab313-31.png)

4. 登录后，将在 "*浏览*" 面板的底部看到一个名为 " **Azure IoT 集线器设备**" 的新部分。 单击此部分以将其展开。

    ![边缘设备](images/AzureLabs-Lab313-32.png)

5. 如果你的设备不在此处，你需要右键单击 *Azure IoT 集线器设备*，然后单击 "**设置 IoT 中心连接字符串**"。 然后，你将看到 **命令面板** (在 VS Code) 的顶部，将提示你输入 *连接字符串*。 这是你在 [第3章](#chapter-3---the-iot-hub-service)末尾记下的 *连接字符串*。 在中复制字符串后，按 **enter** 键。    

6. 设备应加载并显示。 右键单击设备名称，然后单击 " **创建单个设备的部署**"。

    ![创建部署](images/AzureLabs-Lab313-33b.png)

7. 你将看到一个 *文件资源管理器* 提示，你可以在其中导航到 **config** 文件夹，然后选择 " **deployment.js** 文件。 选择该文件后，单击" **选择 Edge 部署清单"** 按钮。

    ![创建部署](images/AzureLabs-Lab313-34.png)

8. 此时，你为 **IoT** 中心服务提供了清单，供其将容器作为模块从 Azure 容器注册表 部署，从而有效地将其部署到设备。

9. 若要查看从设备发送到 IoT 中心的消息，请在 **"Azure IoT** 中心设备"部分中的"资源管理器"面板中再次右键单击设备名称，然后单击"开始监视 **D2C 消息"。** 从设备发送的消息应显示在 VS 终端中。 请耐心等待，因为这可能需要一些时间。 请参阅下一章进行调试，并检查部署是否成功。

此模块现在将在 images 文件夹中的图像之间循环访问，并按每次迭代对其进行分析。 这显然只是演示了如何让基本机器学习模型在IoT Edge环境中工作。 

若要扩展此示例的功能，可以通过多种方式继续操作。 一种方法可能是在容器中包含一些代码，该代码从连接到设备的网络摄像头捕获照片，将图像保存在 images 文件夹中。 

另一种方式可能是将映像从 IoT 设备复制到容器中。 为此，一种实用的方式是在 IoT 设备终端中运行以下命令 (如果你希望自动执行此过程，一个小应用可能会) 。 可以通过从存储文件的文件夹位置手动运行此命令来测试此命令：

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第 10 章 - 调试 IoT Edge 运行时

下面是一系列命令行和提示，可帮助你监视和调试 **Ubuntu** 设备中 *IoT Edge 运行时* 的消息传送活动。 

- 通过 *IoT Edge命令行* 检查运行时状态：

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 请记得按 **Ctrl + C** 完成查看状态。

- 列出当前部署的容器。 如果 *IoT 中心服务* 已成功部署容器，则通过运行以下命令行来显示容器：

    ```bash
        sudo iotedge list
    ```

    或

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 以上是检查模块是否已成功部署的一个好方法，因为它将显示在列表中;否则只会 **看到** *edgeHub* 和 *edgeAgent*。

- 若要显示容器的代码日志，请运行以下命令行：

    ```bash
        journalctl -u iotedge
    ```

**用于管理运行时IoT Edge命令：**

-  删除主机中的所有容器：

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  若要停止 *IoT Edge 运行时*：

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>第 11 章 - 创建表服务 

导航回 Azure 门户，通过创建 Azure 表服务资源，在门户存储服务。

1. 如果尚未登录，请登录到 Azure [门户](https://portal.azure.com)。

2. 登录后，单击左上角的"创建资源"，搜索存储帐户 ，然后按 **Enter** 键开始搜索。 

3. 出现后，从列表中存储 **Blob、文件、表、队列等** 帐户。

    ![搜索存储帐户](images/AzureLabs-Lab313-35.png)

4. 新页面将提供帐户服务 **存储说明**。 在此提示符的左下角，单击" **创建** "按钮，创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab313-36.png)

5. 单击"创建" **后**，将显示一个面板：

    1. 插入此服务 **实例** 的所需名称 (*必须全部小写) 。*

    2. 对于 **"部署模型"，** 请单击 **"资源管理器"。**

    3. 对于 **"帐户类型**"，使用下拉菜单单击存储 (**常规用途 v1) 。**

    4. 单击相应的"**位置"。**
    
    5. 对于" **复制"** 下拉菜单，单击 **RA-GRS** (读取访问异地冗余) 。

    6. 对于 **"性能"，** 请单击"**标准"。**

    7. 在"**需要安全传输"部分中**，单击"**已禁用"。**

    8. 在" **订阅** "下拉菜单中，单击相应的订阅。

    9. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种监视、控制 Azure 资产集合的访问、预配和管理计费的方法。 建议将与单个项目关联的所有 Azure 服务 (例如，这些课程) 位于公共资源组) 。

        > 若要详细了解 Azure 资源组，请按照此 [链接了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。

    10. 如果 **这是一** 个选项 **，** 将"虚拟网络"保留为"已禁用"。

    11. 单击“创建”。

        ![填写存储详细信息](images/AzureLabs-Lab313-37.png)

6. 单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。

7. 创建服务实例后，门户中会显示一条通知。 单击通知以浏览新的服务实例。

    ![新存储通知](images/AzureLabs-Lab313-38.png)

8. 单击 **通知中的**"转到资源"按钮，你将转到新的 存储 服务实例概述页。

    ![转到资源](images/AzureLabs-Lab313-39.png)

9. 在概述页的右侧，单击"表 **"。**
    
    ![表](images/AzureLabs-Lab313-40.png)

10. 右侧面板将更改为显示表 **服务信息，** 其中需要添加新表。 为此，单击左上角的 **"+** 表"按钮。

    ![打开表](images/AzureLabs-Lab313-41.png)

11. 将显示一个新页面，其中需要输入表 **名称**。 这是稍后的创建函数应用 (章节中引用应用程序中数据Power BI) 。 插入 **IoTMessages** 作为名称， (选择自己的名称，只需在本文档稍后使用时记住它，) 单击"确定 **"。** 

12. 创建新表后，可以在底部"表服务"页 (看到) 。 

    ![新创建的表](images/AzureLabs-Lab313-42.png)  

13. 现在 **，单击**"访问密钥"，并使用 记事本) 获取 存储 帐户名和密钥 (的副本。本课程稍后将在创建 Azure Function App 时使用 **这些值**。

    ![新创建的表](images/AzureLabs-Lab313-43.png) 

14. 再次使用左侧的面板，滚动到"表服务"部分，然后单击"表" (或"浏览表"，在较新的门户) 中，使用 记事本) 复制表 **URL** (。  在本课程的稍后部分，将表链接到你的应用程序时，Power BI **此值。**

    ![新创建的表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第 12 章 - 完成 Azure 表

设置表 **服务** 存储帐户后，可以添加数据，用于存储和检索信息。 可以通过使用 来 **编辑Visual Studio。**

1. 打开 **Visual Studio ("Visual Studio Code) "** 。

2. 在菜单中，单击"**查看**  >  Cloud Explorer"。

    ![打开云资源管理器](images/AzureLabs-Lab313-45.png)

3. 该 **Cloud Explorer** 将作为停靠项打开， (患者，因为加载可能需要) 。

    > [!WARNING] 
    > 如果用于创建帐户的订阅存储 *帐户* 不可见，请确保： 
    > - 登录到与用于 Azure 门户的帐户相同的帐户。
    > - 从"帐户管理"页选择了订阅 (可能需要从帐户设置应用筛选器) ：  
    >
    >   ![查找订阅](images/AzureLabs-Lab313-46.png)

4. 将显示 Azure 云服务。 找到 **存储帐户**"，然后单击该帐户左侧的箭头以展开帐户。

    ![打开存储帐户](images/AzureLabs-Lab313-47.png)

5. 扩展后，新存储 **帐户** 应可用。 单击存储左侧的箭头，展开该箭头后，找到"表"，然后单击该表旁边的箭头，以显示在上一章中创建的表。 双击表 **。**

6. 表将在窗口窗口的中心Visual Studio打开。 单击表图标， (**+** 上) 表图标。

    ![添加新表](images/AzureLabs-Lab313-48.png)

7. 将显示一个窗口，提示你添加 *实体*。 你将仅创建一个实体，但它将具有三个属性。 你会注意到 *，PartitionKey* 和 RowKey 已提供，因为表使用这些分区键和 *RowKey* 来查找数据。 

    ![分区键和行键](images/AzureLabs-Lab313-49.png)

8. 请更新以下值：

    - 名称 **：PartitionKey，** 值 **：PK_IoTMessages** 

    - 名称 **：RowKey，** 值 **：RK_1_IoTMessages** 

9. 然后，**单击"添加 ("** 窗口左下角的"添加属性) 并添加以下属性：

    - **作为字符串的 MessageContent***将值* 留空。

10. 你的表应匹配下图中的表：

    ![添加正确的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 实体在行键中具有数字 1 的原因是，如果你希望进一步试验本课程，你可能想要添加更多消息。

11. 完成后 **，** 单击"确定"。 表现已准备就绪，可供使用。

## <a name="chapter-13---create-an-azure-function-app"></a>第 13 章 - 创建 Azure 函数应用 

现在可以创建 *Azure* 函数应用 *，IoT* 中心服务将调用该应用，将 *IoT Edge* 设备消息存储在上一章中创建的表服务中。

首先，需要创建一个文件，使 Azure 函数能够加载所需的库。

1.  打开 **记事本 (** 按 Windows *键*，然后键入 *记事* 本) 。

    ![打开记事本](images/AzureLabs-Lab313-51.png)

2.  打开记事本，将下面的 JSON 结构插入该结构。 完成操作后，将其保存为桌面上的project.js **上**。 此文件定义函数将使用的库。 如果已使用NuGet，它看起来会很熟悉。
    
    > [!WARNING]
    > 命名正确很重要;确保 **该文件没有.txt** 扩展名。 有关参考，请参阅下文：
    >
    > ![JSON 保存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  登录到 [Azure 门户](https://portal.azure.com)。

4.  登录后，单击左上角的"创建资源"，搜索"函数应用"，然后按 **Enter** 键进行搜索。  单击 *结果中的* "函数应用"，打开一个新面板。

    ![搜索函数应用](images/AzureLabs-Lab313-53.png)

5.  新面板将提供函数应用 **服务** 的说明。 在此面板的左下角， **单击"创建** "按钮，创建与此服务的关联。

    ![函数应用实例](images/AzureLabs-Lab313-54.png)

6.  单击"创建 **"后**，填写以下内容：

    1. 对于 **"应用名称**"，请为此服务实例插入所需的名称。

    2. 选择一个“订阅”  。

    3. 选择适合你的定价层，如果这是第一次创建 **函数应用服务**，你应可以使用免费层。

    4. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种监视、控制 Azure 资产集合的访问、预配和管理计费的方法。 建议将与单个项目关联的所有 Azure 服务 (例如，这些课程) 位于公共资源组) 。

        > 若要详细了解 Azure 资源组，请按照此 [链接了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。

    5. 对于OS，Windows，因为这是预期平台。

    6. 选择 **托管计划** (本教程使用消耗 **计划**。

    7. 选择 **"** 位置 (选择与在上一步骤中构建的存储相同的位置) 

    8. 对于 **"存储"****部分，必须选择在上一存储中创建的"服务"。**

    9. 此应用中不需要 *应用程序Insights，* 因此请随意将应用程序保留 **为"关闭"。**

    10. 单击“创建”。

        ![创建新实例](images/AzureLabs-Lab313-55.png)

7.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。

8.  创建服务实例后，门户中会显示一条通知。

    ![新通知](images/AzureLabs-Lab313-56.png)

9.  部署成功后，单击通知 (完成) 。

10. 单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。 

    ![转到资源](images/AzureLabs-Lab313-57.png)

11. 在新面板的左侧，单击"函数 (旁边的 **+**) "图标，以创建新函数。 

    ![添加新函数](images/AzureLabs-Lab313-58.png)

12. 在中央面板中，将显示 **"函数** 创建"窗口。 进一步向下滚动，然后单击"自定义 **函数"。**

    ![自定义函数](images/AzureLabs-Lab313-59.png)

13. 向下滚动下一页，直到找到 **"事件 (IoT) "，** 然后单击它。

    ![自定义函数](images/AzureLabs-Lab313-60.png)

14. 在 **"IoT 中心 (事件**) 边栏选项卡中，将"语言"设置为 **"C#"，****然后单击新的**。

    ![自定义函数](images/AzureLabs-Lab313-61.png)

15. 在出现的窗口中，确保 **已选择"IoT** 中心"，并且 *"IoT* 中心"字段的名称与之前在第 3 章第 8 章步骤 [8](#chapter-3---the-iot-hub-service)中创建的 *ioT* 中心服务 (的名称) 相对应。 然后单击"选择 **"** 按钮。

    ![自定义函数](images/AzureLabs-Lab313-62.png)

16. 返回到 **"IoT 中心" (事件中心) 边栏选项卡**，单击"创建 **"。**

    ![自定义函数](images/AzureLabs-Lab313-63.png)

17. 将重定向到函数编辑器。

    ![自定义函数](images/AzureLabs-Lab313-64.png)

18. 删除所有代码并将其替换为以下内容：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 更改以下变量，以便它们对应于第 11 章第 11章) 的步骤 [11 和 13](#chapter-11---create-table-service)中的相应值 (**Table** 和 存储 值，这些值将在 **存储 帐户中找到**：

    - **tableName，****其中表的名称** 位于存储 **帐户 中**。
    - **tableURL，****其中表的** URL 位于存储帐户 **中**。
    - **storageAccountName**，其值的名称与帐户存储 **名称** 相对应。
    - **storageAccountKey**，具有在之前创建的 存储服务中获取的密钥。

    ![自定义函数](images/AzureLabs-Lab313-65.png)

20. 代码就位后，单击"保存 **"。**

21. 接下来，单击 **\<** () 右侧箭头图标。

    ![自定义函数](images/AzureLabs-Lab313-66.png)

22. 面板会从右侧滑入。 在面板中，单击 **Upload，** 将显示 *"文件浏览器*"。

23. 导航到并单击project.js之前在记事本中创建的 on **文件，** 然后单击"打开 **"** 按钮。 此文件定义函数将使用的库。

    ![自定义函数](images/AzureLabs-Lab313-67.png)

24. 上传文件后，它将显示在右侧面板中。 单击它将在函数编辑器 **中打开** 它。 它的外观 **必须与** 下一张图像完全相同。

    ![自定义函数](images/AzureLabs-Lab313-68.png)

25. 此时，测试函数在表 上存储消息的功能是 *个不错的选择*。 在窗口的右上方，单击"测试 **"。**

    ![自定义函数](images/AzureLabs-Lab313-69.png)

26. 如上图所示 **，在**"请求正文"上插入一条消息，然后单击"运行 **"。** 

27. 函数将运行，并显示结果状态 (你会注意到"输出"窗口上方的绿色"状态 **202** 已接受"，这意味着它是成功调用) ： 

    ![输出结果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第 14 章 - 查看活动消息

如果现在打开Visual Studio (**消息Visual Studio Code) ，** 可以将测试结果可视化，因为它将存储在 *MessageContent* 字符串区域中。

![自定义函数](images/AzureLabs-Lab313-71.png)

表服务和函数应用就位后，Ubuntu 设备消息将显示在 *IoTMessages* 表中。 如果尚未运行，请再次启动设备，并且你将能够使用 Visual Studio Cloud Explorer 在表中查看来自设备和模块 *的结果Visual Studio。*

![可视化数据](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第 15 章 - Power BI设置

若要可视化 IOT 设备的数据，需要设置Power BI (桌面) ，以从刚刚创建的表服务收集数据。  然后 *HoloLens* 版本Power BI将使用该数据可视化结果。

1.  打开Windows 10 上的 Microsoft Store **并搜索** Power BI Desktop。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  下载应用程序。 下载完成后，打开它。

3.  使用 *Power BI* 登录Microsoft 365 **帐户**。 可能会重定向到浏览器进行注册。 注册后，返回到Power BI应用，然后再次登录。

4.  单击"**获取数据"，** 然后单击"更多 **..."。**

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  单击 **"Azure"，存储** Azure 表"，然后单击 **"连接"。** 

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  在创建表服务时，系统会提示你插入前面 ([第 11](#chapter-11---create-table-service)章步骤 13) 收集的表 URL。 插入 URL 后，删除引用表"子文件夹"路径的部分，该路径 (IoTMessages，本课程) 。 最终结果应如下图所示。 然后单击"确定 **"。**

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  在创建表表时存储，系统会提示你插入 (第 11 章步骤[11](#chapter-11---create-table-service)) 中记录存储。 然后单击"连接"。 

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. 将显示 **导航器面板**，勾选"表"旁边的框，然后单击"加载 **"。**

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 表现已加载到Power BI，但它需要查询来显示表中的值。 为此，请右键单击位于屏幕右侧 **"字段** "面板中的表名称。 然后单击"编辑 **查询"。**

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. 一 **Power Query 编辑器**  会作为新窗口打开，并显示表。 单击表的 **"内容** " *列中* 的"记录"一词，将存储的内容可视化。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 单击 **窗口左** 上方的"进入表"。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. 单击"**关闭&应用"。**

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 加载完查询后，在屏幕右侧"**字段**"面板中，勾选与参数"名称"和"值"对应的框，以可视化 **MessageContent** 列内容。 

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 单击窗口 **左上方** 的蓝色磁盘图标，将工作保存到你选择的文件夹中。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 现在，可以单击"发布"按钮将表上传到工作区。 系统提示时，单击 **"我的工作区"，** 然后单击"选择 *"。* 等待它显示提交的成功结果。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 以下章节特定于HoloLens章节。 Power BI目前不作为沉浸式应用程序提供，但可以通过桌面应用在 Windows Mixed Reality 门户 (悬崖小屋) 运行桌面版本。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第 16 章 - 在Power BI上显示HoloLens

1. 在HoloLens，通过点击应用程序Microsoft Store中的图标登录到应用程序。

    ![Power BIH l](images/AzureLabs-Lab313-87.png)

2. 搜索并 **下载Power BI应用程序**。

    ![Power BIH l](images/AzureLabs-Lab313-88.png)

3. 从 **Power BI** 开始运行。 

4. **Power BI** 你可能需要登录到 Microsoft 365 **帐户**。

5. 进入应用后，工作区应默认显示，如下图所示。 如果未发生这种情况，只需单击窗口左侧的工作区图标即可。

    ![Power BIH l](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>已完成 IoT 中心应用程序

祝贺你，你已成功使用模拟的 Virtual Machine Edge 设备创建了 IoT 中心服务。 设备可以将机器学习模型的结果传达给 Azure 表服务，由 Azure 函数应用提供方便，该函数应用可读入 Power BI，并在 Microsoft HoloLens 中可视化。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

展开存储在表中的消息结构，并显示为图形。 可能需要收集更多数据，并存储在同一个表中，以稍后显示。

### <a name="exercise-2"></a>练习 2

创建一个要部署在 IoT 板上的附加"相机捕获"模块，以便它可以通过要分析的相机捕获图像。
