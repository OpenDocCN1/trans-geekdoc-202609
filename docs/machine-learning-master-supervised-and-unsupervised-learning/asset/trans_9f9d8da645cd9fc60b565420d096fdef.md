

# 实验编号 3

**目的：** 编写程序演示基于决策树的 ID3 算法的工作原理。使用合适的数据集构建决策树，并应用该知识对新样本进行分类。

## ID3 算法

```text
ID3 (Examples, Target attribute, Attributes)
```

- **Examples** 是训练示例。
- **Target attribute** 是树预测其值的属性。
- **Attributes** 是学习到的决策树可能测试的其他属性列表。
- 返回一棵能正确分类给定示例的决策树。

### 算法步骤

1. 为树创建一个根节点。
2. 如果所有示例均为正例，返回标签为 `+` 的单节点树根。
3. 如果所有示例均为负例，返回标签为 `-` 的单节点树根。
4. 如果属性为空，返回标签为示例中目标属性最常见值的单节点树根。
5. 否则，开始：
   - `A` ← 从 attributes 中 **最好地** 对示例进行分类的属性。
   - 根的决策属性 ← `A`。
   - 对 `A` 的每个可能值 `v`：
     - 在对应测试 `A = v` 的位置下添加一个新的树分支。
     - 令 `Examples_v` 为 `A` 取值为 `v` 的示例子集。
     - 如果 `Examples_v` 为空：
       - 则在此新分支下添加一个标签为示例中目标属性最常见值的叶节点。
     - 否则在此新分支下添加子树 `ID3(Examples_v, Target attribute, Attributes – {A})`。
6. 返回根节点。

最佳属性是具有最高信息增益的属性。

## 训练数据集：`ML3.CSV`

![数据集](image-bd7zu3of.jpg)

## 程序

```python
import pandas as pd

df = pd.read_csv("ML3.CSV")  # 输入数据集
t = "Answer"  # 目标属性为：t
attribute_names = list(df.keys())
attribute_names.remove(t)  # 预测属性：attribute_names

import math

def entropy(probs):
    return sum([-prob * math.log(prob, 2) for prob in probs])

def entropy_of_list(a_list, classes):
    from collections import Counter
    cnt = Counter(x for x in a_list)  # Counter 计算类别的比例
    total_instances = sum(cnt.values())  # 与 {0} 关联的实例/记录数为：
    probs = [x / total_instances for x in cnt.values()]  # x 表示 YES/NO 的数量
    return entropy(probs)  # 调用熵函数

def information_gain(df, split_attribute, target_attribute, default_attr):
    df_split = df.groupby(split_attribute)  # 根据属性值对数据分组
    glist = []
    for gname, group in df_split:
        glist.append(gname)  # 属性值
    glist.reverse()
    nobs = len(df.index) * 1.0
    df_agg = df_split.agg({target_attribute: [entropy_of_list, lambda x: len(x) / nobs]})
    df_agg.columns = ['Entropy', 'PropObservations']
    new_entropy = sum(df_agg['Entropy'] * df_agg['PropObservations'])
    old_entropy = entropy_of_list(df[target_attribute], default_attr)
    return old_entropy - new_entropy

def id3(df, target_attribute, attribute_names, default_class=None, parent_attr=None):
    from collections import Counter
    cnt = Counter(x for x in df[target_attribute])  # YES/NO 类别

    ## 第一次检查：该数据集分割是否同质？
    if len(cnt) == 1:
        return next(iter(cnt))  # 下一个输入数据集，或在遇到 EOF 时引发 StopIteration。

    ## 第二次检查：该数据集分割是否为空？如果是，返回默认值
    elif df.empty or (not attribute_names):
        return default_class  # 对空数据集返回 None

    ## 否则：该数据集已准备好进行划分！
    # 获取此函数下一次递归调用的默认值：
    default_class = max(cnt.keys())  # YES 和 NO 类别的数量

    # 计算属性的信息增益：
    gainz = []
    for attr in attribute_names:
        ig = information_gain(df, attr, target_attribute, default_class)
        gainz.append(ig)
        print(f"Gain of {attr} is : {ig}")

    index_of_max = gainz.index(max(gainz))  # 最佳属性的索引
    best_attr = attribute_names[index_of_max]  # 选择信息增益最大的属性进行划分
    print(f"Attribute with the maximum gain is: {best_attr}")

    # 创建一个空树，稍后填充
    tree = {best_attr: {}}  # 以最佳属性作为节点初始化树
    remaining_attribute_names = [i for i in attribute_names if i != best_attr]

    # 划分数据集——在每次划分时，递归调用此算法。用递归调用的结果（子树）填充空树
    for attr_val, data_subset in df.groupby(best_attr):
        subtree = id3(data_subset, target_attribute, remaining_attribute_names, default_class, best_attr)
        tree[best_attr][attr_val] = subtree
    return tree

from pprint import pprint
tree = id3(df, t, attribute_names)
print("Resultant Decision Tree")
pprint(tree)

def classify(instance, tree, default=None):
    attribute = next(iter(tree))  # Outlook/Humidity/Wind
    if instance[attribute] in tree[attribute].keys():  # 实例的属性值在树的键集合中
        result = tree[attribute][instance[attribute]]
        if isinstance(result, dict):  # 这是一个树，深入查找
            return classify(instance, result)
        return result  # 这是一个标签
    return default
```

