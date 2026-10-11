

#### 3. 训练字符级 Seq2Seq 模型

根据数据处理后获得的训练样本集对以及前面的 Seq2Seq 模型训练代码，可以训练字符级机器翻译的 Seq2Seq 模型。以下代码定义了编码器和解码器对象 `encoder`、`decoder`，以及相应的优化器 `encoder_optimizer`、`decoder_optimizer`。并将样本集 `pairs` 划分为两个集合 `train_pairs` 和 `valid_pairs` 用于训练和验证，然后调用 Seq2Seq 模型的训练函数 `trainIters()` 来训练模型：

```
from train import *
from Layers import *
from rnn import *
import util

hidden_size = 50 #256 
num_layers = 1
clip = 5.#50.
learning_rate = 0.1
decoder_learning_ratio = 1.0 
teacher_forcing_ratio =0.5

encoder = EncoderRNN(in_verb.n_chars, hidden_size)
decoder = DecoderRNN(out_verb.n_chars,hidden_size,out_verb.n_chars,num_layers,teacher_forcing_ratio)

momentum = 0.5
decay_every  =1000

encoder_optimizer = SGD(encoder.parameters(), learning_rate, momentum,decay_every)
decoder_optimizer = SGD(decoder.parameters(), learning_rate*decoder_learning_ratio, momentum,decay_every)

reg= None#1e-2

if True:
    pairs = pairs[:80000]

np.random.shuffle(pairs)

train_n = (int)(len(pairs)*0.98)
train_pairs = pairs[:train_n]
valid_pairs = pairs[train_n:]

n_iters = 50000
print_every, plot_every = 100,100  #10,10

idx_train_pairs = [tensorsFromPair(random.choice(train_pairs))      for i in range(n_iters)]
idx_valid_pairs  =  [tensorsFromPair(pair)  for pair in valid_pairs]

trainIters(encoder, decoder,encoder_optimizer,decoder_optimizer,idx_train_pairs,idx_valid_pairs,True,print_every, plot_every,reg)
```

![图 8-54 字符序列 Seq2Seq 模型的损失曲线](EPUB/media/file168.png)

从训练损失曲线和验证损失曲线的分离情况可以看出，训练是不稳定的，损失曲线在 40,000 次后趋于平坦并略微上升。

训练好的模型可用于语言翻译。将待翻译语言的词序列（句子）输入 `encoder` 以生成输出上下文信息，该信息再输入 `decoder`。生成翻译后的词序列（句子）。

```
def evaluate(encoder,decoder,in_vocab,out_vocab,sentence,\
             max_length=MAX_LENGTH,last_Hidden = True): 
    encode_input = tensorFromSentence(in_vocab,sentence)
    encoder_output, encoder_hidden = encoder(encode_input, None)   
    if last_Hidden:
        output_sentence =  decoder.evaluate(encoder_hidden,max_length) 
    else:
        output_sentence =  decoder.evaluate(encoder_output,max_length) 
    output_sentence = indexToSentence(out_vocab,output_sentence)
    return output_sentence
```

其中，`last_Hidden` 表示 `decoder` 的输入是 `encoder` 最后一时刻的输出（隐藏向量）还是所有步的输出。

随机选择几个输入句子并使用 `evaluate` 预测翻译句子：

```
indices = np.random.randint(len(pairs), size=3)
for i in indices:
    pair = pairs[i]
    print(pair)
    sentence = pair[0]   
    sentence = evaluate(encoder, decoder,in_verb,out_verb, sentence,MAX_LENGTH)
    print(sentence)
```

```
['es tu jalouse ?', 'are you jealous ?']
are you a see  ??

['continue a courir .', 'keep running .']
come a         .

['lis ton livre !', 'read your book .']
be care it .
```

