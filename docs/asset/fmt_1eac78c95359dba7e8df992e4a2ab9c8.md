
```
print('> %d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))

ensemble_scores.append(ensemble_score)

single_scores.append(single_score)

# summarize average accuracy of a single final model

print('Accuracy %.3f (+/-.3f)' % (mean(single_scores), std(single_scores)))
```

清单 24.24：评估不同大小快照集成的示例。

最后，我们可以绘制每个独立快照模型的性能（蓝点），并与包含截至当前模型（含当前模型）在内的所有模型的集成性能（橙色线）进行对比。

```
# plot score vs number of ensemble members

x_axis = [i for i in range(1, len(members)+1)]

pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')

pyplot.plot(x_axis, ensemble_scores, marker='o')

pyplot.show()
```

清单 24.25：绘制集成性能与集成大小关系的示例。

下面列出了使用不同大小集成进行快照集成预测的完整示例。

```
# load models and make a snapshot ensemble prediction

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

def load_all_models(n_models):

    all_models = list()

    for i in range(n_models):

        # define filename for this ensemble

        filename = 'snapshot_model_' + str(i + 1) + '.h5'

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

print(trainX.shape, testX.shape)

# load models in order

members = load_all_models(10)

print('Loaded %d models' % len(members))

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

    print('> %d: single=%.3f, ensemble=%.3f' % (i, single_score, ensemble_score))

    ensemble_scores.append(ensemble_score)

    single_scores.append(single_score)

# summarize average accuracy of a single final model

print('Accuracy %.3f (+/-.3f)' % (mean(single_scores), std(single_scores)))

# plot score vs number of ensemble members

x_axis = [i for i in range(1, len(members)+1)]

pyplot.plot(x_axis, single_scores, marker='o', linestyle='None')

pyplot.plot(x_axis, ensemble_scores, marker='o')

pyplot.show()
```

清单 24.26：加载并评估不同大小快照集成的示例。

运行该示例时，首先会将所有 10 个模型加载到内存中。

```
>loaded snapshot_model_1.h5

>loaded snapshot_model_2.h5

>loaded snapshot_model_3.h5

>loaded snapshot_model_4.h5

>loaded snapshot_model_5.h5

>loaded snapshot_model_6.h5

>loaded snapshot_model_7.h5

>loaded snapshot_model_8.h5

>loaded snapshot_model_9.h5

>loaded snapshot_model_10.h5

Loaded 10 models
```

清单 24.27：加载已保存的快照集成成员后的示例输出。

接下来，在测试数据集上评估每个快照模型，并报告其准确率。将此与一个快照集成的准确率进行对比，该快照集成包含了从运行结束点开始向前回溯的所有快照模型，包括单个模型。结果显示，随着我们从运行结束点向前回溯，快照模型的性能会如预期那样逐渐变差。

将快照模型组合成集成后，性能会提升，一直到最后 3 到 5 个模型时达到最高，约 82%。这可以与单个快照模型约 80% 的测试集平均准确率形成对比。

注意：由于学习算法具有随机性，你的具体结果可能会有所不同。

可以考虑多次运行该示例，并比较平均性能。

```
> 1: single=0.813, ensemble=0.813

> 2: single=0.814, ensemble=0.813

> 3: single=0.822, ensemble=0.822

> 4: single=0.810, ensemble=0.820

> 5: single=0.813, ensemble=0.818

> 6: single=0.811, ensemble=0.815

> 7: single=0.807, ensemble=0.813

> 8: single=0.805, ensemble=0.813

> 9: single=0.805, ensemble=0.813

> 10: single=0.790, ensemble=0.813

Accuracy 0.809 (0.008)
```
