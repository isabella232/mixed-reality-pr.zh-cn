---
title: DirectX 中的键盘、鼠标和控制器输入
description: 说明如何为使用键盘、鼠标和游戏控制器的 Windows Mixed Reality 创建应用程序。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality，键盘，鼠标，游戏控制器，xbox 控制器，HoloLens，桌面，演练，示例代码
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244179"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX 中的键盘、鼠标和控制器输入

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](../native/openxr-getting-started.md)**。

键盘、鼠标和游戏控制器对于 Windows Mixed Reality 设备，都可以提供有用的输入形式。 蓝牙键盘和鼠标在 HoloLens 上都受支持，可用于调试应用或作为输入的替代形式。 Windows Mixed Reality 还支持附加到电脑的沉浸式耳机，其中鼠标、键盘和游戏控制器一直是标准的。

若要在 HoloLens 上使用键盘输入，请将蓝牙键盘配对到设备，或通过 Windows 设备门户使用虚拟输入。 若要在戴上 Windows Mixed Reality 沉浸式耳机时使用键盘输入，请将输入焦点置于设备上，或使用 Windows 键 + Y 键盘组合将输入焦点分配给混合现实。 请记住，针对 HoloLens 的应用必须提供未连接这些设备的功能。
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>本文中的代码片段当前演示了如何 [使用 c +](../native/creating-a-holographic-directx-project.md)+/cx 中的 c + +/cx 而不是 c + + 17 兼容 c + +/WinRT。  概念与 c + +/WinRT 项目等效，但你将需要转换代码。

## <a name="subscribe-for-corewindow-input-events"></a>订阅 CoreWindow 输入事件

### <a name="keyboard-input"></a>键盘输入

在 Windows 全息应用程序模板中，为键盘输入添加了一个事件处理程序，就像其他任何 UWP 应用一样。 应用以与 Windows Mixed Reality 中相同的方式使用键盘输入数据。

从 AppView：

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>虚拟键盘输入
对于沉浸式桌面耳机，可以通过实现 **CoreTextEditContext** 来支持通过沉浸式视图 Windows 呈现的虚拟键盘。 这使 Windows 了解你自己的应用呈现的文本框的状态，因此虚拟键盘可以正确地参与到文本中。

有关实现 CoreTextEditContext 支持的详细信息，请参阅 [CoreTextEditContext 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>鼠标输入

还可以通过 UWP CoreWindow 输入事件处理程序再次使用鼠标输入。 下面介绍了如何修改 Windows 全息应用程序模板，以支持通过与按下手势相同的方式进行鼠标单击。 进行此修改后，在戴上沉浸式耳机设备时，单击鼠标将重新定位该多维数据集。

> [!NOTE]
> UWP 应用还可以通过使用 [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API 获取鼠标的原始 XY 数据。

首先在 AppView 中声明新的 OnPointerPressed 处理程序：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView 中，将以下代码添加到 SetWindow：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然后将此定义 OnPointerPressed 到文件底部：

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

我们刚刚添加的事件处理程序是模板主类的传递。 让我们修改主类以支持此传递。 将此公共方法声明添加到头文件中：

```
// Handle mouse input.
       void OnPointerPressed();
```

还需要此私有成员变量：

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最后，我们将利用新的逻辑更新主类，以支持鼠标单击。 首先添加此事件处理程序。 请确保更新类名称：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

现在，在 Update 方法中，将现有逻辑替换为包含以下内容的指针：

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

重新编译和重新部署。 请注意，鼠标单击现在会在附加了蓝牙鼠标的情况中，将立方体重定位到沉浸式耳机或 HoloLens 中。

### <a name="game-controller-support"></a>游戏控制器支持

游戏控制器是允许用户控制沉浸式 Windows Mixed Reality 体验的一种有趣且方便的方式。

 将以下私有成员声明添加到主文件的标头类：

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

在主类的构造函数中初始化游戏板事件和当前附加的任何 gamepads：

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

将这些事件处理程序添加到您的主类。 请确保更新类名称：

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

最后，更新输入逻辑以识别控制器状态的更改。 此处，我们使用上述部分中讨论的同一个 m_pointerPressed 变量来添加鼠标事件。 将此添加到 Update 方法，就像它在何处检查 SpatialPointerPose：

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

清理主类时，请不要忘记取消注册事件：

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

重新编译和重新部署。 你现在可以附加或配对游戏控制器，并使用它来重新定位旋转立方体。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>键盘和鼠标输入的重要指导原则

在 Microsoft HoloLens 上使用此代码的方式有一些重要差异–这是一个主要依赖于自然用户输入的设备，与支持 Windows Mixed Reality 的 PC 上提供的内容有关。
* 不能依靠键盘或鼠标输入。 你的所有应用程序功能都必须使用注视、手势和语音输入。
* 附加蓝牙键盘时，为你的应用程序可能要求的任何文本启用键盘输入会很有帮助。 例如，这可以是一个很好的听写补充。
* 在设计应用程序时，不要依赖 (例如) WASD 和用于游戏的鼠标外观控件。 HoloLens 旨在使用户能够浏览房间。 在这种情况下，用户直接控制相机。 使用移动/外观控制来围绕房间来驱动照相机的接口不能提供相同的体验。
* 键盘输入是控制您的应用程序或游戏引擎调试的绝佳方式，特别是因为用户不需要使用键盘。 将其与你一起使用，与 CoreWindow 事件 Api 相同。 在这种情况下，你可以选择实现一种方法，以将你的应用程序配置为在调试会话期间将键盘事件路由到 "仅调试输入" 模式。
* 蓝牙控制器也能正常工作。

## <a name="see-also"></a>另请参阅
* [硬件配件](../../discover/hardware-accessories.md)