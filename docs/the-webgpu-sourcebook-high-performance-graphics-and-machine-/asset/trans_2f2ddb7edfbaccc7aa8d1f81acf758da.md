
据我所知，Khronos Group 从未正式声明 Vulkan 是 OpenGL 的替代品。然而，OpenGL 的最新版本（4.6）已有七年历史，而 Vulkan 的最新版本（1.3.270）是在不到一个月前发布的。

## WebGPU

2017 年，Khronos Group 开始探索下一代基于浏览器的图形的可能性，他们称之为 WebGL Next。苹果的开发者看到了在 Web 应用中访问 GPU 的潜力，并意识到创建专有技术毫无意义。

基于此，苹果提出了一个名为 `WebGPU` 的 API，基于其 Metal 语言。负责开发免费 Firefox 浏览器的 Mozilla 基金会提出了基于 Vulkan 的类似 API。随着时间的推移，WebGPU API 融合了 Vulkan、Metal 和 Direct3D 12 的特性。

Google 在 WebGPU 集成方面处于领先地位，Chrome 的最新版本（适用于 Windows 和 macOS 系统）默认启用 WebGPU。Microsoft 的 Edge 浏览器支持 WebGPU，Firefox 用户可以通过设置 `dom.webgpu.enabled` 标志来启用 WebGPU。

## WebGPU 开发概述

现在你了解了 WebGPU 是什么，我想提供一个关于 WebGPU 开发的简单介绍。一般来说，构成 WebGPU 应用的代码大约 90% 是 JavaScript，10% 是 WebGPU 着色器语言（WGSL）。更具体地说，编写一个非平凡的 WebGPU 应用需要三个步骤：

1. 创建访问 GPU 所需的 JavaScript 对象。
2. 创建包含由 GPU 处理的数据和指令的 JavaScript 对象。
3. 将数据和指令发送给 GPU 执行。

步骤 1 和 2 依赖于 JavaScript，如果你已经熟悉该语言，那么大多数 API 都不会有任何困难——你只需创建对象并调用其方法。但需要创建的对象有 *很多*，跟踪它们可能会很困难。值得庆幸的是，一旦你编写了一个可工作的应用，在其他应用中重用类似代码就很简单。

步骤 3 是困难的部分。要在 GPU 上执行代码，你需要在 WebGPU 着色器语言（WGSL）中编写特殊程序（*着色器*）。WGSL 类似于 C 编程语言，但它被精简以专注于数值计算。也就是说，你不需要字符串处理函数，也可能不会使用很多指针。目标是以高速处理数字，你对线性代数的理解越好，编写着色器就越容易。

WebGPU 应用主要有两种类型：

* *图形应用* 显示在 HTML canvas 中的图形
* *计算应用* 执行计算任务，例如对矩阵进行运算或使用机器学习分析数据

以下讨论探讨了编码这两种类型应用的过程。

### 图形应用开发

在高层次上，图形 WebGPU 应用的目的是定义 HTML canvas 的内容。准确地说，目标是将三维世界转换成立体场景，并在画布中显示该场景。此转换过程称为 *渲染*。

要在 WebGPU 中实现渲染，应用需要在 JavaScript 中创建多个对象，包括一个 `GPURenderPassEncoder` 和一个 `GPURenderPipeline`。应用还需要创建包含 GPU 定义图形场景所需数据的特殊对象。

除了提供数据外，应用还需要向 GPU 提供指令，告诉它如何放置场景中的对象并计算对象的颜色。这些指令必须在两个程序中提供：

* vertex shader—告诉 GPU 在场景中放置对象的位置
* fragment shader—告诉 GPU 为场景的片段分配什么颜色和深度

这些程序必须用 WGSL 编写，下面的代码展示了一个简单的顶点着色器的样子：

```
@group(0) @binding(0) var<uniform> rotMat: mat4x4f;

@vertex
fn vertexMain(@location(0) coords: vec2f) -> @builtin(position) vec4f {    
    return rotMat * vec4f(coords, 0.0, 1.0);
}
```

这看起来可能很可怕，但一旦你熟悉了 WGSL 的数据类型（例如 `mat4x4f` 和 `vec4f`）和属性（例如 `@vertex` 和 `@builtin`），你会发现这段代码很直接。[第 4 章](#chapter4.xhtml) 详细讨论了 WGSL 的特性。

### 计算应用开发

除了图形渲染之外，WebGPU 应用还可以指示 GPU 进行数值计算。在整本书中，我们将这些应用称为 *计算应用*。计算应用的常见用途包括机器学习、图像处理、频率分析和矩阵运算。

计算应用通常比图形应用更容易编码。需要创建的 JavaScript 对象更少，也不需要访问画布。与其关心顶点缓冲区，应用可以将数据存储在存储缓冲区中，后者更容易处理。

此外，计算应用不需要像图形应用那样的顶点着色器和片段着色器。只需要一种着色器——*计算着色器*。与顶点着色器和片段着色器一样，计算着色器也是用 WGSL 编写的。下面的代码展示了一个基本计算着色器的样子：

```
@binding(0) @group(0) var<storage, read_write> data : array<f32, 32>;

@compute @workgroup_size(4)
fn computeMain(
    @builtin(global_invocation_id) id : vec3<u32>,
    @builtin(workgroup_id) wg_id : vec3<u32>,
    @builtin(local_invocation_id) local_id : vec3<u32>)
{
    data[id.x] = f32(wg_id.x) * data[id.x] + f32(local_id.x);
}
```

计算应用与图形应用之间一个主要区别是，计算应用可以将 GPU 的处理组织成 *工作组*。工作组的元素称为 *调用*，可以访问为其组专门分配的内存。这使得组的调用能够协同工作，并使着色器能够同步其操作。

## 示例代码

学习 WebGPU 的最佳方式是亲自动手并与实际代码搏斗。因此，本书的每一章和附录至少有一个示例应用。代码可免费从我的 Github 页面获取，网址为 [https://github.com/mattscar/webgpu_book](https://github.com/mattscar/webgpu_book)。

每个项目文件夹都包含一个名为 `index.html` 的文件和一个 JavaScript 文件（`*.js`）。`index.html` 定义了网页的结构，而 JavaScript 文件包含在页面打开时执行的代码。你只需在浏览器中打开 HTML 文件（`index.html`）即可启动许多应用。

不幸的是，许多应用需要访问外部文件。对于这些应用，如果你在浏览器中打开 `index.html`，你会收到错误。一种解决方法是启动本地 HTTP 服务器并在本地提供页面。Node 生态系统为此提供了 `http-server` 包，[附录 A](#appa.xhtml#appa) 解释了如何安装 Node 和 `http-server` 包。

## 总结

本章介绍了 WebGPU 的主题，从其历史到当前采用情况。简单来说，WebGPU 使 Web 应用能够访问客户端的 GPU。通过访问 GPU，应用可以高速渲染图形和进行数值计算。第一种类型的应用称为图形应用，第二种类型的应用称为计算应用。

本书解释了如何使用 WebGPU 编写图形和计算应用。理论和实践并不容易掌握，但如果你遵循最佳实践，性能提升可能非常惊人。能力越大，复杂性越大…

# 基本对象 2

DOI: [10.1201/9781003422839-2](https://doi.org/10.1201/9781003422839-2)
