---
title: HoloLens（第一代）共享 240 - 多个 HoloLens 设备
description: 按照此编码演练使用 Unity、Visual Studio和HoloLens了解共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit， mixedrealitytoolkit， mixedrealitytoolkit-unity， 共享， 网络， 学院， 教程， HoloLens， 混合现实学院， unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208697"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (共享 240) 第一代设备：HoloLens设备

>[!IMPORTANT]
>混合现实学院教程的设计HoloLens (第一代) Unity 2017 和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不会使用_** 最新工具集或交互进行更新HoloLens 2并且可能与较新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

全息影像在太空中移动时保持就位，使世界保持这种状态。 HoloLens使用各种坐标系来跟踪对象的位置和方向，使全息[](../../../design/coordinate-systems.md)影像保持就位。 当我们在设备之间共享这些坐标系时，我们可以创建一个共享体验，使我们能够参与共享的全息世界。

在本教程中，我们将：

* 为共享体验设置网络。
* 跨设备共享全息HoloLens影像。
* 发现共享全息世界中的其他人。
* 创建可面向其他玩家的共享交互式体验 ， 并针对他们启动项目！

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 共享 240：多个 HoloLens 设备</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 使用Windows 10 Internet 访问权限安装的正确[工具配置的电脑](../../../develop/install-the-tools.md)。
* 至少两HoloLens[配置用于开发 的设备](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载 [项目](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 所需的文件。 需要 Unity 2017.2 或更高版本。
  * 如果仍然需要 Unity 5.6 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果仍然需要 Unity 5.5 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果仍然需要 Unity 5.4 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 将文件取消存档到桌面或其他易于访问的位置。 将文件夹名称保留为 **SharedHolograms**。

>[!NOTE]
>如果要在下载之前查看源代码，可在[GitHub。](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)

## <a name="chapter-1---holo-world"></a>第 1 章 - Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中，我们将设置第一个 Unity 项目并逐步完成生成和部署过程。

### <a name="objectives"></a>目标

* 设置 Unity 以开发全息应用。
* 查看全息影像！

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择“打开”。
* 输入 location 作为之前未搜索的 **SharedHolograms** 文件夹。
* 选择 **Project名称"，** 然后单击"**选择文件夹"。**
* 在"**层次结构"中**，右键单击 **主相机并选择**"删除 **"。**
* 在 **HoloToolkit-Sharing-240/Prefabs/Camera** 文件夹中，找到 **主相机** 预制。
* 将主相机 **拖放** 到层次结构 **中**。
* 在"**层次结构"中**，单击"**创建"** 和"**创建空"。**
* 右键单击新的 **GameObject，然后选择**"重命名 **"。**
* 将 GameObject 重命名为 **HologramCollection**。
* 在" **层次结构"中选择 HologramCollection** **对象**。
* 在检查 **器中**，**将转换位置设置为****：X： 0， Y： -0.25， Z： 2**。
* 在全息影像 **面板** 中的 Project **文件夹中**，找到 **EnergyHub** 资产。
* 将 **EnergyHub** 对象从"Project"**面板** 拖放到"层次结构"，作为 **HologramCollection 的子级**。
* 选择 **"文件>将场景另存为..."**
* 将场景命名 **SharedHolograms，然后单击**"保存 **"。**
* 按 Unity **中的** "播放"按钮预览全息影像。
* 按 **"第** 二次播放"以停止预览模式。

**将项目从 Unity 导出到Visual Studio**

* 在 Unity 中 **，选择"文件>生成设置"。**
* 单击 **"添加打开的** 场景"以添加场景。
* 在 **"平台Windows****选择"通用** 平台"，然后单击"**切换平台"。**
* 将 **SDK 设置为** 通用 **10。**
* 将 **"目标设备**"**设置为"HoloLens"，** 将 **"UWP 生成类型"设置为****"D3D"。**
* 检查 **Unity C# 项目**。
* 单击“生成”。
* 在出现的文件资源管理器窗口中，创建名为 **"App"** 的新文件夹。
* 单击"应用 **"** 文件夹。
* 按 **"选择文件夹"。**
* Unity 完成后，将显示文件资源管理器窗口。
* 打开 **"应用"** 文件夹。
* 打开 **SharedHolograms.sln** 以启动Visual Studio。
* 使用中的顶部工具栏Visual Studio，将目标从"调试"更改为"发布 **"，从**"ARM"更改为 **"X86"。**
* 单击"本地计算机"旁边的下拉箭头，然后选择"**远程设备"。**
    * 将 **"地址**"设置为目标服务器的名称或 IP HoloLens。 如果不知道设备 IP 地址，请查找 **设置 > Network & Internet > 高级选项**，或询问 **Cortana"你好 Cortana，我的 IP 地址是什么？"**
    * 将"**身份验证模式"保留** 设置为"**通用"。**
    * 单击“选择”
* 单击 **"调试>启动而不调试"，** 或按 **Ctrl + F5**。 如果这是首次部署到设备，则需要将其与[Visual Studio。](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)
* 打开你的HoloLens并找到 EnergyHub 全息影像。

## <a name="chapter-2---interaction"></a>第 2 章 - 交互

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中，我们将与全息影像进行交互。 首先，我们将添加一个光标来可视化凝 [视](../../../design/gaze-and-commit.md)。 然后，我们将添加 [手势](../../../design/gaze-and-commit.md#composite-gestures) ，并使用手将全息影像放在太空中。

### <a name="objectives"></a>目标

* 使用凝视输入来控制光标。
* 使用手势输入与全息影像交互。

### <a name="instructions"></a>说明

**凝视**

* 在" **层次结构"面板中** ，选择 **HologramCollection** 对象。
* 在" **检查器"面板中** ，单击" **添加组件"** 按钮。
* 在菜单中，键入搜索框"凝视 **管理器"。** 选择搜索结果。
* 在 **HoloToolkit-Sharing-240\Prefabs\Input** 文件夹中，找到 **Cursor** 资产。
* 将光标资产 **拖放** 到"层次结构 **"上**。

**手势**

* 在" **层次结构"面板中** ，选择 **HologramCollection** 对象。
* 单击 **"添加组件** "，在搜索字段中键入" **笔** 势管理器"。 选择搜索结果。
* 在"**层次结构"面板中**，展开 **"HologramCollection"。**
* 选择子 **EnergyHub** 对象。
* 在" **检查器"面板中** ，单击" **添加组件"** 按钮。
* 在菜单中，键入搜索框"全息 **影像放置"。** 选择搜索结果。
* 通过选择"文件""保存 **场景>保存场景**。

**部署和享受**

* 使用上一章中的HoloLens生成并部署到你的应用程序。
* 应用在应用上启动HoloLens，请四处移动，并注意 EnergyHub 如何跟随你的凝视。
* 请注意在凝视全息影像时光标的显示方式，在未在全息影像上凝视时，光标会变为点光。
* 执行空敲击以放置全息影像。 目前，在我们的项目中，只能在重新部署后放置全息 (，以重试) 。

## <a name="chapter-3---shared-coordinates"></a>第 3 章 - 共享坐标

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

查看全息影像并与之交互很有趣，但让我们进一步吧。 我们将设置第一个共享体验 - 每个人都可以看到的全息影像。

### <a name="objectives"></a>目标

* 为共享体验设置网络。
* 建立公共参考点。
* 跨设备共享坐标系。
* 每个人都会看到相同的全息影像！

>[!NOTE]
>必须 **声明 InternetClientServer** 和 **PrivateNetworkClientServer** 功能，应用必须连接到共享服务器。 此操作已在 240 全息影像中完成，但对于你自己的项目，请记住这一点。

>1. 在 Unity 编辑器中，导航到"编辑播放器"，转到> Project 设置 >设置
>2. 单击"Windows Store"选项卡
>3. 在"发布设置 >"部分中，检查 **InternetClientServer** 功能和 **PrivateNetworkClientServer** 功能

### <a name="instructions"></a>说明

* 在Project **面板中**，导航到 **HoloToolkit-Sharing-240\Prefabs\Sharing** 文件夹。
* 将"共享 **"** 预制块拖放到" **层次结构"面板中**。

接下来，需要启动共享服务。 共享 **体验** 中只有一台电脑需要执行此步骤。

* 在 Unity 中（在顶部菜单中）选择 **"HoloToolkit-Sharing-240"菜单**。
* 在 **下拉列表中选择** "启动共享服务"项。
* 选中" **专用网络"** 选项， **在出现防火墙提示时** 单击"允许访问"。
* 记下共享服务控制台窗口中显示的 IPv4 地址。 这是与运行服务计算机相同的 IP。

按照所有将加入共享体验 **的 PC** 上的其余说明进行操作。

* 在" **层次结构"中**，选择 **"共享"** 对象。
* 在 **检查器** 中，在"共享阶段"组件上，将服务器地址从"localhost"更改为运行 SharingService.exe。
* 在" **层次结构"中** ，选择 **HologramCollection** 对象。
* 在检查 **器中** ，单击 **"添加组件"** 按钮。
* 在搜索框中，键入 **"导入导出定位点管理器"。** 选择搜索结果。
* 在 **"Project"面板** 中，导航到 **"脚本"** 文件夹。
* 双击 **HologramPlacement 脚本** 以在 Visual Studio。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 返回 Unity，在"层次结构"**面板中选择"HologramCollection"。** 
* 在" **检查器"面板中** ，单击" **添加组件"** 按钮。
* 在菜单中，在搜索框中键入"**应用状态管理器"。** 选择搜索结果。

**部署和享受**

* 为设备生成HoloLens项目。
* 指定一HoloLens要首先部署到的映像。 需要等待定位点上传到服务，然后才能放置 EnergyHub (这可能需要大约 30-60) 。 上传完成之前，点击手势将被忽略。
* 放置 EnergyHub 后，其位置将上传到服务，然后你可以部署到所有其他HoloLens设备。
* 当新HoloLens加入会话时，EnergyHub 的位置可能不正确。 但是，一旦从服务下载定位点和 EnergyHub 位置，EnergyHub 就会跳转到新的共享位置。 如果未在大约 30-60 秒内发生此情况，请HoloLens定位点时原始位置，以收集更多环境线索。 如果位置仍未锁定，请重新部署到设备。
* 设备准备就绪并运行应用后，查找 EnergyHub。 你能否同意全息影像的位置以及文本的方向？

## <a name="chapter-4---discovery"></a>第 4 章 - 发现

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

现在每个人都可以看到相同的全息影像！ 现在，让我们看看其他连接到共享全息世界的人。 在本章中，我们将在同一共享会话中抓取所有其他设备HoloLens和旋转。

### <a name="objectives"></a>目标

* 在我们的共享体验中发现彼此。
* 选择并共享播放器头像。
* 将玩家头像附加到每个人的头旁边。

### <a name="instructions"></a>说明

* 在Project **面板** 中，导航 **到全息影像文件夹**。
* 将 **PlayerAvatarStore** 拖放到 **层次结构 中**。
* 在 **"Project"面板** 中，导航到 **"脚本"** 文件夹。
* 双击 **"头像""elector"** 脚本，在Visual Studio。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* 在" **层次结构"中** ，选择 **HologramCollection** 对象。
* 在检查 **器中，** 单击 **"添加组件"。**
* 在搜索框中，键入"**本地播放器管理器"。** 选择搜索结果。
* 在" **层次结构"中** ，选择 **HologramCollection** 对象。
* 在检查 **器中，** 单击 **"添加组件"。**
* 在搜索框中，键入 **"远程播放器管理器"。** 选择搜索结果。
* 在 Visual Studio 中打开 **HologramPlacement** 脚本。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 在 Visual Studio 中打开 **AppStateManager** 脚本。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**部署和享受**

* 生成项目并部署到HoloLens设备。
* 听到 ping 声音时，找到头像选择菜单，然后使用隔空敲击手势选择头像。
* 如果未查看任何全息影像，当 HoloLens 与服务通信时，光标周围的点光将变为不同的颜色：初始化 (深紫色) 、下载定位点 (绿色) 、导入/导出位置数据 (黄色) 、上传定位点 (蓝色) 。 如果光标周围的点光是浅紫色 (颜色) ，则你已准备好与会话中的其他玩家交互！
* 看看连接到你的太空的其他人 - 将存在一个全息机器人浮动在他们上面，并模拟他们的头部运动！

## <a name="chapter-5---placement"></a>第 5 章 - 放置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中，我们将使定位点能够放置在实际表面上。 我们将使用共享坐标将定位点放在连接到共享体验的所有人之间的中间点。

### <a name="objectives"></a>目标

* 根据玩家的头位置将全息影像放在空间映射网格上。

### <a name="instructions"></a>说明

* 在 **Project 面板** 中，导航到 **全息影像** 文件夹。
* 将 **CustomSpatialMapping** prefab 拖放到 **层次结构** 中。
* 在 **Project 面板** 中，导航到 **Scripts** 文件夹。
* 双击 " **AppStateManager** " 脚本，在 Visual Studio 中打开它。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* 在 **Project 面板** 中，导航到 **Scripts** 文件夹。
* 双击 " **HologramPlacement** " 脚本，在 Visual Studio 中打开它。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**部署和体验**

* 生成项目并将其部署到 HoloLens 设备。
* 当应用程序准备就绪时，请将其放在一个圆圈上，并注意 EnergyHub 如何出现在每个人的中心。
* 点击以放置 EnergyHub。
* 尝试使用语音命令 "重置目标" 来选择 EnergyHub 备份，并以组的形式协同工作，以便将全息图移动到新位置。

## <a name="chapter-6---real-world-physics"></a>第6章-Real-World 物理学

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在本章中，我们将添加从实际表面弹跳的全息影像。 观看您和您的朋友所启动的项目的空间。

### <a name="objectives"></a>目标

* 启动炮弹，从实际表面弹跳。
* 共享炮弹，使其他玩家可以看到它们。

### <a name="instructions"></a>说明

* 在 **层次结构** 中，选择 " **HologramCollection** " 对象。
* 在 **检查器** 中单击 " **添加组件**"。
* 在搜索框中，键入 " **Projectile Launcher**"。 选择搜索结果。

**部署和体验**

* 生成并部署到 HoloLens 设备。
* 当应用程序在所有设备上运行时，请在实际的表面上执行轻点击以启动 projectile。
* 了解 projectile 与其他玩家的头像发生冲突时会发生什么情况！

## <a name="chapter-7---grand-finale"></a>第7章-总计 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中，我们将发现一个只能通过协作发现的门户。

### <a name="objectives"></a>目标

* 协同工作，在定位点上启动足够的炮弹来发现机密门户！

### <a name="instructions"></a>说明

* 在 **Project 面板** 中，导航到 **全息影像** 文件夹。
* 将 **Underworld** 资产拖放为 HologramCollection 的 **子项**。
* 选择 **HologramCollection** 后，在 **检查器** 中单击 "**添加组件**" 按钮。
* 在菜单中，在 "搜索" 框中键入 **ExplodeTarget**。 选择搜索结果。
* 选择 **HologramCollection** 后，从 **层次结构** 中，**将 EnergyHub** 对象拖到 **检查器** 中的 **目标** 字段。
* 选择 **HologramCollection** 后，从 **层次结构** 中，**将 Underworld** 对象拖到 **检查器** 中的 **Underworld** 字段。

**部署和体验**

* 生成并部署到 HoloLens 设备。
* 当应用程序启动时，在 EnergyHub 上协作以启动炮弹。
* 显示 underworld 时，请在 underworld 机器人上启动炮弹 (按下机器人三次，以) 额外的乐趣。