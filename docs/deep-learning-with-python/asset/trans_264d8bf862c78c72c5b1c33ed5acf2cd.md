

```
model = keras.models.load_model(
    "transformer_encoder.keras",
    custom_objects={"TransformerEncoder": TransformerEncoder})
print(f"Test acc: {model.evaluate(int_test_ds)[1]:.3f}")
```

提供自定义的 TransformerEncoder 类给模型加载过程。

到了这个时候，你应该开始感到有些不安。有些不对劲。你能说出是什么问题吗？

本节表面上是关于“序列模型”的。我开头就强调了词序的重要性。我说过 Transformer 是一种序列处理架构，最初是为机器翻译而开发的。然而……你刚才看到运行的 Transformer 编码器根本就不是序列模型。你注意到了吗？它由密集层组成，这些密集层独立地处理序列标记，还有一个注意力层，它将标记视为一个集合。你可以改变序列中标记的顺序，得到的成对注意力分数和上下文感知的表示都将完全相同。如果你完全打乱每部电影评论中的单词顺序，模型不会察觉，你依然会得到完全相同的准确率。自注意力是一种集合处理机制，专注于序列元素之间成对的关系（参见图 11.10）——它对这些元素出现在序列的开头、结尾还是中间毫不在意。既然如此，我们为什么说 Transformer 是序列模型？如果它不考虑词序，又怎么可能对机器翻译有好处呢？

| | 词序感知 | 上下文感知（跨单词交互） |
|---|---|---|
| 一元词袋 | 否 | 否 |
| 二元词袋 | 非常有限 | 否 |
| RNN | 是 | 否 |
| 自注意力 | 否 | 是 |
| Transformer | 是 | 是 |

图 11.10 不同类型 NLP 模型的特性

我前面在这章里暗示过解决方案：我顺便提到过，Transformer 是一种混合方法，从技术上讲对顺序不敏感，但会在处理的表示中手动注入顺序信息。这就是缺少的成分！它被称为 _位置编码_。让我们来看看。

## 使用位置编码重新注入顺序信息

位置编码背后的想法非常简单：为了让模型获取词序信息，我们将在每个词嵌入中添加该单词在句子中的位置。我们的输入词嵌入将有两个组成部分：通常的词向量，它独立于任何特定上下文来表示单词；以及一个位置向量，它表示单词在当前句子中的位置。希望模型能够弄清楚如何最好地利用这些额外信息。

你能想到的最简单方案就是将单词的位置与其嵌入向量拼接起来。你会在向量中添加一个“位置”轴，并用序列中第一个单词的 0、第二个单词的 1 等等来填充它。

然而，这可能并不理想，因为位置可能是非常大的整数，这会破坏嵌入向量中值的范围。如你所知，神经网络不喜欢非常大的输入值或离散的输入分布。

原版“Attention is all you need”论文使用了一个有趣的技巧来编码单词位置：它向词嵌入添加了一个向量，该向量包含 [-1, 1] 范围内的值，这些值随位置周期性变化（它使用余弦函数来实现这一点）。这个技巧提供了一种方式，可以通过一个小值向量来唯一表征大范围内的任何整数。这很巧妙，但不是我们要在我们的案例中使用的方法。我们会做一些更简单、更有效的事情：我们将像学习嵌入词索引一样来学习位置嵌入向量。然后我们将把位置嵌入添加到相应的词嵌入中，以获得带有位置感知的词嵌入。这种技术称为“位置嵌入”。让我们来实现它。

## 清单 11.24 将位置嵌入实现为子类化层

```
class PositionalEmbedding(layers.Layer):
    def __init__(self, sequence_length, input_dim, output_dim, **kwargs):
        super().__init__(**kwargs)
        self.token_embeddings = layers.Embedding(
            input_dim=input_dim, output_dim=output_dim)
        self.position_embeddings = layers.Embedding(
            input_dim=sequence_length, output_dim=output_dim)
        self.sequence_length = sequence_length
        self.input_dim = input_dim
        self.output_dim = output_dim

    def call(self, inputs):
        length = tf.shape(inputs)[-1]
        positions = tf.range(start=0, limit=length, delta=1)
        embedded_tokens = self.token_embeddings(inputs)
        embedded_positions = self.position_embeddings(positions)
        return embedded_tokens + embedded_positions

    def compute_mask(self, inputs, mask=None):
        return tf.math.not_equal(inputs, 0)

    def get_config(self):
        config = super().get_config()
        config.update({
            "output_dim": self.output_dim,
            "sequence_length": self.sequence_length,
            "input_dim": self.input_dim,
        })

        return config
```

