

已经很接近了。另一种常见的转换是将特殊字符转换为标准形式，例如将“é”替换为“e”，“æ”替换为“ae”等等。我们的 token “méxico” 就会变成 “mexico”。



最后，一种更高级的标准化模式在机器学习场景中较少使用，即 _词干提取_：将一个术语的不同形式（例如动词的不同变位形式）转换为单个共享表示，例如将“caught”和“been catching”转换为 “[catch]”，或将 “cats” 转换为 “[cat]”。采用词干提取后，“was staring”和“stared”将变成类似 “[stare]” 的形式，而我们的两个相似句子最终将得到完全相同的编码：


> “sunset came i [stare] at the mexico sky isnt nature splendid”
> 

借助这些标准化技术，你的模型将需要更少的训练数据并能更好地泛化——它不再需要大量同时包含“Sunset”和“sunset”的示例来了解它们含义相同，并且即使训练集中只出现过 “mexico”，也能理解 “México”。当然，标准化也可能抹去部分信息，因此请始终注意上下文：例如，如果你正在编写一个从访谈文章中提取问题的模型，它绝对应该将 “？”视为一个独立的 token，而不是将其丢弃，因为对于这项特定任务而言，这是一个有用的信号。


## 11.2.2 文本分割（分词）

文本标准化完成后，你需要将其拆分为用于向量化的单元（token），这一步称为 _分词_。你可以采用三种不同的方式：


- 词级分词——其中 token 是由空格（或标点符号）分隔的子字符串。其一种变体是在适用时进一步将单词拆分为子词——例如，将 “staring” 视为 “star+ing”，或将 “called” 视为 “call+ed。”
- _N_-gram 分词——其中 token 是 _N_ 个连续单词的组合。例如，“the cat” 或 “he was” 将是 2-gram token（也称为 bigram）。
- 字符级分词——其中每个字符本身就是一个 token。在实践中，此方案很少使用，你通常只会在专门的语境中看到它，例如文本生成或语音识别。


一般来说，你总会使用词级分词或 N-gram 分词。文本处理模型分为两类：关注单词顺序的模型，称为 _序列模型_；以及将输入单词视为集合、丢弃其原始顺序的模型，称为 _词袋模型_。如果你构建的是序列模型，则会使用词级分词；如果你构建的是词袋模型，则会使用 N-gram 分词。N-gram 是一种人为向模型注入少量局部单词顺序信息的方法。在本章中，你将了解每种模型的更多内容以及何时使用它们。


### 理解 N-grams 和词袋

单词 N-grams 是你可以从句子中提取的 N（或更少）个连续单词的组合。同样的概念也可以应用于字符而不是单词。

以下是一个简单示例。考虑句子 “the cat sat on the mat。”它可以分解为以下 2-gram 集合：

```
{“the”, “the cat”, “cat”, “cat sat”, “sat”, “sat on”, “on”, “on the”, “the mat”, “mat”}
```

它也可以分解为以下 3-gram 集合：

```
{“the”, “the cat”, “cat”, “cat sat”, “the cat sat”, “sat”, “sat on”, “on”, “cat sat on”, “on the”, “sat on the”, “the mat”, “mat”, “on the mat”}
```

这样的集合分别称为 _2-gram 词袋_ 或 _3-gram 词袋_。这里的“bag”指的是你处理的是一组 token 而不是列表或序列：token 没有特定顺序。这类分词方法称为词袋（或 N-gram 词袋）。

由于词袋不是一种保持顺序的分词方法（生成的 token 被理解为集合而非序列，句子的整体结构丢失），它往往用于浅层语言处理模型，而非深度学习模型。提取 N-gram 是一种特征工程形式，而深度学习序列模型则舍弃了这种手动方法，取而代之的是层次特征学习。一维卷积网络、循环神经网络和 Transformer 都能在未被明确告知此类群组存在的情况下，通过观察连续的单词或字符序列，学习出单词和字符群组的表示。


## 11.2.3 词汇表索引

文本拆分为 token 后，你需要将每个 token 编码为数值表示。你理论上可以采用无状态的方式，例如将每个 token 哈希为固定二进制向量，但实际上，通常的做法是构建训练数据中所有术语的索引（“词汇表”），并为词汇表中的每个条目分配一个唯一整数。


```
vocabulary = {}
for text in dataset:
    text = standardize(text)
    tokens = tokenize(text)
    for token in tokens:
        if token not in vocabulary:
            vocabulary[token] = len(vocabulary)
```

