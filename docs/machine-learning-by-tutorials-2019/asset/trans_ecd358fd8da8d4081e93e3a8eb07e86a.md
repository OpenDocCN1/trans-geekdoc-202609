

# 机器学习第2章：图像分类入门

字典包含了类别的名称以及每个类的置信度得分，因此它与概率分布相同，但它是字典的形式而不是数组。与 Vision 的 `VNClassificationObservation` 对象数组的区别在于，该字典是没有排序的。

> 注意：Xcode 为这些属性生成的代码取决于 .mlmodel 文件中输入和输出的名称。对于这个特定模型，输入被称为 "image"，因此该方法变为 `prediction(image:)`。如果 .mlmodel 文件中的输入称为其他名称（例如 "data"），那么该方法将是 `prediction(data:)`。`HealthySnacks` 输出类中的输入名称也是如此。在导入 Core ML 模型时需要注意这一点：不同的模型会有不同的输入输出名称——这是使用 Vision 时不需要担心的另一个问题。

为了在不使用 Vision 的情况下使用 `HealthySnacks` 类，你必须调用 `prediction(image:)` 并获取包含待分类图像的 `CVixelBuffer`。当预测方法完成后，它会将分类结果作为 `HealthySnacks` 输出对象返回。

接下来，你将切换到 `ViewViewController.swift` 并为 `ViewViewController` 添加以下属性以创建模型的实例：

```swift
let healthySnacks = HealthySnacks()
```

现在，你需要一种方法将 `UIImagePicker` 中的 `UIImage` 转换为 `CVixelBuffer`。此对象是图像数据的低级描述，供 Core Vision 和 AVAudio 使用。你可能习惯于将 `UIImage` 或 `CGImage` 对象处理图像，因此你需要先将这些转换为 `CVixelBuffers`。

向类中添加以下函数：

```swift
func pixelBuffer(for image: UIImage) -> CVixelBuffer? {
    let model = healthySnacks.model

    let imageConstraint = model.modelDescription
        .inputDescriptionsByName["image"]
        .imageConstraint!

    let imageOptions:[MLFeatureValue.ImageOption: Any] = {
        .cropAndScale: VNImageCropAndScaleOption.scaleFill.rawValue
    }

return try? MLFeatureValue(
    cgImage: image.cgImage!,
    constraint: image.cgConstraint,
    options: imageOptions).imageBufferValue
)
```

约束（constraint） 是一个 `MLConstraint`，描述了模型预期的图像大小。`options` 字典允许指定如何对图像进行缩放和裁剪。这使用了与 Vision 相同的选项，但你也可以给它一个带有自定义裁剪区域的 `CGRect`。该 `MLFeatureValue` 构造器还有一个版本，可以在图像不是正立的情况下为其传递一个方向值。

> 注意：此 API 适用于 iOS 13 及更高版本。在本章的下载资源中，我们提供了一个 `UIImage` 扩展，用于为旧版本的 iOS 将 `UIImage` 转换为 `PixelBuffer`。

将 `classify(image:)` 方法更改为：

```swift
func classify(image: UIImage) {
    DispatchQueue.global(qos: .userInitiated).async {
        // 1
        if let pixelBuffer = self.pixelBuffer(for: image) {
            // 2
            if let prediction = try? self.healthySnacks.prediction(image: pixelBuffer) {
                // 3
                let results = self.top(1, prediction.labelProbability)
                self.processObservations(results: results)
            } else {
                self.processObservations(results: [])
            }
        }
    }
}
```

以下是它的工作原理：

- 1. 使用辅助方法将 `UIImage` 转换为 `VPixelBuffer`。这会将图像缩放到预期的大小（227×227），如果它还没有正立，还会修复方向。
- 2. 调用 `prediction(image:)` 方法。这可能会失败——例如，如果图像缓冲区不是227×227 像素——这就是为什么你需要使用 `try?` 并将其放在 `if let` 中。
- 3. 预测对象是 `HealthySnacksOutput` 的实例。你可以查看它的 `label` 属性来寻找最佳类的名称，但你也想查看得分最高的类名称及其概率。这正是字典的作用。

（注：后续重复的文本已根据指令“不要重复输出原文”的要求进行过滤，仅保留核心逻辑翻译）

# 第3章：训练图像分类器
作者：Audrey Tam & Matthijs Hollemans

**更新说明：** 本章已更新至 iOS 13、Xcode 11 和 Swift 5.1

在上一章节中，你学习了如何使用 Core ML 和 Vision 使用训练好的模型对图像进行分类。然而，使用他人的模型往往是不够的——模型可能无法完全按照你的要求工作，你可能想使用自己的数据和类别——而且了解如何训练自己的模型是很有用的。

在接下来的章节中，你将学习创建自己的模型。你将学习如何使用机器学习专家使用的常用工具和库来创建模型。Apple 为开发者提供了 Create ML 机器学习框架，用于在 Xcode 中创建模型。在本章中，你将学习如何使用 Core ML 训练零食模型。

## 数据集

在训练模型之前，你需要数据。你可能还记得引言中提到的，机器学习的核心是训练模型通过观察大量示例来学习规则。

由于你正在构建一个图像分类器，示例自然将是图像。你将训练一个能够区分 20 种不同类型零食的图像分类器。

