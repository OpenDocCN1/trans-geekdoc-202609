
列表 11.18: 为问题 2 准备数据集的示例。

为完整起见，包含此更改的完整示例列在下面。

```python
# fit mlp model on problem 2 and save model to file
from sklearn.datasets.samples_generator import make_blobs
from keras.models import Sequential
from keras.layers import Dense
from keras.utils import to_categorical
from matplotlib import pyplot

# prepare a blobs examples with a given random seed
def samples_for_seed(seed):
    # generate samples
    X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2,
        random_state=seed)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX, testX = X[:n_train, :], X[n_train:, :]
    trainy, testy = y[:n_train], y[n_train:]
    return trainX, trainy, testX, testy

# define and fit model on a training dataset
def fit_model(trainX, trainy, testX, testy):
    # define model
    model = Sequential()
    model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(3, activation='softmax'))
    # compile model
    model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
    # fit model
    history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
    return model, history

# summarize the performance of the fit model
def summarize_model(model, history, trainX, trainy, testX, testy):
    # evaluate the model
    _, train_acc = model.evaluate(trainX, trainy, verbose=0)
    _, test_acc = model.evaluate(testX, testy, verbose=0)
    print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
    # plot loss during training
    pyplot.subplot(211)
    pyplot.title('Loss')
    pyplot.plot(history.history['loss'], label='train')
    pyplot.plot(history.history['val_loss'], label='test')
    pyplot.legend()
    # plot accuracy during training
    pyplot.subplot(212)
    pyplot.title('Accuracy')
    pyplot.plot(history.history['acc'], label='train')
    pyplot.plot(history.history['val_acc'], label='test')
    pyplot.legend()
    pyplot.show()

# prepare data
trainX, trainy, testX, testy = samples_for_seed(2)
# fit model on train dataset
model, history = fit_model(trainX, trainy, testX, testy)
# evaluate model behavior
summarize_model(model, history, trainX, trainy, testX, testy)
```

列表 11.19: 在问题 2 上拟合和保存 MLP 模型的示例。

运行该示例会拟合并评估模型的性能，打印训练集和测试集上的分类准确率。

**注意:** 你的具体结果可能因学习算法的随机性而有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到模型在问题 2 上的表现尚可，但不如问题 1 上看到的那样好，在训练集和测试集上均实现了约 79% 的分类准确率。

```
Train: 0.794, Test: 0.794
```

列表 11.20: 在问题 2 上拟合 MLP 的示例输出。

还创建了一幅图来总结模型的学习曲线。在这种情况下，我们可以看到模型收敛的速度比上一节中问题 1 上看到的更慢。这表明该版本的问题可能更具挑战性，至少对于所选的模型配置而言。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_266_0.png)

图 11.3: 问题 2 上 MLP 在训练集和测试集上的损失和准确率学习曲线。

现在我们已经有了 MLP 在问题 2 上的性能和学习动态的基线，我们可以看到添加迁移学习如何影响该问题上的 MLP。

## 11.2.4 用于问题 2 的带迁移学习的 MLP

在问题 1 上拟合的模型可以被加载，其权重可作为在问题 2 上拟合的模型的初始权重。这是一种迁移学习，其中在不同但相关问题上的学习被用作一种权重初始化方案。这要求 `fit_model()` 函数被更新以加载模型并在问题 2 的示例上重新拟合它。保存在 `model.h5` 中的模型可以使用 `load_model()` Keras 函数加载。

```
# load model
model = load_model('model.h5')
```

列表 11.21: 加载已保存模型的示例。

加载后，模型可以像往常一样编译和拟合。包含此更改的更新后的 `fit_model()` 列在下面。

```
# load and re-fit model on a training dataset
def fit_model(trainX, trainy, testX, testy):
    # load model
```

```python
model = load_model('model.h5')
# compile model
model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
# re-fit model
history = model.fit(trainX, trainY, validation_data=(testX, testY), epochs=100, verbose=0)
return model, history
```

Listing 11.22: 用于加载和重新拟合模型的函数示例。

我们期望，使用在不同但相关的任务上训练得到的模型权重来学习该问题的模型，或许可以在学习曲线方面更快地学习，并且可能导致更低的泛化误差，尽管这些方面取决于问题的选择和模型。为了完整性，包含此更改的完整示例列于下方。

