---
title: DirectX 中的键盘、鼠标和控制器输入
description: 说明如何为使用键盘、鼠标Windows Mixed Reality游戏控制器的控件创建应用。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、键盘、鼠标、游戏控制器、xbox 控制器、HoloLens、桌面、演练、示例代码
ms.openlocfilehash: 2e83fa0a14a24eb98001c7dc88af062202a2ef9a5eee7cd53e9702dbe4eedc8e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192021"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX 中的键盘、鼠标和控制器输入

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](../native/openxr-getting-started.md)**。

键盘、鼠标和游戏控制器都可以为设备提供有用的Windows Mixed Reality形式。 蓝牙键盘和鼠标都支持HoloLens，用于调试应用或作为输入的备用形式。 Windows Mixed Reality还支持附加到电脑的沉浸式头戴显示设备 -其中鼠标、键盘和游戏控制器一直是标准设备。

若要在设备上使用HoloLens输入，蓝牙键盘与设备配对，或者通过 Windows 设备门户。 若要在沉浸式头戴显示设备Windows Mixed Reality键盘输入，请通过将输入焦点置于设备上或使用键盘组合Windows键 + Y 键盘组合为混合现实分配输入焦点。 请记住，适用于 HoloLens的应用必须提供功能，而无需附加这些设备。

>[!NOTE]
>本文中的代码片段当前演示如何使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，如 [C++](../native/creating-a-holographic-directx-project.md)全息项目模板 中使用的。  这些概念等效于 C++/WinRT 项目，但需要转换代码。

## <a name="subscribe-for-corewindow-input-events"></a>订阅 CoreWindow 输入事件

### <a name="keyboard-input"></a>键盘输入

在Windows应用模板中，我们像任何其他 UWP 应用一样包含键盘输入的事件处理程序。 应用在键盘输入数据中的使用方式与Windows Mixed Reality。

从 AppView.cpp：

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
对于沉浸式桌面头戴显示设备，可以通过实现 **CoreTextEditContext** 支持Windows通过沉浸式视图呈现的虚拟键盘。 这样Windows了解自己应用呈现的文本框的状态，以便虚拟键盘可以正确编辑其中的文本。

有关实现 CoreTextEditContext 支持的信息，请参阅 [CoreTextEditContext 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>鼠标输入

也可再次通过 UWP CoreWindow 输入事件处理程序使用鼠标输入。 下面将了解如何修改全息Windows模板，以支持鼠标单击，方式与按下的手势相同。 进行此修改后，在沉浸式头戴显示设备时单击鼠标将重新定位立方体。

> [!NOTE]
> UWP 应用还可使用 [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API 获取鼠标的原始 XY 数据。

首先，在 AppView.h 中声明新的 OnPointerPressed 处理程序：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView.cpp 中，将此代码添加到 SetWindow：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然后将 OnPointerPressed 的此定义放在文件底部：

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

最后，我们将使用新逻辑更新主类以支持鼠标单击。 首先添加此事件处理程序。 请确保更新类名：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

现在，在 Update 方法中，将获取指针姿势的现有逻辑替换为：

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

重新编译和重新部署。 请注意，鼠标单击现在将在沉浸式头戴显示设备中重新定位立方体，或HoloLens蓝牙鼠标进行重新定位。

### <a name="game-controller-support"></a>游戏控制器支持

游戏控制器是一种有趣且方便的方式，允许用户控制沉浸式Windows Mixed Reality体验。

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

在主类的构造函数中初始化游戏板事件以及当前附加的任何游戏板：

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

将这些事件处理程序添加到主类。 请确保更新类名：

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

最后，更新输入逻辑以识别控制器状态的更改。 在这里，我们使用上一m_pointerPressed中讨论的同一个变量来添加鼠标事件。 将此添加到 Update 方法，就在检查 SpatialPointerPose 之前：

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

清理主类时，不要忘记注销事件：

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

重新编译和重新部署。 现在可以附加或配对游戏控制器，并使用它重新定位旋转的立方体。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>键盘和鼠标输入的重要准则

此代码在 Microsoft HoloLens（一种主要依赖于自然用户输入的设备）上的使用方式与已启用 Windows Mixed Reality 的电脑上存在一些主要差异。
* 不能依赖键盘或鼠标输入来存在。 应用的所有功能都必须用于凝视、手势和语音输入。
* 附加蓝牙键盘时，为应用可能要求的任何文本启用键盘输入会很有帮助。 例如，这可以是听写的一个很好的补充。
* 在设计应用时，请不要依赖 (例如) WASD 和鼠标外观控件。 HoloLens专为用户设计，可四处移动房间。 在这种情况下，用户直接控制照相机。 使用移动/外观控件在房间周围驱动相机的界面不会提供相同的体验。
* 键盘输入是控制应用或游戏引擎调试的极佳方法，尤其是因为用户不需要使用键盘。 使用 CoreWindow 事件 API 连接它的方式与以前相同。 在这种情况下，可以选择实现一种方法，将应用配置为在调试会话期间将键盘事件路由到"仅调试输入"模式。
* 蓝牙控制器也正常工作。

## <a name="see-also"></a>另请参阅
* [硬件配件](../../discover/hardware-accessories.md)