
# 机器学习中级教程

## 鸣谢

特别感谢 Austin Kodra 的编辑。

## TensorFlow 和 Google Colab 用户的 10 个技巧

Google 的 Colab 是机器学习领域一个真正创新的产品。它让机器工程师能够运行 `Notebooks` 并轻松地与同事共享。另一个关键优势是可以访问 `GPUs` 和 `TPUs`。在本文中，我们将重点介绍一些帮助您充分利用 Google Colab 的提示和技巧。

### 10. 指定 TensorFlow 版本

很快，Colab 中默认的 `TF` 版本将变为 `TF 2`。这意味着，如果您有在 `TF 1` 中运行的 `Notebooks`，它们可能会失败。为了确保您的代码不会崩溃，建议在所有的 `Notebooks` 中都指定 `TF` 版本。这样，即使默认版本发生变化，您的 `Notebooks` 仍然可以工作 ![](img/rsrc14K.jpg)

### 9. 使用 TensorBoard

Google Colab 默认支持 `TensorBoard`。这是一个可视化模型性能的绝佳工具。用上它吧！![](img/rsrc14M.jpg)

### 8. 在 Colab 上训练 TFLite 模型

在构建移动机器学习模型时，您可以利用 `Colab` 的资源来训练模型。替代方案是使用其他昂贵的云解决方案或在您的笔记本电脑上训练模型，而笔记本电脑可能没有所需的计算能力。

### 7. 使用 TPUs

如果您的模型需要更强大的处理能力，请将默认运行时更改为 `TPU`。但是，只有在确实需要时才应使用 `TPUs`，因为它们的可用性是有限的 ![](img/src14N.jpg)

### 6. 使用本地运行时

如果您有自己的硬件加速器，`Colab` 允许您连接到它。只需点击下拉并选择您的首选运行时 ![](img/rsrc14P.jpg)

### 5. 使用 Colab 草稿板

有时您可能会发现自己想要快速测试某些东西。与其创建一个不打算保存到硬盘的新 `Notebook`，您可以使用不保存到硬盘的空 `Notebook`。

### 4. 将数据复制到 Colabs

为了加速数据的加载，建议将数据文件复制到 `Colab` 的 `VM` 中，而不是从其他地方加载。

### 3. 检查内存和资源限制

由于 `Colab` 的资源是免费的，这意味着它们并不保证可用。因此，请关注 `RAM` 和 `Disk` 的使用，以防耗尽资源 ![](img/src14R.jpg)

### 2. 完成后关闭标签页

关闭标签页可以断开 `VM` 并节省资源。

### 1. 仅需要时使用 GPUs

由于这些资源受到限制，在确实需要时才节省 `GPU` 使用。但是，如果您需要在没有免费版限制的情况下使用 `Colab`，可以查看专业版。希望这些 `Colab` 技巧对您有用。

机器学习的进步带来了巨大的数据隐私问题。当从手机等设备获取的数据训练机器学习模型时，这一点尤其如此。因此，大问题是在不共享数据的情况下训练和改进这些设备模型？我们将在联邦学习技术中寻求答案。

## 集中式机器学习

机器学习模型的传统过程是将数据上传到服务器并使用其进行训练。只要数据隐私不是问题，这种训练方式就是行的。然而，当涉及个人身份数据的机器学习时（设备端或医疗等敏感数据行业），这种方法变得不再适用。在集中服务器上训练模型意味着您需要大量的存储空间以及世界级的安全性来防止数据泄露。但想象一下，如果可以使用本地存储在用户设备上的数据来训练模型。

## 去中心化数据上的机器学习：联邦学习

联邦学习是一种允许设备从共享模型进行协作学习的模型训练技术。共享模型首先在服务器上使用代理数据进行训练。然后每个设备下载模型并使用设备上的联邦数据对其进行改进。设备使用本地可用数据训练模型。对模型的更改总结为 `update`，发送到云端。训练数据和个体更新留在设备上。为了确保更快地上传这些更新，模型使用了旋转和量化。当设备将特定模型发送到服务器时，会对模型进行平均处理以获得单个组合模型。通过多次迭代，直到获得高质量的模型 ![](img/src14S.jpg)

与集中式机器学习相比，联邦学习有几个优势：

- **确保隐私**，因为数据留在用户设备上。
- **低延迟**，因为更新的模型可以在设备上进行预测。
- **更智能的模型**，考虑到协作训练过程。
- **更低功耗**，因为模型是在用户设备上训练的 ![](img/src14T.jpg)

