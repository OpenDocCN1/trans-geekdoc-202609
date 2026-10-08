
加载的图像在此显示，供你参考：

![](img/48c861eac4dc634fbf2a09fdbe884beb_101_0.png)

八倍度（octaves）、尺寸以及尺度空间（scale space）的数量在这里定义：

```
no_octave = 4
scale = 1.4
window_size = 51
```

这些值对于此处显示的示例效果良好，因此需要根据其他图像的大小进行调整。可以选择某一层进行“梦梦”（dreaming），该层的平均值将作为目标函数，如下所示：

```
score = tf.reduce_mean(objective_fn)
gradients = tf.gradients(score, input_placeholder)[0]
```

为了优化，计算图像的梯度。八倍度图像可以通过将图像缩放为不同的尺度并找到差异来计算，如下：

```python
octave_images = []
for i in range(no_octave - 1):
    image_height_width = image.shape[:2]
    scaled_image = resize_image(image,
        tf.int32(np.float32(image_height_width)) / scale)
```

## 图像检索

## 第3章

```python
image_difference = image - resize_image(scaled_image, image_height_width)
image = scaled_image
octave_images.append(image_difference)
```

可以使用所有的八倍度运行优化。窗口在图像上滑动，计算梯度以创建“梦境”，如下所示：

```python
for octave_idx in range(no_octave):
    if octave_idx > 0:
        image_difference = octave_images[-octave_idx]
        image = resize_image(image, image_difference.shape[:2]) + image_difference
```

```python
for i in range(10):
    image_height, image_width = image.shape[:2]
    sx, sy = np.random.random(np.roll(window_size, size=2))
    shifted_image = np.roll(np.roll(image, sx, 1), sy, 0)
    gradient_values = np.zeros_like(image)

    for y in range(0, max_height - window_size // 2, window_size):
        for x in range(0, max(image_width - window_size // 2, window_size), window_size):
            sub = shifted_image[y:y + window_size, x:x + window_size]
            gradient_windows = session.run(gradients, input_placeholder:sub)
            gradient_values[y:y + window_size, x:x + window_size] = gradient_windows
    gradient_windows = np.roll(np.roll(gradient_values, -sx, 1), -sy, 0)
    image += gradient_windows * (1.5 / (np.abs(gradient_windows)).mean())
```

现在，创建 DeepDream 的优化已经完成，可以通过裁剪数值将其保存如下：

```python
image /= 255.0
image = np.uint8(np.clip(image, 0, 1) * 255)
PIL.Image.fromarray(image).save('dream_' + image_name, 'jpeg')
```

在本节中，我们学习了创建 DeepDream 的流程。结果所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_103_0.png)

如我们看到的，狗脸蛞虫到处被激活。你可以尝试其他不同的层并查看结果。这些结果可以用于艺术目的。同样，也可以激活其他层来产生不同的伪影。在接下来的节中，我们将看到一些可以欺骗深度学习模型的对抗示例。

## 对抗示例

图像分类算法在几个数据集上已经达到了人类水平的准确率。但它们很容易被对抗示例欺骗。对抗示例是合成图像，能够欺骗模型产生所需的输出结果。取任意图像并选择一个错误的随机目标类别。可以使用噪声对图像进行修改，直到网络被欺骗，正如 Goodfellow 等人（https://arxiv.org/pdf/1412.6572.pdf）所示。此处展示了对模型的对抗攻击示例：

| | .007 x | |
|---|---|---|
| | 经 Goodfellow 等人许可复制 | |

## 图像检索

## 第3章

在图中，左侧显示了一个图像，对特定标签有 58% 的置信度。左侧图像与中间显示的噪声结合时，右侧的形状[显现了]。对于人类来说，带有噪声的图像看起来仍然相同。但带有噪声的图像被预测为不同的标签。