```python
# transfer learning with mlp model on problem 2
from sklearn.datasets.samples_generator import make_blobs
from keras.utils import to_categorical
from keras.models import load_model
from matplotlib import pyplot

# prepare a blobs examples with a given random seed
def samples_for_seed(seed):
    # generate samples
    X, y = make_blobs(n_samples=1000, centers=3, n_features=2, cluster_std=2,
        random_state=seed)
    # one hot encode output variable
    y = to_categorical(y)
    # split into train and test
    n_train = 500
    trainX, testX = X[:n_train, :], X[n_train:, :]
    trainY, testY = y[:n_train], y[n_train:]
    return trainX, trainY, testX, testY

# load and re-fit model on a training dataset
def fit_model(trainX, trainY, testX, testY):
    # load model
    model = load_model('model.h5')
    # compile model
    model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
    # re-fit model
    history = model.fit(trainX, trainY, validation_data=(testX, testY), epochs=100, verbose=0)
    return model, history

# summarize the performance of the fit model
def summarize_model(model, history, trainX, trainY, testX, testY):
    # evaluate the model
    _, train_acc = model.evaluate(trainX, trainY, verbose=0)
    _, test_acc = model.evaluate(testX, testY, verbose=0)
    print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
    # plot loss during training
    pyplot.subplot(211)
    pyplot.title('Loss')
    pyplot.plot(history.history['loss'], label='train')
    pyplot.plot(history.history['val_loss'], label='test')
    pyplot.legend()
    # plot accuracy during training
pyplot.subplot(212)
pyplot.title('Accuracy')
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.legend()
pyplot.show()

# prepare data
trainX, trainY, testX, testY = samples_for_seed(2)
# fit model on train dataset
model, history = fit_model(trainX, trainY, testX, testY)
# evaluate model behavior
summarize_model(model, history, trainX, trainY, testX, testY)
```

Listing 11.23: 问题 2 的迁移学习示例。

运行该示例会拟合并评估模型的性能，打印训练集和测试集上的分类准确率。

**Note:** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

在这种情况下，我们可以看到模型实现了更低的泛化误差，在问题 2 的测试数据集上达到了约 81% 的准确率，而独立模型约为 79% 的准确率。

```
Train: 0.786, Test: 0.810
```

Listing 11.24: 问题 2 迁移学习的示例输出。

还创建了一张图来总结模型的学习曲线。在这种情况下，我们可以看到模型的学习曲线似乎相似，尽管我们确实观察到测试集（橙色线）的学习曲线有明显改善，无论是在更早阶段（第 20 个 epoch 起）的更好性能，还是超过了模型在训练集上的性能。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_269_0.png)

Figure 11.4: 问题 2 上使用迁移学习的 MLP 在训练集和测试集上的损失和准确率学习曲线。

我们仅查看了独立 MLP 模型和带迁移学习的 MLP 的单次运行。神经网络算法具有随机性，因此需要对多次运行的性能进行平均，以判断观察到的行为是真实的还是统计上的偶然。

## 11.2.5 问题 2 上模型的比较

为了确定在 blobs 多分类问题中使用迁移学习是否具有实际效果，我们必须多次重复每个实验并分析重复试验的平均性能。我们将比较在问题 2 上训练的独立模型与使用迁移学习的模型的性能，平均基于 30 次重复。此外，我们将研究保持某些层的权重固定是否能提高模型性能。在问题 1 上训练的模型有两个隐藏层。通过固定第一层或第一层和第二层隐藏层，具有不可更改权重的层将充当特征提取器，并可能提供使学习问题 2 更容易的特征，从而影响学习速度和/或模型在测试集上的准确率。作为第一步，我们将简化 `fit_model()` 函数，使其拟合模型并丢弃任何训练历史，以便我们专注于训练后模型的最终准确率。

```python
# define and fit model on a training dataset
def fit_model(trainX, trainy):
    # define model
    model = Sequential()
    model.add(Dense(5, input_dim=2, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(5, activation='relu', kernel_initializer='he_uniform'))
    model.add(Dense(3, activation='softmax'))
    # compile model
    model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
    # fit model
    model.fit(trainX, trainy, epochs=100, verbose=0)
    return model
```

Listing 11.25: 用于拟合并返回模型的函数示例。

接下来，我们可以开发一个函数，该函数将在训练数据集上反复拟合新的独立模型于问题 2，并在测试集上评估准确率。下面的 `eval_standalone_model()` 函数实现了此功能，接受训练集和测试集作为参数，以及重复次数，并返回模型在测试数据集上的准确率分数列表。

```python
# repeated evaluation of a standalone model
def eval_standalone_model(trainX, trainy, testX, testy, n_repeats):
    scores = list()
    for _ in range(n_repeats):
        # define and fit a new model on the train dataset
        model = fit_model(trainX, trainy)
        # evaluate model on test dataset
        _, test_acc = model.evaluate(testX, testy, verbose=0)
        scores.append(test_acc)
    return scores
```

Listing 11.26: 用于模型重复评估的函数示例。

总结此函数返回的准确率分数的分布将给出所选独立模型在问题 2 上表现如何的初步了解。
