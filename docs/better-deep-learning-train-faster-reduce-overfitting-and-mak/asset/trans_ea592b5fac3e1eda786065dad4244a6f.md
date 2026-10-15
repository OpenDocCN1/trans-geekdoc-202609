
训练100个epoch的模型将能完美学会该问题。因此，我们将在每一层使用10个节点，以确保模型仅用一层就拥有足够的能力来学习该问题。更新后的函数如下所示，它以层数和数据集作为参数，并返回模型的训练历史和测试准确率。

```
# fit model with given number of layers, returns test set accuracy
def evaluate_model(n_layers, trainX, trainy, testX, testy):
    # configure the model based on the data
    n_input, n_classes = trainX.shape[1], testy.shape[1]
    # define model
    model = Sequential()
    model.add(Dense(10, input_dim=n_input, activation='relu',
                kernel_initializer='he_uniform'))
    for _ in range(1, n_layers):
        model.add(Dense(10, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(n_classes, activation='softmax'))
    # compile model
    opt = SGD(lr=0.01, momentum=0.9)
    model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
    # fit model
    history = model.fit(trainX, trainy, epochs=100, verbose=0)
    # evaluate model on test set
    _, test_acc = model.evaluate(testX, testy, verbose=0)
    return history, test_acc
```

清单2.22：用于评估不同层数模型的函数示例。

鉴于单隐藏层模型已具备足够的能力来学习该问题，我们将探索逐渐增加层数，直到学习算法变得不稳定且无法再学习该问题为止。如果所选的建模问题更加复杂，我们可以探索增加层数，并检查模型性能的提升直至达到收益递减点。在此情况下，我们将评估1到5层的模型，预期在某个时刻，层数的增加会导致所选学习算法无法适应训练数据。

```
# evaluate model and plot learning curve of model with given number of layers
all_history = list()
num_layers = [1, 2, 3, 4, 5]
for n_layers in num_layers:
    # evaluate model with a given number of layers
    history, result = evaluate_model(n_layers, trainX, trainy, testX, testy)
    print('layers=%d: %.3f' % (n_layers, result))
    # plot learning curve
    pyplot.plot(history.history['loss'], label=str(n_layers))
pyplot.legend()
pyplot.show()
```

清单2.23：评估不同层数MLP的模型示例。

将这些元素整合在一起，完整示例代码如下所示。

```python
# study of mlp learning curves given different number of layers for multi-class
    classification
from sklearn.datasets.samples_generator import make_blobs
from keras.models import Sequential
from keras.layers import Dense
from keras.optimizers import SGD
from keras.utils import to_categorical
from matplotlib import pyplot

# prepare multi-class classification dataset
def create_dataset():
    # generate 2d classification dataset
    X, y = make_blobs(n_samples=1000, centers=20, n_features=100, cluster_std=2,
                      random_state=2)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX, testX = X[:n_train, :], X[n_train:, :]
    trainy, testy = y[:n_train], y[n_train:]
    return trainX, trainy, testX, testy

# fit model with given number of layers, returns test set accuracy
def evaluate_model(n_layers, trainX, trainy, testX, testy):
    # configure the model based on the data
    n_input, n_classes = trainX.shape[1], testy.shape[1]
    # define model
    model = Sequential()
    model.add(Dense(10, input_dim=n_input, activation='relu',
                    kernel_initializer='he_uniform'))
    for _ in range(1, n_layers):
        model.add(Dense(10, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(n_classes, activation='softmax'))
    # compile model
    opt = SGD(lr=0.01, momentum=0.9)
    model.compile(loss='categorical_crossentropy', optimizer=opt, metrics=['accuracy'])
    # fit model
    history = model.fit(trainX, trainy, epochs=100, verbose=0)
    # evaluate model on test set
    _, test_acc = model.evaluate(testX, testy, verbose=0)
    return history, test_acc

# get dataset
trainX, trainy, testX, testy = create_dataset()
# evaluate model and plot learning curve of model with given number of layers
all_history = list()
num_layers = [1, 2, 3, 4, 5]
for n_layers in num_layers:
    # evaluate model with a given number of layers
    history, result = evaluate_model(n_layers, trainX, trainy, testX, testy)
    print('layers=%d: %.3f' % (n_layers, result))
    # plot learning curve
    pyplot.plot(history.history['loss'], label=str(n_layers))
pyplot.legend()
pyplot.show()
```

清单2.24：在blobs问题上评估不同层数MLP模型的示例。

运行该示例，首先会输出每种模型配置的测试准确率。

注意：由于学习算法的随机性，您的具体结果可能会有所不同。建议多次运行示例并比较平均性能。

在这种情况下，我们可以看到模型最多能良好地学习该问题达三层，之后便开始表现不佳。我们可以看到，五层时性能显著下降，并且如果进一步增加层数，性能预计会继续下降。

```
layers=1: 1.000
layers=2: 1.000
layers=3: 1.000
layers=4: 0.948
layers=5: 0.794
```

清单2.25：在blobs问题上评估不同层数MLP模型的输出示例。

还绘制了一张线图，展示了每种模型配置（1到5层）在100个训练轮次中训练数据集上的交叉熵损失。我们可以看到，1层、2层和3层（蓝色、橙色和绿色）的模型动态非常相似，都能快速学习该问题。令人意外的是，4层和5层的训练损失起初表现良好，随后急剧上升，这表明模型很可能陷入了一组次优的权重，而不是对训练数据集过拟合。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_60_0.png)

图2.3：在blobs多分类问题上，改变模型层数时，MLP在训练数据集上的交叉熵损失随训练轮次变化的线图。

分析表明，通过增加深度来提升模型容量是一种非常有效的工具，但必须谨慎使用，因为它可能很快导致模型容量过大，从而难以轻松学习训练数据集。

## 2.4 扩展

本节列出了一些扩展本教程的想法，您可能希望尝试。

- **节点过多**。更新增加节点的实验，以找到学习算法无法再学习该问题的临界点。
- **重复评估**。更新实验，对每种配置进行重复评估，以应对学习算法的随机性。
- **更难的问题**。在一个需要增加深度所提供的容量才能表现良好的问题上，重复增加层数的实验。

如果你探索了其中任何扩展，我很想知道。

## 2.5 延伸阅读

如果你想深入了解，本节提供有关该主题的更多资源。

### 2.5.1 书籍

- *神经锻造：前馈人工神经网络中的监督学习*，1999年。
  https://amzn.to/2vhyW8j
- *深度学习*，2016年。
  https://amzn.to/2IXzUIY

### 2.5.2 API

- Keras核心层API。
  https://keras.io/layers/core/
- Keras卷积层API。
  https://keras.io/layers/convolutional/
- Keras循环层API。
  https://keras.io/layers/recurrent/
- Keras实用函数API。
  https://keras.io/utils/
- sklearn.datasets.make_blobs API。
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html

