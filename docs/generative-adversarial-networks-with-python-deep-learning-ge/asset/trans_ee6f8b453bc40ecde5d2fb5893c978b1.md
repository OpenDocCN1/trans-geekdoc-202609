

将像素值缩放到 [-1,1] 范围，然后扩展单个图像的维度以表示一个输入样本。下面的 load_image() 函数实现了此功能，返回可直接提供给已加载 Pix2Pix 模型的图像像素。

```python
# load an image
def load_image(filename, size=(256,256)):
    # load image with the preferred size
    pixels = load_img(filename, target_size=size)
    # convert to an array
    pixels = img_to_array(pixels)
    # scale from [0,255] to [-1,1]
    pixels = (pixels - 127.5) / 127.5
    # reshape to 1 sample
    pixels = expand_dims(pixels, 0)
    return pixels
```

清单 23.25：用于加载和准备图像以进行翻译的函数示例。

然后，我们可以加载裁剪后的卫星图像。

```python
...
# load source image
src_image = load_image('satellite.jpg')
print('Loaded', src_image.shape)
```

清单 23.26：加载和准备图像的示例。

与之前一样，我们可以加载保存的 Pix2Pix 生成器模型，并生成加载图像的翻译。

```python
...
# load model
model = load_model('model_109600.h5')
# generate image from source
gen_image = model.predict(src_image)
```

清单 23.27：加载生成器并翻译图像的示例。

最后，我们可以将像素值重新缩放到 [0,1] 范围并绘制结果。

```python
...
# scale from [-1,1] to [0,1]
gen_image = (gen_image + 1) / 2.0
# plot the image
pyplot.imshow(gen_image[0])
pyplot.axis('off')
pyplot.show()
```

清单 23.28：绘制单个翻译图像的示例。

将所有内容整合在一起，下面列出了使用单个图像文件执行临时图像翻译的完整示例。

```python
# example of loading a pix2pix model and using it for one-off image translation
from keras.models import load_model
from keras.preprocessing.image import img_to_array
from keras.preprocessing.image import load_img
from numpy import expand_dims
from matplotlib import pyplot
```

```python
# load an image
def load_image(filename, size=(256,256)):
    # load image with the preferred size
    pixels = load_img(filename, target_size=size)
    # convert to numpy array
    pixels = img_to_array(pixels)
    # scale from [0,255] to [-1,1]
    pixels = (pixels - 127.5) / 127.5
    # reshape to 1 sample
    pixels = expand_dims(pixels, 0)
    return pixels

# load source image
src_image = load_image('satellite.jpg')
print('Loaded', src_image.shape)
# load model
model = load_model('model_109600.h5')
# generate image from source
gen_image = model.predict(src_image)
# scale from [-1,1] to [0,1]
gen_image = (gen_image + 1) / 2.0
# plot the image
pyplot.imshow(gen_image[0])
pyplot.axis('off')
pyplot.show()
```

清单 23.29：翻译单个图像的示例。

运行示例将从文件加载图像，创建其翻译，并绘制结果。生成的图像似乎是源图像的合理翻译。街道似乎不是直线，建筑物的细节有点不足。也许通过进一步训练或选择不同的模型，可以生成更高质量的图像。

![](img/443014fed0f53a293f6ece3b211c1603_527_0.png)

图 23.8：使用最终 Pix2Pix GAN 模型将卫星图像翻译为 Google 地图的图表。

## 23.6 如何将 Google 地图翻译为卫星图像

既然我们已经熟悉如何开发和使用 Pix2Pix 模型将卫星图像翻译为 Google 地图，我们也可以探索相反的情况。也就是说，我们可以开发一个 Pix2Pix 模型，将 Google 地图图像翻译为逼真的卫星图像。这要求模型发明（或幻觉）逼真的建筑物、道路、公园等。我们可以使用相同的代码来训练模型，只有一个小的不同。我们可以更改 `load_real_samples()` 函数返回的数据集顺序；例如：

```python
# load and prepare training images
def load_real_samples(filename):
    # load the compressed arrays
    data = load(filename)
    # unpack arrays
    X1, X2 = data['arr_0'], data['arr_1']
    # scale from [0,255] to [-1,1]
    X1 = (X1 - 127.5) / 127.5
    X2 = (X2 - 127.5) / 127.5
    # return in reverse order
    return [X2, X1]
```

清单 23.30：用于按反向顺序加载配对图像的函数示例。