为了确保应用程序的用户体验不受影响，模型训练会在用户设备连接 WiFi、空闲且连接电源时进行 ![](img/src14U.jpg)

## TensorFlow Federated

TensorFlow 通过利用自己的框架实现了联邦学习的应用。[TensorFlow Federated (TFF)](https://www.google.com/url?q=https://www.tensorflow.org/federated&sa=D&ust=1597504082156000&usg=AOvVaw3rA-I6vkJUB3w) 是用于去中心化数据机器学习和其他计算的开源框架。`TFF` 有两个层：`Federated Learning (FL) API` 和 `Federated Core (FC) API`。`Federated Learning (FL) API` 允许开发者对现有模型应用联邦训练和评估。`Federated Core (FC) API` 是联邦学习的核心基础。它是一个低级接口系统，用于在强类型函数编程环境中结合分布式通信操作编写联邦算法。

联邦学习的一个应用示例是 [Google 的 Gboard 键盘](https://www.google.com/url?q=https://arxiv.org/abs/1811.03604&sa=D&ust=1597504082157000&usg=AOvVaw3lI8ivtKHUG898GY4gy)。在这种情况下，使用去中心化的设备上数据集训练了一个循环神经网络语言模型。其目标是预测手机键盘上的下一个单词 ![](img/src14V.jpg) 使用去中心化的设备上数据集训练模型，证明了在设备上使用联邦平均算法优于基于服务器的随机梯度下降。当设备将特定模型发送到服务器时，会对模型进行平均处理以产生一个新的全局模型。在这种情况下，由于联邦学习的使用，设备上训练产生新的波并增加了数据隐私。联邦学习的使用导致了 Gboard 单词预测准确率提升了 24%。这意味着在使用 Gboard 时，用户现在可以看到更多相关的表情和 GIF。希望这能激活你对联邦学习的兴趣。

## 使用 Dask 在本地机器上处理大型数据集

在笔记本电脑上处理几个 GB 的数据通常是一项艰巨的任务，除非笔记本电脑有高内存和计算力。尽管如此，数据科学家仍然需要寻找替代方案来解决这个问题。一些技巧包括调整 `Pandas` 以处理大型数据集、购买 `GPU` 机器或在云端购买计算力。在本文，我们将看到如何使用 [Dask](https://www.google.com/url?q=https://dask.org/&sa=D&ust=1597504082158000&usg=AOvVaw2mb0ovHJrap) 在本地机器上处理大型数据集。

### Dask 和 Python

`Dask` 是一个用于 Python 并行计算的灵活库。它旨在与 `NumPy`、`Pandas` 和 `scikit-learn` 等开源项目良好集成。在 `Dask` 中，`Dask arrays` 等同于 `NumPy Arrays`，`Dask DataFrames` 等同于 `Pandas DataFrames`，`Dask-ML` 等同于 `scikit-learn`。这些相似性使得将 `Dask` 引入您的工作流变得非常容易。使用 `Dask` 的优势可以将计算扩展到计算机的多个核心。这允许您处理无法放入内存的数据集。它还有加速通常需要很长时间计算的作用 ![](img/src14W.jpg)

### Dask DataFrames

加载大数据时，`Dask` 通常读取数据的样本以推断数据类型。为了避免类型错误，预先声明数据类型是良好的做法。`Dask` 能够通过 `blocksize` 参数将文件切分来加载大型文件。

```python
data_types = {'column1': str, 'column2': float}
df = dd.read_csv("data.csv", dtype=data_types, blocksize=64000)
``` ![](img/src14X.jpg)

`Dask DataFrame` 中的命令大部分与 `Pandas` 中的相似。例如，获取 head 和 tail 是：

```python
df.head()
df.tail()
```

`DataFrame` 上的函数是延迟执行的。这意味着在调用 `compute()` 之前它们不会计算。由于数据是分区加载的，某些 `Pandas` 函数如 `sort_values()` 将失败。解决方法是使用 `nlargest()` 函数。

```python
df.isnull().sum().compute()
```

### 集群

并行计算是 `Dask` 的关键，因为它允许在多个核心上运行计算。`Dask` 提供了一个在单机上运行的调度器。它不可扩展。它还提供可以扩展到多台机器的分布式调度器。

### 使用 dask.distributed

即使在单机上使用 `dask.distributed` 也有好处，因为它通过仪表板提供了某些诊断功能。如果您打算使用 `dask.distributed`，这应该是您做的第一件事。

```python
from dask.distributed import Client
client = Client()
``` ![](img/src14Y.jpg)

### Dask ML

`Dask` 还允许您以并行方式进行机器学习和预测。`dask-ml` 的目标是提供可扩展的机器学习。当您在 `scikit-learn` 中声明 `n_jobs = -1` 时，您可以并行运行计算。这是通过 `joblib` 实现的，该包允许 Python 中的并行化和流水线化。使用 `Dask ML`，您可以实现 `scikit-learn` 模型以及如 `Xgboost` 等其他库。这就是一个简单实现的样子。

```python
from dask_ml.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(verbose=1)
# 然后您必须导入 joblib 以启用并行计算。
from sklearn.externals.joblib import parallel_backend
with parallel_backend('dask'):
    model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### 限制和内存使用

`Dask` 中的单个任务无法并行运行。工作节点是 Python 进程，继承了 Python 计算的所有优点和缺点。在分布式环境中工作时也应注意数据安全和隐私。`Dask` 有一个中心调度器跟踪工作节点和集群上的数据。该调度器还控制从集群释放数据。一旦任务完成，它就会从内存中清除以释放内存。如果某些客户端需要它对于持续计算很重要，它将留在内存中。

另一个 Dask 的限制是它没有实现 `Pandas` 的所有函数。`Pandas` 接口很大，因此 `Dask` 没有完整实现。这意味着在 `Dask` 上尝试某些操作可能是困难的。此外，在 `Pandas` 中很慢的操作在 `Dask` 中也很慢。

### 你不需要 Dask DataFrame

在以下情况下，您可能不需要 `Dask`：

- 当您需要 `Dask` 尚未实现的 `Pandas` 函数时。
- 当您的数据完美适应计算机内存时。
- 当数据不是表格格式时。在这种情况下，尝试 `dask.bag` 或 `dask.array`。

在本文中，我们看到了如何使用 `Dask` 在本地机器或分布式方式处理大型数据集。我们看到由于其熟悉的语法和扩展能力，我们可以使用 `Dask`。它具有扩展到数千个核心的能力。

```python
image = skimage.io.imread(os.path.join(IMAGE_DIR, 'animals.jpg'))
```

准备好后，我们现在可以运行预测：

```python
results = model.detect([image], verbose=1)
```

可视化结果非常直观：

```python
r = results[0]
visualize.display_instances(image, r['rois'], r['masks'], r['class_ids'], class_names, r['scores'])
``` ![](img/rsrc151.jpg)

如你所见，非常简单。然而，此实现与[官方论文](https://www.google.com/url?q=https://arxiv.org/abs/1703.06870&sa=D&ust=1597504082180000&usg=AOvVaw0a04z1zEOVwzkHyS7LAUcm) 有几处不同：

- 将所有图像缩放到相同大小，以支持每批次训练多个图像。在官方论文中，缩放方式是保持最短边为 800px，最长边被裁剪为 1000px。
- 忽略数据集中自带的边界框，以便动态生成它们。
- 使用了比论文中建议的 0.02 更低的学习率。较低的学习率收敛更快。

由于我对 GitHub 上的原始代码进行了一些微调，因此[提供了本文中使用的源代码](https://www.google.com/url?q=https://bitbucket.org/mwitiderrick/mask-r-cnn/src/master/Mask%2520R-CNN/&sa=D&ust=1597504082181000&usg=AOvVaw31BUuyMko-5n0rcVwnFB0O)。

如你所见，Matterport 提供了一种使用 Mask R-CNN 实现图像分割的快速简单方法。如果你想对图像进行自己的训练，请查看他们 GitHub 页面上的这个 [Notebook](https://www.google.com/url?q=https://github.com/matterport/Mask_RCNN/blob/master/samples/shapes/train_shapes.ipynb&sa=D&ust=1597504082181000&usg=AOvVaw2xmJgJqhGPmxmKwUMppML1)。你也可以查看我关于图像分割的其他文章。

## LightGBM 算法详解

LightGBM 算法的力量不容小觑（双关语在此）。LightGBM 是一种分布式的且高效的[梯度提升框架](https://www.google.com/url?q=https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html&sa=D&ust=1597504082182000&usg=AOvVaw2rHXMUsu4pnWCYCseG2HiI)，使用了基于树的学习。它是[基于直方图的](https://www.google.com/url?q=https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.HistGradientBoostingClassifier.html&sa=D&ust=1597504082183000&usg=AOvVaw2XOsw3E2ze6BA)，将连续值放入离散桶中，从而导致更快的训练和更高效的内存使用。在本文，我们将深入探讨 LightGBM。

### 优势

根据官方文档，LightGBM 的优势如下：

- 更快的训练速度
- 更低的内存占用
- 更好的准确率
- 支持并行和 GPU 学习
- 能够处理大规模数据

### 参数调优

该框架使用叶优先（leaf-wise）生长算法，与其他许多使用深度优先（depth-wise）成长的树算法不同。叶优先树算法比深度优先的收敛更快。然而，它们往往更容易过拟合。 (rsrc51.jpg)

为了获得良好的结果，我们需要调优以下参数：

- `num_leaves`: 将叶节点数设置为 `2^(max_depth)` 会给你与深度优先树相同的叶节点数。然而，这并不是良好的做法。
- `min_data_in_leaf`: 取值取决于 `num_leaves` 和训练样本，防止过拟合。对于大型数据集，可以设置为数百或数千。
- `max_depth`: 限制树的深度。
- `save_binary`: 为了加速数据加载。
- `bagging`, `bagging_freq`: 通过设置 `bagging_freq` 进行并行学习。
- `feature_fraction`: 采样。为了获得更好的准确率，可以使用较大的 `max_bin`、较小的 `learning_rate` 并使用 `num_iterations`。此外，人也可以使用许多 `num_leaves`，但可能会导致过拟合。
- `path_smooth`: 使用较大的训练集。
- `lambda_1`, `lambda_2`, `min_gain_to_split`:

### 类别特征

机器学习中处理类别特征的常用方法是独热编码（one-hot encoding）。这种方法对于树学习并不是最优的，基于独热编码构建的树是不平衡的且长得太深。使用 `categorical_feature` 属性，我们可以指定类别特征（无需独热编码）。它们应该从零开始。

### 应用

LightGBM 最适用于以下问题：

- 使用 `logloss` 目标函数的二分类分类
- 使用 `L2 loss` 的回归
- 使用 `logloss` 目标函数的多分类



- 使用 `lambdarank` 目标函数的 LambdaRank

## 指标

LightGBM 支持的指标有：

- L1 loss、L2 loss、Log loss、错误率、AUC、NDCG、MAP、多类 log loss、多类错误率、Fair、Poisson、Quantile、MAPE、Kullback-Leibler、Tweedie

默认情况下，LightGBM 能够处理缺失值。可以通过设置 `use_missing=false` 禁用。它使用 `NA` 表示缺失，但为了使用零，你可以设置 `zero_as_missing=true`。

## 核心参数

以下是 LightGBM 的一些核心参数：

- `task`: 默认训练。其他选项有 `predict`、`convert_model` 和 `refit`。该参数的别名是 `task_type`。
- `convert_model`: 将模型转换为 if-else 格式。
- `objective`: 默认回归。其他选项有 `regression_1`、`huber`、`fair`、`poisson`、`quantile`、`mape`、`gamma`、`tweedie`、`binary`、`multiclass`、`multiclass_ova`、`cross_entropy`、`cross_entropy_lambda`、`lambdarank` 和 `rank_xend`。该参数的别名是 `objective_type`、`app` 和 `application`。
- `boosting`: 默认 `gdt` —— 传统的梯度提升决策树。其他选项有 `rf` —— 森林、`dart` —— Dropout 多加回归树、`goss` —— 基于梯度的单侧采样。该参数的别名是 `boosting_type` 和 `boost`。
- `num_leaves`: 基础学习器的最大叶节点数——默认 31。
- `max_depth`: 基础学习器的最大树深度。
- `learning_rate`: 学习率。
- `n_estimators`: 拟合的提升树数量——默认 200000。
- `importance_type`: 填充 `feature_importances_` 的重要性类型。使用 `split` 意味着特征在模型中的次数将包含在结果中。
- `device_type`: 树学习设备——CPU 或 GPU。可以使用 `device` 作为别名。

## 学习控制参数

以下是几个学习控制参数：

- `force_col_wise`: 设置为 true 时，强制按列构建直方图。当列数较多或总桶数很大时，建议将其设置为 true。当你想要减少内存成本且 `num_threads` 很大时（例如大于 20）时，也可以将其设置为 true。此参数仅供 CPU 使用。
- `force_row_wise`: 设置为 true 时，强制按行构建直方图。此参数仅供 CPU 使用。当数据点很多、总桶数较小且 `num_threads` 较小（例如小于等于 16）时，可以开启。当你想要使用较小的 `bagging_fraction` 或 `goss` Boosting 来加速训练时，也可以设置为 true。
- `neg_bagging_fraction`: 用于不平衡分类问题。
- `bagging_freq`: bagging 的频率。零意味着禁用 bagging。
- `feature_fraction`: 可用于处理过拟合。例如设置为 0.5 意味着 LightGBM 在每个节点选择 50% 的特征。
- `extra_trees`: 当你想使用随机树时设置为 true。
- `early_stopping_round`: 设置为 true 时，一旦某个参数无法改进就会停止。
- `max_drop`: 默认值为 50。表示每次迭代丢弃的树的数量。
- `cat_l2`: 类别特征的 L2 正则化。
- `cat_smooth`: 减少类别特征中的噪声，特别是对于数据有限的情况。
- `categorical_feature`: 类别特征。

## 目标参数

注意以下几个目标参数：

- `is_balance`: 如果训练数据不平衡，可以设置为 true。
- `num_class`: 用于指示类别的数量。
- `scale_pos_weight`: 正类标签的权重。与 `is_balance` 一起使用可能会导致对个体概率的估计不良。

## 实际实现

我们现在来看算法的快速实现。我们将使用 scikit-learn 的包装器。我们从导入模型开始：

```python
from lightgbm import LGBMClassifier
```

下一步是创建模型实例并设置目标。选项有 `regression`、`binary` 或 `multiclass` 对于 `LGBMClassifier`。

```python
model = LGBMClassifier(objective='multiclass')
```

在拟合模型时，我们可以设置类别特征：

```python
model.fit(X_train, y_train, categorical_feature=[0, 3])
```

一旦在模型上运行预测，你也可以获得特征：

```python
predictions = model.predict(X_test)
importances = model.feature_importances_
```

剪枝是一种消除不必要的值的模型优化技术。在本文中我们将通过示例应用剪枝并查看其对最终模型大小的影响。

## 导入常规

我们的第一步是获取一些导入：

```python
import os
import tensorflow as tf
import tensorflow_model_optimization as tfmot
from tensorflow.keras.models import load_model
from tensorflow import keras
%load_ext tensorboard
```

这将帮助我们评估模型的大小。

## 数据集生成

对于这个实验，我们将使用 scikit-learn 生成回归数据集。随后将数据集分为训练集和测试集：

```python
from sklearn.datasets import make_friedman1
X, y = make_friedman1(n_samples=10000, n_features=10, random_state=0)
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)
```

## 未剪枝的模型

我们将创建一个简单的神经网络来预测目标变量 y。然后检查均方误差。之后，将其与整个剪枝后的模型以及仅剪枝的 Dense 层进行比较。

```python
def setup_model():
    model = keras.Sequential([
        keras.layers.Dense(units=128, activation='relu', input_shape=(X_train.shape[1],)),
        keras.layers.Dense(units=1, activation='relu')
    ])
    return model
```

接下来，我们设置一个回调，在模型停止改进后停止训练（30 个 epoch 后）。

```python
early_stop = keras.callbacks.EarlyStopping(monitor='val_loss', patience=30)
```

打印模型摘要以便与剪枝模型对比：

```python
model = setup_model()
model.summary()
```

![](img/rsrc54.jpg)

编译并训练模型。

```python
model.compile(optimizer='adam', loss=tf.keras.losses.mean_squared_error, metrics=['mae', 'mse'])
model.fit(X_train, y_train, epochs=300, validation_split=0.2, callbacks=early_stop, verbose=0)
```

由于是回归问题，我们正在监控平均绝对误差和均方误差。这是绘制模型模型。输入是 10，因为生成的数据集有 10 个特征。

```python
tf.keras.utils.plot_model(
    model, to_file="model.png", show_shapes=True, show_layer_names=True, rankdir="TB", expand_nested=True, dpi=96,
)
```

![](img/rsrc55.jpg)

现在检查均方误差。我们可以进入下一部分，看看当剪枝整个模型时它如何变化。

```python
from sklearn.metrics import mean_squared_error
predictions = model.predict(X_test)
print('Without Pruning MSE %.4f' % mean_squared_error(y_test, predictions.reshape(3300)))
```

未剪枝 MSE 0.0201

## 使用 ConstantSparsity 剪枝整个模型

将上述 MSE 与剪枝整个模型后获得的进行比较。第一步是定义剪枝参数。基于幅度的剪枝意味着在训练过程中某些权重被转换为零。模型变得稀疏，从而更容易压缩。稀疏模型推理更快。预期参数有：

- `pruning_schedule`: 在这种情况下，我们设置 50% 的稀疏度，意味着 50% 的权重将被归零。
- `block_size`: 块的大小。
- `block_pooling_type`: 块池化。必须为 `AVG` 或 `MAX`。

```python
from tensorflow_model_optimization.sparsity.keras import ConstantSparsity
pruning_params = {
    'pruning_schedule': ConstantSparsity(0.5, 0),
    'block_size': (1, 1),
    'block_pooling_type': 'AVG'
}
```

现在可以通过我们的剪枝参数来剪枝整个模型。

```python
from tensorflow_model_optimization.sparsity.keras import prune_low_magnitude
model_to_prune = prune_low_magnitude(
    keras.Sequential([
        keras.layers.Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
        keras.layers.Dense(units=1, activation='relu')
    ]), **pruning_params)
```

检查模型摘要。从下图中我们可以看到整个模型已被剪枝。

```python
model_to_prune.summary()
```

![](img/rsrc56.jpg)

在将其用于训练和测试集之前，我们必须编译模型。

```python
model_to_prune.compile(optimizer='adam', loss=tf.keras.losses.mean_squared_error, metrics=['mae', 'mse'])
```

由于我们正在应用剪枝，除了早停止回调外，我们还需要定义剪枝回调。定义文件夹来记录模型，然后创建一个列表。

```python
log_dir = '.models'

callbacks = [
    tfmot.sparsity.keras.UpdatePruningStep(),  # 记录稀疏和其他指标到 Tensorboard
    tfmot.sparsity.keras.PruningSummaries(log_dir=log_dir),
    keras.callbacks.EarlyStopping(monitor='val_loss', patience=10)
]
```

通过这种方式，我们现在可以将模型拟合到训练集。

```python
model_to_prune.fit(X_train, y_train, epochs=100, validation_split=0.2, callbacks=callbacks, verbose=0)
```

检查该模型的均方误差，我们注意到它比未剪枝的模型略高。

```python
prune_predictions = model_to_prune.predict(X_test)
print('Whole Model Pruned MSE %.4f' % mean_squared_error(y_test, prune_predictions.reshape(3300)))
```

整个模型 MSE 0.1830

## 使用 PolynomialDecay 剪枝计划仅剪枝 Dense 层

现在实现相同的模型——但这次我们只剪枝 Dense 层。注意剪枝计划中使用 `PolynomialDecay` 函数。

```python
from tensorflow_model_optimization.sparsity.keras import PolynomialDecay

layer_pruning_params = {
    'pruning_schedule': PolynomialDecay(initial_sparsity=0.2, final_sparsity=0.8, begin_step=1000, end_step=2000),
    'block_size': (2, 3),
    'block_pooling_type': 'MAX'
}
```

```python
model_layer_pruning = prune_low_magnitude(
    keras.Sequential([
        keras.layers.Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
        keras.layers.Dense(units=1, activation='relu')
    ]), **layer_pruning_params)
```

从摘要中，我们可以看到只有第一个 Dense 层将被剪枝。

```python
model_layer_pruning.summary()
```

![](img/rsrc57.jpg)

我们编译并拟合模型。

```python
model_layer_pruning.compile(optimizer='adam', loss=tf.keras.losses.mean_squared_error, metrics=['mae', 'mse'])
model_layer_pruning.fit(X_train, y_train, epochs=300, validation_split=0.1, callbacks=callbacks, verbose=0)
```

现在，检查均方误差。

```python
layer_une_predictions = model_layer_pruning.predict(X_test)
print('Layer Prunned MSE %.4f' % mean_squared_error(y_test, layer_une_predictions.reshape(3300)))
```

层剪枝 MSE 0.1388

由于我们使用了不同的参数，我们无法将此处获得的 MSE 与上一个进行比较。如果你想比较它们，请确保剪枝参数相似。

## 比较模型大小

现在让我们比较有剪枝和没有剪枝的模型大小。从训练并保存权重开始。

```python
def train_save_weights():
    model = setup_model()
    model.compile(optimizer='adam', loss=tf.keras.losses.mean_squared_error, metrics=['mae', 'mse'])
    model.fit(X_train, y_train, epochs=300, validation_split=0.2, callbacks=callbacks, verbose=0)
    model.save('models/friedman.weights')

train_save_weights()
```

我们设置基础模型并加载保存的权重。然后我们剪枝整个模型。编译、拟合模型，并在 Tensorboard 上可视化结果。

```python
base_model = setup_model()
base_model.load_weights('models/friedman.weights')

## 可选，但为了准确率
model_for_pruning = tfmot.sparsity.keras.prune_low_magnitude(base_model)
model_for_pruning.compile(loss=tf.keras.losses.mean_squared_error, optimizer='adam', metrics=['mae', 'mse'])
```



model_for_pruning.fit(X_train, y_train, callbacks=callbacks, epochs=300, validation_split=0.2, verbose=0)
%tensorboard --logdir={log_dir}

![](img/src158.jpg)

其他的剪枝摘要也可以在 Tensorboard 上查看。(rsrc159.jpg)

现在我们定义一个函数来计算模型的大小。

```python
def get_gzipped_model(model, mode_name, zip_name):
    # 返回压缩模型的大小（字节）。
    model.save(mode_name, include_optimizer=False)
    with zipfile.ZipFile(zip_name, 'w', compression=zipfile.ZIP_DEFLATED) as f:
        f.write(mode_name)
    return os.path.getsize(zip_name)
```

现在我们定义导出模型并计算大小。对于剪枝模型，使用 `tfmot.sparsity.keras.strip_pruning()` 来恢复原始稀疏权重。注意剥离和未剥离模型大小的差异。

```python
model_for_export = tfmot.sparsity.keras.strip_pruning(model_for_pruning)

print("Size of gzipped model without stripping: %.2f bytes" % (get_gzipped_model(model_for_pruning, '.models/for_pruning.h5', '.models/for_pruning.zip')))

print("Size of gzipped model with stripping: %.2f bytes" % (get_gzipped_model(model_for_export, '.models/for_export.h5', '.models/for_export.zip')))
```

未剥离压缩模型大小：6101.00 字节
剥离压缩模型大小：5140.00 字节

在对两个模型上运行预测，我们看到它们具有相同的均方误差。

```python
model_for_pruning_predictions = model_for_pruning.predict(X_test)

print('Model for Pruning Error %.4f' % mean_squared_error(y_test, model_for_pruning_predictions.reshape(3300)))

model_for_export_predictions = model_for_export.predict(X_test)

print('Model for Export Error %.4f' % mean_squared_error(y_test, model_for_export_predictions.reshape(3300)))
```

剪枝误差 0.0264
导出误差 0.0264

## 最后想法

你可以继续测试不同的剪枝计划如何影响模型大小。显然，这里的观察结果并不是通用的。你必须尝试不同的剪枝参数，并学习它们如何根据你的问题影响模型大小、预测误差和或准确率。为了进一步优化模型，你可以对其进行量化。如果你想探索这些更多，请查看[仓库](https://github.com/mwitiderrick/Pruning-in-TensorFlow) 和[资源](https://www.google.com/url?q=https://www.tensorflow.org/model_optimization/guide/pruning/comprehensive_guide)

## 特征选择

特征选择是任何机器学习应用的一项任务。当涉及的数据具有许多特征时，这尤为关键。最佳特征数量也可以提高模型准确率。获取最重要的特征和最佳特征数量可以通过特征重要性或特征排名获得。在本文中，我们将探索特征排名。

### 递归特征消除

递归消除所需的第一个项目是估计器；例如线性模型或决策树。这些模型在线性模型中具有系数，在决策树模型中具有重要性。在选择最佳特征数量时，训练估计器并通过系数或特征重要性选择特征。移除不重要的特征。这个过程递归进行，直到获得最佳特征数量。

### Sklearn 中的应用

Scikit-learn 可以通过 `sklearn.feature_selection.RFE` 实现递归消除。该类接受以下参数：

- `estimator`：一个可以通过 `coef_` 或 `feature_importances_` 提供重要性的机器学习估计器。
- `n_features_select`：要选择的特征数量。如果不指定，则为一半。
- `step`：每次迭代移除的特征数量，或者 0 到 1 之间的数字表示移除特征的百分比。

一旦拟合，可以获得以下属性：

- `ranking_`：特征排名。
- `n_features_`：已选择的特征数量。
- `support_`：表示特征是否被选择的数组。

### 应用

如前，我们需要与提供 `feature_importances_` 或 `coef_` 属性的估计器工作。通过快速示例。数据集有 13 个特征——我们将获取最佳特征数量。

```python
import pandas as pd

df = pd.read_csv('heart.csv')

df.head()
```

![](img/rsrc1A.jpg)

获取 X 和 y 特征。

```python
X = df.drop(['target'], axis=1)
y = df['target']
```

将其分为测试集和训练集以准备建模：

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
```

为了避免数据泄露，最佳实践是执行交叉验证：

```python
from sklearn.pipeline import Pipeline
from sklearn.model_selection import RepeatedStratifiedKFold
from sklearn.model_selection import cross_val_score
from sklearn.feature_selection import RFE
import numpy as np

pipe = Pipeline([('Feature Selection', rfe), ('Model', model)])

cv = RepeatedStratifiedKFold(n_splits=10, n_repeats=5, random_state=36851234)

n_scores = cross_val_score(pipe, X_train, y_train, scoring='accuracy', cv=cv, n_jobs=-1)

np.mean(n_scores)
```

第一步是创建 `RFE` 类实例，指定估计器和想要选择的特征数量。在这种情况下，我们选择 6：

```python
rfe = RFE(estimator=GradientBoostingClassifier(), n_features_select=6)
```

接下来，我们创建一个使用的模型实例：

```python
model = GradientBoostingClassifier()
```

我们将使用 `Pipeline` 中指定用于特征选择步骤的 `rfe` 和下一步使用的模型。然后我们指定具有 10 次划分和 5 次重复的 `RepeatedStratifiedKFold`。分层 K 折确保每个折中的样本数是平衡的。`RepeatedStratifiedKFold` 以指定的次数重复分层 K 折，每次重复都有不同的随机化。

```python
pipe = Pipeline([('Feature Selection', rfe), ('Model', model)])
```

下一步是将此流水线拟合到数据集。

```python
pipe.fit(X_train, y_train)
```

一旦完成，我们可以检查 `support_` 和排名。`support_` 表示特征是否被选择。

```python
rfe.support_
# array([ True, False, True, False, True, False, False, True, False, True, True, True])
```

我们可以将其放入 dataframe 并检查结果：

```python
pd.DataFrame(rfe.support_, index=df.columns, columns=['Rank'])
```

![](img/rsrc1B.jpg)

我们也可以检查相对排名。

```python
rf_df = pd.DataFrame(rfe.ranking_, index=df.columns, columns=['Rank']).sort_values(by='Rank', ascending=True)
rf_df.head()
```

![](img/rsrc1C.jpg)

### 自动特征选择

与其手动配置特征数量，如果我们可以自动选择它们就太好了。这可以通过递归特征消除和交叉验证来实现。这是通过 `sklearn.feature_selection.RFECV` 完成的。该类接受以下参数：

- `estimator`：与 `RFE` 类相同。
- `min_features_select`：选择的最少特征数量。
- `cv`：交叉验证策略。

返回的属性有：

- `n_features_`：通过交叉验证选择的最佳数量。
- `support_`：包含特征选择信息的数组。
- `ranking_`：特征排名。
- `grid_scores_`：从交叉验证中获得的分数。

第一步是导入该类并创建其实例。

```python
from sklearn.feature_selection import RFECV

rfecv = RFECV(estimator=GradientBoostingClassifier())
```

下一步是指定流水线和 `cv`。

```python
model = GradientBoostingClassifier()

pipeline = Pipeline([('Feature Selection', rfecv), ('Model', model)])

cv = RepeatedStratifiedKFold(n_splits=10, n_repeats=5, random_state=36851234)

n_scores = cross_val_score(pipeline, X_train, y_train, scoring='accuracy', cv=cv, n_jobs=-1)

np.mean(n_scores)
```

让我们拟合流水线，然后获得最佳特征数量。

```python
pipeline.fit(X_train, y_train)

print(rfecv.n_features_)
```

最佳特征数量：7。排名和支持可以像时间一样获得。

```python
rfecv_df = pd.DataFrame(rfecv.ranking_, index=df.columns, columns=['Rank']).sort_values(by='Rank', ascending=True)
rfecv_df.head()
```
