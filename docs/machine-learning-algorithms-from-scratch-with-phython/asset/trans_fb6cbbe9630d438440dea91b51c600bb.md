

```
# Evaluate an algorithm using a cross validation split
def evaluate_algorithm(dataset, algorithm, n_folds, *args):
    folds = cross_validation_split(dataset, n_folds)
    scores = list()
    for fold in folds:
        train_set = list(folds)
        train_set.remove(fold)
        train_set = sum(train_set, [])
        test_set = list()
        for row in fold:
            row_copy = list(row)
            test_set.append(row_copy)
            row_copy[-1] = None
        predicted = algorithm(train_set, test_set, *args)
        actual = [row[-1] for row in fold]
        accuracy = accuracy_metric(actual, predicted)
        scores.append(accuracy)
    return scores
```

```
# Calculate the Euclidean distance between two vectors
def euclidean_distance(row1, row2):
    distance = 0.0
    for i in range(len(row1)-1):
        distance += (row1[i] - row2[i])**2
    return sqrt(distance)
```

```
# Locate neighbors for a new row
def get_neighbors(train, test_row, num_neighbors):
    distances = list()
    for train_row in train:
        dist = euclidean_distance(test_row, train_row)
        distances.append((train_row, dist))
    distances.sort(key=lambda tup: tup[1])
    neighbors = list()
    for i in range(num_neighbors):
        neighbors.append(distances[i][0])
    return neighbors
```

```
# Make a prediction with kNN
def knn_predict(model, test_row, num_neighbors=2):
    neighbors = get_neighbors(model, test_row, num_neighbors)
    output_values = [row[-1] for row in neighbors]
    prediction = max(set(output_values), key=output_values.count)
    return prediction
```

```
# Prepare the kNN model
def knn_model(train):
    return train
```

```
# Make a prediction with weights
def perceptron_predict(model, row):
    activation = model[0]
    for i in range(len(row)-1):
        activation += model[i + 1] * row[i]
    return 1.0 if activation >= 0.0 else 0.0
```

```
# Estimate Perceptron weights using stochastic gradient descent
def perceptron_model(train, l_rate=0.01, n_epoch=5000):
    weights = [0.0 for i in range(len(train[0]))]
    for _ in range(n_epoch):
        for row in train:
            prediction = perceptron_predict(weights, row)
            error = row[-1] - prediction
            weights[0] = weights[0] + l_rate * error
            for i in range(len(row)-1):
                weights[i + 1] = weights[i + 1] + l_rate * error * row[i]
    return weights
```

```
# Make a prediction with coefficients
def logistic_regression_predict(model, row):
    yhat = model[0]
    for i in range(len(row)-1):
        yhat += model[i + 1] * row[i]
    return 1.0 / (1.0 + exp(-yhat))
```

```
# Estimate logistic regression coefficients using stochastic gradient descent
def logistic_regression_model(train, l_rate=0.01, n_epoch=5000):
    coef = [0.0 for i in range(len(train[0]))]
    for _ in range(n_epoch):
        for row in train:
            yhat = logistic_regression_predict(coef, row)
            error = row[-1] - yhat
            coef[0] = coef[0] + l_rate * error * yhat * (1.0 - yhat)
            for i in range(len(row)-1):
                coef[i + 1] = coef[i + 1] + l_rate * error * yhat * (1.0 - yhat) * row[i]
    return coef
```

```
# Make predictions with sub-models and construct a new stacked row
def to_stacked_row(models, predict_list, row):
    stacked_row = list()
    for i in range(len(models)):
        prediction = predict_list[i](models[i], row)
        stacked_row.append(prediction)
    stacked_row.append(row[-1])
    return row[0:len(row)-1] + stacked_row
```

