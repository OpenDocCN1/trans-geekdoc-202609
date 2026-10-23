
```python
apply_init(model[1], nn.init.kaiming_normal_)
```

我们可以检查模型是否包含两部分。

```python
len(model)
2
```

现在我们已经完成了模型，可以创建学习器了。但为了能够冻结我们的模型，我们必须使用一个默认分割器（default-splitter）将模型分成两组。第一组将被学习器冻结，只有在我们调用 unfreeze 后才会被训练。

```python
learner = Learner(dls, model,
    → loss_func=LabelSmoothingCrossEntropy(),
splitter=default_split,
metrics=error_rate)
```

```python
learner.freeze()
```

如果我们现在调用 learner.summary()，会看到编码器已被冻结，而头部是可训练的。这会得到一定数量的可训练和不可训练参数：

```text
Total params: 12,295,208
Total trainable params: 1,686,272
Total non-trainable params: 10,608,936
```

现在我们可以寻找一个学习率并训练模型。

```python
learner.lr_find()
```

```text
SuggestedLRs(lr_min=0.00831763744354248,
lr_steep=0.0020892962347716093)
```

![](img/d5454da46c702784893ef8b0b539e5b9_187_0.png)

```python
learner.fit_one_cycle(5, slice(3e-2))
```

| 轮次 | 训练损失 | 验证损失 | 错误率 | 时间 |
|---|---|---|---|---|
| 0 | 2.159734 | 2.660265 | 0.214479 | 00:57 |
| 1 | 1.338896 | 1.042187 | 0.103518 | 00:57 |
| 2 | 1.162674 | 1.107470 | 0.103518 | 00:57 |
| 3 | 1.021449 | 0.929794 | 0.080514 | 00:57 |
| 4 | 0.922285 | 0.905211 | 0.067659 | 00:57 |

## 模型架构

```python
learner.save('11-stage-1')
Path('models/11-stage-1.pth')
```

训练 EfficientNet 模型最困难的部分之一，就是弄清楚如何找到一个不会破坏一切的正确学习率，因此要谨慎选择，并且始终比你在解冻后想要使用的学习率略低一些。

我们勉强落后于 Resnet34。这意味着我们的 efficientNet 无法超越 ResNet，但我们现在使用的模型只有 Resnet34 模型大小的 57%——所以其实还不错！

## 13.1 预训练 PKL 文件

但如果我们没有这样功能丰富的库，只有 pkl 文件，我们该如何进行同样的权重迁移呢？

例如，你想进行两次迁移学习。你已经训练了一个能够识别不同犬种的模型。基于这个模型，你想创建一个能进行二分类的模型，用来判断一张狗的图像是否显示的是比特犬。

我们想使用犬种分类器的权重，因为它在二分类上也会表现得更好。

现在我们以预训练模型开始，尝试在其上运行 ImageWoof 数据集。

让我们首先获取 ImageWoof 数据：

```python
path = untar_data(URLs.IMAGEWOOF)
tfms = [[PILImage.create],
[parent_label, Categorize()]]
item_tfms = [ToTensor(), Resize(128)]
batch_tfms = [FlipItem(),
RandomResizedCrop(128, min_scale=0.35), IntToFloatTensor(),
Normalize.from_stats(*imagenet_stats)]

items = get_image_files(path)
split_idx = GrandparentSplitter(valid_name='val')(items)
datasets = Datasets(items, tfms, splits=split_idx)
dls = datasets.dataloaders(after_item=item_tfms,
after_batch=batch_tfms,
bs=64)
dls.show_batch()
```

我们开始的方式与之前完全相同：
- 创建模型的主体
- 创建模型的头部
- 拼接主体和头部
- 应用初始化值
- 创建学习器

## n02093754

## n02096294

## n02115641

## n02093754

## n02115641

## n02088364

## n02089973

## n02093754

## n02105641

![](img/d5454da46c702784893ef8b0b539e5b9_189_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_5.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_6.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_7.png)

![](img/d5454da46c702784893ef8b0b539e5b9_189_8.png)

```python
body = create_timm_body('efficientnet_b3a', pretrained=False)
head = create_head(3072, dls.c)
model = nn.Sequential(body, head)
apply_init(model[1], nn.init.kaiming_normal_)

learner = Learner(dls, model,
loss_func=LabelSmoothingCrossEntropy(), splitter=default_split,
metrics=accuracy)
```

