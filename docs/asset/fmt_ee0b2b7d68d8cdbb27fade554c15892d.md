
# 2.2c 使用多层深度学习网络进行分类 – Tanh 激活函数 (Octave)

以下代码在 Octave 中对隐藏层使用 Tanh 激活函数。

```octave
# 读取数据
data = csvread("data.csv");
X = data(:, 1:2);
Y = data(:, 3);

# 设置层维度
# 2 - 输入特征
# 9 7 – 2 个隐藏层，分别含 9 和 7 个隐藏单元
# 1 – 输出层含 1 个 Sigmoid 单元
layersDimensions = [2 9 7 1] # tanh=-0.5(ok), # relu=0.1 best!

# 执行 L 层深度学习网络
# 隐藏层激活函数 – tanh
# 学习率 – 0.1
[weights biases costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                           hiddenActivationFunc='tanh',
                                           learningRate = 0.1,
                                           numIterations = 10000);

# 绘制代价 vs 迭代次数
plotCostVsIterations(10000, costs);

# 绘制决策边界
plotDecisionBoundary(data, weights, biases, hiddenActivationFunc="tanh")
```

# 3. 伯努利双纽线

为了增加趣味性，我创建了伯努利双纽线的二维图形来执行非线性分类。双纽线由以下方程给出：

$$ (x^2 + y^2)^2 - 2a^2(x^2 - y^2) \le 0 $$

## 3a. 使用深度学习网络对双纽线进行分类 – Relu 激活函数 (Python)

```python
import os
import numpy as np
import matplotlib.pyplot as plt

os.chdir("C:\\software\\DeepLearning-Posts\\part3")
execfile("./DLfunctions33.py")

# 创建数据集
x1 = np.random.uniform(0, 10, 2000).reshape(2000, 1)
x2 = np.random.uniform(0, 10, 2000).reshape(2000, 1)
X = np.append(x1, x2, axis=1)

# 创建一个平方值 <0.4 的值子集。执行 ravel() 以展平此向量
# 创建方程
# (x² + y²)² - 2a²*(x² - y²) <= 0
a = np.power(np.power(X[:, 0] - 5, 2) + np.power(X[:, 1] - 5, 2), 2)
b = np.power(X[:, 0] - 5, 2) - np.power(X[:, 1] - 5, 2)
c = a - (b * np.power(4, 2)) <= 0
Y = c.reshape(2000, 1)

# 创建双纽线的散点图
plt.scatter(X[:, 0], X[:, 1], c=Y, marker='o', s=15, cmap="viridis")
Z = np.append(X, Y, axis=1)
plt.savefig("fig50.png", bbox_inches='tight')
plt.clf()

# 设置分类数据
X2 = X.T
Y2 = Y.T

# 这些设置效果最好
# 设置用于 Relu 激活函数的深度学习层维度
# 2 - 输入特征
# 7, 4 – 2 个隐藏层，分别含 7 和 4 个隐藏单元
# 1 – 输出层含 1 个 Sigmoid 激活单元
layersDimensions = [2, 7, 4, 1]

# 执行 L 层深度学习网络
# 隐藏层激活函数 – relu
# 学习率 – 0.5
parameters = L_Layer_DeepModel(X2, Y2, layersDimensions,
                               hiddenActivationFunc='relu',
                               learning_rate=0.5,
                               num_iterations=10000,
                               fig="fig5.png")

# 绘制决策边界
plot_decision_boundary(lambda x: predict(parameters, x.T), X2, Y2, str(2.2), "fig6.png")

# 计算混淆矩阵
yhat = predict(parameters, X2)
from sklearn.metrics import confusion_matrix
a = confusion_matrix(Y2.T, yhat.T)

# 打印准确率、精确率、召回率和 F1 分数
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
print('Accuracy: {:.2f}'.format(accuracy_score(Y2.T, yhat.T)))
print('Precision: {:.2f}'.format(precision_score(Y2.T, yhat.T)))
print('Recall: {:.2f}'.format(recall_score(Y2.T, yhat.T)))
print('F1: {:.2f}'.format(f1_score(Y2.T, yhat.T)))

## Accuracy: 0.93
## Precision: 0.77
## Recall: 0.76
## F1: 0.76
```

通过进一步调优，我们可以获得更好的性能。请自行尝试修改代码。

> **注意：** 双纽线数据已保存为 CSV，随后在 R 和 Octave 中读取。

## 3b. 使用深度学习网络对双纽线进行分类 – Relu 激活函数 (R 代码)

下图展示了伯努利双纽线在 R 语言下的决策边界。

```r
# 读取双纽线数据
Z <- as.matrix(read.csv("lemniscate.csv", header=FALSE))
Z1 <- data.frame(Z)

# 创建双纽线的散点图
ggplot(Z1, aes(x=V1, y=V2, col=V3)) + geom_point()

# 设置深度学习网络的数据
X <- Z[, 1:2]
Y <- Z[, 3]
X1 <- t(X)
Y1 <- t(Y)

# 设置用于 tanh 激活函数的层维度
# 2 – 输入特征数量
# 5, 4 – 2 个隐藏层，分别含 5 和 4 个隐藏单元
# 1 – 输出层含 1 个 Sigmoid 输出激活函数
layersDimensions = c(2, 5, 4, 1)

# 执行 L 层深度学习网络
# 隐藏层激活函数 - Tanh 激活
# 学习率=0.3
retvals = L_Layer_DeepModel(X1, Y1, layersDimensions,
                            hiddenActivationFunc='tanh',
                            learningRate = 0.3,
                            numIterations = 20000,
                            print_cost = True)

# 绘制代价 vs 迭代次数
costs <- retvals[['costs']]
numIterations = 20000
iterations <- seq(0, numIterations, by=1000)
df <- data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  xlab('迭代次数') + ylab('代价') + ggtitle("代价 vs 迭代次数")

# 绘制决策边界
plotDecisionBoundary(Z, retvals, hiddenActivationFunc="tanh", 0.3)
```