为标记索引准备一个 Embedding 层。

位置嵌入的一个缺点是序列长度需要事先知道。

还有一个用于标记位置

将两个嵌入向量相加。

实现序列化以便我们可以保存模型。

与 Embedding 层一样，这一层也应该能够生成掩码，以便我们可以忽略输入中的填充 0。compute_mask 方法会由框架自动调用，掩码会传播到下一层。

你会像使用常规 Embedding 层一样使用这个 PositionalEmbedding 层。让我们看看它的实际效果！

## 全部整合起来：一个文本分类 Transformer

要开始考虑词序，你只需要将旧的 Embedding 层替换为我们的位置感知版本即可。

## 清单 11.25 将 Transformer 编码器与位置嵌入相结合

```
vocab_size = 20000
sequence_length = 600
embed_dim = 256
num_heads = 2
dense_dim = 32

inputs = keras.Input(shape=(None,), dtype="int64")
x = PositionalEmbedding(sequence_length, vocab_size, embed_dim)(inputs)
x = TransformerEncoder(embed_dim, dense_dim, num_heads)(x)
x = layers.GlobalMaxPooling1D()(x)
x = layers.Dropout(0.5)(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop",
              loss="binary_crossentropy",
              metrics=["accuracy"])
model.summary()

callbacks = [
    keras.callbacks.ModelCheckpoint("full_transformer_encoder.keras",
                                    save_best_only=True)
]

model.fit(int_train_ds, validation_data=int_val_ds, epochs=20,
          callbacks=callbacks)
model = keras.models.load_model(
    "full_transformer_encoder.keras",
    custom_objects={"TransformerEncoder": TransformerEncoder,
                    "PositionalEmbedding": PositionalEmbedding})
print(f"Test acc: {model.evaluate(int_test_ds)[1]:.3f}")
```

我们达到了 88.3% 的测试准确率，这一显著提升清楚地证明了词序信息对于文本分类的价值。这是我们迄今为止最好的序列模型！然而，它仍然比词袋方法低一筹。

### 11.4.4 何时使用序列模型而非词袋模型

你有时可能会听到有人说，词袋方法已经过时，而基于 Transformer 的序列模型才是无论处理什么任务或数据集的首选。这绝对不是事实：在二元词袋之上堆叠一小部分 Dense 层在许多情况下仍然是一种完全有效且相关的方法。事实上，在本章中我们尝试的 IMDB 数据集的各种技术中，目前表现最好的是二元词袋！

那么，你在什么情况下应该偏好其中一种方法而非另一种呢？

2017 年，我和我的团队对各种文本分类技术在多种不同类型文本数据集上的性能进行了系统分析，发现了一条决定是使用词袋模型还是序列模型的显著且令人惊讶的经验法则（http://mng.bz/AOzK）——可以说是一种“黄金常数”。

事实证明，在处理新的文本分类任务时，你应该密切关注训练数据中样本数量与每个样本平均单词数之间的比率（参见图 11.11）。如果该比率较小——小于 1,500——那么二元词袋模型表现会更好（而且作为额外奖励，训练和迭代也会快得多）。如果该比率高于 1,500，那么你应该选择序列模型。换句话说，当有大量训练数据可用且每个样本相对较短时，序列模型效果最佳。

![](img/ab452ecf572a1f1372915be13bd8088f_373_0.png)

所以，如果你要分类每篇 1,000 字的长文档，且你有 100,000 篇（比率为 100），你应该选择二元词模型。如果你要分类平均长度为 40 个字的推文，且你有 50,000 条（比率为 1,250），你也应该选择二元词模型。但是，如果你将数据集规模增加到 500,000 条推文（比率为 12,500），就应该选择 Transformer 编码器。IMDB 电影评论分类任务呢？我们有 20,000 个训练样本，平均单词数为 233，所以我们的经验法则指向二元词模型，这证实了我们在实践中发现的情况。

这从直觉上讲得通：序列模型的输入代表一个更丰富、更复杂的空间，因此需要更多数据来映射该空间；与此同时，一个简单的术语集是一个如此简单的空间，以至于你只需几百或几千个样本就可以在其上训练逻辑回归。此外，样本越短，模型就越不能舍弃其包含的任何信息——特别是，词序变得更加重要，舍弃它可能会产生歧义。“this movie is the bomb” 和 “this movie was a bomb” 这两个句子有非常

