
![](img/0684d2da98e09085c0a622d4fd69aaad_73_0.png)

图 2-3. 你在 Jupyter 中的工作区

笔记本包含单元格列表。每个单元格都可以包含可执行代码或格式化文本。现在笔记本只包含一个空代码单元格，标记为 `"In [1]:"`。在单元格中输入 `print("Hello world!")`，然后点击播放按钮（参见[图 2-4]）或按 `Shift-Enter`。这会将单元格发送到该笔记本的 `Python` 内核，内核运行它并返回输出。结果将显示在单元格下方，由于我们已经到达笔记本的末尾，系统会通过 `Jupyter Help` 菜单中的用户界面工具自动创建一个新单元格以便学习基础知识。

![](img/0684d2da98e09085c0a622d4fd69aaad_73_1.png)

图 2-4. Hello world Python 笔记本

# 第 2 章：端到端机器学习项目

## 下载数据

在典型环境中，你的数据可以在关系型数据库（或某些常用数据存储）中，并分布在多个表格/文档/文件中。要访问它，你首先需要获取凭据和访问权限，并熟悉数据模式（`schema`）。然而，在这个项目中，情况简单得多：你只需要下载一个单一压缩文件 `housing.tgz`，其中包含一个所有数据的逗号分隔值（CSV）文件。

你可以使用浏览器下载它，并运行 `tar xzf housing.tgz` 来解压文件并提取 CSV 文件，但最好编写一个小函数来完成。如果特定数据经常变化，这非常有用，因为它允许你编写一个脚本，并在每次需要获取最新数据时运行它（或者你可以设置一个定时任务每隔一段时间自动执行）。如果你需要在多台机器上安装数据集，自动化获取数据的过程也是很有用的。

以下是获取数据的函数：

```
import os
import tarfile
from six.moves import urllib

DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/housing-ml2/master/"
HOUSING_PATH = os.path.join("datasets", "housing")
HOUSING_URL = DOWNLOAD_ROOT + "/datasets/housing/housing.tgz"

def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):
    if not os.path.exists(housing_path):
        os.makedirs(housing_path)
    tgz_path = os.path.join(housing_path, "housing.tgz")
    urllib.request.urlretrieve(housing_url, tgz_path)
    housing_tgz = tarfile.open(tgz_path)
    housing_tgz.extractall(path=housing_path)
    housing_tgz.close()
```

现在当你调用 `fetch_housing_data()` 时，它会创建一个 `datasets` 目录，下载 `housing.tgz` 文件，并从中提取 `housing.csv`。现在让我们用 Pandas 加载数据。

```python
import pandas as pd
def load_housing_data(housing_path=HOUSING_PATH):
    path = os.path.join(housing_path, "housing.csv")
    return pd.read_csv(path)
```

此函数返回一个 Pandas `DataFrame`。

## 快速查看数据

让我们使用 `head()` 查看前五行（参见图 2-5）。

 | longitude | latitude | housing_median_age | total_rooms | total_bedrooms | population |

|---|---|---|---|---|---|---|

| 0 | -122.2337 | 37.8752 | 41 | 6869 | 2 | 3269 |

| 1 | -122.2715 | 37.8509 | 21 | 6462 | 3 | 2466 |

| 2 | -122.2175 | 37.8581 | 52 | 1718 | 2 | 1569 |

| 3 | -122.2272 | 37.825 | 54 | 5365 | 9 | 2018 |

| 4 | -122.2235 | 37.8253 | 53 | 5355 | 2 | 1417 |

图 2-5. 前五行

数据集中有 20640 个实例，按机器学习标准来说相当小，但非常适合入门。注意 `total_bedrooms` 属性有 20433 个非空值，这意味着有 207 个地区缺失该特征。我们需要处理这个问题。

`info()` 方法有助于获取数据的快速描述，特别是行数、每个属性的类型和非空值（参见图 2-6）。

```
<class 'pandas.core.DataFrame'>
RangeIndex: 20640 entries, 0 to 20639
Data columns (total 10 columns):
 longitude 20640 non-null float64
latitude 20640 non-null float64
housing_median_age 20640 non-null float64
total_rooms 20640 non-null float64
total_bedrooms 20433 non-null float64
population 20640 non-null float64
households 20640 non-null float64
median_income 20640 non-null float64
housing_value 20640 non-null float64
ocean_proximity 20640 non-null object
types: float64(9), object(1)
memory usage: 1.6 MB
```

图 2-6. Housing 信息

