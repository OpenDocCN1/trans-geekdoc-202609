

```python
original_width, original_height = keras.utils.load_img(base_image_path).size
img_height = 400
img_width = round(original_width * img_height / original_height)
```

我们的内容图片如图 12.10 所示，而图 12.11 则展示了我们的风格图片。

![](img/ab452ecf572a1f1372915be13bd8088f_410_0.png)

图 12.10 内容图片：从 Nob Hill 俯瞰旧金山

![](img/ab452ecf572a1f1372915be13bd8088f_410_1.png)

图 12.11 风格图片：梵高的《星月夜》

我们还需要一些辅助函数，用于加载、预处理和后处理进出 VGG19 卷积网络的图像。

### 清单 12.17 辅助函数

```python
import numpy as np

def preprocess_image(image_path):
    img = keras.utils.load_img(
        image_path, target_size=(img_height, img_width))
    img = keras.utils.img_to_array(img)
    img = np.expand_dims(img, axis=0)
    img = keras.applications.vgg19.preprocess_input(img)
    return img

def deprocess_image(img):
    img = img.reshape((img_height, img_width, 3))
    img[:, :, 0] += 103.939
    img[:, :, 1] += 116.779
    img[:, :, 2] += 123.68
    img = img[:, :, ::-1]
    img = np.clip(img, 0, 255).astype("uint8")
    return img
```

让我们搭建 VGG19 网络。就像在 DeepDream 示例中一样，我们将使用预训练的卷积网络来创建一个特征提取器模型，该模型返回中间层的激活值——这次是模型中的所有层。

### 清单 12.18 使用预训练的 VGG19 模型创建特征提取器

```python
model = keras.applications.vgg19.VGG19(weights="imagenet", include_top=False)

outputs_dict = dict([(layer.name, layer.output) for layer in model.layers])

feature_extractor = keras.Model(inputs=model.inputs, outputs=outputs_dict)
```

让我们定义内容损失，以确保 VGG19 卷积网络的顶层对风格图像和组合图像具有相似的视角。

### 清单 12.19 内容损失

```python
def content_loss(base_img, combination_img):
    return tf.reduce_sum(tf.square(combination_img - base_img))
```

接下来是风格损失。它使用一个辅助函数来计算输入矩阵的 Gram 矩阵：即原始特征矩阵中发现的相关性映射。

### 清单 12.20 风格损失

```python
def gram_matrix(x):
    x = tf.transpose(x, (2, 0, 1))
    features = tf.reshape(x, (tf.shape(x)[0], -1))
    gram = tf.matmul(features, tf.transpose(features))
    return gram

def style_loss(style_img, combination_img):
    S = gram_matrix(style_img)
    C = gram_matrix(combination_img)
    channels = 3
    size = img_height * img_width
    return tf.reduce_sum(tf.square(S - C)) / (4.0 * (channels ** 2) * (size ** 2))
```

在这两个损失分量中，你再添加第三个：_总变化损失_，它作用于生成的组合图像的像素。它鼓励生成图像中的空间连续性，从而避免过度像素化的结果。你可以将其解释为一种正则化损失。

### 清单 12.21 总变化损失

```python
def total_variation_loss(x):
    a = tf.square(
        x[:, : img_height - 1, : img_width - 1, :] - x[:, 1:, : img_width - 1, :]
    )
    b = tf.square(
        x[:, : img_height - 1, : img_width - 1, :] - x[:, : img_height - 1, 1:, :]
    )
    return tf.reduce_sum(tf.pow(a + b, 1.25))
```

你要最小化的损失是这三种损失的加权平均值。计算内容损失时，你只使用一个上层——`block5_conv2` 层——而对于风格损失，你使用一个涵盖低级层和高级层的层列表。你在最后添加总变化损失。

取决于你使用的风格参考图片和内容图片，你可能需要调整 `content_weight` 系数（内容损失对总损失的贡献）。更高的 `content_weight` 意味着目标内容在生成的图像中会更容易辨认。

### 清单 12.22 定义最终要最小化的损失

```python
style_layer_names = [
    "block1_conv1",
    "block2_conv1",
    "block3_conv1",
    "block4_conv1",
    "block5_conv1",
]
content_layer_name = "block5_conv2"
total_variation_weight = 1e-6
style_weight = 1e-6
content_weight = 2.5e-8

def compute_loss(combination_image, base_image, style_reference_image):
    input_tensor = tf.concat(
        [base_image, style_reference_image, combination_image], axis=0)
    features = feature_extractor(input_tensor)

    loss = tf.zeros(shape=())
    layer_features = features[content_layer_name]
    base_image_features = layer_features[0, :, :, :]
    combination_features = layer_features[2, :, :, :]
    loss = loss + content_weight * content_loss(
        base_image_features, combination_features
    )
    for layer_name in style_layer_names:
        layer_features = features[layer_name]
        style_reference_features = layer_features[1, :, :, :]
        combination_features = layer_features[2, :, :, :]
        style_loss_value = style_loss(
            style_reference_features, combination_features)
        loss += (style_weight / len(style_layer_names)) * style_loss_value

    loss += total_variation_weight * total_variation_loss(combination_image)
    return loss
```

