

// Iterate through test points
for (var test: u32 = 0; test < num_test_points; test++) {

    var test_addr = test * num_inputs;

    // First layer
    if (batch_id == 0) {
        sum = 0.0;
        for (i = 0; i < num_inputs; i++) {
            sum += test_data[test_addr + i] * weights[node_id * num_inputs + i];
        }
        sum += bias_weights[node_id];
        layer1[node_id] = max(0.0, sum);
    }
    workgroupBarrier();
    // Second layer
    weight_addr = l1_size * num_inputs;
    bias_addr = l1_size;
    if (batch_id == 0) {
        sum = 0.0;
        for (i = 0; i < l1_size; i++) {
            sum += layer1[i] * weights[weight_addr + node_id * l1_size + i];
        }
        sum += bias_weights[bias_addr + node_id];
        layer2[node_id] = max(0.0, sum);
    }
    workgroupBarrier();

    // Third layer
    weight_addr += l2_size * l1_size;
    bias_addr += l2_size;
    if((batch_id == 0) && (node_id < l3_size)) {
        sum = 0.0;
        for (i = 0; i < l2_size; i++) {
            sum += layer2[i] * weights[weight_addr + node_id * l2_size + i];
        }
        sum += bias_weights[bias_addr + node_id];
        layer3[node_id] = sum;
    }
    workgroupBarrier();

    // Update test result buffer
    if(id.x == 0) {
        d = exp(layer3[0]) + exp(layer3[1]) + exp(layer3[2]);
        test_results[test * 3] = exp(layer3[0])/d;
        test_results[test * 3 + 1] = exp(layer3[1])/d;
        test_results[test * 3 + 2] = exp(layer3[2])/d;
    }
    storageBarrier();
}
```

如图所示，`Layer 1` 中的节点读取测试输入数据，将其乘以 `weights`，并将 `bias weight` 加到 `sum` 上。`Layer 2` 中的节点接收 `Layer 1` 节点的加权输出，而 `Layer 3` 中的节点接收 `Layer 2` 节点的加权输出。最终概率是通过对 `Layer 3` 的值取 `softmax` 计算得出的。

## Summary

现代数据处理中机器学习的重要性不言而喻，且其重要性随着每一天的过去而不断增长。本章展示了 `WebGPU` 如何使在 Web 应用程序中利用这一能力成为可能。虽然鸢尾花分类可能看起来并不令人印象深刻，但本章介绍的方法可以应用于其他任务。

神经网络是机器学习最流行的实现方式。神经网络由排列在各层中的节点组成。每个节点接收多个加权输入，将它们相加，并将总和传递给激活函数。如本章所述，最流行的激活函数是 `ReLU`、`logistic` 和 `softmax` 函数。

在处理神经网络时，主要的困难在于更新 `weights`，以使最终层的节点产生合适的输出。这被称为 `training`，理解或编码都不容易。但一旦神经网络完全训练完毕，它就能执行许多人会觉得惊人的分类和预测任务。

# 图像和视频处理10

DOI: [10.1201/9781003422839-10](https://doi.org/10.1201/9781003422839-10)

在最近两章中，`compute shaders` 对存储在 `storage buffers` 中的原始数据进行了操作。这对于计算数字来说是合适的，但 `compute shaders` 也可以访问名为 `storage textures` 的特殊纹理。这使得 `compute shaders` 能够高速处理图像。

本章首先解释 `storage textures` 是什么、如何创建以及如何在 `compute shaders` 中访问它们。为了演示，我将逐步介绍一个在 `compute shader` 中执行图像滤波的应用程序的开发过程。

本章的下一部分重点介绍视频处理。我将解释如何在 `HTML` 中创建视频元素，以及 `WebCodecs API` 如何使访问视频帧成为可能。然后我将解释如何从视频帧创建纹理并使用 `WebGPU` 处理它们。

## Storage Textures

## 存储纹理

[第6章](#chapter6.xhtml) 介绍了纹理主题并演示了如何创建和显示它们。`WebGPU` 支持多种不同的纹理格式，而 `fragment shaders` 使用 `samplers` 从中读取 texel 数据。

在低层级，`storage textures` 与普通纹理完全相同。根本区别在于着色器可以写入 `storage textures`。在撰写本文时，`storage textures` 为 `write-only`。规范指出支持 `read-write` `storage textures`，但目前浏览器中尚不可用。

从编码角度来看，`storage textures` 与普通纹理在三个主要方面不同：

*   调用 `createTexture` 时，使用标志必须包含 `GPUTextureUsage.STORAGE_BINDING` 以将纹理标识为 `storage texture`。
*   在 `compute shader` 中，`storage texture` 必须使用合适的 `storage texture type` 声明。
*   在 `compute shader` 中，可以通过调用 `textureStore` 写入 `storage texture`。

对于第二点，`storage texture` 的通用声明如下所示：

```
@group(…) @binding(…) var name: storage_type<format, access>;
```

`group` 和 `binding` 属性在 [第4章](#chapter4.xhtml) 中引入。`storage_type` 部分可以用 [表10.1](#chapter10.xhtml#tbl10_1) 中列出的类型之一替换。

[表10.1](#chapter10.xhtml#b10tbl10_1) 存储纹理类型

| 存储纹理类型 || 描述 |
| --- | --- |
| `texture_storage_1d` || 一维存储纹理 |
| --- | --- |
| `texture_storage_2d` || 二维存储纹理 |
| `texture_storage_2d_array` || 二维存储纹理数组 |
| `texture_storage_3d` || 三维存储纹理 |

`Storage textures` 不支持深度/模板值访问或多重采样。此外，声明中的 `format` 部分只能设置为有限数量的纹理格式。[表10.2](#chapter10.xhtml#tbl10_2) 列出了 `storage textures` 支持的不同格式。

[表10.2](#chapter10.xhtml#b10tbl10_2) 存储纹理格式

| `rgba8unorm` || `rgba16float` || `rg32float` |
| --- | --- | --- |
| `rgba8snorm` || `r32uint` || `rgba32uint` |
| `rgba8uint` || `r32sint` || `rgba32sint` |
| `rgba8sint` || `r32float` || `rgba32float` |
| `rgba16uint` || `rg32uint` || `bgra8unorm` |
| `rgba16sint` || `rg32sint` ||  |

这些纹理格式 each has one (`r`)、two (`rg`) 或 four (`rgba`/`bgra`) 个颜色通道。`storage textures` 不支持压缩。

声明的最后一部分标识纹理在着色器中如何被访问。根据规范，这可以设置为 `read`、`write` 或 `read-write`。在撰写本文时，每个 `storage texture` 必须将此值设置为 `write`。

为了演示，以下代码声明了一个名为 `tex` 的变量，表示一个二维只写 `storage texture`。每个 texel 包含四个通道，表示为 8 位无符号归一化整数。

```
// Declare a storage texture
@binding(0) @group(0) var tex: texture_storage_2d<rgba8unorm, write>
```

在声明了 `storage texture` 之后，着色器可以通过调用 `textureStore` 写入它。它接受一个纹理变量、应写入值的位置以及要写入的值。作为示例，以下代码将一个四元素向量写入位置 (3, 3)。

```
// Write texture data
textureStore(tex, vec2u(3, 3), vec4f(1.0, 1.0, 1.0, 1.0));
```

值得注意的是，`textureStore` 不接受 `sampler`。此外，第二个参数必须作为无符号整数向量给出。

## Image Filtering

## 图像滤波

专业的图像编辑工具，例如 `Adobe Photoshop` 和 `GNU Image Manipulation Program (GIMP)`，可以为图像添加模糊、锐化和浮雕等效果。这些效果是通过图像滤镜实现的。本节解释图像滤镜的工作原理以及如何使用 `WebGPU` 实现它们。

