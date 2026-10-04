
```python
if word.lower() in word_dict:
    index_value = word_dict.index(word.lower())
    hot_vector[index_value] += 1

hot_vector = np.array(list(hot_vector))
result = (sess.run(tf.argmax(nn_output.eval,
feed_dict[pl: hot_vector]), 1))

if result[0] == 0:
    print('Negative:', input_data)
elif result[0] == 1:
    print('Positive:', input_data)
```

开始定义占位符的函数，它接收我们的句子，并创建一个 `saver` 对象来加载我们训练的模型。我们还使用了单词字典文件。

我们创建一个 TensorFlow 会话并恢复保存的模型。恢复基本上是从存储在 `model.ckpt` 中的变量中读取值，并将它们赋值给在运行 `ff_neural_function` 模型时创建的变量。

使用 `sess.run`，我们通过传递 `hot_vector` 并使用 `tf.argmax` 函数运行模型，得到神经网络的答案。我们知道 `[1, 0]` 是正性的，`[0, 1]` 是负性的，如果 `argmax` 返回 0，则索引位置0是最大的，这是一个正性句子；如果是1，则这是一个负性句子。我们使用 IF 语句使结果对人类可读。

## 5.3.6 运行代码

要使用 IBM PowerAI 运行代码，请导入（source）你想要使用的框架，加载带有库的框架环境。为此，前往 `/opt/DL`（框架安装所在），并打开你想要使用的那个。在我们的情况下，我们想要使用 `tensorflow/bin`。在目录 (`/opt/DL/tensorflow/bin`) 下运行 `source tensorflow-activate`。

要训练模型，你必须运行训练函数并向其传递 TensorFlow 占位符。要使用你的模型，你必须运行 `get_sentiment` 函数并提供你想要检查的句子。

在训练时，你可以在终端上运行 `nvidia-smi` 命令查看 GPU 的使用情况。

如果你想进行测试或想对模型进行更改，可以使用较小数据集进行实验。例如，我们创建了一个名为 `smaller_dataset_gen` 的函数，用于从大型数据集中随机提取行并创建一个较小集。你只需要运行该函数并提供原始数据集、它包含多少行（如果你使用的是 Sentiment140，则为 1600000 行）、目标数据集的名称以及它想要拥有的行数。

完整代码可以在 GitHub 上找到。更多信息请参阅第 241 页的附录“情感分析”。

## 5.4 在 TensorFlow 中使用长短记忆记忆进行单词建议

本节描述了一种使用长短期记忆（LSTM）循环神经网络（RNN）的单词实现，以便你理解。我们的示例完全关于将我们的模型训练到短语数据集中；当我们使用它时，可以开始预测下一个单词可能是什么，这样我们就不需要输入它。

为此，我们使用 RNN，因为单词的顺序或序列提供了很好的建议。我们实现了一种特定的 RNN，称为 LSTM，因为简单的 RNN 无法保留旧迭代的数据；LSTM 会记住重要的，并遗忘不重要的。更多信息请参阅第 8 页的 1.2.3，“神经网络的类型及其用法”。

### 5.4.1 我们的数据集

我们使用了一个简单且小的数据集，包含 100 个创建的问题，模拟了用户询问如何在系统内执行某些操作、如何重置密码、如何访问互联网以及在哪里找到某些信息。

数据已经是正确的格式，但在生产环境中，你必须从数据库获取数据并应用转换将其转换为所需的格式。

### 5.4.2 代码的整体结构

代码的整体结构与 5.3 节第 123 页“基于 PowerAI 的 TensorFlow 情感分析”中使用的相同，因此使用了相同的图（第 8 页图 5-1）。该图表示了我们代码的结构。

有一个准备阶段，用于创建字典并将短语放入正确的 Python 对象中，以便神经网络使用。然后，在第二阶段我们定义 LSTM 神经网络模型并对其进行训练，以便进入可以使用该模型的第三阶段。

### 5.4.3 数据准备

在这一阶段，我们创建单词字典，以便了解数据集中出现的每个不同单词。我们不排除任何单词，因为每个单词对系统都是重要的。

在此阶段，我们将集合中的每个短语转换为单词列表并将其保存到 pickle 文件中，以便我们可以处理更大的数据集，而无需将它们全部保存在内存中。

示例 5-7 为你提供了代码示例。

**示例 5-7 `create_word_list` 函数**

```python
def create_word_list(source_ds):
    words_list = []
    num_lines = 0
    with open(source_ds, 'r', 20000, 'latin-1') as ds:
        with open('ds_to_list.pickle', 'wb', 10000) as ds_list:
            for line in ds:
                words = word_tokenize(line.lower())
                words_list += list(words)
                pickle.dump(words, ds_list)
                num_lines += 1

    word_count = set(words_list)
    word_list_final = {}
    count = 0
    for i in word_count:
        word_list_final[i] = count
        count += 1
    rev_word_dict = dict(zip(word_list_final.values(),
        word_list_final.keys()))
```

```python
list_size = len(word_list_final)
```

```python
print("Word dictionary: {}".format(list_size))
with open('word_dict.pickle', 'wb') as wd:
    pickle.dump(word_list_final, wd)
```

```python
with open('rev_word_dict.pickle', 'wb') as wd:
    pickle.dump(rev_word_dict, wd)
```

