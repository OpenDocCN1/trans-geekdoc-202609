

```python
# Load dataset
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
print('Loaded data file {0} with {1} rows and {2} columns'.format(filename, len(dataset),
    len(dataset[0])))
```

清单 1.3: 加载皮马印第安人糖尿病数据集 CSV 文件示例。

运行此示例，我们看到：

```text
Loaded data file pima-indians-diabetes.csv with 768 rows and 9 columns
```

清单 1.4: 加载皮马印第安人糖尿病数据集 CSV 文件的示例输出。

此函数的一个局限是，它会加载数据文件中的空行，并将其添加到我们的行列表中。我们可以通过一次性将数据行添加到数据集并跳过空行来克服这一问题。下面是使用此新改进版本的 `load_csv()` 函数的更新示例。

```python
# Example of loading Pima Indians CSV dataset
from csv import reader

# Load a CSV file
def load_csv(filename):
    dataset = list()
    with open(filename, 'r') as file:
        csv_reader = reader(file)
        for row in csv_reader:
            if not row:
                continue
            dataset.append(row)
    return dataset

# Load dataset
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
print('Loaded data file {0} with {1} rows and {2} columns'.format(filename, len(dataset),
    len(dataset[0])))
```

清单 1.5: 加载皮马印第安人糖尿病数据集 CSV 文件的改进示例。

运行此示例，我们看到：

```text
Loaded data file pima-indians-diabetes.csv with 768 rows and 9 columns
```

清单 1.6: 加载皮马印第安人糖尿病数据集 CSV 文件的示例输出。

### 1.2.2 将字符串转换为浮点数

绝大多数（如果不是全部的话）机器学习算法都倾向于使用数字。具体来说，更偏好使用浮点数。我们用于加载 CSV 文件的代码将数据集作为列表的列表返回，但每个值都是字符串。如果我们打印数据集中的一条记录，可以看到这一点：

```python
print(dataset[0])
```

清单 1.7: 显示数据集中的一条记录。

这将产生如下输出：

```
['6', '148', '72', '35', '0', '33.6', '0.627', '50', '1']
```

清单 1.8: 显示一行数据的示例输出。

我们可以编写一个小函数，将加载的数据集中特定列转换为浮点数值。下面是名为 str_column_to_float() 的函数。它会将数据集中的给定列转换为浮点数值，并在转换前小心地去除值中的任何空白字符。

```
def str_column_to_float(dataset, column):
    for row in dataset:
        row[column] = float(row[column].strip())
```

清单 1.9: 将字符串数据转换为浮点数的函数。

我们可以通过将此函数与上面的加载 CSV 函数结合来测试它，并将皮马印第安人数据集中的所有数值数据转换为浮点数值。完整示例如下。

```python
# Example of converting string variables to float
from csv import reader

# Load a CSV file
def load_csv(filename):
    dataset = list()
    with open(filename, 'r') as file:
        csv_reader = reader(file)
        for row in csv_reader:
            if not row:
                continue
            dataset.append(row)
    return dataset

# Convert string column to float
def str_column_to_float(dataset, column):
    for row in dataset:
        row[column] = float(row[column].strip())

# Load pima-indians-diabetes dataset
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
print('Loaded data file {0} with {1} rows and {2} columns'.format(filename, len(dataset),
      len(dataset[0])))
print(dataset[0])
# convert string columns to float
for i in range(len(dataset[0])):
    str_column_to_float(dataset, i)
print(dataset[0])
```

清单 1.10: 在皮马印第安人糖尿病数据集中将字符串值转换为浮点数的示例。

运行此示例，我们可以看到数据集的第一行在转换前后都被打印出来。我们可以看到，每列中的值都已从字符串转换为数字。

```
Loaded data file pima-indians-diabetes.csv with 768 rows and 9 columns
['6', '148', '72', '35', '0', '33.6', '0.627', '50', '1']
[6.0, 148.0, 72.0, 35.0, 0.0, 33.6, 0.627, 50.0, 1.0]
```

