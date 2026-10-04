

# 第 8 章 使用表格数据开启深度学习之旅

表 8.2 Keras 和 TabNet 解决方案的优缺点总结（续上）

| Keras | TabNet |
| --- | --- |
| 缺点 | 无对表格数据的内置支持，这意味着模型定义需要手动编写代码。没有一站式的总结语句来查看模型结构。 |
| | 训练过程慢得多。Keras 模型训练笔记本运行需约 20 秒，而 Tab-Net-ing 训练笔记本运行了超过 4 分钟。 |

在这一节中，我们回顾了针对 PyTorch TabNet 的 Airbnb 价格预测解决方案。在接下来的节中，我们将展示针对 Airbnb 问题的最终方案：结合 Lightning Flash 的 PyTorch。

# 8.4 结合 Lightning Flash 的 PyTorch

到目前为止，我们已经针对 Airbnb 价格预测问题考虑了 Keras、fastai 和 TabNet PyTorch 解决方案。现在，让我们转向最后一个技术栈堆栈：Lightning Flash。作为一个专为快速原原型设计、基准测试和微调设计的平台，具有清晰的 API 和卓越的文档，Lightning Flash 相比于我们目前探索的栈可能具有优势。

你可以在 https://mng.bz/Vknp 找到该解决方案的代码。图 8.13 显示了基于 PyTorch 的 fastai 和 TabNet 栈。

| PyTorch 生态系统 | PyTorch 生态系统 |
| --- | --- |
| 低层框架 | PyTorch |
| 高层 API | fastai |
| 表格数据库 | fastai | TabNet |

图 8.13 基于 PyTorch 的 fastai 和 TabNet 栈

# 8.4.1 Lightning Flash 解决方案的关键方面

Lightning Flash 解决方案的代码在许多方面与我们目前看到的解决方案不同。在这一节中，我们将通过浏览模型训练笔记本（https://mng.bz/4aDR），重点介绍该解决方案中最感兴趣的点。

# 结合 Lightning Flash 的 PyTorch

为了在 Colab 中运行 Lightning Flash 解决方案需要按照特定的顺序进行一系列安装，如 8.14 所示。该列表的来源是 https://mng.bz/QDP6。

# 8.14 在 Colab 中运行 Lightning 所需的安装

```
:pip install torch==1.8.1+cu102 -f https://download.pytorch.org/whl/torch_stable.html
:pip install vision==0.9.0
:pip install effectter
:pip install lightning-flash [image]
:pip install git+https://github.com/PyTorchLightning/lightning-flash.git
:pip uninstall fastai -y
curl https://raw.githubusercontent.com/airc/icevision/44b47c569423ba3f8c6ae5f605fb11leb/icevision/core/7record_components.py --output - /usr/local/lib/python3/dist/packages/icevision/core/record_components.py
```

- 一系列 pip 安装以获取所需的 PyTorch Lightning 层。
- 为了消除 fastai 和 Lightning Flash 之间潜在的冲突，需要卸载 fastai。
- 手动对 icevision 当前版本中的一个 bug 应用修复。
- 8.14 包含了所有的列表安装（以及一个卸载），以确保 Lightning Flash 在 Colab 中运行。根据经验，我们知道这种非常特定的安装列表是必需的，否则 Lightning Flash 所需的库级别与 Colab 的默认库级别之间将产生冲突。

接下来，需要导入 Lightning Flash 需要的库。

# 8.15 Lightning Flash 要求的库导入

```
import torch
import flash
from flash.tabular import TabularClassificationData,
from flash.tabular import TabularClassifier
```

- 导入 torch 张量库
- 导入 flash 库
- 导入表格分类模型所需的对象

注意，列表 8.15 中的 torch 导入语句与你在 8.11 中为 TabNet 导入 torch 的相同。
接下来，我们定义用于训练模型的数据集参数。

# 8.16 设置数据集参数

```
dep_var = 'target'
cat=['neighbourhood_group','neighbourhood','room_type']
cont=['min_minutes','number_of_reviews',
'reviews_per_month','calculated_host_listings_count']
```

