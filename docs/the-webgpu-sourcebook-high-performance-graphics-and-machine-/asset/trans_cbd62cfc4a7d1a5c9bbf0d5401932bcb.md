

| --- | --- | --- |

| `destination` || Y || 用于标识纹理数据应写入位置的对象 |

| `copySize` || Y || 用于标识纹理数据尺寸的对象 |

第一个参数 `source` 标识纹理数据的来源。此参数必须设置为最多包含三个属性的对象。[表 6.5](#chapter6.xhtml#tbl6_5) 列出了它们各自。

[表 6.5](#chapter6.xhtml#b6tbl6_5) `copyExternalImageToTexture` 源对象的属性

| 属性 || 是否必需？ || 描述 |

| --- | --- | --- |

| `source` || Y || 包含要写入的数据的 `ImageBitmap`、`HTMLVideoElement`、`VideoFrame`、`HTMLCanvasElement` 或 `OffscreenCanvas` |

| --- | --- | --- |

| `origin` || N || 指向数据源的偏移量，用于标识要访问的第一个（左上）位置（默认为 (0, 0)） |

| `flipY` || N || 标识源图像是否应垂直翻转（默认为 false） |

这些属性很容易理解。在整本书中，我们将 `source` 属性设置为第一步中创建的 `ImageBitmap`。

`copyExternalImageToTexture` 的 `destination` 参数标识将接收图像数据的对象。它接受最多六个属性，[表 6.6](#chapter6.xhtml#tbl6_6) 列出了它们各自。

[表 6.6](#chapter6.xhtml#b6tbl6_6) `copyExternalImageToTexture` 源对象的属性

| 属性 || 是否必需？ || 描述 |

| --- | --- | --- |

| `texture` || Y || 使用前面讨论的 `device.createTexture` 方法创建的 `GPUTexture` |

| --- | --- | --- |

| `origin` || N || 指向纹理的偏移量，用于标识要访问的第一个（左上）位置（默认为 (0, 0)） |

| `aspect` || N || 标识应受复制操作影响的纹理的哪个方面；可以是 all、depth-only 或 stencil-only（默认为 all） |

| `mipLevel` || N || 标识应更新纹理的哪个 mipmap 级别（默认为 1） |

| `premultipliedAlpha` || N || 标识在渲染之前是否应将 RGB 通道乘以 alpha 通道（默认为 false） |

| `colorSpace` || N || 标识纹理的颜色空间和编码（默认为 srgb） |

`copyExternalImageToTexture` 的最后一个属性是 `copySize`，它标识从源到目标要写入的数据的尺寸。它可以接受最多三个值：`width`、`height` 和深度或数组层数。这些值必须作为数组提供，或作为具有名为 `width`、`height` 和 `depthOrArrayLayers` 的属性的对象提供。

尽管对象和属性数量众多，但对 `copyExternalImageToTexture` 的大多数调用都相当简单。例如，如果纹理数据存储在 `imageBitmap` 中，并且纹理对象的名称为 `tex`，则以下代码将定义一个操作，将 `imageBitmap` 的所有像素写入 `tex`：

```
 // Copy data from the bitmap into the texture
device.queue.copyExternalImageToTexture(
    { source: imageBitmap },
    { texture: tex },
    [imageBitmap.width, imageBitmap.height]
);
```

如图所示，`ImageBitmap` 的宽度和高度可以通过对象的 `width` 和 `height` 属性获得。

### 步骤 4：创建采样器

如我们所见，着色器可以通过具有 `@location`、`@group` 和 `@binding` 等属性的变量访问缓冲区中的数据。但要访问纹理数据，着色器需要使用一种称为 `sampler` 的特殊资源。简单来说，采样器使纹理着色器能够从纹理中读取像素数据。

在 JavaScript 中，应用程序可以通过调用 `GPUDevice` 的 `createSampler` 方法来创建采样器。这不需要任何参数，但可以接受一个包含多个可选属性的对象。[表 6.7](#chapter6.xhtml#tbl6_7) 列出了它们并提供了每个属性的描述。

[表 6.7](#chapter6.xhtml#b6tbl6_7) 采样器属性

| 属性 || 是否必需？ || 描述 |

| --- | --- | --- |

| `label` || N || 采样器的标识符 |

| --- | --- | --- |

| `minFilter` || N || 标识如果采样器访问的区域小于一个 texel 时应如何获取 texel 数据；可能的值为 nearest 和 linear |

| `magFilter` || N || 标识如果采样器访问的区域大于一个 texel 时应如何获取 texel 数据，可能的值为 nearest 和 linear |

| `mipMapFilter` || N || 标识如果采样器访问的区域位于 mipmap 级别之间时应如何获取 texel 数据，可能的值为 nearest 和 linear |

| `maxAnisotropy` || N || 采样器使用的各向异性钳制 |

| `lodMinClamp` || N || 采样纹理时使用的最小细节级别 (LOD) 范围为 0 到 32；默认为 0 |

| `lodMaxClamp` || N || 采样纹理时使用的最大细节级别范围为 0 到 32；默认为 32 |

| `addressModeU` || N || 标识当采样器在 u 方向访问纹理外部区域时应返回的数据 |

| `addressModeV` || N || 标识当采样器在 v 方向访问纹理外部区域时应返回的数据 |

| `addressModeW` || N || 标识当采样器在 w 方向访问纹理外部区域时应返回的数据 |

| `compare` || N || 创建比较采样器 |

尽管这些属性是可选的，但它们在决定应用程序显示图像的质量方面可能发挥重要作用。以下讨论将查看这些属性并解释它们如何影响渲染过程。

#### 纹理过滤

要在纹理中的特定位置读取 texel 数据，片段着色器使用浮点坐标。如果某个位置位于多个 texel 之间，着色器有两个选项。它可以从中心最接近该点的 texel 读取数据，也可以计算周围 texel 的加权和。这些选项由 `minFilter`、`magFilter` 和 `mipMapFilter` 属性的两个值表示：

*   `nearest`—从中心最接近的 texel 选择数据

*   `linear`—计算周围 texel 的加权平均值

如果将 `minFilter` 设置为 `linear`，纹理采样器将使用一种称为 *双线性插值* 的过程读取数据。要理解其工作原理，假设点 P 位于四个相邻 texel A、B、C 和 D 之间。[图 6.7](#chapter6.xhtml#fig6_7) 显示了其外观。

![图 6.7 双线性插值。](images/fig6_7.jpg)

[图 6.7](#chapter6.xhtml#b6fig6_7) 双线性插值。

为了确定 P 相对于周围 texel 的位置，我们使用两个值 `t[1]` 和 `t[2]`。它们称为插值参数，范围从 0 到 1。如果 `t[1]` 和 `t[2]` 都等于 1，

P 与 D 的中心重合。如果 `t[1]` 和 `t[2]` 都等于 0，P 与 A 的中心重合。

在此图中，P 最接近 A。因此，如果将 `minFilter` 设置为 `nearest`，P 的颜色将被设置为等于 A 的颜色。但如果将其设置为 `linear`，P 的颜色将使用以下方程计算：

Color (P) = *t*[1] × *t*[2] × Color(A) + (1 − *t*[1]) × *t*[2] × Color(B) + *t*[1] × (1−*t*[2]) × Color (C) + (1 −*t*[1]) × (1 − *t*[2]) × Color(D)

`magFilter` 属性标识当 texel 的面积大于片段时应使用的过滤方法。如果纹理包含 mipmap 级别，应用程序可以使用 `mipMapFilter` 属性自定义采样。如果将其设置为 `nearest`，采样器将从最近的 mipmap 图像中选择数据。如果将其设置为 `linear`，采样器将计算相邻 mipmap 中 texel 的加权平均值。

Mipmap 级别可以被视为第三个维度。当双线性过滤与 mipmap 线性过滤结合时，结果称为 *三线性过滤*。

#### 各向异性过滤

在大多数应用程序中，片段着色器将在 x 和 y 方向读取相同数量的样本。这称为 *各向同性过滤*，因为采样在每个方向上执行的方式相同。

