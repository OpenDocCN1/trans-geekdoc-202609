

![](img/e891acaacd4fb5b80dab2ed824618203_360_0.png)

图 9.15 ffill 的实现逻辑。(a) 带有缺失值的输入数据示意图；(b) 回溯偏移量逻辑的创建。在当前示例中，有四组空条目。第 1 组和第 2 组只有单个空值条目，而第 3 组和第 4 组有两个空条目。因此，对于第 1 组和第 2 组，偏移量只需回溯 1 个值（回溯 1），而对于第 3 组和第 4 组，组内的每个后续索引需要多回溯 1，即 -1、-2，依此类推。(c) 给定矩阵的所有索引集合，我们在每个空条目处应用回溯逻辑。(d) 使用 gather 重新创建填充了空值的矩阵的迭代示例。请注意，第二行的前两个值无法使用 ffill 方法填充。

使用 (0, 1) 处的非空值。使用相同的逻辑，对于多索引 (1, 1) 处出现的空值，我们需要回溯两个索引以使用 (1, -1) 处的非空值。但是，在 (1, 1) 处的值之前没有出现非空值，因为该行以空值开头，因此我们需要保持此条目为空。因此，我们将索引裁剪以重复使用索引 0 处的值，而索引 0 碰巧是一个空条目。

- 第 26–29 行创建完整的回溯偏移量数组。我们先创建一个全为 -1 的数组。然后，我们替换空段的回溯偏移量值。请参见图 9.15b 了解示意图。

- 第 32–39 行更新矩阵值索引，将任何空值的索引替换为用于替换空值的相应索引。请参见图 9.15c 了解示意图。

- 第 44 行处理任何剩余的 -1。算法试图使用最近的前一个值来填充当前的空值，但如果空值在行的开头，就不存在可以使用的前一个值。因此，这些空条目在 ffill 后仍保持为空。我们将索引矩阵裁剪为最小值 0，将剩余的 -1 替换为 0 索引，这对应于一个空值。

- 第 47–48 行使用 gather 操作从原始矩阵重新采样值。如果原始索引处的原始值不是空值，则保持不变。但是，如果原始索引处的原始值是空条目，则我们从最近的非空值索引处采集。请参见图 9.15d 了解示意图。

bfill 很容易实现，因为我们只需反转序列，然后再次调用 ffill。以下是先 ffill 再 bfill 缺失值后的最终结果。

```
1 event_timestamp = tf.constant( # reproduced from above
2     [
3         [
4             "2022-03-15 06:23:24",
5             "2022-03-15 06:23:38",
6             "",
7             "2022-03-15 06:24:58",
8             "",
9         ],
10        ["", "", "2022-03-18 06:24:37", "", ""],
11    ]
12 )
13
14 # ffill
15 event_timestamp_filled = ffill(event_timestamp)
16 # bfill
17 event_timestamp_filled = ffill(event_timestamp_filled[:, ::-1])
```

```
<tf.Tensor: shape=(2, 5), dtype=string, numpy=
array([[b'2022-03-15 06:24:58', b'2022-03-15 06:24:58',
       b'2022-03-15 06:23:38', b'2022-03-15 06:23:38',
       b'2022-03-15 06:23:24'],
      [b'2022-03-18 06:24:37', b'2022-03-18 06:24:37',
       b'2022-03-18 06:24:37', b'2022-03-18 06:24:37',
       b'2022-03-18 06:24:37']], dtype=object)>
```

## Bibliography

Martín Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. TensorFlow 量化。https://www.tensorflow.org/model_optimization/guide/quantization/post_training, 2023.

Yoshua Bengio, Réjean Ducharme, Pascal Vincent, and Christian Jauvin. 一种神经概率语言模型, 2003.

Alexey Dosovitskiy, Lucas Beyer, Alexander Kolesnikov, Dirk Weissenborn, Xiaohua Zhai, Thomas Unterthiner, Mostafa Dehghani, Matthias Minderer, Georg Heigold, Sylvain Gelly, Jakob Uszkoreit, and Neil Houlsby. 一图抵十六字：用于大规模图像识别的 Transformer, 2021 年 6 月.

Google. TFHub NNLM Kaggle 模型。https://www.kaggle.com/models/google/nnlm, 2023.

Kaiming He, Xinlei Chen, Saining Xie, Yanghao Li, Piotr Dollár, and Ross Girshick. 掩码自编码器是可扩展的视觉学习者, 2021 年 12 月.

