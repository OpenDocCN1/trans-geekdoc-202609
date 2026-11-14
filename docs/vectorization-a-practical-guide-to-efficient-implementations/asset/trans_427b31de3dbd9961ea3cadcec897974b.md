

```
3 unique, index = np.unique(feature, return_inverse=True)
4 # unique = array(["a", "b", "c"], dtype="<U1")
5 # index = array([0, 1, 2, 1, 0])
```

这里，`unique` 数组将作为分类特征的词汇表，而 `index` 则是相应的索引。可以很容易地验证，使用类别的 `unique` 词汇表和索引，我们可以重建特征。

```
6 # code continues from above
7 recovered_feature = np.take(unique, index)
8 assert np.all(feature == recovered_feature)
```

然而，使用 `np.unique` 的缺点在于，确定的索引可能无法复现：如果原始列表的顺序发生变化，则不再保证相同的字符串值会映射到相同的整数索引值。例如，

```
1 import numpy as np
2
3 feature_a = ["a", "b", "c", "b", "a"]
4 feature_b = ["c", "b", "a", "b", "b"]
5
6 _, index_a = np.unique(feature_a, return_inverse=True)
7 # array([0, 1, 2, 1, 0])
8 _, index_b = np.unique(feature_b, return_inverse=True)
9 # array([2, 1, 0, 1, 1])
```

Pandas 还具有 `pd.factorize` 方法，可以实现类似的效果。

## 6.4.2 Pandas pd.Categorical

与使用 `pd.factorize` 不同，在 Pandas 中对字符串值进行编码的另一种方法是使用 `pd.Categorical` 数据类型来表示特征列。我们可以像下面这样创建带有分类列的 Pandas DataFrame：

```
1 import pandas as pd
2 df = pd.DataFrame({
3 "user_id": pd.Series([1, 2, 3, 4, 5, 6], dtype=int),
4 "age": pd.Series([
5 "18-25", "65+", "26-30", "30-40", "40-50", "50-65"
6 ], dtype="category")
7 })
```

显示表格，

| user_id | age |
|---|---|
| 1 | 18-25 |
| 2 | 65+ |
| 3 | 26-30 |
| 4 | 30-40 |
| 5 | 40-50 |
| 6 | 50-65 |

我们可以使用 `df.info(memory_usage="deep")` 来检查数据类型以及表在内存中的大小：

```
# df.info(memory_usage="deep")
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 6 entries, 0 to 5
Data columns (total 2 columns):
 #   Column      Non-Null Count  Dtype
---  ------      --------------  -----
 0   user_id     6 non-null      int64
 1   age         6 non-null      category

dtypes: category(1), int64(1)
memory usage: 724.0 bytes
```

使用 pd.Categorical 的一个优势是节省 DataFrame 的内存占用。假设我们有一个包含两个分类特征的大得多的表：

```
import pandas as pd
df = pd.DataFrame({
    "user_id": pd.Series(np.arange(6000), dtype=int),
    "age": pd.Series([
    "18-25", "65+", "26-30", "30-40", "40-50", "50-65"
] * 1000, dtype="category"),
"item_id": pd.Series([
    "qbirwk5xss1lhtsbgtoct782jd9asopijt9m4132s5xfrtomiq8cuabc9z2y",
    "cuOlw3xoat1lpge1ikuu2q25bxxkqlaivwskkp631iqbtgsq9mbmbkszyntSmg8",
    "glg7hb0a0tiii3huq7iixx3rdmt36sz0869hw439o7iwtdtxslcglx6whtj1j6",
    "4w58m7a91s4q3968oc8xnlom4p89zh14vt014atllif86bclh4hf7xnaugu3",
    "cbjgeyvraoamkpkrebftrffnpivbnzpiikyjmgsoelabulobgfbmedwsozrv",
    "qbivirv9xs6lhtsgbtoc782jda9opijt9m4l32s5xftfromiq8cuabc9z2y0"
] * 1000, dtype="category")
})
# make a copy of the table, and set the "age" and "item_id" columns to
# string
df_non_category = df.copy()
df_non_category["age"] = df_non_category["age"].astype(str)
df_non_category["item_id"] = df_non_category["item_id"].astype(str)
```

然后我们可以比较上面创建的两个表的内存占用，一个使用 pd.Categorical，另一个不使用它来存储这两个字符串特征：

