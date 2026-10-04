
- 开源深度学习框架，如`Caffe`、`Torch`或`TensorFlow`
- 使用其他厂商的技术。
- 适配带有`Spark`的`HPC`集群。
- 缓解设备间网络相关的瓶颈。

### 7.3.2 IBM 解决方案

为了满足 238 页 7.3.1“客户需求”所示的要求，IBM 提供了可以与其他软件集成的经验和解决方案。作为基础建议（图 7-6），IBM 可以提供包含以下组件的解决方案：

- 硬件：用于高性能计算服务器的`Power 8S22LC`
- 主机操作系统：`Ubuntu 16.04`
- 软件：带有分布式深度学习 (DDL) 和大模型支持 (LMS) 功能的 IBM PowerAI Release 4：
  - `CUDA`：版本 8
  - `cuDNN`：版本 6
  - `NVIDIA`驱动版本：384.66
  - 带有`Spark`的`IBM Spectrum Conductor`
  - `LSF`
- 网络：用于`EDR`的`Infiniband`机和电缆

### 7.3.3 收益

通过考虑到 238 页 7.3.2“IBM 解决方案”所示的所有组件的 IBM PowerAI 端到端解决方案，客户可以获得以下收益：

- 通过最新技术使训练时间缩减。
- `LMS`和`DDL`提供了更好的`GPU`可扩展性。
- 通过本地`Power System`解决方案轻松更改数据和人工智能 (AI) 模型。
- 使用带有优化`DL`库的 IBM PowerAI 工具包实现更简单、更快速。
- 通过作业调度器轻松管理和控制资源。

## 7.4 结论

在接下来的章节中，我们描述了 IBM PowerAI 深度学习框架的组件，总结了`GPU`加速`Power Systems`硬件的优势，并提供了 IBM PowerAI 版本 4 和 5 的示例安装和实现。

IBM PowerAI 让深度学习领域对所有人（包括普通用户、小型企业和传统 HPC 组织）变得触及且易用。`GPU`带来的加速意义体现在处理时间和物理占用的节省上。使用云提供商容量的小型案例（如 IBM 和 NVIDIA 合作推出的全球最快深度学习企业解决方案）提供了一种低成本的评估和实施路径；而在较大的案例中，物理服务器的数量与过去几十年的传统计算需求相比有所减少。

如果您不熟悉深度学习领域，这些示例案例提供了背景和视角。了解您拥有什么数据是使用深度学习的关键。连接、趋势或观察结果可能隐藏了您的视野？使用深度学习进行数据处理为学术、科学、工业、零售和商业领域提供了许多以前未有的机会和兴趣。深度学习的普及已经持续段时间，但目前易于采用的特性使其在我们日常生活的许多领域变得普遍。

![](img/f6f95c5defc8b3406a94a86b8d202807_252_0.png)

## 情感分析代码

本附录提供了第 121 页第5 章“在 IBM PowerAI 中处理数据和创建模型”中介绍的情感分析场景代码，并描述了文件的结构。

本附录包含以下主题：

- 使用`TensorFlow`进行情感分析

## 使用 TensorFlow 进行情感分析

本节介绍了使用`TensorFlow`代码进行情感分析。

## 代码结构组织

情感分析代码组织在三个 Python (.py) 文件中：

- `data_prep.py`：此文件用于准备数据。您可以独立运行它，并生成后续步骤使用的输出数据集和字典。
- `sentiment_neural_net.py`：此文件包含负责模型创建和训练的函数。由于代码的准备方式，您可以从`use_neural_net.py`文件运行训练。
- `use_neural_net.py`：从此文件，您可以运行训练并使用神经网络向`get_sentiment`函数提供句子。如果您不想运行训练函数，请注释掉调用训练函数的行。

该代码也可以在 GitHub 上找到。

## 情感分析代码

示例 A-1 显示了`data_prep.py`准备文件。

示例 A-1 `data_prep.py`文件

```python
from nltk import word_tokenize
from nltk.stem import WordNetLemmatizer
import numpy as np
import re
import random
import pandas as pd
import pickle
import os
from collections import Counter
```

```python
lemm = WordNetLemmatizer()

def rand_list(lines, max_value):
    randlist = []
    for i in range(lines):
        num = random.randint(0, max_value)
        while num in randlist:
            num = random.randint(0, max_value - 1)
        randlist.append(num)

    return randlist
```

```python
def shuffle(input_ds,
```

```python
def create_dataset():
```

```python
df_source = pd.read_csv(input_ds, ' ', error_bad_lines=False)
df_shuffled = df_source.iloc[np.random.permutation(len(df_source))]
df_shuffled.to_csv(output_ds, ' ', index=False)
```

```python
def smaller_dataset_gen(ds, newsds, drows, num_lines=1000):
    count = 0
    with open(ds, 'r', 5000, 'latin-1') as raw_ds:
        with open(newsds, 'w', 5000) as target_ds:
            selected_lines = rand_list(num_lines, drows)
            for line in raw_ds:
                if len(selected_lines) == 0:
                    break
                if count in selected_lines:
                    target_ds.write(line)
                    selected_lines.remove(count)
                count += 1

print("New dataset created with {} lines".format(num_lines))
```

