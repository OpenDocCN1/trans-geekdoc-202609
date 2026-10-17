
```python
import pandas as pd
import tensorflow as tf
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1).values
y = df['target_column'].values

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 缩放特征
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# 使用 Keras 构建并训练模型
model = tf.keras.Sequential([
    tf.keras.layers.Dense(16, activation='relu', input_shape=(X_train.shape[1],)),
    tf.keras.layers.Dense(1, activation='sigmoid')
])
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
model.fit(X_train, y_train, epochs=10, batch_size=32, validation_split=0.1)

# 评估模型
_, accuracy = model.evaluate(X_test, y_test)
```

### Pandas 与 PyTorch 的集成

`PyTorch` 是一个基于 `Torch` 的 Python 开源机器学习库。要将 `Pandas DataFrame` 与 `PyTorch` 配合使用，需要将它们转换为 `PyTorch Tensor`。下面是一个示例：

```python
import pandas as pd
import torch
from torch.utils.data import DataLoader, TensorDataset
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

##### 加载数据集
url = 'https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv'
df = pd.read_csv(url)

##### 分离特征和目标变量
X = df.drop('target_column', axis=1).values
y = df['target_column'].values

##### 执行训练-测试集划分
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 缩放特征
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# 将 NumPy 数组转换为 PyTorch Tensor 并创建 DataLoader
train_dataset = TensorDataset(torch.Tensor(X_train), torch.Tensor(y_train))
test_dataset = TensorDataset(torch.Tensor(X_test), torch.Tensor(y_test))
train_loader = DataLoader(train_dataset, batch_size=32, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=32)

# 使用 PyTorch 构建并训练模型
model = torch.nn.Sequential(
    torch.nn.Linear(X_train.shape[1], 16),
    torch.nn.ReLU(),
    torch.nn.Linear(16, 1),
    torch.nn.Sigmoid()
)
criterion = torch.nn.BCELoss()
optimizer = torch.optim.Adam(model.parameters())

for epoch in range(10):
    for X_batch, y_batch in train_loader:
        y_pred = model(X_batch)
        loss = criterion(y_pred, y_batch.view(-1, 1))
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

# 评估模型
with torch.no_grad():
    correct = 0
    total = 0
    for X_batch, y_batch in test_loader:
        y_pred = model(X_batch)
        predicted = (y_pred > 0.5).float()
        total += y_batch.size(0)
        correct += (predicted == y_batch.view(-1, 1)).sum().item()
    accuracy = correct / total
```

总之，将 `Pandas` 与 `Scikit-learn`、`TensorFlow` 和 `PyTorch` 集成，使机器学习任务中的工作流更加流畅，因为 `Pandas` 提供了强大的数据操作工具，而这些库提供了先进的机器学习和深度学习功能。

## 总结

我们涵盖了与使用 `pandas` 进行机器学习相关的主题，包括数据预处理、特征工程、处理不平衡数据和特征缩放。我们还介绍了训练集-测试集划分和交叉验证的技术，并提供了使用 `Python` 和 `Scikit-learn` 实现它们的示例。此外，我们讨论了 `pandas` 与各种机器学习库（包括 `Scikit-learn`、`TensorFlow` 和 `PyTorch`）的集成，这使得在机器学习任务中能够无缝地进行数据处理和预处理。我们提供了如何将 `pandas` 与这些库集成并实现各种机器学习任务的示例。

机器学习的一个基本方面是特征工程，它涉及选择、转换和构造特征以提高模型性能。我们讨论了各种特征工程技术，如独热编码、特征缩放和降维，以及它们对机器学习的优势和益处。

此外，我们还谈到了处理不平衡数据，这是机器学习中的常见问题，尤其是在分类任务中。我们提供了使用 `Python` 和 `Scikit-learn` 识别和解决不平衡数据的分步说明。

最后，我们介绍了特征缩放和归一化，这些是用于标准化数据集中自变量或特征范围的预处理技术。我们讨论了特征缩放在机器学习中的重要性，并提供了使用 `Scikit-learn` 实现特征缩放和归一化的示例。

总体而言，本章涵盖了使用 `pandas` 进行机器学习的各种基本主题，包括数据预处理、特征工程、处理不平衡数据和模型评估技术。我们还演示了 `pandas` 与各种机器学习库的集成，这对于机器学习任务中的流程化工作流至关重要。

# 第 8 章：文本数据与自然语言处理

## 文本数据清洗与预处理

