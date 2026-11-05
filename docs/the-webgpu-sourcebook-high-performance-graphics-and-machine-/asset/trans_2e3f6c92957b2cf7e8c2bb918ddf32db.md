
# WGSL 变量声明和地址空间

WGSL 支持 `let`、`const` 和 `var`，但它们在 WGSL 与 JavaScript 中的用法存在主要差异。当你在着色器中使用 `let` 或 `const` 时，你声明的是一个 *值*。声明为值分配一个名称，但数据不会存储在任何地方。此外，`let` 只能在函数内部使用，而 `const` 既可以在函数内部也可以在函数外部使用。

当声明以 `var` 开始时，它会创建一个 *变量*，其数据将存储在内存中。这比使用 `let` 和 `const` 更复杂，因为一个 `var` 声明需要标识将包含变量数据的内存类型。

为变量设置内存类型，声明可以在 `var` 后跟随尖括号之间的 *地址空间* 名称。例如，以下代码声明一个 32 位浮点变量存储在私有地址空间中：

```
var<private> foo: f32;
```

设置变量类型的另一种方法是提供一个值。在以下代码中，可以理解变量将存储一个浮点值：

```
var<private> foo = 1234.0;
```

在这些声明中，`private` 关键字表示变量应存储在 `private` 地址空间中。这适用于在着色器函数外部声明的全局变量。如果变量 intended 在函数内部使用，其地址空间应设置为 `function`。如果变量在函数内部声明且没有地址空间，则理解为变量将存储在 `function` 空间中。这在以下代码中显示：

```
// Stored in the function address space
var foo = 1234.0;
```

[表 4.5](#chapter4.xhtml#tbl4_5) 列出了可用于存储变量的所有地址空间。

[表 4.5](#chapter4.xhtml#b4tbl4_5) 变量的地址空间

| 地址空间 || 默认访问模式 || 描述 |
| --- | --- | --- |
| function || 读写 || 函数内部声明的变量 |
| --- | --- | --- |
| private || 读写 || 全局变量 |
| storage || 只读 || 存储缓冲区中的数据 |
| uniform || 只读 || 统一缓冲区中的数据 |
| handle || 只读 || 采样器和纹理变量 |
| workgroup || 读写 || 计算着色器使用的数据 |

[第 3 章](#chapter3.xhtml) 解释了应用程序如何创建用于保存着色器数据的资源。资源有两种类型：*缓冲区*，用于保存通用数据，以及 *纹理*，用于保存纹理数据。要访问资源，着色器需要在 `storage`、`uniform` 或 `handle` 地址空间中声明一个变量。提供资源访问的变量称为 *资源变量*，我将在本章中对其进行讨论。

[第 3 章](#chapter3.xhtml) 还解释了属性数据（如坐标）会从一个顶点变化到下一个顶点。相比之下，uniform 数据在从一个顶点到下一个顶点时保持不变（uniform）。因此，uniform 数据存储在统一缓冲区中，通过 `uniform` 地址空间访问。[第 5 章](#chapter5.xhtml) 将更深入地讨论 uniform。

最后两个地址空间 `handle` 和 `workgroup` 将在后面的章节中讨论。`handle` 空间仅由访问纹理的应用程序使用，这将在 [第 6 章](#chapter6.xhtml) 中讨论。`workgroup` 空间仅由创建计算着色器的应用程序使用，这将在 [第 8 章](#chapter8.xhtml) 中讨论。

## 常量和覆盖变量

正如我们将看到的，将数据从应用程序（JavaScript）传递到着色器（WGSL）通常是一个复杂的过程。你需要创建特殊的资源对象（缓冲区和纹理）并将这些资源与专门格式的数据和其他对象关联。

如果你只想在着色器中设置标量值，可以利用常量（它们与 `const` 关键字无关）。如 [第 3 章](#chapter3.xhtml) 中所述，`createRenderPipeline` 方法接受一个包含 `vertex` 对象和 `fragment` 对象的对象。`vertex` 和 `fragment` 对象有一个可选属性名为 `constants`，可以设置为名称-值对序列。以下代码展示了其工作原理：

```
// Create a render pipeline that defines constants
const renderPipeline = device.createRenderPipeline({
    layout: …,
    vertex: {
        module: …,
        entryPoint: …
        constants: {
            0: false,
            22: 5.4,
            num_pixels: 256,
       }
    },
});
```

在此代码中，`constants` 被设置为包含三个由冒号分隔的名称-值对的对象。每个名称可以是整数或字符串。每个值可以是整数、浮点值或布尔值。

在着色器内部，这些名称-值对可以通过称为 *覆盖变量* 的特殊变量访问。覆盖变量可以用两种方式之一声明。如果常量名称是整数，则相应的声明以包含名称的括号的 `@id` 属性开头。声明的一般形式如下所示：

```
@id(name) override var_name: type;
```

例如，如果 `constants` 对象将 0 映射为 false，则着色器中相应的声明可以如下编码：

```
@id(0) override example: bool;
```

尽管此变量在着色器中未被设置为值，但在着色器执行时它将被设置为 false。

如果常量名称是字符串，则不需要 `@id` 属性。相反，变量的名称需要设置为常量的名称。例如，如果 `constants` 对象将 `num_pixels` 映射为 256，则着色器中相应的声明可以如下编码：

```
override num_pixels: u32;
```

变量的值在着色器中未被设置，但由于 `constants` 对象，`num_pixels` 在着色器执行时将被设置为 256。

覆盖变量在应用程序需要在编译时将简单标量传递给着色器时非常方便。它们在编写计算应用程序时尤其有帮助，计算应用程序将在 [第 8 章](#chapter8.xhtml) 中介绍。

## 顶点着色器

现在你已经了解了 WGSL 的基础知识，让我们看看顶点着色器是如何编码的。以下代码展示了 `Ch04_OrangeTriangle` 应用程序中使用的顶点着色器：

```
@vertex
fn vertexMain(@location(0) coords: vec2f, @location(1) colors: vec3f) -> @builtin(position) vec4f {
    return vec4f(coords, 0.0, 1.0);
}
```

此函数是顶点着色器的入口点，因为其名称 `vertexMain` 前面有 `@vertex`。它接受两个参数（一个 `vec2f` 和一个 `vec3f`）并产生一个向量作为返回值。

这段代码有两个方面需要解释：在两个参数之前出现的 `@location` 属性以及在返回值之前出现的 `@builtin` 属性。在我看来，这些修饰符应称为 *注解* 或 *装饰器*，因为 *attribute* 在 WebGPU 中已有特定含义。然而，WGSL 标准将它们称为属性。

### 位置属性

`@location` 属性使着色器能够访问资源（缓冲区和纹理）中的数据。在前面的代码中，此属性位于着色器的参数 `coords` 和 `colors` 之前。

[第 3 章](#chapter3.xhtml) 解释了如何创建包含二维三角形顶点的顶点缓冲区。每个顶点需要两个属性：每个顶点的 (x, y) 坐标和 RGB 颜色。以下代码显示顶点数据是如何定义的：

```
// Define vertex data (coordinates and colors)
const vertexData = new Float32Array([
    0.0, 0.5, 0.0, 1.0, 0.0,    // First vertex (green)
    −0.5, −0.5, 1.0, 0.0, 0.0,  // Second vertex (red)
    0.5, −0.5, 0.0, 0.0, 1.0    // Third vertex (blue)
]);
```

为了使此数据可供着色器使用，应用程序需要创建一个顶点缓冲区。以下代码展示了如何完成此操作：
