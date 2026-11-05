
`@group(0)` 属性指定变量取自绑定组 0 中的资源。`@binding(0)` 属性表示采样器对应于绑定组中绑定值为 0 的资源。`@binding(1)` 属性表示纹理对应于绑定组中绑定值为 1 的资源。

在声明变量之后，片段着色器通过调用前面讨论过的 `textureSample` 方法来设置片段的颜色。如下代码所示：

```
fn fragmentMain(fragData: DataStruct) -> @location(0) vec4f {
    return textureSample(tex, sam, fragData.uvPos);
}
```

`textureSample` 的第一个参数是纹理，第二个是采样器，第三个是要采样的位置。该位置以 UV 坐标给出，这些坐标从顶点着色器传递给片段着色器。UV 坐标与传入顶点的 (x, y) 坐标不同，理解这一点很重要。

在 `ch06_simpletexture.js` 代码中，顶点缓冲区为每个顶点存储四个值：(x, y) 坐标和 (u, v) 坐标。顶点着色器将 (x, y) 坐标分配给每个顶点，而片段着色器使用 (u, v) 坐标从纹理中采样数据。

## 深度和模板测试

默认情况下，`WebGPU` 按应用程序给定的顺序绘制三角形，而不考虑其位置。这意味着如果远处的物体绘制得更晚，其三角形的绘制会覆盖近处物体的三角形。这在表面重叠时经常导致问题。

为了解决这个问题，应用程序可以利用 *深度测试*。目标是确保深度最低的片段被绘制，而深度更大的片段被丢弃。

如前所述，每个片段都有一个深度范围从 0.0（最近）到 1.0（最远）。在每个片段位置，应用程序存储一个最小深度值和对应的片段。如果新片段的深度值低于存储的值，则存储其深度并丢弃旧片段。这可以用以下伪代码表示：

```
let x = newFragment.x;
let y = newFragment.y;
let minDepthValue = depth(x, y);
if(newFragment.depth < minDepthValue) {
    depth(x, y) = newFragment.depth;
    fragment(x, y) = newFragment;
}
```

存储每个位置最小片段深度的结构称为 *深度缓冲区*，也称为 *z 缓冲区*。本质上，它是一个深度值在 0.0 到 1.0 之间的二维数组。

除了深度缓冲区外，应用程序还可以设置 *模板缓冲区* 中的值。片段着色器可以读取这些值，执行比较测试，并根据结果保留或丢弃片段。本质上，模板缓冲区使能够屏蔽渲染区域的部分。

模板值不需要太多位，因此常见的做法是让一个缓冲区同时充当深度缓冲区 *和* 模板缓冲区。常见的做法是使用 24 位存储深度值和 8 位存储模板值。

因此，`WebGPU` 文档将深度和模板测试的主题结合在一起，并将其称为 *深度/模板测试*。请记住，这两个测试是不同的，应用程序可以执行深度测试、模板测试、两者或都不执行。

在 OpenGL 中，通过调用 `glEnable(GL_DEPTH_TEST)` 来启用深度测试。在 `WebGPU` 中，过程要复杂得多。要在 `WebGPU` 中实现深度/模板测试，应用程序需要执行五个步骤：

1. 创建一个纹理用作深度/模板缓冲区。
2. 创建并配置比较采样器以访问纹理。
3. 配置渲染通道编码器以访问深度和模板缓冲区。
4. 配置渲染管线以执行深度/模板测试。
5. 在片段着色器中执行比较测试。

本文讨论探讨了这些步骤中的每一个。在每种情况下，我们都会查看测试过程中需要的对象和方法。

### 创建深度/模板纹理

在启用深度/模板测试之前，应用程序需要创建一个纹理来存储深度和/或模板值。这就是深度/模板缓冲区，可以使用本章前面讨论过的相同的 `device.createTexture` 方法创建。但有三点需要注意：

* 纹理的内容（可能）不会设置为图像，因此（通常）无需设置 `GPUTextureUsage.COPY_DST` 标志。
* 纹理的 `size` 通常应设置为覆盖视口中的每个像素。
* 纹理的 `format` 必须设置为深度/模板格式之一。

这一点很重要。如果纹理将保存深度和/或模板值，其格式不能设置为常规纹理格式。相反，format 属性需要设置为 [表 6.15](#chapter6.xhtml#tbl6_15) 中的值之一。

[表 6.15](#chapter6.xhtml#b6tbl6_15) 深度/模板纹理格式

| 格式 || 描述 |
| --- | --- |
| `stencil8` || 存储 8 位模板值 |
| --- | --- |
| `depth16unorm` || 存储为 16 位无符号归一化整数的深度值 |
| `depth24plus` || 使用至少 24 位每值存储整数深度值 |
| `depth24plus-stencil8` || 使用至少 24 位每值存储整数深度值并使用 8 位值存储模板值 |
| `depth32float` || 存储为 32 位浮点值的深度值 |
| `depth32float-stencil8` || 存储为 32 位浮点值的深度值和存储为 8 位整数的模板值 |

截至本文撰写时，并非所有符合条件的 GPU 都支持 `depth32float-stencil8` 格式。在使用之前，请务必检查 `GPUAdapter` 的 `features` 属性，以查看是否支持 `depth32float-stencil8` 功能。

作为示例，以下代码创建了一个 400 x 200 的纹理用作深度/模板缓冲区。format 属性设置为 `depth24plus-stencil8`，因此纹理可以存储深度和模板值。

```
// Create texture to store depth/stencil values.
const depthStencilTexture = device.createTexture({
    size: [400, 200, 1],
    usage: GPUTextureUsage.RENDER_ATTACHMENT |
        GPUTextureUsage.TEXTURE_BINDING,
    format: "depth24plus-stencil8"
});
```

创建纹理后，应用程序需要创建一个 *纹理视图* 来提供对纹理数据的访问。这是通过调用纹理的 `createView` 方法创建的，如以下代码所示：

```
const depthStencilView = depthStencilTexture.createView();
```

一旦此视图可用，应用程序就可以配置渲染通道编码器以访问纹理来存储深度和/或模板值。我将在接下来讨论这一点。

### 创建比较采样器

与常规纹理一样，片段着色器使用采样器从深度/模板纹理中读取。但用于深度/模板测试的采样器与常规采样器不同。它们称为 *比较采样器*，应用程序需要在配置过程中做两处小的更改。

首先，必须使用具有 `compare` 属性的对象调用 `device.createSampler` 方法，该属性标识要执行的比较的性质。这在以下代码中显示：

```
resource: device.createSampler({
    compare: "less",
}
```

其次，绑定组布局需要使用采样器进行配置，其 `type` 属性设置为 `comparison`。以下代码显示了如何执行此操作：

```
const bindGroupLayout = device.createBindGroupLayout({
    entries: [
        {
            binding: 0,
            visibility: GPUShaderStage.FRAGMENT,
            sampler: {
                type: "comparison",
            },
        },
    ],
});
```

因此，片段着色器将能够将采样器作为比较采样器访问。

### 配置渲染通道编码器