除了 `ocean_proximity` 字段外，所有属性都是数值型的。它的类型是 `object`，因此它可以包含任何类型的 Python 对象，但由于你是从 CSV 文件加载的这些数据，所以知道它是文本属性。当你查看前五行时，可能注意到 `ocean_proximity` 列的值是重复的，这意味着它可能是一个分类属性。你可以使用 `value_counts()` 方法查看有多少地区属于每个类别：

```
>>> housing['ocean_proximity'].value_counts()
<1H OCEAN        9136
INLAND            6555
NEAR OCEAN        2658
NEAR BAY          2290
ISLAND             5
Name: ocean_proximity, dtype: int64
```

### 在 [8]: housing.describe()

| | 经度 | 纬度 | 房屋中位数年龄 | 总房间数 | 总卧室数 |

|---|---|---|---|---|---|

| 计数 | 20640.00000 | 20640.00000 | 20640.00000 | 20640.00000 | 20433.00000 |

| 均值 | -119.569704 | 35.631861 | 28.639486 | 2635.763081 | 537.870533 |

| 标准差 | 2.003532 | 2.135952 | 12.586558 | 2181.615252 | 421.385070 |

| 最小值 | -124.350000 | 32.540000 | 1.000000 | 2.000000 | 1.000000 |

| 25% | -121.810000 | 33.930000 | 18.000000 | 1447.750000 | 296.000000 |

| 50% | -118.490000 | 34.260000 | 29.000000 | 2127.000000 | 435.000000 |

| 75% | -118.010000 | 37.710000 | 37.000000 | 3148.000000 | 647.000000 |

| 最大值 | -114.310000 | 41.950000 | 52.000000 | 3932.000000 | 6445.000000 |

图 2-7. 每个数值属性的摘要

计数、均值、最小值和最大值行是非常言而易明的。注意，空值被忽略了（例如，`total_bedrooms` 的计数为 20,433，而不是 20,640）。该行显示标准差，它衡量了值的离散程度。¹

25%、50% 和 75% 行显示相应的百分位数：百分位数计算的是在一组观测值中，有特定百分比的观测值低于该值。例如，25% 的地区 `housing_median_age` 长于 18 年，而 50% 低于 29 年，75% 低于 37 年。这些通常被称为第 25 分位数（或*第一四分位数*）、中位数和第 75 分位数（或*第三四分位数*）。

了解你正在处理的数据类型的另一种方法是为每个数值属性绘制直方图。直方图显示了具有给定值范围（在横轴上）的实例数量（在纵轴上）。你可以一次绘制一个属性的图表，也可以在整个数据集上调用 `hist()` 方法，它将为每个数值属性绘制直方图（见图 2-8）。例如，你可以看到略多于 800 个地区的 `median_house_value` 等于 $100,000。

```python
%matplotlib 仅在 Jupyter notebook 中有效
import matplotlib.pyplot as plt
housing.hist(bins=50, figsize=(20,15))
```

> ¹ 12 标准差通常表示为 σ（希腊字母 sigma），它是方差的平方根，而方差是离均值平方差的平均值。当特征呈现钟形正态分布（也称为高斯分布）时（这非常常见），“68-95-99.7%”规则适用：约 68% 的值在均值的 1σ 以内，95% 在 2σ 以内，99.7% 在 3σ 以内。

`hist()` 方法依赖于 Matplotlib，而 Matplotlib 又依赖用户指定的图形后端在你的屏幕上绘图。在绘制任何图表之前，你需要指定 Matplotlib 应该使用哪个后端。最简单的选项是使用 Jupyter 的魔法命令 `%matplotlib inline`。这告诉 Jupyter 设置 Matplotlib 使用 Jupyter 自己的后端。图表随后将在笔记本内部渲染。注意，在 Jupyter notebook 中调用 `show()` 是可选的，因为 Jupyter 在执行单元格时会自动显示图表。

![](img/0684d2da98e09085c0a622d4fd69aaad_78_0.png)

图 2-8. 每个数值属性的直方图

注意这些直方图中的几点：

- 1. 首先，中位数收入属性看起来并不像是以美元（USD）表示的。在与收集数据的团队核实后，你被告知对较高的中位数收入进行了缩放并封顶在 15（实际上为 15.0001），对较低的中位数收入则封顶在 0.5（实际上为 0.4999）。这些数字代表大约万美元。

- 2. 房屋中位数年龄和房屋价值也被封顶了。如果这是你的目标属性（标签），可能会是一个严重的问题。机器学习算法可能会学习价格不会超过限制。你需要与你的团队（使用你系统输出的团队）确认这是否是一个问题。如果你告诉他们你需要超过 $500,000 的精确预测，那么你主要有两个选择：

    a. 为被封顶的地区收集正确的标签。

    b. 从训练集中移除这些地区（同时也从测试集中移除，你的系统在预测超过 $500,000 时不应被评估糟糕）。

