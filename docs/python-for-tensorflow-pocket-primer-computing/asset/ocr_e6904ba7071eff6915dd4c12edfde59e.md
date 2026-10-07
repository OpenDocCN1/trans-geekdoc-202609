+   2. Create an Iterator
3. Consume the Data

There are many ways to populate a TF Dataset with data that can be retrieved from multiple sources. For simplicity, the code samples in the first part of this chapter perform the following steps: first create a TF Dataset instance with an initialized NumPy array of data; second, define an iterator instance in order to iterate through the TF Dataset; and third, use the iterator to access the elements of the dataset (and in some cases, supply those elements to a TF model).

# A Simple TensorFlow Dataset

Listing 6.1 displays the contents of tf-numpy-dataset.py that illustrates how to create a TF Dataset from a NumPy array of numbers. Although this code sample is minimalistic, it is the starting point in other code samples in this chapter.

> LISTING 6.1: tf-numpy-dataset.py

```
import tensorflow as tf
import numpy as np

x = np.arange(0, 10)

# make a dataset from a numpy array
dataset = tf.data.Dataset.from_tensor_slices(x)
```

Listing 6.1 contains two import statements and then initializes the variable x as the integers from 0 through 9 inclusive. The variable dataset is initialized as a TF Dataset is based on the contents of the variable x.

Note that nothing else happens in Listing 6.1; later you will see more meaningful code samples involving TF Datasets.