- 设置目标字段为训练模型将预测的值
- 定义分类特征列表
- 定义连续特征列表

# 第 8 章 使用表格数据开启深度学习之旅

列表 8.16 中的定义让你回想起 fastai 解决方案中的类似代码块（列表 8.3），在其中我们定义了目标特征以及分类和连续特征的列表。

接下来，我们使用刚刚定义的值来定义 `TabularClassificationData` 对象。该对象指定了我们用于训练模型的数据集的最小特征。

```
列表 8.17 定义 TabularClassificationData
```

```
datamodule = TabularClassificationData.from_csv(
categorical_fields=cat,
numerical_fields=cont,
target_fields='target',
train_file='../data/train.csv',
val_file='../data/val.csv',
predict_file='../data/test.csv',
batch_size=64)
```

- 定义分类特征
- 定义连续特征
- 定义目标特征
- 定义训练数据集
- 定义验证数据集
- 定义测试数据集

我们应该解释为什么 `TabularClassificationData` 的定义在训练、验证和测试数据集上是分开的，因为 8.17 所示的 Lightning 解决方案使用了来自 mng.bz/Xx9 的 pickle 文件中的不同的 CSV 文件。作为练习，我们可以更新 8.17 所示的 `TabularClassificationData` 定义，使其使用三个独立的 CSV 文件而不是单个 pickle 文件。
现在我们已经指定了数据集的细节，准备好定义并训练模型，如下：

```
列表 8.18 设置数据集参数
```

```
model = TabularClassifier.from_data(datamodule,
learning_rate=0.1)
trainer = flash.Trainer(max_epochs=3,
gpus=torch.cuda.device_count())
trainer.fit(model, datamodule=datamodule)
```

- 使用 `TabularClassifier` 对象定义模型
- 定义 Trainer 对象
- 拟合模型

# 结合 Lightning 的 PyTorch

Lightning 的训练代码在 8.14 中生成输出。

```
INFO: pytorchlightning.accelerators.cuda:LOCAL_RANK: 0 - CUDA_VISIBLE_DEVICES: []
INFO: pytorchlightning.callbacks.model_summary:
| Name | Type | Params |
|0 train_metrics | ModuleDict | 0 |
1 val_metrics | ModuleDict | 0 |
2 test_metrics | ModuleDict | 0 |
3 adapter | PyTorchAdapter | 12.7 K |

12.7 K Trainable params
0 Non-trainable params
12.7 K Total params
0.051 Total params size (MB)
Epoch 2:100%
611/611 [00:19:00,31.67/s,loss=0_481,v_num=3,train_loss=0.456,valid_loss=0.461,valid_accuracy=0.710,train_accuracy=0.698] reached.
```

图 8.14 Lightning 训练过程输出

![](img/def89cc476fa39f4c54bd34e78d91674_341_0.png)

注意输出包含了模型的验证准确率和训练准确率。本节示例中的表格数据栈。

Lightning 解决方案的代码整合了一些非常优雅的想法，例如在定义数据集整体特征的同一个对象中指定训练、验证和测试数据集。Lightning 的 API 易于理解。遗憾的是，由于 Lightning Flash 在 Colab 中运行需要特定的要求，这些优势被削弱了。否则，考虑到 fastai 的简单性和 Keras 的直观性，Lightning Flash 可能会成为首选。

图 8.15 PyTorch 与 Lightning Flash 栈

# 8.4.2 Lightning 解决方案与 Keras 解决方案的比较

我们看到了针对 Airbnb NYC 列表问题的四种深度学习解决方案：Keras 解决方案、fastai 解决方案、TabNet 解决方案，最后是 Lightning Flash 解决方案。在这一节中，我们将 Keras 解决方案与 Lightning Flash 解决方案进行对比，并回顾两者的优缺点。
我们看到 Lightning Flash 在推出快速、简单的解决方案方面具有真正的优势。然而，在 Colab 中使用 Lightning Flash 缺乏成熟路径

