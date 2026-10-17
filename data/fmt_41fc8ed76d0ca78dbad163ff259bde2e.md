
图 6.3 显示了预测的前几类：

Top 5 classes:

图 6.7 显示了最小权重至少为 0.1 的超像素（superpixels）：

![](img/c06290096a327475ed918ba4a4328b77_149_0.png)

图 6.7 - 权重大于定义最小值的超像素

深度学习模型在提取图像低级特征（如角、边缘和条纹）方面表现出色。然而，这些低级特征对人类来说不可解释。来自 `lime_image` 的 `LIMEImageExplainer` 方法通过突出对模型预测产生正向或负向贡献的感兴趣区域（ROIs）或超像素，为图像分类器提供高层级解释。因此，LIME 可以评估所提供的解释是否具有敏感性，并防止模型由于错误的原因做出准确预测。

在本节中，我们使用 Inception V3 训练模型构建了一个图像分类器，并使用 LIME 解释了输出。接下来，让我们讨论在使用内在性（intrinsic）与事后性（post hoc）解释性时的最佳实践。

### 考虑内在性与事后解释性

我们能忽略解释性而仅仅信任最先进的模型吗？简单的回答是否定的。正确的预测并不能充分解决现实世界的问题。除非 AI 系统是可信赖的，否则用户不会采用它。了解预测为何重要，可以展示 AI 系统在多大程度上值得信任，并结合领域专业知识提供最佳行动方案的见解。

在选择内在解释性还是事后解释性时，没有硬性规定。从解释性的角度来看，具有足够准确性的内在模型始终比复杂模型更优。否则，后处理方法是可以在模型训练后提供事后解释性的替代方案。

不可避免的是，人类会根据位置、领域知识和个人经验带有无偏的偏见来信任解释选择。通常情况下，人类寻求对比性和交互性的解释，因为它们更容易理解。因此，在生成解释时可能会丢失部分信息。因此，忠实于模型且审慎的解释至关重要，它们通过关注重要方面而非每个细节来增加用户的信任。

### 总结

随着机器学习成为主流，解释性将是不可或缺的。可解释机器学习（interpretable ML）有助于验证模型、防止因错误原因产生正确预测，并增加用户信任，从而实现更广泛的应用。例如，我们不希望信贷申请根据性别而非还款记录状况来拒绝不合格的申请者。

可解释机器学习通过帮助人类理解模型的决策过程来发现新的见解。今天，用户除了基于统计关系的概率外，还要求关于因果关系的信息。尽管设计标准缺乏共识，但可解释机器学习技术在基准测试方法面临挑战。在下一章中，我们将探索反传播 XAI 技术。

## 反传播与扰动解释性

研究人员发现，大脑可以在 13 毫秒内处理并解释眼睛看到的图像。人类视觉过程始于光线到达视网膜，视网膜将光转换为神经信号，将形状、颜色和方向等信息发送到大脑。根据过去的经验，人脑提取影响视觉感知的特征。

图 7.1 显示了计算机如何在 0 到 255 之间的像素值网格中查看图像，而对形状和颜色没有内在知识。深度神经网络（如卷积神经网络 CNN）类似于人类大脑，包含非线性结构和人工神经元层，用于从输入图像中学习特征。

![](img/c06290096a327475ed918ba4a4328b77_151_0.png)

图 7.1 – 人类视觉感知与计算机视觉

尽管近年来取得了令人鼓舞的结果，但这些最先进的模型由于其透明特性带来的不确定性，尚未获得广泛采用。可解释神经网络提供了一种机制，用于可视化网络如何学习，并解释训练输入与预测之间的关系。

## 反传播与扰动解释性

有许多可解释人工智能（XAI）技术可以研究神经网络的内部工作。在第 6 章中，我们回顾了全局和局部解释性的范围，以及它们如何应用于内在和事后解释模型。本章涵盖了两种流行的 XAI 方法：反传播和扰动。本章主要主题包括：

- 回顾反传播解释性
- 回顾扰动解释性
- 比较反传播与扰动

在本章结束，你将学习更多关于反传播和扰动的方法，以便为你的用例选择合适的方法。

### 回顾反传播解释性

特征归因方法通常包含两个步骤：通过前向传播确定推理结果，然后通过反传播为已训练模型上的输入特征分配相关性评分。

