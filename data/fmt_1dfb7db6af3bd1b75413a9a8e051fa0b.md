
```python
ensemble_visible = [model.input for model in members]

# concatenate merge output from each model

ensemble_outputs = [model.output for model in members]

merge = concatenate(ensemble_outputs)

hidden = Dense(10, activation='relu')(merge)

output = Dense(3, activation='softmax')(hidden)

model = Model(inputs=ensemble_visible, outputs=output)

# plot graph of ensemble

plot_model(model, show_shapes=True, to_file='model_graph.png')

# compile

model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])

return model
```

# fit a stacked model

```python
def fit_stacked_model(model, inputX, inputy):

    # prepare input data

    X = [inputX for _ in range(len(model.input))]

    # encode output data

    inputy_enc = to_categorical(inputy)

    # fit model

    model.fit(X, inputy_enc, epochs=300, verbose=0)
```

# make a prediction with a stacked model

```python
def predict_stacked_model(model, inputX):

    # prepare input data

    X = [inputX for _ in range(len(model.input))]

    # make prediction

    return model.predict(X, verbose=0)
```

# generate 2d classification dataset

```python
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)

# split into train and test

n_train = 100

trainX, testX = X[:n_train, :], X[n_train:, :]

trainy, testy = y[:n_train], y[n_train:]

# load all models

n_members = 5

members = load_all_models(n_members)

print('Loaded %d models' % len(members))

# define ensemble model

stacked_model = define_stacked_model(members)

# fit stacked model on test dataset

fit_stacked_model(stacked_model, testX, testy)

# make predictions and evaluate

yhat = predict_stacked_model(stacked_model, testX)

yhat = argmax(yhat, axis=1)

acc = accuracy_score(testy, yhat)

print('Stacked Test Accuracy: %.3f' % acc)
```

Listing 25.33: 拟合 MLP 堆叠模型的示例。

运行示例首先加载五个子模型。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。

考虑多次运行示例并比较平均性能。

定义了一个更大的堆叠集成神经网络并在测试数据集上进行拟合，然后使用新模型对测试数据集进行预测。我们可以看到，在这种情况下，模型的准确率约为 83.3%，优于上一节中的线性模型。

```
>loaded models/model_1.h5
>loaded models/model_2.h5
>loaded models/model_3.h5
>loaded models/model_4.h5
>loaded models/model_5.h5
Loaded 5 models
Stacked Test Accuracy: 0.833
```

Listing 25.34: 评估堆叠 MLP 模型的示例输出。

## 25.3 扩展

本节列出了一些您可以探索的扩展教程的想法。

- **替代元学习器。** 更新示例以使用除逻辑回归模型之外的替代元学习器分类模型。
- **单一 Level 0 模型。** 更新示例以使用单个 level-0 模型并比较结果。
- **变化 Level 0 模型。** 开发一项研究，展示测试分类准确率与堆叠集成中使用的子模型数量之间的关系。
- **交叉验证堆叠集成。** 更新示例以使用 *k*-折交叉验证为元学习器模型准备训练数据集。
- **在元学习器中使用原始输入。** 更新示例，使元学习器算法不仅采用子模型的输出，还采用样本的原始输入数据并比较性能。

如果您探索其中任何一个扩展，我很乐意知道。

## 25.4 进一步阅读

如果您想深入了解，本节提供了有关该主题的更多资源。

### 25.4.1 书籍

