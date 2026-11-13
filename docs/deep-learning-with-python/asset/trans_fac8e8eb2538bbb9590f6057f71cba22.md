

## 4.3.1 波士顿房价数据集

在本节中，我们将尝试根据当时郊区的数据点（例如犯罪率、当地房产税率等）来预测20世纪70年代中期给定波士顿郊区住宅的中位数价格。我们将使用的数据集与前两个示例有一个有趣的区别。它的数据点相对较少：只有506个，分为404个训练样本和102个测试样本。并且输入数据中的每个特征（例如犯罪率）都有不同的尺度。例如，有些值是比例，取值在0到1之间，有些取值在1到12之间，有些在0到100之间，等等。

## 清单 4.23 加载波士顿房价数据集

```
from tensorflow.keras.datasets import boston_housing
(train_data, train_targets), (test_data, test_targets) = (
 boston_housing.load_data())
```

让我们来看看数据：

```
>>> train_data.shape
(404, 13)
>>> test_data.shape
(102, 13)
```

如您所见，我们有404个训练样本和102个测试样本，每个样本都有13个数值特征，例如人均犯罪率、每户平均房间数、高速公路可达性等等。

目标是自有住房的中位数值，单位为千美元：

```
>>> train_targets
[ 15.2, 42.3, 50 ... 19.4, 19.4, 29.1]
```

价格通常在10,000美元到50,000美元之间。如果这听起来很便宜，请记住这是20世纪70年代中期，这些价格没有按通货膨胀进行调整。

## 4.3.2 准备数据

将数值范围差异巨大的值馈送到神经网络中会很有问题。模型可能能够自动适应这种异构数据，但这肯定会让学习更加困难。处理此类数据的一种广泛的最佳实践是进行特征归一化：对于输入数据中的每个特征（输入数据矩阵的一列），我们减去该特征的均值并除以标准差，使特征围绕0中心化并具有单位标准差。这在NumPy中很容易实现。

## 清单 4.24 归一化数据

```
mean = train_data.mean(axis=0)
train_data -= mean
std = train_data.std(axis=0)
train_data /= std
test_data -= mean
test_data /= std
```

请注意，用于归一化测试数据的量是使用训练数据计算的。您永远不应该在工作流中使用任何在测试数据上计算的量，即使是进行像数据归一化这样简单的操作。

## 4.3.3 构建您的模型

由于可用样本很少，我们将使用一个非常小的模型，包含两个中间层，每个层有64个单位。一般来说，训练数据越少，过拟合就越严重，使用小模型是缓解过拟合的一种方法。

## 清单 4.25 模型定义

```
def build_model():
    model = keras.Sequential([
        layers.Dense(64, activation="relu"),
        layers.Dense(64, activation="relu"),
        layers.Dense(1)
    ])
    model.compile(optimizer="rmsprop", loss="mse", metrics=["mae"])
    return model
```

模型以一个单元且没有激活函数结尾（它将是一个线性层）。这是标量回归（试图预测单个连续值的回归）的典型设置。应用激活函数将限制输出可以取的范围；例如，如果在最后一层应用sigmoid激活函数，模型只能学习预测0到1之间的值。在这里，由于最后一层是纯粹线性的，模型可以自由地学习预测任何范围内的值。

请注意，我们使用mse损失函数编译模型——均方误差，即预测值与目标值之差的平方。这是回归问题中广泛使用的损失函数。

我们在训练期间还监控一个新指标：平均绝对误差（MAE）。它是预测值与目标值之差的绝对值。例如，在这个问题上MAE为0.5意味着您的预测平均偏差为500美元。

## 4.3.4 使用K折交叉验证验证您的方法

在不断调整模型参数（例如训练使用的 epoch 数量）的同时评估模型，我们可以像之前的示例一样将数据分为训练集和验证集。但由于我们的数据点很少，验证集最终会非常小（例如，大约100个样本）。因此，验证分数可能会根据我们选择哪些数据点作为验证、哪些作为训练而变化很大：验证分数可能对验证划分具有高 _方差_。这将阻止我们可靠地评估模型。

