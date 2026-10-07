numbers.

# LISTING 6.25: tf-random-one-shot2.py

```
import tensorflow as tf
import numpy as np

# two Numpy arrays with random numbers
features, labels = (np.random.sample((100,2)),
p.random.sample((100,1)))
dataset = tf.data.Dataset.from_tensor_slices
((features, labels))

iter = dataset.make_one_shot_iterator()
el = iter.get_next()

with tf.Session() as sess:
    print(sess.run(el))
```

Listing 6.25 initializes the variables features and labels that are generated from a NumPy array consisting of 100 rows and 2 columns of randomly generated numbers, and from a NumPy array consisting of 100 rows and 1 column of randomly generated numbers.

Next, the variable dataset is initialized as a TF Dataset that is created from the contents of the features and labels. The next snippet defines the variable iter as a “one-shot” iterator, followed by the variable el that is populated with the first element in the variable dataset. The final portion of Listing 6.25 prints the first line of transformed data, as shown here:

```
(array([0.47582573, 0.36387037]),
array([0.26763744]))
```

# TF DATASETS FROM CSV FILES