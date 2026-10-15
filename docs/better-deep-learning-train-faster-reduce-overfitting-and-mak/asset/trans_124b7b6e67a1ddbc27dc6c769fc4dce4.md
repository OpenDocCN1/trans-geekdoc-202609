
> 4: single=0.805, ensemble=0.813
> 5: single=0.807, ensemble=0.813
> 6: single=0.805, ensemble=0.813
> 7: single=0.802, ensemble=0.811
> 8: single=0.805, ensemble=0.810
> 9: single=0.805, ensemble=0.809
> 10: single=0.810, ensemble=0.809

清单26.28：线性加权集成的示例输出。

折线图显示了性能的提升，并且与使用均匀加权集成相比，在不同规模的集成模型上，测试准确率的性能更加稳定。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_554_0.png)

图26.4：线性衰减下单模型测试性能（蓝点）与模型权重集成测试性能（橙线）的折线图。

我们还可以尝试对模型的贡献进行指数衰减。这需要指定一个衰减率（alpha）。下面的示例创建了一个衰减率为2的指数衰减权重。

```
# prepare an array of exponentially decreasing weights
alpha = 2.0
weights = [exp(-i/alpha) for i in range(1, n_members+1)]
```

## 清单26.29：对集成成员使用指数递减权重的示例。

下面列出了在集成模型中对模型贡献进行指数衰减以计算平均权重的完整示例。

```python
# exponentially decreasing weighted average of models on blobs problem
from sklearn.datasets.samples_generator import make_blobs
from keras.utils import to_categorical
from keras.models import load_model
from keras.models import clone_model
from matplotlib import pyplot
from numpy import average
from numpy import array
from math import exp

# load models from file
def load_all_models(n_start, n_end):
    all_models = list()
    for epoch in range(n_start, n_end):
        # define filename for this ensemble
        filename = 'model_' + str(epoch) + '.h5'
        # load model from file
        model = load_model(filename)
        # add to list of members
        all_models.append(model)
        print('>loaded %s' % filename)
    return all_models

# create a model from the weights of multiple models
def model_weight_ensemble(members, weights):
    # determine how many layers need to be averaged
    n_layers = len(members[0].get_weights())
    # create a set of average model weights
    avg_model_weights = list()
    for layer in range(n_layers):
        # collect this layer from each model
        layer_weights = array([model.get_weights()[layer] for model in members])
        # weighted average of weights for this layer
        avg_layer_weights = average(layer_weights, axis=0, weights=weights)
        # store average layer weights
        avg_model_weights.append(avg_layer_weights)
    # create a new model with the same structure
    model = clone_model(members[0])
    # set the weights in the new model
    model.set_weights(avg_model_weights)
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    return model

# evaluate a specific number of members in an ensemble
def evaluate_n_members(members, n_members, testX, testy):
    # select a subset of members
    subset = members[:n_members]
    # prepare an array of exponentially decreasing weights
    alpha = 2.0
    weights = [exp(-i/alpha) for i in range(1, n_members+1)]
    # create a new model with the weighted average of all model weights
    model = model_weight_ensemble(subset, weights)
    # make predictions and evaluate accuracy
    _, test_acc = model.evaluate(testX, testy, verbose=0)
    return test_acc

# generate 2d classification dataset
X, y = make_blobs(n_samples=1100, centers=3, n_features=2, cluster_std=2, random_state=2)
# one hot encode output variable
y = to_categorical(y)
# split into train and test
n_train = 100
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# load models in order
members = load_all_models(490, 500)
print('Loaded %d models' % len(members))
# reverse loaded models so we build the ensemble with the last models first
members = list(reversed(members))
# evaluate different numbers of ensembles on hold out set
single_scores, ensemble_scores = list(), list()
for i in range(1, len(members)+1):
    # evaluate model with i members
    ensemble_score = evaluate_n_members(members, i, testX, testy)
    # evaluate the i'th model standalone
    _, single_score = members[i-1].evaluate(testX, testy, verbose=0)
    # summarize this step
    print('> %d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))
    ensemble_scores.append(ensemble_score)
    single_scores.append(single_score)
# plot score vs number of ensemble members
x_axis = [i for i in range(1, len(members)+1)]
pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')
pyplot.plot(x_axis, ensemble_scores, marker='o')
pyplot.show()
```

清单26.30：指数加权集成性能的示例。

运行该示例显示出性能的小幅提升，与在已保存模型的加权平均中使用线性衰减非常相似。

**注意：** 由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行该示例并比较平均性能。

> 1: single=0.814, ensemble=0.814
> 2: single=0.814, ensemble=0.815
> 3: single=0.811, ensemble=0.814
> 4: single=0.805, ensemble=0.814
> 5: single=0.807, ensemble=0.813
> 6: single=0.805, ensemble=0.813
> 7: single=0.802, ensemble=0.813
> 8: single=0.805, ensemble=0.813
> 9: single=0.805, ensemble=0.813
> 10: single=0.810, ensemble=0.813

清单26.31：指数加权集成的示例输出。

## 26.3 扩展

测试准确率分数的折线图显示，与线性或等权重的模型加权相比，使用指数衰减具有更强的稳定效果。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_557_0.png)

## 26.3 扩展

本节列出了你可能希望探索的一些扩展本教程的想法。

- 模型数量。评估更多模型将其权重贡献给最终模型的效果。
- 衰减率。评估在指数加权平均中使用不同衰减率对测试性能的影响。

如果你探索了其中任何扩展，我很乐意了解。

## 26.4 进一步阅读

如果你想更深入地了解该主题，本节提供了更多资源。

### 26.4.1 书籍

- 第8.7.3节 Polyak 平均，*深度学习*，2016年。
  https://amzn.to/2A1v00d

### 26.4.2 论文

- *通过平均加速随机逼近*，1992年。
  https://epubs.siam.org/doi/abs/10.1137/0330046
- *来自慢收敛 Robbins-Monro 过程的有效估计*，1988年。
  https://ecommons.cornell.edu/handle/1813/8664

### 26.4.3 API

- Keras Sequential 模型入门。
  https://keras.io/getting-started/sequential-model-guide/
- Keras Core Layers API。
  https://keras.io/layers/core/
- sklearn.datasets.make_blobs API。
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html
- numpy.average API。
  https://docs.scipy.org/doc/numpy/reference/generated/numpy.average.html

## 26.5 总结

在本教程中，你了解了如何将多个不同模型的权重合并到一个模型中用于预测。具体来说，你学到了：

- 训练神经网络的随机性和挑战性可能意味着优化过程不会收敛。
- 使用训练过程末尾观察到的模型权重的平均值创建模型，可以得到更稳定且有时性能更好的解决方案。
- 如何开发使用多个已保存模型参数的等权重、线性加权和指数加权平均创建的最终模型。

### 26.5.1 下一步

这是本部分的最后一个教程。接下来，你将了解附录和资源，你可以利用它们更深入地探讨如何让神经网络获得更好性能的主题。

