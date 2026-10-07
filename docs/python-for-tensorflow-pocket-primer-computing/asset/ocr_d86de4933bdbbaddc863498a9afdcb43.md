corresponds to the title that is allotted to each feature. These titles are used later for extracting the data from TFRecord. The created dictionary is passed as input to a Feature class. Finally, the features object is passed as input to Example class that is appended into the TFRecord. The preceding process is repeated for every type of data that is stored in TFRecord.

The TFRecord file is a record-oriented binary format that you can use for training data. In addition, the tf.data.TFRecordDataset class enables you to stream over the contents of one or more TFRecord files as part of an input pipeline.

You can store any type of data, including images, in the Example format. However, you specify the mechanism for arranging the data into serialized bytes, as well as reconstructing the original format.

# A Simple TFRecord

Listing 6.29 displays the contents of tf-record1.py illustrates how to define a TFRecord.

LISTING 6.29: tf-record1.py

```
import tensorflow as tf

simple1 = tf.train.Example(features=tf.train.Features(feature={
  'my_ints':
  tf.train.Feature(int64_list=tf.train.Int64List(value=[2, 5])),
  'my_float':
  tf.train.Feature(float_list=tf.train.FloatList(value=[3.6])),
  'my_bytes':
  tf.train.Feature(bytes_list=tf.train.BytesList(value=['data']))
})))))
```