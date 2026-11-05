
这段代码与在[第6章](#chapter6.xhtml)中介绍的 `ch06_simpletexture` 代码类似。该纹理的格式为 `rgba8unorm`，这意味着每个纹素以 8 位无符号归一化整数存储红色、绿色、蓝色和 alpha 分量。usage 属性包含 `RENDER_ATTACHMENT`，这意味着它可以在渲染应用程序中显示。`usage` 不包含 `GPUTextureUsage.STORAGE_BINDING`，因此其内容为只读。

部分 WebGPU 实现不支持读写纹理，因此应用程序需要创建第二个纹理来保存经过滤波的纹素。该纹理将被写入，因此需要将其创建为 `storage texture`。以下代码展示了其工作原理：

// Create texture to hold storage image
const storageTexture = device.createTexture({
    size: [imageBitmap.width, imageBitmap.height],
    format: "rgba8unorm",
    usage:
        GPUTextureUsage.TEXTURE_BINDING |
        GPUTextureUsage.COPY_DST |
        GPUTextureUsage.STORAGE_BINDING
});

输出纹理将与输入纹理具有相同的大小，因此尺寸被设置为 `imageBitmap.width` 和 `imageBitmap.height`。`STORAGE_BINDING` 标志表示它将用作存储纹理，这意味着着色器可以将其作为具有 `texture_storage_2d` 类型的变量访问。

## 创建计算管线

创建纹理后，应用程序再创建三个对象：计算着色器的着色器模块、计算通道编码器和计算管线。以下代码创建这些对象并在它们之间建立关联：

// Create the shader module
const computeModule = device.createShaderModule({
    label: "Shader module 0",
    code: computeCode
});

// Create the compute pass encoder
const computePass = encoder.beginComputePass({
    label: "Compute Pass 0"
});

// Define the compute procedure
const computePipeline = device.createComputePipeline({
    label: "Compute Pipeline 0",
    layout: "auto",
    compute: {
        module: computeModule,
        entryPoint: "computeMain",
        constants: {
            group_size_x: 16,
            group_size_y: 16
        }
    }
});
computePass.setPipeline(computePipeline);

这段代码根据 `computeCode` 字符串的内容创建 `computeModule`。然后使用着色器模块初始化计算管线。除了设置着色器模块和入口点外，`createComputePipeline` 还提供了两个常量（`image_width` 和 `image_height`），计算着色器可以将其作为覆盖变量访问。此代码的最后一行将管线与计算通道编码器关联起来。

接下来，应用程序通过创建包含两个纹理的绑定组来定义计算操作的数据。以下代码展示了实现方式：

// Create the bind group
let computeBindGroup = device.createBindGroup({
    layout: computeBindGroupLayout,
    entries: [
    {
        binding: 0,
        resource: imageTexture.createView({
            dimension: "2d",
        })
    },
    {
        binding: 1,
        resource: storageTexture.createView({
            dimension: "2d",
        })
    }]
});
computePass.setBindGroup(0, computeBindGroup);

绑定组创建后，最后一行将其与计算通道编码器关联并绑定到值 0。因此，着色器可以通过将 `@group` 属性设置为 0 并将 `@binding` 属性设置为资源的绑定值来访问其资源。

在将计算通道编码器与其指令（`computePipeline`）和数据（`bindGroup`）关联后，应用程序使用以下代码编码计算命令：

// Encode compute commands
computePass.dispatchWorkgroups(40, 40);

// Complete encoding compute commands
computePass.end();

`dispatchWorkgroups` 的参数告诉计算着色器使用 40×40 的工作组网格处理数据。每个工作组包含 16×16 的调用网格，因此总共有 640×640 次调用。因此，每个调用可以使用其全局 ID 处理输入图像的一个像素。

## 计算着色器

计算着色器相当简单。每次调用都会调用 `textureLoad` 从输入图像加载一个纹素。然后它将 RGB 值转换为灰度并调用 `textureStore` 将灰度写入纹理存储。

@group(0) @binding(0) var in_tex : texture_2d<f32>;
@group(0) @binding(1) var out_tex : texture_storage_2d<rgba8unorm, write>;

override group_size_x: u32;
override group_size_y: u32;

@compute @workgroup_size(group_size_x, group_size_y)
fn computeMain(
    @builtin(global_invocation_id) global_id: vec3<u32>) {

    var x = global_id.x;
    var y = global_id.y;
    var k = array<f32, 9>(-1.0, -1.0, -1.0, -1.0, 9.0, -1.0, -1.0, -1.0, -1.0);

    // Load the texel at the given position
    var texel: vec4f =
        k[0] * textureLoad(in_tex, vec2(x-1, y-1), 0) +
        k[1] * textureLoad(in_tex, vec2(x,   y-1), 0) +
        k[2] * textureLoad(in_tex, vec2(x+1, y-1), 0) +
        k[3] * textureLoad(in_tex, vec2(x-1, y), 0) +
        k[4] * textureLoad(in_tex, vec2(x,   y), 0) +
        k[5] * textureLoad(in_tex, vec2(x+1, y), 0) +
        k[6] * textureLoad(in_tex, vec2(x-1, y+1), 0) +
        k[7] * textureLoad(in_tex, vec2(x,   y+1), 0) +
        k[8] * textureLoad(in_tex, vec2(x+1, y+1), 0);

    // Store result to the storage texture
    textureStore(out_tex, vec2(x, y), texel);
}

在这段代码中，`k` 包含图像锐化核的元素。每次调用都会将 `k` 的元素与由其全局 ID 定位的 3×3 纹素块相乘。然后使用 `textureStore` 方法将总和写入输出纹理。

虽然片段着色器使用 `textureSample` 读取纹素，但此计算着色器使用 `textureLoad` 读取纹素数据。与 `textureSample` 不同，`textureLoad` 需要整数坐标且不使用采样器。这两个函数之间的另一个重要区别是计算着色器不能调用 `textureSample`。

## 显示纹理

计算着色器完成后，应用程序创建渲染管线以在画布中显示存储纹理。此代码与[第6章](#chapter6.xhtml)中的代码相似，但有一个有趣之处：顶点/片段着色器将纹理作为 `texture_2d` 访问，而不是 `texture_storage_2d`。这阐明了存储纹理与普通纹理之间没有根本区别这一点。

## 视频处理

WebGPU 最引人注目的功能之一是其能够读取视频源的帧并将其作为纹理处理。这使得可以对视频执行与对普通图像相同的操作。使用 WebGPU 处理视频的一般过程包括四个步骤：

1. 创建、配置并播放 `HTMLVideoElement`。
2. 为每一帧创建 `VideoFrame`。
3. 从每个 `VideoFrame` 创建纹理。
4. 在着色器中处理纹理。

本节探讨这些步骤并展示如何在代码中执行它们。后文将介绍一个处理从 `*.webm` 文件接收的帧的应用程序。

### 视频元素

HTML5 使网页中可以插入 <video> 元素。在 JavaScript 中，这些元素作为 `HTMLVideoElement` 访问，应用程序可以通过调用 `document.createElement` 并将参数设置为 `video` 来创建它们。`HTMLVideoElement` 在本讨论中起着核心作用，因此熟悉其继承层次结构是个好主意。这在[图 10.6](#chapter10.xhtml#fig10_6)中有所说明。

![图 10.6 HTMLVideoElement 继承层次结构.](images/fig10_6.jpg)

[图 10.6](#chapter10.xhtml#b10fig10_6) `HTMLVideoElement` 继承层次结构。
