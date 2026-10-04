
TensorFlow V1.4.0 包包含对额外功能的支持：

- HDFS
- NCCL
- 实验性 XLA JIT 编译

## 4.4.6 卸载机器学习和

IBM Power TensorFlow 包包含 TensorBoard。要卸载机器学习和框架，您可能需要运行以下命令：

```
$ sudo uninstall-machine-learning
```

第二阶段是使转换后的数据准备好以供神经网络导入。这个过程通常需要大量的处理，出现一些数据扩展是正常的，因为你必须以不同的格式表示你的数据。描述具体的细节超出了本节的范围，因此此阶段所需的方法取决于数据的格式（图像、声音、文本或数字）以及所选神经网络的架构。

神经网络在用数字作为输入时更有效，因为它是一个数学模型。在这种背景下，有必要将你的数据转换为数字，同时保持其组织良好、结构化，并符合神经网络架构预期的格式（通常是向量数组）。

例如，如果你的数据是一张图像，你可能会将其转换为灰度，提取其矩阵并将其转换为数组。此过程必须在所有图像上进行，以便你的数据每一行代表一张图像。此外，有必要创建标签，以便神经网络可以从中学习。这些标签必须转换为数字并存储为热向量（hot vector），以便输入到神经网络中。

这种方法是处理数据并将其就绪的多种方案中的一种高级路径。接下来的章节展示了准备数据以及使用这些数据创建神经网络模型的几个场景。

## 5.3 在 IBM PowerAI 上使用 TensorFlow 进行情感分析

这句话说明了前馈神经网络（FFNN）模型，该模型可以识别一个句子是正面还是负面的。此示例使用 IBM PowerAI 上的 TensorFlow 来创建和训练模型。

模型是使用 TensorFlow 创建的。

### 5.3.1 示例数据集

使用的数据集来自斯坦福项目 Sentiment140。也可以从该处下载数据集，它包含了 160 万行正面和负面的句子。

> 注意：在编写期间，项目网站提到可能存在负面、正面和中性的句子。在我们分析了数据集后，我们只发现了正面的句子和负向的句子，因此我们只使用了两个选项来创建和训练我们的模型。

所有信息与数据集格式以及在编写时创建的代码均是有效的。如果你尝试运行相同的示例，如果数据布局稍后发生更新，你必须对其进行更改。

数据集包含两个 CSV 文件，共有六个字段，一个用于训练数据，另一个较小用于测试。两个文件都按照以下格式结构（取自项目网站）：

- 推文的极性（0 = 负面，2 = 中性，4 = 正面）。
- 推文的 ID（2087）。
- 推文日期（2009 年 5 月 16 日 23:58:44 协调世界时）。
- 3 (lyx)。如果没有查询，则此值为 NO_QUERY。
- 4 推特的用户（robotickilldozr）。
- 5 推文内容（Lyx is cool）。

数据集中的句子是从 Twitter 提取的，它们的情感尚未由对文件进行正确标签层标注的人工识别。使用了一段代码来识别带有正面表情符号的句子，并假设它们是正面表情符号，以及带有负面情绪的负面表情符号。你可以使用自己的句子数据集并根据需要对其标记。有关该数据集和项目的更多信息，请参阅 Sentiment140 项目。

### 5.3.2 代码结构

代码分为三个文件：第一个是准备数据，第二个是关于创建 FFNN 模型，最后一个文件是使用已创建和训练好的模型。更多信息，请参见图 5-1。

![](img/f6f95c5defc8b3406a94a86b8d202807_137_0.png)

图 5-1 代码结构

考虑到你正在处理 160 万行数据，使用持久化（persistence）来确保所有数据都保存在内存中是非常重要的，这样在发生失败的情况下不需要从头开始过程。

接下来的章节描述了每一个步骤并展示了一些代码片段。

### 5.3.3 数据准备

此阶段确保数据经过转换，并在流程结束时处于 FFNN 预期的正确格式。

图 5-2 显示了数据准备阶段的视图，用于描述代码细节。

![](img/f6f95c5defc8b3406a94a86b8d202807_138_0.png)

图 5-2 数据准备流程

#### 清洗数据集

你必须要做的是移除不需要的列，例如 Twitter ID、日期等，只保留情感和 Twitter 文本。要完成这项任务，请使用 `clean_dataset` 函数，如示例 5-1 所示。

> 示例 5-1 负责清洗原始数据集的函数

