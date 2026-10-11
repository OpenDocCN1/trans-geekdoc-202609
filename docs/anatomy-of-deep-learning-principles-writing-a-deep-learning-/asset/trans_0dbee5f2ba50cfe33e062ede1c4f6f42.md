

![](EPUB/media/file159.png "fig:")
图 7-32 股票数据训练模型的短期预测效果

## 7.5 RNN 语言模型与文本生成

在 k-gram 语言模型中，每个词仅依赖于前面的 k-1 个词。由于无法利用更多的上下文信息，这限制了模型的准确性。RNN 模型可以接受任意长度的输入序列。使用 RNN 表示语言模型，可以从任意长度的输入词序列中预测词表中每个词作为下一个词的概率。即在时刻 `t=i`，基于时刻 `t` 之前的所有词，预测时刻 `t=i+1` 出现该词的概率：`P(w[i+1] | w[1], w[2], ..., w[i])`。

根据该概率，采样一个词作为下一个词，并不断重复此过程。即可从初始词连续生成新词，也就是生成一系列词或文本。这种基于某种语言模型，从初始的一个或少量词自动生成大段文本的过程称为**文本生成**。

文本生成依赖于训练好的语言模型。要训练语言模型，需要从现有的文本（如一部或多部小说、散文）中以词为单位采样序列数据。这些用于采样词序列样本的原始文本称为**语料库**。这些语料通常首先按词为单位划分为词序列，然后利用前面的序列数据采样方法采样出用于训练 RNN 模型的序列样本。

对于英文文章，原文可以用空格和标点符号划分为词序列；而对于中文字符文本，则需要使用一些特殊的分词技术从文本中分割提取词语。无论何种语言，词的数量都非常大。为简化起见，可以将每个字符视为一个词。这样的语言模型称为**字符语言模型**。字符语言模型无需专门提取文本中的词，且语言中的字符数量通常远小于词的数量。例如，英语只有 26 个字母和少量标点符号，而英语单词的数量却非常庞大。

无论是字符语言模型还是普通的词语言模型，其原理都是相同的。例如，在使用 RNN 训练语言模型之前，需要量化语言模型的基本单位——词或字符，即将词或字符转换为值向量。为了量化词（字符），第一步是建立词表（字符表）。

### 7.5.1 字符表

构建词表或字符表的过程是扫描语料库中的所有文本，找出所有的词或字符，并将它们放入一个线性表中，使每个词（字符）在表中都有一个确定的位置（下标）。对于字符语言模型，只需扫描语料库文本中的所有字符并将其放入字符表即可。

如果语料库仅包含一个文本文件 `input.txt`（莎士比亚的剧本），以下代码将文本内容读入 `data`，并使用 `set(data)` 构建所有不同字符的集合。然后将这些不同字符放入列表对象 `chars` 中（`chars = list(set(data))`），该列表对象即为所有字符的字符表。

```
filename = 'input.txt'

data = open(filename, 'r').read()

chars = list(set(data))
```

输出文本中所有字符的数量、字符列表的长度、字符列表的前 10 个字符以及文本的前 148 个字符：

```
data_size, vocab_size = len(data), len(chars)

print ('Total number of characters %d, length of character table %d unique.' % (data_size, vocab_size))

print('First 10 characters of the character table: \n', chars[:10])

print('First 148 characters: \n', data[:148])
```

```
    字符总数为 1115394，字符列表长度为 65 个唯一字符。

    字符表的前 10 个字符：

     ['t', 'z', 'A', 'Y', 'm', ' ', 'B', 'g', 'r', '.']

    前 148 个字符：

     First Citizen:

    Before we proceed any further, hear me speak.

    All:

    Speak, speak.

    First Citizen:

    You are all resolved rather to die than to famish?
```

字符表中的每个字符对应一个下标，可以使用两个字典来表示字符到下标和下标到字符的映射关系：

```
char_to_idx = { ch:i for i,ch in enumerate(chars) }

idx_to_char = { i:ch for i,ch in enumerate(chars) }
```

有了字符表，就可以量化每个字符。最简单的方法是根据字符在字符表中的下标，用独热向量来表示字符。独热向量的长度等于字符表的长度。除该字符对应下标的值为 1 外，该向量其余位置均为 0。如果字符表只有四个字符，如图 7-33 所示：

图 7-33 字符表中只有 4 个字符：'h','e','l','o'

字符 'e' 的下标为 1，因此其独热向量为 (0,1,0,0)。

函数 `one_hot_idx` 根据字符（词）表大小 `vocab_size` 和字符在字符（词）表中的下标 `idx`，将字符转换为独热向量：

```
def one_hot_idx(idx, vocab_size):  
    x = np.zeros((1, vocab_size)) 
    x[0, idx] = 1  
    return x
```

### 7.5.2 字符序列样本的采样

为了训练字符语言模型，需要一些训练样本。与前面的序列数据采样过程类似，可以从原始文本中采样字符序列样本。以下代码以顺序采样的方式采样字符序列样本：

```
import numpy as np

def character_seq_data_iter_consecutive(data, batch_size, seq_len, start_range=10):
    # 每次在 data[offset:] 中采样，使每个 epoch 的训练样本不同
    start = np.random.randint(0, start_range)
    block_len = (len(data) - start - 1) // batch_size
    num_batches = block_len // seq_len  # 每个块中可连续采样的最大批次数
    bs = np.array(range(0, block_len * batch_size, block_len))  # 每个块的起始位置
    i_end = num_batches * seq_len
    for i in range(0, i_end, seq_len):  # 一个块的序列起始位置
        s = start + i  # 块中的位置
        X = np.empty((seq_len, batch_size), dtype=object)  # ,dtype=np.int32)
        Y = np.empty((seq_len, batch_size), dtype=object)  # ,dtype=np.int32)
        for b in range(batch_size):  # b 表示一个批次样本的样本数
            s_b = s + bs[b]
            for t in range(seq_len):
                X[t, b] = data[s_b]
                Y[t, b] = data[s_b + 1]
                s_b += 1
        if i == 0:
            yield X, Y, True
        else:
            yield X, Y, False
```

测试该函数：

```
x = 'Li,where are you from'
batch_size = 2
seq_length  = 3
data_it = character_seq_data_iter_consecutive(x, batch_size, seq_length, 1)
i = 0 
for x, y, _ in data_it:
    print("x:", x)
    print("y", y)
    i += 1
    if i == 2: break
```

```
    x: [['L' 'r']
     ['i' 'e']
     [',' ' ']]
    y [['i' 'e']
     [',' ' ']
     ['w' 'y']]
    x: [['w' 'y']
     ['h' 'o']
     ['e' 'u']]
    y [['h' 'o']
     ['e' 'u']
     ['r' ' ']]
```

函数返回的字符还需要进一步向量化，例如将每个字符转换为独热向量形式。为此，修改上述函数：

