
# Word2Vec 模型训练

为了获得合适的词潜在向量表示以反映词之间的相关性（如同义词），需要使用自编码器训练该权重矩阵。与自编码器类似，隐藏向量通过 `W[W[N×V]]` 转换为与词表长度相同的输出向量。该输出向量的每个分量 `p[i]` 代表第 `i` 个词的得分，可通过 softmax 函数转换为概率。为了训练该神经网络模型，CBOW 和 Skip-gram 使用不同方法从由大量句子组成的语料库中生成训练样本。

编码器和解码器均为无偏置、无激活函数的全连接层，即仅有一个权重矩阵。因此，该 2 层神经网络包含 2 个权重矩阵，可用简化的图 8-56 表示：

**图 8-56 简化的词量化神经网络，编码器和解码器仅为一个权重矩阵**

其工作过程类似于自编码器。第一个全连接线性层是一个无偏置的权重矩阵 `W[1]`，将输入词的独热向量 `x` 转换为低维嵌入表示 `h = xW[1]`，该 `h` 即为词 `x` 的量化表示。为训练权重矩阵 `W[1]`，将 `h` 通过另一个无偏置、无激活函数的全连接线性层（即权重矩阵 `W[2]`），输出所有词得分的向量 `f = hW[2]`。训练过程中，将该 `f` 与目标词比较得到损失误差，并通过这些损失误差的反向传播更新模型参数。

如图 8-57 所示，对于句子中的一个词，若记为 `w[t]`（即中心词或目标词），CBOW 使用其上下文或周围词作为输入。例如，若上下文窗口 `C` 设为 `C = 5`，输入将为位置 `w[t-2]`、`w[t-1]`、`w[t+1]` 和 `w[t+2]` 处的词，即中心词 `w[t]` 前后各两个词。将某中心词 `w[t]` 的上下文词（`w[t-2]`、`w[t-1]`、`w[t+1]`、`w[t+2]`）输入网络，CBOW 期望输出的预测词 `w[p]` 为目标词 `w[t]`。通过计算预测词 `w[p]` 与目标词 `w[t]` 的交叉熵损失来训练网络。

**图 8-57 CBOW 以词的上下文（周围词）作为编码器输入，解码器输出词表词的得分，得分最高的目标词应为中心词**

与 CBOW 利用句子中词的上下文预测该词相反，Skip-gram 利用词 `w[t]` 预测其上下文词 `w[t-2]`、`w[t-1]`、`w[t+1]`、`w[t+2]`，如图 8-58 所示。即输入词 `w[t]` 的独热向量，通过编码器得到隐藏向量 `h[N]`，再通过解码器输出与词表等长的向量，表示词表中每个词的得分。得分可通过 softmax 函数转为概率，以上下文词为目标词计算交叉熵损失，从而训练编码器和解码器。

**图 8-58 Skip-gram 以词作为编码器输入，解码器输出词表词的得分，得分最高的应为该词的上下文词，即上下文词为目标词**

CBOW 和 Skip-gram 均利用语料库中的句子生成训练样本。对于 Skip-gram 方法，句子中的每个词作为中心词，每个上下文词作为目标词形成一个训练样本。

例如，对于句子 "Seq2Seq is a general purpose encoder decoder framework"，第一个词 "Seq2Seq" 的上下文词为 "is" 和 "a"，则得到 2 个训练样本 (Seq2Seq, is) 和 (Seq2Seq, a)，如图 8-59 所示。同理，第二个词 "is" 的上下文词为 "seq2seq"、"a"、"general"，得到三个样本 (is, Seq2Seq)、(is, a)、(is, general)。以此类推，最后一个词 "framework" 可得到样本 (framework, encoder) 和 (framework, decoder)。

**图 8-59 Skip-gram 针对句子 "Seq2Seq is a general purpose encoder decoder framework" 生成的训练样本**

CBOW 和 Skip-gram 各有优劣。CBOW 适用于词汇量较小的语言模型，能较好表示稀有词；Skip-gram 适用于词汇量大的语言模型，能更好表示高频词。

以下代码以 skip-gram 为例说明如何实现该模型的训练过程。对于 skip-gram，输入为当前中心词，目标为上下文词，但因存在多个上下文词（即多个目标），每个目标词需与 `f = hW[2]` 计算一个交叉熵损失。

类似地，定义 `wordlist` 表示语言中的所有词，可从语料库句子构建：

```python
class Vocab:

    def __init__(self, corpus):

        wordset = set()

        for sentence in corpus:

            if isinstance(sentence, str):

                for word in sentence.split(' '):

                    wordset.add(word)

            else:

                for word in sentence:

                    wordset.add(word)

        wordlist = list(wordset)

        self.word2index = dict([(word, i) for i, word in enumerate(wordset)])

        self.index2word = dict([(i, word) for i, word in enumerate(wordset)])

        self.n_words = len(wordset)

    def index2onehot(self, idx):

        x = np.zeros((1, self.n_words))

        x[0, idx] = 1

        return x

corpus = ["i am from china",]

vocab = Vocab(corpus)

print(vocab.word2index)

print(vocab.word2index["am"])

print(vocab.index2word)

print(vocab.index2word[3])
```

```
{'china': 0, 'am': 1, 'i': 2, 'from': 3}
1
{0: 'china', 1: 'am', 2: 'i', 3: 'from'}
from
```

可读取语料库文件中的所有句子构建词表，并基于词表和语料库中的句子生成训练 Word2Vec 模型的训练样本。函数 `generate_training_data()` 根据由词表 `vocab` 和句子组成的语料库 `corpus` 以及采样窗口大小 `window`，采样用于训练 Word2Vec 模型的样本：

```python
def generate_training_data(vocab, corpus, window=2):

    training_data = []

    for sentence in corpus:  # for each sentence

        sent_len = len(sentence)

        for i, word in enumerate(sentence):  # for each word in the sentence

            w_target = vocab.word2index[sentence[i]]

            w_context = []

            for j in range(i - window, i + window + 1):

                if j != i and j <= sent_len - 1 and j >= 0:

                    w_context.append(vocab.word2index[sentence[j]])

            training_data.append([w_target, w_context])

    return np.array(training_data)

corpus = [["i", "am", "from", "china"]]

generate_training_data(vocab, corpus)
```

```
array([[2, list([1, 3])],
       [1, list([2, 3, 0])],
       [3, list([2, 1, 0])],
       [0, list([1, 3])]], dtype=object)
```

可在词表和语料库基础上训练 Word2Vec 模型，以下类 `Word2Vec` 为其代码实现：

```python
class Word2Vec():

    def __init__(self, corpus, hidden_n, window, learning_rate=0.01, epochs=5000):

        self.hidden_n = hidden_n

        self.window = window

        self.lr = learning_rate

        self.epochs = epochs

        self.vocab = Vocab(corpus)

        print("Training a Word2Vec model....")
```