反传播是一种基于梯度的 XAI 方法，它通过在神经网络中进行多次前向和反向传播生成输出的偏导数来评估特征归因。与神经网络训练不同，特征归因背景下的反传播不需要计算模型参数权重更新的梯度。反传播特征归因不是从输入层开始，而是从最终输出层开始分配重要性评分，然后反向跨每个中间层计算局部激活梯度，直到到达输入层，如图 7.2 所示：

![](img/c06290096a327475ed918ba4a4328b77_152_0.png)

本节介绍了显著性图（saliency maps），这是一种基于反传播的 XAI 技术。

### 显著性图

显著性图是使用 CNN 解释图像时最常用的 XAI 方法之一。它适用于大多数深度学习网络，并提供了一种直观的方法来调查 CNN 内部隐藏层。

显著性图利用反传播探测已训练的神经网络，获取关于特定类别的空间信息——识别物体的位置，而无需显式地为图像标记此类信息。显著性图放大梯度的权重，以反映或近似图像的相关部分。显著性图只需要一次反向传播，因为它关注得分最高的类别。

获取显著性图有三种方法：

- 使用反卷积网络（DeconvNet），通过反池化和逆 ReLU 技术反转特定的激活输入层
- 使用基于梯度的反传播，根据对输入网络的计算梯度高亮像素
- 使用引导反传播结合 DeconvNet 和基于梯度的反传播

让我们看看基于梯度的反传播方法的显著性图。示例笔记本 `chapter7_saliency_maps.ipynb` 以及本章讨论的包依赖项可见于 https://github.com/PacktPublishing/Deep-Learning-and-XAI-Techniques-for-Anomaly-Detection/tree/main/Chapter7。

你可以在 Amazon SageMaker Studio Lab（https://aws.amazon.com/sagemaker/studio-lab/）上进行实验，这是一个免费的 ML 开发环境，为每个用户提供 12 小时 CPU 或 4 小时 GPU 以及 15 GB 存储。或者你也可以在你喜欢的集成开发环境（IDE）中尝试。或者，你可以尝试你偏好的 IDE：

1. 首先，让我们加载必要的库：

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
from platform import python_version
import os
import warnings
warnings.filterwarnings("ignore")
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "3"
```

### 138 反向传播与扰动可解释性

```python
print(f'TensorFlow version: {tf.__version__}')
print(f'Python version: {python_version()}')
%matplotlib inline
```

2. 加载一个在 ImageNet 上预训练权重的 VGG16 分类模型：

```python
model = tf.keras.applications.VGG16(weights='imagenet')
model.summary()
```

7.3 显示了 VGG16 模型架构的摘要：

| 层 (类型) | 输出形状 | 参数 |
|---|---|---|
| input_1 (InputLayer) | (None, 224, 224, 3) | 0 |
| block1_conv1 (Conv2D) | (None, 224, 224, 64) | 1792 |
| block1_conv2 (Conv2D) | (None, 224, 224, 64) | 36928 |
| block1_pool1 (MaxPooling2D) | (None, 112, 112, 64) | 0 |
| block2_conv1 (Conv2D) | (None, 112, 112, 128) | 73856 |
| block2_conv2 (Conv2D) | (None, 112, 112, 128) | 147584 |
| block2_pool1 (MaxPooling2D) | (None, 56, 56, 128) | 0 |
| block3_conv1 (Conv2D) | (None, 56, 56, 256) | 295168 |
| block3_conv2 (Conv2D) | (None, 56, 56, 256) | 590000 |
| block3_pool1 (MaxPooling2D) | (None, 28, 28, 256) | 0 |
| block4_conv1 (Conv2D) | (None, 28, 28, 512) | 1180160 |
| block4_conv2 (Conv2D) | (None, 28, 28, 512) | 2359008 |
| block4_conv3 (Conv2D) | (None, 28, 28, 512) | 2359008 |
| block4_pool1 (MaxPooling2D) | (None, 14, 14, 512) | 0 |
| block5_conv1 (Conv2D) | (None, 14, 14, 512) | 2359008 |
| block5_conv2 (Conv2D) | (None, 14, 14, 512) | 2359008 |
| block5_conv3 (Conv2D) | (None, 14, 14, 512) | 2359008 |
| block5_pool1 (MaxPooling2D) | (None, 7, 7, 512) | 0 |
| flatten (Flatten) | (None, 25088) | 0 |
| fc1 (Dense) | (None, 4096) | 10276454 |
| fc2 (Dense) | (None, 4096) | 16781312 |
| predictions (Dense) | (None, 1000) | 4097000 |

总参数: 138,357,544
可训练参数: 138,357,544
不可训练参数: 0

图 7.3 – VGG16 模型摘要

3. 加载图像文件并为 VGG16 设置期望的目标输入大小：

```python
img_path = 'panda.jpeg'
image = tf.keras.utils.load_img(img_path, target_size=(224, 224))
plt.imshow(image)
plt.axis('off')
plt.show()
```

图 7.4 显示了原始图像：img/c06290096a327475ed91ba4a432b77_155.png

图 7.4 – 原始图像

4. 在获取前几类的预测之前对图像进行预处理：

```python
img = tf.keras.utils.img_to_array(image)
img = img.reshape((1, *img.shape))
y_pred = model.predict(img)
top5 = tf.keras.applications.vgg16.decode_predictions(y_pred, top=5)
print('Top 5 classes:')
top5
```

### 反向传播与扰动可解释性

图 7.5 显示了预测概率最高的大熊猫的排五个预测类别：

```
1/1 [====================] - 1s40ms/step
Top 5 classes:
('n0251045', 'giant_panda', 0.955901),
('n0250981', 'less_panda', 0.0398475),
('n0248336', 'gibbon', 0.0192165),
('n2443114', 'polecat', 0.0085649),
('n2488702', 'collar', 0.0003928)]
```

图 7.5 - 前五个预测类别

5. 通过寻找梯度的绝对值和最大值来识别此类预测感兴趣区域 (ROI)。我们归一化梯度：

```python
images = tf.Variable(img, dtype=float)
with tf.GradientTape() as tape:
    pred = model(images, training=False)
    sorted_class = np.argsort(pred.numpy()[0])[::-1]
    loss = pred[sorted_class[0]]
    grads = tape.gradient(loss, images)
    grads_abs = tf.math.abs(grads)[0]
    gmin, gmax = np.min(grads_abs), np.max(grads_abs)
    grads_eval = (grads_abs - gmin) / (gmax - gmin + 1e-8)
