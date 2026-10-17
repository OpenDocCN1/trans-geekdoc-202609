
## Split text into words
```python
python3 = sys.version_info[0] == 3
with open('lovecraft.txt', 'r') as f:
 input_str = f.read().lower()
 if python3:
  trans = input_str.maketrans('', '', string.punctuation)
  input_str = input_str.translate(trans)
 else:
  input_str = input_str.decode('utf-8').translate(None, string.punctuation)
 words = input_str.split()
 num_words = len(words)
```

## Convert words to values
```python
word_freq = collections.Counter(words).most_common()
vocab_size = len(word_freq)
lookup = dict()
for word, _ in word_freq:
 lookup[word] = len(lookup)
input_vals = np.asarray([[lookup[str(word)]] for word in words])
input_vals = input_vals.reshape(-1,)
```

## Set values
```python
input_size = 6
batch_size = 10
num_hidden = 600
```

## Placeholders
```python
input_holder = tf.placeholder(tf.float32, [batch_size, input_size])
label_holder = tf.placeholder(tf.float32, [batch_size, vocab_size])
```

## Reshape input and feed to RNN
```python
cell = tf.nn.rnn_cell.BasicRNNCell(num_hidden)
outputs, _ = tf.nn.static_rnn(cell, [input_holder], dtype=tf.float32)
```

## Compute loss
```python
weights = tf.Variable(tf.random_normal([num_hidden, vocab_size]))
biases = tf.Variable(tf.random_normal([vocab_size]))
model = tf.matmul(outputs[-1], weights) + biases
loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=model, labels=label_holder))
```

## Create optimizer and check result
```python
optimizer = tf.train.AdagradOptimizer(0.1).minimize(loss)
check = tf.equal(tf.argmax(model, 1), tf.argmax(label_holder, 1))
correct = tf.reduce_sum(tf.cast(check, tf.float32))
```

## Execute the graph
```python
start_time = time.time()
with tf.Session() as sess:
 sess.run(tf.global_variables_initializer())
 input_block = np.empty([batch_size, input_size])
 label_block = np.empty([batch_size, vocab_size])

 step = 0
 num_correct = 0.
 accuracy = 0.
 while accuracy < 95.:
  for i in range(batch_size):
   offset = np.random.randint(num_words-(input_size+1))
   input_block[i, :] = input_vals[offset:offset+input_size]
   label_block[i, :] = np.eye(vocab_size)[input_vals[offset+input_size]]
  _, corr = sess.run([optimizer, correct],
```

```python
feed_dict={input_holder: input_block, label_holder: label_block})
num_correct += corr
accuracy = 100*num_correct/(1000*batch_size)
if step % 1000 == 0:
    print('Step', step, '- Accuracy =', accuracy)
num_correct = 0
step += 1
```

### 显示耗时结果

`duration = time.time() - start_time`

`print('Time to reach 95% accuracy: {:.2f} seconds'.format(duration))`

开始时，该模块将 `lovecraft.txt` 的内容读入一个字符串，将字符串拆分为单词，并为每个单词关联一个数字。单词的数字由其频率决定。也就是说，该模块将最常见的单词关联为 0，将第二常见的单词关联为 1，以此类推。

在获得与单词对应的数字数组后，该模块创建了一个具有 600 个隐藏层的 RNN 单元。它使用该 RNN 单元调用 `tf.nn.static_rnn`，以提供 RNN 的输出值。为了确定损失，该模块将 RNN 的输出乘以权重矩阵并向乘积添加偏置。然后它创建一个 `AdagradOptimizer` 来最小化损失。

对于每次训练运行，应用程序构造一个包含十个（`batch_size`）序列的批次，每个序列包含六个（`input_size`）值。因此，RNN 只能识别最多六个连续单词之间的依赖关系。对于每个六值序列，期望的标签是第七个值，它代表要预测的期望单词。

该应用程序不执行固定次数的训练运行。相反，它会一直训练，直到预测准确率超过 95%。每进行一千次训练运行，应用程序就会打印预测准确率。

### 创建多层单元

应用程序可以通过将单元按顺序堆叠在一起提高 RNN 的分析能力。这种堆叠过程将一个单元的输出连接到另一个单元的输入。TensorFlow 应用程序可以通过创建 `tf.contrib.rnn.MultiRNNCell` 类的实例来堆叠 RNN 单元，其构造函数如下所示：

`MultiRNNCell(cells, state_is_tuple=True)`

要创建 `MultiRNNCell`，应用程序需要将第一个参数设置为 `RNNCell` 实例的列表。返回的单元将按顺序包含所列实例。

第二个参数设置单元状态的形式。如果将 `state_is_tuple` 设置为 `True`，单元将以元组形式提供其状态，该元组包含每个组合单元的一个元素。如果将此参数设置为 `False`，单元将连接各个单元的状态。

例如，以下代码创建了两个 `BasicRNNCell`，然后创建了一个将单元堆叠在一起的 `MultiRNNCell`：

```python
brc1 = tf.nn.rnn_cell.BasicRNNCell(3)
brc2 = tf.nn.rnn_cell.BasicRNNCell(3)
multi_cell = tf.nn.rnn_cell.MultiRNNCell([brc1, brc2])
```

因此，`multi_cell` 将 `brc1` 和 `brc2` 堆叠在一起，将 `brc1` 的输出连接到 `brc2` 的输入。

