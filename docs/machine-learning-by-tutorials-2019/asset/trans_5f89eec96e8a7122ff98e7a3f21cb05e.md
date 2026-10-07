

# 机器学习

## 第 2 章：入门图像分类

- 3. 因为 Core ML 可能需要一些时间来完成分类所需涉及的所有计算（回想 ResNet 处理单张图像需要进行 3.9 亿次计算），因此最好在后台队列上执行请求，以免阻塞主线程。
- 4. 为此图像及其取向信息创建一个新的 `VNImageRequestHandler`，然后调用 `perform` 来实际执行请求。注意，可以执行一个 `VNRequest` 对象数组，这样如果你想，就可以在同一图像上执行多个 Vision 请求。在这里，只需使用你之前创建的 `classificationRequest` 属性中的 `CoreMLRequest` 对象即可。

上述步骤基本上 `classificationRequest` 懒加载属性，它是用于 Vision Core ML 应用的。

因为当你第一次通过 `classify(image:)` 获取时，它会加载 Core ML 模型并设置 Vision 请求。它只会执行一次，并对每张图像重用同一个请求对象。另一方面，你每次都需要创建一个新的 `VNImageRequestHandler`，因为这个处理器特定于你正尝试分类的图像。

## 图像方向

当你用 iPhone 相机拍摄照片时，无论你如何握手机，图像数据都存储为横向，因为那是相机传感器的原生取向。

iOS 通过 `imageOrientation` 属性跟踪图像的真实方向。对于照片相册中的图像，方向信息存储在图像文件的 EXIF 数据中。

如果你以竖直模式握持手机并拍照，它的 `imageOrientation` 将为 `.right`，表示相机顺时针旋转了 90 度。0 度意味着手机是横向的，且按钮在右侧。

方向 `.up` 意味着图像的正确侧已经是上方。这对于横向拍摄的照片是如此，也适用于来自其他来源的竖直照片，例如你在 Photoshop 中创建的图像。

大多数图像分类模型都期望看到朝向正确的输入图像。请注意，Core ML 模型并不接受“图像方向”作为输入，因此它只会看到图像缓冲区中的“原始”像素，而不知道哪一侧是上方。

![](img/5720be5c3cca252e12448e68d25607b5_65_0.png)

# 机器学习第 2 章：入门图像分类

图像分类器通常经过训练，以考虑到图像可能被水平翻转，以便它们能够识别面向左侧和面向右侧的对象；它们通常没有经过训练来处理旋转了 90、180 或 270 度的图像。

如果你传入一个方向不正确的图像，模型可能不会给出准确的预测，因为它没有学会以那种方式查看图像。

![](img/5720be5c3cca252e12448e68d25607b5_66_0.png)

这只猫不是正的

这就是为什么你需要告诉 Vision 图像的方向，以便它在像素到达 Core ML 之前正确地旋转图像像素。由于 Vision 使用的是 `CIImage` 而不是 `UImage`，你需要将 `UImage.Orientation` 值转换为 `CGPropertyOrientation` 值。

## 尝试一下

此时，你可以编译并运行该应用，然后选择一张照片。

在模拟器中运行此应用是可能的，但只有照片库按钮是激活的。模拟器上的照片库默认不包含零食的照片，但你可以通过 Google 搜索它们并将这些 JPEG 或 PNG 文件拖入“照片”应用来添加自己的图片。

在设备上运行应用以使用相机，因为模拟器不支持拍照。

拍摄或选择一张照片，Xcode 调试面板将输出类似的内容：

```
Request is finished! Optional[<VNClassificationObservation:0x6c0002b2940-8B9F37D-B9CF-405A-AE33-64AF4F6763BB 0.8175 "healthy" (0.917060),<VNClassificationObservation:0x6c0002b350-B919C6-B264-AB33-5AAE84F6384A 0.18295 "unhealthy" (0.082490)]]
```