```python
print("Word dictionary generated and saved")
return list_size, num_lines
```

`create_word_list` 函数接收数据集并逐行处理它。对于每一行，该函数使用 NLTK 库中的 `word_tokenize` 函数将其转换为单词列表，使用 `pickle` 将其保存到文件中，并添加到名为 `words_list` 的列表中，然后使用 `set` 进行唯一化存储。

我们创建一个字典并为每个单词分配一个从 0 到 `word_count` 的数字。这些数字被用于输入神经网络。我们必须创建一个反向单词字典，以便当我们拥有单词数字并需要回溯单词时更容易进行映射。基本上，该字典是通过使用第一个字典的值作为键、其键作为值创建的。

处理此过程后，我们将两个字典都写入文件，以便在不同的模块中使用。该函数返回单词字典的大小和原始数据的大小，以便它们可以在不同的模块中用于循环控制。

## 5.4.4 模型创建

在创建了每个单词对应数字的字典后，数据集的格式为每个短语一个列表，列表中的每个项是短语的一个单词，我们使用 LSTM 神经网络创建模型。`lst_rnn` 函数就是定义发生的地方，如示例 5-8 所示。

**示例 5-8 `lstm_rnn` 函数**

```python
output_weight = tf.Variable(tf.random_normal([num_neurons,
                                                files_details['list']]))
output_biases = tf.Variable(tf.random_normal([[files_details['list']]]))

tf_placeholder = tf.reshape(tf_placeholder, [-1, interval_size])

tf_placeholder = tf.split(tf_placeholder, interval_size, 1)
nn_layers = rnn.MultiRNNCell([rnn.BasicLSTMCell(num_neurons),
                               rnn.BasicLSTMCell(num_neurons)])

out, states = rnn.static_rnn(nn_layers, tf_placeholder, dtype=tf.float32)

return tf.matmul(outputs[-1], output_weight) + output_biases
```

完成以下步骤：

1. 为神经网络输出层定义权重和偏置。权重是一个所有权重随机初始化的矩阵，偏置也是随机初始化的。它们是 TensorFlow 变量，因此框架知道它们在训练阶段必须进行更新和调整。

2. 创建 TensorFlow-placeholder 来接收数据集（newmer 格式），并将其重塑为符合 `rnn.static_rnn` 函数预期的格式。

3. TensorFlow 通过准备好使用的函数来设置 LSTM 神经网络。

4. 使用 `rnn.MultiRNNCell` 创建一个具有多个隐藏层的 RNN。此函数接收每层的神经元，在这种情况下是 LSTM 神经元。必须使用指定神经元数量的 `BasicLSTMCell` 函数。`static_rnn` 函数将整个模型与标识符绑定以创建神经网络。TensorFlow 帮助定义神经网络的完整结构。

5. 执行输出层操作，即将第二个隐藏层的输出乘以输出权重和偏置之和。使用输出的最后一个位置是因为我们对 RNN 的最后一个输出感兴趣。RNN 在每次迭代后生成一个输出，因此它生成一个数组作为输出。

## 5.4.5 训练

训练阶段与 5.3 中应用于情感分析的阶段相似。参考第 123 页的“在 IBM PowerAI 上使用 TensorFlow 进行情感分析”。区别在于向神经网络提供了什么以及如何。示例 5-9 解析了代码并展示了其细节。

**示例 5-9 训练函数**

```python
def training(in_placeholder):
    rnn_output = lstm_rnn(in_placeholder)
    saver = tf.Saver()

    cost = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(labels=y, logits=rnn_output))
    optimizer = tf.train.AdamOptimizer(learning_rate=0.001).minimize(cost)

    correct = tf.equal(tf.argmax(rnn_output, 1), y)
    accuracy = tf.reduce_mean(tf.cast(correct, tf.float32))

    init = tf.global_variables_initializer()

    with tf.Session() as session:
        session.run(init)
        step = 0
        start = 0
        end = interval_size
        acc_total = 0
        loss_total = 0
        counter = 0

        with open('word_dict.pickle', 'rb') as wd:
            word_dict = pickle.load(wd)
        while step < end:
            with open('ds_to_list.pickle', 'rb') as ds:
                line_list = pickle.load(ds)
                for i in range(len(line_list)):
                    sequence = np.zeros([len(word_dict)])
                    for word in line_list[i]:
                        sequence[word_dict[word]] = 1
                    sequence = np.reshape(sequence, [1, -1])
                    hot_vector = np.zeros([len(word_dict)])
                    hot_vector[line_list[i][3]] = 1
                    
                    acc, loss = session.run([accuracy, cost],
                        feed_dict={in_placeholder: sequence, y: hot_vector})
                    counter += 1
                    acc_total += acc
                    loss_total += loss
            step += 1
            print('{}. Loss: {:.4f} and Accuracy: {:.2f}%'.format(step+1, loss_total/counter, (100*acc_total)/counter))

        saver.save(session, 'model.ckpt')
```

## 5.4.6 使用模型

要使用训练过的网络模型，请如示例 5-10 所示创建 `get_word` 函数。该函数负责提供一个 CLI（命令行界面）体验，提示用户至少输入三个单词，根据输入调用神经网络模型，获取其返回并呈现三个最佳单词选项，以便用户自动补全正在输入的句子。

**示例 5-10 `get_word` 函数**
