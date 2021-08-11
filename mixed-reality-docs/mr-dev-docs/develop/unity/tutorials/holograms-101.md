---
title: HoloLens（第一代）基础知识 101 - 使用设备完成项目
description: 按照以下编码演练操作，使用 Unity，Visual Studio 和 HoloLens 了解 Windows Mixed Reality 的基本知识。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality，Windows Mixed Reality，HoloLens，全息影像，学院，教程，HoloLens，混合现实学院，unity，混合现实耳机，Windows Mixed reality 耳机，虚拟现实耳机，Windows 10
ms.openlocfilehash: 63219edebeb63dbf4589e8162f8dc1bab83275c38f29b106db9bae234cdabde0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200957"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>HoloLens (第一代) 基础知识101：通过设备完成项目

<br>

>[!IMPORTANT]
>混合现实学院教程的设计目的是 HoloLens (一代) 、Unity 2017 和混合现实沉浸式耳机。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新，可能与新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

本教程将引导你完成 Unity 中内置的一个完整项目，该项目演示了 HoloLens 的核心 Windows Mixed Reality 功能，包括[注视](../../../design/gaze-and-commit.md)、[手势](../../../design/gaze-and-commit.md#composite-gestures)、[语音输入](../../../design/voice-input.md)、[空间音效](../../../design/spatial-sound.md)和[空间映射](../../../design/spatial-mapping.md)。

教程大约需要1小时才能完成。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 基础知识 101：使用设备设置完整的项目</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 使用安装了正确的[工具](../../install-the-tools.md)配置的 Windows 10 PC。
* [为开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的 [文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 。 需要 Unity 2017.2 或更高版本。
  * 如果仍需要 Unity 5.6 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果仍需要 Unity 5.5 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果仍需要 Unity 5.4 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 取消将文件存档到桌面或其他易于访问的位置。 将文件夹名称保留为 **日式折纸**。

>[!NOTE]
>如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)查看。

## <a name="chapter-1---holo-world"></a>第1章-"Holo" 世界

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

在本章中，我们将设置第一个 Unity 项目，并逐步完成生成和部署过程。

### <a name="objectives"></a>目标

* 为全息版开发设置 Unity。
* 制作全息影像。
* 查看您创建的全息影像。

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择“打开”。
* 输入 "位置" 作为以前未存档的 **日式折纸** 文件夹。
* 选择 " **日式折纸** " 并单击 " **选择文件夹**"。
* 由于 **日式折纸** 项目不包含场景，因此请将空的默认场景保存到新文件，使用： **file**  /  **save 场景 As**。
* 将新场景命名为 **日式折纸** ，并按 " **保存** " 按钮。

#### <a name="setup-the-main-virtual-camera"></a>设置主虚拟摄像机

* 在“层次结构面板”中，选择“主摄像头” 。
* **检查器** 将其转换位置设置为 **0，0，0**。
* 找到 " **清除标志** " 属性，然后将下拉列表中的 **Skybox** 更改为 **纯色**。
* 单击“背景”字段以打开颜色选取器。
* 将“R、G、B 和 A”设置为“0” 。

#### <a name="setup-the-scene"></a>设置场景

* 在 " **层次结构" 面板** 中，单击 " **创建** " 并 **创建空**。
* 右键单击新的 " **GameObject** "，然后选择 "重命名"。 将 GameObject 重命名为 **OrigamiCollection**。
* 在 "Project" 面板中的 "**全息影像**" 文件夹中 (展开 "资产" 并选择 "全息影像" 或双击全息影像面板中的 Project 文件夹) ：
  * 将 **阶段** 拖到层次结构中，使其成为 **OrigamiCollection** 的子级。
  * 将 **Sphere1** 拖到层次结构中，使其成为 **OrigamiCollection** 的子元素。
  * 将 **Sphere2** 拖到层次结构中，使其成为 **OrigamiCollection** 的子元素。
* 右键单击 "**层次结构" 面板** 中的 **方向浅** 对象，然后选择 "**删除**"。
* 从 "**全息影像**" 文件夹中，将 "**灯光**" 拖动到 "**层次结构" 面板** 的根。
* 在 **层次结构** 中，选择 " **OrigamiCollection**"。
* 在 **检查器** 中，将转换位置设置为 **0、-0.5、2.0**。
* 按下 Unity 中的 " **播放** " 按钮，预览全息影像。
* 预览窗口中应会显示日式折纸对象。
* 按第二次 **播放** 以停止预览模式。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>将项目从 Unity 导出到 Visual Studio

* 在 Unity 中，选择 "**文件" > 生成设置**。
* 选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。
* 将 **SDK** 设置为 **通用 10** ，将 **类型** 设置为 **D3D**。
* 检查 **Unity c # 项目**。
* 单击 " **添加打开的场景** " 添加场景。
* 单击“生成”。
* 在出现的 "文件资源管理器" 窗口中，创建一个名为 "App" 的 **新文件夹** 。
* 单击 **应用文件夹**。
* 按 " **选择文件夹**"。
* 当 Unity 完成后，将显示文件资源管理器窗口。
* 打开 **应用程序** 文件夹。
* 打开 (双击 ") **日式**"。
* 使用 Visual Studio 中的顶部工具栏将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **X86**"。
* 单击 "设备" 按钮旁边的箭头，并选择 " **远程计算机** " 以通过 wi-fi 进行部署。
  * 将 **地址** 设置为 HoloLens 的名称或 IP 地址。 如果你不知道设备 IP 地址，请查看 **设置 > 网络 & Internet > 高级选项**，或询问 Cortana **"你好 Cortana，我的 IP 地址是什么？"**
  * 如果 HoloLens 通过 usb 连接，则可以选择 "**设备** 通过 usb 进行部署"。
  * 将 **身份验证模式** 设置为 " **通用**"。
  * 单击“选择”

* 单击 " **调试" > "开始但不调试** " 或按 **Ctrl + F5**。 如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。

* 现在，日式折纸项目将生成、部署到您的 HoloLens，然后运行。
* 放在 HoloLens 上，浏览一下新的全息影像。

## <a name="chapter-2---gaze"></a>第2章-注视

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

在本章中，我们将介绍第三种与全息影像交互的方式-- [注视](../../../design/gaze-and-commit.md)。

### <a name="objectives"></a>目标

* 使用全球锁定的光标直观显示注视。

### <a name="instructions"></a>说明

* 返回到 Unity 项目，并关闭 "生成设置" 窗口（如果该窗口仍处于打开状态）。
* 在 " **Project" 面板** 中选择 "**全息影像**" 文件夹。
* 将 **光标** 对象拖到 **层次结构面板** 中的根级别。
* 双击 **光标** 对象以详细查看它。
* 右键单击 "Project" 面板中的 "**脚本**" 文件夹。
* 单击 " **创建** " 子菜单。
* 选择 " **c # 脚本**"。
* 将脚本 **"WorldCursor"命名**。 注意：名称区分大小写。 无需添加 .cs 扩展。
* 在" **层次结构** "面板 **中选择"游标"对象**。
* 将 **WorldCursor 脚本** 拖放到检查 **器面板 中**。
* 双击 **WorldCursor** 脚本以在 Visual Studio。
* 将此代码复制并粘贴到 **WorldCursor.cs 和****"全部保存"** 中。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* 从"文件"和 **"生成>重新生成设置。**
* 返回到之前Visual Studio部署到目标帐户的 HoloLens。
* 当系统提示时，选择"全部重新加载"。
* 单击 **"调试"->启动而不调试"，** 或按 **Ctrl + F5**。
* 现在查看场景，并注意光标如何与对象的形状交互。

## <a name="chapter-3---gestures"></a>第 3 章 - 手势

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

在本章中，我们将添加对手势 [的支持](../../../design/gaze-and-commit.md#composite-gestures)。 当用户选择纸张球体时，我们将通过使用 Unity 的物理引擎打开加速度来使球体下降。

### <a name="objectives"></a>目标

* 使用"选择"手势控制全息影像。

### <a name="instructions"></a>说明

首先，我们将创建一个脚本，然后可以检测"选择"手势。

* 在 **Scripts 文件夹中** ，创建名为 **GazeGestureManager 的脚本**。
* 将 **GazeGestureManager** 脚本拖到 Hierarchy 中的 **OrigamiCollection** 对象上。
* 在 Visual Studio 中打开 **GazeGestureManager** 脚本并添加以下代码：

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* 在 Scripts 文件夹中创建另一个脚本，这次名为 **SphereCommands**。
* 在" **层次结构"视图中展开 OrigamiCollection** 对象。
* 将 **SphereCommands** 脚本拖到"层次结构 **"面板中的 Sphere1** 对象上。
* 将 **SphereCommands** 脚本拖到"层次结构 **"面板中的 Sphere2** 对象上。
* 在脚本Visual Studio脚本进行编辑，将默认代码替换为以下代码：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* 将应用导出、生成并部署到HoloLens。
* 查看其中一个球体。
* 执行选择手势，并观察球体拖放到下面的图面上。

## <a name="chapter-4---voice"></a>第 4 章 - 语音

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

在本章中，我们将添加对两个语音命令[](../../../design/voice-input.md)的支持："重置世界"，将丢弃的球体返回到其原始位置，以及"放置球体"使球体下降。

### <a name="objectives"></a>目标

* 添加始终在后台侦听的语音命令。
* 创建对语音命令做出反应的全息影像。

### <a name="instructions"></a>说明

* 在 Scripts **文件夹中** ，创建名为 **SpeechManager 的脚本**。
* 将 **SpeechManager** 脚本拖到 **层次结构中的 OrigamiCollection** 对象上
* 在 Visual Studio 中打开 **SpeechManager** 脚本。
* 将此代码复制并粘贴到 **SpeechManager.cs 和****"全部保存"中**：

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* 在命令 **中打开 SphereCommands** Visual Studio。
* 将脚本更新为读取，如下所示：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* 将应用导出、生成并部署到HoloLens。
* 查看其中一个球体，并说"**放置球体**"。
* 说"**重置世界**"，让他们回到初始位置。

## <a name="chapter-5---spatial-sound"></a>第 5 章 - 空间声音

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

在本章中，我们将向应用添加音乐，然后对某些操作触发音效。 我们将使用空间 [声音在](../../../design/spatial-sound.md) 3D 空间中为声音提供特定位置。

### <a name="objectives"></a>目标

* 听到你的世界中的全息影像。

### <a name="instructions"></a>说明

* 在 Unity 中，从顶部菜单中选择"编辑> Project 设置 >**音频"**
* 在右侧检查器面板中，找到"空间化程序 **插件**"设置，然后选择 **"MS HRTF 空间化程序"。**
* 从全息影像 **面板** 中的 Project 文件夹中，将 **Ambience** 对象拖到"层次结构面板"中的 **OrigamiCollection** 对象上。
* 选择 **"OrigamiCollection"，** 在"检查器 **"** 面板中查找"音频源"组件。 更改以下属性：
  * 检查 **Spatialize** 属性。
  * 检查"**唤醒时播放"。**
  * 将 **滑块** 一直拖动到右侧，将"空间混合"更改为 **"3D"。** 移动滑块时，该值应从 0 更改为 1。
  * 检查 **Loop** 属性。
  * 展开 **"3D 声音设置"，** 并输入 **"0.1"** 作为 **"Doppler 级别"。**
  * 将 **"卷回滚"** 设置为 **"对数回退"。**
  * 将 **"最大距离"** 设置为 **20。**
* 在 Scripts **文件夹中** ，创建名为 **SphereSounds 的脚本**。
* 将 **SphereSounds** 拖放到 **层次结构中的 Sphere1** 和 **Sphere2** 对象。
* 在 **"应用"中Visual Studio SphereSounds，** 更新以下代码并 **"全部保存"。**

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 保存脚本并返回到 Unity。
* 将应用导出、生成并部署到HoloLens。
* 从"阶段"中移近和进一步，并并排打开来听到声音变化。

## <a name="chapter-6---spatial-mapping"></a>第 6 章 - 空间映射

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

现在，我们将使用 [空间映射](../../../design/spatial-mapping.md) 将游戏板放在现实世界中的真实对象上。

### <a name="objectives"></a>目标

* 将现实世界引入虚拟世界。
* 将全息影像放在最重要的位置。

### <a name="instructions"></a>说明

* 在 Unity 中，**单击全息影像** 面板中的 Project 文件夹。
* 将 **空间映射资产** 拖到层次结构 的 **根目录**。
* 单击" **层次结构"中的** "空间映射"对象。
* 在" **检查器"** 面板中，更改以下属性：
  * 选中" **绘制视觉对象网格"** 框。
  * 找到 **"绘制** 材料"，然后单击右侧圆圈。 在顶部的 **搜索字段中键入"wireframe"。** 单击结果，然后关闭窗口。 这样做时，"绘制材料"的值应设置为"线框"。
* 将应用导出、生成并部署到HoloLens。
* 应用运行时，线框网格将覆盖现实世界。
* 观看滚动球体如何从阶段滑出，并滑到楼层！

现在，我们将展示如何将 OrigamiCollection 移动到新位置：

* 在" **脚本"** 文件夹中，创建名为 **TapToPlaceParent 的脚本**。
* 在" **层次结构"中**，展开 **"OrigamiCollection"** 并选择 **"Stage"** 对象。
* 将 **TapToPlaceParent 脚本** 拖到 Stage 对象上。
* 在 Visual Studio 中打开 **TapToPlaceParent** 脚本，并更新为以下内容：

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 导出、生成和部署应用。
* 现在，你应能够将游戏放在特定位置，具体方法为：在游戏上操作，使用"选择"手势，然后移动到新位置，然后再次使用"选择"手势。

## <a name="chapter-7---holographic-fun"></a>第 7 章 - 全息有趣

### <a name="objectives"></a>目标

* 揭示进入全息世界。

### <a name="instructions"></a>说明

现在，我们将展示如何发现全息下部：

* 从 **全息影像** 面板中的Project文件夹：
  * 将 **Underworld** 拖动到层次结构中，成为 **OrigamiCollection 的子级**。
* 在 Scripts **文件夹中** ，创建名为 **HitTarget 的脚本**。
* 在"**层次结构"中**，展开 **"OrigamiCollection"。**
* 展开" **阶段"** 对象，然后选择蓝色 **风扇 (目标**) 。
* 将 **HitTarget 脚本** 拖到 **Target 对象** 上。
* 在 Visual Studio 中打开 **HitTarget** 脚本，并更新为以下内容：

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* 在 Unity 中，选择 **"目标"** 对象。
* 现在，命中目标组件上显示两个 **公共** 属性，需要引用场景中的对象：
  * 将 **"Underworld"** 从"**层次结构"面板** 拖到"命中目标"组件 **上的"Underworld"** 属性。 
  * 将 **"阶段**"**从"层次结构"面板** 拖到"**对象"，以隐藏****"命中目标"组件** 上的属性。
* 导出、生成和部署应用。
* 将 Origami 集合放在楼层上，然后使用"选择"手势进行球体放置。
* 当球体命中蓝色风扇 (目标) ，将发生爆炸。 集合将被隐藏，并且下层会出现一个孔。

## <a name="the-end"></a>结束

这就是本教程的结束！

你已了解：

* 如何在 Unity 中创建全息应用。
* 如何使用凝视、手势、语音、声音和空间映射。
* 如何使用应用程序生成和部署Visual Studio。

现在可以开始创建自己的全息体验了！

## <a name="see-also"></a>另请参阅

* [MR 基础知识 101E：使用仿真器完成项目](holograms-101e.md)
* [凝视](../../../design/gaze-and-commit.md)
* [头部凝视并提交](../../../design/gaze-and-commit.md)
* [语音输入](../../../design/voice-input.md)
* [空间音效](../../../design/spatial-sound.md)
* [空间映射](../../../design/spatial-mapping.md)