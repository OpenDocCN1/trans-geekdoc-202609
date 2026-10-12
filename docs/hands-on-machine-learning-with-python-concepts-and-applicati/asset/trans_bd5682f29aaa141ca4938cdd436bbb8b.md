

# 数据探索与特征工程

## 数据概览

```text
Sex              418 non-null object
Age              332 non-null float64
SibSp            418 non-null int64
Parch            418 non-null int64
Ticket           418 non-null object
Fare             417 non-null float64
Cabin             91 non-null object
Embarked         418 non-null object

dtypes: float64(2), int64(4), object(5)
memory usage: 36.0+ KB
```

注意不同特征中存在大量空值。下一步是进一步探索数据以获取早期洞察和总体认识：

![](images/00020.jpeg)

以下是数据摘要中最值得注意的几点：

* 891 名乘客，约占泰坦尼克号实际乘客总数（2,224 人）的 40%。
* 近 30% 的乘客有兄弟姐妹和/或配偶同行（`SibSp` 列）。
* 大多数乘客（> 75%）没有父母或子女同行（`Parch` 列）。

## 特征筛选

现在我们已对数据有了初步了解。下一步是剔除与生存率无关的明显特征。这是一个重要步骤：在应用复杂算法之前，首先排除不必要的特征总是好的。

* **姓名 (`Name`)**：一个人的名字与生存有关吗？可以肯定答案是否定的。因此我们删除 `Name` 并将其从后续模型中排除。
* **票号 (`Ticket`)**：哪个人获得特定票号是随机的。因此可以安全地从数据中排除 `Ticket` 特征。`PassengerId` 也是同理。
* **船舱 (`Cabin`)**：该特征有大量空值（891 条记录中仅 204 个非空对象，意味着绝大部分值为空）。

## 假设与验证

除了剔除特征，我们还需要做一些假设。这是数据分析和机器学习的自然组成部分。我们从几个假设开始，最后验证它们是否合理。

**假设 1**：女性（数据集中 `Sex = female`）更有可能生存（例如在紧急救援中享有优先权）。儿童和头等舱乘客（`Pclass = 1`）也有更好的生存机会。

好消息是我们可以实际检验这些假设，并尽早查看它们是否合理：

### 乘客等级 (`Pclass`) 与生存率

```python
train_df[['Pclass', 'Survived']].groupby(['Pclass'], as_index=False).mean().sort_values(by='Survived', ascending=False)
```

![](images/00021.jpeg)

注意 `Pclass = 1`（头等舱乘客）拥有最高的生存率。

### 性别 (`Sex`) 与生存率

```python
train_df[["Sex", "Survived"]].groupby(['Sex'], as_index=False).mean().sort_values(by='Survived', ascending=False)
```

![](images/00022.jpeg)

女性的生存率超过 74%。

### 同行兄弟姐妹/配偶 (`SibSp`) 与生存率

```python
train_df[["SibSp", "Survived"]].groupby(['SibSp'], as_index=False).mean().sort_values(by='Survived', ascending=False)
```

![](images/00023.jpeg)

### 同行父母/子女 (`Parch`) 与生存率

```python
train_df[["Parch", "Survived"]].groupby(['Parch'], as_index=False).mean().sort_values(by='Survived', ascending=False)
```

![](images/00024.jpeg)

上述特征可能以某种方式影响乘客的生存几率（但请记住运气仍然发挥作用，因此 100% 正确的预测可能是不可能实现的）。

## 数据可视化

为了进一步分析，让我们可视化数据（这可能更容易解释）。首先，导入必要的库和包：

```python
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline  # 以便绘图在笔记本中内联显示
```

### 年龄 (`Age`) 分布

```python
g = sns.FacetGrid(train_df, col='Survived')
g.map(plt.hist, 'Age', bins=20)
```

![](images/00025.jpeg)

注意右侧直方图（显示数值频率）中，许多婴儿存活（看接近 0 岁处）。还要注意一些老年乘客（接近 80 岁）也存活了。这证实了我们之前的假设：`Age` 是后续分析的相关特征。

### 乘客等级 (`Pclass`) 与生存情况