在此版本的函数中，X1 和 X2 的顺序被反转。这意味着模型将以 Google 地图图像作为输入，并学习生成卫星图像。为简洁起见，此处省略完整示例。与之前一样运行示例。

**注意**：在 CPU 硬件上运行示例可能需要许多小时。如果可能，我建议在 GPU 硬件上运行示例。如果您需要帮助，可以使用 AWS EC2 实例快速开始训练模型。请参阅附录 C 中的说明。

与之前一样，每次训练迭代都会报告模型的损失。如果判别器的损失降至零并长时间保持不变，请考虑重新启动训练运行，因为这是训练失败的一个示例。

**注意**：由于学习算法的随机性，您的具体结果可能会有所不同。请考虑运行示例几次并比较平均性能。

```
>1, d1[0.442] d2[0.650] g[49.790]
>2, d1[0.317] d2[0.478] g[56.476]
>3, d1[0.376] d2[0.450] g[48.114]
>4, d1[0.396] d2[0.406] g[62.903]
>5, d1[0.496] d2[0.460] g[40.650]
...
>109596, d1[0.311] d2[0.057] g[25.376]
>109597, d1[0.028] d2[0.070] g[16.618]
>109598, d1[0.007] d2[0.208] g[18.139]
>109599, d1[0.358] d2[0.076] g[22.494]
>109600, d1[0.279] d2[0.049] g[9.941]
>Saved: plot_109600.png and model_109600.h5
```

清单 23.31：在反向顺序的准备地图数据集上训练 Pix2Pix GAN 的示例输出。

生成的卫星图像质量更难判断，然而，仅在 10 个时代后就会生成逼真的图像。

![](img/443014fed0f53a293f6ece3b211c1603_529_0.png)

图 23.9：使用 Pix2Pix 在 10 个训练时代后将 Google 地图翻译为卫星图像的图表。

与之前一样，图像质量将在训练过程中不断提高并继续变化。最终模型可以根据生成的图像质量来选择，而不是根据总训练时代数。该模型似乎在生成合理的水体、公园、道路等方面几乎没有困难。

![](img/443014fed0f53a293f6ece3b211c1603_530_0.png)

图 23.10：使用 Pix2Pix 在 90 个训练时代后将 Google 地图翻译为卫星图像的图表。

## 23.7 扩展

本节列出了一些您可能希望探索的扩展教程的想法。

- **独立卫星**。开发一个示例，将独立的 Google 地图图像翻译为卫星图像，就像我们为卫星到 Google 地图图像所做的那样。
- **新图像**。为完全新的位置找到一张卫星图像，并将其翻译为 Google 地图，然后将结果与 Google 地图中的实际图像进行比较。
- **更多训练**。继续训练模型另外 100 个时代，并评估额外训练是否会带来图像质量的进一步提升。
- **图像增强**。在训练期间使用一些轻微的图像增强，如 Pix2Pix 论文中所述，并评估是否会产生更高质量的生成图像。

如果您探索其中任何扩展，我很乐意了解。

## 23.8 进一步阅读

如果您希望深入了解，本节提供了更多关于该主题的资源。

### 23.8.1 官方

- 使用条件对抗网络的图像到图像翻译，2016。https://arxiv.org/abs/1611.07004
- 使用条件对抗网络的图像到图像翻译，主页。https://phillipi.github.io/pix2pix/
- 使用条件对抗网络的图像到图像翻译，GitHub。https://github.com/phillipi/pix2pix
- pytorch-CycleGAN-and-pix2pix，GitHub。https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
- 交互式图像到图像演示，2017。https://affinelayer.com/pixsrv/
- Pix2Pix 数据集 http://efrosgans.eecs.berkeley.edu/pix2pix/datasets/

### 23.8.2 API

- Keras 数据集 API。https://keras.io/datasets/
- Keras 顺序模型 API https://keras.io/models/sequential/
- Keras 卷积层 API。https://keras.io/layers/convolutional/
- 如何“冻结” Keras 层？https://keras.io/getting-started/faq/#how-can-i-freeze-keras-layers

## 23.9 总结

在本教程中，您了解了如何开发用于图像到图像翻译的 Pix2Pix 生成对抗网络。具体而言，您学习了：

- 如何加载和准备卫星图像到 Google 地图图像到图像翻译数据集。
- 如何开发用于将卫星照片翻译为 Google 地图图像的 Pix2Pix 模型。
- 如何使用最终的 Pix2Pix 生成器模型翻译临时卫星图像。

