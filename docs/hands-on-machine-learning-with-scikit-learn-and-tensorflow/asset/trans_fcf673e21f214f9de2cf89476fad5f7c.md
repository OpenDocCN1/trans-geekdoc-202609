

# 从多个文件中交错读取行

首先，假设你加载了加利福尼亚住房数据集，对其进行了洗牌（除非它已经洗牌过），将其拆分为训练集、验证集和测试集，然后将每个集合都拆分为许多 CSV 文件，每个文件如下所示（每行包含 8 个输入特征加上目标中位房价）：

| MedInc,HouseAge,AveAoms,AveBedsrms,Pop,AveOcc,Lat,Long,MedianHouseValue |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 3.5214 |15.0349 |8.91065 |14.7 |1.6599 |37.63|-122.43 |1.442 |
| 5.3275 |5.0 |6.9800 |0.9910 |3.463 |3.4433 |33.69|-117.39 |1.687 |
| 3.1290 |7.5423 |1.5915 |1328.0 |2.2508 |38.44|-122.98 |1.621 |

假设 `train_filepaths` 包含文件路径列表（你还有 `valid_filepaths` 和 `test_filepaths`）：

```python
>>> train_filepaths
['datasets/housing/my_train_00.csv', 'datasets/housing/my_train_01.csv', ...]
```

现在创建一个仅包含这些文件的数据集：

```python
filepath_dataset = tf.data.Dataset.list_files(train_filepaths, seed=42)
```

默认情况下，`list_files()` 返回一个会打乱文件路径的数据集。通常情况下这是一件好事，但如果你出于某些原因不希望这样做，可以设置 `shuffle=False`。

接下来，我们可以使用 `interleave()` 每次读取 5 行并将它们交错读取（使用 `skip()` 方法跳过每个文件的第一行，即表头行）：

```python
n_readers = 5
dataset = filepath_dataset.interleave(
    lambda filepath: tf.data.TextLineDataset(filepath).skip(1),
    cycle_length=n_readers
)
```

`interleave()` 方法将创建一个数据集，从 `filepath_dataset` 中提取 5 个文件路径，并对每个路径它都会调用我们提供的函数（在此示例中为 lambda）来创建一个新的 `TextLineDataset`。它会在这 5 个数据集之间循环，每次读取一行，直到所有数据集都数据数据。然后它将从 `filepath_dataset` 获取下 5 个文件路径并以同样的方式进行交错，以此类推，直到路径耗尽。

![](img/0684d2da98e09085c0a622d4fd69aaad_433_0.png)

为了让交错效果最好，最好具有长度相同的文件，否则最长文件的末尾将无法交错读取。

默认情况下，`interleave()` 不使用并行计算，它会从每个文件中顺序读取一行。然而，如果你想让它实际上并行读取文件，可以将 `num_parallel_calls` 参数设置为你使用的线程数。你可以将其设置为 `tf.data.experimental.AUTOTUNE`，让 TensorFlow 根据可用的 CPU 动态选择合适的线程数（这目前是一项实验性功能）。让我们看看数据集包含什么：

```python
>>> for line in dataset.take(5):
...    print(line.numpy())
...
b'4.2083,44.0,5.3232,0.8171,04.2,2.3770,33.73,-122.2,2.7872'
b'4.1812,52.0,5.7013,0.9659,0.2,2.4027,33.73,-118.31,3.215'
b'3.6875,44.0,5.2414,0.9959,0.3,1.9538,34.04,-118.15,1.625'
b'3.3456,37.0,4.5140,0.9858,0.3,2.2253,36.67,-121.7,2.526'
b'3.5214,15.0,3.0899,1.1865,14.0,1.6059,36.7,-122.43,1.4402'
```

这些是随机选择的 CSV 文件第一行（包括表头）。很好！但如你看到的，这些只是字符串，我们需要解析它们，并对数据进行缩放。

# 数据预处理

让我们实现执行此预处理的小函数：

```python
X_mean, X_std = [..] # 训练集中每个特征的均值和缩放
n_inputs = 8
```

```python
def preprocess(line):
    defs = [0.] * n_inputs + [tf.constant([], dtype=tf.float32)]
    fields = tf.stack(tf.io.decode_csv(line, record_defaults=defs))
    x = tf.stack(fields[:-1])
    y = tf.stack(fields[-1:])
    return (x - X_mean) / X_std
```

