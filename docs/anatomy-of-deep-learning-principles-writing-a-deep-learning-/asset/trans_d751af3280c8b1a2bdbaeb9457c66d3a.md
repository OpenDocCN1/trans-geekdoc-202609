

## Word2Vec 模型训练与应用

### 核心训练代码

```python
train_data = generate_training_data(self.vocab, corpus, self.window)

self.train(train_data, self.vocab.n_words, self.hidden_n)

self.epsilon = 1e-8

print("Complete the training of the Word2Vec model!")
```

```python
def train(self, train_data, word_count, hidden_n):
    bound = 0.01

    self.w1 = np.random.uniform(-bound, bound, (word_count, hidden_n))
    self.w2 = np.random.uniform(-bound, bound, (hidden_n, word_count))

    for i in range(0, self.epochs):
        loss = 0
        for w_t, w_c in train_data:
            f, h, z = self.forward_pass(w_t)
            w_y = [self.vocab.index2onehot(c) for c in w_c]
            dz = np.sum([np.subtract(f, y) for y in w_y], axis=0)
            self.backprop(dz, h)  # , w_t)
            loss += np.sum([-np.sum(y * np.log(f)) for y in w_y])
        print('epoch:', i, 'loss:', loss)
```

```python
def forward_pass(self, idx):
    self.x = self.vocab.index2onehot(idx)
    # h = np.dot(self.x, self.w1)
    h = self.w1[idx, :]
    z = np.dot(h, self.w2)
    f = self.softmax(z)
    return f, h, z
```

```python
def backprop(self, dz, h):
    x = self.x
    dw2 = np.outer(h.T, dz)
    dh = np.dot(dz, self.w2.T)
    dw1 = np.outer(np.array(x).T, dh)
    self.w1 = self.w1 - (self.lr * dw1)
    self.w2 = self.w2 - (self.lr * dw2)
```

```python
def softmax(self, x):
    e_x = np.exp(x - np.max(x))
    return e_x / e_x.sum(axis=0)
```

```python
def word_vec(self, word):
    w_index = self.vocab.word2index[word]
    embeded_w = self.w1[w_index]
    return embeded_w
```

```python
def __call__(self, word):
    return self.word_vec(word)
```

### 测试示例

```python
# --- Test example -----------------------------
hidden_n = 5
window_size = 2
min_count = 0  # minimum word count
epochs = 5000  # number of training epochs
learning_rate = 0.01  # learning rate

np.random.seed(0)  # set the seed for reproducibility
corpus = ["Neural Machine Translation using word level seq2seq model".split(' ')]

# INITIALIZE W2V MODEL
w2v = Word2Vec(corpus, hidden_n, window_size, learning_rate, epochs)
print(w2v("Machine"))
```

**输出结果：**

```
Training a Word2Vec model....
epoch: 0 loss: 54.065347305478255
epoch: 1 loss: 54.06530596613177
epoch: 2 loss: 54.06526433976022
......
epoch: 4998 loss: 31.565571058450484
epoch: 4999 loss: 31.565565641922532
Complete the training of the Word2Vec model!
[-0.83213006 -2.9516065   0.14489502  0.27716055  0.85657948]
```

---

### 语料库读取与预处理

```python
MAX_LENGTH = 10

eng_prefixes = (
    "i am ", "i m ",
    "he is", "he s ",
    "she is", "she s ",
    "you are", "you re ",
    "we are", "we re ",
    "they are", "they re "
)

def filterPair(p):
    return len(p[0].split(' ')) < MAX_LENGTH and \
        len(p[1].split(' ')) < MAX_LENGTH and \
        p[1].startswith(eng_prefixes)

def filterPairs(pairs):
    return [pair for pair in pairs if filterPair(pair)]

def read_pairs(lang2lang_file, reverse=False):
    pairs = readLangs(lang2lang_file, reverse)
    print("Read %s sentence pairs" % len(pairs))
    pairs = filterPairs(pairs)
    print("Trimmed to %s sentence pairs" % len(pairs))
    return pairs

lang2lang_file = './data/eng-fra.txt'
pairs = read_pairs(lang2lang_file, True)
print(random.choice(pairs))
```

**输出结果：**

```
Reading lines...
Read 170651 sentence pairs
Trimmed to 12761 sentence pairs
['je ne le vendrai pas .', 'i m not going to sell it .']
```