```
# df.info(memory_usage="deep")
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 6000 entries, 0 to 5999
Data columns (total 3 columns):
 #   Column       Non-Null Count  Dtype
 ---  ------       --------------  -----
  0   user_id     6000 non-null   int64
  1   age         6000 non-null   category
  2   item_id     6000 non-null   category
dtypes: category(2), int64(1)
memory usage: 60.0 KB

# df_non_category.info(memory_usage="deep")
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 6000 entries, 0 to 5999
Data columns (total 3 columns):
 #   Column       Non-Null Count  Dtype
 ---  ------       --------------  -----
  0   user_id     6000 non-null   int64
  1   age         6000 non-null   object
  2   item_id     6000 non-null   object
dtypes: int64(1), object(2)
memory usage: 1.1 MB
```

包含非分类列的表占用 1.1 MB 内存。相比之下，将两列存储为分类变量时仅使用了 60.0 KB 内存，内存占用节省了近 20 倍！

LightGBM 和 XGBoost 等基于树的模型库的更新版本可以直接处理 pd.Categorical 特征，而无需创建进一步的索引查找。在使用机器学习模型时，这是使用 pd.Categorical 的另一优势。

## 6.4.3 Scikit-learn sklearn.preprocessing.LabelEncoder

迄今为止我们讨论的编码方法都无法轻松重用字符串值与索引之间的映射，而在生产环境中对新数据进行推理时，这是一个必要条件。sklearn.preprocessing.LabelEncoder 类允许我们创建并保存映射以供以后使用。

```python
from sklearn.preprocessing import LabelEncoder
vocabulary = [chr(ii+97) for ii in range(26)]
feature_train = ["b", "a", "c", "d", "z"]
# Create the encoder
feature_lookup = LabelEncoder()
feature_lookup.fit(vocabulary)
# Transform during training
index_train = feature_lookup.transform(feature_train)
# array([1, 0, 2, 3, 25])
# New data during inference
feature_test = ["f", "g", "a", "b", "h"]
index_test = feature_lookup.transform(feature_test)
# array([5, 6, 0, 1, 7])
```

请注意，feature_train 和 feature_test 特征中都包含字符串值 a 和 b。相应的 index_train 和 index_test 索引分别均为 0 和 1。这表明 sklearn.preprocessing.LabelEncoder 可以（重新）生成一致的字符串值到索引映射。

## 6.4.4 Tensorflow tf.lookup

Tensorflow 的 tf.lookup 提供了另一套工具，用于将特征的字符串值转换为索引。tf.lookup 具有构建哈希表的方法，因此可用于更通用的用途，而不仅限于字符串到整数的映射。在我看来，tf.lookup 的一个关键特性是能够处理不在词汇表中的新特征值（OOV）。这是迄今为止我们讨论的三个库中所缺少的。在我的日常实践中，我通常保留索引 0 供 OOV 词汇使用，并从索引 1 开始。另一种选择是仍然使用 0 作为第一个索引，并使用索引 len（vocabulary）作为 OOV 索引（我们也可以将 -1 用作等效替代方案）。为了说明用法，假设我们有一个字母表列表，希望将其映射为整数索引：

```python
import tensorflow as tf
# Create a list to store all the alphabet
alphabet_lookup = tf.constant([chr(ii+97) for ii in range(26)])
# Last value in the list is oov
values = tf.constant(["b", "a", "c", "d", "z", "1"])
# Create the lookup hash table
table = tf.lookup.StaticHashTable(
    tf.lookup.KeyValueTensorInitializer(
        keys=alphabet_lookup,
        # index starts from 1
        values=list(range(1, len(alphabet_lookup)+1)),
        key_dtype=tf.string,
        value_dtype=tf.int64,
    ),
    default_value=0, # oov
)
# Map the values
index = table.lookup(values)
# <tf.Tensor: shape=(6,), dtype=int64, numpy=array([ 2, 1, 3, 4, 26, 0])>
```

tf.lookup 还可以通过加载文本文件来创建查找表。

```python
import os
import tempfile
import tensorflow as tf
# Create a list to store all the alphabet and save to a file
alphabet_lookup = [chr(ii+97) for ii in range(26)]
_, file_path = tempfile.mkstemp()
with open(file_path, "w") as fid:
    fid.write("\n".join(alphabet_lookup))
# Last value in the list is oov
values = tf.constant(["z", "a", "c", "q", "h", "3"])
# Create the vocabulary lookup
table = tf.lookup.StaticHashTable(
    tf.lookup.TextFileInitializer(
        filename=file_path,
        # each line of the text file is a feature value
        key_index=tf.lookup.TextFileIndex.WHOLE_LINE,
        # use the line number as the index of the value
```