```python
grid = sns.FacetGrid(train_df, col='Survived', row='Pclass', size=2.2, aspect=1.6)
grid.map(plt.hist, 'Age', alpha=.5, bins=20)
grid.add_legend()
```

![](images/00026.jpeg)

注意右上角（`Pclass = 1` | `Survived = 1`）即头等舱幸存者所在区域相当密集（高密度）。同时注意左下角（`Pclass = 3` | `Survived = 0`）即三等舱非幸存者也很密集。换句话说，乘客等级与生存率相关（例如头等舱乘客机会更大）。

### 登船港口 (`Embarked`) 的影响

如果乘客在不同地点登船，是否会影响其生存几率？这比较棘手，但我们还是探索一下：

```python
grid = sns.FacetGrid(train_df, row='Embarked', size=2.2, aspect=1.6)
grid.map(sns.pointplot, 'Pclass', 'Survived', 'Sex', palette='deep')
grid.add_legend()
```

![](images/00027.jpeg)

**登船港口说明**：S = 南安普顿；C = 瑟堡；Q = 皇后镇。

注意在瑟堡登船的男性（`Embarked = C`）有更高的生存率。这是否意味着 `Embarked` 特征影响生存？一个可能的原因是：在瑟堡登船的男性多为 `Pclass = 1` 或 `2`。换句话说，生存率与 `Pclass` 的关系更大，而非 `Embarked` 特征本身。但如何确认这一点？这里有一种方法：

```python
grid = sns.FacetGrid(train_df, row='Embarked', col='Survived', size=2.2, aspect=1.6)
grid.map(sns.barplot, 'Sex', 'Fare', alpha=.5, ci=None)
grid.add_legend()
```

![](images/00028.jpeg)

这里我们还考虑了一个额外特征（`Fare`）。注意支付更高票价的乘客有更好的生存机会。还要注意登船港口与生存率之间存在相关性。因此，在后续分析中包含 `Fare` 是好的。

## 特征工程实施

下一步是排除无关特征并包含相关特征。

```python
print("Before", train_df.shape, test_df.shape, combine[0].shape, combine[1].shape)
train_df = train_df.drop(['Ticket', 'Cabin'], axis=1)
test_df = test_df.drop(['Ticket', 'Cabin'], axis=1)
combine = [train_df, test_df]
print("After", train_df.shape, test_df.shape, combine[0].shape, combine[1].shape)
```

结果如下：

```text
Before (891, 12) (418, 11) (891, 12) (418, 11)
After (891, 10) (418, 9) (891, 10) (418, 9)
```

因为我们从训练和测试数据中删除了 `Ticket` 和 `Cabin`，所以特征变少了。

请记住，我们之前也要移除 `Name` 和 `PassengerId`，因为它们似乎与生存率无关。但 `Name` 实际上可能是一个人生存的“信号”。例如，如果名字中包含 "Miss" 或 "Mrs."，很可能是女性（意味着更高的生存率，因为女性生存率较高）。

因此，创建一个新特征 `Title`（称谓）可能是好的，因为这可能与生存率相关。我们可以通过以下代码实现（你应该熟悉 Python 中的正则表达式）：

```python
for dataset in combine:
    dataset['Title'] = dataset.Name.str.extract(' ([A-Za-z]+)\.', expand=False)

pd.crosstab(train_df['Title'], train_df['Sex'])
```

![](images/00029.jpeg)

称谓种类太多。也许将大多数称谓归类为 "Rare" 以便于处理，然后查看称谓及对应的生存百分比：

```python
for dataset in combine:
    dataset['Title'] = dataset['Title'].replace(['Lady', 'Countess','Capt', 'Col',
                                                 'Don', 'Dr', 'Major', 'Rev', 'Sir', 'Jonkheer', 'Dona'], 'Rare')
    dataset['Title'] = dataset['Title'].replace('Mlle', 'Miss')
    dataset['Title'] = dataset['Title'].replace('Ms', 'Miss')
    dataset['Title'] = dataset['Title'].replace('Mme', 'Mrs')

train_df[['Title', 'Survived']].groupby(['Title'], as_index=False).mean()
```

![](images/00030.jpeg)