### 创建动态 RNN

`static_rnn` 函数假定您事先知道输入数据的长度。它要求输入数据以矩阵列表的形式提供，其中每个矩阵的大小为 [`batch_size`, `input_size`]。当应用程序调用 `static_rnn` 时，TensorFlow 会在当前图中创建整个 RNN 结构。

`dynamic_rnn` 函数在提供输入数据时为您提供更大的灵活性。它告诉 TensorFlow 动态形成图结构，而不是提前构建它。`dynamic_rnn` 的签名如下所示：

`dynamic_rnn(cell, inputs, sequence_length=None, initial_state=None, dtype=None, parallel_iterations=None, swap_memory=False, time_major=False, scope=None)`

这些参数中的大多数与 `static_rnn` 相同。主要区别在于应用程序可以将 `inputs` 设置为不同的形状。此形状取决于批大小、最大序列长度以及函数的 `time_major` 参数。`time_major` 的默认值是 `False`，这意味着应用程序必须将输入分配给大小为 [`batch_size`, `max_sequence`, …] 的张量或嵌套元组。如果应用程序将 `time_major` 设置为 `True`，则必须将输入分配给大小为 [`max_sequence`, `batch_size`, …] 的张量或嵌套元组。

TensorFlow 可以并行执行没有时间依赖性的操作。`parallel_iterations` 参数控制应同时执行多少个此类操作，默认值是 32。

如果应用程序将 `swap_memory` 设置为 `True`，TensorFlow 将在训练过程中在 GPU 和 CPU 之间交换张量，从而产生轻微的性能损失。第 11 章 解释了如何在 GPU 上执行 TensorFlow 操作。

与 `static_rnn` 一样，`dynamic_rnn` 返回构建的 RNN 的输出和状态。以下代码演示了如何使用 `dynamic_rnn`：

```python
example_cell = tf.nn.rnn_cell.BasicRNNCell(4)
output, state = tf.nn.dynamic_rnn(example_cell,
example_input, dtype=tf.float32)
```

在我的实验中，`dynamic_rnn` 的性能略优于 `static_rnn`。

## 长短期记忆 LSTM 单元

随着 RNN 处理更多阶段，其展开网络变得更大，并且更容易受到梯度消失的影响。由于 RNN 有固定数量的阶段，因此它们无法分析具有长期依赖关系的序列。也就是说，如果 RNN 最多可以处理 N 个阶段，它就不会识别元素 0 和元素 N+1 之间的任何依赖关系。

为了弥补这些不足，Sepp Hochreiter 和 Jürgen Schmidhuber 在 1997 年的论文 *Long Short-Term Memory* 中提出了对 RNN 结构的修改。从本质上讲，他们建议通过限制 RNN 接受数据的时机来减小 RNN 状态的大小。具体来说，LSTM 使用三种类型的限制：

* 限制 RNN 接受输入数据的时机
* 限制存储在 RNN 状态中的元素
* 限制 RNN 产生输出数据的时机

Hochreiter 和 Schmidhuber 将他们的新型单元称为 *long short-term memory (LSTM) cell*，通常简称为 *LSTM*。由于其限制，LSTM 仅处理和存储其预测所需的数据。

LSTM 的一个主要优势是规模。为了处理数据序列，LSTM 所需的节点比可比的 RNN 更少。此外，由于 LSTM 可以阻止存储无关数据，因此其状态可以检查具有长期依赖关系的序列。

为了实现这些限制，Hochreiter 和 Schmidhuber 在 RNN 单元结构中添加了三个门：输入门、遗忘门和输出门。图 9-5 展示了这些门如何控制 LSTM 单元的连接性。

![FIGURE 9-5: An LSTM reduces the size of an RNN by preventing unnecessary data from cluttering the RNN’s state.](img/9788126592555-fg0905.png)

FIGURE 9-5: An LSTM reduces the size of an RNN by preventing unnecessary data from cluttering the RNN’s state.

每个门都维护自己的权重和偏置，以确定何时打开和关闭。准确地说，这三个门通过将信号乘以 sigmoid 函数的结果（σ）来工作。对于输入门和输出门，该函数决定允许通过多少信号。对于遗忘门，该函数决定数据是否应存储在单元的状态中（1）或丢弃（0）。

将输入门的状态表示为 `i[t]`，遗忘门的状态表示为 `f[t]`，输出门的状态表示为 `o[t]`，以下方程显示了这些门的工作原理：

请记住，在门内部，底层单元的行为类似于 RNN 单元。也就是说，它依赖于 `tanh` 函数（默认情况下）作为其激活函数。

### 在代码中创建 LSTM

在 TensorFlow 中，创建 LSTM 的过程与创建普通 RNN 相似：创建单元类的实例并基于该单元形成 RNN。第二步需要使用前面章节 “创建 RNN 单元” 中讨论的相同的 `static_rnn` 和 `dynamic_rnn` 函数。

`tf.nn.rnn_cell` 包提供了一些代表 LSTM 单元的类，基本类是 `BasicLSTMCell` 和 `LSTMCell`。前者使用起来更简单，但后者提供更多自定义选项。

#### 设置状态

在普通 RNN 中，你可以用大小为 [`batch_size`, `state_size`] 的矩阵设置初始状态。但要初始化 LSTM 网络的状态，你需要提供一个包含两个状态矩阵的元组：一个标识单元状态，一个标识隐藏状态。