在这种情况下，最佳实践是使用 _K折_ 交叉验证（参见图4.8）。

![](img/ab452ecf572a1f1372915be13bd8088f_140_0.png)

## 图 4.8 使用 K=3 的 K 折交叉验证

它包括将可用数据分为 _K_ 个分区（通常 _K_ = 4 或 5），实例化 _K_ 个相同的模型，并在 _K_ – 1 个分区上训练每个模型，同时在剩余分区上进行评估。然后使用的模型的验证分数是所获得的 _K_ 个验证分数的平均值。从代码角度来看，这很简单。

## 清单 4.26 K 折验证

```
k = 4
num_val_samples = len(train_data) // k
num_epochs = 100
all_scores = []
for i in range(k):
    print(f"Processing fold #{i}")
    val_data = train_data[i * num_val_samples: (i + 1) * num_val_samples]
    val_targets = train_targets[i * num_val_samples: (i + 1) * num_val_samples]
    partial_train_data = np.concatenate(
        [train_data[:i * num_val_samples],
         train_data[(i + 1) * num_val_samples:]],
        axis=0)
    partial_train_targets = np.concatenate(
        [train_targets[:i * num_val_samples],
         train_targets[(i + 1) * num_val_samples:]],
        axis=0)
    model = build_model()
    model.fit(partial_train_data, partial_train_targets,
              epochs=num_epochs, batch_size=16, verbose=0)
    val_mse, val_mae = model.evaluate(val_data, val_targets, verbose=0)
    all_scores.append(val_mae)
```

使用 num_epochs = 100 运行此代码会产生以下结果：

```
>>> all_scores
[2.112449, 3.0801501, 2.6483836, 2.4275346]
>>> np.mean(all_scores)
2.5671294
```

不同的运行确实显示出相当不同的验证分数，从2.1到3.1。平均值（2.6）比任何单一分数都可靠得多——这就是K折交叉验证的整个要点。在这种情况下，我们平均偏差为2,600美元，考虑到价格范围在10,000美元到50,000美元之间，这是显著的。

让我们尝试训练模型更长一段时间：500个 epoch。为了记录模型在每个 epoch 的表现，我们将修改训练循环以保存每个 fold 每个 epoch 的验证分数日志。

## 清单 4.27 保存每个 fold 的验证日志

```
num_epochs = 500
all_mae_histories = []
for i in range(k):
    print("Processing fold #", i)
    val_data = train_data[i * num_val_samples : (i + 1) * num_val_samples]
    val_targets = train_targets[i * num_val_samples : (i + 1) * num_val_samples]
    partial_train_data = np.concatenate(
        [train_data[:i * num_val_samples],
         train_data[(i + 1) * num_val_samples:]],
        axis=0)
    partial_train_targets = np.concatenate(
        [train_targets[:i * num_val_samples],
         train_targets[(i + 1) * num_val_samples:]],
         axis=0)
    model = build_model()
    history = model.fit(partial_train_data, partial_train_targets,
                        validation_data=(val_data, val_targets),
                        epochs=num_epochs, batch_size=16, verbose=0)
    mae_history = history.history["val_mae"]
    all_mae_histories.append(mae_history)
```

然后我们可以计算所有 fold 每个 epoch MAE 分数的平均值。

## 清单 4.28 构建连续平均 K 折验证分数的历史记录

```
average_mae_history = [
    np.mean([x[i] for x in all_mae_histories]) for i in range(num_epochs)]
```

让我们绘制这个；参见图4.9。

## 清单 4.29 绘制验证分数

```
plt.plot(range(1, len(average_mae_history) + 1), average_mae_history)
plt.xlabel("Epochs")
plt.ylabel("Validation MAE")
plt.show()
