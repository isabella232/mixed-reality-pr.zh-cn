---
title: Unity 中的 HP 回音 G2 控制器
description: 了解如何在 SteamVR 和 Windows Mixed Reality Unity 应用程序中设置和使用新的 HP 回音 G2 控制器。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity，回音，回音 G2，HP 回音 G2，mixed reality，开发，运动控制器，用户输入，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发
ms.openlocfilehash: 1c9d8f1279f81ea1d8020e2a3c689dae86496221
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009827"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="37b27-104">Unity 中的 HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="37b27-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="37b27-105">HP 运动控制器是全新类型的 Windows Mixed Reality 控制器：所有相同的跟踪技术都具有一组略有不同的可用输入：</span><span class="sxs-lookup"><span data-stu-id="37b27-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="37b27-106">触摸板已替换为以下两个按钮： A 和 B （适用于右控制器）和 X 和 Y （适用于左侧控制器）。</span><span class="sxs-lookup"><span data-stu-id="37b27-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="37b27-107">抓住现在是一个触发器，用于发布介于0.0 和1.0 之间的值流，而不是使用按下但未按下的按钮。</span><span class="sxs-lookup"><span data-stu-id="37b27-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="37b27-108">由于不能通过现有的 Windows 和 Unity Api 访问新的输入，因此需要专用的 **MixedReality** UPM 包。</span><span class="sxs-lookup"><span data-stu-id="37b27-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="37b27-109">**此包中的类不会替换现有的 Windows 和 Unity Api，但对它们进行了补充。**</span><span class="sxs-lookup"><span data-stu-id="37b27-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="37b27-110">通常可用于经典 Windows Mixed Reality 控制器和 HP 运动控制器的功能可通过使用现有 Api 的相同代码路径进行访问。</span><span class="sxs-lookup"><span data-stu-id="37b27-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="37b27-111">只有新输入需要使用其他 MixedReality 包。</span><span class="sxs-lookup"><span data-stu-id="37b27-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="37b27-112">HP 运动控制器概述</span><span class="sxs-lookup"><span data-stu-id="37b27-112">HP Motion Controller overview</span></span>

<span data-ttu-id="37b27-113">*MixedReality. MotionController* 表示运动控制器。</span><span class="sxs-lookup"><span data-stu-id="37b27-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="37b27-114">每个 *MotionController* 实例都有一个 *XR。WSA.InteractionSource* 对等互连，可使用左右手使用习惯、供应商 ID、产品 id 和版本进行关联。</span><span class="sxs-lookup"><span data-stu-id="37b27-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="37b27-115">可以通过创建 *MotionControllerWatcher* 并订阅其事件来获取 MotionController 实例，类似于使用 *InteractionManager* 事件来发现新的 *InteractionSource* 实例。</span><span class="sxs-lookup"><span data-stu-id="37b27-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="37b27-116">MotionController 的方法和属性说明控制器支持的输入，包括其按钮、触发器、二维轴和操纵杆。</span><span class="sxs-lookup"><span data-stu-id="37b27-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="37b27-117">MotionController 类还公开通过 *MotionControllerReading* 类访问输入状态的方法。</span><span class="sxs-lookup"><span data-stu-id="37b27-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="37b27-118">MotionControllerReading 类表示在给定时间的控制器状态的快照。</span><span class="sxs-lookup"><span data-stu-id="37b27-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="37b27-119">使用 Unity 包管理器安装 MixedReality</span><span class="sxs-lookup"><span data-stu-id="37b27-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="37b27-120">Unity 包管理器使用 [清单文件](https://docs.unity3d.com/Manual/upm-manifestPkg.html) () 上的 # B0 来确定要安装的包以及要安装的注册表 (服务器) 可以从安装这些包。</span><span class="sxs-lookup"><span data-stu-id="37b27-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="37b27-121">你需要注册混合现实组件服务器，然后才能使用 MixedReality 包。</span><span class="sxs-lookup"><span data-stu-id="37b27-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="37b27-122">注册混合现实组件服务器</span><span class="sxs-lookup"><span data-stu-id="37b27-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="37b27-123">对于将使用混合现实输入包的每个项目，"包" 文件夹中文件 (的 manifest.js) 需要添加混合现实范围内的注册表。</span><span class="sxs-lookup"><span data-stu-id="37b27-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="37b27-124">若要正确修改 manifest.js以支持混合现实：</span><span class="sxs-lookup"><span data-stu-id="37b27-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="37b27-125"><projectRoot>在文本编辑器中打开/Packages/manifest.js，如 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="37b27-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="37b27-126">在清单文件的顶部，将混合现实服务器添加到作用域注册表部分，并保存该文件。</span><span class="sxs-lookup"><span data-stu-id="37b27-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="37b27-127">添加 MixedReality 包</span><span class="sxs-lookup"><span data-stu-id="37b27-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="37b27-128"><projectRoot>在文本编辑器中修改/Packages/manifest.json file 的依赖项部分，以添加 mixedreality 包并保存该文件。</span><span class="sxs-lookup"><span data-stu-id="37b27-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="37b27-129">使用 MixedReality</span><span class="sxs-lookup"><span data-stu-id="37b27-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="37b27-130">输入值</span><span class="sxs-lookup"><span data-stu-id="37b27-130">Input values</span></span>