最后，让我们设置梯度下降过程。在原始的 Gatys 等人论文中，优化是使用 L-BFGS 算法执行的，但 TensorFlow 中不可用，因此我们将改用 SGD 优化器进行小批量梯度下降。我们将利用一个你之前未见过的优化器功能：学习率调度。我们将使用它将学习率从一个非常高的值（100）逐渐降低到一个更小的最终值（约 20）。这样，我们在训练的早期阶段可以快速进展，然后在接近损失最小值时更加谨慎地进行。

### 清单 12.23 设置梯度下降过程

```python
import tensorflow as tf

@tf.function
def compute_loss_and_grads(
    combination_image, base_image, style_reference_image):
    with tf.GradientTape() as tape:
        loss = compute_loss(
            combination_image, base_image, style_reference_image)
        grads = tape.gradient(loss, combination_image)
        return loss, grads

optimizer = keras.optimizers.SGD(
    keras.optimizers.schedules.ExponentialDecay(
        initial_learning_rate=100.0, decay_steps=100, decay_rate=0.96
    )
)

base_image = preprocess_image(base_image_path)
style_reference_image = preprocess_image(style_reference_image_path)
combination_image = tf.Variable(preprocess_image(base_image_path))

iterations = 4000
for i in range(1, iterations + 1):
    loss, grads = compute_loss_and_grads(
        combination_image, base_image, style_reference_image
    )
    optimizer.apply_gradients([(grads, combination_image)])
    if i % 100 == 0:
        print(f"Iteration {i}: loss={loss:.2f}")
        img = deprocess_image(combination_image.numpy())
        fname = f"combination_image_at_iteration_{i}.png"
        keras.utils.save_img(fname, img)
```

图 12.12 展示了你得到的结果。请记住，这种技术实现的只是一种图像重贴图，或者说纹理迁移。它最适合用于纹理强烈且高度自相似的风格参考图片，以及不需要高度细节即可辨认的内容目标。它通常无法实现相当抽象的成就，例如将一幅肖像的风格转移到另一幅肖像上。该算法更接近经典信号处理而非 AI，所以不要指望它像魔法一样起作用！

![](img/ab452ecf572a1f1372915be13bd8088f_414_0.png)

图 12.12 风格迁移结果

此外，请注意这种风格迁移算法运行缓慢。但该设置执行的变换足够简单，也可以由一个小型、快速的前馈卷积网络来学习——只要你有合适的训练数据可用。因此，可以先使用这里概述的方法，花费大量计算周期为固定的风格参考图片生成输入-输出训练样本，然后训练一个简单的卷积网络来学习这种特定于风格的变换。完成之后，对给定图像进行风格化是即时的：只需对这个小型卷积网络进行一次前向传递即可。

### 12.3.4 总结

- 风格迁移包括创建一张新图像，该图像既保留目标图像的内容，又捕捉参考图像的风格。
- 内容可以通过卷积网络的高级激活来捕捉。
- 风格可以通过卷积网络不同层激活的内部相关性来捕捉。
- 因此，深度学习允许将风格迁移表述为使用预训练卷积网络定义的损失的优化过程。
- 从这个基本思想出发，有许多变体和改进是可能的。

## 12.4 使用变分自编码器生成图像

当今最流行且最成功的创意 AI 应用是图像生成：学习隐藏的视觉空间并从中采样，以创造完全新的图片，这些图片是从真实图片中插值而来的——虚构人物、虚构地点、虚构猫狗等图片。

在本节和下一节中，我们将回顾与图像生成相关的一些高级概念，以及该领域两种主要技术的实现细节：*变分自编码器（VAEs）*和*生成对抗网络（GANs）*。请注意，我在这里介绍的技术并不特定于图像——你可以使用 GANs 和 VAEs 开发声音、音乐甚至文本的隐空间——但在实践中，最有趣的结果是用图片获得的，而我们将在此处专注于此。

### 12.4.1 从图像的隐空间中采样

图像生成的关键思想是发展一个低维的*隐空间*表示（像深度学习中的其他一切一样，它是一个向量空间），其中任何点都可以映射到一个“有效”的图像：即看起来像真实事物的图像。能够实现这种映射的模块，以隐点作为输入并输出图像（像素网格），称为*生成器*（GANs 的情况）或*解码器*（VAEs 的情况）。一旦学习了这样的隐空间，你就可以从中采样点，并通过将它们映射回图像空间来生成前所未见的图像（参见图 12.13）。这些新图像是训练图像的中间态。

GANs 和 VAEs 是学习此类图像表示隐空间的两种不同策略，各有其特点。VAEs 非常适合学习

