example, categorical features with a large number of categories (such as cities, or words) can be encoded using embeddings (as we will see, an embedding is a trainable dense vector that represents a category).

Both the Data API and the Features API work seamlessly with tf.keras.

In this chapter, we will cover the Data API, the TFRecord format and the Features API in detail. We will also take a quick look at a few related projects from TensorFlow's ecosystem:

+   - TF Transform (tf.Transform) makes it possible to write a single preprocessing function that can run in both mode on your full training set, before training (to speed it up), and exported to a TF Function and incorporated into your trained model, so once it is deployed in production, it can take care of preprocessing new instances on the fly.

+   - TF Datasets (TFDS) provides a convenient function to download many common datasets of all kinds, including large ones like ImageNet, and it provides convenient datasets to manipulate them using the Data API.

So let's get started!

# The Data API

The whole Data API revolves around the concept of a dataset: as you might suspect, this represents a sequence of data items. Usually you use datasets that gradually read data from disk, but for simplicity let's create a dataset in RAM using tf.data.Dataset.from_tensor_slices():

```
>>> X = tf.range(10) # any data tensor
>>> dataset = tf.data.Dataset.from_tensor_slices(X)
>>> dataset
<TensorSliceDataset shapes: (), types:int32>
```

The from_tensor_slices() takes a tensor and creates a tf.data.Dataset whose elements are all the slices of X (the first dimension), so this dataset contains 10 items: tensors 0, 1, 2, ..., 9. In this case we would have obtained the same dataset if we used tf.data.Dataset.range(10).

You can iterate over a dataset's items like this:

```
>>> for item in dataset:
    print(item)
```