- 第 8.8 节 模型平均与堆叠，*统计学习要素：数据挖掘、推断与预测*，第二版，2016 年。
- [https://amzn.to/2DYeHA0](https://amzn.to/2DYeHA0)

## 25.4 进一步阅读

- 第 7.5 节 组合多个模型，Data Mining: Practical Machine Learning Tools and Techniques，第二版，2005 年。
https://amzn.to/2pBxIPN

- 第 9.8.2 节 堆叠泛化，Neural Networks for Pattern Recognition，1995 年。
https://amzn.to/2pQAOR

### 25.4.2 论文

- Stacked generalization，1992 年。
https://www.sciencedirect.com/science/article/pii/S08936080005800231

- Issues in Stacked Generalization，1999 年。
https://www.jair.org/index.php/jair/article/view/10228

### 25.4.3 API

- 使用 Keras Sequential 模型入门。
https://keras.io/getting-started/sequential-model-guide/

- Keras Core Layers API。
https://keras.io/layers/core/

- numpy.argmax API。
https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmax.html

- sklearn.datasets.make_blobs API。
http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html

- numpy.dstack API。
https://docs.scipy.org/doc/numpy/reference/generated/numpy.dstack.html

- sklearn.linear_model.LogisticRegression API。
http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html

### 25.4.4 文章

- Stacked Generalization (Stacking) Bibliography。
http://machine-learning.martinsewell.com/ensembles/stacking/

- Ensemble learning，Wikipedia。
https://en.wikipedia.org/wiki/Ensemble_learning

## 25.5 总结

在本教程中，您了解了如何为深度学习神经网络开发堆叠泛化集成。具体来说，您学习了：

- 堆叠泛化是一种集成方法，其中新模型学习如何最好地组合多个现有模型的预测结果。
- 如何使用神经网络作为子模型和 scikit-learn 分类器作为元学习器来开发堆叠模型。
- 如何开发一种堆叠模型，其中神经网络子模型嵌入到更大的堆叠集成模型中用于训练和预测。

在下一教程中，您将了解如何组合多个集成成员的模型参数或权重，而不是它们的预测结果。

## 第26章

## 使用平均模型权重集成组合模型参数

神经网络的训练过程是一个具有挑战性的优化过程，往往无法收敛。这意味着训练结束时的模型可能不是用作最终模型时稳定或性能最佳的一组权重。解决此问题的一种方法是使用训练运行结束时看到的多个模型的权重的平均值。这称为 Polyak-Ruppert 平均，可以通过使用模型权重的线性或指数递减加权平均来进一步改进。除了得到更稳定的模型外，平均模型权重的性能也可能带来更好的性能。在本教程中，您将了解如何将来自多个不同模型的权重组合成单个模型以进行预测。完成本教程后，您将了解：

- 训练神经网络的随机性和挑战性意味着优化过程可能不收敛。
- 使用训练运行结束时观察到的模型的权重平均值创建模型可能会导致更稳定且有时性能更好的解决方案。
- 如何使用来自多个保存模型的模型参数的等权重、线性加权和指数加权平均值创建最终模型。

开始吧。

### 26.1 平均模型权重集成

为深度神经网络模型学习权重需要解决高维非凸优化问题。解决此优化问题的挑战在于存在许多良好的解决方案，学习算法可能会在周围弹跳而无法稳定在一个解决方案上。在随机优化领域，这被称为优化算法在解上收敛的问题，其中解由一组特定的权重值定义。

如果您的模型存在收敛问题，您可能会看到的症状是训练和/或测试损失值显示出高于预期的方差，例如在训练周期中上下波动。解决此问题的一种方法是组合训练过程结束时收集的权重。通常，这可能被称为时间平均法，被称为 Polyak 平均或 Polyak-Ruppert 平均，以该方法的原始开发者命名。

> Polyak 平均法是将优化算法在参数空间中遍历的轨迹中的几个点进行平均。
> 
> — 第322页，*深度学习*，2016年。

对学习过程中多个有噪声的权重集合进行平均乍听之下似乎不如自行调整优化过程那么理想，但对于可能需要数天、数周甚至数月才能训练的非常大的神经网络来说，可能是一种理想的解决方案。

> 基本的进步是基于一个悖论性的想法实现的：收敛速度低于最佳的慢算法必须进行平均。
> 
> — *通过平均加速随机逼近*，1992年。

从单次训练运行中对多个模型的权重进行平均可以平滑掉噪声优化过程，该过程可能因学习超参数（如学习率）的选择或正在学习映射函数的形状而产生噪声。结果是最终模型或一组权重可能提供更稳定、也许更准确的结果。

> 基本思想是优化算法可能会在山谷两侧来回跳跃多次，而从未访问过接近山谷底部的位置。不过，所有位置的平均值应该接近山谷底部。
> 
> — 第322页，*深度学习*，2016年。

Polyak-Ruppert 平均的最简单实现涉及计算最近几个训练周期中模型权重的平均值。这可以通过计算加权平均值来改进，其中对较新的模型赋予更大权重，该权重在之前的周期中线性递减。一种替代且更广泛使用的方法是在加权平均中使用指数衰减。

> 已证明 Polyak-Ruppert 平均可以改善标准 SGD [...] 的收敛性。或者，可以使用参数的指数移动平均，给较新的参数值更高权重。
> 
> — *Adam：一种随机优化方法*，2014年。

在最终模型中使用模型权重的平均值或加权平均值是实践中确保从训练运行中获得最佳结果的常见技术。该方法是在 Google Inception V2 和 V3 深度卷积神经网络模型中用于照片分类的众多 *tricks* 之一，这是深度学习领域的里程碑。

> 模型评估是使用随时间计算的参数运行平均值来执行的。
> 
> — *重新思考计算机视觉中的 Inception 架构*，2015年。

### 26.2 平均模型权重集成案例研究

在本节中，我们将演示如何使用平均模型权重集成来降低 MLP 在简单多类分类问题上的方差。此示例为将平均模型权重集成应用于您自己的神经网络以解决分类和回归问题提供了模板。

### 26.2.1 多类分类问题

我们将使用一个小型多类分类问题作为基础来演示模型权重集成。scikit-learn 类提供了 `make_blobs()` 函数，可用于创建具有规定样本数、输入变量、类别数以及类内样本方差的多类分类问题。该问题可以配置为有两个输入变量（表示点的 x 和 y 坐标），并且每个组内点的标准差为 2.0。我们将使用相同的随机状态（伪随机数生成器的种子），以确保我们始终获得相同的数据点。

```python
# generate 2d classification dataset

X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)
```

清单 26.1：创建 blobs 问题样本的示例。

结果是我们可建模的数据集的输入和输出元素。为了感受问题的复杂性，我们可以将每个点绘制在二维散点图上，并按类别值对每个点着色。完整示例如下所示。

```python
# scatter plot of blobs dataset

from sklearn.datasets.samples_generator import make_blobs

from matplotlib import pyplot

from numpy import where

# generate 2d classification dataset

X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2, random_state=2)

# scatter plot for each class value

for class_value in range(3):

    # select indices of points with the class label

    row_ix = where(y == class_value)

    # scatter plot for points with a different color

    pyplot.scatter(X[row_ix, 0], X[row_ix, 1])

# show plot

pyplot.show()
```

清单 26.2：绘制 blobs 问题样本的示例。

运行示例会创建整个数据集的散点图。我们可以看到，标准差为 2.0 意味着类别不是线性可分的（可由直线分隔），导致许多模糊点。这是理想的，因为这意味着问题是非平凡的，并且会允许神经网络模型找到许多不同的足够好的候选解决方案，从而导致高方差。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_540_0.png)

