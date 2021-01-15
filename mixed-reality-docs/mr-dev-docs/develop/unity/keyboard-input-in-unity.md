---
title: Unity 中的键盘输入
description: Unity 提供了 TouchScreenKeyboard 类，可用于在没有可用物理键盘时接受键盘输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 键盘，输入，unity，touchscreenkeyboard，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 90416f91a7de369ff97a2254fed4b3773724408b
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226406"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="4b263-104">Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="4b263-104">Keyboard input in Unity</span></span>

<span data-ttu-id="4b263-105">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="4b263-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="4b263-106">**类型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="4b263-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="4b263-107">虽然 HoloLens 支持多种形式的输入，包括蓝牙键盘，但大多数应用程序都无法假定所有用户都有可用的物理键盘。</span><span class="sxs-lookup"><span data-stu-id="4b263-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="4b263-108">如果你的应用程序需要文本输入，则应该提供某种形式的屏幕键盘。</span><span class="sxs-lookup"><span data-stu-id="4b263-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="4b263-109">Unity 提供了 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类，可用于在没有可用物理键盘时接受键盘输入。</span><span class="sxs-lookup"><span data-stu-id="4b263-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="4b263-110">Unity 中的 HoloLens 系统键盘行为</span><span class="sxs-lookup"><span data-stu-id="4b263-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="4b263-111">在 HoloLens 上， *TouchScreenKeyboard* 利用系统的屏幕键盘。</span><span class="sxs-lookup"><span data-stu-id="4b263-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard.</span></span> <span data-ttu-id="4b263-112">系统的屏幕键盘不能叠加在容量耗尽视图的顶部。</span><span class="sxs-lookup"><span data-stu-id="4b263-112">The system's on-screen keyboard can't overlay on top of a volumetric view.</span></span> <span data-ttu-id="4b263-113">Unity 必须创建辅助 2D XAML 视图，以显示键盘，然后在提交输入后返回到容量耗尽视图。</span><span class="sxs-lookup"><span data-stu-id="4b263-113">Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="4b263-114">用户流如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b263-114">The user flow goes like this:</span></span>
1. <span data-ttu-id="4b263-115">用户执行导致应用程序代码调用 *TouchScreenKeyboard* 的操作</span><span class="sxs-lookup"><span data-stu-id="4b263-115">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="4b263-116">在调用 *TouchScreenKeyboard* 之前，应用负责暂停应用状态</span><span class="sxs-lookup"><span data-stu-id="4b263-116">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="4b263-117">应用可能会终止，然后再切换回容量耗尽视图</span><span class="sxs-lookup"><span data-stu-id="4b263-117">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="4b263-118">Unity 切换到了世界上 autoplaced 的 2D XAML 视图</span><span class="sxs-lookup"><span data-stu-id="4b263-118">Unity switches to a 2D XAML view, which is autoplaced in the world</span></span>
3. <span data-ttu-id="4b263-119">用户使用系统键盘输入文本并提交或取消</span><span class="sxs-lookup"><span data-stu-id="4b263-119">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="4b263-120">Unity 切换回容量耗尽视图</span><span class="sxs-lookup"><span data-stu-id="4b263-120">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="4b263-121">应用负责在 *TouchScreenKeyboard* 完成后恢复应用程序状态</span><span class="sxs-lookup"><span data-stu-id="4b263-121">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="4b263-122">提交的文本在 *TouchScreenKeyboard* 中提供</span><span class="sxs-lookup"><span data-stu-id="4b263-122">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="4b263-123">可用的键盘视图</span><span class="sxs-lookup"><span data-stu-id="4b263-123">Available keyboard views</span></span>

