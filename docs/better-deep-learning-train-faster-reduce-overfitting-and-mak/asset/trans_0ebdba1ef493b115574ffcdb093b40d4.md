
一条线图也被创建，用来展示模型在每个训练 epoch 上在训练集和测试集上的损失和准确率学习曲线。我们可以看到，在大部分运行过程中，训练准确率比我们也在最终得分中注意到的更为乐观。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_438_0.png)

图 21.2：训练集和测试集上模型准确率随每个训练 Epoch 变化的线图学习曲线。

现在我们已经确定该模型是开发集成模型的良好候选者，接下来我们可以着眼于开发一个简单的模型平均集成。

## 21.2.3 模型平均集成

在研究加权平均集成（在第 20 章中深入介绍）之前，我们可以先开发一个简单的模型平均集成。模型平均集成的结果可以用作比较点，因为我们期望一个配置良好的加权平均集成表现更好。首先，我们需要拟合多个模型以开发集成。我们将定义一个名为 `fit_model()` 的函数，在训练数据集上创建并拟合单个模型，我们可以重复调用它以创建任意数量的模型。

```python
# fit model on dataset
def fit_model(trainX, trainy):
    trainy_enc = to_categorical(trainy)
    # define model
    model = Sequential()
    model.add(Dense(25, input_dim=2, activation='relu'))
    model.add(Dense(3, activation='softmax'))
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    # fit model
    model.fit(trainX, trainy_enc, epochs=500, verbose=0)
    return model
```

Listing 21.10: 用于拟合并返回 MLP 模型的函数示例。

我们可以调用此函数来创建 10 个模型的池。

```python
# fit all models
n_members = 10
members = [fit_model(trainX, trainy) for _ in range(n_members)]
```

Listing 21.11: 创建拟合模型列表的示例。

接下来，我们可以开发模型平均集成。我们不知道这个问题合适的成员数量是多少，因此我们可以创建从 1 到 10 个成员的不同大小的集成，并在测试集上评估每个集成的性能。我们也可以在测试集上评估每个独立模型的性能。这为模型平均集成提供了一个有用的比较点，因为我们期望集成在平均情况下会优于随机选择的单个模型。

每个模型预测每个类别标签的概率，例如有三个输出。单个预测可以通过在预测概率上使用 argmax() 函数转换为类别标签，例如返回预测中概率值最大的索引。我们可以通过对每个类别预测的概率求和并对结果使用 argmax() 来集成多个模型的预测。下面 ensemble_predictions() 函数实现了这种行为。

```python
# make an ensemble prediction for multiclass classification
def ensemble_predictions(members, testX):
    # make predictions
    yhats = [model.predict(testX) for model in members]
    yhats = array(yhats)
    # sum across ensemble members
    summed = numpy.sum(yhats, axis=0)
    # argmax across classes
    result = argmax(summed, axis=1)
    return result
```

Listing 21.12: 用于进行集成预测的函数示例。

我们可以通过从所有模型的列表中选择所需数量的模型，调用 ensemble_predictions() 函数进行预测，然后通过将其与真实值进行比较来计算预测的准确率，来估计给定大小的集成的性能。下面 evaluate_n_members() 函数实现了这种行为。

```python
# evaluate a specific number of members in an ensemble
def evaluate_n_members(members, n_members, testX, testy):
    # select a subset of members
    subset = members[:n_members]
    # make prediction
    yhat = ensemble_predictions(subset, testX)
    # calculate accuracy
    return accuracy_score(testy, yhat)
```

Listing 21.13: 用于评估具有给定成员数量的集成的函数示例。

每个大小的集成的分数可以存储以便稍后绘制，并且收集每个单独模型的分数并报告平均性能。

```python
# evaluate different numbers of ensembles on hold out set
single_scores, ensemble_scores = list(), list()
for i in range(1, len(members)+1):
    # evaluate model with i members
    ensemble_score = evaluate_n_members(members, i, testX, testy)
    # evaluate the i'th model standalone
    testy_enc = to_categorical(testy)
    _, single_score = members[i-1].evaluate(testX, testy_enc, verbose=0)
    # summarize this step
    print('>%d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))
    ensemble_scores.append(ensemble_score)
    single_scores.append(single_score)
# summarize average accuracy of a single final model
print('Accuracy %.3f (+%.3f)' % (mean(single_scores), std(single_scores)))
```

Listing 21.14: 评估不同大小集成性能的示例。

最后，我们创建一个图表，显示每个单独模型的准确率（蓝色点）和模型平均集成随着成员数量从 1 增加到 10 时的性能（橙色线）。将所有这些联系起来，完整的示例列在下面。

```python
# model averaging ensemble for the blobs dataset
from sklearn.datasets.samples_generator import make_blobs
from sklearn.metrics import accuracy_score
from keras.utils import to_categorical
from keras.models import Sequential
from keras.layers import Dense
from matplotlib import pyplot
from numpy import mean
from numpy import std
import numpy
from numpy import array
from numpy import argmax

# fit model on dataset
def fit_model(trainX, trainy):
    trainy_enc = to_categorical(trainy)
    # define model
    model = Sequential()
    model.add(Dense(25, input_dim=2, activation='relu'))
    model.add(Dense(3, activation='softmax'))
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    # fit model
    model.fit(trainX, trainy_enc, epochs=500, verbose=0)
    return model

# make an ensemble prediction for multi-class classification
def ensemble_predictions(members, testX):
    # make predictions
    yhats = [model.predict(testX) for model in members]
    yhats = array(yhats)
    # sum across ensemble members
    summed = numpy.sum(yhats, axis=0)
    # argmax across classes
    result = argmax(summed, axis=1)
    return result

# evaluate a specific number of members in an ensemble
def evaluate_n_members(members, n_members, testX, testy):
    # select a subset of members
    subset = members[:n_members]
    # make prediction
    yhat = ensemble_predictions(subset, testX)
    # calculate accuracy
    return accuracy_score(testy, yhat)

# generate 2d classification dataset
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# fit all models
n_members = 10
members = [fit_model(trainX, trainy) for _ in range(n_members)]
# evaluate different numbers of ensembles on hold out set
single_scores, ensemble_scores = list(), list()
for i in range(1, len(members)+1):
    # evaluate model with i members
    ensemble_score = evaluate_n_members(members, i, testX, testy)
    # evaluate the i th model standalone
    testy_enc = to_categorical(testy)
    _, single_score = members[i-1].evaluate(testX, testy_enc, verbose=0)
    # summarize this step
    print('> %d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))
    ensemble_scores.append(ensemble_score)
    single_scores.append(single_score)
# summarize average accuracy of a single final model
print('Accuracy %.3f (%.3f)' % (mean(single_scores), std(single_scores)))
# plot score vs number of ensemble members
x_axis = [i for i in range(1, len(members)+1)]
pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')
pyplot.plot(x_axis, ensemble_scores, marker='o')
pyplot.show()
```

Listing 21.15: blobs 问题上模型平均集成的示例。

运行示例首先报告每个单个模型的性能以及具有 1、2、3 等成员的给定大小的模型平均集成的性能。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。考虑多次运行示例并比较平均性能。

本次运行中，单个模型的平均性能报告约为 80.4%，并且
