```
LISTING 6.22: tf-zip-batch.py

import tensorflow as tf
import numpy as np

ds1 = tf.data.Dataset.range(100)
ds2 = tf.data.Dataset.range(0, -100, -1)
ds3 = tf.data.Dataset.zip((ds1, ds2))
ds4 = ds3.batch(4)
```

```
iterator = ds4.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    print(sess.run(next_element))
    print(sess.run(next_element))
    print(sess.run(next_element))
```

Listing 6.22 initializes the variables ds1, ds2, ds3, and ds4 TF Datasets that are created successively, starting from ds1 that contains the integers between 0 and 99 inclusive.

The next portion of Listing 6.22 defines the variable iterator as a “one-shot” iterator, followed by the variable next_element that is populated with the first element in the variable dataset. The final portion of Listing 6.22 prints three lines of “batched” output, as shown here:

```
array([0, 1, 2, 3]), array([ 0, -1, -2, -3]))
array([4, 5, 6, 7]), array([-4, -5, -6, -7])
array([ 8, 9, 10, 11]), array([ -8, -9, -10, -11]))
```

# COMBINING THE TF ZIP() AND TAKE() OPERATORS