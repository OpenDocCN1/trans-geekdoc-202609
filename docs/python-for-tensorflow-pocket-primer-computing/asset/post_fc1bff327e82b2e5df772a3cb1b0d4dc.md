
The answer lies in the conditional logic in the for loop: when the variable i equals 9, the iterator variable is “reset” to its initial value, thereby preventing an error. You can test this situation by “commenting out” the if statement, and when you launch the code you will see the following error message:

```
OutOfRangeError (see above for traceback): End of sequence
[[node IteratorGetNext (defined at tf-init-iterator.py:11) ]
```

Reset the code in Listing 6.5 to its original contents and you will see the following output when you launch the code in Listing 6.5 here:

+   0
1
2
3
4
5
6
7
8
9
0
1
2
3
4

# THE TENSORFLOW FILTER() OPERATOR

Listing 6.6 displays the contents of tf-filter.py that illustrates how to use the filter() operator in TensorFlow with a "one-shot" iterator.

# LISTING 6.6: tf-filter.py

```python
import tensorflow as tf
import numpy as np

def filter_fn(x):
    # return tf.reshape(tf.not_equal(x % 2, 1), [])

x = np.array([1,2,3,4,5,6,7,8,9,10])

ds = tf.Dataset.from_tensor_slices(x)
s = ds.filter(lambda x:
    tf.reshape(tf.not_equal(x%2,1), []))
#ds = ds.filter(filter_fn)

iterator = ds.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    try:
        while True:
            value = sess.run(next_element)
            print("value:",value)
    except tf.errors.OutOfRangeError:
        pass
    sess.run(iterator.initializer)
```

Listing 6.6 initializes the variable x as a NumPy array consisting of the integers from 1 through 10 inclusive. Next, the variable ds is initialized as a TF Dataset that is created from the contents of the variable x. The next code snippet invokes the filter() operator, inside of which a lambda expression returns even numbers because of this expression:

```
tf.not_equal(x%2,1)
```

The next code snippet defines the variable iterator as a “one-shot” iterator, followed by the variable next_element that is populated with the first integer in dx (which is the 0).

The final portion of Listing 6.6 contains a try/except block, inside of which is a True code block that iterates through the elements of the dataset until tf.errors.OutOfRange error is reached. When this error occurs, the code exits the loop gracefully. The output from launching the code in Listing 6.6 is:

```
('value:', 2)
('value:', 4)
('value:', 6)
('value:', 8)
('value:', 10)
```

TensorFlow also supports a TextLineDataset that is useful for processing the contents of text files. The next several sections contain code samples that show you how to define a TextLineDataset and perform simple operations.

# TENSORFLOW TEXTLINEDATASET (1)

Listing 6.7 displays the contents of file.txt that is referenced in the code in Listing 6.8.

# LISTING 6.7: file.txt

```
this is file line #1
this is file line #2
this is file line #3
this is file line #4
this is file line #5
```

Listing 6.8 displays the contents of tf-textlinedataset1.py that illustrates another way to define a LineDataset in TensorFlow.

# LISTING 6.8: tf-textlinedataset1.py

```python
import tensorflow as tf
import numpy as np

dataset = tf.data.TextLineDataset("file.txt")
dataset = dataset.map(lambda string: tf.string_split([string])).values

iterator = dataset.make_initializable_iterator()
next_element = iterator.get_next()
init_op = iterator.initializer

with tf.Session() as sess:
    sess.run(init_op)
    print(sess.run(next_element))
```

Listing 6.8 initializes the variable dataset as a TF Dataset that contains the contents of the text file. The next code snippet defines the variable iterator as an “initializable” iterator, followed by the variable next_element that is populated with the first line of text. The final portion of Listing 6.8 prints one “tokenized” line from the file, as shown here:

```
['this' 'is' 'file' 'line' '#1']
```

# TENSORFLOW TEXTLINEDATSET (2)

Listing 6.9 displays the contents of tf-textlinedatset2.py that illustrates another way to define a TextLineDataset.

# LISTING 6.9: tf-textlinedatset2.py

