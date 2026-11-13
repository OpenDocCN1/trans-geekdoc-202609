
接下来，让我们通过将 20% 的训练文本文件单独放入新目录 aclImdb/val 中来准备验证集：

```
import os, pathlib, shutil, random
base_dir = pathlib.Path("aclImdb")
val_dir = base_dir / "val"
train_dir = base_dir / "train"
for category in ("neg", "pos"):
    os.makedirs(val_dir / category)
    files = os.listdir(train_dir / category)
    random.Random(1337).shuffle(files)
    num_val_samples = int(0.2 * len(files))
    val_files = files[:num_val_samples]
    for fname in val_files:
        shutil.move(train_dir / category / fname,
                    val_dir / category / fname)
```

还记得在第 8 章中，我们如何使用 `image_dataset_from_directory` 实用程序为目录结构创建图像及其标签的批量 Dataset 吗？你可以对文本文件做完全相同的事，使用 `text_dataset_from_directory` 实用程序。让我们创建三个用于训练、验证和测试的 Dataset 对象：

```
from tensorflow import keras
batch_size = 32
train_ds = keras.utils.text_dataset_from_directory(
    "aclImdb/train", batch_size=batch_size
)
val_ds = keras.utils.text_dataset_from_directory(
    "aclImdb/val", batch_size=batch_size
)
test_ds = keras.utils.text_dataset_from_directory(
    "aclImdb/test", batch_size=batch_size
)
```

这些数据集产生的输入是 TensorFlow `tf.string` 张量，目标是编码值 “0” 或 “1” 的 int32 张量。

### 代码清单 11.2 显示第一批数据的形状和数据类型

```
>>> for inputs, targets in train_ds:
>>>     print("inputs.shape:", inputs.shape)
>>>     print("inputs.dtype:", inputs.dtype)
>>>     print("targets.shape:", targets.shape)
>>>     print("targets.dtype:", targets.dtype)
>>>     print("inputs[0]:", inputs[0])
>>>     print("targets[0]:", targets[0])
>>>     break
inputs.shape: (32,)
inputs.dtype: <dtype: "string">
targets.shape: (32,)
targets.dtype: <dtype: "int32">
inputs[0]: tf.Tensor(b"This string contains the movie review.", shape=(),
 dtype=string)
targets[0]: tf.Tensor(1, shape=(), dtype=int32)
```

一切就绪。现在让我们尝试从这些数据中学习一些东西。

## 11.3.2 将单词作为集合处理：词袋方法

将一段文本编码为机器学习模型可处理形式的最简单方法是丢弃顺序，将其视为一组符号（即 “词袋”）。你可以查看单个词（一元词），也可以尝试通过查看连续符号组（N-gram）来恢复一些局部顺序信息。

### 使用二进制编码的单个词（一元词）

如果你使用单个词的词袋，句子 “the cat sat on the mat” 将变为

```
{ "cat", "mat", "on", "sat", "the" }
```

这种编码的主要优点是，你可以将整段文本表示为单个向量，其中每个条目都是给定词的存在指示符。例如，使用二进制编码（多热编码），你会将文本编码为一个向量，其维度数等于词汇表中的词数——几乎处处都是 0，只有编码文本中存在的词的维度为 1。这就是我们在第 4 章和第 5 章处理文本数据时所做的。让我们在我们的任务上尝试一下。

首先，让我们用 TextVectorization 层处理我们的原始文本数据集，使其产生多热编码的二进制词向量。我们的层只会查看单个词（即一元词）。

### 代码清单 11.3 使用 TextVectorization 层预处理我们的数据集

```
text_vectorization = TextVectorization(
    max_tokens=20000,
    output_mode="multi_hot",
)
text_only_train_ds = train_ds.map(lambda x, y: x)
text_vectorization.adapt(text_only_train_ds)

binary_1gram_train_ds = train_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)
binary_1gram_val_ds = val_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)
binary_1gram_test_ds = test_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)
```

- 将词汇表限制为出现频率最高的 20,000 个词。否则，我们将为训练数据中的每个词建立索引——可能有成千上万个只出现一两次且不具信息性的术语。通常，20,000 是文本分类的合适词汇表大小。
- 将输出标记编码为多热二进制向量。
- 准备一个仅产生原始文本输入（无标签）的数据集。
- 使用该数据集通过 adapt() 方法为数据集建立词汇表索引。
- 准备我们训练、验证和测试数据集的预处理版本。务必指定 num_parallel_calls 以利用多个 CPU 内核。

