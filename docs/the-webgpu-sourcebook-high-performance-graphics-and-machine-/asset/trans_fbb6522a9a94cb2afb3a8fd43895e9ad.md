
### VertexState 字段

| --- | --- | --- |

| `nextInChain` || `ChainedStruct*` || 指向专用类 |

| --- | --- | --- |

| `module` || `ShaderModule` || 包含着色器代码 |

| `entryPoint` || `char const*` || 顶点着色器的入口点 |

| `constantCount` || `size_t` || 传递给顶点着色器的常量数量 |

| `constants` || `ConstantEntry*` || 传递给顶点着色器的键值对 |

| `bufferCount` || `size_t` || 顶点缓冲区的数量 |

| `buffers` || `VertexBufferLayout*` || 顶点缓冲区的布局 |

[第 4 章](#chapter4.xhtml) 介绍了常量的主题，它使应用程序能够向着色器传递键值对。Dawn 通过 `constants` 字段提供了类似的功能，该字段可以设置为一个或多个 `ConstantEntry` 结构。每个 `ConstantEntry` 都有一个 `key` 字段和一个 `value` 字段，可以通过重写的变量在顶点着色器中访问。

表中最后两个字段与缓冲区相关。`bufferCount` 字段标识可用的顶点缓冲区数量，而 `buffers` 字段标识每个缓冲区的布局。请记住，缓冲区必须设置为缓冲区布局，而不是缓冲区本身。

`AppB_DawnTriangle` 项目中的代码不使用常量且只有一个缓冲区，因此 `VertexState` 结构使用以下代码创建：

// Create vertex state
wgpu::VertexState vertexState {
    .module = shaderModule,
    .entryPoint = "vertexMain",
    .bufferCount = 1,
    .buffers = &vertLayout
};
```

正如 `VertexState` 定义了顶点着色器的操作一样，`FragmentState` 结构定义了片段着色器的操作。[表 B.18](#appb.xhtml#tblb_18) 列出了此结构的字段。

[表 B.18](#appb.xhtml#btblb_18) Fields of the FragmentState structure

| FIELD || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| `nextInChain` || `ChainedStruct*` || 指向专用类 |

| --- | --- | --- |

| `module` || `ShaderModule` || 包含着色器代码 |

| `entryPoint` || `char const*` || 片段着色器的入口点 |

| `constantCount` || `size_t` || 传递给片段着色器的常量数量 |

| `constants` || `ConstantEntry*` || 传递给片段着色器的键值对 |

| `targetCount` || `size_t` || 顶点缓冲区的数量 |

| `targets` || `ColorTargetState*` || 顶点缓冲区的布局 |

`FragmentState` 的大部分字段与 `VertexState` 结构中的字段相同，但 `targetCount` 和 `targets` 字段是新的。`targets` 字段必须设置为一个或多个 `ColorTargetState` 结构，以配置片段着色器产生的颜色。

`ColorTargetState` 结构有一个 `format` 字段，必须设置为 [第 6 章](#chapter6.xhtml) 中介绍的纹理格式之一。以下代码配置片段着色器以生成包含蓝色、绿色、红色和 alpha 分量的颜色，作为 8 位无符号归一化值。

```
// Define the color state
wgpu::ColorTargetState colorTargetState {
    .format = wgpu::TextureFormat::BGRA8Unorm
};
```

创建此结构后，`AppB_DawnTriangle` 中的代码使用以下代码创建 `FragmentState` 结构：

// Create fragment state
wgpu::FragmentState fragmentState {
    .module = shaderModule,
    .entryPoint = "fragmentMain",
    .targetCount = 1,
    .targets = &colorTargetState
};
```

创建 `VertexState` 和 `FragmentState` 后，应用程序将这些结构分配给 `PipelineDescriptor` 的 `vertex` 和 `fragment` 字段。

### 组装图元

默认情况下，Dawn 从前三个顶点创建一个三角形，从下一个三个顶点创建另一个三角形，以此类推。这种组装方法对应于 *三角形列表*，并且是可以通过将 `PipelineDescriptor` 的 `primitive` 字段设置为 `PrimitiveState` 结构来配置的众多功能之一。[表 B.19](#appb.xhtml#tblb_19) 列出了此结构的五个字段。

[表 B.19](#appb.xhtml#btblb_19) Fields of the PrimitiveState structure

| FIELD || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| `nextInChain` || `ChainedStruct*` || 指向专用类 |

| --- | --- | --- |

| `topology` || `PrimitiveTopology` || 设置要组装的图元类型 |

| `stripIndexFormat` || `IndexFormat` || 顶点索引的数据类型 |

| `frontFace` || `FrontFace` || 被视为正面朝向的三角形 的方向 |

| `cullMode` || `CullMode` || 标识应丢弃哪些三角形 |

`topology` 字段告诉渲染器如何从顶点形成形状。它可以设置为 `PrimititveTopology` 类型的任何值，其中包括 `PointList`、`LineList`、`LineStrip`、`TriangleList` 和 `TriangleStrip`。

前一章解释了应用程序如何通过丢弃（或 *剔除*）三角形来提高性能。在 Dawn 中，配置剔除过程需要两个步骤。首先，`frontFace` 字段需要标识被视为正面朝向的三角形的顶点方向。它可以设置为 `FrontFace::CW` 和 `FrontFace::CCW`。默认情况下，顶点按逆时针方向排列的三角形被视为正面朝向。

`cullMode` 标识应从渲染中丢弃哪些三角形。它必须设置为 `CullMode` 类型的值，其中包括 `None`、`Front` 和 `Back`。默认情况下，渲染器不会丢弃任何三角形。

`AppB_DawnTriangle` 中的代码将渲染器设置为组装三角形条带，并将其他字段保留为默认值。以下代码展示了其工作原理：

// Set the primitive state
wgpu::PrimitiveState primitiveState {
    .topology = wgpu::PrimitiveTopology::TriangleStrip
};
```

创建此结构后，`AppB_DawnTriangle` 应用程序将其分配给 `PipelineDescriptor` 的 `primitive` 字段。以下讨论将介绍此重要结构。

### 创建管线

`AppB_DawnTriangle` 项目不使用多重采样或深度/模板缓冲区。因此，`PipelineDescriptor` 中唯一需要设置的字段是 `layout`、`vertex`、`shader` 和 `primitive`。以下代码展示了如何使用前面创建的结构设置这些字段。

```
// Create the render pipeline
wgpu::RenderPipelineDescriptor pipelineDescriptor{
    .layout = pipelineLayout,
    .vertex = vertexState,
    .primitive = primitiveState,
    .fragment = &fragmentState
};
pipeline = device.CreateRenderPipeline(&pipelineDescriptor);
```

管线描述符创建后，应用程序可以将其与渲染通道编码器关联。但在创建渲染通道编码器之前，应用程序需要为渲染定义 surface 和 swapchain。

## 表面和交换链

如果你编写 WebGPU 代码在浏览器中运行，则无需担心低级渲染细节。然而，Dawn 的渲染并不限于浏览器。因此，Dawn 应用程序需要精确定义渲染如何以及在何处执行。

为了在低级层面定义渲染过程，应用程序需要创建一个 `Surface`，它标识用于渲染的抽象区域。它还需要创建一个 `Swapchain`，它控制渲染如何执行。本讨论解释了如何创建这两个数据结构。

### 创建表面

Dawn 提供了一个 `Surface` 类来表示渲染区域。要创建 `Surface`，应用程序需要调用 `Instance` 对象的 `createSurface` 函数。它接受一个 `SurfaceDescriptor`，该描述符有两个字段：`nextInChain` 和 `label`。

`AppB_DawnTriangle` 应用程序在浏览器中运行，并使用 HTML canvas 作为其渲染表面。因此，它需要将 `SurfaceDescriptor` 的 `nextInChain` 字段设置为指向 `SurfaceDescriptorFromCanvasHTMLSelector`。它有一个 `selector` 字段，用于标识用作渲染表面的 canvas。
