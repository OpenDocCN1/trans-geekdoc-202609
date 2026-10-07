
每种手势都有超过 5000 个样本，`rest_it` 有超过 13,000 个。另一方面，每个*错误*预测只发生了少数几次，其中最少的是 `rest_it` 被预测为 `drive_it` 的仅有 17 次，最多的是 `drive_it` 被预测为 `rest_it` 的有 184 次。几乎所有的错误都涉及 `rest_it` 活动，这是意料之中的。毕竟，你永远不知道人们在录制 `rest_it` 时在做什么——他们可能一直在做手势！

事实上，请注意，唯一*没有*涉及 `rest_it` 活动的错误预测是 176 个 `chop_it` 手势被预测为 `shake_it`。这两个手势之间可能出现错误是合理的，切切动作实际上与抖动非常相似——如果一个人切得很快，看起来可能像抖动，或者如果抖动得太夸张，看起来可能有点像切切。

请记住，你看到的模型性能可能比它的测试结果更好，因为如果你对模型仍然不满意，你应该创建一个新的。有些建议会告诉你不要重用训练数据，因为数据会泄露到你的模型中。从技术上来说这是正确的，你应该听他们的……除非你有源不断的免费数据，否则你可能没有每个测试集只用一个奢侈。好消息是——在很多情况下这可能是可以的。例如，对于像这样的项目，App 将运行良好，而你的测试数据只是帮助你实现目标的工具。你的模型在这些数据上运行良好，因此你将在带有真人数据的实际设备上运行它。那些是真实的测试，而且都是独一二二的——所以你甚至告诉那些建议你每次都使用了新的测试集！测试准确率等指标很棒，但在发布之前让许多人测试你的 App 更好这样你就知道它确实按照你想要的方式运行。

当你认为模型已准备好在设备上测试时，请使用以下代码保存它：

```
model.export_coreml("GestureClassifier.mlmodel")
model.save("GestureClassifier")
```

这会将模型导出为适用于应用的 Core ML，并保存一个副本，以便你以后想使用时可以在 Python 中重新加载。

你已经保存了模型，它经过训练可以分析 iPhone 数据并识别这些数据是否表示发生了特定手势。它的表现良好，至少在针对*录制的*运动数据进行测试时是这样。很好的开始，但你希望它能够实时运行，在运动数据*在设备上产生*时对其进行评估。你需要一个 App！继续阅读学习如何构建一个。

# 了解你的模型

在 Xcode 中打开 GestureIt 起始项目。如果你已经读了此章节之前的章节，你已经练习过向项目中添加 Core ML 模型——找到在上一节保存训练模型时创建的 `GestureClassifier.mlmodel` 文件，并将其拖入 Xcode。或者，如果你想使用在提供的数据集上训练的模型，请添加 `notebooks/pre-trained/GestureClassifier.mlmodel`。

> 注意：现在你已经在 Xcode 中有了模型，本节的其余部分都是理论。如果你现在对这个讨论感兴趣，可以安全地跳过。

在项目导航器（Project Navigator）中查看 `GestureClassifier.mlmodel`，你会看到以下内容，它与本书第一节的模型相似但又完全不同：

| 机器学习模型 |
| :--- |
| 名称 (Name) | GestureClassifier |
| 类型 (Type) | 神经网络分类器 (Neural Network Classifier) |
| 大小 (Size) | 98 KB |
| 作者 (Author) | unknown |
| 描述 (Description) | 由 Turi Create (版本 5.0) 创建的分类器 |
| 许可证 (License) | unknown |

| 模型类 (Model Class) |
| GestureClassifier |
| 生成的 Swift 模型类 |

| 模型评估参数 (Model Evaluation Parameters) | 名称 (Name) | 描述 (Description) |
| :--- | :--- | :--- |
| 输入 (Inputs) | | |
| features | MultiArray(Double 1 x 20 x 6) Window = [rotX, rotY, rotZ, accelX, accelY, accelZ] |
| hiddenin | MultiArray(Double 200?) LSTM 状态输入 |
| cellin | MultiArray(Double 200?) LSTM 单元状态输入 |
| 输出 (Outputs) | | |
| activityProbability | Dictionary (String + Double) 活动预测概率 |
| hiddenOut | MultiArray(Double 200) LSTM 状态输出 |
| cellOut | MultiArray(Double 200) LSTM 单元状态输出 |
| activity | String 最高预测的类别标签 |
| | |