你可以尝试查看其中一个数据集的输出。

### 代码清单 11.4 检查我们的二进制一元词数据集的输出

```
>>> for inputs, targets in binary_1gram_train_ds:
...     print("inputs.shape:", inputs.shape)
...     print("inputs.dtype:", inputs.dtype)
...     print("targets.shape:", targets.shape)
...     print("targets.dtype:", targets.dtype)
...     print("inputs[0]:", inputs[0])
...     print("targets[0]:", targets[0])
...     break
inputs.shape: (32, 20000)
inputs.dtype: <dtype: 'float32'>
targets.shape: (32,)
targets.dtype: <dtype: 'int32'>
inputs[0]: tf.Tensor([1. 1. 1. ... 0. 0. 0.], shape=(20000,), dtype=float32)
targets[0]: tf.Tensor(1, shape=(), dtype=int32)
```

接下来，让我们编写一个可复用的模型构建函数，我们将在本节的所有实验中使用它。

### 代码清单 11.5 我们的模型构建实用程序

```
from tensorflow import keras
from tensorflow.keras import layers

def get_model(max_tokens=20000, hidden_dim=16):
    inputs = keras.Input(shape=(max_tokens,))
    x = layers.Dense(hidden_dim, activation="relu")(inputs)
    x = layers.Dropout(0.5)(x)
    outputs = layers.Dense(1, activation="sigmoid")(x)
    model = keras.Model(inputs, outputs)
    model.compile(optimizer="rmsprop",
                  loss="binary_crossentropy",
                  metrics=["accuracy"])
    return model
```

最后，让我们训练并测试我们的模型。

### 代码清单 11.6 训练和测试二进制一元词模型

```
model = get_model()
model.summary()
callbacks = [
    keras.callbacks.ModelCheckpoint("binary_1gram.keras",
                                    save_best_only=True)
]
model.fit(binary_1gram_train_ds.cache(),
          validation_data=binary_1gram_val_ds.cache(),
          epochs=10,
          callbacks=callbacks)
model = keras.models.load_model("binary_1gram.keras")
print(f"Test acc: {model.evaluate(binary_1gram_test_ds)[1]:.3f}")
```

> 我们在数据集上调用 cache() 将其缓存在内存中：这样，我们只会在第一个时期进行一次预处理，并为后续时期重用预处理后的文本。只有当数据足够小以装入内存时，才能这样做。

这样我们就得到了 89.2% 的测试准确率：不错！请注意，在此情况下，由于数据集是一个平衡的二分类数据集（正样本和负样本数量相同），我们在不训练实际模型的情况下能达到的 “朴素基线” 只有 50%。与此同时，在不利用外部数据的情况下，在这个数据集上能达到的最佳得分大约是 95% 的测试准确率。

### 使用二进制编码的二元词

当然，丢弃词序非常简单化，因为即使是原子概念也可以通过多个词来表达：术语 “United States” 传达的概念与分别取词 “states” 和 “united” 的含义截然不同。出于这个原因，你通常最终会通过查看 N-gram 而不是单个词（最常见的是 bigram）将局部顺序信息重新注入到你的词袋表示中。

使用 bigrams，我们的句子变为

```
{"the", "the cat", "cat", "cat sat", "sat",
"sat on", "on", "on the", "the mat", "mat"}
```

TextVectorization 层可以配置为返回任意 N-gram：bigrams、trigrams 等。只需传递一个 ngrams=N 参数，如下一个清单所示。

### 代码清单 11.7 配置 TextVectorization 层以返回 bigrams

```
text_vectorization = TextVectorization(
    ngrams=2,
    max_tokens=20000,
    output_mode="multi_hot",
)
```

让我们测试一下我们的模型在使用这种二进制编码的 bigram 词袋进行训练时的表现。

### 代码清单 11.8 训练和测试二进制 bigram 模型

```
text_vectorization.adapt(text_only_train_ds)
binary_2gram_train_ds = train_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)
binary_2gram_val_ds = val_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)
binary_2gram_test_ds = test_ds.map(
    lambda x, y: (text_vectorization(x), y),
    num_parallel_calls=4)

model = get_model()
model.summary()
callbacks = [
    keras.callbacks.ModelCheckpoint("binary_2gram.keras",
                                    save_best_only=True)
]
```
