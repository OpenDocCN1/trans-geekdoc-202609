

## 用于 NLP 的深度学习算法

以下是用于 NLP 的深度学习算法：

- 深度学习模型，例如循环神经网络（`RNNs`）和基于 Transformer 的架构（例如，来自 Transformer 的双向编码器表示（`BERT`），已彻底改变了 NLP。
- 这些模型在机器翻译、情感分析和问答等任务中表现出色。

### 文本预处理

文本预处理是将非结构化文本转换为结构化形式以供分析的过程。它涉及分词、归一化和停用词删除等任务，以提高 NLP 任务的准确性和效率。

以下是文本预处理的一些主要组件：

- 分词：将文本分解为单词或子词单元。
- 使用 `torchtext`：`torchtext` 提供文本处理实用程序，包括分词。

以下代码片段使用 `torchtext` 中的分词器函数。它处理示例文本输入并进行分词：

```
import torchtext

from torchtext.data import get_tokenizer

tokenizer = get_tokenizer("basic_english")

sentence = "You can now install TorchText using pip!"

tokens = tokenizer(sentence)

print(tokens)

# Output: ['you', 'can', 'now', 'install', 'torchtext', 'using', 'pip', '!']
```

基本英语分词器将句子拆分为小写标记，并删除标点符号。

- 使用预训练模型：如果您正在处理更复杂的模型，例如文本到文本迁移 Transformer（`T5`），分词涉及额外步骤。

例如，`T5` 使用 SentencePiece 模型进行文本分词。

以下代码片段使用预训练的 SentencePiece 模型构建文本预处理管道：

```
from torchtext.models import T5Transform

padding_idx = 0

eos_idx = 1

max_seq_len = 512

t5_sp_model_path = "[^1^][1]"

transform = T5Transform(

sp_model_path=t5_sp_model_path,

max_seq_len=max_seq_len,

eos_idx=eos_idx,

padding_idx=padding_idx,

)
```

该管道对文本进行分词，将标记转换为整数 ID，截断序列，并添加序列结束（`EOS`）和填充标记 ID。

#### 停用词删除、词干提取和词形还原

停用词是常见词（例如，`the` 和 `in`），它们对句子的意义贡献很小。停用词删除有助于提高文本处理效率并专注于基本内容。词干提通过去除后缀将单词减少到其根形式（例如，`running` 到 `run`）。它有助于搜索引擎中的信息检索和索引。词形还原将单词转换为其基本或词典形式（例如，`better` 到 `good`）。它保留语义含义，并且比词干提取更准确。

以下代码片段使用自然语言工具包（`NLTK`）库来删除停用词：

- 使用 `NLTK` 进行停用词删除：使用以下代码：

```
import nltk

from nltk.corpus import stopwords

from nltk.tokenize import word_tokenize

nltk.download('stopwords')

nltk.download('punkt')

example_sent = "This is a sample sentence, showing off the stop words filtration."

tokens = word_tokenize(example_sent)

filtered_tokens = [word for word in tokens if word.lower() not in stopwords.words('english')]

print(filtered_tokens)

# Output: ['sample', 'sentence', ',', 'showing', 'stop', 'words', 'filtration', '.']
```

- 使用 `NLTK` 进行词形还原：词形还原将单词减少到其基本或词典形式。

以下代码片段使用 `NLTK` 库，该库提供了一个词形还原器：

```
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()

lemmatized_tokens = [lemmatizer.lemmatize(word) for word in filtered_tokens]

print(lemmatized_tokens)

# Output: ['sample', 'sentence', ',', 'showing', 'stop', 'word', 'filtration', '.']
```

- 使用 `NLTK` 进行词干提取：词干提取将单词减少到其根形式。

以下代码片段使用 `NLTK` 库，该库提供了一个词干提取器：

```
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

stemmed_tokens = [stemmer.stem(word) for word in filtered_tokens]

print(stemmed_tokens)

# Output: ['sampl', 'sentenc', ',', 'show', 'stop', 'word', 'filtrat', '.']
```

#### 处理特殊字符、标点符号和大小写敏感性

特殊字符（例如，`@`、`#`）在文本预处理期间需要被删除。它们可能会干扰分词和模型性能。

标点符号有助于检测句子边界。根据上下文，可以保留或删除标点符号。

大小写敏感性是将文本标准化为小写以保持一致性。它有助于避免重复（例如，`apple` 与 `Apple`）。

让我们来看看代码示例：

- 删除特殊字符和标点符号：以下代码片段使用正则表达式或字符串操作来删除特殊字符和标点符号：

```
import re

def remove_special_chars(text):

return re.sub(r'[^a-zA-Z0-9\s]', '', text)

cleaned_sentence = remove_special_chars(sentence)

print(cleaned_sentence)

# Output: "This is an Example Sentence"
```

- 将文本转换为小写：以下代码片段将输入文本转换为小写，如输出所示：

```
sentence = "This is an Example Sentence."

lowercased_sentence = sentence.lower()

print(lowercased_sentence)

# Output: "this is an example sentence."
```

## 文本分类

文本分类涉及将预定义的标签或类别分配给文本文档。在本章中，我们将使用 PyTorch 探索二进制和多类文本分类：

- 二进制文本分类：二进制文本分类处理只有两个可能类别的问题。示例包括垃圾邮件检测（`spam` vs. `non-spam`）或情感分析（`positive` vs. `negative`）。该方法是构建能够有效区分这两个类别的模型。PyTorch 提供了用于实现逻辑回归和其他算法的强大工具。
- 多类文本分类：多类文本分类将二进制分类扩展到处理两个以上的类别。例如，将新闻文章分类为体育、政治或娱乐等主题。可以使用一对其余或 softmax 激活等技术进行多类分类。

我们将探讨如何调整现有模型以用于此目的。

### 用于文本分类的监督学习算法

可以在 PyTorch 中使用多种算法进行文本分类。以下是可以使用 PyTorch 调整用于文本分类的算法列表：

- 逻辑回归：它是一种常用于文本分类的线性模型。它模拟文档属于特定类别的概率。在 PyTorch 中，我们可以使用单层神经网络实现逻辑回归。
- 支持向量机（`SVM`）：`SVMs` 可以使用适当的核函数（例如，线性和径向基函数）针对文本分类进行定制。它们找到最佳分隔高维空间中文本特征的超平面。PyTorch 库允许我们实现类似 `SVM` 的模型。
- 用于文本分类的神经网络：神经网络为解决文本分类任务提供了多功能的架构范围，每种架构都适合捕捉文本数据的不同方面，以实现有效的学习和预测。
- 模型架构：以下是用于文本分类的一些关键神经网络架构类型：

  - 带有隐藏层的前馈神经网络（`FNNs`）从文本数据中学习复杂的表示。
  - 卷积神经网络（`CNNs`）捕捉文本中的局部模式（例如，n-gram）。
  - `RNNs` 处理顺序数据（例如，句子和文档）。

### 用于文本分类的评估指标

可以使用不同的评估指标进行文本分类。以下是一些重要且流行的评估指标：

