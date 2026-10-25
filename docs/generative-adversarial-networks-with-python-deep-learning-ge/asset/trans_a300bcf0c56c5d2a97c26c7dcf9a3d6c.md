
模型每训练五个 epoch 保存一次，或者每 (1187 × 5) 5,935 次训练迭代保存一次，文件名中同样使用迭代次数。

```
g_model_AtoB_053415.h5
g_model_AtoB_059350.h5
...
g_model_BtoA_053415.h5
g_model_BtoA_059350.h5
```

清单 26.20：已保存生成器模型的示例输出。

生成图像的图表可用于选择模型，更多的训练迭代不一定意味着更高质量的生成图像。马到斑马的翻译在大约 50 个 epoch 后开始变得可靠。

![](img/443014fed0f53a293f6ece3b211c1603_585_0.png)

图 26.2：53,415 次训练迭代后的源马照片（顶行）和翻译斑马照片（底行）图表。

斑马到马的翻译对模型来说似乎更具挑战性，尽管在 50 到 60 个 epoch 后也开始生成一些看似合理的翻译。我怀疑，如论文中所用，通过额外的 100 个训练 epoch 配合权重衰减，或许可以获得更高质量的结果，同时也许还可以使用一个系统地遍历每个数据集而非随机采样的数据生成器。

![](img/443014fed0f53a293f6ece3b211c1603_586_0.png)

图 26.3：90,212 次训练迭代后的源斑马照片（顶行）和翻译马照片（底行）图表。

既然我们已经训练好了 CycleGAN 生成器，就可以以临时的方式使用它们来翻译照片。

## 26.5 如何使用 CycleGAN 执行图像翻译

已保存的生成器模型可以加载并用于临时图像翻译。第一步是加载数据集。我们可以使用上一节开发的相同 `load_real_samples()` 函数。

```
...
# load dataset
A_data, B_data = load_real_samples('horse2zebra_256.npz')
print('Loaded', A_data.shape, B_data.shape)
```

清单 26.21：加载准备好的数据集的示例。

查看生成图像的图表并选择一对可用于图像生成的模型。在此示例中，我们将使用在大约第 89 个 epoch（训练迭代 89,025）保存的模型。我们的生成器模型使用了 keras_contrib 库中的自定义层，具体来说是 InstanceNormalization 层。因此，在加载每个生成器模型时，我们需要指定如何加载该层。这可以通过指定层名称到对象的字典映射，并将其作为参数传递给 Keras 的 load_model() 函数来实现。

```
# load the models
cust = {'InstanceNormalization': InstanceNormalization}
model_AtoB = load_model('g_model_AtoB_089025.h5', cust)
model_BtoA = load_model('g_model_BtoA_089025.h5', cust)
```

清单 26.22：加载已保存生成器模型的示例。

我们可以使用上一节开发的 select_sample() 函数从数据集中选择一张随机照片。

```
# select a random sample of images from the dataset
def select_sample(dataset, n_samples):
    # choose random instances
    ix = randint(0, dataset.shape[0], n_samples)
    # retrieve selected images
    X = dataset[ix]
    return X
```

清单 26.23：从数据集中选择随机图像样本的函数示例。

接下来，我们可以使用 Generator-AtoB 模型，首先从域 A（马）中选择一张随机图像作为输入，使用 Generator-AtoB 将其翻译到域 B（斑马），然后使用 Generator-BtoA 模型重建原始图像（马）。

```
... select input and generate translated images
A_real = select_sample(A_data, 1)
B_generated = model_AtoB.predict(A_real)
A_reconstructed = model_BtoA.predict(B_generated)
```

清单 26.24：使用生成器模型翻译图像的示例。

然后，我们可以将三张照片并排绘制，分别为原始/真实照片、翻译照片和原始照片的重建。下面的 show_plot() 函数实现了此功能。

```
# plot the image, the translation, and the reconstruction
def show_plot(imagesX, imagesY1, imagesY2):
    images = vstack((imagesX, imagesY1, imagesY2))
    titles = ['Real', 'Generated', 'Reconstructed']
    # scale from [-1,1] to [0,1]
```

清单 26.25：绘制生成图像的函数示例。

然后，我们可以调用此函数来绘制真实照片和生成的照片。

```
...
show_plot(A_real, B_generated, A_reconstructed)
```

清单 26.26：绘制生成图像的示例。

这是对两个模型的良好测试，不过，我们也可以执行相反的操作。具体来说，将域 B（斑马）的一张真实照片翻译到域 A（马），然后重建为域 B（斑马）。

```
...
# plot B->A->B
B_real = select_sample(B_data, 1)
A_generated = model_BtoA.predict(B_real)
B_reconstructed = model_AtoB.predict(A_generated)
show_plot(B_real, A_generated, B_reconstructed)
```

清单 26.27：使用另一个生成器模型生成和绘制图像的示例。

将所有这些整合在一起，完整示例如下所示。

```
# example of using saved cyclegan models for image translation
from keras.models import load_model
from numpy import load
from numpy import vstack
from matplotlib import pyplot
from numpy.random import randint
from keras_contrib.layers.normalization.instancenormalization import InstanceNormalization

# load and prepare training images
def load_real_samples(filename):
    # load the dataset
    data = load(filename)
    # unpack arrays
    X1, X2 = data['arr_0'], data['arr_1']
    # scale from [0,255] to [-1,1]
    X1 = (X1 - 127.5) / 127.5
    X2 = (X2 - 127.5) / 127.5
    return [X1, X2]

# select a random sample of images from the dataset
def select_sample(dataset, n_samples):
    # choose random instances
    ix = randint(0, dataset.shape[0], n_samples)
    # retrieve selected images
    X = dataset[ix]
    return X

# plot the image, the translation, and the reconstruction
def show_plot(imagesX, imagesY1, imagesY2):
    images = vstack((imagesX, imagesY1, imagesY2))
    titles = ['Real', 'Generated', 'Reconstructed']
    # scale from [-1,1] to [0,1]
    images = (images + 1) / 2.0
    # plot images row by row
    for i in range(len(images)):
        # define subplot
        pyplot.subplot(1, len(images), 1 + i)
        # turn off axis
        pyplot.axis('off')
        # plot raw pixel data
        pyplot.imshow(images[i])
        # title
        pyplot.title(titles[i])
    pyplot.show()

# load dataset
A_data, B_data = load_real_samples('horse2zebra_256.npz')
print('Loaded', A_data.shape, B_data.shape)
# load the models
cust = {'InstanceNormalization': InstanceNormalization}
model_AtoB = load_model('g_model_AtoB_089025.h5', cust)
model_BtoA = load_model('g_model_BtoA_089025.h5', cust)
# plot A->B->A
A_real = select_sample(A_data, 1)
B_generated = model_AtoB.predict(A_real)
A_reconstructed = model_BtoA.predict(B_generated)
show_plot(A_real, B_generated, A_reconstructed)
# plot B->A->B
B_real = select_sample(B_data, 1)
A_generated = model_BtoA.predict(B_real)
B_reconstructed = model_AtoB.predict(A_generated)
show_plot(B_real, A_generated, B_reconstructed)
```

清单 26.28：加载已保存生成器模型并执行图像翻译的示例。

运行示例首先选择一张随机的马照片，将其翻译，然后尝试重建原始照片。

![](img/443014fed0f53a293f6ece3b211c1603_590_0.png)

图 26.4：使用 CycleGAN 的真实马照片、翻译为斑马以及重建的马照片图表。

然后以相反的方式执行类似过程，选择一张随机的斑马照片，将其翻译为马，然后重建原始的斑马照片。