```python
def clean_dataset(ds, os):
    with open(ds, 'r', 30000, 'latin-1') as raw_ds:
        with open('tempds.csv', 'w', 20000) as cleaned_ds:
            for line in raw_ds:
                result = re.search("^(\d*) (.*)\$", line)
                new_line = result.group(1) + ' ' + result.group(2) + '\n'
                cleaned_ds.write(new_line)

shuffler('tempds.csv', os)

os.remove('tempds.csv')
```

```python
def create_word_dict(source_ds):
    word_dict = []
    with open(source_ds, 'r', 30000, 'latin-1') as ds:
        for line in ds:
            text = line.split(' ', 1)
            words = word_tokenize(text.lower())
            lemm_words = [lemm.lemmatize(w) for w in words]
            word_dict += list(lemm_words)
```

```python
word_count = Counter(word_dict)
cleaned_word = [word for word in word_count]
```

# 模型与训练

示例 A-2 显示了`sentiment_neural_net.py`模型和训练文件。

示例 A-2 `sentiment_neural_net.py`文件

```python
import tensorflow as tf
import pickle

x = tf.placeholder('float')
y = tf.placeholder('float')

batch_size = 1000
num_epochs = 1

def load_details():
    with open('data_details.pkl', 'rb') as details:
        det = pickle.load(details)
        return det
```

`line_sizes = load_details()`

```python
# 创建神经网络模型
def ff_neural_net(input_data):
    neurons_h1 = 1500
    neurons_h2 = 1500
    neurons_h3 = 1500

    output_neurons = 2

    l1_weight = tf.Variable(tf.random_normal([[line_sizes['dict'], neurons_h1]), name='w1')
    l1_bias = tf.Variable(tf.random_normal([neurons_h1]), name='b1')

    l2_weight = tf.Variable(tf.random_normal([[neurons_h1, neurons_h2]), name='w2')
    l2_bias = tf.Variable(tf.random_normal([neurons_h2]), name='b2')

    l3_weight = tf.Variable(tf.random_normal([[neurons_h2, neurons_h3]), name='w3')
    l3_bias = tf.Variable(tf.random_normal([neurons_h3]), name='b3')

    output_weight = tf.Variable(tf.random_normal([[neurons_h3, output_neurons]), name='wo')
    output_bias = tf.Variable(tf.random_normal([output_neurons]), name='bo')

    l1 = tf.add(tf.matmul(input_data, l1_weight), l1_bias)
    l1 = tf.nn.relu(l1)

    l2 = tf.add(tf.matmul(l1, l2_weight), l2_bias)
    l2 = tf.nn.relu(l2)
```

```python
    l3 = tf.add(tf.matmul(l2, l3_weight), l3_bias)
    l3 = tf.nn.relu(l3)
```

```python
    output = tf.matmul(l3, output_weight) + output_bias

    return output
```

```python
def training(in_placeholder):

    nn_output = ff_neural_net(in_placeholder)

    saver = tf.train.Saver()

    cost = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(

        logits=nn_output, labels=y))

    optimizer = tf.train.AdamOptimizer(learning_rate=0.001).minimize(cost)

    with tf.Session() as sess:

        sess.run(tf.global_variables_initializer())

        for epoch in range(num_epochs):

            epoch_loss = 0

            buffer = []

            buffer_label = []

            with open('train_hot_vectors.pickle', 'rb') as train_vec:

                for i in range(line_sizes['train']):

                    hot_vector_line = pickle.load(train_vec)

                    buffer.append(hot_vector_line[0])

                    buffer_label.append(hot_vector_line[1])

                if len(buffer) >= batch_size:

                    cost_iter = sess.run(optimizer, cost,

                        feed_dict={in_placeholder: buffer, y: buffer_label})

                    epoch_loss += cost_iter

                    buffer = []

                    buffer_label = []

            print('Epoch {}. Total loss: {}'.format(epoch+1, epoch_loss))

    correct = tf.equal(tf.argmax(nn_output, 1), tf.argmax(y, 1))

    accuracy = tf.reduce_mean(tf.cast(correct, 'float'))

    with open('test_hot_vectors.pickle', 'rb') as train_vec:

        buffer = []

        buffer_label = []

        for i in range(line_sizes['test']):

            test_vector_line = pickle.load(train_vec)

            buffer.append(test_vector_line[0])

            buffer_label.append(test_vector_line[1])

    print('Accuracy using test dataset: {}'.format(accuracy.eval({in_placeholder: buffer})))
```

# 使用模型

示例 A-3 显示了`use_neural_net.py`模型。

示例 A-3 `use_neural_net.py`文件

```python
import tensorflow as tf
import pickle
import numpy as np
from nltk.tokenize import word_tokenizer
from nltk.stem import WordNetLemmatizer
from sentiment_neural_net import ff_neural_net
from sentiment_neural_net import training

lem = WordNetLemmatizer()
x = tf.placeholder('float')
```

```python
def get_sentiment(input_data):
    tf.reset_default_graph()
    pl = tf.placeholder('float')
    nn_output = ff_neural_net(pl)
    saver = tf.train.Saver()
    with open('word_dict.pickle', 'rb') as f:
        word_dict = pickle.load(f)
```

注意：此脚本生成的文件保存在运行脚本时的相同目录中。

# 使用

本节显示了命令语法、其标志、示例运行及其结果：

```
$ plc.pl [-b bmc_address | -i ] [-a admin_pw] [-s sysadmin_pw] [-h host -u user -p password] [-f]
```
