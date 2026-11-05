
## 错误范围

1. 将错误范围压入栈中。
2. 执行一个或多个可能产生错误的运算。
3. 弹出错误范围以检查给定的错误是否发生。

对于第一步，应用程序需要调用 `GPUDevice` 的 `pushErrorScope()` 方法。此方法接受一个字符串，用于标识应监控的错误类型。 [表 7.1](#chapter7.xhtml#tbl7_1) 列出了三种错误类型。

[表 7.1](#chapter7.xhtml#b7tbl7_1) 检测到的错误类型

| 错误 ID || 描述 |
| --- | --- |
| out-of-memory || 执行操作时可用内存不足 |
| --- | --- |
| validation || 方法输入无效（数据类型错误或值不可接受） |
| internal || 与系统或 WebGPU 实现相关的错误 |

在将错误范围压入栈后，应用程序可以通过调用 `popErrorScope()` 方法来检查错误是否发生。此方法返回一个 Promise，该 Promise 解析为描述范围内捕获的第一个错误的对象的。常见的做法是使用名为 `error` 的变量访问错误对象，如以下代码所示：

```
 // Respond to error if error occurred
 device.popErrorScope().then((error) => {
     …
 });
```

如果发生错误，该变量的类型将为 `GPUError`，它提供一个 `message` 属性来标识错误的性质。在以下代码中，如果发生错误，应用程序会打印错误的消息。

```
 device.popErrorScope().then((error) => {
     
     // Check if error occurred
     if(error) {
         
         // Print error message
         console.log(error.message);
     }
 });
```

当应用程序尝试创建客户端系统可能不支持的渲染管线时，错误范围很有帮助。以下代码检查创建渲染管线是否会产生内部错误。如果是，则应用程序会调用 `createSimplerPipeline()` 方法。

```
 // Monitor internal errors
 device.pushErrorScope("internal");
 
 // Attempt to create rendering pipeline
 const renderPipeline = device.createRenderPipeline(…);
 
 // Check to see if internal error occurred
 device.popErrorScope().then((error) => {
     if(error) {
         console.log("Couldn't create pipeline");
         createSimplerPipeline(…);
     }
 });
```

`GPUDevice` 是 `EventTarget` 的子类，因此可以调用其 `addEventListener()` 方法来跟踪事件。特别是，可以通过将第一个参数设置为 uncapturederror 来处理未捕获的错误。以下代码展示了这一点：

```
 // Handle errors that haven't been captured in error scopes
 device.addEventListener("uncapturederror", (event) => {

     // Display the error's message in the console
     console.error("Uncaptured error: ", event.error.message);
 });
```

近几个月来，WebGPU 规范经常发生变化。出于此及其他原因，采用错误检查以确保应用程序正常运行是个好主意。

## 视口和剪裁矩形

到目前为止所介绍的每个示例应用程序中，渲染始终占据整个画布。应用程序在创建渲染通道编码器时提供颜色附件，从而标识画布区域。以下代码从与画布关联的 WebGPU 上下文创建视图：

```
 // Render to the WebGPU context of the canvas
 const renderPass = encoder.beginRenderPass({
     colorAttachments: [{
         view: context.getCurrentTexture().createView(),
         …
     }]
 });
```

如果你不希望渲染占据整个画布，可以通过调用 `GPURenderPassEncoder` 的 `setViewport()` 方法来设置渲染区域（称为 *视口*）。该方法接受六个值，[表 7.2](#chapter7.xhtml#tbl7_2) 列出了全部。

[表 7.2](#chapter7.xhtml#b7tbl7_2) setViewport 方法的参数

| 参数 || 类型 || 描述 |
| --- | --- | --- |
| x || Integer || 画布左上角的 x 坐标 |
| --- | --- | --- |
| y || Integer || 画布左上角的 y 坐标 |
| width || Integer || 渲染表面的宽度 |
| height || Integer || 渲染表面的高度 |
| minDepth || Integer || 最小深度值（默认为 0） |
| maxDepth || Integer || 最大深度值（默认为 1） |

一个示例会使这一点更清晰。假设你希望应用程序的渲染仅限于画布左上角的 100×100 正方形。在这种情况下，你将使用 `setViewport()` 方法，将左上角设置为 (0, 0)，尺寸设置为 100 和 100。以下代码展示了其工作原理：

```
 // Set the boundaries of the rendering
 renderPass.setViewport(0, 0, 100, 100, 0, 1);
```

除了自定义视口外，应用程序还可以定义称为 *剪裁矩形* 的区域，告诉渲染器应丢弃哪些片段。这是通过调用 `GPURenderPassEncoder` 的 `setScissorRect()` 方法实现的。该方法接受矩形左上角的坐标，然后是其宽度和高度。

例如，假设应用程序希望丢弃 150×250 矩形外部的所有片段，该矩形的左上角位于 (20, 30)。以下代码为此目的定义了一个剪裁矩形：

```
 // Set the boundaries of the scissor rectangle
 renderPass.setScissorRect(20, 30, 150, 250);
```

由于这段代码，剪裁矩形外部的任何片段都不会被绘制。默认情况下，剪裁矩形具有与视口相同的边界。

## 遮挡查询

[第 6 章](#chapter6.xhtml) 解释了应用程序如何使用深度和模板测试丢弃片段。应用程序可以通过提交 *遮挡查询* 来检查有多少片段通过了这些测试。如果只有少量片段通过，应用程序可能希望绘制更简单的对象或使用更简单的着色器。

应用程序可以通过采用六个步骤来创建和配置遮挡查询：

1. 创建查询集，并在创建渲染通道编码器时标识它。
2. 创建一个缓冲区来保存查询结果。
3. 调用渲染通道编码器的 `beginOcclusionQuery()` 方法。
4. 在渲染命令完成后，调用 `endOcclusionQuery()`。
5. 通过调用 `resolveQuerySet()` 编码记录查询的命令。
6. 通过调用其 `destroy()` 方法销毁查询集。

以下讨论探讨了这些步骤。在每种情况下，它解释了需要哪些对象和方法，然后展示了如何在代码中实现它们。

### 创建查询集

`GPUQuerySet` 对象可以保存多个查询，应用程序可以通过调用 `GPUDevice` 的 `createQuerySet()` 方法来创建一组查询。此方法接受一个描述符，其中包含 [表 7.3](#chapter7.xhtml#tbl7_3) 中列出的属性。

[表 7.3](#chapter7.xhtml#b7tbl7_3) 查询集描述符属性

| 属性 || 可选？ || 描述 |
| --- | --- | --- |
| label || Y || 查询集的字符串标识符 |
| --- | --- | --- |
| count || N || 可以访问的查询数量 |
| type || N || 如果集合包含遮挡查询（occlusion）或时间戳（queries） |

对于遮挡查询，`count` 必须设置为大于 1 的整数，并且 `type` 必须设置为 occlusion。对于时间戳查询，`type` 必须设置为 timestamp。 [第 8 章](#chapter8.xhtml) 将讨论时间戳查询并展示其用法。

为了演示这一点，以下代码创建了一个能够保存四个遮挡查询的查询集：

```
 // Create a new query set
 const querySet = device.createQuerySet({
     label: "Query Set 0",
     count: 4,
     type: "occlusion"
 });
```

创建查询集后，应用程序需要将其与渲染通道编码器关联起来。这是通过设置在 `beginRenderPass()` 方法中使用的对象的 `occlusionQuerySet` 属性实现的。在以下代码中，渲染通道被配置为使用之前创建的查询集：