- 3. [此处原文不完整]

- 4. 最后，某些直方图不同；我们稍后会讨论。

![](img/0684d2da98e09085c0a622d4fd69aaad_78_0.png)

## 创建测试集

等等，但这并不完美：如果你再次运行程序，它将生成不同的测试集，这是你想要避免的。一种解决方案是在第一次运行时保存测试集，并在后续运行加载它。另一种方案是在调用 `np.permutation()` 之前设置随机生成器的种子（例如 `np.random.seed(42)`），以便生成相同的洗牌索引。这里有一个可能的实现：

```python
import numpy as np
from zlib import crc32
```

```python
def test_set_check(identifier, test_ratio):
    return crc32(np.int64(identifier)) & 0xffffffff < test_ratio * 2***32
```

```python
def split_train_test_by_id(data, test_ratio, id_column):
    ids = data[id_column]
```

你可以这样使用该函数：

```python
>>> train_set, test_set = split_train_test(housing, 0.2)
>>> len(train_set)
16512
>>> len(test_set)
4128
```

```python
in_test_set = ids.apply(lambda id: test_set_check(id, test_ratio))
data.loc[-in_test_set], data.loc[in_test_set]
```

遗憾的是，房价数据集没有标识符列。简单的解决方案是使用行索引作为 ID：

```python
housing_with_id = housing.reset_index(0)  # 添加了 'index' 列
train_test_set = split_train_test_by_id(housing_with_id, 0.2, "index")
```

如果你使用行索引作为唯一标识符，必须确保数据一直延伸到数据集的末尾，且没有任何某行从未被删除。如果无法做到这一点，你可以尝试使用最稳定的特征来构建唯一标识符。

例如，一个地区的纬度和经度保证在几年内是稳定的，你可以将它们合并为一个 ID，如下：

```python
housing_with_id['id'] = housing['longitude'] * 1000 + housing['latitude']
train_test_set = split_train_test_by_id(housing_with_id, 0.2, "id")
```

Scikit-Learn 有几个函数可以以各种方式将数据集划分为子集。最简单的函数是 `train_test_split`，它的功能与之前定义的 `split_train_test` 函数几乎相同，但增加了一些额外功能。首先，有一个 `random_state` 参数，允许你设置之前设置过的随机生成器作为种子；然后你可以传递多个行数相同的数据集，它将按照相同的索引对它们进行拆分（这非常有用，例如当你有一个单独的标签 DataFrame 时）：

```python
from sklearn.model_selection import train_test_split

train_test_set = train_test_split(housing, test_size=0.2, random_state=42)
```

到为止，我们考虑了随机采样方法。但如果你的数据集足够大（相对于属性数量）呢？如果不够大，你就面临引入显著采样偏差的风险。当一项调查决定拨打 1000 个电话来询问几个问题时，他们并不仅仅是从电话簿中随机挑选 1000 个人。他们试图确保这 1000 人能代表整个人口。例如，美国人口由 51.3% 的女性和 48.7% 的男性组成，因此在美国进行一项良好的调查会尝试保持相同的比例： 513 名女性和 487 名男性。这被称为**分层采样**（stratified sampling）：将人口分为称为“分层”（stratum）的同质小组，以保证测试集对总体人口具有代表性。如果使用纯随机采样，大约有 12% 的概率采样出一个偏斜的测试集（其中女性比例少于 49% 或超过 54%）。无论如何，结果都会产生显著偏差。

假设你和专家聊过，他们告诉你中位数收入是预测中位数房价非常重要的属性。你可能希望确保测试集对整个数据集中各种收入类别具有代表性。由于中位数收入是一个连续数值属性，你首先需要创建一个收入类别属性。让我们仔细观察中位数收入直方图（回到图 2-8）：大多数中位数收入值集中在 1.5 到 6 之间（即 $15,000 到 $60,000），但一些中位数收入远超过 6。在数据集中为每个分层拥有足够的实例是非常重要的，否则对该分层重要性的估计可能会产生偏差。这意味着你不应该有太多的分层，每个分层都应该足够大。以下代码使用 `pd.cut()` 函数创建一个具有 5 个类别的收入类别（标记为 1 到 5）：类别 1 的范围从 0 到 1.5（即少于 $15,000），类别 2 从 1.5 到 3，依此类推：

```python
housing["income_cat"] = pd.cut(housing["median_income"],
bins=[0, 1.5, 3.0, 4.5, 6., np.inf),
labels=[1, 2, 3, 4, 5])
```

这些收入类别在图 2-9 中所示：

```python
housing["income_cat"].hist()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_82_0.png)