## 3c. 使用深度学习网络对双纽线进行分类 – Relu 激活函数 (Octave 代码)

Octave 用于生成非线性双纽线边界。

```octave
# 读取数据
data = csvread("lemniscate.csv");
X = data(:, 1:2);
Y = data(:, 3);

# 设置层的维度
# 2 – 输入特征数量
# 9 7 – 2 个隐藏层，分别含 9 和 7 个激活单元
# 1 – 输出层含 1 个激活单元 (Sigmoid)
layersDimensions = [2 9 7 1]

# 执行 L 层深度学习网络
# 隐藏层激活函数 – relu
# 学习率- 0.20
[weights biases costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                           hiddenActivationFunc='relu',
                                           learningRate = 0.20,
                                           numIterations = 10000);

# 绘制代价 vs 迭代次数
plotCostVsIterations(10000, costs);

# 绘制决策边界
plotDecisionBoundary(data, weights, biases, hiddenActivationFunc="relu")
```

# 4a. 使用 MNIST 进行二分类 – Python 代码

最后，我使用 MNIST 手写数字进行简单分类，根据 Geoffrey Hinton 教授的说法，这是“深度学习的果蝇”。

## 使用 MNIST 进行二分类

读取 MNIST 数据的 Python 代码取自 Alex Kesling 的 GitHub 链接 MNIST (https://gist.github.com/akesling/5358964)。

在下面的 Python 代码中，我对手写数字 '5' 和 '非 5'（即所有其他数字）执行了一个简单的二分类。我将在第 5 章使用 Softmax 分类器对所有数字进行正确分类。

```python
import os
import numpy as np
import matplotlib.pyplot as plt

execfile("./DLfunctions34.py")

# Load MNIST
execfile("./load_mnist.py")

# Set the training and test data and labels
training = list(read(dataset='training', path="./mnist"))
test = list(read(dataset='testing', path="./mnist"))

lbls = []
pxls = []

print(len(training))

# Select the first 10000 training data and the labels
for i in range(10000):
    l, p = training[i]
    lbls.append(l)
    pxls.append(p)

labels = np.array(lbls)
pixels = np.array(pxls)

# Set y=1 when labels == 5 and 0 otherwise
y = (labels == 5).reshape(-1, 1)
X = pixels.reshape(pixels.shape[0], -1)

# Create the necessary feature and target variable
X1 = X.T
Y1 = y.T

# Create the layer dimensions. The number of features are 28 x 28 = 784 since the 28 x 28
# pixels is flattened to single vector of length 784.
# 784 – No of input features = 28 x28
# 15, 9 – 2 hidden layers with 15 and 9 hidden activation units
# 1 – 1 activation unit in the output layer (sigmoid)
layersDimensions = [784, 15, 9, 7, 1]  #

# Execute the L-Layer Deep Learning Network
# hidden activation function – relu
# learning rate – 0.1
parameters = L_Layer_DeepModel(X1, Y1, layersDimensions,
                               hiddenActivationFunc='relu', learning_rate=0.1,
                               num_iterations=1000, fig="fig7.png")

# Read the Test data and labels
lbls1 = []
pxls1 = []

for i in range(800):
    l, p = test[i]
    lbls1.append(l)
    pxls1.append(p)

testLabels = np.array(lbls1)
testData = np.array(pxls1)

ytest = (testLabels == 5).reshape(-1, 1)
Xtest = testData.reshape(testData.shape[0], -1)
Xtest1 = Xtest.T
Ytest1 = ytest.T

# Predict based on test data
yhat = predict(parameters, Xtest1)

from sklearn.metrics import confusion_matrix

# Compute the confusion matrix
a = confusion_matrix(Ytest1.T, yhat.T)

# Print accuracy, precision, recall and F1 score
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

print('Accuracy: {:.2f}'.format(accuracy_score(Ytest1.T, yhat.T)))
print('Precision: {:.2f}'.format(precision_score(Ytest1.T, yhat.T)))
print('Recall: {:.2f}'.format(recall_score(Ytest1.T, yhat.T)))
print('F1: {:.2f}'.format(f1_score(Ytest1.T, yhat.T)))

# Plot the Precision-Recall curve
probs = predict_proba(parameters, Xtest1)

from sklearn.metrics import precision_recall_curve

precision, recall, thresholds = precision_recall_curve(Ytest1.T, probs.T)
closest_zero = np.argmin(np.abs(thresholds))
closest_zero_p = precision[closest_zero]
closest_zero_r = recall[closest_zero]

# Plot precision-recall curve
plt.xlim([0.0, 1.01])
plt.ylim([0.0, 1.01])
plt.plot(precision, recall, label='Precision-Recall Curve')
plt.plot(closest_zero_p, closest_zero_r, 'o', markersize=12, fillstyle='none', c='r', mew=3)
plt.xlabel('Precision', fontsize=16)
plt.ylabel('Recall', fontsize=16)
plt.savefig("fig8.png", bbox_inches='tight')
```

## 结果

**Accuracy: 0.99**

**Precision: 0.96**

**Recall: 0.89**

**F1: 0.92**

![Image 183](img/index-123_1.jpg)
