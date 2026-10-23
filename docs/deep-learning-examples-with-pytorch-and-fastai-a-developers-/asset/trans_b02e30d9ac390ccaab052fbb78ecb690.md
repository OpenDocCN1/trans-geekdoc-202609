
```
[Path('/home/bmayr/.fastai/data/adult_sample/models'),
Path('/home/bmayr/.fastai/data/adult_sample/export.pkl'),
Path('/home/bmayr/.fastai/data/adult_sample/adult.csv')]
```

我们想要使用的数据位于 adults.csv 文件中。让我们获取这些数据并将其传递到一个 DataFrame 对象中，然后查看一下。 df = pd.read_csv(path/'adult.csv')
df.head()

年龄 工作类别
0 49 私营企业
1 44 私营企业
2 38 私营企业
3 38 自雇(公司)
4 42 自雇(非公司) fnlwgt 教育程度 101320 大学副学士(转学) 236746 硕士 96185 高中毕业 112847
专业学校 82297 7-8年级 教育年限 婚姻状况 12.0 已婚(配偶在旁) 14.0 离异 缺失
离异 15.0 已婚(配偶在旁) 缺失 已婚(配偶在旁) 职业 家庭角色 种族 性别 资本收益 资本损失 每周工作小时数 国籍 薪水 缺失 妻子 白人 女性 0 1902
执行管理层 非家庭成员 白人 男性 10520 0
未婚 黑人 女性 0 0
丈夫 亚裔太平洋岛民 男性 0 0
妻子 黑人 女性 0 0
40 美国 >=50k 45 美国 >=50k 缺失
专业领域
其他服务
32 美国 <50k 40 美国 >=50k 50 美国 <50k

## 22.1 Tabular Pandas

fastai 库提供了一种处理表格数据的新方式。你可以使用 TabularPandas 对象。这使得 fastai 在表格数据上的使用更加便捷。
它需要一些数据帧、进程（procs）、分类变量名、连续变量名、目标变量名、目标变量块以及一些数据划分。我们将逐一介绍它们。

首先，我们需要获取分类变量和连续变量，以及我们想要如何处理数据的方式。

```python
cat_names = ['workclass', 'education', 'marital-status', 'occupation',
'relationship', 'race']
cont_names = ['age', 'fnlwgt', 'education-num']
```

这个 #na# 类别也包含在不同的列中，例如职业列。这个 #na# 基本上填补了数据中特定值缺失的位置。

```python
to.show(max_n=3)
```

```text
工作类别
0 私营企业
1 私营企业
2 私营企业 教育程度 婚姻状况 职业 家庭角色 种族

大学副学士(转学) 已婚(配偶在旁) #na# 妻子 白人 硕士
高中毕业
离异 执行管理层 非家庭成员 白人 离异 #na# 未婚
黑人
```

如果我们调用 cats ，我们可以看到所有嵌入的分类数据。 to.cats.head()

```text
工作类别 教育程度 婚姻状况 职业 家庭角色 种族
0 5 8 3 0 6 5
1 5 13 1 5 2 5
2 5 12 1 0 5 3
3 6 15 3 11 1 2
4 7 6 3 9 6 3
```

## 22.2 数据归一化

为了正确处理数值列，我们需要展示出它们之间可以帮助模型理解的关系。这通常通过归一化来完成，我们将数据缩放到 -1 和 1 之间，并计算 z 分数。

```python
norm = Normalize()
cont_names
['age', 'fnlwgt', 'education-num']
to = TabularPandas(df, norm, cont_names=cont_names)
norms = to.procs.normalize
```

数据 — 但这样看起来有点奇怪）：

```
to.conts.head()
```

```
年龄 fnlwgt 教育年限
0 49 101320 12.0
1 44 236746 14.0
2 38 96185 10.0
3 38 112847 15.0
4 42 82297 10.0
```

如果我们现在查看分类变量名称，我们会发现多了一个额外的列教育年限_na。这是我们之前提到的由 FillMissing 生成的额外布尔列。

```
to.cat_names
```

```
(#1) ['education-num_na'] to.cats.head()
```

```
教育年限_na
0 False
1 False
2 True
3 False
4 True
```

## 22.4 数据加载器（DataLoaders）

现在我们可以定义我们的数据加载器了。我们需要分割数据并声明我们的目标变量名称。我们使用 DataFrame 中的 range_of 函数。这个函数返回数据帧中的所有索引列表，我们可以将其传入我们的 RandomSplitter。

```
splits = RandomSplitter()(range_of(df))
splits
((#26049) [2306,19921,9386,24488,10147,12102,4127,148,21552,554...],
(#6512) [26356,28927,6605,14197,15965,23886,6892,28781,10153,4823...])
```

我们获取分类变量和连续变量以及我们的预处理器。我们声明 Categorify、FillMissing 和 Normalize。这些按照给定的顺序实现。

我们还需要目标值（我们要预测的变量）的名称，在我们的案例中是薪水列。对于目标值，我们定义一个类别块。

```
cat_names = ['workclass', 'education', 'marital-status', 'occupation', 'relationship', 'race']
cont_names = ['age', 'fnlwgt', 'education-num']
procs = [Categorify, FillMissing, Normalize]
y_names = 'salary'
y_block = CategoryBlock()
```

声明了所有这些值后，我们可以创建 TabularPandas：