<span data-ttu-id="37b27-131">MotionController 可以公开两种输入：</span><span class="sxs-lookup"><span data-stu-id="37b27-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="37b27-132">按钮和触发器状态由介于0.0 和1.0 之间的唯一浮点值表示，用于指示按下的量。</span><span class="sxs-lookup"><span data-stu-id="37b27-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="37b27-133">按下时，按钮只能返回 0.0 ( (按) 下时未按) 或1.0 时，触发器可以返回 0.0 (完全释放) 到 1.0 (完全按下) 的连续值。</span><span class="sxs-lookup"><span data-stu-id="37b27-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="37b27-134">操纵杆状态由其 X 和 Y 分量介于-1.0 和1.0 之间的 Vector2.y 表示。</span><span class="sxs-lookup"><span data-stu-id="37b27-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="37b27-135">可以使用 *MotionController. GetPressableInputs ( # B1* 返回一个输入列表，该列表返回按 (按钮和触发器) 或 *( MotionController # B5* 方法返回的输入，以返回返回2轴值的输入列表。</span><span class="sxs-lookup"><span data-stu-id="37b27-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="37b27-136">MotionControllerReading 实例表示在给定时间的控制器状态：</span><span class="sxs-lookup"><span data-stu-id="37b27-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="37b27-137">*GetPressedValue ( # B1* 检索按钮或触发器的状态。</span><span class="sxs-lookup"><span data-stu-id="37b27-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="37b27-138">*GetXYValue ( # B1* 检索操纵杆的状态。</span><span class="sxs-lookup"><span data-stu-id="37b27-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="37b27-139">创建缓存以维护 MotionController 实例及其状态的集合</span><span class="sxs-lookup"><span data-stu-id="37b27-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="37b27-140">首先实例化 MotionControllerWatcher 并为其 *MotionControllerAdded* 和 *MotionControllerRemoved* 事件注册处理程序，以保留可用 MotionController 实例的缓存。</span><span class="sxs-lookup"><span data-stu-id="37b27-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="37b27-141">此缓存应是附加到 GameObject 的 MonoBehavior，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="37b27-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="37b27-142">通过轮询读取新输入</span><span class="sxs-lookup"><span data-stu-id="37b27-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="37b27-143">可以在 MonoBehavior 类的 *Update* 方法中通过 *MotionController* 读取每个已知控制器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="37b27-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="37b27-144">要传递 *DateTime。现在* 作为时间戳参数，以确保读取控制器的最新状态。</span><span class="sxs-lookup"><span data-stu-id="37b27-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="37b27-145">可以使用控制器的左右手使用习惯获取控制器的当前输入值：</span><span class="sxs-lookup"><span data-stu-id="37b27-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

<span data-ttu-id="37b27-146">例如，若要读取 InteractionSource 的模拟抓住值：</span><span class="sxs-lookup"><span data-stu-id="37b27-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="37b27-147">从新输入生成事件</span><span class="sxs-lookup"><span data-stu-id="37b27-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="37b27-148">您可以选择将所有状态变化作为事件来处理，而不是每个帧都轮询控制器的状态，这样您就可以更快地处理持久小于帧的操作。</span><span class="sxs-lookup"><span data-stu-id="37b27-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="37b27-149">为了使此方法生效，运动控制器的缓存需要处理控制器自最后一帧后发布的所有状态，可以通过存储从 MotionController 检索到的最后一个 MotionControllerReading 的时间戳并调用 *MotionController ( # B1*：</span><span class="sxs-lookup"><span data-stu-id="37b27-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

<span data-ttu-id="37b27-150">更新缓存内部类后，MonoBehavior 类可以公开两个事件（按下并释放），并从更新 ( # A1 方法中引发它们：</span><span class="sxs-lookup"><span data-stu-id="37b27-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="37b27-151">上述代码示例中的结构使注册事件的可读性更高：</span><span class="sxs-lookup"><span data-stu-id="37b27-151">The structure in the above code examples makes registering events much more readable:</span></span> 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a><span data-ttu-id="37b27-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37b27-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->