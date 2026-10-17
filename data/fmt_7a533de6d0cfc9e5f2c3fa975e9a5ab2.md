
### 进行集成预测的函数示例

`result = argmax(summed, axis=1)`

`return result`

Listing 23.17: 进行集成预测的函数示例。

接下来，我们需要一个函数来评估给定大小的集成成员子集。需要选择子集，进行预测，并通过将预测与预期值进行比较来估计集成的性能。下面的 `evaluate_n_members()` 函数实现了这种集成大小评估。

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

Listing 23.18: 评估给定大小集成的函数示例。

我们现在可以枚举从 1 到 50 的不同大小的水平投票集成。每个成员单独评估，然后评估该大小的集成并记录分数。

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
```

Listing 23.19: 评估不同给定大小集成的示例。

在评估结束时，我们报告单个模型在测试数据集上的分数分布。平均分数是我们如果选择任何已保存模型作为最终模型所期望的平均值。

```python
# summarize average accuracy of a single final model

print('Accuracy %.3f (%.3f)' % (mean(single_scores), std(single_scores)))
```

Listing 23.20: 汇总单个模型性能的示例。

最后，我们可以绘制分数。每个独立模型的分数以蓝色点绘制，并为每个连续模型集成创建线图（橙色）。

```python
# plot score vs number of ensemble members

x_axis = [i for i in range(1, len(members)+1)]

pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')

pyplot.plot(x_axis, ensemble_scores, marker='o')

pyplot.show()
```

Listing 23.21: 绘制单个模型和集成模型性能的示例。

我们的预期是，合理大小的集成将优于随机选择的模型，并且在选择集成大小时存在收益递减点。完整示例列在下面。

```python
# load models and make predictions using a horizontal voting ensemble

from sklearn.datasets.samples_generator import make_blobs

from sklearn.metrics import accuracy_score

from keras.utils import to_categorical

from keras.models import load_model

from matplotlib import pyplot

from numpy import mean

from numpy import std

from numpy import array

from numpy import argmax

import numpy

# load models from file

def load_all_models(n_start, n_end):

    all_models = list()

    for epoch in range(n_start, n_end):

        # define filename for this ensemble

        filename = 'models/model_' + str(epoch) + '.h5'

        # load model from file

        model = load_model(filename)

        # add to list of members

        all_models.append(model)

        print('>loaded %s' % filename)

    return all_models

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

# load models in order

members = load_all_models(950, 1000)

print('Loaded %d models' % (len(members)))

# reverse loaded models so we build the ensemble with the last models first

members = list(reversed(members))

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

print('Accuracy %.3f (%.3f)' % (mean(single_scores), std(single_scores)))

# plot score vs number of ensemble members

x_axis = [i for i in range(1, len(members)+1)]

pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')

pyplot.plot(x_axis, ensemble_scores, marker='o')

pyplot.show()
```

Listing 23.22: 评估水平集成模型的示例。

首先，将 50 个已保存的模型加载到内存中。

```
...
>loaded models/model_990.h5
>loaded models/model_991.h5
>loaded models/model_992.h5
>loaded models/model_993.h5
>loaded models/model_994.h5
>loaded models/model_995.h5
>loaded models/model_996.h5
>loaded models/model_997.h5
>loaded models/model_998.h5
```

```
>loaded models/model_999.h5
```

Listing 23.23: 加载保存模型的示例输出。

接下来，对每个单模型的性能在保留的测试数据集上进行评估，并创建该大小（1、2、3 等）的集成，并在保留的测试数据集上进行评估。

```
> 1: single=0.814, ensemble=0.814
> 2: single=0.816, ensemble=0.816
> 3: single=0.812, ensemble=0.816
> 4: single=0.812, ensemble=0.815
> 5: single=0.811, ensemble=0.815
> ...
> 46: single=0.817, ensemble=0.818
> 47: single=0.812, ensemble=0.818
> 48: single=0.811, ensemble=0.818
> 49: single=0.810, ensemble=0.818
> 50: single=0.811, ensemble=0.818
```

Listing 23.24: 评估单模型的示例输出。

粗略来看，集成似乎优于大多数单模型， consistently 达到约 81.8% 的准确率。接下来报告单模型准确率的分布。我们可以看到，随机挑选保存的任意一个模型，其准确率平均为 81.6%，标准差相当紧，约为 0.3%。为了有用，水平集成必须优于这一平均水平。

**Note**: 由于学习算法的随机性，您的具体结果可能会有所不同。建议多次运行示例并比较平均性能。

```
Accuracy 0.816 (0.003)
```