现在我们的权重只包含随机权重。

*严格来说，并不仅限于随机值，而是来自统计分布的值（想了解 Kaiming 初始化的原理，请查看这个链接：https://towardsdatascience.com/understand-kaiming-initialization-and-implementation-detail-in-pytorch-f7aa967e9138。*

但我们想加载之前模型的权重。如果我们只通过调用 load 来加载它们，就会遇到大小不匹配错误。

## 模型架构

模型的所有权重都存储在模型的 state_dict 中。我们使用一个 transfer_learn 函数，传入学习器、预训练模型权重的名称，以及我们想要使用的设备。

对于 fastai 模型，我们通常也会存储优化器。因此我们可能需要索引到模型中：

```python
new_state_dict = torch.load(model_path,
→ map_location=device)['model']
```

接下来，我们将检查所有层，看这些层是否匹配。如果匹配，我们就把当前状态字典中的所有权重复制到新模型的状态字典中。

最后要做的是将迁移后的状态字典加载到我们的新模型中：learn.model.load_state_dict(learn_state_dict)

```python
def transfer_learn(learn:Learner, name:Path,
→ device:torch.device=None):
"Load model `name` from `self.model_dir` using `device`, \ defaulting to `self.dls.device`."
if device is None: device = learn.dls.device
learn.model_dir = Path(learn.model_dir)
if (learn.model_dir/name).with_suffix('.pth').exists():

model_path = (learn.model_dir/name).with_suffix('.pth')
else:
model_path = name
new_state_dict = torch.load(model_path,
→ map_location=device)['model']
learn_state_dict = learn.model.state_dict()
for name, param in learn_state_dict.items():
```

```python
learner = Learner(dls,

model,
loss_func=LabelSmoothingCrossEntropy(), splitter=default_split,
metrics=accuracy)
```

```python
learner.freeze()
learner.fit_one_cycle(5, 3e-3)
```

| 轮次 | 训练损失 | 验证损失 | 准确率 | 时间 |
|---|---|---|---|---|
| 0 | 2.863151 | 2.840038 | 0.124459 | 00:31 |
| 1 | 2.707900 | 3.295326 | 0.106643 | 00:31 |
| 2 | 2.569036 | 2.880788 | 0.125986 | 00:31 |
| 3 | 2.471119 | 2.462975 | 0.141257 | 00:31 |
| 4 | 2.438831 | 2.446061 | 0.146602 | 00:31 |

**哇！这个学习器只有大约 15% 的准确率，而迁移学习器却有大约 90%！** 这是迁移学习的巨大成功！

## 第14章

### 关键点检测

关键点和姿态检测（Keypoint and Pose Detection）试图在人物图像上找到特定位置。我们使用回归来完成这个任务。因此，如果我们想要检测 n 个关键点，就必须使用具有 n 个输出的 CNN。

```python
import os
!pip install q feather-format kornia pyarrow wandb nbdev → fastprogress fastai2 fastcore -upgrade
!pip install Pillow==6.2.1 -upgrade
```

Collecting Pillow==6.2.1 manylinux1_x86_64.whl (2.1 Attempting uninstall: Pillow Uninstalling Pillow-7.0.0: Successfully uninstalled Pillow-7.0.0 Successfully installed Pillow-6.2.1

```python
from fastai.basics import *
from fastai.vision.all import *
from fastai.callback.all import *
```

Using cached MB) Installing

Found existing

Pillow-6.2.1-cp37-cp37mcollected packages: Pillow installation: Pillow 7.0.0

### 14.1 数据集

和往常一样，我们首先看一下要使用的数据集。我们使用的是来自 Kaggle 的猫数据集，你可以在以下网址找到：https://www.kaggle.com/crawford/cat-dataset

> 该数据集“包含超过 9,000 张猫图像。每张图像都有猫头部的注解，包含九个点：两个用于眼睛，一个用于嘴，六个用于耳朵。”

这个数据集包含了猫脸上不同关键点的位置：

> 注释数据存储在一个文件中，文件名为对应图像的名称加上末尾的“.cat”。每张猫图像对应一个注释文件。对于每个注释文件，注释数据按以下顺序存储：

- 点的数量（默认是 9）
- 左眼
- 右眼
- 嘴
- 左耳-1
- 左耳-2
- 左耳-3
- 右耳-1
- 右耳-2
- 右耳-3