这是 `VNCoreMLRequest` 完成处理程序中 `print` 语句的输出。它打印了请求结果数组。如你所示，此数组包含两个 `VNClassificationObservation` 对象，一个健康（healthy）类的概率（0.917060 或 91.7%），另一个是不健康（unhealthy）类的概率（0.082490 或 8.29%）。

## 显示结果

当然，向输出面板打印内容并不有趣，所以让我们在应用中正确地显示这些结果吧。

在 `lazy classificationRequest` 的声明内部，将 `VNCoreMLRequest` 对象的完成处理程序更改为如下：

```
let request = VNCoreMLRequest(model: visionModel,
    completionHandler: {
        [weak self] request, error in
        self?.processObservations(for: request, error: error) // 添加此行
    }
)
```

现在你调用的不是之前存在的 `print` 语句，而是一个新方法 `processObservations(for:error)`。直接将处理结果的代码推送到完成处理程序内部是完全可能的，但这往往会使代码更难读。

在 `ViewController.swift` 中添加新方法：

```
func processObservations(for request: VNRequest, error: Error?) {
    // 1
    DispatchQueue.main.async {
        // 2
        if let results = request.results as? [VNClassificationObservation] {
            // 3
            if results.isEmpty {
                self.resultsLabel.text = "nothing found"
            } else {
                self.resultsLabel.text = String(format:"%@ %.1f%%", results[0].identifier, results[0].confidence * 100)
            }
            // 4
        } else if let error = error {
            self.resultsLabel.text = "error: \(error.localizedDescription)"
        } else {
            self.resultsLabel.text = "???"
        }
        // 5
        self.showResults()
    }
}
```

![](img/5720be5c3cca252e12448e68d25607b5_67_0.png)

# 机器学习

## 第 2 章：图像分类

```
}
```

以下是该方法逐步执行的操作：

- 1. 完成处理程序在主队列上执行，Vision 请求在后台队列上运行。
- 2. 如果请求结果成功转换为 `[VNClassificationObservation]` 数组：
- 3. 如果结果为空，将结果标签显示为“nothing found”；否则，显示第一个结果的标识符和置信度百分比。
- 4. 如果存在错误，则显示错误信息。
- 5. 如果以上都不是，则显示“???”。
- 6. 最后，调用 `showResults()`。

# 机器学习

## 应用并分类一些图像

![](img/5720be5c3cca252e12448e68d25607b5_69_0.png)
![](img/5720be5c3cca252e12448e68d25607b5_69_1.png)
![](img/5720be5c3cca252e12448e68d25607b5_69_2.png)
![](img/5720be5c3cca252e12448e68d25607b5_69_3.png)

## 对几张图像的预测

非常酷。通过几行代码，你就为应用添加了一个顶尖的图像分类器！

> 注意：你在 Xcode 中查看 Core ML 模型时（通过在项目导航器中选择 .mlmodel 文件），它显示该模型有两个输出：一个包含概率的字典和一个顶部预测的标签。然而，Vision 请求给你一个 `VNObservation` 对象数组。Vision 将来自 Core ML 的字典转换为它自己的“观测”对象。之后，你将看到直接使用 Core ML 而不使用 Vision，在这种情况下，你可以访问模型的输出。

## 如果图像没有零食怎么办？

应用显示胜利类别及其对该预测的置信度。在上面的左图中，该类别是“healthy”，置信度为 94.8%。

如果输出类似于“healthy 95%”，模型对自己很有信心。你将在橙子、苹果、香蕉等的预测中看到这种情况。随后，如果输出是“unhealthy 95%”，模型对零食是不健康的非常确定，你将在椒盐和华夫饼上看到。这就是我们希望看到的置信预测。

应用中使用的模型是针对 20 种不同零食进行训练的。但当你向它展示一种从未见过的零食，甚至是一个完全不同的物体时，会发生什么呢——可能是一个根本不是不可食的东西？

