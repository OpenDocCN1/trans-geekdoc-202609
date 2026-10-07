
# THE TENSORFLOW BATCH() OPERATOR (2)

Listing 6.12 displays the contents of tf-batch2.py that illustrates how to use the batch() operator in TensorFlow with a one-shot iterator.

LISTING 6.12: tf-batch2.py

```
import tensorflow as tf
import numpy as np

x = np.arange(0, 33)
ds = tf.data.Dataset.from_tensor_slices(x).batch(3)
iterator = ds.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    for i in range(11):
        val = sess.run(next_element)
        print(val)
```

Listing 6.12 initializes the variable x as a NumPy array consisting of the integers from 0 through 32 inclusive. Next, the variable ds is initialized as a TF Dataset that is created from the contents of the variable x. Notice how method chaining is performed by “tacking on” batch(3) operator as part of the definition of ds.

The next code snippet defines the variable iterator as a “one-shot” iterator, followed by the variable next_element that is populated with the first integer in ds (which is the integer 0).

The final portion of Listing 6.12 contains a loop that executes 11 times, and during each iteration the loop prints eleven “triples” of consecutive integers, starting with the triple [0 1 2]. The output from launching the code in Listing 6.12 is:

```
[0 1 2]
[0 1 2]
[3 4 5]
[6 7 8]
[ 9 10 11]
[12 13 14]
[15 16 17]
[18 19 20]
[21 22 23]
[24 25 26]
[27 28 29]
[30 31 32]
```

![](img/55c2af1cab44d6186a8b2008b93f459f_294_0.png)

The companion disc contains tf-batch3.py, tf-batch4.py, and tf-batch5.py that illustrate variations of the preceding code sample. Experiment with the code by changing the hard-coded values and then see if you can correctly predict the output.

# THE TENSORFLOW MAP() OPERATOR (1)

Listing 6.13 displays the contents of tf-map.py that illustrates how to use the map() operator in TensorFlow with a one-shot iterator.

# LISTING 6.13: tf-map.py

```
import tensorflow as tf
import numpy as np

# a simple Numpy array
x = np.array([[1],[2],[3],[4]])

# make a dataset from a numpy array
dataset = tf.data.Dataset.from_tensor_slices(x)

# a lambda expression to double each value
dataset = dataset.map(lambda x: x*2)

# define an iterator
iter = dataset.make_one_shot_iterator()
el = iter.next()

with tf.Session() as sess:
    for _ in range(len(x)):
        print("value:", sess.run(el))
```

Listing 6.13 initializes the variable x as a NumPy array consisting of four elements, where each element is a 1x1 array consisting of the numbers 1, 2, 3, and 4. Next, the variable dataset is initialized as a TF Dataset that is created from the contents of the variable x. Notice how dataset.map() then defines a lambda expression that doubles each input value, which consists of the integers from 1 to 4 in this example.

The next snippet defines the variable iter as a “one-shot” iterator, followed by the variable el that is populated with the first element in the variable dataset.

The final portion of Listing 6.13 iterates through the element of dataset and displays their values. The output from launching the code in Listing 6.13 is:

```
('value:', array([2]))
('value:', array([4]))
('value:', array([6]))
('value:', array([8]))
```

# THE TENSORFLOW MAP() OPERATOR (2)

Listing 6.14 displays the contents of tf-map2.py that illustrates how to invoke the map() operator three times in TensorFlow with a one-shot iterator.

# LISTING 6.14: tf-map2.py

```
import tensorflow as tf
import numpy as np

# a simple Numpy array
x = np.array([[1],[2],[3],[4]])

# make a dataset from a Numpy array
dataset = tf.data.Dataset.from_tensor_slices(x)

# METHOD #1: THE LONG WAY
# a lambda expression to double each value
dataset = dataset.map(lambda x: x*2)
# a lambda expression to add one to each value
dataset = dataset.map(lambda x: x+1)
# a lambda expression to cube each value
dataset = dataset.map(lambda x: x**3)

# METHOD #2: A SHORTER WAY
dataset = dataset.map(lambda x: (x*2+1)**3)

# define an iterator
iter = dataset.make_one_shot_iterator()
el = iter.next()

with tf.Session() as sess:
    for _ in range(len(x)):
        print("value:", sess.run(el))
```
*(Note: The OCR text for Method 2 in 6.14 was corrupted in the source; I have reconstructed the logical structure based on standard TensorFlow patterns and the context of mapping operations.)*