```
# Stacking Generalization Algorithm
def stacking(train, test):
    model_list = [knn_model, perceptron_model]
    predict_list = [knn_predict, perceptron_predict]
    models = list()
    for i in range(len(model_list)):
        model = model_list[i](train)
        models.append(model)
    stacked_dataset = list()
    for row in train:
        stacked_row = to_stacked_row(models, predict_list, row)
        stacked_dataset.append(stacked_row)
    stacked_model = logistic_regression_model(stacked_dataset)
    predictions = list()
    for row in test:
        stacked_row = to_stacked_row(models, predict_list, row)
        stacked_dataset.append(stacked_row)
        prediction = logistic_regression_predict(stacked_model, stacked_row)
        prediction = round(prediction)
        predictions.append(prediction)
    return predictions
```

```
# Test stacking on the sonar dataset
seed(1)
# load and prepare data
filename = 'sonar.all-data.csv'
dataset = load_csv(filename)
# convert string attributes to integers
for i in range(len(dataset[0])-1):
    str_column_to_float(dataset, i)
# convert class column to integers
str_column_to_int(dataset, len(dataset[0])-1)
n_folds = 3
scores = evaluate_algorithm(dataset, stacking, n_folds)
print('Scores: %s' % scores)
print('Mean Accuracy: %.3f%%' % (sum(scores)/float(len(scores))))
```

采用 k=3 进行交叉验证，每个折叠包含 208/3 = 69.3 条记录，即每次迭代评估略少于 70 条记录。我在训练数据集上分别评估了每个子模型，KNN 达到 74.879%，感知机算法达到 72.464%；两种算法均优于 53% 的基准准确率。

在堆叠数据集上训练逻辑回归（不包含用于上下文的训练行）可达到 75.845% 的准确率。将训练行包含在堆叠数据集中可进一步提升至 76.329%。运行示例将打印最终配置的得分及其平均值。

```
Scores: [78.26086956521739, 78.26086956521739, 72.46376811594203]
Mean Accuracy: 76.329%
```

## 18.3 扩展

本节列出了本教程的扩展内容，您可能有兴趣探索。

- **调整算法**。本教程中用于子模型和聚合模型的算法均未进行调整。探索替代配置，看看是否能进一步提升性能。

- **预测相关性**。如果子模型的预测之间弱相关，堆叠效果更好。实现计算以估计子模型预测之间的相关性。

- **不同的子模型**。实现更多不同的子模型，以使用堆叠过程进行组合。

- **不同的聚合模型**。尝试更简单的模型（如平均和投票）以及更复杂的聚合模型，看看是否能提升性能。

- **更多数据集**。将堆叠应用于 UCI 机器学习库中的更多数据集。

## 18.4 回顾

在本教程中，您了解了如何在 Python 中从头实现堆叠算法。具体来说，您学习了：

- 如何组合多个模型的预测。
- 如何将堆叠应用于现实世界的预测建模问题。

### 18.4.1 进一步阅读

- 第 7.5 节，组合多个模型，第 315 页，_数据挖掘：实用机器学习工具与技术_，第二版，2005 年。
- http://amzn.to/2fj3SYY

### 18.4.2 下一步

这结束了关于集成算法的第 4 部分。接下来在第 5 部分我们将结束本书。

## 第 V 部分

## 结论

## 第 19 章

## 你已经走得多远

你做到了。做得好。花点时间回顾一下你已经走得多远。

- 你知道如何加载和准备用于建模的机器学习数据。
- 你知道如何评估机器学习模型做出的预测并估计模型的性能。
- 你知道如何估计问题上的基准性能并比较问题上的多个模型。
- 你知道如何实现和应用线性回归、逻辑回归和感知机线性机器学习算法。
- 你知道如何实现和应用 CART、朴素贝叶斯、KNN、LVQ 和反向传播非线性机器学习算法。
- 你知道如何实现和应用 Bagging、随机森林和堆叠集成机器学习算法。

不要轻视这一点。你在短时间内取得了长足进步。你已经掌握了使用 Python 实现和解决机器学习问题的重要而宝贵的技能。这是大多数在职数据科学家专业人士使用的平台。前途无量。

我想花点时间诚挚地感谢你，让我能帮助你使用 Python 开启机器学习算法之旅。我希望你继续学习，并在继续掌握机器学习的过程中享受乐趣。

