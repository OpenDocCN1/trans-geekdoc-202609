

# 4.1 卷积神经网络

# 卷积神经网络

## 参考文献：

我使用的一些图片和内容来自这两篇优秀的博客文章 \[1\] https://adeshpande3.github.io/adeshpande3.github.io/ 和 \[2》这本精彩的书籍，["Neural Networks and Deep Learning"](http://neuralnetworksanddeeplearning.com/) 由 Michael Nielsen 编写。（**强烈推荐**）

卷积神经网络（`CNN`，或 `ConvNet`）是一种 **前馈** 人工神经网络，其神经元之间的连接模式受动物视觉皮层组织的启发。

这些网络由多层小的神经元集合组成，它们处理输入图像的部分，称为 **感受野**。

然后将这些集合的输出铺开，使它们的输入区域重叠，以获得原始图像的 *更好表示*；这对每一层都重复进行。

## 它长什么样？

![](convnets_cover.png)

> source: [https://flickrcode.files.wordpress.com/2014/10/conv-net2.png](https://flickrcode.files.wordpress.com/2014/10/conv-net2.png)

# 问题空间

## 图像分类

图像分类是获取输入图像并输出一个类别（猫、狗等）或最能描述该图像的类别概率的任务。

对于人类来说，这种识别任务是我们从出生起就学习的第一项技能之一，并且作为成年人，它是自然而然、毫不费力的。

这些能够快速识别模式、*基于先前知识进行泛化* 以及适应不同图像环境的技能，是我们与机器不共有的。

## 输入和输出

![](cnn1.png)

source: http://www.pawbuzz.com/wp-content/uploads/sites/551/2014/11/corgi-puppies-21.jpg

当计算机看到一张图像（将图像作为输入）时，它会看到一个像素值数组。

根据图像的分辨率和大小，它会看到一个 `32 x 32 x 3` 的数字数组（`3` 指的是 `RGB` 值）。

假设我们有一个 `JPG` 格式的彩色图像，其大小为 `480 x 480`。代表性数组将是 `480 x 480 x 3`。这些数字中的每一个都被赋予 `0` 到 `255` 之间的值，描述该点的像素强度。

## 目标

我们希望计算机能够区分它所给出的所有图像，并找出使狗成为狗或使猫成为猫的独特特征。

当我们看一张狗的照片时，如果照片中有可识别的特征，例如爪子或 `4` 条腿，我们可以将其分类为狗。

同样，计算机应该能够通过寻找 *低级* 特征（如边缘和曲线），然后通过一系列 **卷积层** 构建更抽象的概念来执行图像分类。

## CNN 的结构

> 对 CNN 所做工作的更详细概述是：你获取图像，将其通过一系列卷积层、非线性层、池化层（下采样）和全连接层传递，并得到输出。如前所述，输出可以是单个类别或最能描述图像的类别概率。

source: \[1\]

# 卷积层

`CNN` 中的第一层始终是 **卷积层**。

![](2301343e.gif)

**Reference**: [http://deeplearning.net/software/theano/tutorial/conv\_arithmetic.html](http://deeplearning.net/software/theano/tutorial/conv_arithmetic.html)

### 卷积滤波器

卷积滤波器很像图像识别中的 **核**，是一个用于模糊、锐化、浮雕、边缘检测等的小矩阵。

这是通过核与图像之间的卷积来实现的。

#### 这里的主要区别在于，卷积矩阵是 **学习** 得到的。

当滤波器在输入图像周围滑动，或 **卷积** 时，它将滤波器中的值与图像的原始像素值相乘

（a.k.a. 计算 **逐元素乘法**）。

![](cnn2.png)

现在，我们对输入体积上的每个位置重复此过程。（下一步是将滤波器向右移动 `1` 个单位，然后再向右移动 `1` 个单位，依此类推）。

在将滤波器滑过所有位置后，我们得到一个通常称为 **激活图** 或 **特征图** 的数字数组。

## 高层视角

让我们简要谈谈这个卷积实际上从高层次在做什么。

每个滤波器都可以被视为 **特征标识符**（例如，*直线边缘、简单颜色、曲线*）

![](cnn3.png)

### 感受野的可视化

![](cnn4.png)

![](cnn5.png)

![](cnn6.png)

该值要低得多！这是因为图像部分中没有任何东西响应曲线检测器滤波器。请记住，此卷积层的输出是一个激活图。

# 深入网络

现在，在传统的 **卷积神经网络** 架构中，还有其他层穿插在这些卷积层之间。

![](fedad2b.png)

## ReLU（整流线性单元）层

每个卷积层之后，通常会立即应用一个 *非线性层*（或 **激活层**）。

此层的目的是为一个基本上在卷积层期间一直在执行线性操作（仅逐元素乘法和求和）的系统引入非线性。

## 使用 Bokeh（交互式图表）

```
from bokeh.plotting import figure, output_notebook, show

output_notebook()
```

```
<div class="bk-root">
    <a href="http://bokeh.pydata.org" target="_blank" class="bk-logo bk-logo-small bk-logo-notebook"></a>
    <span id="0af86eff-6a55-4644-ab84-9a6f5fcbeb3e">Loading BokehJS ...</span>
</div>
```

```
p = figure(plot_width=600, plot_height=600)

colors = [x for x in 'blue-green-red-cyan-magenta-yellow-black-purple-coral-lime'.split('-')]
colors_map = colors_map[:1000]
for cl in range(nb_classes):
    indices = np.where(colors_map==cl)
    p.circle(X_tsne[indices, 0].ravel(), X_tsne[indices, 1].ravel(), size=7, 
             color=colors[cl], alpha=0.4, legend=str(cl))

# show the results
p.legend.location = 'bottom_right'
show(p)
```

```
<div class="bk-root">
    <div class="bk-plotdiv" id="e90df1a2-e577-49fb-89bb-6e083232c9ec"></div>
</div>
```

#### 注：我们使用了 `default` TSNE 参数。通过调整 TSNE 超参数可以获得更好的结果

## 练习 1：

### 尝试使用不同的算法创建流形

```
from sklearn.manifold import MDS
```

```
## Your code here
```

## 练习 2：

### 尝试提取模型第一层和最后一层的隐藏特征

```
## Your code here
```

```
## Try using the `get_activations` function relying on keras backend
def get_activations(model, layer, X_batch):
    activations_f = K.function([model.layers[0].input, K.learning_phase()], [layer.output,])
    activations = activations_f((X_batch, False))
    return activations
```

