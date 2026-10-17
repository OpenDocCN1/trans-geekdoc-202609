

```
w2v.similarity('I', 'My')
```

```
0.082851942583535218
```

```
print(posts[5])
w2v.similarity('ring', 'husband')
```

```
I've tried starting blog after blog and it just never feels right.  Then I read today that it feels strange to most people, but the more you do it the better it gets (hmm, sounds suspiciously like something else!) so I decided to give it another try.    My husband bought me a notepad at  urlLink McNally  (the best bookstore in Western Canada) with that title and a picture of a 50s housewife grinning desperately.  Each page has something funny like "New curtains!  Hurrah!".  For some reason it struck me as absolutely hilarious and has stuck in my head ever since.  What were those women thinking?





0.037229111896779618
```

```
w2v.similarity('ring', 'housewife')
```

```
0.11547398696865138
```

```
w2v.similarity('women', 'housewife')  # Diversity friendly
```

```
-0.14627530812290576
```

## Doc2Vec

与 word2vec 相同的技术被推广到文档中。在这里，我们做了 word2vec 中的所有工作 + 我们也对文档进行向量化

```
import numpy as np
```

```
# 0 for male, 1 for female
y_posts = np.concatenate((np.zeros(len(filtered_male_posts)),
                          np.ones(len(filtered_female_posts))))
```

```
len(y_posts)
```

```
4842
```

# 用于句子分类的卷积神经网络

训练卷积网络用于情感分析。

基于 Yoon Kim 的 "Convolutional Neural Networks for Sentence Classification" [http://arxiv.org/pdf/1408.5882v2.pdf](http://arxiv.org/pdf/1408.5882v2.pdf)

对于 `CNN-non-static`，在 61 个 epoch 后达到 82.1%，设置如下：`embedding_dim = 20`  

`filter_sizes = (3, 4)` `num_filters = 3` `dropout_prob = (0.7, 0.8)` `hidden_dims = 100`

对于 `CNN-rand`，在 7-8 个 epoch 后达到 78-79%，设置如下：`embedding_dim = 20`  

`filter_sizes = (3, 4)` `num_filters = 150` `dropout_prob = (0.25, 0.5)` `hidden_dims = 150`

对于 `CNN-static`，在 7 个 epoch 后达到 75.4%，设置如下：`embedding_dim = 100`  

`filter_sizes = (3, 4)` `num_filters = 150` `dropout_prob = (0.25, 0.5)` `hidden_dims = 150`

*   事实证明，像 "Movie reviews with one sentence per review"（Pang and Lee, 2005）这样小的数据集，所需的网络远小于原始文章中介绍的网络：

*   嵌入维度仅为 20（而不是 300；`CNN-static` 仍然需要 ~100）

*   2 个滤波器尺寸（而不是 3）

*   较高的 dropout 概率，以及

*   每个滤波器尺寸 3 个滤波器对于 `CNN-non-static` 就足够了（而不是 100）

*   嵌入初始化不需要预构建的 Google Word2Vec 数据。在相同的 "Movie reviews" 数据集上训练 Word2Vec 就足以达到文章中报告的性能（81.6%）

** 另一个明显的区别是使用长度为 2 的滑动 MaxPooling 窗口，而不是像文章中那样对整个特征图进行 MaxPooling

```
import numpy as np
import word_embedding
from word2vec import train_word2vec

from keras.models import Sequential, Model
from keras.layers import (Activation, Dense, Dropout, Embedding, 
                          Flatten, Input, 
                          Conv1D, MaxPooling1D)
from keras.layers.merge import Concatenate

np.random.seed(2)
```

```
Using gpu device 0: GeForce GTX 760 (CNMeM is enabled with initial size: 90.0% of memory, cuDNN 4007)
Using Theano backend.
```

### 参数

模型变体。有关详细信息，请参阅 Kim Yoon 的 Convolutional Neural Networks for Sentence Classification，第 3 节。

```
model_variation = 'CNN-rand'  #  CNN-rand | CNN-non-static | CNN-static
print('Model variation is %s' % model_variation)
```

```
Model variation is CNN-rand
```

```
# Model Hyperparameters
sequence_length = 56
embedding_dim = 20          
filter_sizes = (3, 4)
num_filters = 150
dropout_prob = (0.25, 0.5)
hidden_dims = 150
```

```
# Training parameters
batch_size = 32
num_epochs = 100
val_split = 0.1
```

```
# Word2Vec parameters, see train_word2vec
min_word_count = 1  # Minimum word count                        
context = 10        # Context window size
```

### 数据准备

```
# Load data
print("Loading data...")
x, y, vocabulary, vocabulary_inv = word_embedding.load_data()

if model_variation=='CNN-non-static' or model_variation=='CNN-static':
    embedding_weights = train_word2vec(x, vocabulary_inv, 
                                       embedding_dim, min_word_count, 
                                       context)
    if model_variation=='CNN-static':
        x = embedding_weights[0][x]
elif model_variation=='CNN-rand':
    embedding_weights = None
else:
    raise ValueError('Unknown model variation')
```

```
Loading data...
```

```
# Shuffle data
shuffle_indices = np.random.permutation(np.arange(len(y)))
x_shuffled = x[shuffle_indices]
y_shuffled = y[shuffle_indices].argmax(axis=1)
```

```
print("Vocabulary Size: {:d}".format(len(vocabulary)))
```

```
Vocabulary Size: 18765
```

### 构建 CNN 模型

```
graph_in = Input(shape=(sequence_length, embedding_dim))
convs = []
for fsz in filter_sizes:
    conv = Conv1D(filters=num_filters,
                  filter_length=fsz,
                  padding='valid',
                  activation='relu',
                  strides=1)(graph_in)
    pool = MaxPooling1D(pool_length=2)(conv)
    flatten = Flatten()(pool)
    convs.append(flatten)

if len(filter_sizes)>1:
    out = Concatenate()(convs)
else:
    out = convs[0]

graph = Model(input=graph_in, output=out)

# main sequential model
model = Sequential()
if not model_variation=='CNN-static':
    model.add(Embedding(len(vocabulary), embedding_dim, input_length=sequence_length,
                        weights=embedding_weights))
model.add(Dropout(dropout_prob[0], input_shape=(sequence_length, embedding_dim)))
model.add(graph)
model.add(Dense(hidden_dims))
model.add(Dropout(dropout_prob[1]))
model.add(Activation('relu'))
model.add(Dense(1))
model.add(Activation('sigmoid'))
```

```
model.compile(loss='binary_crossentropy', optimizer='rmsprop', 
              metrics=['accuracy'])

# Training model
# ==================================================
model.fit(x_shuffled, y_shuffled, batch_size=batch_size,
          nb_epoch=num_epochs, validation_split=val_split, verbose=2)
```

