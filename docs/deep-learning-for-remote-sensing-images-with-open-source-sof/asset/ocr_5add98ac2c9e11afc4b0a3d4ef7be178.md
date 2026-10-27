![](bbox=[0.129, 0.098, 0.867, 0.176])

# **FIGURE 6.1**

The new Fully Convolutional Neural Network. Pooling operators have been removed, and convolution operators have been added. Note that there is no stride in convolution, preserving the physical spacing in spatial dimensions.

Let’s implement our new FCN architecture. We will use the `create_model2.py` Python code provided in the resources repository.[^1]

```
```python
#
# Do not forget to add the otbtf/python directory to your PYTHONPATH.
# Else "tricks" can’t be imported.
# In the OTBTF Docker image, tricks.py is located in the following
# path: /work/otb/otb/Modules/otbtf
#
# Works with OTBTF 1.7
#
from tricks import *
import sys

nclasses=6

def myModel(x):

    # input patches: 16x16x4
    conv1 = tf.layers.conv2d(inputs=x, filters=16, kernel_size=[5,5],
                             padding="valid", activation=tf.nn.relu)
    # conv1 out size: 12x12x16
    conv2 = tf.layers.conv2d(inputs=conv1, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv2 out size: 10x10x16
    conv3 = tf.layers.conv2d(inputs=conv2, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv3 out size: 8x8x16
    conv4 = tf.layers.conv2d(inputs=conv3, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv4 out size: 6x6x32
    conv5 = tf.layers.conv2d(inputs=conv4, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv5 out size: 4x4x32
    conv6 = tf.layers.conv2d(inputs=conv5, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv6 out size: 2x2x32
```
```

[^1]: https://github.com/remicres/otbtf_tutorials_resources