让我们来看一下这段代码：

- 首先，假设我们已经预计算了训练集中每个特征的均值和标准差。`X_mean` 和 `X_std` 是包含 8 个值的 1D 张量（或 NumPy 数组），每个输入特征一个。
- `preprocess()` 函数接收一个 CSV 行并对其解析。为此，它使用 `tf.io.decode_csv()` 函数，该函数接受两个参数：第一个是待解析的行，第二个是包含每列默认值的数组。这不仅告诉 TensorFlow 每列的默认值，还告诉列数和每列的类型。例如，我们告诉它所有特征都是浮点数，并且通过提供空数组 `tf.float32` 作为最后一列（目标）的默认值来处理缺失值：这告诉 TensorFlow 没有默认值，因此如果遇到缺失值，它将抛出异常。
- `decode_csv()` 函数返回标量张量的列表（每列一个），但我们需要返回 1D 张量。我们调用 `tf.stack()`。
- 最后，通过减去均值并除以标准差来缩放特征（此处原文代码未闭合，但逻辑如此）。

让我们看看数据集包含什么：

```python
>>> for line in dataset.take(5):
...    print(line.numpy())
...
b'4.2083,44.0,5.3232,0.8171,04.2,2.3770,33.73,-122.2,2.7872'
b'4.1812,52.0,5.7013,0.9659,0.2,2.4027,33.73,-118.31,3.215'
b'3.6875,44.0,5.2414,0.9959,0.3,1.9538,34.04,-118.15,1.625'
b'3.3456,37.0,4.5140,0.9858,0.3,2.2253,36.67,-121.7,2.526'
b'3.5214,15.0,3.0899,1.1865,14.0,1.6059,36.7,-122.43,1.4402'
```

这些是随机选择的 CSV 文件第一行（包括表头）。很好！但如你看到的，这些只是字符串，我们需要解析它们，并对数据进行缩放。

# 整合所有内容

为了使代码可读，让我们把讨论的所有内容整合到一个较小的函数中：它将从多个文件高效地加载数据、进行洗牌并处理（见图 13-2）：

```python
def csv_reader_dataset(filepaths, repeat=None, n_readers=5,
    n_threads=None, shuffle_buffer_size=10000, batch_size=32):
    dataset = tf.data.list_files(filepaths).repeat(repeat)
    dataset = dataset.interleave(lambda filepath: tf.data.TextLineDataset(filepath).skip(1),
        cycle_length=n_readers, num_parallel_calls=n_threads)
    dataset = dataset.shuffle(shuffle_buffer_size)
    dataset = dataset.map(preprocess, num_parallel_calls=n_threads)
    dataset = dataset.batch(batch_size)
    return dataset.prefetch(1)
```

![](img/0684d2da98e09085c0a622d4fd69aaad_436_0)

图 13-2. 从多个 CSV 文件加载和预处理数据

# 预取 (Prefetching)

通过最后调用 `prefetch(1)`，我们正在创建一个尽可能始终领先一个批的数据集。换句话说，当我们的算法处理一个批数据时，数据集已经在并行准备下一批数据了。这可以显著提高性能。如果我们还确保加载和预处理是多线程的（通过调用 `interleave` 和 `map` 时设置 `num_parallel_calls`），我们就可以利用 CPU 的多个核心，并希望准备一个批的数据比在 GPU 上运行一个步骤的时间短：这样 GPU 将几乎 100% 利用（除了从 CPU 到 GPU 的数据传输时间），训练将运行得更快。

> 一般来说

# 不预取

| CPU | 准备 1 | 准备 2 | 准备 |
| :--- | :--- | :--- | :--- |
| GPU | 使用 1 | 使用 2 | 时间 |

# 使用预取

| CPU | 准备 1 | 准备 2 | 准备 3 | 准备 4 |
| :--- | :--- | :--- | :--- | :--- |
| GPU | 使用 1 | 使用 2 | 使用 3 |

# 使用预取 + 多线程加载与预处理

| CPU 线程 1 | 准备 1 | 准备 2 | 准备 3 | 准备 4 | 准备 5 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CPU 线程 2 | | | | | |
| GPU | 使用 1 | 使用 2 | 使用 3 | 使用 4 |

图 13-3. 使用预取和多线程加速训练任务

