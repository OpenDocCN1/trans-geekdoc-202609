

注意：如果不确定是哪个应用程序的 `samplesPerSecond` 必须与训练模型时使用的数据匹配，请考虑这个示例：假设你使用 200 个样本的预测窗口训练了模型，而数据采集频率为每秒 100 个样本。这意味着模型将学习识别高度详细的、两秒长的数据块中的动作。如果你在将 `samplesPerSecond` 设置为 8 的情况下运行此程序，它将需要 20 秒的时间来收集预期的 200 个样本！此时，你的模型将查看 20 秒的数据，但会像评估 2 秒钟的数据那样对其进行评估，因为它是那样学习的。这几乎肯定会让这些序列中的模式看起来与模型在训练期间看到的不同。请记住，机器学习模型只有在处理与训练期间数据相似的数据时效果良好，因此在这里采样率错误可能会会让一个完美的模型看起来完全坏了。

同样，本章讨论的模型期望一次处理 20 个样本的块数据，且每个样本有 6 个特征。`windowSize` 和 `numFeatures` 常量捕捉了这些预期。

> 注意：如果你正在使用 Puri Create 的活动分类器，并且不确定预期的特征数量和窗口大小，你可以通过查看 Xcode 项目导航器中的 .model 文件来找到它们。然而，这不包括关于运动数据需要处理速率的信息，所以你只需要留意这一点。

现在你已经添加了常量，就可以通过设置 `CMotionManager` 的更新间隔来完成启动代码中 `enableMotionUpdates` 的实现。要这样做，请在 `enableMotionUpdates` 内部调用 `startDeviceMotionUpdates` 之前添加以下行：

```
motionManager.deviceMotionUpdateInterval = 1.0 / Config.samplesPerSecond
```

就像在 `GestureDataRecord` 中一样，这告诉 MotionManager 每秒向你的应用程序交付 25 次更新——每隔 0.04 秒一次。

Core ML 模型（如 `GestureClassifier`）以 `MLMultiArray` 对象的格式接收输入。遗憾的是，处理这些对象涉及大量的类型转换。Swift 的类型安全非常棒，显式的类型转换强制开发人员对代码更加严谨——但我想我们都能同意，当有太多的转换时，代码非常难看。为了将这种丑陋以及它所需的额外输入降到最低，你将在便利方法中隔离 `MLMultiArray` 特有的代码。在 `GameViewController` 的 `MARK: Core ML methods` 下方添加这些方法中的第一个：

```
static func makeMLMultiArray(numSamples: Int) ->
MLMultiArray? {
    return try MLMultiArray(
        shape: [1, numSamples, Config.numFeatures] as [NSNumber],
        dataType: MLMultiArrayDataType.double
    )
}
```

该函数接收数组应包含的样本数作为输入。然后尝试创建一个形状和数据类型与我们的模型匹配的 `MLMultiArray`：分别为 `[1, numSamples, Config.numFeatures]` 和 `double`。注意形状需要被转换为 `NSNumber` 数组——在处理 `MLMultiArrays` 时，你会看到很多此类类型的转换。

尝试创建 `MLMultiArray` 可能会因抛出异常而失败。如果在这里发生这种情况，`try?` 会导致此函数返回 `nil`。这可能发生在某些情况下，例如没有足够的内存来创建请求的数组。希望这永远不会发生，但你稍后会添加一些代码来处理这种可能性。

现在你有了该函数，将使用它来创建一个空间以存储运动数据，并作为模型的输入。在 `// MARK: Core ML properties` 注释下方区域添加以下属性：

```
let modelInput: MLMultiArray =
GameViewController.makeMLMultiArray(numSamples:
Config.windowSize)
```

这创建了 `modelInput` 数组，其大小适用于你训练的模型。稍后你将在将其传递给模型进行分类之前，用运动数据填充此数组。

> 注意：你可能注意到 `modelInput` 被声明为隐式解包可选类型，`makeMLMultiArray` 可以返回 `nil`。这难道不是意味着如果你在 `modelInput` 为 `nil` 时尝试解包它，会有应用程序崩溃的风险吗？通常这是一个问题，但稍后你将添加一些代码来确保这种情况永远不会发生。

# 机器学习

## 重叠预测窗口

现在，下面的图显示了它的样子：

![](img/5720be5c3cca252e12448e68d25607b5_427_0.png)

如上图所示，数组在 $T1$ 和 $T20$ 时间填充，然后你将其传递给模型。这种技术代码编写最简单，适用于许多应用程序。然而，在某些情况下，这会导致一些问题。考虑另一种场景，如下图所示：

![](img/5720be5c3cca252e12448e68d25607b5_427_1.png)

在这种情况下，第一个窗口中的数据量足够模型识别它。但如果模型需要的数据比第一个窗口提供的要多，它将等到 10 个样本后才能进行分类。更糟糕，第二个窗口中的所有数据可能会导致第二次预测失败。延迟响应或不准确的预测——任选其一，都不是好主意。该程序运行起来更加灵敏，且不会错过活动。重叠预测很大程度上解决了上述问题。但根据模型做出预测需要看到的数据以及你窗口的重叠程度，你可能仍然会遇到或错误分类。这取决于为你的应用程序找到最佳重叠量。

你将在 `Gesture` 中实现重叠预测，因为你希望快速响应以评估玩家的手势。但如果你正在制作一个跟踪跑步时间的应用程序，你可能可以接受长时间内（例如每几秒一次）的非重叠预测。

> 注意：预测的重叠程度直接影响的不只是准确性和响应时间。更多的重叠意味着更频繁地进行模型推理，额外的处理可能会增加电耗。取决于模型做出预测所需的时间，它可能无法跟上请求速度，导致应用程序出现其他性能问题。因此，请测试各种方案，并根据目标确定预测频率。

为了定义预测窗口，请在文件顶部的 `Config` 结构体中添加以下常量：

```
static let windowOffset = 5
static let numWindows = windowSize / windowOffset
```

在这里你将 `windowOffset` 定义为五。这不是窗口重叠的方式，而是窗口起始相对于上一个窗口起始的偏移量。根据你之前定义的 20 `windowSize`，这使得 `numWindows` 等于四。这就是在你基本上回到第一个窗口之前将拥有的预测窗口数量。

如果你参考下面的图，应该会更清晰，它显示了你的预测在前 40 个样本中是如何重叠的：

![](img/5720be5c3cca252e12448e68d25607b5_429_0.png)