```
to = TabularPandas(df, procs=procs, cat_names=cat_names, cont_names=cont_names, y_names=y_names, y_block=y_block, splits=splits)
```

现在我们一切就绪，可以构建数据加载器了。我们可以用两种方式构建数据加载器。要么使用完整数据，要么使用两个数据加载器分别用于训练和验证数据。

### 首次尝试：只使用一个数据加载器：

我们只需调用 dataloaders 并查看一个随机批次。 dls = to.dataloaders() dls.show_batch()

工作类别
0 私营企业
1 私营企业
2 私营企业
3 私营企业
4 私营企业
5 私营企业
6 私营企业
7 私营企业
8 ?
9 联邦政府 教育程度 学士 10年级
高中毕业 大学在读 大学在读 已婚(配偶在旁) 大学在读 高中毕业 高中毕业 学士
高中毕业 婚姻状况 已婚(配偶在旁) 分居
未婚 分居
未婚 未婚 已婚(配偶在旁) 已婚(配偶在旁) 未婚 职业

执行管理层 行政文员 手工艺修理
机器操作检查 技术支持 手工艺修理
手工艺修理
运输搬运 ?
其他服务 家庭角色 种族 教育年限_na 年龄 fnlwgt 教育年限 薪水 丈夫 白人
False 34.000000 158419.999201 13.0 <50k 未婚 白人 False 38.000000 150601.000243 6.0
<50k 非家庭成员 白人 False 56.000000 261232.001670 9.0 <50k 非家庭成员 黑人 False
44.000000 721160.993845 10.0 <50k 丈夫 黑人 False 52.000000 321958.996919 10.0 >=50k
其他亲属 白人 False 30.000000 158002.000589 10.0 <50k 非家庭成员 白人 False 24.000001
162282.000054 9.0 <50k 丈夫 黑人 False 24.000001 291407.000489 9.0 <50k 丈夫 白人
False 63.000001 83042.997601 13.0 <50k 亲生子女 黑人 False 32.000000 249409.001923 9.0 <50k

### 第二次尝试：创建两个数据加载器用于训练和验证：

我们也可以创建两个 DataLoaders（一个用于训练，一个用于验证）。

我们更喜欢这种实现方式的一个很重要的原因是**我们可以为每个 TabDataLoader 传入不同的批次大小**，同时可以更改诸如 shuffle 和 drop_last 等选项（在底部我会展示为什么这非常酷）。

那么如何使用它呢？

我们的训练和验证数据目前存在于 to.train 和 to.valid 中。所以我们指定这些以及我们的选项。当你制作训练 DataLoader 时，你希望 shuffle 为 True，drop_last 为 True。这样最后一个不完整的批次将被丢弃。

对于验证数据加载器，我们使用 to.valid 中的所有数据，并使用更大的批次大小 128（因为我们的数据较少，可以更快地遍历）。我们不进行随机打乱，并保留最后较小的批次。

然后我们只需调用 DataLoaders 并传入我们的两个数据加载器。

```
trn_dl = TabDataLoader(to.train, bs=64,
shuffle=True, drop_last=True)
val_dl = TabDataLoader(to.valid, bs=128)
```

```
dls = DataLoaders(trn_dl, val_dl)
dls.show_batch()
```

工作类别 教育程度 婚姻状况 职业 家庭角色 种族 教育年限_na 年龄 fnlwgt 教育年限 薪水

0 私营企业
1 私营企业
2 私营企业
3 私营企业
4 私营企业
5 私营企业
6 私营企业
7 自雇(公司)
8 联邦政府
9 地方政府 11年级
高中毕业
学士 学士 学士 大学在读 学士 学士 高中毕业
高中毕业
已婚(配偶在旁) 已婚(配偶在旁) 分居
已婚(配偶在旁) 离异
分居
未婚 已婚(配偶在旁) 未婚 已婚(配偶在旁) 其他服务 手工艺修理 销售
销售
保护性服务 销售
销售
执行管理层 机器操作检查 保护性服务 丈夫 美洲印第安/爱斯基摩人 False 47.000000
157900.998506 7.0 <50k 丈夫 白人 False 47.000000 198901.000079 9.0 <50k 未婚 白人
False 41.000000 173369.999937 13.0 <50k 丈夫 白人 False 39.000000 129596.997458 13.0 <50k
非家庭成员 黑人 False 32.000000 155232.000523 13.0 >=50k 未婚 白人 False 21.999999
203181.999300 10.0 <50k 非家庭成员 白人 False 33.000000 284530.999371 13.0 <50k 丈夫
白人 False 59.000000 223214.998492 13.0 >=50k 未婚 白人 False 31.000000 113687.998068
9.0 <50k 丈夫 白人 False 60.999999 321116.998013 9.0 <50k

我们现在已经对我们原始 Pandas 对象调用了 .Dataloaders。这之所以有效，是因为 TabularPandas 实际上就是 TabDataLoaders。

我们可以通过调用 ._dbunch_type 来检查这一点：

```
to._dbunch_type
fastai.tabular.data.TabularDataLoaders dls._dbunch_type
fastai.tabular.data.TabularDataLoaders
```

## 22.5 创建 TabularLearner

现在我们准备构建我们的模型！

在处理分类数据时，我们创建了一个所谓的**嵌入矩阵**。这允许在不同分类基数之间的关系上增加维度。

找到最佳的尺寸比例是由杰里米·霍华德通过实验完成的

