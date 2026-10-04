

## 列表 3.33. 卷积神经网络-加载数据集

```
digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndmos'), ...
'ndatasets','DigitDataset'; % 获取 Digit Dataset 文件的完整路径
imds = imageDatastore(digitDatasetPath, ...
'IncludeSubfolders',true, ...
'LabelSource','foldnames'); % 加载 Digit Dataset
```

随后，通过列表 3.34 中的代码将数据集分为训练集和测试集：

## 列表 3.34. 卷积神经网络-划分数据集

```
numTrainFiles = 800; % 训练集将包含800张图像。剩余图像将用于测试。
[imdsTrain,imdsValidation] = splitEachLabel(imds,numTrainFiles,'randomize'); % 划分数据集
```

图像的大小（28x28x1 像素）和类别的数量（因为有10个数字，所以有10类）通过列表 3.35 中的代码根据 CNN 的层细节进行定义：

## 列表 3.35. 卷积神经网络-定义图像大小、类别数量及 CNN 层细节

```
inputSize = [28 28 1]; % 图像大小
numClasses = 10; % 类别数量（数字）
% 应用 CNN 层
layers = [
InputLayer(inputSize) % 输入图像并应用归一化
convolution2DLayer(5,20) % 应用滑动滤波器
batchNormalizationLayer % 跨所有观测值对每个通道独立归一化小批量数据
reluLayer % 将所有小于零的值设为零
fullyConnectedLayer(numClasses) % 将输入乘以权重矩阵并加上偏置向量
softmaxLayer % 输出表示一组潜在结果的概率分布的向量
classificationLayer]; % 为互斥类别的分类任务和加权分类任务计算交叉熵损失
```

定义训练选项，然后连同训练数据集和层细节一起传递给 `trainNetwork` 函数，以训练 CNN：

## 列表 3.36. 卷积神经网络-定义训练选项并训练 CNN

```
options = trainingOptions('sgdm', 
'MaxEpochs',4, ...
'ValidationData',imdbValidation, ...
'ValidationFrequency',30, ...
'Verbose',false, ...
'Plots','training-progress'); % 定义训练选项
net = trainNetwork(imdsTrain,layers,options); % 训练 CNN
```

图 3.25 显示的窗口展示了执行 `trainNetwork` 函数时 CNN 训练的进度：

![](img/2b52fde0e707e8c2f05a10309c3f8982_193_0.png)

图 3.25. 卷积神经网络-训练进度。GUI。

训练完 CNN 后，使用列表 3.37 中的代码通过 `classify` 函数对测试集中的图像进行分类。此外，通过比较预测数字与其实际值来计算 CNN 的准确率：

## 列表 3.37. 卷积神经网络-分类数据

```
YPred = classify(net,imdsValidation); % 对测试集的图像分类
YValidation = imdsValidation.Labels; % 获取测试集的实际标签
accuracy = mean(YPred == YValidation) % 计算预测的准确率
```

在工作区中得到的预测准确率为 0.9810，这非常接近 1 的最大精度，意味着训练后 CNN 的预测是非常精确的。

## 3.5. 强化学习算法

### 3.5.1. Q-Learning

Q-learning 是一种学习方法，系统依赖与环境的交互来确定价值函数。Q-learning 代理不利用环境模型作为参考，因此被认为是一种无模型算法。代理的作用是从当前状态决定采取的最优动作。

Q-learning 的方程由 (3.24) [50]。该方程依赖于当前状态和所选动作来计算 Q 值。Q 值存储在 Q 表中，也称为称为评论家（critic）。Q 表在学习过程中不断更新。总长期奖励根据动作的执行确定，并识别出导致最高奖励的动作。Q-learning 代理使用探索过程来识别最高奖励。探索是指采取系统已知会导致当前已知最高 Q 值以外的动作，以尝试获得更高的 Q 值 [50]。

```
$Q(s_t, a_t) \leftarrow Q(s_t, a_t) + a[r_{t+1} + \gamma \max Q(s_{t+1}, a_t) - Q(s_t, a_t)] \quad (3.24)$
```

其中，

- $s_t$ - 当前状态
- $a_t$ - 选择的动作
- $Q(s_t, a_t)$ - 当前状态下所选动作的 Q 值
- $\max_a Q(s_{t+1}, a_t)$ - 下一状态下导致最大 Q 动作的 Q 值
- $\alpha$ - 学习率
- $\gamma$ - 折扣率
- $r_{t+1}$ - 移动到 $s_{t+1}$ 时接收的奖励

## 示例 10

在本示例中，使用 Q-Learning 训练 Q-learning 代理，以找到通往目标状态最高奖励的最佳路径。在这种情况下，环境是一个 1×4 的网格世界，如下：

| W | X | Y | Z |
|---|---|---|---|
| | | | |

网格世界适用以下规则：

- 1. 代理最初被放置在单元格 W。
- 2. 代理可以采取的两个可能动作是向前移动或向后移动。
- 3. 向前移动将代理向右移动一个单元格。
- 4. 向后移动将代理向左移动一个单元格。