处理文本数据是数据分析的重要组成部分，因为许多数据集包含需要处理和分析的文本信息。文本数据可以有多种不同形式，例如客户评论、社交媒体帖子，甚至医疗记录。在数据分析中，处理文本数据涉及许多任务，包括清洗和预处理数据、提取相关信息，以及分析数据中的模式和趋势。为了完成这些任务，数据分析师通常会使用专门为处理文本数据而设计的专用工具和技术。

在 Python 中处理文本数据最强大的工具之一是 `Pandas` 库。`Pandas` 提供了许多专门设计用于在 `DataFrame` 或 `Series` 中处理文本数据的字符串方法。这些字符串方法使得操作和分析文本数据变得容易，让数据分析师能够快速轻松地提取相关信息并从数据中获得洞察。

以下是 `Pandas` 中用于处理文本数据的一些最常用字符串方法：

### `str.contains()`

`str.contains()` 方法用于检查字符串是否包含指定的子字符串，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否包含子字符串 'cool'
df['contains_cool'] = df['text'].str.contains('cool')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | contains_cool |
| :--- | :--- |
| hello world | False |
| python is awesome | False |
| data science is cool | True |

正如你所见，`str.contains()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否包含子字符串 'cool'。

### `str.startswith()`

`str.startswith()` 方法用于检查字符串是否以指定的子字符串开头，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否以子字符串 'hello' 开头
df['starts_with_hello'] = df['text'].str.startswith('hello')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | starts_with_hello |
| :--- | :--- |
| hello world | True |
| python is awesome | False |
| data science is cool | False |

正如你所见，`str.startswith()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否以子字符串 'hello' 开头。

### `str.endswith()`

`str.endswith()` 方法用于检查字符串是否以指定的子字符串结尾，并返回布尔值。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 检查 'text' 列是否以子字符串 'world' 结尾
df['ends_with_world'] = df['text'].str.endswith('world')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | ends_with_world |
| :--- | :--- |
| hello world | True |
| python is awesome | False |
| data science is cool | False |

正如你所见，`str.endswith()` 方法向 `DataFrame` 添加了一列新列，指示 'text' 列中的每一行是否以子字符串 'world' 结尾。

### `str.split()`

`str.split()` 方法用于根据指定的分隔符将字符串拆分为子字符串列表。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello,world', 'python,is,awesome', 'data,science,is,cool']})

# 使用逗号作为分隔符将 'text' 列拆分为子字符串列表
df['text_list'] = df['text'].str.split(',')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_list |
| :--- | :--- |
| hello,world | [hello, world] |
| python,is,awesome | [python, is, awesome] |
| data,science,is,cool | [data, science, is, cool] |

正如我们从前面的示例中所见，`str.split()` 方法根据逗号分隔符将 'text' 列拆分为子字符串列表。生成的列表随后存储在一个名为 'text_list' 的新列中。

### `str.strip()`

`str.strip()` 方法用于移除字符串前导和尾随的空白字符。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['  hello world  ', '  python is awesome  ', '  data science is cool  ']})

# 移除 'text' 列前导和尾随的空白字符
df['text_stripped'] = df['text'].str.strip()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_stripped |
| :--- | :--- |
| hello world | hello world |
| python is awesome | python is awesome |
| data science is cool | data science is cool |

正如我们从输出中所见，`str.strip()` 方法移除了 'text' 列前导和尾随的空白字符，并将清洗后的文本存储在一个名为 'text_stripped' 的新列中。

### `str.replace()`

`str.replace()` 方法用于将指定的子字符串替换为另一个子字符串。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['hello world', 'python is awesome', 'data science is cool']})

# 在 'text' 列中将 'world' 替换为 'universe'
df['text_replaced'] = df['text'].str.replace('world', 'universe')

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_replaced |
| :--- | :--- |
| hello world | hello universe |
| python is awesome | python is awesome |
| data science is cool | data science is cool |

正如我们从输出中所见，`str.replace()` 方法在 'text' 列中将子字符串 'world' 替换为 'universe'，并将更新后的文本存储在一个名为 'text_replaced' 的新列中。

### `str.lower()`

`str.lower()` 方法用于将字符串转换为小写。

```python
import pandas as pd

# 创建示例 DataFrame
df = pd.DataFrame({'text': ['Hello World', 'Python is Awesome', 'Data Science is Cool']})

# 将 'text' 列转换为小写
df['text_lower'] = df['text'].str.lower()

# 显示更新后的 DataFrame
print(df)
```

**输出：**

| text | text_lower |
| :--- | :--- |
| Hello World | hello world |
| Python is Awesome | python is awesome |
| Data Science is Cool | data science is cool |