```python
def shuffer(input_ds, output_ds):
    df_source = pd.read_csv(input_ds, '<sep>', error_bad_lines=False)
    df_shuffled = df_source.iloc[np.random.permutation(len(df_source))]
    df_shuffled.to_csv(output_ds, 'μ', index=False)

def clean_dataset(ds, ods):
    with open(ds, 'r', 30000, 'latin-1') as row_ds:
        with open('tempds.csv', 'w', 20000) as cleaned_ds:
            for line in row_ds:
                result = re.search(r"^(\d*),(.*)$", line)
                new_line = result.group(1) + '<sep>' + result.group(2) + '\n'
                cleaned_ds.write(new_line)
```

```python
shuffer('tempds.csv', ods)
os.remove('tempds.csv')
print('data set cleanup')
```

`shuffer` 函数接收输入并生成一个以 `<sep>` 分隔的 CSV 文件以避免字符冲突。尽管数据集是 CSV 文件，但 Twitter 文字中存在逗号，仅使用 `split` 函数不起作用，因此使用正则表达式来获取所需内容。

`clean_dataset` 函数遍历数据集的每一行并应用正则表达式将新行写入临时文件。最后一步是洗牌生成的数据集以确保神经网络得到训练。对于此示例，使用 Pandas 库并写入为参数提供的输出。对于洗牌过程，Pandas 库被设计用于处理大文件。

#### 生成词汇字典

生成清洗后的数据集后，下一步是使用清洗后的数据创建词汇字典。在示例 5-2 中显示了如下：

```python
def word_dict(ds):
    word_dict = []
    with open(ds, 'r', 30000, 'latin-1') as ds:
        for line in ds:
            text = line.lower()
            words = tokenize(text)
            word_ = = [matize(w) for w in words]
    word_count = Counter(word_dict)
    cleaned_dict = [word for word in word_count if word_count[word] > 6]
    dict_size = len(cleaned_dict)
```

```python
print('Word dictionary generated'.format(dict_size))
with open('word_dict.pickle', 'wb') as wd:
    pickle.dump(cleaned_dict, wd)
```

然后，逐词遍历句子并检查该词是否存在于词汇字典中。如果是，则在句子向量中与其在词汇列表相同的位置上加 1。

该字母存在于字典中且索引为 0，因此在句子向量的第 0 处加 1：

