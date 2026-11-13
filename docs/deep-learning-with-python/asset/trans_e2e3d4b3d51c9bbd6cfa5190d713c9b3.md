

![](img/ab452ecf572a1f1372915be13bd8088f_365_0.png)

**图 11.7** 从数据库中检索图像：“查询”与一组“键”进行比较，匹配分数用于对“值”（图像）进行排序。

“tiempo”），你希望回到源句（“今天天气怎么样？”），并识别出与之相关的不同部分（“tiempo”和“weather”应该有强匹配）。而且，自然地，如果你只是做序列分类，那么query、keys和values都是一样的：你是在将一个序列与其自身进行比较，以便用整个序列的上下文来丰富每个token。

这就解释了为什么我们需要将 `inputs` 传递三次给我们的 `MultiHeadAttention` 层。但为什么是“多头”注意力呢？

## 11.4.2 多头注意力

“多头注意力”是对自注意力机制的一种额外改进，最初在“Attention is all you need”中提出。“多头”这一名称指的是：自注意力层的输出空间被分解为一组独立子空间，并分别进行学习：初始的query、key和value分别经过三组独立的全连投影，从而得到三个分离的向量。每个向量通过神经注意力进行处理，然后将三个输出拼接回一个单一的输出序列。每个这样的子空间被称为一个“head”。完整情况如图 11.8 所示。

可学习的全连投影的存在使该层能够真正学到一些东西，而不是作为一种纯粹无状态的转换（这种转换需要在前后添加额外层才能发挥作用）。此外，拥有独立的头有助于该层为每个token学习不同的特征组，其中一组内的特征彼此相关，但与不同组中的特征大多独立。

![](img/ab452ecf572a1f1372915be13bd8088f_366_0.png)

**图 11.8** MultiHeadAttention 层

这在原则上与使深度可分卷积工作原理相似：在深度可分卷积中，卷积的输出空间被分解为许多子空间（每个输入通道一个），并独立学习。“Attention is all you need”论文写于这样一个时期：将特征空间分解为独立子空间的想法已被证明对计算机视觉模型大有裨益——无论是深度可分卷积的情况，还是密切相关的分组卷积方法的情况。多头注意力只是将同一想法应用于自注意力。

## 11.4.3 Transformer 编码器

如果添加额外的全连投影如此有用，为什么不也在注意力投影机制的输出上应用一两个呢？其实，这是个好主意——那就这么办。而且我们的模型开始做很多事情了，因此我们可能想要添加残差连接，以确保在过程中不破坏任何有价值的信息——你在第 9 章中学过，它们对于任何足够深的架构都是必须的。还有，你在第 9 章中学过另一件事：归一化层应该有助于在反向传播过程中更好地传递梯度。让我们也添加那些层。

这大约就是我想象中，Transformer架构的发明者们当时脑海中展开的思考过程。将输出分解为多个独立空间、添加残差连接、添加归一化层——所有这些都是标准架构模式，在任何复杂模型中明智地利用它们都是不错的选择。这些锦上添花的功能共同构成了Transformer编码器——这是构成Transformer架构的两个关键部分之一（见图 11.9）。

![](img/ab452ecf572a1f1372915be13bd8088f_367_0.png)

图 11.9 TransformerEncoder 将 MultiHeadAttention 层与全连投影相连，并添加归一化和残差连接。

原始的Transformer架构由两部分组成：处理源序列的Transformer编码器，以及使用源序列生成译文的Transformer解码器。你稍后将了解解码器部分。

关键的是，编码器部分可用于文本分类——这是一个非常通用的模块，它接收一个序列并学习将其转换为更有用的表示形式。让我们实现一个Transformer编码器，并在电影评论情感分类任务上尝试一下。

### 代码清单 11.21 作为子类化层实现的Transformer编码器

```
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

class TransformerEncoder(layers.Layer):
    def __init__(self, embed_dim, dense_dim, num_heads, **kwargs):
        super().__init__(**kwargs)
        self.embed_dim = embed_dim
        self.dense_dim = dense_dim
        self.num_heads = num_heads
        self.attention = layers.MultiHeadAttention(
            num_heads=num_heads, key_dim=embed_dim)
        self.dense_proj = keras.Sequential(
            [layers.Dense(dense_dim, activation="relu"),
             layers.Dense(embed_dim),])
```

- 输入token向量的大小
- 内部全连层的大小
- 注意力头的数量

```
self.layernorm_1 = layers.LayerNormalization()
self.layernorm_2 = layers.LayerNormalization()

def call(self, inputs, mask=None):
    if mask is not None:
        mask = mask[:, tf.newaxis, :]
    attention_output = self.attention(
        inputs, inputs, attention_mask=mask)
    proj_input = self.layernorm_1(inputs + attention_output)
    proj_output = self.dense_proj(proj_input)
    return self.layernorm_2(proj_input + proj_output)

def get_config(self):
    config = super().get_config()
    config.update({
        "embed_dim": self.embed_dim,
        "num_heads": self.num_heads,
        "dense_dim": self.dense_dim,
    })
    return config
```

### 保存自定义层

编写自定义层时，请务必实现get_config方法：这使得层可以从其配置字典中重新实例化，在模型保存和加载期间很有用。该方法应返回一个Python字典，包含用于创建该层的构造函数参数的值。

所有Keras层都可以按如下方式进行序列化和反序列化：

```
config = layer.get_config()
new_layer = layer.__class__.from_config(config)
```

例如：

```
layer = PositionalEmbedding(sequence_length, input_dim, output_dim)
config = layer.get_config()
new_layer = PositionalEmbedding.from_config(config)
```

保存包含自定义层的模型时，保存文件将包含这些配置字典。从文件加载模型时，你应该将自定义层类提供给加载过程，以便它能理解这些配置对象：

```
model = keras.models.load_model(
    filename, custom_objects={"PositionalEmbedding": PositionalEmbedding})
```

你会注意到，我们在这里使用的归一化层不是我们之前在图像模型中使用过的BatchNormalization层。这是因为BatchNormalization不适合序列数据。相反，我们使用的是LayerNormalization层，它将批次中的每个序列与其他序列独立地进行归一化。用类NumPy的伪代码表示如下：

```
def layer_normalization(batch_of_sequences):
    mean = np.mean(batch_of_sequences, keepdims=True, axis=-1)
    variance = np.var(batch_of_sequences, keepdims=True, axis=-1)
    return (batch_of_sequences - mean) / variance
```

输入形状：(batch_size, sequence_length, embedding_dim)

计算均值和方差时，我们仅对最后一个轴（axis -1）进行数据汇聚。

与BatchNormalization（训练期间）相比：

```
def batch_normalization(batch_of_images):
    mean = np.mean(batch_of_images, keepdims=True, axis=(0, 1, 2))
    variance = np.var(batch_of_images, keepdims=True, axis=(0, 1, 2))
    return (batch_of_images - mean) / variance
```

输入形状：(batch_size, height, width, channels)

对批次轴（axis 0）进行数据汇聚，这会创建批次中样本之间的交互作用。

虽然BatchNormalization从许多样本中收集信息以获取特征均值和方差的准确统计量，但LayerNormalization在每个序列内部单独汇聚数据，这更适合序列数据。

现在我们已经实现了TransformerEncoder，可以使用它来组装一个类似于你之前见过的基于GRU的文本分类模型。

### 代码清单 11.22 使用Transformer编码器进行文本分类

```
vocab_size = 20000
emb_dim = 256
num_heads = 2
dense_dim = 32

inputs = keras.Input(shape=(None,), dtype="int64")
x = layers.Embedding(vocab_size, emb_dim)(inputs)
x = TransformerEncoder(emb_dim, dense_dim, num_heads)(x)
x = layers.GlobalMaxPooling1D()(x)
x = layers.Dropout(0.5)(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop",
    loss="binary_crossentropy",
    metrics=["accuracy"])
model.summary()
```

由于TransformerEncoder返回完整序列，我们需要通过全局池化层将每个序列缩减为单个向量以用于分类。

让我们来训练一下。它在测试集上达到87.5%的准确率——略低于GRU模型。

### 代码清单 11.23 基于Transformer编码器模型的训练与评估

```
callbacks = [
    keras.callbacks.ModelCheckpoint("transformer_encoder.keras",
        save_best_only=True)
]
model.fit(int_train_ds, validation_data=int_val_ds, epochs=20,
    callbacks=callbacks)