<span data-ttu-id="4b263-124">有六种不同的键盘视图可用：</span><span class="sxs-lookup"><span data-stu-id="4b263-124">There are six different keyboard views available:</span></span>
* <span data-ttu-id="4b263-125">单行文本框</span><span class="sxs-lookup"><span data-stu-id="4b263-125">Single-line textbox</span></span>
* <span data-ttu-id="4b263-126">带有标题的单行文本框</span><span class="sxs-lookup"><span data-stu-id="4b263-126">Single-line textbox with title</span></span>
* <span data-ttu-id="4b263-127">多行文本框</span><span class="sxs-lookup"><span data-stu-id="4b263-127">Multi-line textbox</span></span>
* <span data-ttu-id="4b263-128">带有标题的多行文本框</span><span class="sxs-lookup"><span data-stu-id="4b263-128">Multi-line textbox with title</span></span>
* <span data-ttu-id="4b263-129">单行密码框</span><span class="sxs-lookup"><span data-stu-id="4b263-129">Single-line password box</span></span>
* <span data-ttu-id="4b263-130">带有标题的单行密码框</span><span class="sxs-lookup"><span data-stu-id="4b263-130">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="4b263-131">如何在 Unity 中启用系统键盘</span><span class="sxs-lookup"><span data-stu-id="4b263-131">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="4b263-132">HoloLens 系统键盘仅适用于使用 "UWP 版本类型" 设置为 "XAML" 导出的 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4b263-132">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="4b263-133">选择 "XAML" 作为 "UWP 生成类型" over "D3D" 时，会产生一些折衷。</span><span class="sxs-lookup"><span data-stu-id="4b263-133">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="4b263-134">如果你不熟悉这些折衷方案，你可能希望浏览到系统键盘的 [备用输入解决方案](#alternative-keyboard-options) 。</span><span class="sxs-lookup"><span data-stu-id="4b263-134">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="4b263-135">打开 "**文件**" 菜单，然后选择 "**生成设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="4b263-135">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="4b263-136">确保将 **平台** 设置为 **Windows 应用商店**，将 **SDK** 设置为 **通用 10**，并将 **UWP 生成类型** 设置为 **XAML**。</span><span class="sxs-lookup"><span data-stu-id="4b263-136">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="4b263-137">在 " **生成设置** " 对话框中，选择 " **播放机设置 ...** " 按钮</span><span class="sxs-lookup"><span data-stu-id="4b263-137">In the **Build Settings** dialog, select the **Player Settings...** button</span></span>
4. <span data-ttu-id="4b263-138">选择 " **Windows 应用商店设置** " 选项卡</span><span class="sxs-lookup"><span data-stu-id="4b263-138">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="4b263-139">展开 " **其他设置** " 组</span><span class="sxs-lookup"><span data-stu-id="4b263-139">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="4b263-140">在 " **呈现** " 部分中，选中 " **支持虚拟现实** " 复选框，以添加新的 **虚拟现实设备** 列表</span><span class="sxs-lookup"><span data-stu-id="4b263-140">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="4b263-141">确保 **Windows 全息** 出现在虚拟现实 sdk 列表中</span><span class="sxs-lookup"><span data-stu-id="4b263-141">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="4b263-142">如果你没有将生成标记为在 HoloLens 设备上受支持的虚拟现实，则项目将导出为 2D XAML 应用。</span><span class="sxs-lookup"><span data-stu-id="4b263-142">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="4b263-143">在 Unity 应用中使用系统键盘</span><span class="sxs-lookup"><span data-stu-id="4b263-143">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="4b263-144">声明键盘</span><span class="sxs-lookup"><span data-stu-id="4b263-144">Declare the keyboard</span></span>

<span data-ttu-id="4b263-145">在类中，声明一个用于存储 *TouchScreenKeyboard* 的变量，并声明一个用于保存键盘返回的字符串的变量。</span><span class="sxs-lookup"><span data-stu-id="4b263-145">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="4b263-146">调用键盘</span><span class="sxs-lookup"><span data-stu-id="4b263-146">Invoke the keyboard</span></span>

<span data-ttu-id="4b263-147">当请求键盘输入时发生事件时，请根据所需的输入类型，使用 textPlaceholder 参数中的标题调用这些函数之一。</span><span class="sxs-lookup"><span data-stu-id="4b263-147">When an event occurs requesting keyboard input, call one of these functions depending on the type of input you want using the title in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="4b263-148">检索类型化内容</span><span class="sxs-lookup"><span data-stu-id="4b263-148">Retrieve typed contents</span></span>

<span data-ttu-id="4b263-149">在更新循环中，检查键盘是否收到新输入，并将其存储起来供其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="4b263-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.status == TouchScreenKeyboard.Status.Done)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="4b263-150">备用键盘选项</span><span class="sxs-lookup"><span data-stu-id="4b263-150">Alternative keyboard options</span></span>

<span data-ttu-id="4b263-151">我们了解，从容量耗尽视图切换到2D 视图并不是获取用户文本输入的理想方法。</span><span class="sxs-lookup"><span data-stu-id="4b263-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="4b263-152">通过 Unity 使用系统键盘的当前替代方法包括：</span><span class="sxs-lookup"><span data-stu-id="4b263-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="4b263-153">使用语音听写输入 (<b>注意：</b> 这通常容易出错，无法用于字典中找不到的词，也不适合密码条目) </span><span class="sxs-lookup"><span data-stu-id="4b263-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and isn't suitable for password entry)</span></span>
* <span data-ttu-id="4b263-154">在应用程序独占视图中创建工作键盘</span><span class="sxs-lookup"><span data-stu-id="4b263-154">Create a keyboard that works in your applications exclusive view</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="4b263-155">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="4b263-155">Next Development Checkpoint</span></span>

<span data-ttu-id="4b263-156">如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="4b263-156">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="4b263-157">在这里，你可以继续阅读任何 [主题](unity-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或模拟器上部署你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4b263-157">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b263-158">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="4b263-158">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