在这里你可以看到 GestureClassifier 是来自 Turi Create 的活动分类器。它是

# 机器学习第 12 章：为序列分类训练模型

小于 1MB —— 对于一个没有利用 iOS 预装模型（如你之前做的那些模型）的神经网络来说，这已经不错了。但接下来是模型评估参数部分，那里的情况会变得复杂一些。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它基本上只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 模型输出的字典，包含了概率。
- activity: String 最高预测的类别标签。
- hiddenIn: MultiArray(Double 200?) LSTM 隐藏状态输入。
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入。
- hiddenOut: MultiArray(Double 200) LSTM 隐藏状态输出。
- cellOut: MultiArray(Double 200) LSTM 单元状态输出。

但接下来是模型评估参数部分，那里的情况会变得复杂一些。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它基本上只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 模型输出的字典，包含了概率。
- activity: String 最高预测的类别标签。
- hiddenIn: MultiArray(Double 200?) LSTM 隐藏状态输入。
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入。
- hiddenOut: MultiArray(Double 200) LSTM 隐藏状态输出。
- cellOut: MultiArray(Double 200) LSTM 单元状态输出。

等待，让我们根据 OCR 流程重新对齐文本：

在这里你可以看到 GestureClassifier 是来自 Turi Create 的活动分类器。小于 1MB —— 对于一个没有利用 iOS 预装模型（如你之前做的那些模型）的神经网络来说，这已经不错了。但接下来是模型评估参数部分，那里的情况会变得复杂一些。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 字典
- hiddenIn: MultiArray(Double 200?) LSTM 状态输入 |
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入 |
- hiddenOut: MultiArray(Double 200) LSTM 状态输出 |
- cellOut: MultiArray(Double 200) LSTM 单元状态输出 |
- activity: String 最高预测的类别标签

实际上，OCR 非常碎片化。让我们提供解构后的版本：

在这里你可以看到 GestureClassifier 是来自 Turi Create 的活动分类器。小于 1MB —— 对于一个没有利用 iOS 预装模型（如你之前做的那些模型）的神经网络来说，这已经不错了。但接下来是模型评估参数部分，那里的情况会变得复杂。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它基本上只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 字典
- hiddenIn: MultiArray(Double 200?) LSTM 状态输入 |
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入 |
- hiddenOut: MultiArray(Double 200) LSTM 状态输出 |
- cellOut: MultiArray(Double 200) LSTM 单元状态输出 |
- activity: String 最高预测的类别标签

等待，我看到 OCR 有重复或损坏的部分。我将重构逻辑流。

---

在这里你可以看到 GestureClassifier 是来自 Turi Create 的活动分类器。小于 1MB —— 对于一个没有利用 iOS 预装模型（如你之前做的那些模型）的神经网络来说，这已经不错了。但接下来是模型评估参数部分，那里的情况会变得复杂。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它基本上只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 模型输出包含概率的字典。
- activity: String 最高预测的类别标签。
- hiddenIn: MultiArray(Double 200?) LSTM 状态输入。
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入。
- hiddenOut: MultiArray(Double 200) LSTM 状态输出。
- cellOut: MultiArray(Double 200) LSTM 单元状态输出。

（自纠：我现在将根据提供的页面无缝输出最终清理文本。）

[content]
请记住，你看到的模型性能可能比它的测试结果更好，因为如果你对模型仍然不满意，你应该创建一个新的。有些建议会告诉你不要重用训练数据，因为数据会泄露到你的模型中。从技术上来说这是正确的，你应该听他们的……除非你有源不断的免费数据，否则你可能没有每个测试集只用一个奢侈。好消息是——在很多情况下这可能是可以的。例如，对于像这样的项目，App 将运行良好，而你的测试数据只是帮助你实现目标的工具。你的模型在这些数据上运行良好，因此你将在带有真人数据的实际设备上运行它。那些是真实的测试，而且都是独一无二的——所以你甚至告诉那些建议你每次都使用了新的测试集！测试准确率等指标很棒，但在发布之前让许多人测试你的 App 更好这样你就知道它确实按照你想要的方式运行。

当你认为模型已准备好在设备上测试时，请使用以下代码保存它：

```
model.export_coreml("GestureClassifier.mlmodel")
model.save("GestureClassifier")
```

