The dataset methods do not modify datasets, they create new ones, so make sure to keep a reference to these new datasets (e.g., set = ...), or else nothing will happen.

You can also apply any transformation you want to the items by calling the map() method. This creates a new dataset with all items doubled:

```
>>> dataset = dataset.map(lambda x: x * 2) # Items: [0,2,4,6,8,10,12]
```

This function is when you will call to apply preprocessing to your want data. Sometimes, this will include computations that can be quite intensive, such as reshaping or rotating an image, so you will want to spawn multiple threads to speed things up: it's as setting the num_parallel_calls argument.

While map() applies a transformation to each item, the apply() method applies a transformation to the dataset as a whole. For example, the following code "unbatches the dataset, by applying the unbatch() function to the dataset (this function is currently experimental, but it will most likely move to the core API in a future release). Each item in the new dataset will be a single integer tensor of a batch of 7 integers:

```
>>> dataset = dataset.apply(tf.data.experimental.unbatch()) # Items: 0,2,4,...
```

It is also possible to filter the dataset using the filter method:

```
>>> dataset = dataset.filter(lambda x: x < 10) # Items: 0 2 4 6 8 0 2 4 6...
```

You will want to look at a few items from a dataset. You can use the take() method for that:

```
>>> for item in dataset.take(3):
print(item)
...
tf.Tensor(0,shape=(), dtype=int64)
tf.Tensor(2,shape=(), dtype=int64)
tf.Tensor(4,shape=(), dtype=int64)
```

# Shuffling the Data

As you know, Gradient Descent works best when the instances in the training set are independent and identically distributed (see Chapter 4). For this, you can just use the shuffle() method. It will create a new dataset that will start by filling a buffer with the first items of the source dataset, then when it is asked for an item, it will pull out randomly from the buffer, and replace it with a fresh one from the source dataset, until it has iterated through the source dataset. At this point continues to pull items randomly from the buffer until it is empty. You must specify the buffer size, and