

## 机器学习

在真正使用模型之前，还有最后一件事。在书前面的部分，你读过 Core ML 预测结果带有概率，这些概率本质上是模型对预测的置信度。你已经看到模型总是产生某些预测，但并不一定具有很高的置信度。

为了避免对低概率预测做出反应，你需要定义一个阈值，只有概率超过该阈值才被认为足够执行。在文件顶部的 `Config` 中添加以下常量：

```swift
static let predictionThreshold = 0.9
```

这意味着在应用响应之前，模型的预测概率需要超过 90%。这个阈值是在经过一些测试后选择的，但在超过某个阈值后，主要取决于个人偏好。值太低会导致应用在不存在手势的地方幻幻手势，所以务必避免这一点，除此之外这取决于你希望应用有多灵敏。稍后，在你写完应用后，尝试不同的值来观察它们如何影响游戏体验。

完成这些小的添加后，现在是时候编写使用你训练的模型来识别手势的方法了。在 `GameViewController` 的末尾添加以下代码：

```swift
func predictGesture(window: Int) {
  // 1
  let previousOutput = modelOutputs[window]
  let modelOutput = try? gestureClassifier.prediction(
    features: modelInput,
    hidden: previousOutput?.hiddenOut,
    cell: previousOutput?.cellOut)
  // 2
  modelOutputs[window] = modelOutput
  if let prediction = modelOutput?.activity,
     let probability = modelOutput?.activityProbability[prediction] {
    // 4
    if prediction == Config.restItValue {
      return
    }
    // 5
    if probability > Config.predictionThreshold {
      // 6
      if prediction == expectedGesture {
        updateScore()
      } else {
        gameOver(incorrectPrediction: prediction)
      }
    }
    // 7
    expectedGesture = nil
  }
}
```

你已经写了相当多的代码，但这个方法是应用中唯一真正使用机器学习的部分。它的作用如下：

- 1. 首先，它调用 `gestureClassifier.prediction` 来尝试对运动数据进行分类，并将结果存储为 `modelOutput`。注意，你提供了 `modelInput`（你在其中填充了 `motionData`）以及该窗口上一次预测的 LSTM 和内部单元格状态。这些值在每次第一次预测时将为 `nil`，这会告诉分类器没有历史数据，它应该相应地进行初始化。
- 2. 然后，它将模型的响应存储在 `modelOutputs` 中，以便你下次对该窗口进行预测时可以访问它。
- 3. 接下来，它从模型输出中获取预测的活动以及分配给该预测的概率。
- 4. 它检查非手势的预测（即休息）并直接忽略它们。
- 5. 对于非休息预测，它检查概率是否超过了你之前定义的阈值。如果是，它就认为这是一个真实的预测；否则它什么都不做，应用将继续处理运动事件。
- 6. 下一段代码是游戏逻辑，但你编写使用分类模型编写的任何代码都会有类似的内容——一个你真正使用预测值的地方。如果模型告诉玩家正确的手势（即预测的手势与 `expectedGesture` 匹配），它将调用 `updateScore` 加分；否则，应用认为玩家操作失误并调用 `gameOver`。

- 7. 无论预测如何，该方法会将 `expectedGesture` 重置为 `nil`，以便应用停止处理一段时间运动数据。启动项目现有的游戏逻辑将在合适的时候将其设置为新手势。

注意：Xcode 生成了三个不同的预测方法，以及可以在一次调用中批量处理多个预测的 `predictions`（带有 "s"）。此代码使用了直接接收 `MLMultiArrays` 的版本，但你可能会在应用中发现你倾向于使用其他版本的情况，因此请务必检查生成的代码以获取选项。

![](img/5720be5c3cca252e12448e68d25607b5_439_0.png)

现在回到你之前添加的注释——`// TODO predict the gesture`，将其替换为对刚刚编写的方法调用：

```swift
predictGesture(window: window)
```

你已经在 `processMotionData` 内部计算了正确的预测窗口，现在这里将其传递给 `predictGesture` 以执行推理。

现在构建应用并在你的 iPhone 上运行。（抱歉，模拟器里没数据！）你可能在第一个手势上成功，但很快应用就会报出一个手势，然后立即抱怨你做错了。怎么回事？

记得那些复杂的重叠窗口吗？嗯，那个底层存储缓冲区可能仍然包含我们之前正在处理的序列数据。当应用请求新手势时，有一个预测窗口所需的数据就那样坐在那里等待被识别——它是在你做出上一个手势时收集的。不要忘记，循环模型使用来自之前预测的状态来帮助它们做出新预测，因为它们假设数据是相关的。但当此应用请求新手势时，它不再希望模型考虑先之前的数据。每个新手势都获得一个干净的状态。

为了这一点，你需要重置缓冲区和模型的之前的输出状态。在 `GameViewController` 中添加该方法：

```swift
func resetPredictionWindows() {
  // 1
  bufferIndex = 0
  // 2
  isDataAvailable = false
  // 3
  for i in 0..<modelOutputs.count {
    modelOutputs[i] = nil
  }
}
```

这部分代码不多，但对于功能至关重要。它的作用是：

- 1. 将 `bufferIndex` 重置为 0。
- 2. 将 `isDataAvailable` 设置为 `false`，以便再次开始填充缓冲区。
- 3. 将 `modelOutputs` 中的所有内容置为 `nil`，以清除从之前的预测构建的状态。

![](img/5720be5c3cca252e12448e68d25607b5)

现在定义了这个方法，在 `GameViewController` 的顶部调用它：

```swift
resetPredictionWindows()
```

现有的游戏逻辑会在通知玩家执行新手势时自动调用它。有了这个添加，可以确保预测是基于处理早先手势时产生的数据。

就是这样！再次构建并运行！如果游戏出现得太快，请增加 `Config.gestureTimeout` 的值。或者如果你增加挑战，看看能将其降低到多低。你能正确识别多少？

关键点

- 使用重叠预测窗口以提供更快、更准确的响应。
- 调用模型的预测方法对数据进行分类。
- 通过 `MLArray` 对象向模型传递多特征输入。
- 按训练时使用的顺序排列输入特征值。如果你以任何顺序排列，模型将产生无效结果。
- 在多次调用预测处理序列时，将上一个时间步的隐藏和单元格输出传递给下一个时间步。
- 忽略概率低于某个合理阈值的预测。但请记住，模型偶尔会以非常高的概率做出错误预测，所以这种技巧不能完全消除错误预测。

挑战

扩展是练习活动识别的好方法。在 `GestureDataRecorder` 项目中添加新的手势类型是一个直接的过程，所以从那里开始，收集一些数据。接下来，将你的新数据添加到提供的数据集中并训练新模型。用新训练的模型替换 `Gesture` 项目中的模型，并进行必要的修改以将你的新手势添加到游戏中。

之后，你可以识别手势以外的活动。例如，你可以制作一个自动跟踪用户进行不同类型锻炼时间的应用。构建此类活动的数据集将更加困难，因为你对设备位置的控制较少，且每个活动的差异更大。在这种情况下，你需要从许多不同的人那里收集更多样化的数据集，以训练一个泛化良好的模型。

并且记住，这些模型也适用于其他设备。Apple Watch 是一个特别合适的选择——一个包含多个实用传感器的设备，保持在用户身上的已知位置，并且全天或大部分时间佩戴。如果你有权限，请试一下吧！