```

6. 图 7.6 显示了该输入的热力图，其中熊猫的眼睛和鼻子对大熊猫类别的得分贡献。颜色条突出了亮度的范围：

```python
fig, axes = plt.subplots(1,2, figsize=(20,7))
axes[0].imshow(image)
fig.colorbar(axes[1].imshow(grads_eval, cmap="turbo", alpha=0.9))
plt.savefig('panda_saliency_maps.png')
```

img/c06290096a327475ed91ba4a432b77_157.png
img/c06290096a327475ed91ba4a432b77_1.png

图 7.6 – 热力图

前面的示例显示了如何使用基于梯的反向传播提取贡献像素。现在，在下一节中探索扰动可解释性。

### 扰动可解释性

扰动方法通过扰动训练输入（通过遮图像像素或替换文本数据中的单词）来研究神经网络的属性。领域专家和用户可以通过直觉分析热力图中突出特征来评估其对整体模型预测的影响。本节探索使用局部模型无关解释 (LIME) 的基于扰动的可解释性。

### LIME

我们在第 6 章中讨论了 LIME 作为局部近似框架。在本节中，我们将探索 LIME 如何通过扰动提供局部可解释性。LIME 将解释定义为人类可理解的数值、视觉或文本表示。有三种 LIME 解释器：

- **LimeTabularExplainer**：基于表格数据的分类器预测。
- **LimeImageExplainer**：基于超像素的存在或具有共同特征像素分组的图像分类器预测。
- **LimeTextExplainer**：基于单词的存在或解释文本分类器预测。LIME 扰动给定的句子“The cake is delicious”，生成如“The cake delicious”、“The is delicious”或“cake is delicious”等变体，并识别相关单词“delicious”。

让我们看看 LIME 如何使用 Amazon 评论数据集（https://www.kaggle.com/datasets/arhamrumi/amazon-product-reviews）为文本分类器提供局部解释性。示例 Jupyter 笔记本（`chapter7_lime.ipynb`）和文件依赖项可以在 https://github.com/PacktPublishing/Deep-Learning-and-XAI-Techniques-for-Anomaly-Detection/main/ 获取。或者，你可以在喜欢的 IDE 中尝试：

1. 首先，安装并加载库：

```python
pip install nltk wordcloud
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf
from tensorflow import keras
import os
import warnings
warnings.filterwarnings("ignore")
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "3"
```

2. 接下来，加载并预览数据集，如图 7.7 所示：

```python
df = pd.read_csv('reviews.csv')
df.head()
```