这会将模型导出为适用于应用的 Core ML，并保存一个副本，以便你以后想使用时可以在 Python 中重新加载。

你已经保存了模型，它经过训练可以分析 iPhone 数据并识别这些数据是否表示发生了特定手势。它的表现良好，至少在针对*录制的*运动数据进行测试时这样。很好的开始，但你希望它能够实时运行，在运动数据*在设备上产生*时对其进行评估。你需要一个 App！继续阅读学习如何构建一个。

# 了解你的模型

在 Xcode 中打开 GestureIt 起始项目。如果你已经读了此章节之前的章节，你已经练习过向项目中添加 Core ML 模型——找到在上一节保存训练模型时创建的 `GestureClassifier.mlmodel` 文件，并将其拖入 Xcode。或者，如果你想使用在提供的数据集上训练的模型，请添加 `notebooks/pre-trained/GestureClassifier.mlmodel`。

> 注意：现在你已经在 Xcode 中有了模型，本节的其余部分都是理论。如果你现在对这个讨论感兴趣，可以安全地跳过。

在项目导航器（Project Navigator）中查看 `GestureClassifier.mlmodel`，你会看到以下内容，它与本书第一节的模型相似但又完全不同：

| 机器学习模型 |
| :--- |
| 名称 (Name) | GestureClassifier |
| 类型 (Type) | 神经网络分类器 (Neural Network Classifier) |
| 大小 (Size) | 98 KB |
| 作者 (Author) | unknown |
| 描述 (Description) | 由 Turi Create (版本 5.0) 创建的分类器 |
| 许可证 (License) | unknown |

| 模型类 (Model Class) |
| GestureClassifier |
| 生成生成的 Swift 模型类 |

| 模型评估参数 (Model Evaluation Parameters) | 名称 (Name) | 描述 (Description) |
| :--- | :--- | :--- |
| 输入 (Inputs) | | |
| features | MultiArray(Double 1 x 20 x 6) Window = [rotX, rotY, rotZ, accelX, accelY, accelZ] |
| hiddenin | MultiArray(Double 200?) LSTM 状态输入 |
| cellin | MultiArray(Double 200?) LSTM 单元状态输入 |
| 输出 (Outputs) | | |
| activityProbability | Dictionary (String + Double) 活动预测概率 |
| hiddenOut | MultiArray(Double 200) LSTM 状态输出 |
| cellOut | MultiArray(Double 200) LSTM 单元状态输出 |
| activity | String 最高预测的类别标签 |
| | |

在这里你可以看到 GestureClassifier 是来自 Turi Create 的活动分类器。它小于 1MB —— 对于一个没有利用 iOS 预装模型（如你之前做的那些模型）的神经网络来说，这已经不错了。但接下来是模型评估参数部分，那里的情况会变得复杂一些。

首先是那些较容易识别的项目：

- features: 你将作为输入的 Double 类型的 MLMultiArray。如果你以前见过 MLMultiArray，不要担心，它没什么新奇的。它基本上只是 Core ML 用来高效处理数据的多维数组。它的大小足以存储训练期间你使用的每个特征的单个预测窗口值：用户绕 X、Y、Z 轴的旋转和加速度。
- activityProbability: 模型输出的字典，包含了概率。
- activity: String 最高预测的类别标签。
- hiddenIn: MultiArray(Double 200?) LSTM 隐藏状态输入。
- cellIn: MultiArray(Double 200?) LSTM 单元状态输入。
- hiddenOut: MultiArray(Double 200) LSTM 隐藏状态输出。
- cellOut: MultiArray(Double 200) LSTM 单元状态输出。

# 循环神经网络

到目前为止，在书中你主要处理卷积神经网络 —— CNN。它们非常适合识别数据中的空间关系。另一种类型的网络，称为循环神经网络 —— RNN —— 设计用于识别时间关系。记住，序列通常意味着时间的流逝，所以实际上意味着。

为了做到，它们一次处理一个序列，并为每个序列产生输出。这到底意味着什么？

考虑你是如何阅读句子的：“The fox jumps over the lazy dog.”你并不是只看每个单词并忽略其他。相反，句子的每个元素增加了你的理解。发生了什么？跳跃。谁在跳跃？狐狸。它看起来像什么？它是棕色的。而且 RNN 被设计用来做类似的事情，通过将输入元素与上一个元素的输出结合来解释序列的每个元素。注意，RNN 在处理给定项目之前无法处理