清单 1.11: 将字符串值转换为浮点数的示例输出。

### 1.2.3 将字符串转换为整数

鸢尾花数据集与皮马印第安人数据集类似，其列包含数值数据。不同之处在于最后一列，传统上用于存储给定行的结果或要预测的值。鸢尾花数据的最后一列是以字符串形式表示的鸢尾花物种。例如，以下是原始数据集的前 5 行。

```
5.1,3.5,1.4,0.2,Iris-setosa
4.9,3.0,1.4,0.2,Iris-setosa
4.7,3.2,1.3,0.2,Iris-setosa
4.6,3.1,1.5,0.2,Iris-setosa
5.0,3.6,1.4,0.2,Iris-setosa
```

清单 1.12: 鸢尾花物种数据集预览。

某些机器学习算法偏好所有值都是数值，包括结果或预测值。我们可以通过创建映射，将鸢尾花数据集中的类别值转换为整数。

1. 首先，我们定位所有唯一的类别值，它们恰好是：Iris-setosa、Iris-versicolor 和 Iris-virginica。
2. 接下来，我们为每个值分配一个整数值，例如：0、1 和 2。
3. 最后，我们将所有类别字符串值的出现替换为相应的整数值。

下面是一个名为 str_column_to_int() 的函数，用于完成此操作。与之前介绍的 str_column_to_float() 类似，它作用于数据集中的单个列。

```python
# Convert string column to integer
def str_column_to_int(dataset, column):
    class_values = [row[column] for row in dataset]
    unique = set(class_values)
    lookup = dict()
    for i, value in enumerate(unique):
        lookup[value] = i
    for row in dataset:
        row[column] = lookup[row[column]]
    return lookup
```

清单 1.13: 将字符串类别值整数编码的函数。

我们可以结合之前用于加载 CSV 文件和将列转换为浮点数值的两个函数来测试这个新函数。它还返回类别值到整数值的字典映射，以防下游用户想要将预测值再次转换回字符串值。下面的示例加载鸢尾花数据集，然后将前 3 列转换为浮点数，将最后一列转换为整数值。

```python
# Example of integer encoding string class values
from csv import reader

# Load a CSV file
def load_csv(filename):
    dataset = list()
    with open(filename, 'r') as file:
        csv_reader = reader(file)
        for row in csv_reader:
            if not row:
                continue
            dataset.append(row)
    return dataset

# Convert string column to float
def str_column_to_float(dataset, column):
    for row in dataset:
        row[column] = float(row[column].strip())

# Convert string column to integer
def str_column_to_int(dataset, column):
    class_values = [row[column] for row in dataset]
    unique = set(class_values)
    lookup = dict()
    for i, value in enumerate(unique):
        lookup[value] = i
    for row in dataset:
        row[column] = lookup[row[column]]
    return lookup

# Load iris dataset
filename = 'iris.csv'
dataset = load_csv(filename)
print('Loaded data file {0} with {1} rows and {2} columns'.format(filename, len(dataset), len(dataset[0])))
print(dataset[0])
# convert string columns to float
for i in range(4):
    str_column_to_float(dataset, i)
# convert class column to int
lookup = str_column_to_int(dataset, 4)
print(dataset[0])
print(lookup)
```

清单 1.14: 鸢尾花数据集中类别值整数编码的示例。

运行此示例将产生以下输出。我们可以看到数据类型转换前后数据集的第一行。我们还可以看到类别值到整数的字典映射。

```
Loaded data file iris.csv with 150 rows and 5 columns
['5.1', '3.5', '1.4', '0.2', 'Iris-setosa']
[5.1, 3.5, 1.4, 0.2, 1]
{'Iris-virginica': 0, 'Iris-setosa': 1, 'Iris-versicolor': 2}
```

清单 1.15: 类别值整数编码的示例输出。

