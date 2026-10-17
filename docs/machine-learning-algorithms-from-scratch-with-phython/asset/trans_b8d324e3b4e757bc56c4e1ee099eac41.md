

```python
def predict_classification(train, test_row, num_neighbors):
    neighbors = get_neighbors(train, test_row, num_neighbors)
    output_values = [row[-1] for row in neighbors]
    prediction = max(set(output_values), key=output_values.count)
    return prediction

# kNN Algorithm
def k_nearest_neighbors(train, test, num_neighbors):
    predictions = list()
    for row in test:
        output = predict_classification(train, row, num_neighbors)
        predictions.append(output)
    return(predictions)

# Test the kNN on the Abalone dataset
seed(1)
# load and prepare data
filename = 'abalone.csv'
dataset = load_csv(filename)
for i in range(1, len(dataset[0])):
    str_column_to_float(dataset, i)
# convert first column to integers
str_column_to_int(dataset, 0)
# evaluate algorithm
n_folds = 5
num_neighbors = 5
scores = evaluate_algorithm(dataset, k_nearest_neighbors, n_folds, num_neighbors)
print('Scores: %s' % scores)
print('Mean Accuracy: %.3f%%' % (sum(scores)/float(len(scores))))
```

清单 13.12: 鲍鱼数据集上的分类 KNN。

使用了 *k*=5 个邻居来进行预测。你可以尝试更大的 *k* 值来提高准确率。运行示例将打印每个折叠上达到的准确率分数及其平均值。我们可以看到，23% 的平均准确率优于 16% 的基准，但总体来说相当差。这是因为类别数量较多，使得准确率成为评估此问题技能的不佳指标。这一事实，加上许多类别只有很少或只有一个示例的事实，也使得该问题具有挑战性。

```
Scores: [24.191616766467066, 24.431137724550897, 23.47305389221557, 22.035928143712574,
 23.11377245508982]
Mean Accuracy: 23.449%
```

清单 13.13: 鲍鱼数据集上分类 KNN 的示例输出。

我们也可以将该数据集建模为回归预测建模问题。这是因为类别值具有自然的序数关系，因为它们是年份。

### 13.2.5 作为回归的鲍鱼案例研究

回归可能是建模此问题更有用的方法，因为类别数量较多且某些类别值稀疏。我们可以通过将 KNN 更改为预测邻居的平均值并使用根均方误差来评估预测，轻松将上述示例更改为回归。下面是一个包含这些更改的完整可运行示例。

```python
def predict_regression(train, test_row, num_neighbors):
    neighbors = get_neighbors(train, test_row, num_neighbors)
    output_values = [row[-1] for row in neighbors]
    prediction = sum(output_values) / float(len(output_values))
    return prediction

# kNN Algorithm
def k_nearest_neighbors(train, test, num_neighbors):
    predictions = list()
    for row in test:
        output = predict_regression(train, row, num_neighbors)
        predictions.append(output)
    return(predictions)

# Test the kNN on the Abalone dataset
seed(1)
# load and prepare data
filename = 'abalone.csv'
dataset = load_csv(filename)
for i in range(1, len(dataset[0])):
    str_column_to_float(dataset, i)
# convert first column to integers
str_column_to_int(dataset, 0)
# evaluate algorithm
n_folds = 5
num_neighbors = 5
scores = evaluate_algorithm(dataset, k_nearest_neighbors, n_folds, num_neighbors)
print('Scores: %s' % scores)
print('Mean RMSE: %.3f' % (sum(scores)/float(len(scores))))
```

清单 13.14: 鲍鱼数据集上的回归 KNN。

运行此示例将打印每个折叠上的 RMSE 以及所有折叠的平均 RMSE。我们可以看到，2.242 个环的 RMSE 优于 3.222 个环的基准。我们还有一个模型，在该领域可能更有用，其性能更易于理解。

```
Scores: [2.1235153320071554, 2.258503558410589, 2.2739767060988636, 2.3582090027389,
2.196633243122396]
Mean RMSE: 2.242
```

清单 13.15: 鲍鱼数据集上回归 KNN 的示例输出。

### 13.3 扩展

本节列出了你可能希望考虑的教程扩展，以供调查。

- 调整 KNN。尝试越来越大的 *k* 值，看看是否可以提高算法在鲍鱼数据集上的性能。
- 用于分类的回归。将用于回归问题进行预测的方法（取平均值）与用于分类进行预测的方法（返回整数）相结合，看看是否可以改进结果。
- **更多距离度量。** 实现其他可用于查找相似历史数据的距离度量，例如汉明距离、曼哈顿距离和闵可夫斯基距离。
- **数据准备。** 距离度量强烈受输入数据规模的影响。尝试归一化和标准化数据准备方法以改进结果。
- **更多问题。** 与往常一样，在更多不同的分类和回归问题上尝试该技术。

### 13.4 回顾

在本教程中，你了解了如何从头使用 Python 实现 *k*-最近邻算法。具体来说，你学习了：

- 如何在 Python 中从头实现 *k*-最近邻。
- 如何将 *k*-最近邻应用于分类问题。
- 如何将 *k*-最近邻应用于回归问题。

### 13.4.1 进一步阅读

- 第 3.5 节 线性回归与 K-最近邻比较，第 104 页，《统计学导论》，2014年。  
  http://amzn.to/2eeTyQx
- 第 18.8 节，非参数模型，第 737 页，《人工智能：一种现代的方法》，2010年。  
  http://amzn.to/2e31FqP
- 第 7.4 节 K-最近邻，第 159 页，和第 13.5 节 K-最近邻，第 350 页，《应用预测建模》，2013年  
  http://amzn.to/2e31NXF
- 第 4.7 节，基于实例的学习，第 128 页，《数据挖掘：实用机器学习工具和技术》，第二版，2005年。  
  http://amzn.to/2fj3SYY

### 13.4.2 下一步

在下一个教程中，你将了解如何实现和应用学习向量量化算法用于分类。

## 第 14 章

## 学习向量量化

k-最近邻的一个局限是，为了进行预测，你必须保留大量训练示例数据库。学习向量量化算法通过学习一个更小的子集模式来解决这个问题，这些模式最能代表训练数据。在本教程中，你将了解如何从头使用 Python 实现学习向量量化算法。完成本教程后，你将知道：

- 如何从训练数据集中学习一组码本向量。
- 如何使用学习到的码本向量进行预测。
- 如何将学习向量量化应用于真实的预测建模问题。

让我们开始吧。

### 14.1 描述

本节简要介绍了学习向量量化算法以及本教程中将使用的电离层分类问题。

### 14.1.1 学习向量量化

学习向量量化（LVQ）算法与 k-最近邻非常相似。预测是通过在模式库中找到最佳匹配来进行的。区别在于，模式库是从训练数据中学习的，而不是直接使用训练模式本身。

模式库称为码本向量，每个模式称为一个码本向量。码本向量初始化为从训练数据集中随机选择的值。然后，经过若干个时代，它们使用学习算法进行调整，以最好地总结训练数据。学习算法一次显示一条训练记录，在码本向量中找到最佳匹配单元，如果它们属于同一类别，则将其移近训练记录，如果属于不同类别，则将其移远。

一旦准备就绪，码本向量将用于使用 k-最近邻算法进行预测，其中 *k*=1。该算法是为分类预测建模问题开发的，但可以调整用于回归问题。

