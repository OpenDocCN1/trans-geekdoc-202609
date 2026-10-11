

```python
if word not in self.word2count:
    self.word2count[word] = 1
else:
    self.word2count[word] += 1

def build(self):
    for word in self.word2count:
        if self.word2count[word] < self.min_count:
            self.word2index[word] = UNK_token
        else:
            self.word2index[word] = self.n_words
            self.index2word[self.n_words] = word
            self.n_words += 1

vocab = Vocab()
vocab.addSentence("i am from china")
vocab.build()

print(vocab.word2index["i"])
print(vocab.index2word[4])
```

```
3
am
```

为输入和输出语言创建词表对象 `in_vocab` 和 `out_vocab`：

```python
in_vocab = Vocab()
out_vocab = Vocab()

lang2lang_file = './data/eng-fra.txt'
pairs = read_pairs(lang2lang_file, True)

for pair in pairs:
    in_vocab.addSentence(pair[0])
    out_vocab.addSentence(pair[1])

in_vocab.build()
out_vocab.build()

def indexesFromSentence(vocab, sentence):
    return [vocab.word2index[word] for word in sentence.split(' ')]

def tensorFromSentence(vocab, sentence):
    indexes = indexesFromSentence(vocab, sentence)
    indexes.append(EOS_token)
    return np.array(indexes).reshape(-1, 1)

def tensorsFromPair(pair):
    input_tensor = tensorFromSentence(in_vocab, pair[0])
    target_tensor = tensorFromSentence(out_vocab, pair[1])
    return (input_tensor, target_tensor)

def indexToSentence(vocab, indexes):
    sentense = [vocab.index2word[idx] for idx in indexes]
    return ' '.join(sentense)

# input_tensor, target_tensor = tensorsFromPair(random.choice(pairs))
# print(input_tensor.shape)
# print(input_tensor)
# print(target_tensor)
```

### 基于词嵌入的 Seq2Seq 模型的训练过程与之前的类似：

```python
from train import *
from Layers import *
from rnn import *
import util

hidden_size = 256
num_layers = 1
clip = 5.  # 50.
learning_rate = 0.03
decoder_learning_ratio = 1.0
teacher_forcing_ratio = 0.5
output_size = out_vocab.n_words  # num of words

encoder = EncoderRNN_Embed(in_vocab.n_words, hidden_size)
decoder = DecoderRNN_Embed(hidden_size, out_vocab.n_words, num_layers, teacher_forcing_ratio)

momentum = 0.3
decay_every = 1000

encoder_optimizer = SGD(encoder.parameters(), learning_rate, momentum, decay_every)
decoder_optimizer = SGD(decoder.parameters(), learning_rate * decoder_learning_ratio, momentum, decay_every)

reg = None  # 1e-2

np.random.shuffle(pairs)
train_n = int(len(pairs) * 0.98)
train_pairs = pairs[:train_n]
valid_pairs = pairs[train_n:]

print_every, plot_every = 100, 100  # 10, 10
n_iters = 40000

idx_train_pairs = [tensorsFromPair(random.choice(train_pairs)) for i in range(n_iters)]
idx_valid_pairs = [tensorsFromPair(pair) for pair in valid_pairs]

trainIters(encoder, decoder, encoder_optimizer, decoder_optimizer, idx_train_pairs, idx_valid_pairs, True, print_every, plot_every, reg)
```

![](EPUB/media/file170.png "fig:")
图 8-55 词嵌入层 Seq2Seq 模型的训练和验证损失曲线

### 进行预测：

```python
indices = np.random.randint(len(train_pairs), size=3)

for i in indices:
    pair = pairs[i]
    print(pair)
    sentence = pair[0]
    sentence = evaluate(encoder, decoder, in_vocab, out_vocab, sentence, MAX_LENGTH)
    print(sentence)
```

```
['c est une vraie commere .', 'she is a confirmed gossip .']
she is a total . .

['nous sommes meilleures qu elles .', 'we re better than they are .']
we re better than they are .

['tu es curieux hein ?', 'you are curious aren t you ?']
you are curious right ?
```

