

`num_units` 参数设置单元中隐藏单元的数量。该参数决定了 RNN 的学习能力。也就是说，随着单元数量的增加，单元的状态存储大小也会增加。不幸的是，训练时间也会增加。此外，如果将 `num_units` 设置得过高，就有过拟合的风险。

构造函数的第二个参数设置单元的激活函数。默认情况下，RNN 单元依赖于反正切（`tanh`）来产生其输出。

最后一个参数 `reuse` 指定应用程序是否可以访问单元创建的同名变量。

创建单元实例后，应用程序可以通过调用 `tf.nn` 包中的少数几个函数来构建 RNN。其中最简单的一个函数是 `static_rnn`：

```
static_rnn(cell, inputs, initial_state=None, dtype=None, sequence_length=None, scope=None)
```

应用程序必须将 `inputs` 指定为输入矩阵的列表。对于列表中的每个输入矩阵，该函数都会创建一个单元来接收和处理该矩阵。输入矩阵中的行数等于应用程序的批大小。在此讨论中，我将该数字称为 `batch_size`。

默认情况下，`static_rnn` 假定 RNN 的序列长度等于输入矩阵中的列数。应用程序可以通过将 `sequence_length` 设置为 `batch_size` 个值的一维张量来自定义此长度。`sequence_length` 的每个值都设置输入矩阵对应行的序列长度。

其名称所示，`initial_state` 参数初始化 RNN 的状态。应用程序必须为输入矩阵的每一行提供一个状态值，因此如果单元的 `state_size` 为整数，则应用程序必须将 `initial_state` 设置为形状为 [`batch_size`, `state_size`] 的矩阵。如果 `state_size` 为元组，则应用程序必须将 `initial_state` 设置为形状为 [`batch_size`, `element_size`] 的张量元组，其中 `element_size` 是 `state_size` 中对应元素的大小。

如果应用程序设置了 `initial_state` 参数，`static_rnn` 将使用状态的元素来确定 RNN 元素的 数据类型。如果应用程序未设置 `initial_state`，则必须使用 `dtype` 参数指定数据类型。TensorFlow 不为 RNN 的内容设置默认数据类型。

`static_rnn` 返回一个包含两个元素的元组：RNN 的输出和最终状态。输出包含 `batch_size` 个元素，最终状态的形状由单元的 `state_size` 决定。

单元数量、状态、输入和输出之间的关系可能令人困惑，因此查看一个基本示例会有帮助。以下代码使用五个单元创建了一个 `BasicRNNCell`：

```
new_cell = tf.nn.rnn_cell.BasicRNNCell(5)
```

由于 RNN 单元有五个单元，单元输出矩阵中的每一行长度都为五。

对于此示例，每个输入矩阵有两行，每行有四个元素。如果应用程序需要提供三个输入矩阵，则可以使用以下代码设置 RNN 的输入：

```
inputs = [tf.constant([[1.,2.,3.,4.], [1.,2.,3.,4.]]), tf.constant([[1.,2.,3.,4.], [1.,2.,3.,4.]]), tf.constant([[1.,2.,3.,4.], [1.,2.,3.,4.]])]
```

创建 `new_cell` 后，应用程序可以使用以下代码创建新的 RNN 并传递输入矩阵列表。`dtype` 参数指定 RNN 的状态和输出应由浮点值组成：

```
output, state = tf.nn.static_rnn(new_cell, inputs, dtype=tf.float32)
```

由于 `inputs` 包含三个输入矩阵，新 RNN 的结构包含三个单元。每个单元产生的输出矩阵的行数与输入矩阵相同。[Figure 9-4](#14_9788126592555-ch09.xhtml#c09-fig-0004) 给出了简单 RNN 的大致外观。

![FIGURE 9-4: TensorFlow creates one RNN cell for each input matrix. Each cell produces one output matrix.](images/9788126592555-fg0904.png)

[FIGURE 9-4:](#14_9788126592555-ch09.xhtml#rc09-fig-0004) TensorFlow creates one RNN cell for each input matrix. Each cell produces one output matrix.

在 [Figure 9-4](#14_9788126592555-ch09.xhtml#c09-fig-0004) 中，`x[i](t)` 标识在 `inputs` 参数中提供的输入矩阵，而 `y[i](t)` 标识 `static_rnn` 返回的输出矩阵。初始状态进入第一个单元，该单元将其状态传递给第二个单元，第二个单元将其状态传递给第三个单元，第三个单元在 `static_rnn` 中返回其状态。

`output` 和 `state` 的精确值并不重要，但查看它们的形状是有帮助的。每个 RNN 都产生一个输出矩阵列表，其大小由输入矩阵列表的大小决定。因此，`output` 是一个包含三个矩阵的列表。由于每个输入批次包含两行，每个输出矩阵都有两行。每行有五个值，因为单元有五个单元。

单元状态的形状由批大小和单元中的单元数量决定。在此示例单元中，状态的形状为 `[2, 5]`，因为批大小为二，单元包含五个单元。

### 使用 RNN 预测文本

因为我是国宝级的，所以我将 H.P. Lovecraft 短篇小说 *Herbert West–Reanimator* 的一部分提取到 `ch9/lovecraft.txt` 文件中。`ch9/rnn_lovecraft.py` 模块读取此文本并使用 RNN 来预测 H.P. Lovecraft 如何为短语添加单词。我相信我们可以都同意该应用程序对人类文化发展至关重要，而 [Listing 9-1](#14_9788126592555-ch09.xhtml#c09-fea-0001) 展示了代码。

[LISTING 9-1](#14_9788126592555-ch09.xhtml#rc09-fea-0001) Predicting Text with an RNN

```
# Split text into words
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

# Convert words to values
word_freq = collections.Counter(words).most_common()
vocab_size = len(word_freq)
lookup = dict()
for word, _ in word_freq:
 lookup[word] = len(lookup)
input_vals = np.asarray([[lookup[str(word)]] for word in words])
input_vals = input_vals.reshape(-1,)

# Set values
input_size = 6
batch_size = 10
num_hidden = 600

# Placeholders
input_holder = tf.placeholder(tf.float32, [batch_size, input_size])
label_holder = tf.placeholder(tf.float32, [batch_size, vocab_size])

# Reshape input and feed to RNN
cell = tf.nn.rnn_cell.BasicRNNCell(num_hidden)
outputs, _ = tf.nn.static_rnn(cell, [input_holder], dtype=tf.float32)

# Compute loss
weights = tf.Variable(tf.random_normal([num_hidden, vocab_size]))
biases = tf.Variable(tf.random_normal([vocab_size]))
model = tf.matmul(outputs[-1], weights) + biases
loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=model, labels=label_holder))

# Create optimizer and check result
optimizer = tf.train.AdagradOptimizer(0.1).minimize(loss)
check = tf.equal(tf.argmax(model, 1), tf.argmax(label_holder, 1))
correct = tf.reduce_sum(tf.cast(check, tf.float32))

# Execute the graph
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