[1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

继续重复此过程，直到到达句子末尾，然后处理第二个句子。处理结束，你将得到两个向量：

- 句子 1: [1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
- 句子 2: [0, 0, 1, 1, 0, 1, 0, 1, 1, 1, 1]

该代码读取句子训练数据集和词汇字典作为输入，将句子通过词分词函数，对单词进行词形还原并开始向量化。代码还获取了情感标签并将其转换为两个元素的列表，因为存在正面和负面句子。句子和情感向量被放入列表中并保存到二进制文件中，供后续步骤的模型读取：

示例 5-3 `sentence_to_vector` 函数。

示例 5-3 用于将句子转换为向量的代码

```python
def sentence_to_vector(word_dict, cleaned_ds, output_file):
    with open(cleaned_ds, 'r', 30000, 'latin-1') as ds:
        with open(word_dict, 'rb') as wd:
            word_dict = pickle.load(wd)
            num_lines = 0
            with open(output_file, 'wb') as hv:
                for line in ds:
                    hot_vector = np.zeros(len(word_dict))
                    if line.count('\'') == 1:
                        sentiment, text = line.split('matize[text.lower()])
                        lemm_words = [lemmatize(w) for w in words]
                        for word in lemm_words:
                            hot_vector[word_dict.index(word)] += 1
                        hot_vector = list(hot_vector)
                        clean_sentiment = re.search('.*(\d).*.', sentiment)
                    if clean_sentiment.group(1) == 0:
                        sentiment = [1, 0]
                    else:
                        sentiment = [0, 1]
                    num_lines += 1
                    pickle.dump([hot_vector, sentiment], hv)
            print('Hot vectors file generated with {} lines'.format(num_lines))
    return num_lines
```

## 注意事项

在完成训练数据集处理后，测试数据集将通过相同的过程，以确保其具有相同的格式并可用于检查模型的准确性。如第 128 页的示例 5-3 所示，测试数据集也必须使用训练数据集生成的相同词汇字典。

关于数据规模，此场景使用了 Python 和一些库来完成数据处理工作以及一些策略，例如使用框架来更高效地管理大型数据集。如果你需要扩展并处理大型数据集，可以在分布式框架中对所有数据进行处理，为神经网络做好准备绪。你可以通过使用 IBM Spectrum Scale 实现分布式解决方案，以提供可靠且可扩展的环境。本场景未涉及这些细节，因为它们超出了本书的范围。然而，这描述了 TensorFlow 如何通过使用多个图形处理器（GPU）来利用分布式处理。

## 5.4. 模型创建

现在，我们必须构建基于 TensorFlow 的模型。在数据准备阶段，我们保存了一些关于词汇表列表大小以及生成的向量文件中行数的信息。示例 5-4 显示了负责创建神经网络架构的函数。

> 5-4 创建神经网络架构

```python
def neural_net(input_data):
    neurons_h1 = 1500
    neurons_h2 = 1500
    neurons_h3 = 1500

    output_neurons = 2

    1_weight = tf.Variable(tf.random_normal([line_size['dict'], neurons_h1]), name='w1')
    1_bias = tf.Variable(tf.random_normal([neurons_h1]), name='b1')

    2_weight = tf.Variable(tf.random_normal([neurons_h1, neurons_h2]), name='w2')
    2_bias = tf.Variable(tf.random_normal([neurons_h2]), name='b2')

    3_weight = tf.Variable(tf.random_normal([neurons_h2, neurons_h3]), name='w3')
    3_bias = tf.Variable(tf.random_normal([neurons_h3]), name='b3')

    output_weight = tf.Variable(tf.random_normal([neurons_h3, output_neurons]), name='wo')
    output_bias = tf.Variable(tf.random_normal([output_neurons]), name='bo')

    11 = tf.add(tf.matmul(input_data, 1_weight), 11_bias)
    12 = tf.add(tf.matmul(11, 2_weight), 2_bias)
    13 = tf.add(tf.matmul(12, 3_weight), 3_bias)
    output = tf.add(tf.matmul(13, output_weight), output_bias)

    return output
```

本节未提供相关细节，因为它们超出了本书的范围。

计算模型输出与正确标签之间产生的成本或误差。在计算成本（误差）的过程中，应用了一个名为 Adam 的优化器，这是一种随机梯度下降（SGD）方法，它通过使用反向传播算法更新神经网络中的所有权重和偏置来降低成本。

到目前为止，这只是创建了 TensorFlow 对象并将它们相互连接。该过程创建了一个 TensorFlow 会话（session），其中运行图并导入数据。在调用 `session.run` 函数之前，该过程会从向量化的句子中读取数据，每当定义的临时缓冲区达到我们定义的批次大小（batch size）时，代码就会调用 TensorFlow 并运行优化器，从而运行整个模型。

我们 true true标签的缓冲区列表，因为我们必须提供句子及其对应的标签，以确保网络被正确训练。我们还会运行成本函数，以知道每个轮次（epoch）产生的总成本。

训练阶段会发生多次，次数由 `epochs` 变量定义。代码使用了 10 次，尽管你可以更改它并检查是否能获得更好的结果。基本上，训练数据分批次提交给 TensorFlow 模型，误差由 Adam 优化器进行计算和调整。

训练循环完成后，向图中添加正确的张量，它使用 `tf.argmax` 函数，该函数是网络输出和正确标签之间最大值的索引位置。如果两者相同，`tf.equal` 为 1，如果不匹配则为 0。使用正确张量，准确率通过正确张量的平均值来计算。

现在，我们通过相同的批处理过程读取向量化的数据集文件，但不包含轮次循环。我们使用 `eval` 函数并将数据集及其标签传递给占位符（placeholders），提交测试数据对我们的模型进行评估。完成后，通过 `saver.save` 函数保存模型。

## 5.3.5 使用模型

在训练好的模型保存并准备就绪后，创建了一个名为 `get_sentiment` 的函数，它接收句子作为输入并打印其是正性还是负性（示例 5-6）。

示例 5-6 使用此模型的函数

```python
def get_sentiment(input_data):
    tf.reset_default_graph()
    pl = tf.placeholder('float')
    nn_output = ff_neural_net(pl)
    saver = tf.train.Saver()
    with open('word_dict.pickle', 'rb') as f:
        word_dict = pickle.load(f)

    with tf.Session() as sess:
        saver.restore(sess, "model.ckpt")
        words = word_tokenize(input_data.lower())
        lemm_words = [lemm.lemmatize(w) for w in words]
        hot_vector = np.zeros(len(word_dict))
```

for word in lemm_words:
