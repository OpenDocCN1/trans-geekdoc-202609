
正在构建情感分类器或聚类文档。
让我们来看图像预处理的示例：
在处理图像数据时，预处理通常涉及缩放、归一化并将图像转换为张量，特别是对于分类或目标检测任务。以下转换流水线为深度学习模型准备图像数据：

```python
from torchvision import transforms
transform = transforms.Compose([
    transforms.Resize((128, 128)),
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5))
])
```

这些预处理步骤标准化图像尺寸和像素强度值，确保数据适用于深度学习模型。

# AI 工具的作用

文本归一化、图像缩放，甚至音频数据的频谱图生成等任务在不同项目中经常重复出现。像 GitHub Copilot 这样的 AI 辅助编程工具可以通过根据上下文自动建议完整的代码块来加速这些过程。同时，ChatGPT 帮助开发者理解为什么使用特定方法，并针对用例提供替代策略和定制建议。
通过简化重复性任务并提供智能指导，AI 工具桥接了结构化与非结构化数据处理之间的鸿沟，让开发者能够专注于构建更智能、更具适应性的 ML 系统。

# 自动化特征提取与选择

在机器学习中，特征是构建模型的基础。它们代表了算法学习模式、做出预测和分类数据所需的变量。然而，并非所有特征的贡献都相等；某些特征可以提高准确性并提供有价值的信号，而另一些则会引入噪声，甚至可能编码了可能误导模型的隐藏偏差。

这就是特征提取和特征选择这两个过程变得至关重要的地方。特征提取侧于从原始或非结构化数据创建新的、有意义的特征；例如从文本或时间戳生成数值指标。另一方面，特征选择涉及过滤无关或冗余的变量，确保模型仅对真正的内容进行训练。

如果操作当，这些步骤可以大幅提高模型性能、减少过拟合并加速训练，特别是处理高维数据集时。然而，手动工程和选择特征可能耗时且容易出错，需要领域知识和技术精度。

GitHub Copilot 和 ChatGPT 等 AI 辅助编程工具出现了。这些工具改变了特征工程的工作流。Copilot 可以预测转换模式并动态生成相关的代码段，而 ChatGPT 提供上下文建议，帮助你根据数据集和目标，在多项式扩展、编码策略、降维或交互项等技术之间做出选择。

无论你是构建回归模型、分类器，还是探索无监督学习，AI 工具都能协助自动化重复部分，并提升你特征工程过程的质量和效率。通过减少人工开销并支持知智决策，这些工具使开发者能够更快、更可靠地构建出更好的模型。

# 示例数据集

让我们探索一个基于员工数据集的简化示例，演示特征提取和选择在实践中是如何工作的。这个模拟数据集包含了基本的员工属性，如部门、薪水、经验、入职日期，甚至是自由文本评论。它为结构化和非结构化特征工程实验提供了一个全面的基础。
以下是数据集的创建方式：

```python
import pandas as pd
data = {
  'EmployeeID': [101, 102, 103, 104],
  'Department': ['Sales', 'HR', 'Engineering', 'HR'],
  'Salary': [58000, 62000, 72000, 60000],
  'Experience': [2, 4, 6],
  'JoinDate': ['2020-05-10', '2019-08-15', '2018-03-20', '2021-01-01'],
  'Comments': [
    'Hardworking and punctual',
    'Excellent team player',
    'Technically sound and innovative',
    'Quick learner'
  ]
}
df = pd.DataFrame(data)
```

该数据集允许我们展示几种类型的特征工程技术：

- 从文本（**Comments**）和日期（**JoinDate**）提取特征。
- 针对 **Department** 的类别编码。
- 针对 **Experience** 和 **Salary** 的数值转换或分箱。
- 特征选择以识别识别变量对下游预测的影响最大。

在接下来的子章节中，我们将应用传统和 AI 辅助方法来自动化此数据集的特征工程过程。

# 从类别和文本数据中提取特征

类别和文本特征通常包含丰富且有意义的信息，但在机器学习模型有效使用它们之前，必须将其转换为数值格式。这种转换是特征提取的核心部分，适当的技术取决于数据的性质和所用模型的复杂性。

# 传统方法

对于 **Department** 等类别变量的最常用技术之一是独热编码（one-hot encoding），它为每个类别创建一个单独的二进制列。

以下行对 **'Department'** 列应用了独热编码：

```python
# One-hot encoding for Department
df = pd.get_dummies(df, columns=['Department'], drop_first=True)
```

在处理如 **Comments** 这样的自由文本字段时，通常使用词频文档频率（TF-IDF）来提取可以输入模型的关键术。

以下代码使用 TF-IDF 从 'Comments' 列提取关键术：
```python
from sklearn.feature_extraction.text import TfidfVectorizer
vectorizer = TfidfVectorizer(stop_words='english', max_features=10)
X_text = vectorizer.fit_transform(df['Comments'])
```

TF-IDF 有助于量化每条评论中单词的重要性，同时减少了如 and、or、the 等常用词的影响。

# AI 辅助

AI 辅助工具显著地简化并丰富了这一过程：

- GitHub Copilot 可以自动建议常用转换的代码段，例如 `get_dummies()` 和 `TfidfVectorizer`，包括 `stop_words='english'` 或 `max_features` 等有用参数。
- ChatGPT 根据你的数据集和建模需求提供智能建议。例如：
  - 它可能会对有序变量建议标签编码（label encoding）。
  - 对于许多唯一值的类别列（例如超过100个），可以推荐频率编码或目标编码以避免创建过多的新列。
  - 它根据数据集大小以及你使用的模型，帮助你在 TF-IDF 和 CountVectorizer 之间做出选择。

让我们来看一个交互示例：

# 提示：如何处理具有100多个多个唯一值的类别变量？

# ChatGPT 洞察：使用频率编码或目标编码代替独热编码，以避免维度问题和内存效率低下。

通过自动化和指导这些选择，AI 工具帮助开发者从类别数据中提取有意义的特征，而不会牺牲性能或可解释性。

# 从日期和时间提取特征

时间字段通常包含原始格式中无法直接看到的价值见解。通过提取有意义的组件（如年份、月份或星期几），开发者可以发现与季节性、趋势和随时间变化的模式。这些提取的特征可以提高模型性能，特别是在销售预测、员工流失分析或网络流量预测等时间敏感的应用中。

# 传统方法

从日期列派生新特征的最常用方法是使用 Pandas 的 datetime 访问器。这是一个简单的示例：

```python
df['JoinDate'] = pd.to_datetime(df['JoinDate'])
df['JoinYear'] = df['JoinDate'].dt.year
df['JoinMonth'] = df['JoinDate'].dt.month
df['JoinDayOfWeek'] = df['JoinDate'].dt.dayofweek
```

该代码段从 JoinDate 列提取了年份、月份和星期。这些新特征可以用于下游建模任务，以理解季节性趋势、基于工作的行为等。

# ChatGPT 建议的循环编码

虽然从日期字段中提取数值是有帮助的，