## 输出

**输入数据集为：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**目标属性为：** `Answer`
**预测属性为：** `['Outlook', 'Temperature', 'Humidity', 'Wind']`

### `Outlook` 的信息增益计算

**分组属性值 (overcast)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| overcast | hot | high | weak | yes |

**分组属性值 (rain)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**分组属性值 (sunny)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |

- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `overcast` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- 目标属性类别计数(Yes/No)= `{'no': 1}`
- 与 `sunny` 关联的实例/记录总数为：`1`
- 类别 `no` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'no': 2, 'yes': 3}`
- 与 `S` 关联的实例/记录总数为：`5`
- 类别 `no` 的概率为：`0.4000`
- 类别 `yes` 的概率为：`0.6000`
- **`Outlook` 的信息增益为：`0.4199730940219749`**

### `Temperature` 的信息增益计算

**分组属性值 (cool)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**分组属性值 (hot)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |

**分组属性值 (mild)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `cool` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'no': 1, 'yes': 1}`
- 与 `hot` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `mild` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'no': 2, 'yes': 3}`
- 与 `S` 关联的实例/记录总数为：`5`
- 类别 `no` 的概率为：`0.4000`
- 类别 `yes` 的概率为：`0.6000`
- **`Temperature` 的信息增益为：`0.17095059445466854`**

### `Humidity` 的信息增益计算

**分组属性值 (high)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |

**分组属性值 (normal)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

- 目标属性类别计数(Yes/No)= `{'no': 1, 'yes': 2}`
- 与 `high` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `normal` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'no': 2, 'yes': 3}`
- 与 `S` 关联的实例/记录总数为：`5`
- 类别 `no` 的概率为：`0.4000`
- 类别 `yes` 的概率为：`0.6000`
- **`Humidity` 的信息增益为：`0.01997309402197489`**

### `Wind` 的信息增益计算

**分组属性值 (strong)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | strong | no |

**分组属性值 (weak)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |

- 目标属性类别计数(Yes/No)= `{'no': 1}`
- 与 `strong` 关联的实例/记录总数为：`1`
- 类别 `no` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'no': 1, 'yes': 3}`
- 与 `weak` 关联的实例/记录总数为：`4`
- 类别 `no` 的概率为：`0.2500`
- 类别 `yes` 的概率为：`0.7500`
- 目标属性类别计数(Yes/No)= `{'no': 2, 'yes': 3}`
- 与 `S` 关联的实例/记录总数为：`5`
- 类别 `no` 的概率为：`0.4000`
- 类别 `yes` 的概率为：`0.6000`
- **`Wind` 的信息增益为：`0.3219280948873623`**

**信息增益最大的属性为：** `Outlook`

### `Temperature` 的信息增益计算（`rain` 的子树）

**分组属性值 (cool)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**分组属性值 (mild)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `cool` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `mild` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Temperature` 的信息增益为：`0.2516291673878229`**

### `Humidity` 的信息增益计算（`rain` 的子树）

**分组属性值 (high)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

**分组属性值 (normal)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `high` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `normal` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Humidity` 的信息增益为：`0.2516291673878229`**

### `Wind` 的信息增益计算（`rain` 的子树）

**分组属性值 (strong)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | strong | no |

**分组属性值 (weak)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |

- 目标属性类别计数(Yes/No)= `{'no': 1}`
- 与 `strong` 关联的实例/记录总数为：`1`
- 类别 `no` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2}`
- 与 `weak` 关联的实例/记录总数为：`2`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Wind` 的信息增益为：`0.9182958340544896`**

**信息增益最大的属性为：** `Wind`

## 生成的决策树

```python
{'Outlook': {'overcast': 'yes',
  'rain': {'Wind': {'strong': 'no', 'weak': 'yes'}},
  'sunny': 'no'}}
```

