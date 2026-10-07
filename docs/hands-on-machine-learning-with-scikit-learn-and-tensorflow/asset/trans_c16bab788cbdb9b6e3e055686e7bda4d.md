

```python
message Feature {
  Bytes bytes_list = 1;
  Floatlist float_list = 2;
  Int64 int64_list = 3;
}

message Features { map<string, Feature> features = 1 };
message Example { Features features = 1 };
```

BytesList、FloatList 和 Int64List 的定义非常直观（对于重复数值字段使用 `[packed = true]` 以实现更高效的编码）。一个特征包含一个 BytesList、一个 FloatList 或一个 Int64List。Features（带 s）包含一个字典，将特征名称映射到对应的特征。最后，一个 example包含一个 Features 对象。以下是你如何编写一个 `tf.train.Example` 来表示之前之前的同一个人，并将其写入 TFRecord 文件。

```python
from tensorflow.train import BytesList, FloatList, Int64List
from tensorflow.train import Example, Features, Example
```

```python
person_example = Example(
  features={
    "name": Feature(bytes_list=BytesList(["Alice"])
    "id": Feature(int64_list=Int64List([123]))),
    "emails": Feature(bytes_list=BytesList(["b@b.com"]))
  }
)
```

这段代码有些冗长且重复，但它非常直观（你可以轻松地将其封装在一个较小的辅助函数中）。现在我们可以通过 `SerializeToString()` 方法对其进行序列化，它会将结果数据返回到 TFRecord 文件：

```python
with tf.io.TFRecordWriter("my_contacts.tfrecord") as f:
  f.write(person_example.SerializeToString())
```

通常情况下，你写的不仅仅是一个 example！通常情况下，你会创建一个转换脚本，从你的格式（例如 CSV 文件）读取数据，为每个实例创建一个 Example protobuf，将它们序列化并保存到多个 TFRecord 文件中，并在过程中对它们进行去洗牌处理（deuffling）。这需要一些工作，所以再次务必确保这确实是必要的（也许你的流水线使用 CSV 文件也能运行得很好）。

现在我们已经有了一个包含序列化 Example 的很不错的 TFRecord 文件，让我们尝试加载它。

# 加载和解析示例

为了加载序列化的 protobuf，我们将再次使用 `tf.data.TFRecordDataset`，并使用 `tf.io.parse_single_example()` 解析每个 Example。这是一个 TensorFlow 操作，因此它可以被包含在 TF Function 中。它至少需要两个参数：一个包含序列化数据的字符串张量，以及每个特征的描述。该描述是一个字典，将每个特征名称映射到 `tf.io.FixedLenFeature` 描述符（指示特征的形状、类型和默认值）或 `tf.io.VarLenFeature` 描述符（仅指示类型，如果长度可能会变化，例如 "emails" 特征）。例如：

```python
feature_description = {
    "name": tf.io.FixedLenFeature([])
```

```python
for serialized_example in tf.data.TFRecordDataset(['my_contacts.tfrecord']):
    parsed_example = tf.io.parse_single_example(serialized_example,
        feature_description)
```

固定长度特征被解析为普通张量，但变长度特征被解析为稀疏张量（sparse tensors）。你可以使用 `tf.sparse.to_dense()` 将稀疏张量转换为密集张量，但在情况下，直接访问其值更为简单：

```python
>>> tf.sparse.to_dense(parsed_example['emails'], default_value=b"")
<tf.Tensor: [...] dtype=string, numpy=array([b'a@b.com', b'c@d.com', [...]])])
>>> parsed_example['emails'].values
<tf.Tensor: [...] dtype=string, numpy=array([b'a@b.com', b'c@d.com', [...]])])
```

Byteslist 可以包含任何二进制数据，包括任何序列化的 example。例如，你可以使用 `tf.io.encode_jpeg` 将图像编码为 JPEG，并将此数据格式化为 Byteslist。当你的代码读取 TFRecord 时，它将从解析 Example 开始，然后你需要调用 `tf.io.decode_jpeg()` 来解析数据并获取原始图像（或者你可以使用 `tf.io.decode_image()`，它可以解码任何 BMP、GIF、JPEG 或 PNG 图像）。你还可以通过使用 `tf.io.serialize_tensor()` 序列化你使用的任何张量，将生成的字节字符串放入 Byteslist 特征中。当你解析 TFRecord 时，可以使用 `tf.io.parse_tensor()` 解析此数据。

与其使用 `tf.io.parse_single_example()` 逐个解析示例，你可能希望通过 `tf.io.parse_example()` 批量解析它们：

```python
dataset = tf.data.TFRecordDataset(["my_contacts.tfrecord"]).batch(10)
for serialized_examples in dataset:
    parsed_examples = tf.io.parse_example(serialized_examples,
    feature_description)
```

如你所见，Example 对于大多数情况可能足够了。然而，当你处理列表列表（lists of lists）时，它可能会有些繁琐。例如，假设你想对文本文档进行分类。每个文档可能表示为句子列表，其中每个句子表示为单词列表。而且每个文档还有一个评论列表，其中每条评论都表示为单词列表。此外，可能还有一些上下文数据，例如文档的作者、标题和发布日期。TensorFlow 的 SequenceExample protobuf 正是为这类情况设计的。

# 使用 SequenceExample Protobuf 处理列表列表

以下是 SequenceExample protobuf 的定义：

```python
message FeatureList { repeated Feature feature = 1 };
message FeatureLists { map<string, FeatureList> feature_list = 1 };
message SequenceExample {
  Features context = 1;
  FeatureLists feature_lists = 2;
}
```

SequenceExample 包含用于上下文数据的 Features，Features 包含 FeatureList 对象（例如，名为 "content" 的 FeatureList 和另一个名为 "comments" 的 FeatureList）。（注：原文此处存在大量重复段落，已按要求处理)。