然后，你可以将该整数转换为神经网络可处理的向量编码，例如 one-hot 向量：


```
def one_hot_encode_token(token):
    vector = np.zeros((len(vocabulary), ))
    token_index = vocabulary[token]
    vector[token_index] = 1
    return vector
```

请注意，在此步骤中，通常将词汇表限制为训练数据中出现频率最高的前 20,000 或 30,000 个单词。任何文本数据集都倾向于包含极大量的唯一术语，其中大部分只出现一两次——为这些罕见术语建立索引会导致特征空间过于庞大，其中大部分特征几乎不包含信息内容。

还记得你在第 4 章和第 5 章使用 IMDB 数据集训练第一批深度学习模型时的情形吗？你当时使用的 `keras.datasets.imdb` 数据已经预处理为整数序列，其中每个整数代表一个特定单词。当时，我们使用了 `num_words=10000` 设置，以将词汇表限制为训练数据中出现频率最高的前 10,000 个单词。

这里有一个不容忽视的重要细节：在词汇表索引中查找新 token 时，该 token 可能并不存在。你的训练数据中可能不包含单词 “cherimoya” 的任何实例（或者你可能因为它太罕见而将其从索引中排除），因此执行 `token_index = vocabulary["cherimoya"]` 可能会导致 `KeyError`。为处理这种情况，你应该使用一个“超出词汇表”索引（缩写为 _OOV 索引_，用于涵盖索引中不存在的任何 token。它通常是索引 1：你实际上是在执行 `token_index = vocabulary.get(token, 1)`。在将整数序列解码回单词时，你会将 1 替换为类似 “[UNK]” 的内容（你会称其为 “OOV token”）。

你可能会问：“为什么使用 1 而不是 0？”这是因为 0 已经被占用了。你会常用的两个特殊 token 是：OOV token（索引 1）和 _掩码标记_（索引 0）。OOV token 表示“这里有一个我们无法识别的单词”，而掩码标记则告诉我们“忽略我，我不是单词。”你尤其会用它来填充序列数据：因为数据批次需要是连续的，序列数据批次中的所有序列必须具有相同的长度，因此较短的序列应填充至最长序列的长度。如果你想用序列 [5, 7, 124, 4, 89] 和 [8, 34, 21] 制作一个数据批次，它必须是这样的：


```
[[5, 7, 124, 4, 89]
[8, 34, 21, 0, 0]]
```

你在第 4 章和第 5 章使用的 IMDB 数据集的整数序列批次就是以这种方式用零填充的。


## 11.2.4 使用 TextVectorization 层

我迄今介绍的每个步骤在纯 Python 中实现都非常简单。你也许可以编写类似下面这样的内容：


```
import string

class Vectorizer:
    def standardize(self, text):
        text = text.lower()
        return "".join(char for char in text
                       if char not in string.punctuation)

    def tokenize(self, text):
        text = self.standardize(text)
        return text.split()

    def make_vocabulary(self, dataset):
        self.vocabulary = {"": 0, "[UNK]": 1}
        for text in dataset:
            text = self.standardize(text)
            tokens = self.tokenize(text)
            for token in tokens:
                if token not in self.vocabulary:
                    self.vocabulary[token] = len(self.vocabulary)

        self.inverse_vocabulary = dict(
            (v, k) for k, v in self.vocabulary.items())

    def encode(self, text):
        text = self.standardize(text)
        tokens = self.tokenize(text)
        return [self.vocabulary.get(token, 1) for token in tokens]

    def decode(self, int_sequence):
        return " ".join(
            self.inverse_vocabulary.get(i, "[UNK]") for i in int_sequence)

vectorizer = Vectorizer()
dataset = [
    "I write, erase, rewrite",
    "Erase again, and then",
    "A poppy blooms.",
]
vectorizer.make_vocabulary(dataset)
```

![](img/ab452ecf572a1f1372915be13bd8088f_340_0.png)

它可以正常工作：


```
>>> test_sentence = "I write, rewrite, and still rewrite again"
>>> encoded_sentence = vectorizer.encode(test_sentence)
>>> print(encoded_sentence)
[2, 3, 5, 7, 1, 5, 6]
>>> decoded_sentence = vectorizer.decode(encoded_sentence)
>>> print(decoded_sentence)
"i write rewrite and [UNK] rewrite again"
```