Adam Paszke, Sam Gross, Francisco Massa, Adam Lerer, James Bradbury, Gregory Chanan, Trevor Killeen, Zeming Lin, Natalia Gimelshein, Luca Antiga, Alban Desmaison, Andreas Köpf, Edward Yang, Zach DeVito, Martin Raison, Alykhan Tejani, Sasank Chilamkurthy, Benoit Steiner, Lu Fang, Junjie Bai, and Soumith Chintala. PyTorch 量化。https://pytorch.org/docs/stable/quantization.html#module-torch.ao.quantization, 2023.

Juan Terven and Diana Cordova-Esparza. YOLO 全面综述：从 YOLOv1 及以后, 2023 年 10 月.

Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, and Illia Polosukhin. 注意力就是你所需要的。神经信息处理系统进展，2017-Decem (Nips)，第 5999–6009 页，2017。ISSN 10495258.

Ruibin Xiong, Yunchang Yang, Di He, Kai Zheng, Shuxin Zheng, Chen Xing, Huishuai Zhang, Yanyan Lan, Liwei Wang, and Tie-Yan Liu. 关于 Transformer 架构中的层归一化, 2020 年 6 月.

## 10 排序与重排

无论是处理连续时间序列还是分析其他形式的按顺序表示的离散数据，通常以批处理方式处理序列数据比使用 for 循环逐个序列应用处理逻辑更高效。如果所有序列长度相同，序列数据通常表示为密集张量。然而，并非所有序列长度都相同，因此，序列数据通常表示为带填充的密集张量（其数据条目可由填充掩码确定），或左对齐的不规则或稀疏张量。在本章中，我们将重点介绍几种对批量变长序列数据进行排序和重排的不同方式的案例研究。我们将运用迄今所学的所有向量化知识来实现这些问题的解决方案。

> 通常，TensorFlow 将一批序列数据表示为形状为 `(batch_size, seq_len, <embed_size> ...)` 的张量，而 PyTorch 则将其表示为形状为 `(batch_size, <embed_size> ..., seq_len)` 的张量。这是库之间不同约定的一个小细节。在本章中，我将在示例代码中使用 TensorFlow 约定，但通过正确转置张量，可以相对容易地实现 PyTorch 约定。

### 10.1 排序操作

**排序**是计算机科学中的一项基本操作，它根据某些排序规则重新排列数组中的元素。表 10.1 列出了在 NumPy、TensorFlow 和 PyTorch 中实现的等效排序操作。

### 表 10.1 NumPy、TensorFlow 和 PyTorch 中的排序操作列表。

| 操作 | NumPy | TensorFlow | PyTorch |
| :--- | :--- | :--- | :--- |
| 排序^a) | np.sort | tf.sort | torch.sort |
| 对数组排序的索引^a) | np.argsort | tf.argsort | torch.argsort |
| 字典序排序^b) | np.lexsort | N/A | N/A |
| 唯一值/索引^c) | np.unique | tf.unique, tf.unique_with_counts | torch.unique |
| 最大值^d) | np.max | tf.reduce_max | torch.max |
| 最大值索引^d) | np.argmax | tf.argmax | torch.argmax |
| 最小值^d) | np.min | tf.reduce_min | torch.min |
| 最小值索引^d) | np.argmin | tf.argmin | torch.argmin |
| Top K 最小/最大值^c) | N/A | tf.math.top_k | torch.topk |
| 分区^f) | np.partition | N/A | N/A |
| 对数组分区的索引^f) | np.argpartition | N/A | N/A |
| 已排序数组的插入索引^g) | np.searchsorted | tf.searchsorted | torch.searchsorted |

注释：
a) 默认情况下，`.sort` 操作将数组按升序（从小到大）排序。然而，在 TensorFlow 和 PyTorch 的实现中，用户可以指定参数以降序（从大到小）排序。对于 TensorFlow，这是 `tf.sort(direction="DESCENDING")`，而对于 PyTorch，这是 `torch.sort(descending=True)`。对于 NumPy，我们可以使用 `[:, -1]` 反转排序顺序。`.argsort` 操作返回可用于对原始数组排序的索引。
b) `np.lexsort` 仅限于 NumPy。它根据指定的键对一组数组进行一起排序。在下一个案例研究中，我们将看到如何使用 `np.lexsort` 来对矩阵的行进行排序。
c) `.unique` 操作返回唯一内容集。它还可以返回：
- 可用于将原始张量转换为唯一集的索引。在 NumPy 中，这是设置 `return_index=True`；在 TensorFlow 中，这是使用 `tf.unique` 并使用第二个返回输出。在撰写本章时，PyTorch 似乎未实现此功能。
- 可用于从唯一集恢复原始张量的索引。在 NumPy 和 PyTorch 中，这是设置 `return_inverse=True`。在 TensorFlow 中，这是调用 `tf.unique_with_counts` 并使用第二个返回输出。