```python
import tensorflow as tf
import numpy as np

dataset = tf.data.TextLineDataset("file.txt")
dataset = dataset.map(lambda string: tf.string_split(string)).values
iterator = dataset.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    print(sess.run(next_element))
    print(sess.run(next_element))
    print(sess.run(next_element))
```

Listing 6.9 initializes the variable dataset as a TF Dataset that contains the contents of the text file. The next code snippet defines a lambda expression that tokenizes each line of text in the file. The next code snippet defines the variable iterator as an “initializable” iterator, followed by the variable next_element that is populated with the first line of text. The final portion of Listing 6.9 prints three “tokenized” lines of text from the file, as shown here:

```
['this' 'is' 'file' 'line' '#1']
['this' 'is' 'file' 'line' '#2']
['this' 'is' 'file' 'line' '#3']
```

# TENSORFLOW TEXTLINEDATASET (3)

Listing 6.10 displays the contents of tf-textlinedaset3.py that illustrates a third way to define a TextLineDataset.

# LISTING 6.10: tf-textlinedaset3.py

```python
import tensorflow as tf
import itertools

dataset = tf.data.TextLineDataset("file.txt")
dataset = dataset.map(lambda string: tf.string_split([string]).values

iterator = dataset.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    for i in range(5):
        print(sess.run(next_element))
```

Listing 6.10 initializes the variable dataset as a TF Dataset that contains the contents of the text file. The next code snippet defines a lambda expression that tokenizes each line of text in the file. The next code snippet defines the variable next_element as a “one-shot” iterator, followed by that is populated with the first line of text in the dataset variable. The final portion of Listing 6.10 contains a for loop that prints five “tokenized” lines of text from the file, as shown here:

```
['this' 'is' 'file' 'line' '#1']
['this' 'is' 'file' 'line' '#2']
['this' 'is' 'file' 'line' '#3']
['this' 'is' 'file' 'line' '#4']
['this' 'is' 'file' 'line' '#5']
```

![](img/552af1cab44d6186a8b200b93f459f_291_0.png)

The companion disc also contains the files tf-textlinedat4.py and tf-textlinedat5.py that use tf-data.TensorLineDataset and lazy operators.

# THE TENSORFLOW BATCH() OPERATOR (1)

Listing 6.11 displays the contents of tf-batch1.py illustrates how to use the batch() operator in TensorFlow with a reusable iterator.

# LISTING 6.11: tf-batch1.py

```python
import tensorflow as tf
import numpy as np

x = np.arange(0, 33)
dx = tf.data.Dataset.from_tensor_slices(x).batch(3)
iterator = dx.make_initializable_iterator()

with tf.Session() as sess:
  sess.run(iterator.initializer)
  for i in range(15):
    next_element = iterator.get_next()
    val = sess.run(next_element)
    print(val)
  if (i + 1) % (10 // 3) == 0 and i > 0:
    sess.run(iterator.initializer)
```

Listing 6.11 initializes the variable x as NumPy array consisting of the integers from 0 through 32 inclusive. Next, the variable dx is initialized as a TF Dataset that is created from the contents of the variable x. Notice that the definition of x involves method chaining by “tacking on” the batch(3) operator as part of the definition of dx.

The next code snippet defines the variable iterator as an “initializable” iterator, followed by the variable next_element that is populated with the first integer in dx (which is the integer 0).

The final portion of Listing 6.11 contains a loop that executes 5 times, and prints five “blocks” of numbers, where a block consists of the following output:

+   [ 0 1 2]
[3 4 5]
[6 7 8]

The reason for this “chunked” effect is because of the conditional logic that “resets” the iterator to the first element of the dataset, as shown here:

```
if (i + 1) % (10 // 3) == 0 and i > 0:
sess.run(iterator.initializer)
```

Now launch the code in Listing 6.11 to see the output in its entirety, as shown here:

+   [ 0 1 2]
[3 4 5]
[6 7 8]
+   [ 0 1 2]
[3 4 5]
[6 7 8]
+   [ 0 1 2]
[3 4 5]
[6 7 8]