图 26.1：具有三个类别且按类别值着色的点的 Blobs 数据集散点图。

### 26.2.2 多层感知机模型

在定义模型之前，我们需要设计一个适合集成的问题。在我们的问题中，训练数据集相对较小。具体来说，训练数据集中示例与保留数据集的比例为 10:1。这模拟了我们可能拥有大量未标记示例和少量用于训练模型的标记示例的情况。我们将从 blobs 问题中创建 1,100 个数据点。模型将在前 100 个点上进行训练，其余 1,000 个点将被保留在测试数据集中，模型无法使用。

该问题是多类分类问题，我们将使用输出层的 softmax 激活函数对其进行建模。这意味着模型将预测一个具有三个元素的向量，表示样本属于三个类别中每个类别的概率。因此，我们必须在将行拆分为训练和测试数据集之前对类别值进行独热编码。我们可以使用 Keras 的 `to_categorical()` 函数来完成此操作。

```python
# generate 2d classification dataset

X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)

# one hot encode output variable

y = to_categorical(y)

# split into train and test
```

将所有内容整合起来，完整的示例列在下面。

```python
# develop an mlp for blobs dataset

from sklearn.datasets.samples_generator import make_blobs

from keras.utils import to_categorical

from keras.models import Sequential

from keras.layers import Dense

from keras.optimizers import SGD

from matplotlib import pyplot
```
