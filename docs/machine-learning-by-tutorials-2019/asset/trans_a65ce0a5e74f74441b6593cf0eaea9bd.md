

# 机器学习第 2 章：图像分类入门

对你来说最重要的是，Vision 能够轻松运行以图像作为输入的 Core ML 模型。你甚至可以将其与其他 Vision 任务结合，以构建一个图像处理流水线。例如，在一个检测人物情绪的应用中，你可以构建一个 Vision 流水线，首先检测图像中的人脸，然后对该人脸运行基于 Core ML 的分类器，以判断人是在微笑还是皱眉。

如果你正在处理图像，强烈建议使用 Vision 来运行 Core ML。请记住，HealthySnacks 模型需要 227x227 图像作为输入，而来自照片库或相机的图像会大得多，且通常不是正方形的。Vision 会自动调整图像的大小并裁剪。

在为 .model 自动生成的 Swift 文件中，你可能注意到输入图像（参见 HealthySnacksInput）具有一个 `CVPixelBuffer`，而 `UIImage` 给你的是一个 `UIImage`。Vision 可以为你完成转换，因此你就不需要担心 `CVPixelBuffer`。

最后，Vision 还会执行其他一些技巧，例如旋转图像使其始终正立，并将图像的颜色与设备的色彩空间匹配。如果没有 Vision 框架，你将编写大量额外的代码！你一定会同意，让 Vision 处理所有这些事情要方便得多。

> 注意：当然，如果你使用的模型不接受图像作为输入，那么你就无法使用 Vision。在这种情况下，你必须直接使用 Core ML API。

Vision 显示你需要创建一个 `VNRequest` 对象，它描述你想要执行的任务，然后使用 `VNImageRequestHandler` 来执行该请求。由于你将使用 Vision 运行 Core ML 模型，该请求是一个名为 `VNCoreMLRequest` 的子类。让我们写一些代码：

## 创建 VNCoreML 请求

为了在应用中添加图像分类，你将在 `ViewController.swift` 中实现 `classify(image:)`。该方法目前是空的。

在这里，你将使用 Vision 运行 Core ML 模型并解释其结果。首先，在文件顶部添加所需的导入：

```swift
import CoreML
import Vision
```

接下来，你需要创建一个 `VNCoreMLRequest` 对象。你通常只创建一次这个请求对象，并对想要分类的每张图像重复使用它。不要在每次想要分类图像时都创建一个新的请求对象——那是浪费资源。

在 `ViewController.swift` 中，在 `ViewController` 类内部 `@IBOutlets` 附近添加以下代码：

```swift
lazy var classificationRequest: VNCoreMLRequest = {
  do {
    // 1
    let healthySnacks = HealthySnacks()
    // 2
    let visionModel = try VNCoreMLModel(for: healthySnacks.model)
    // 3
    let request = VNCoreMLRequest(model: visionModel, completionHandler: {
      [weak self] request, error in
        print("Request is finished!", request.results)
    })
    // 4
    request.imageCropScaleOption = .centerCrop
    return request
  } catch {
    fatalError("Failed to create VNCoreMLModel: \(error)")
  }
}()
```

以下是这段代码的作用：

- 1. 创建 `HealthySnacks` 实例。这是来自 .mlmodel 文件自动生成代码的类。你不会直接使用这个类，所以只有你可以将它的 `MLModel` 对象传递给 Vision。

- 2. 创建 `VNCoreMLModel` 对象。这是一个包装对象，将来自 Core ML 框架的 `MLModel` 实例与 Vision 连接起来。

- 3. 创建 `VNCoreMLRequest` 对象。该对象将执行实际操作：将图像转换为 `CVPixelBuffer`、将其缩放到 227×227、运行核心模型、解释结果等。

由于 Vision 请求是异步运行的，因此你可以提供一个完成处理程序来接收结果。目前，完成处理程序只是向 Xcode 调试输出面板打印一些内容。你稍后会完善它。

- 4. `imageCropScaleOption` 告诉 Vision 它应该如何将照片缩小到模型预期的 227×227 像素。

代码封装在 `do-catch` 块中，是因为如果 .mlmodel 文件由于某种原因无效，加载 `VNCoreMLModel` 可能会失败。在示例项目中这不应该发生，因此你通过让应用崩溃来处理此类错误。应用可能会下载 .mlmodel 文件，如果下载失败，.mlmodel 可能会损坏。在这种情况下，你可能希望以一种更优雅的方式处理它。

> 注意：`classificationRequest` 变量是一个懒加载（lazy）属性。如果你不熟悉懒加载属性，这仅意味着在应用中第一次使用 `classificationRequest` 之前，不会创建 `VNCoreMLRequest`。

## 裁剪和缩放选项

现在已经提到过几次，你使用的基于 SqueezeNet 的模型需要 227×227 像素的输入图像。由于你正在使用 Vision，你并不需要担心这个问题——Vision 会自动将图像缩放到正确的大小。然而，调整图像大小的方法有多种，你可能需要为模型选择正确的方法，否则它的效果可能没有你预期的好。

对于你的模型的正确方法取决于它是如何训练的。对于 Healthy Snacks 应用，你将使用 `.centerCrop`，因为这是训练时使用的缩放策略。只需确保你相机指向的对象位于图片中心附近。可以随意尝试不同的缩放选项，看看会产生什么差异（如果有的话）。

Vision 提供了三个选择：

- centerCrop
- scaleFill
- scaleFit

`.centerCrop` 选项首先调整图像大小，使最短边变为2227像素，然后裁剪掉超出正方形的图像部分。注意，这会移除图像左边缘和右边缘的像素（如果图像是纵向的，则是顶部和底部）。

使用 `.scaleFill` 时，图像将被调整为 227x227 而不移除任何内容，但如果原始图像不是正方形的，它会被压缩。最后，`.scaleFit` 通过用像素填充剩余部分保持宽高比例不变。

## 执行请求

现在你已经有了请求对象，可以实现 `classify(image:)` 方法。向方法中添加以下代码：

```swift
func classify(image: UIImage) {
  // 1
  guard let image = CIImage(image: image) else {
    print("Unable to create CIImage")
    return
  }
  // 2
  let orientation = CGImagePropertyOrientation(image.orientation)
  // 3
  DispatchQueue.global(qos: .userInitiated).async {
    // 4
    let handler = VNImageRequestHandler(ciImage: image, orientation: orientation)
    do {
      try handler.perform([self.classificationRequest])
    } catch {
      print("Failed to perform classification: \(error)")
    }
  }
}
```

从 `UIPPickerController` 获取的图像是 `UIImage` 对象，但 Vision 倾向于处理 `CIImage` 或 `CIImage` 对象。任何一种都可以正常工作，而且它们都很容易从原始 `UIImage` 获取。使用 `CIImage` 的优势是这允许你对图像应用额外的 Core Image 转换。

以下是方法的执行步骤：

- 1. 将 `UIImage` 转换为 `CIImage` 对象。

- 2. `UIImage` 有一个 `orientation` 属性，描述绘制时的方向。例如，如果方向是“向下”，则图像应该旋转180度。你需要告诉 Vision 图像的方向，以便在必要时旋转图像，因为 Core ML 期望图像是正立的。

