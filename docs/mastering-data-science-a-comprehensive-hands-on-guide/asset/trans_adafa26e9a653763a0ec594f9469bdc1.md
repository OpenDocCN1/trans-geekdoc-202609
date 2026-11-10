
# 文本预处理和分词

文本预处理是在准备原始文本数据进行分析时必不可少的一步，它确保一致性，同时消除可能阻碍模型性能的噪声或无关信息。该过程涉及将文本转换为更统一和结构化的格式，使其更易于分析、处理或用于机器学习模型。

## 文本预处理的关键步骤

小写转换：将所有字符转换为小写，以避免将“Hello”和“hello”等词视为不同实体，从而消除大小写敏感性。示例："Hello World" → "hello world"

去除标点符号：从文本中消除标点符号（如逗号、句号或感叹号），因为它们通常不为词的含义做出贡献。示例："Hello, world!" → "Hello world"

去除停用词：停用词如“the”、“a”和“in”出现频率很高，但在文本分析的上下文中通常语义意义最小。去除它们有助于关注更有意义的词。示例："This is a great day" → "great day"

词干提取和词形还原：这两种技术都用于将词还原为其词根形式，但方法不同：
• 词干提取：通过剥离后缀来缩减词， often  resulting in a root form that may not always be a real word. 示例："running," "runner" → "run"
• 词形还原：使用语法和词汇规则将词还原为其基本或词典形式，确保结果始终是一个有效词。示例："running" → "run," "better" → "good"

分词：分词将文本拆分为较小的单元，如词、句子甚至字符。这对进一步处理和分析至关重要。示例："Hello World" → `["Hello", "World"]`

去除数字：除非数字对分析至关重要（如处理财务数据时），通常会被去除。示例："I have 2 apples" → "I have apples"

处理特殊字符：特殊字符，包括 @、# 或 URL，通常根据分析目的进行去除或处理。示例："@hello" → "hello" 或 "http://example.com" → "example"

文本规范化：这涉及通过将非正式语言、缩写或俚语转换为更正式、一致的表达来标准化文本。示例："lol" → "laugh out loud" 或 "u" → "you"

这些预处理步骤有助于将原始文本转换为可用于文本挖掘、情感分析或其他类型的自然语言处理（NLP）任务的形式。

## 23.1.2 分词

分词是自然语言处理（NLP）中的关键步骤，其中文本被拆分为称为 token 的较小单元，这些单元更易于模型处理。这些 token 可以根据任务的不同而范围从词、子词、句子甚至单个字符。通过将文本分解为这些较小单元，分词允许进行更细粒度的分析，使模型更容易理解文本的结构和含义。

### 分词类型

词分词：这是最常见的分词形式，其中文本被拆分为单个词。例如，句子 "Natural Language Processing" 被拆分为 token `["Natural", "Language", "Processing"]`。该方法简单明了，在文本直接时效果良好，但在包含标点或复合词的词上可能会遇到挑战。

句子分词：在句子分词中，文本被分解为句子。这对于需要理解较长文本结构等任务非常有帮助，例如文档摘要或句子级情感分析。例如，文本 "Hello world. How are you?" 将被分词为 `["Hello world.", "How are you?"]`。

子词分词：该技术将词分解为较小的有意义部分（子词），特别适用于处理罕见词或不在词汇表中的词。子词分词在像 BERT 和 GPT 这样的基于 Transformer 的模型中广泛使用，其中词 "processing" 可能会被分词为较小的部分如 `["proc", "ess", "ing"]`。这种方法通过在子词级别识别模式，帮助模型更好地泛化到未见词。

字符分词：这里，文本被划分为单个字符而不是词或子词。该方法对于字符级语言建模等任务很有用，在这些任务中理解单个字母的模式很重要。例如，"NLP" 将被分词为 `["N", "L", "P"]`。

这些分词方法可以根据 NLP 任务的复杂性和要求组合使用。分词策略的选择对模型性能有重大影响，因为它决定了文本被分析的粒度以及模型处理语言变化的能力。

### 分词工具

NLTK（自然语言工具包）：一个流行的用于文本预处理的 Python 库。

示例：
```python
from nltk.tokenize import word_tokenize

text = "Hello, world! This is NLP."

tokens = word_tokenize(text)

print(tokens)  # Output: ['Hello', ',', 'world', '!', 'This', 'is', 'NLP', '.']
```

SpaCy：一个具有先进分词能力的快速 NLP 库。

示例：
```python
import spacy

nlp = spacy.load("en_core_web_sm")

text = "Hello, world! This is NLP."

doc = nlp(text)

tokens = [token.text for token in doc]

print(tokens)  # Output: ['Hello', ',', 'world', '!', 'This', 'is', 'NLP', '.']
```

Hugging Face Tokenizers：提供针对 Transformer 模型优化的子词分词。

示例：
```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

tokens = tokenizer.tokenize("Hello, world! This is NLP.")

print(tokens)  # Output: ['hello', ',', 'world', '!', 'this', 'is', 'nlp', '.']
```

Gensim：常用于词嵌入和主题建模。

示例：
```python
from gensim.utils import simple_preprocess

tokens = simple_preprocess("Hello, world! This is NLP.")

print(tokens)  # Output: ['hello', 'world', 'this', 'is', 'nlp']
```

## 23.1.3 高级分词技术

字节对编码（BPE）：字节对编码（BPE）是一种子词分词方法，它将罕见词拆分为更频繁的子词单元，同时保留常见词。它首先将字符编码为 token 并迭代合并最频繁的字符或子词单元对。该技术在减少词汇表大小和有效处理未知或罕见词方面特别有用。BPE 已在 GPT 和 BERT 等模型中广泛使用，其中它允许模型在保持训练和推理效率的同时处理大量文本。例如，词 "unhappiness" 可能会被拆分为 "un"、"happiness" 或进一步拆分为 "un"、"h"、"appiness" 等子词，具体取决于 token 对的频率。

WordPiece 分词：WordPiece 分词由 Google 引入，是另一种将词分解为子词单元的技术。它通过将词表示为子词单元序列来确保更有效地使用词汇表，这在处理未知词和减少整体词汇表大小方面是有益的。例如，词 "unbelievable" 可能会被拆分为 token `["un", "##believable"]`，其中 "##" 表示部分 "believable" 是根 "un" 的延续。这种方法确保即使模型在训练期间未遇到 "unbelievable"，它仍可以根据其子词处理该词，从而促进更好的泛化。