---

### 句子预测库构建

```python
if True:
    pairs = pairs[:80000]

in_corpus = []
out_corpus = []

for pair in pairs:
    in_corpus.append(pair[0].split(' '))
    out_corpus.append(pair[1].split(' '))

print(in_corpus[:2])
print(out_corpus[:2])
```

**输出结果：**

```
[['j', 'ai', 'ans', '.'], ['je', 'vais', 'bien', '.']]
[['i', 'm', '.'], ['i', 'm', 'ok', '.']]
```

---

### 双语 Word2Vec 模型训练

```python
hidden_n = 150
window_size = 2
min_count = 0  # minimum word count
epochs = 1  # number of training epochs
learning_rate = 0.01  # learning rate

np.random.seed(0)  # set the seed for reproducibility

# INITIALIZE W2V MODEL
in_word2vec = Word2Vec(in_corpus, hidden_n, window_size, learning_rate, epochs)
out_word2vec = Word2Vec(out_corpus, hidden_n, window_size, learning_rate, epochs)

print(in_word2vec("peur"))
print(in_word2vec("trouble"))
```

**输出结果：**

```
Training the Word2Vec model...
```

> **注意**：此训练时间将非常长。您可以考虑使用现有的 Word2Vec 训练库，例如多线程的 `gensim` 库，因为使用 Fortran 或 C 语言中的低级线性代数库可以获得数百倍的训练加速。

**安装命令：**

```bash
pip install --upgrade gensim
```

---

### Gensim Word2Vec 使用示例

```python
import gensim

sentence = "i am from China"
sentence2 = "how old are you ?"
test_corpus = [sentence.split(" "), sentence2.split(' ')]
print(test_corpus)

hidden_n = 8
model = gensim.models.Word2Vec(test_corpus, size=hidden_n, window=2, min_count=1, workers=10, iter=10)
print('am:', model.wv['am'])
```

**输出结果：**

```
[['i', 'am', 'from', 'China'], ['how', 'old', 'are', 'you', '?']]
am: [-0.00522377  0.03762834 -0.05772045  0.02232596  0.00224983 -0.05164414
 -0.02401852 -0.01468942]
```

---

### 使用 Gensim 训练输入/输出语言模型

```python
import gensim

hidden_n = 150
window_size = 2

in_vocab = gensim.models.Word2Vec(in_corpus, size=hidden_n, window=window_size, min_count=1, workers=10, iter=10)
out_vocab = gensim.models.Word2Vec(out_corpus, size=hidden_n, window=window_size, min_count=1, workers=10, iter=10)
```

---

### 特殊字符扩展与辅助函数

由于上述训练的 Word2Vec 模型不包含特殊字符 `SOS`、`EOS` 和 `UNK`，这三个特殊词也可以添加到词表中以获得扩展词表（词表长度变为 `hidden_n + 3`）。对于这 3 个特殊词，其量化表示可直接用随机向量表示：

```python
import numpy as np

SEU_count = 3
in_SEU = np.random.rand(3, hidden_n + SEU_count)
out_SEU = np.random.rand(3, hidden_n + SEU_count)
```

以下代码定义了一些辅助函数，用于从字面句子获取索引句子和词量化表示。

`indexesFromSentence()` 将句子的单词转换为词表索引。因为 `gensim` 的模型词表不包含 3 个特殊字符，所以普通单词 `word` 在 `gensim` 词模型中的索引是 `vocab.wv.vocab[word].index`，需要加上偏移量 `SEU_count=3` 才能得到其在扩展词表中的索引。

`vocab_word2vec` 根据 `gensim` 的 Word2Vec 模型的词表索引（包含特殊字符的词表索引）序列，为每个词索引 `idx` 获取其量化表示。对于普通词，索引也应偏移到 `gensim` 词表的索引 `vocab.wv.index2word[idx - SEU_count]`。对于特殊字符，直接使用 `SEU[idx]` 获取其量化表示。

```python
def indexesFromSentence(vocab, sentence):
    return [vocab.wv.vocab[word].index + SEU_count for word in sentence.split(' ')]

def vocab_word2vec(vocab, word_indices_input, SEU, expend=False):
    x = []
    SEU_vec = np.zeros(SEU_count)
```

